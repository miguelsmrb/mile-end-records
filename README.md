# 🎧 Mile End Records | AI Concierge (Isobel)

> **TSE Case Study Assignment** > **Candidate:** [Your Name]  
> **Target Role:** Technical Support Engineer (TSE)  
> **Platform:** Botpress Cloud  
> **Location Focus:** Mile End, Montreal

---

## 📍 Project Overview
This project features **Isobel**, an AI assistant for *Mile End Records*, a boutique vinyl shop in Montreal. The goal was to build a bot that balances high-end technical logic with a distinct, local brand voice, solving for both customer support (FAQs) and sales discovery (Recommendations).

### 🔗 Live Links
* **Live Deployment:** [INSERT YOUR GITHUB PAGES URL HERE]
* **Botpress Studio:** [INSERT YOUR BOTPRESS PUBLIC LINK HERE]

---

## 🛠️ Technical Architecture

Isobel is built using a "Three-Pillar" data strategy to ensure accuracy and minimize LLM hallucination:

| Pillar | Component | Purpose |
| :--- | :--- | :--- |
| **Structured** | Botpress Tables | Manages real-time inventory (Artist, Album, Price, Stock). |
| **Unstructured** | Knowledge Base | Handles "Ticket Deflection" for store hours, vinyl grading, and care tips. |
| **Dynamic** | iTunes Search API | Fetches live album data for personalized user recommendations. |



---

## ✨ Key Features

### 1. The "Mile End" Persona
Isobel is programmed with a specific "Record Store Employee" persona—knowledgeable, inclusive, and Montreal-aware. She uses variables to maintain context-aware conversations (e.g., addressing users by name and referencing previous genre interests).

### 2. Smart Recommendation Engine (API)
Using an **Execute Code** block, the bot queries the iTunes API to provide real-time suggestions based on user input. 
* **TSE Logic:** Implemented `try/catch` error handling and empty-state fallbacks to ensure the UI never "breaks" if an artist isn't found.

### 3. Integrated Knowledge Base (KB)
The KB acts as the "Ground Truth" for store policies. If a user asks about **Vinyl Grading (VG+ vs M)**, the bot pulls specifically from the store’s standards rather than guessing, reducing the need for human staff intervention.

---

## 🧠 Technical Decisions & Troubleshooting

* **Proactive Engagement:** I utilized the `Conversation Started` event trigger. This ensures a proactive welcome message, increasing user engagement compared to waiting for a user to type.
* **Logic over Hallucination:** I implemented an **AI Task** to translate vague "moods" (e.g., "I'm feeling moody and dark") into concrete genres (e.g., "Post-Punk, Gothic Rock") before querying the API.
* **Edge Case Management:** To handle potential API timeouts, I set a default "Staff Pick" recommendation so the user journey is never interrupted.

---

## 🚀 Future Roadmap (The "TAM" Perspective)
If this were a production deployment for a high-value client, my next steps would be:
1.  **E-commerce Integration:** Connecting the `Inventory` table to a live Shopify backend for real-time purchasing.
2.  **Sentiment-Based Escalation:** Using Botpress logic to detect frustrated users and automatically escalate to a human agent via Zendesk or Intercom.
3.  **Analytics Tracking:** Implementing "Goal" nodes to track which recommendations lead to "Waitlist" sign-ups to calculate ROI for the client.

---

## 📂 Repository Structure
* `index.html`: The landing page hosted on GitHub Pages.
* `PROMPT.md`: The full System Prompt and Persona instructions.
* `Store_Policy.txt`: The source document used for the Knowledge Base.
