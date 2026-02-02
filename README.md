# 🎧 Mile End Records | AI Music Concierge (Isobel)

> **TSE Case Study Assignment** > **Candidate:** Miguel Somarriba
> **Target Role:** Technical Support Engineer 
> **Platform:** Botpress
> 
---

## 📍 Project Overview
This project features **Isobel**, a custom AI assistant for *Mile End Records*, a boutique vinyl shop based in Montreal. This solution demonstrates a hybrid data sources, combining local store inventory with global music metadata to provide a specialized "Concierge" experience that mirrors the expertise of a physical record store employee.

### 🔗 Live Links
* **Live Deployment:** [INSERT YOUR GITHUB PAGES URL HERE]
* **Botpress Studio:** [INSERT YOUR BOTPRESS PUBLIC LINK HERE]

---

## 🛠️ Technical Architecture

Isobel utilizes 3 main sources as it's Knowledge Base

| Pillar | Source | Purpose |
| :--- | :--- | :--- |
| **Structured** | **Botpress Tables** | Manages real-time **Inventory** (Artist, Album, Price, and Stock status). |
| **Unstructured** | **FAQ PDF** | Provides "Ground Truth" for **Store Policies**, vinyl grading (VG+, M), and care tips. |
| **Dynamic** | **TheAudioDB API** | Fetches live artist biographies and album metadata for personalized **Recommendations**. |

---

## ✨ Key Features

### 1. Context-Aware "Mile End" Persona
Isobel is designed with a "Record Store Employee" persona—knowledgeable, inclusive, and locally-aware. She uses session variables to track the user's name and genre preferences, ensuring the conversation feels like a high-touch human interaction rather than a transactional script.

### 2. Global Music Discovery (API Integration)
Using an **Execute Code** block, the bot queries **TheAudioDB API** to provide deep-dive recommendations.
I implemented robust error handling to manage "Artist Not Found" scenarios and API timeouts. In the event of an API failure, the bot provides a curated "Staff Pick" fallback to maintain a seamless user journey.

### 3. Automated Ticket Deflection (KB)
By integrating a specialized **FAQ PDF** into the Botpress Knowledge Base, Isobel answers common support queries (e.g., *"What is your return policy?"* or *"What does a VG+ grading mean?"*) instantly. This demonstrates the platform's ability to reduce low-level support volume for human agents.

---

## 🧠 Technical Decisions & Troubleshooting

* **Proactive Logic:** I utilized the `Conversation Started` trigger to ensure an immediate, warm welcome. The bot captures the user's name early to personalize all subsequent responses from the Tables and API.
* **Optimized Search:** For the structured data queries, I used **Find Records** logic that handles partial matches in the Inventory table (e.g., a search for "Radiohead" will correctly identify "Radiohead - Kid A" in stock).
* **API Resilience:** During development, I prioritized the use of `try/catch` blocks within the Javascript Execute Code cards. This ensures that even if the external API (TheAudioDB) is unreachable, the bot remains functional and helpful.

---

## 📂 Repository Structure
* `index.html`: The landing page hosted on GitHub Pages.
* `Instructions.md`: The full System Prompt and Persona instructions.
* `FAQ.pdf`: The source document used for the Knowledge Base.
