# CareerCoachAssistant
AI-Powered Skill Gap Analysis & Training Recommendation System  
(using Amazon Q Business)

---

## Project Overview
- Automates skill-gap analysis for employment coaches  
- Features:
  - CV & JD skill extraction
  - Skill-gap analysis
  - Personalized training recommendations & schedules
  - Coach refinement inputs
  - Indexed course catalogs (PDF + S3)
  - ACL-based restricted access & keyword blocking
  - Secure access via IAM Identity Center

---

## Architecture (high level)
Coach User → Upload CV + JD → Q App  
↓  
AI Skill Gap Analysis  
↓  
Retrieve Courses (PDF uploader + S3 + ACL)  
↓  
Apply Keyword Blocking & Guardrails  
↓  
Recommendations & Learning Plan

---

## Prerequisites (AWS)
- Amazon Q Business / Q Apps
- AWS IAM Identity Center
- Amazon S3
- IAM roles
- Udacity sandbox provides CareerCoaches group & pre-enabled Q Business

---

## Amazon Q Business App Setup
Settings:
- Application Name: CareerCoachAssistant
- User Access: Authenticated (IAM Identity Center)
- Web Experience: Enabled
- LLM Direct Query Access: Enabled (Global Controls)

---

## Data Sources
1. File Uploader: CourseCatalogA/B.pdf, AdditionalCourseCatalogA/B.pdf  
2. S3 (us-west-2): s3://career4all-course-catalog-han  
   - Restricted1.pdf, Restricted2.pdf

Indexed for Q search and recommendation.

---

## Access Control (ACL)
Example acl.json:
```json
{
  "accessControlList": [
    {
      "principals": ["career.coach.one"],
      "allowedPatterns": ["Restricted1.pdf"],
      "deniedPatterns": []
    },
    {
      "principals": ["career.coach.two"],
      "allowedPatterns": ["Restricted2.pdf"],
      "deniedPatterns": []
    }
  ]
}
```
- Uploaded via Data Source → Settings → ACL Configuration

---

## Keyword Blocking (Global Controls)
Blocked phrases:
- Gambling
- Casino
- Self-harm
- Attack

Purpose: prevent unsafe or irrelevant recommendations.

---

## User & Group Access
- Udacity sandbox: group-level assignment only
- Group: CareerCoaches (all coaches gain access)

---

## Verification Steps
Skill gap query should:
- Use indexed PDFs
- Respect ACL restrictions
- Remove blocked keywords
- Generate learning plan and recommendations

Expected: list 5 relevant courses for provided CV + JD.

---

## Q App Structure
Input Cards:
- CV Upload
- Job Description Upload
- Coach Notes

Output Cards:
- Skill Gap Analysis
- Training Recommendation
- Learning Schedule

Built with Q Apps → Create App → Custom Prompt

---

## User Guide (Coach workflow)
1. Open Web Experience link  
2. Log in via IAM Identity Center  
3. Upload CV & JD  
4. Ask: "Perform skill-gap analysis and recommend courses"  
5. Review & refine recommendations (e.g., target beginner learner)

---

## Updating Content
- Upload new PDFs to S3 or File Uploader
- Click "Sync Now"
- Content indexed and available immediately

---

## Conclusion
CareerCoachAssistant automates coaching workflows with secure, ACL-aware recommendations using Amazon Q Business — improving accuracy and coach efficiency.

---

---

# CareerCoachAssistant
AI-Powered Skill Gap Analysis & Training Recommendation System  
(using Amazon Q Business)

---

## Project Overview
- Automates skill-gap analysis for employment coaches  
- Features:
  - CV & JD skill extraction
  - Skill-gap analysis
  - Personalized training recommendations & schedules
  - Coach refinement inputs
  - Indexed course catalogs (PDF + S3)
  - ACL-based restricted access & keyword blocking
  - Secure access via IAM Identity Center

---

## Architecture (high level)
Coach User → Upload CV + JD → Q App  
↓  
AI Skill Gap Analysis  
↓  
Retrieve Courses (PDF uploader + S3 + ACL)  
↓  
Apply Keyword Blocking & Guardrails  
↓  
Recommendations & Learning Plan

---

## Prerequisites (AWS)
- Amazon Q Business / Q Apps
- AWS IAM Identity Center
- Amazon S3
- IAM roles
- Udacity sandbox provides CareerCoaches group & pre-enabled Q Business

---

## Amazon Q Business App Setup
Settings:
- Application Name: CareerCoachAssistant
- User Access: Authenticated (IAM Identity Center)
- Web Experience: Enabled
- LLM Direct Query Access: Enabled (Global Controls)

---

## Data Sources
1. File Uploader: CourseCatalogA/B.pdf, AdditionalCourseCatalogA/B.pdf  
2. S3 (us-west-2): s3://career4all-course-catalog-han  
   - Restricted1.pdf, Restricted2.pdf

Indexed for Q search and recommendation.

---

## Access Control (ACL)
Example acl.json:
```json
{
  "accessControlList": [
    {
      "principals": ["career.coach.one"],
      "allowedPatterns": ["Restricted1.pdf"],
      "deniedPatterns": []
    },
    {
      "principals": ["career.coach.two"],
      "allowedPatterns": ["Restricted2.pdf"],
      "deniedPatterns": []
    }
  ]
}
```
- Uploaded via Data Source → Settings → ACL Configuration

---

## Keyword Blocking (Global Controls)
Blocked phrases:
- Gambling
- Casino
- Self-harm
- Attack

Purpose: prevent unsafe or irrelevant recommendations.

---

## User & Group Access
- Udacity sandbox: group-level assignment only
- Group: CareerCoaches (all coaches gain access)

---

## Verification Steps
Skill gap query should:
- Use indexed PDFs
- Respect ACL restrictions
- Remove blocked keywords
- Generate learning plan and recommendations

Expected: list 5 relevant courses for provided CV + JD.

---

## Q App Structure
Input Cards:
- CV Upload
- Job Description Upload
- Coach Notes

Output Cards:
- Skill Gap Analysis
- Training Recommendation
- Learning Schedule

Built with Q Apps → Create App → Custom Prompt

---

## User Guide (Coach workflow)
1. Open Web Experience link  
2. Log in via IAM Identity Center  
3. Upload CV & JD  
4. Ask: "Perform skill-gap analysis and recommend courses"  
5. Review & refine recommendations (e.g., target beginner learner)

---

## Updating Content
- Upload new PDFs to S3 or File Uploader
- Click "Sync Now"
- Content indexed and available immediately

---

## Conclusion
CareerCoachAssistant automates coaching workflows with secure, ACL-aware recommendations using Amazon Q Business — improving accuracy and coach efficiency.
