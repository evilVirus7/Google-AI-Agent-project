# 💰 AI Personal Finance and Investment Advisor Agent

An intelligent assistant built with the Google Agent Development Kit (ADK) designed to provide instant, data-driven financial guidance, leveraging specialized tools for investment inquiries and market data.

---

## 🖼️ Project Showcase

[Overview](https://github.com/evilVirus7/Google-AI-Agent-project/blob/master/Gemini_Generated_Image_edkjwcedkjwcedkj.png)



*Replace `assets/project_thumbnail.png` with the actual path and filename of your image once you upload it to your GitHub repository.*

---

## 🎯 Project Overview

This agent helps users with two main tasks:
1.  **Investment Inquiry:** Using a mock tool to provide data (price, performance, recommendation) for investments like AAPL, TSLA, and the S&P 500.
2.  **General Advice:** Providing conversational guidance on foundational financial topics, such as budgeting and emergency funds.

The agent uses the **Gemini 2.5 Flash Lite** model and is configured with explicit instructions to maintain a professional advisor persona and include a mandatory financial disclaimer.

---

## 🛠️ Setup and Installation

### Prerequisites

1.  **Python:** Ensure you have Python 3.10+ installed.
2.  **Gemini API Key:** Obtain a key from [Google AI Studio](https://makersuite.google.com/app/apikey).

### Local Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
    cd your-repo-name
    ```
    *(Remember to replace `https://github.com/your-username/your-repo-name.git` with your actual repository URL)*
2.  **Create and activate a virtual environment:**
    ```bash
    python -m venv google # Or simply 'python -m venv .venv'
    # On macOS/Linux
    source google/bin/activate
    # On Windows (Command Prompt)
    google\Scripts\activate.bat
    ```
3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
4.  **Set Environment Variable for API Key:**
    ```bash
    export GOOGLE_API_KEY="YOUR_API_KEY_HERE"
    # On Windows (Command Prompt)
    # set GOOGLE_API_KEY="YOUR_API_KEY_HERE"
    ```
    **Never commit your API key directly to version control.**

---

## 🚀 Running the Agent

### A. Via Python Notebook (Recommended)

1.  Ensure you have activated your virtual environment and set your `GOOGLE_API_KEY` as an environment variable (as described in "Local Installation").
2.  Open the `personal_finance_agent.ipynb` file in your preferred notebook environment (Jupyter Lab, VS Code, or Google Colab).
3.  Run the cells sequentially. The first executable cell (`!pip install -r requirements.txt`) will install dependencies in Colab, and the API key setup cell will guide you if the key is missing.
4.  Execute the test cells in **Section 3** to see the agent call its tools and provide advice.

### B. Via Google Colab Directly

Click the badge below to open and run the notebook directly in Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/your-username/your-repo-name/blob/main/personal_finance_agent.ipynb)

*(Remember to replace `https://colab.research.google.com/github/your-username/your-repo-name/blob/main/personal_finance_agent.ipynb` with the actual URL to your notebook on GitHub)*

**Important for Colab:** You will need to add your `GOOGLE_API_KEY` to Colab's secret manager (the key icon on the left sidebar) and name it `GOOGLE_API_KEY`.

---

## 📂 Project Structure

```
.
├── personal_finance_agent.ipynb  # The main agent code and testing notebook
├── requirements.txt              # Required Python packages
└── .gitignore                    # Files to ignore for Git
└── assets/                       # Folder for images and other assets
    └── project_thumbnail.png     # Your project showcase image
```

---

## 📝 Project Description

### Problem Statement
In today's complex financial world, individuals often struggle with **making informed investment and budgeting decisions**. Traditional financial advice is expensive, often delayed, and inaccessible to many. The problem we're solving is providing **instant, data-driven, and personalized-style financial guidance** for basic inquiries about stocks, funds, and personal finance concepts (like budgeting) in a single, accessible interface. This is important because it democratizes access to financial intelligence and empowers users to manage their money better.

### Why Agents?
Agents are the ideal solution because the problem requires **specialized reasoning and dynamic tool use**:

* **Tool Coordination:** A traditional LLM cannot access real-time or structured financial data. An agent can intelligently decide **when and how to call the specialized `get_investment_info` tool** to fetch data (like stock prices or volatility).
* **Structured Output & Persona:** The agent uses an **Instruction** (System Prompt) to adopt a "friendly and professional Personal Finance and Investment Advisor" persona, ensuring the final output is clearly formatted, includes the tool's data analysis, and critically, adds a **mandatory financial disclaimer**.
* **Complex Decision-Making:** The agent can differentiate between questions requiring tool use (e.g., "What about AAPL?") and those requiring internal knowledge (e.g., "How do I budget?"), providing a seamless, multi-domain advice experience.

### What You Created
The solution is a **Financial Advisor Agent** built using the Agent Development Kit (ADK), structured as a single specialized service:

The overall architecture is: **User Input → ADK Runner → LlmAgent → Tool Call (if needed) → Structured Response.**

* **LlmAgent:** The core of the system, configured with the `gemini-2.5-flash-lite` model for low latency and cost efficiency.
* **Instruction:** Explicitly guides the agent to use the tool, summarize findings, and include the necessary financial disclosure.
* **Tool:** The Python function `get_investment_info()` simulates a connection to a real-time financial API, providing structured data (price, performance, recommendation) based on the user's query.
* **Session Service:** Uses `InMemorySessionService` to maintain conversation context within a session, allowing for follow-up questions.

### Demo
The agent successfully handles two types of queries:

1.  **Tool-Based Inquiry (AAPL Stock):** The agent identifies the need for external data, calls the `get_investment_info("AAPL")` tool, integrates the returned data (e.g., price, +3.1% in 30 days), and presents a professional response including the mandatory disclaimer.
2.  **Internal Knowledge Inquiry (Budgeting):** The agent correctly determines no tool is needed and uses its base knowledge to provide step-by-step general advice on starting a personal budget.
3.  **Concept Inquiry (Emergency Fund):** The agent calls the tool to fetch a structured definition and recommendation on how to handle the fund.

### The Build
The project was created from scratch using the following tools and technologies:

* **Agent Framework:** **Google Agent Development Kit (ADK)**.
* **Model:** **Gemini 2.5 Flash Lite** via the `Gemini` model wrapper for its balance of speed and intelligence.
* **Tooling:** A Python `def` function, `get_investment_info`, decorated as a tool for the agent to call.
* **Execution:** The `Runner` class and `InMemorySessionService` were used for local, asynchronous testing.
* **Configuration:** Custom `HttpRetryOptions` were applied to the `Gemini` model for robust handling of transient API errors (e.g., 429 rate limits).

### If I had more time, this is what I'd do
1.  **Real-Time Data Integration:** Replace the mock `get_investment_info` tool with a live API connection (e.g., to an institutional data provider or financial API) for genuine real-time advice.
2.  **Long-Term Memory:** Implement **Vertex AI Memory Bank** to give the agent long-term memory, allowing it to remember a client's risk tolerance or portfolio size across different sessions.
3.  **Multi-Agent System (A2A):** Create a separate **"Risk Profiler Agent"** and integrate it via the **Agent2Agent (A2A) Protocol**. The Financial Advisor Agent would first call the remote Risk Profiler Agent to determine the user's risk score before giving a final recommendation on a stock, making the advice context-aware.
4.  **Deployment:** Deploy the fully featured agent to **Vertex AI Agent Engine** using the ADK CLI, making it a scalable, public service.

---

## 📜 License

This project is licensed under the MIT License - see the LICENSE file for details.
