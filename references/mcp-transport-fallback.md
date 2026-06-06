# MCP transport fallback for NoCode-X audits

Use this reference when the normal `mcp_nocodex_mcp_*` tool surface is temporarily blocked by a transport/session/circuit-breaker problem, but `hermes mcp test nocodex-mcp` shows the server itself is reachable.

This is a fallback for read-only auditing and documentation work. Prefer normal MCP tools when they work.

## Symptoms

Normal MCP tool calls return errors such as:

- `ClosedResourceError`
- `MCP server 'nocodex-mcp' is unreachable after N consecutive failures`
- auto-retry/circuit-breaker cooldown messages

But CLI test succeeds:

```bash
hermes mcp test nocodex-mcp
# ✓ Connected
# ✓ Tools discovered: 36
```

## Recovery sequence

1. Re-authenticate if needed:

```bash
hermes mcp login nocodex-mcp
```

2. Test server reachability:

```bash
hermes mcp test nocodex-mcp
```

3. If the built-in tool channel is still blocked by circuit-breaker state, run a short Python fallback that imports Hermes' MCP client and calls the registered MCP handlers directly.

## Minimal Python pattern

```python
import sys, json
sys.path.insert(0, r'C:/Users/admin/AppData/Local/hermes/hermes-agent')

from tools.mcp_tool import discover_mcp_tools, _stop_mcp_loop
from tools.registry import registry

WORKSPACE_ID = '...'
APPLICATION_ID = '...'


def call(name, args=None):
    entry = registry.get_entry('mcp_nocodex_mcp_' + name)
    if not entry:
        return {'error': f'entry not registered: {name}'}
    raw = entry.handler(args or {})
    try:
        return json.loads(raw)
    except Exception:
        return {'raw': raw}


def unwrap(result):
    value = result.get('result') if isinstance(result, dict) else result
    if isinstance(value, str):
        try:
            return json.loads(value)
        except Exception:
            return value
    return value

try:
    discover_mcp_tools()
    call('switch_workspace', {'id': WORKSPACE_ID})
    call('switch_application', {'applicationId': APPLICATION_ID})

    print('workspace', unwrap(call('get_current_workspace')))
    print('application', unwrap(call('get_current_application')))
    print('actions', unwrap(call('get_actions')))
    print('schemas', unwrap(call('list_all_dataschemas')))
    print('apis', unwrap(call('list_all_apis')))
    print('issues', unwrap(call('list_all_issues')))
finally:
    try:
        _stop_mcp_loop()
    except Exception:
        pass
```

## Notes and pitfalls

- This fallback reads the same configured MCP server as Hermes; it does not require exposing OAuth tokens.
- Always call `_stop_mcp_loop()` in `finally` so the temporary process cleans up MCP sessions.
- MCP results are often double-encoded: the handler returns JSON with a `result` string that may itself contain JSON. Use an `unwrap()` helper.
- Keep this read-only unless the user explicitly requested a mutating NoCode-X operation.
- Do not turn transient `ClosedResourceError` into a durable claim that NoCode-X MCP is broken. The reusable lesson is the fallback/retry pattern.