## The "ProcureAI" Interview Pitch
### 1. The Hook (The Problem) "I built ProcureAI, which is an intelligent, full-stack B2B procurement dashboard. I noticed that procurement managers spend hours manually reading messy PDF proposals from vendors and typing that data into Excel just to compare complex trade-offs like specifications, price, warranties, and delivery timelines side-by-side. It’s slow and error-prone. My goal was to automate this entire lifecycle—from creating the Request for Proposal (RFP) to analyzing the vendor's response—using Generative AI."

### 2. The Architecture (High Level) "Technically, I architected this as a decoupled full-stack application:

* **Backend: I used FastAPI (Python) because its asynchronous capabilities are perfect for handling I/O-bound AI tasks.**

* **Frontend: I built a responsive dashboard using React and Material UI.**

* **Database: This was my most critical design decision. I used PostgreSQL, but with a Hybrid Approach. I used standard relational tables for Vendors, but JSONB columns for the RFP data. This allows the system to store highly variable data structures—like specs for 'Laptops' vs. 'Catering Services'—without needing complex database migrations."**

### 3. The Workflow & AI Logic (The "Deep Dive") "The system has three main intelligent workflows:
* **First is Generative Design: When a user types a natural language request like 'I need 50 gaming monitors', I don't use hardcoded forms. I send that text to Google Gemini, which architecturally designs a strict JSON Schema (creating columns for 'Refresh Rate', 'Resolution', etc.) on the fly.**

 * **Second is the Communication Layer: The system uses a decoupled Email Microservice (fastapi-mail) to send professional SMTP invitations to vendors.**

 * **Third, and most complex, is the Analytical Extraction: When a vendor replies with a PDF, I use pypdf to strip the text. I then implemented a 'Schema-Guided Extraction' pipeline. I inject the schema created in step 1 back into the AI prompt. This forces the LLM to perform Zero-Shot Named Entity Recognition, mapping messy unstructured text into normalized database rows. It even normalizes currency strings like '$10k' into sortable integers."**

### 4. The Result "Finally, the frontend renders a dynamic Comparison Matrix that adapts to the data. I also implemented an AI Judge that semantically compares the User's Budget against the Vendor's Quote to assign a 0-100 'Fit Score', helping the manager make data-driven decisions instantly."

### 5. Closing "In summary, ProcureAI demonstrates how to bridge the gap between unstructured documents and structured business intelligence using a modern, scalable tech stack."

## What are the challenges you faced during this project

### Challenge 1: Taming the AI (Hallucinations & Formatting)
**"The biggest challenge was getting the LLM to be Deterministic. Early on, when I asked Gemini to 'Extract data', it would sometimes return valid JSON, but other times it would return conversational text like 'Here is the data you asked for: ...' or wrap the JSON in Markdown backticks. This broke my backend parsing logic.**
### How I solved it: I realized I couldn't trust the model blindly. I implemented a strict 'Schema-Guided' prompt strategy.
1.	I injected the exact target JSON schema into the system prompt.
2.	I added explicit constraints: 'Return JSON ONLY. Do not include markdown.'
3.	I wrote a fallback utility function (clean_json_string) in Python to strip any accidental markdown formatting before parsing. This improved reliability from ~60% to near 100%."

### Challenge 2: Handling Unstructured Data Types (Normalization)
* "The second challenge was Data Normalization. For the Comparison Matrix to work, I needed to sort vendors by Price. But raw PDF text is messy—one vendor writes '$10,000', another writes '10k USD', and another writes '10000.00'. If I treated these as strings, the sorting broke.
* How I solved it: I tried using Regex at first, but it was too brittle. I decided to 'Shift Left'—I pushed the complexity to the AI. I updated my prompt to include specific data hygiene rules: 'Normalize all currency values to integers. Remove symbols.' This was much more effective than writing Python parsing logic for every possible currency format."






