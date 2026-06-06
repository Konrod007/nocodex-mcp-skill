# Installing And Maintaining The NoCode-X MCP Skill In Hermes

Use this reference when a user provides a local `nocodex-mcp` skill folder and asks to review, improve, or install it into Hermes.

## Local Skill Installation Pattern

Hermes `hermes skills install` is for hub identifiers or direct HTTP(S) `SKILL.md` URLs. For a local skill directory, install by copying the complete skill folder into the active profile's skills tree:

```bash
SRC='/path/to/nocodex-mcp-skill'
DEST="$LOCALAPPDATA/hermes/skills/mcp/nocodex-mcp"
mkdir -p "$(dirname "$DEST")"
rm -rf "$DEST"
cp -a "$SRC" "$DEST"
```

If `DEST` already exists, make a timestamped backup before replacing it.

## Validation Checklist

Before copying or after editing, validate:

- `SKILL.md` starts at byte 0 with `---`.
- YAML frontmatter parses successfully.
- `name: nocodex-mcp` is present.
- `description` is quoted if it contains `:` characters.
- `description` is <= 1024 chars.
- body after frontmatter is non-empty.
- linked files under `references/` exist.
- YAML files such as `agents/openai.yaml` parse successfully.

Minimal Python validator:

```python
import pathlib, re, yaml
root = pathlib.Path(r'D:/cursor-prod/nocode-x/nocodex-mcp-skill')
content = (root / 'SKILL.md').read_text(encoding='utf-8')
assert content.startswith('---')
m = re.search(r'\n---\s*\n', content[3:]); assert m
fm = yaml.safe_load(content[3:m.start()+3])
assert fm['name'] == 'nocodex-mcp'
assert fm.get('description') and len(fm['description']) <= 1024
assert content[m.end()+3:].strip()
for rel in ['references/tools-reference.md', 'references/workflows.md', 'references/debugging-playbook.md', 'references/safety-and-limitations.md', 'references/vendor-roadmap.md', 'agents/openai.yaml']:
    p = root / rel
    assert p.exists(), rel
    if p.suffix in ['.yaml', '.yml']:
        yaml.safe_load(p.read_text(encoding='utf-8'))
```

## NoCode-X Transport Detail

For the NoCode-X endpoint `https://back.nocode-x.com/sse`, use SSE transport:

```yaml
transport: "sse"
url: "https://back.nocode-x.com/sse"
```

Do not label this endpoint as `streamable_http` unless the vendor changes the endpoint/protocol.

## Post-Install Verification

After copying into Hermes:

```bash
hermes skills list | grep -i 'nocodex\|nocode-x'
```

Expected: `nocodex-mcp` appears as a local enabled skill under category `mcp`.

Then verify the loader can read it with `skill_view(name='nocodex-mcp')` in the current/fresh Hermes session.

## User-Preference Reminder For NoCode-X Audits

When auditing NoCode-X apps, avoid unsupported extrapolation. If MCP does not expose rendered UI, environment names, reproduction steps, or runtime data, mark those fields as `Unknown` and ask for the minimum missing input rather than guessing.