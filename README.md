# MAP-001 — AI Email Auto Reply Assistant

## Overview

An AI-powered workflow built with n8n that automatically generates professional email replies using Google Gemini and sends them through Gmail.

---

## Business Problem

Many SaaS companies spend valuable time replying to repetitive customer emails.

---

## Solution

This workflow automatically:

- Receives a customer inquiry
- Uses Google Gemini to generate a professional response
- Sends the reply through Gmail

---

## Workflow

Customer
↓
Webhook
↓
Google Gemini
↓
Gmail
↓
Customer receives reply

---

## Tech Stack

- n8n
- Google Gemini
- Gmail API

---

## Screenshots

<img width="1082" height="362" alt="Screenshot 2026-07-23 115645" src="https://github.com/user-attachments/assets/d4769357-1e8b-42b6-bdcf-3e46761fb690" />


---

## Architecture

<img width="1360" height="1040" alt="architecture" src="https://github.com/user-attachments/assets/d650fc68-7022-4457-ad1f-a0e587d42a86" />


---

## Demo

(Video later)

---

## Future Improvements

- CRM Integration
- Ticket Classification
- Lead Qualification
- Memory
- Human Approval
