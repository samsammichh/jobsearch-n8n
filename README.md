# Job Status → Tailored Resume Generator (n8n)

This repository contains an n8n workflow that connects **Google Sheets** and **Notion** to automate resume tailoring for job applications.

Jobs are tracked in Google Sheets. Resume content is stored in Notion.  
When a job is marked for resume preparation, the workflow tailors the resume content based on the **job description, role, and company**, and saves the result back to Notion.

---

## Problem

While applying to multiple jobs:
- Job details are tracked manually
- Resume content is repeatedly copied and edited
- There is no single system linking job applications and resume versions

This workflow reduces manual effort by automating resume tailoring and tracking.

---

## How the Workflow Works

1. Job applications are tracked in **Google Sheets**
2. Resume content blocks are stored in **Notion**
3. When a job status is set to **Prepare Resume**:
   - Job details are read from Google Sheets
   - Resume content is fetched from Notion
   - Resume content is tailored based on:
     - Job Description
     - Role
     - Company
4. A tailored resume version is created in Notion
5. Job status is updated in Google Sheets

---

## Inputs

### From Google Sheets
- Job ID
- Company
- Role
- Job Description
- Job Status

### From Notion
- Resume sections
- Experience bullet points
- Skills and content blocks

---

## Workflow Steps

1. **Google Sheets Trigger**
   - Monitors job rows for updates

2. **Status Check**
   - Continues only if:
     ```
     Status = "Prepare Resume"
     ```

3. **Job Context Setup**
   - Extracts company, role, and job description

4. **Resume Content Fetch**
   - Retrieves all resume content blocks from Notion

5. **Resume Aggregation**
   - Combines job context and resume content

6. **Resume Tailoring**
   - Tailors resume content using existing resume blocks
   - No new experience or skills are generated

7. **Save Resume Version**
   - Creates a new resume entry in Notion

8. **Update Job Status**
   - Updates the job row in Google Sheets

---

## AI Usage

- AI is used only for tailoring resume content
- It rephrases and selects from existing resume blocks
- No new skills or experience are generated
- Output is parsed and validated before saving

---

## Tools Used

- n8n
- Google Sheets
- Notion
- AI model for resume tailoring

---


