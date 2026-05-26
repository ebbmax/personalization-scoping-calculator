# Personalization Scoping Calculator

A self-contained HTML tool for Salesforce Account Executives to scope Personalization opportunities and generate a recommended SKU bill of materials (BOM).

**Live URL:** [https://ebbmax.github.io/personalization-scoping-calculator/](https://ebbmax.github.io/personalization-scoping-calculator/)

---

## Overview

The calculator walks an AE through a guided 4-step flow to capture a customer's personalization requirements and outputs a recommended list of SKUs with quantities and notes — ready to use in a quote.

---

## Features

- **Welcome screen** — choose to start a new calculator or load a previously saved one
- **Export config file** — save all inputs as a `.scopingcalc` file, named `{Customer Name}_{datetime}.scopingcalc`
- **Load existing calculator** — drag and drop or browse for a `.scopingcalc` file to reload a prior session and adjust inputs
- **Input validation** — required fields are enforced at each step before progressing
- **SLDS2 design** — built with Salesforce Lightning Design System tokens, no external CSS dependencies
- **Single file** — no build step, server, or dependencies required; open directly in any modern browser

---

## The 4-Step Flow

### Step 1 — Scoping Context
- Customer name
- Contract length (1–5 years)
- Provisioning region (AMER / EMEA / APAC)
- Does the customer own Marketing Cloud Personalization today? *(required)*
- Is the customer actively using MCP to power personalized experiences?

### Step 2 — Channel Scoping
Select the channels to personalize:
- Web
- Mobile App
- Marketing Cloud Engagement (Email)
- Marketing Cloud Advanced (Email Recommendations)
- Retail Triggers *(with trigger type sub-selection)*

### Step 3 — Channel Volumes
Enter volume inputs for each selected channel:
- **Web** — number of domains + Monthly Unique Visitors (MUV) per domain
- **Mobile** — number of apps + Monthly Active Users (MAU) per app
- **Email** — monthly emails sent + % of emails using personalized recommendations
- **Retail** — number of named contacts

Each of the **Web** and **Mobile** sections includes an **Advanced Settings** panel where the *Decisions Per MUV* (web) and *Decisions Per MAU* (mobile) used in the credit-calculation formula can be overridden. Both default to **8** and can be configured independently to make the credit estimate higher or lower than the default.

All volume fields are required before SKUs can be generated.

### Step 4 — Recommended SKUs
Displays a generated BOM with:
- SKU name
- Recommended quantity
- Notes and guidance

Also shows a scoping summary of all inputs and contextual callouts (e.g. outbound-only channel warnings, Data Cloud prerequisite guidance).

---

## Config Files

`.scopingcalc` files are JSON exports of a complete calculator session. They capture every input across all steps and can be reloaded via **Update Existing Calculator** on the welcome screen to pick up where you left off or share a draft with a colleague.

---

## Tech Stack

- Vanilla HTML, CSS, JavaScript — no frameworks
- Salesforce SLDS2 design tokens (inlined)
- No build step or server required
