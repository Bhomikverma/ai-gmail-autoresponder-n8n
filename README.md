# ai-gmail-autoresponder-n8n
AI-Powered Gmail Auto-Responder using n8n, LLMs, and Pinecone — handles customer support emails with smart replies.

This project showcases two powerful AI automation workflows built with **n8n**, designed to classify incoming Gmail messages and auto-reply using **LLMs (via OpenRouter)** and **vector search with Pinecone**.

Both workflows intelligently respond to **customer support emails**, but differ in control vs autonomy.

📺 **[Watch the Demo Video:] (https://drive.google.com/file/d/1Rx07MF_qM_Sg5L8VEXKn2suuQuEogwdM/view?usp=sharing)(#)** 

---

## 🧠 How the Workflow Works

### 1. Email Ingestion
- Triggered every minute via **Gmail Trigger**
- Fetches the latest incoming email

### 2. Email Classification
- The email content is sent to a **Text Classifier node**
- Classification is powered by an **LLM**
- If the email is labeled as a **customer support query**, it proceeds further

---

## 🔷 Workflow 1: AI Agent (Autonomous)

An **AI Agent** handles the response generation:

1. **System Prompt**, user message, and **Tool Descriptions** are passed to the agent
2. The agent uses an LLM to decide if additional knowledge is needed
3. If yes, it queries **Pinecone** with embeddings to fetch relevant context
4. The LLM uses these chunks to craft a smart, contextual reply
5. The response is labeled and sent via Gmail to the original sender

> ✅ Autonomous  
> ⚠️ But may skip tool usage or context retrieval occasionally

---

## 🔶 Workflow 2: AI Workflow (Manual, Controlled)

A more deterministic approach where you control the logic:

1. Email is classified like before
2. Query is sent **directly to Pinecone**
3. Retrieved chunks go through a **Filter node** (based on similarity score)
4. Filtered chunks are aggregated and passed to an **LLM Chain**
5. The LLM crafts the reply using this exact context
6. Final reply is labeled and sent via Gmail

> ✅ Higher control, predictable logic  
> 🚫 No agent-level tool decision involved

---

## 🔧 Tech Stack

- **n8n** (Low-code automation)
- **OpenRouter** (LLM access)
- **Pinecone** (Vector database)
- **HuggingFace Embeddings**
- **Gmail API**
- **LLM Agents & Chains**

---

## 📁 Project Structure

| Node/Module         | Purpose                                  |
|---------------------|------------------------------------------|
| `Gmail Trigger`     | Detects new incoming emails              |
| `Text Classifier`   | LLM-powered email intent detection       |
| `AI Agent`          | Handles dynamic tool usage + reasoning   |
| `Pinecone`          | Vector store for past support knowledge  |
| `Filter`            | Keeps only high-relevance chunks         |
| `Basic LLM Chain`   | Converts context into a response         |
| `Gmail Reply`       | Sends back auto-generated message        |

---

## 🚀 Use Cases

- Customer support automation  
- Helpdesk query classification  
- Smart reply bots with memory/context  
- AI assistant backend logic

---

## 📹 Demo

🔗 [Click here to watch the full workflow demo:](https://drive.google.com/file/d/1Rx07MF_qM_Sg5L8VEXKn2suuQuEogwdM/view?usp=sharing)(#)  
(Add your video link here — YouTube, Loom, or hosted .mp4)

---

## 💬 Author

Built by **www.linkedin.com/in/
bhomik-verma** — an AI automation enthusiast using no-code + LLMs.  
Feel free to connect or collaborate!

---

