# Mile End Records — Customer Support & Music Recommendation Bot

This repository documents the design, logic, and functionality of the **Mile End Records Chatbot**, a fictional but production-minded customer support assistant built using **Botpress Cloud**.

The bot is designed to support real user needs for an independent record store by combining structured knowledge, inventory awareness, recommendation logic, and clear human escalation paths.

---

## 🎯 Purpose of the Bot

The chatbot serves three primary goals:

1. **Support customers** by answering common questions about the store, policies, vinyl care, and equipment.
2. **Assist with music discovery** through thoughtful, taste-based recommendations.
3. **Support internal operations** by raising tickets and scheduling appointments.

The bot is intentionally designed to avoid hallucinations or invent information. When it cannot confidently answer a question, it clearly directs users to contact a human staff member.

---

## 🧠 High-Level Bot Architecture

The bot is built around **intent-driven conversational paths**, each ending in a clear resolution:
- An answer
- A recommendation
- An operational action
- Or a human handoff

All responses are grounded in:
- A structured knowledge base (FAQs, store guide)
- A CSV-based inventory system
- Explicit fallback and escalation rules

---

## 🗺️ Conversation Paths & End States

### 1. Welcome & Entry Point

**Path:**  
`Start → Welcome Message`

**Function:**  
- Greets the user in a warm, record-store tone  
- Sets expectations for what the bot can help with  

**Possible Transitions:**  
- Store information  
- Inventory lookup  
- Music recommendation  
- Equipment advice  
- Human assistance  

**End State:**  
Routes the user into the appropriate intent flow.

---

### 2. Store Information & FAQs

**Path:**  
`User Question → Store Info / FAQ Node`

**Covers:**  
- Store hours & location  
- Shipping & pickup policies  
- Returns & exchanges  
- Vinyl grading  
- Vinyl care & storage  
- Equipment sales & recommendations  

**Data Source:**  
- Public-facing store guide (PDF / Knowledge Base)

**End State:**  
- Answer provided  
- Or escalation to human if information is missing or ambiguous  

---

### 3. Inventory Lookup (Records)

**Path:**  
`User Requests Specific Record → Inventory Check`

**Logic:**  
- Queries the inventory CSV  
- Confirms availability and stock quantity  
- Avoids guessing if the record is not found  

**Additional Behavior:**  
- Increments `demand_counter` for the requested item  
- Helps identify restock priorities over time  

**End State:**  
- Record confirmed in stock  
- Record out of stock  
- Or record not found → human handoff  

---

### 4. Music Recommendations

**Path:**  
`User Describes Taste → Recommendation Logic`

**Logic:**  
- Uses normalized genres for cleaner matching  
- Factors in popularity and demand data  
- Keeps recommendations grounded and relevant  

**Tone:**  
- Enthusiastic but not pushy  
- Knowledgeable and non-judgmental  

**End State:**  
- One or more curated recommendations  
- Optional follow-up question  
- Or escalation if the request is too vague  

---

### 5. Equipment & Setup Guidance

**Path:**  
`User Asks About Turntables / Equipment → Equipment Advisor`

**Covers:**  
- Entry-level vs. mid-range turntables  
- Speaker types (powered vs. passive)  
- Accessories (brushes, sleeves, cleaners)  
- Warnings against damaging equipment (e.g., suitcase turntables)  

**Constraints:**  
- No repair promises  
- No unsupported technical claims  

**End State:**  
- General guidance provided  
- Referral to in-store staff or trusted technicians  

---

## 🛠️ Operational Integrations

### JIRA Issue Creation

The bot is designed to support internal workflows by creating **JIRA issues** when needed.

---

### Google Calendar Event Creation

The bot can also trigger **Google Calendar events** for equipment reparation requests.

---

Thank you to **Botpress** for the opportunity to work with the platform and demonstrate how thoughtful conversational design, operational awareness, and customer empathy can come together in a practical support solution.

This project reflects a support-first mindset, where automation exists to help both customers and teams — not replace them.
