## Part 12: Web Crawler & RAG with Pinecone

Video: http://www.youtube.com/watch?v=Bmy-B1zVBIk

### 1. Core Concepts (RAG & Vector Databases)

**Pinecone:**
Vector database that stores information as vectors — ideal for AI tasks [00:29]

**RAG (Retrieval Augmented Generation):**
Concept where AI (LLM) searches vector storage and uses retrieved information to answer user questions [00:44]

### 2. Setup & Configuration

**Pinecone Assistant:**
- Create assistant in Pinecone
- Get API key [01:40]

**NoCode-X Plugin:**
```
Hub → Search "Pinecone Website Crawler" → Install
```
[02:27]

**Scrape Config Data Format:**
```
Data Format: scrape_config
Fields:
- pinecone_api_key (Secret) - API key
- assistant_name (Text) - Assistant name
- max_pages (Number) - Max pages to crawl (e.g., 200) [05:13]
- scrape_links (Boolean) - Follow internal links
```
[03:21]

### 3. Scraping Process

**Initiate Crawling:**
```
Create record in Scrape Request table:
- url: "https://nocode-x.com"
- status: "pending"
```
[06:09]

**Engine Workflow:**
```
1. Download HTML from URL
2. Extract text content
3. Convert to Markdown
4. Upload to Pinecone Assistant
5. Index for semantic search
```
[06:54]

**Result:**
All website pages become "knowledge" for the AI assistant

### 4. Extracting Structured Data

**Instead of just chatting with bot:**
Get data in strict format (JSON) using your schema

**Step 1: Create Data Format**
```
Website Information:
- company_name (Text)
  Description: "Company name from homepage or about page"
  
- email (Email)
  Description: "Contact email, may be on contact page or in footer"
  
- phone (Text)
  Description: "Phone number with country code"
  
- social_links (List)
  Description: "Links to LinkedIn, Twitter, Facebook"
  
- products (List of Objects)
  Description: "Products or services offered"
```
[15:06, 15:34]

**Step 2: Fetch Structured Data**
```
Action: Extract Website Info

Function: Fetch website information from assistant
Parameters:
- Assistant: Your Pinecone assistant
- URL: Website to analyze
- Output Format: Website Information (Data Format)
```
[14:20]

**AI Uses Field Descriptions:**
```
Detailed descriptions help AI find correct data:
❌ Bad: "Email"
✅ Good: "Contact email address, usually found on contact page or footer, may be obfuscated"
```
[15:34, 20:27]

### 5. Automation & API

**Creating API Endpoint:**
```
Create endpoint in 30 seconds:
- Input: URL parameter
- Action: Fetch website info from assistant
- Output: JSON with extracted data

Result: POST /extract → Returns {company, email, phone, products}
```
[23:31]

**Automation Example:**
```
After extracting email:
1. Save to database
2. Send automated email to company
3. Add to CRM
4. Notify sales team
```
[13:55]

### Best Practices

**Handling Protection:**
```
Some sites obfuscate emails:
✅ Add hints in field descriptions
✅ Specify alternative locations
✅ Mention expected domains

Example: "Email may be on contact page, 
about page, or footer. Look for @company.com"
```
[20:27]

**Customization:**
```
All plugins are Blueprints (чертежи):
✅ Modify logic
✅ Combine with other APIs
✅ Change prompts
✅ Add preprocessing
```
[22:12]

**Limits:**
```
✅ Always set Max pages limit
✅ Start small (10-20 pages)
✅ Monitor API usage
✅ Check crawl duration

Why: Avoid infinite crawling and extra costs [05:13]
```

### Use Cases

**Lead Generation:**
- Crawl competitor websites
- Extract contact information
- Enrich CRM data automatically

**Content Aggregation:**
- Collect articles from news sites
- Index documentation
- Build knowledge bases

**Market Research:**
- Analyze product catalogs
- Compare pricing
- Monitor changes over time
