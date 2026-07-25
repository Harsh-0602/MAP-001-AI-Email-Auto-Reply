# MAP-001 — AI Email Auto Reply Assistant

## Overview

An AI-powered workflow built with n8n that generates professional email reply drafts using Google Gemini, with validation and human review built in before anything reaches a customer.

---

## Business Problem

Many SaaS companies spend valuable time replying to repetitive customer emails, and fully automated replies carry the risk of sending something wrong or irrelevant without anyone checking it first.

---

## Solution

This workflow:

- Validates that the incoming customer message is not empty before processing
- Uses Google Gemini to generate a professional response
- Validates the AI output before proceeding (prevents silent failures on bad/empty responses)
- Creates a Gmail **draft** instead of auto-sending — a human reviews and sends it
- Flags anything that fails validation into a separate review path instead of failing silently

---

## Workflow

Webhook
↓
Validate Customer Input (empty check)
↓
Google Gemini (generate reply)
↓
Validate AI Reply (output check)
↓ (valid) ↓ (invalid)
Create Gmail Draft Mark Needs Review
↓
Human reviews & sends

---

## Tech Stack

- n8n
- Google Gemini
- Gmail API

---

## Sample Input / Output

**Input:**
```json
{
  "customer_email": "customer@example.com",
  "message": "Hi, I'd like to know the status of my order #12345."
}
```

**Output (Gmail Draft created):**

Dear Customer,

Thank you for reaching out regarding order #12345. Let me check on the current status and get back to you with the shipping details shortly.

Regards,
Support Team

---

## Screenshots

<img width="1640" height="576" alt="Screenshot 2026-07-25 104043" src="https://github.com/user-attachments/assets/7ec8d7e0-8210-4f32-9102-ff3eeba9969c" />


---

## Architecture

<img width="1600" height="1320" alt="architecture" src="https://github.com/user-attachments/assets/dbb31c3c-0410-4b3b-a8d2-cb879351e889" />


---

## Demo



https://github.com/user-attachments/assets/e732a50b-319a-4115-814b-913cd67ace30



---

## Recent Updates (based on r/n8n community feedback)

This workflow was reviewed by the n8n community on Reddit, and the following changes were made based on their feedback:

- Added input validation to reject empty/meaningless messages before calling the AI
- Added output validation to catch empty or malformed AI responses instead of failing silently
- Switched from auto-send to draft + human review — removes the risk of an incorrect AI reply reaching a real customer
- Added a "Mark Needs Review" path to safely capture failed cases for manual follow-up


---

## Future Improvements

- Switch from webhook trigger to native Gmail Trigger for more reliable email detection
- CRM Integration
- Ticket Classification
- Lead Qualification
- Memory
- Confidence-threshold based auto-send (only for high-confidence replies)
