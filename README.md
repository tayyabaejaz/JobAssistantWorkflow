# Job Assistant Workflow (n8n + LLM + Google Sheets)

This repository contains an **n8n workflow** that helps job seekers analyze job postings automatically and save results into Google Sheets.

---

## 🚀 Workflow Overview

1. **HTTP Request – Job API**  
   Fetches job postings from an external API.

2. **Function – Extract Job Info**  
   Extracts key fields:  
   - `title`  
   - `company`  
   - `description`  

3. **LLM – Analyze Job Posting**  
   Sends job info to an AI model, which generates:  
   - A summary of the role  
   - Key required skills  
   - A tailored cover letter  

4. **Merge – Job Info + LLM Response**  
   Combines original job info with AI output.

5. **Function – Parse LLM Output**  
   Extracts structured fields (`summary`, `skills`, `coverLetter`) using regex.

6. **Google Sheets – Save Results**  
   Appends a row for each job, containing:  
   - Job Title  
   - Company  
   - Description  
   - Summary  
   - Skills  
   - Cover Letter  

---

## 📦 Files

- `workflows/JobAssistantWorkflow.json` → The exported n8n workflow (can be imported into n8n).  

---

## 🛠 How to Use

### 1. Import Workflow into n8n
- Open n8n → **Import Workflow**  
- Upload `JobAssistantWorkflow.json`  

### 2. Set Up Credentials
- Add credentials for:
  - **HTTP Request** → your Job API  
  - **Google Sheets** → connect with your Google account  
  - **LLM Provider** → (OpenAI, AtlasCloud, etc.)  

### 3. Run Workflow
- Start the workflow manually or schedule it with **Cron**.  
- Each job posting will be analyzed and saved into Google Sheets.

---

## 🌱 Example Output (Google Sheets)

| Title             | Company   | Description        | Summary | Skills | Cover Letter |
|-------------------|-----------|--------------------|---------|--------|--------------|
| Junior AI Engineer | Cobec Inc | Full-stack AI role | ...     | ...    | ...          |

---

## 📌 Notes
- Update regex in the **Parse LLM Output** function node if the model’s response format changes.  
- You can extend this workflow to also send email alerts, create Trello/Jira tasks, or save to a database.  
