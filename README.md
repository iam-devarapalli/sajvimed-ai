# SajviMed - AI
Intelligent Healthcare Knowledge & Research Assistant.

### Project vision: 
Develop an intelligent healthcare assistant that understands medical questions, analyzes medical documents, retrieves trustworthy scientific evidence, and provides explainable answers with verified source citations.

## Module 1: 
### SajviMed Chatbot
A user enters a brand or generic name, confirms the exact medicine if there are multiple matches, and gets a plain-language drug profile with links to the source.

The most important feature is “When and how to take it.” Some instructions refer to meals, some specify a time of day, and some leave the timing to the prescription. Your app should preserve that distinction. If the verified source gives no time of day, display “No specific time of day is listed. Follow your prescription

###  1. What the chatbot should show
<img width="710" height="462" alt="Screenshot 2026-11-21 at 9 02 05 PM" src="https://github.com/user-attachments/assets/c05b78e1-afe2-463f-8a7a-2a9f2794d0a5" />

### 2. Choose your drug data sources
<img width="717" height="217" alt="Screenshot 2026-11-21 at 9 05 25 PM" src="https://github.com/user-attachments/assets/f7628018-b0a5-4202-9215-beccf7f54012" />

Indian Website: https://cdscoonline.gov.in/CDSCO/brandNames

USA Website: https://lhncbc.nlm.nih.gov/RxNav/APIs/api-Prescribable.getApproximateMatch.html

### 3. Build it with FastAPI, PostgreSQL, and React
<img width="1140" height="1332" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/7c7bd039-7335-4f27-b1cd-6f3b975b3740" />

### 3.1 Build the catalogue:
Store each product and its aliases in PostgreSQL. Keep the ingredient, strength, form, route, market, and manufacturer. Link every profile to a versioned source document.

### 3.2 Build the lookup and drug card first:
Create GET /drugs/search?q=...&market=IN for product selection and GET /drugs/{id} for the verified profile. Render timing, food instructions, and serious warnings directly from reviewed fields.
### 3.3 Add RAG for follow-up questions:
Create POST /drugs/{id}/ask. Use LangChain to retrieve sections from the confirmed product’s label and an LLM to explain them in plain language with citations. If the source has no answer, say so. For questions like “Can I take it at midnight instead?” show the verified instructions and direct the user to a pharmacist or prescriber for an individual schedule change.
### 3.4 Evaluate with LangSmith: 
Test misspellings, look-alike brands, combination products, different strengths and release forms, missing timing, missed doses, and requests to change a prescribed schedule. Your most important checks are correct product selection and zero invented dose or timing instructions.

