# FinSight-Multi-Agent-AI-Financial-Research-System
Architected a multi-agent AI workflow using Python and FastAPI to automate quantitative analysis and financial research for equities, including the Indian stock market. Implemented Retrieval-Augmented Generation (RAG) to fetch live market news via external APIs, grounding the LLM in real-time events to eliminate hallucination.
Designed a central orchestrator that coordinates specialized LLM personas (Fundamental, Technical, Sentiment) to debate conflicting financial signals and generate comprehensive investment reports.
Integrated deterministic tool-calling, enabling the AI to utilize Pandas and NumPy to compute precise technical indicators (RSI, MACD) rather than relying on generative approximations.
Developed an autonomous financial research platform that synthesizes fundamental valuation metrics, technical momentum, and behavioral market sentiment into a single unified thesis.

Engineered a data pipeline using yfinance to ingest historical price data and balance sheet metrics, allowing the system to evaluate value investing frameworks and revenue growth.

Built a deterministic technical analysis engine using Python to calculate moving averages and MACD crossovers, feeding mathematically accurate data into a generative AI model for interpretation.

Here is a professional, FAANG-ready `README.md` tailored for your repository. It clearly explains the architecture, emphasizes the agentic AI design, and makes it easy for recruiters or other developers to understand your engineering decisions.

You can copy and paste everything below the line directly into your `README.md` file.

---

# FinSight: Multi-Agent AI Financial Research System 📊🤖

FinSight is an autonomous, agentic AI platform designed to perform comprehensive quantitative and qualitative equity research. By leveraging a multi-agent architecture, the system delegates specific analytical tasks—fundamental analysis, technical analysis, and sentiment evaluation—to specialized AI personas, synthesizing their findings into a cohesive, institutional-grade investment thesis.

The system natively supports both global equities and Indian stock markets (NSE/BSE), applying rigorous analytical frameworks, including traditional value investing principles, to evaluate assets.

## 🌟 Key Features

* **Multi-Agent Orchestration:** Utilizes a supervisor "Orchestrator" agent to manage and synthesize the outputs of specialized sub-agents (Technical, Fundamental, and Sentiment), resolving conflicting market signals.
* **Retrieval-Augmented Generation (RAG):** Eliminates LLM hallucination by fetching and injecting live market news, ensuring the Sentiment Agent evaluates real-time market catalysts.
* **Deterministic Tool Calling:** Prevents mathematical hallucinations by forcing the AI to call deterministic Python functions (using Pandas/NumPy) to calculate exact technical indicators (RSI, MACD, SMAs) before reasoning about them.
* **Value Investing & Fundamentals:** The Fundamental Agent evaluates core solvency metrics, revenue growth, and valuation multiples to assess the intrinsic value and margin of safety.
* **Full-Stack Architecture:** Features a robust FastAPI backend serving intelligent endpoints to a responsive React frontend dashboard.

## 🏗️ System Architecture

```text
[ User Input ] ---> [ Ticker Resolution ] ---> [ Data Collector (yfinance) ]
                                                      |
        +---------------------------------------------+---------------------------------------------+
        |                                             |                                             |
[ Technical Agent ]                           [ Fundamental Agent ]                         [ Sentiment Agent ]
Uses pandas to calculate:                     Evaluates:                                    Uses RAG to analyze:
- Moving Averages (SMA)                       - P/E & P/B Ratios                            - Live News Headlines
- RSI & MACD                                  - Debt-to-Equity & Margins                    - Market Catalysts
        |                                             |                                             |
        +---------------------------------------------+---------------------------------------------+
                                                      |
                                          [ Master Orchestrator ]
                                   (Debates signals, synthesizes thesis)
                                                      |
                                          [ Final Research Report ]

```

## 🛠️ Tech Stack

* **Backend:** Python, FastAPI, Uvicorn
* **AI/LLM:** Google Gemini 2.5 Flash
* **Data Processing:** Pandas, NumPy, yfinance
* **Frontend:** React.js, Node.js

## 📂 Directory Structure

* `agents/`: Contains the specialized LLM personas (`orchestrator.py`, `fundamental.py`, `technical.py`, `sentiment.py`) and the `data_collector.py` for API ingestion.
* `tools/`: Deterministic scripts that the agents call for factual data (`indicators.py` for math, `name_resolver.py` for ticker mapping).
* `frontend/`: The React web application serving the user interface.
* `main.py` / `app.py`: FastAPI application entry points and API route definitions.

## 🚀 Installation & Setup

### 1. Backend Setup (Python/FastAPI)

Clone the repository and set up a virtual environment:

```bash
git clone https://github.com/yourusername/finsight.git
cd finsight
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`

```

Install backend dependencies:

```bash
pip install -r requirements.txt

```

Set your API key as an environment variable:

```bash
export GEMINI_API_KEY="your_api_key_here"  # On Windows use `set GEMINI_API_KEY=your_api_key_here`

```

Start the backend server:

```bash
python main.py  # Or uvicorn app:app --reload depending on your entry point

```

### 2. Frontend Setup (React)

Open a new terminal window and navigate to the frontend directory:

```bash
cd finsight/frontend
npm install

```

Start the React development server:

```bash
npm start

```

## 💻 Usage

Once both servers are running, access the dashboard via `http://localhost:3000`. Enter a company name (e.g., "Tata Motors" or "Nvidia") or a specific ticker (e.g., "TATAMOTORS.NS" or "NVDA").

The system will asynchronously gather data, route it through the specialized agents, and render a comprehensive investment breakdown.

## 🧠 Engineering Challenges Solved

* **Mathematical Inaccuracy in LLMs:** Bypassed by abstracting indicator calculations into a standalone `indicators.py` tool. The LLM only receives the final calculated integers/floats.
* **Outdated Knowledge Cutoffs:** Solved by utilizing `yfinance` to fetch real-time news data and injecting it into the Sentiment Agent's context window (RAG).
* **Conflicting Market Signals:** Addressed via the `orchestrator.py`, which acts as a Chief Investment Officer (CIO) to weigh bullish technicals against bearish fundamentals (or vice versa) to make a definitive, holistic call.
