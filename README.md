## Customer Support Ticket Automation with n8n

Automate your support intake end-to-end with n8n. This workflow collects tickets via a form, summarizes and prioritizes them using Gemini AI, records structured data in Airtable, and sends timely email notifications to both the customer and your team.

![Customer Support Ticket Automation Cover](./images/Customer%20Support%20Ticket%20Automation%20Cover.png)

---

## Table of Contents

- [Overview](#overview)
- [How It Works](#how-it-works)
  - [Workflow Steps](#workflow-steps)
- [Benefits](#benefits)
- [Requirements](#requirements)
- [Setup Instructions](#setup-instructions)
  - [1. Clone or Import Workflow](#1-clone-or-import-workflow)
  - [2. Connect Gemini AI](#2-connect-gemini-ai)
  - [3. Connect Airtable](#3-connect-airtable)
  - [4. Connect Gmail](#4-connect-gmail)
  - [5. Customize Summary, Priority, and Team Mapping](#5-customize-summary-priority-and-team-mapping)
  - [6. Schedule or Host the Form Trigger](#6-schedule-or-host-the-form-trigger)
  - [7. Test the Workflow](#7-test-the-workflow)
- [Customization](#customization)
  - [Airtable Table Structure](#airtable-table-structure)
  - [Email Message Personalization](#email-message-personalization)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Overview

**Customer Support Ticket Automation** streamlines support by automating form intake, AI ticket analysis, data recording, and email alerts. It:

- Collects tickets via an n8n-hosted form
- Uses Gemini AI to summarize the issue and set a priority
- Stores all ticket details in Airtable
- Sends confirmation to the customer and notifies your support team

---

## How It Works

![Customer Support Ticket Automation Workflow](./images/Customer%20Support%20Ticket%20Automation%20workflow.png)

### Workflow Steps

1. **Trigger on form submission**
   - Captures customer inputs: Full Name, Email, Issue Category, Subject, and Detailed Description

2. **Summarize ticket via Gemini AI**
   - Generates a concise, professional summary based on submitted details

3. **Parse summary and priority**
   - Returns structured JSON with fields `summary` and `priority` (Low, Medium, High)

4. **Assign to the correct team**
   - Maps `Issue Category` to an internal team (e.g., Tech, Billing, Account)

5. **Create a record in Airtable**
   - Inserts the ticket with summary, priority, team assignment, and timestamps

6. **Email customer confirmation**
   - Sends a confirmation email acknowledging receipt

7. **Notify the support team**
   - Sends an internal notification email with all ticket details

---

## Benefits

- **Automates ticket triage**
- **Speeds response and improves accuracy**
- **Centralizes data in Airtable**
- **Ensures timely email notifications**

---

## Requirements

- [n8n](https://n8n.io/) installation or cloud account
- Google account with:
  - Access to Gemini AI API (for summarization and prioritization)
  - Access to Gmail (for sending emails)
- Airtable account and a base with a `Tickets` table
- Ability to host or access the n8n Form Trigger URL

---

## Setup Instructions

### 1. Clone or Import Workflow

- Download or import the attached workflow: `Customer Support Ticket Automation.json`
- Use the Visual Editor or n8n Desktop to open it

### 2. Connect Gemini AI

- Add your Google/Gemini AI credentials in n8n
- In the `Google Gemini Chat Model` and `Analyze Customer Details` nodes, select your credentials

### 3. Connect Airtable

- Add your Airtable Personal Access Token in n8n
- Set the Base and Table (e.g., Base: Customer Support Ticket, Table: Tickets)
- Ensure fields match those referenced by the workflow (Full Name, Email Address, Issue Category, Subject, Detailed Description, Summary, Assigned To, Priority, Status, Created At)

### 4. Connect Gmail

- Add your Gmail OAuth2 credentials to both email nodes
- Confirm the sender email and permissions are correct

### 5. Customize Summary, Priority, and Team Mapping

- Edit the AI prompt in `Analyze Customer Details` if you want different tone or output
- Adjust team mapping in the `Map to Teams` node to match your organization

### 6. Schedule or Host the Form Trigger

- Enable the `Form Trigger` node to host the submission form
- Share the form URL with users or embed it in your site/portal

### 7. Test the Workflow

- Submit a test ticket via the hosted form
- Verify Airtable record creation
- Check customer and team emails for correct content

---

## Customization

### Airtable Table Structure

Your table should resemble the example below (see sample data image):

![Ticket Data Example](./images/Ticket%20Data.png)

- Suggested fields: `Full Name`, `Email Address`, `Issue Category`, `Subject`, `Detailed Description`, `Summary`, `Assigned To`, `Priority`, `Status`, `Created At`

### Email Message Personalization

You can personalize email subject and body using Airtable fields or prior node outputs. For example, in n8n expressions:

```
Dear {{ $json.fields['Full Name'] }},

We have received your support request regarding "{{ $json.fields.Subject }}" in the "{{ $json.fields['Issue Category'] }}" category.
```

Customer confirmation example:

![Message Sent to Customer](./images/Message%20Sent%20to%20Customer.png)

Team notification example:

![Message Sent to Team](./images/Message%20Sent%20to%20Team.png)

---

## Troubleshooting

- **Form not receiving submissions**: Ensure the `Form Trigger` node is active and reachable
- **Gemini AI errors**: Check API credentials and quotas
- **Airtable write failures**: Verify Base/Table IDs and field names; ensure token permissions
- **Gmail send errors**: Confirm OAuth2 credentials and sending limits
- **Incorrect team assignment**: Update mapping logic in `Map to Teams`

---

## Contributing

Contributions and suggestions are welcome. Feel free to fork the repo, submit issues, or open pull requests for improvements.

---

## License

This project is licensed under the MIT License. See `LICENSE` for details.

---

## Contact

- **Email:** nebeyoumusie@gmail.com
- **LinkedIn:** [LinkedIn](https://www.linkedin.com/in/nebeyou-musie)
- **X(Twitter):** [X](https://x.com/NebeyouMusie)
- **Upwork:** [Upwork](https://www.upwork.com/freelancers/~017ff01729e3cd26e0?mp_source=share)
- **My Agency:** [Fuzion Tech Website](https://fuzion-tech.com/) or [Fuzion Tech on Upwork](https://www.upwork.com/agencies/1948388369189366041/)

---

**Skills & Technologies:**  
`n8n`, `Automation`, `Customer Support`, `Airtable`, `Gmail`

---

**Enjoy streamlined support intake, smarter triage, and faster resolution!**

---

> _For any issues, please contact the project maintainer or open an issue on your workflow repository._

