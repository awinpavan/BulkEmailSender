# Custom Bulk Email Sender (n8n Workflows)

A personalized bulk email automation system built using **n8n**, **OpenAI**, **Google Sheets**, and **Microsoft Outlook**.

The project consists of two independent workflows:

1. **Generate personalized emails and create Outlook drafts**
2. **Review and send the generated drafts**

This separation allows you to review every email before it is sent, making the workflow safer for large-scale outreach.

---

# Features

- Read recipient information directly from Google Sheets
- Generate personalized email content using OpenAI
- Automatically create Outlook drafts
- Store generated email content back into Google Sheets
- Save Outlook Draft IDs for tracking
- Send approved drafts in bulk
- Batch processing for improved API usage
- Easily customizable prompts, signatures, and email templates

---

# Project Structure

```
CustomeBulkEmailSender/
│
├── TEobwjDS1ux9BBnA-My_workflow.json
│   └── Generates personalized emails and creates Outlook drafts
│
└── ucOoYttOEQhjVeaV-My_workflow_2.json
    └── Sends previously created Outlook drafts
```

---

# Prerequisites

Before importing the workflows, ensure you have:

- n8n (Cloud, Desktop, or Self-hosted)
- Google Sheets OAuth2 credentials
- Microsoft Outlook OAuth2 credentials
- OpenAI API credentials
- A Google Sheet containing recipient information

Useful links:

- n8n Documentation  
  https://docs.n8n.io/

---

# Workflow Overview

## Workflow 1 – Generate Emails & Create Drafts

This workflow:

- Reads recipient data from Google Sheets
- Filters valid rows
- Generates personalized email content using OpenAI
- Updates the generated email back into the sheet
- Appends your HTML email signature
- Creates an Outlook draft
- Saves the Draft ID back into Google Sheets

### Workflow Flow

```
Manual Trigger
      │
      ▼
Read Google Sheet
      │
      ▼
Filter Valid Rows
      │
      ▼
Loop Through Recipients
      │
      ▼
Generate Email (OpenAI)
      │
      ▼
Update Google Sheet
      │
      ▼
Append HTML Signature
      │
      ▼
Create Outlook Draft
      │
      ▼
Save Draft ID
```

---

## Workflow 2 – Send Outlook Drafts

This workflow:

- Reads Draft IDs from Google Sheets
- Loops through each row
- Sends the corresponding Outlook draft

### Workflow Flow

```
Manual Trigger
      │
      ▼
Read Google Sheet
      │
      ▼
Loop Through Draft IDs
      │
      ▼
Send Outlook Draft
```

---

# Installation

## 1. Import the Workflows

Import both JSON files into your n8n instance.

```
TEobwjDS1ux9BBnA-My_workflow.json
```

```
ucOoYttOEQhjVeaV-My_workflow_2.json
```

---

## 2. Configure Credentials

Configure the following credentials inside n8n:

- Google Sheets OAuth2
- Microsoft Outlook OAuth2
- OpenAI API

---

## 3. Configure Google Sheets

Open every Google Sheets node and update:

- Spreadsheet ID
- Sheet Name

Ensure the column names match those expected by the workflow.

---

## 4. Run Workflow 1

Execute:

**Generate Emails & Create Drafts**

The workflow will:

- Read recipients
- Generate personalized emails
- Create Outlook drafts
- Store Draft IDs back into the spreadsheet

---

## 5. Review Drafts

Open Outlook and verify:

- Subject
- Personalization
- Formatting
- Signature
- Recipient

---

## 6. Run Workflow 2

Once you're satisfied with the generated drafts, execute the second workflow to send them.

---

# Customization

## OpenAI Prompt

Inside the OpenAI node you can modify:

- Writing tone
- Prompt instructions
- Model
- Temperature
- Maximum tokens

---

## Email Signature

The JavaScript Code node appends an HTML signature.

Replace the HTML inside the `signature` variable with your own signature.

---

## Outlook Fields

Modify the Outlook node to customize:

- Subject
- HTML body
- CC recipients
- Sender
- Attachments

---

## Batch Size

Adjust the **Loop Over Items** node to control:

- Processing speed
- OpenAI API usage
- Microsoft Outlook rate limits

---

# Testing

Before sending emails to real recipients:

- Use a test spreadsheet
- Add only a few recipients
- Send drafts to yourself
- Verify formatting and personalization
- Confirm all expressions resolve correctly

---

# Troubleshooting

### Missing Credentials

If imported nodes display a red warning icon:

- Open the node
- Select the correct credential
- Save the workflow

---

### Google Sheets Not Returning Data

Check:

- Spreadsheet ID
- Sheet name
- OAuth permissions
- Spreadsheet sharing settings

---

### OpenAI Errors

Verify:

- API key
- Billing status
- Model availability

---

### Outlook Errors

Verify:

- OAuth permissions
- Microsoft account authorization
- Required Outlook scopes

---

### Expression Errors

If expressions fail:

- Verify the column names
- Check execution logs
- Confirm the referenced nodes return the expected values

---

# Security

- Never store API keys inside workflow JSON files.
- Use n8n Credentials to securely manage secrets.
- Review generated emails before sending.
- Be mindful of email regulations and organizational policies when sending bulk emails.

---

# Repository

Workflow Files

- Generate Emails & Drafts  
  https://github.com/awinpavan/BulkEmailSender/blob/main/CustomeBulkEmailSender/TEobwjDS1ux9BBnA-My_workflow.json

- Send Drafts  
  https://github.com/awinpavan/BulkEmailSender/blob/main/CustomeBulkEmailSender/ucOoYttOEQhjVeaV-My_workflow_2.json
