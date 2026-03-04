# Automated Job Outreach System (n8n)

A workflow automation system that sends personalized job outreach emails to HR contacts using Google Sheets, Gmail, and Google Drive through n8n.

This project automates cold email outreach while preventing duplicate messages and respecting safe email sending limits.

---

## Problem

Job seekers often need to send hundreds of outreach emails to recruiters or HR professionals.  
Manually sending these emails is repetitive, time-consuming, and prone to mistakes.

This project automates the outreach process using a workflow automation pipeline.

---

## Solution

The system uses **n8n workflow automation** to:

1. Read HR contact data from Google Sheets
2. Filter contacts where **Status = Pending**
3. Send personalized emails using Gmail
4. Attach resume automatically from Google Drive
5. Wait between emails to avoid spam detection
6. Update the contact status to **Sent**

---

## Workflow Architecture


```

Manual Trigger
↓
Read Google Sheets
↓
Filter (Status = Pending)
↓
Limit Rows (80)
↓
Split In Batches
↓
Download Resume (Google Drive)
↓
Send Email (Gmail)
↓
Wait 60 Seconds
↓
Update Status → Sent

```

---

## Technologies Used

- n8n (Workflow Automation)
- Google Sheets API
- Gmail API
- Google Drive API
- OAuth2 Authentication
- Docker / Local n8n Environment

---

## Key Features

### Automated Email Personalization

Emails are dynamically generated using data from Google Sheets.

Example:

```

Hi {{Name}},
I’m reaching out regarding opportunities at {{Company}}.

```

---

### Duplicate Email Prevention

Emails are sent only when:

```

Status = Pending

```

After sending, the workflow updates the row to:

```

Status = Sent

```

This prevents duplicate outreach.

---

### Email Rate Limiting

To avoid spam detection and Gmail sending limits, the workflow waits:

```

60 seconds between emails

```

---

### Automated Resume Attachment

The system automatically downloads a resume from Google Drive and attaches it to each email before sending.

---

## Example Use Case

This automation workflow was used to streamline job outreach while searching for opportunities in:

- Data Analytics
- Artificial Intelligence
- Machine Learning
- Data Science

---

## Sample Data

This repository includes a **sample contact sheet with placeholder data** to demonstrate the workflow structure.

Real contact information used in the automation is not included to protect privacy.

Example structure:

| Name | Email | Title | Company | Status |
|-----|-----|-----|-----|-----|
| John Smith | john.smith@example.com | HR Manager | TechCorp | Pending |
| Sarah Lee | sarah.lee@example.com | Talent Partner | DataWorks | Pending |

---

## Future Improvements

- Randomized subject lines
- Email open tracking
- AI-generated personalized messages
- CRM integration
- Automated follow-up emails

---

## Author

**Vignesha S**  
Data Analyst | AI & Automation Enthusiast

