# LLM Opinion Dynamics Simulation

A sociological simulation designed to observe **opinion dynamics** and **emergence** in artificial intelligence systems. It spins up a variable number of distinct AI agents (LLMs) that debate a topic over multiple rounds, while an **AI Judge** scores each statement on a 1–10 stance scale so you can visualize how opinions drift over time.

> **Project status note (2026-05-02):** The legacy **Anvil** frontend has been removed. The recommended interface is the **Streamlit dashboard**.

## Key Features
- **Multi-Agent Simulation:** Generates diverse personas and runs structured, multi-round debates.
- **Automated AI Judge:** Enforces strict JSON outputs to quantify qualitative text on a 1-to-10 stance scale.
- **Modular Advanced Scenarios:** Swap between a standard townhall and intervention/topology scenarios.
- **Streamlit Dashboard (Live & History):** Run new simulations and explore saved runs with interactive plots.
- **Isolated Run Logs:** Archives transcripts, prompts, and results into timestamped directories under `runs/`.

---

## Setup & Installation

### 1. Create a Virtual Environment and Install Dependencies
Ensure you have Python 3.10+ installed. It is recommended to use a virtual environment:
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 2. Configure API Keys
This project uses Groq API access via the OpenAI compatibility layer. Create a `.env` file in the root directory and add your key(s):
```env
# single key fallback
GROQ_API_KEY="your_api_key_here"

# OR load-balanced multi-key configuration
GROQ_API_KEY_1="your_first_key"
GROQ_API_KEY_2="your_second_key"
...
GROQ_API_KEY_20="your_twentieth_key"
```

> If you previously used the Anvil Uplink integration, note that `anvil-uplink` is no longer required.

---

## How to Run

### Streamlit Dashboard (Recommended)
To launch the primary interactive dashboard locally:
```bash
streamlit run app.py
```
This will open the dashboard in your browser (typically `http://localhost:8501`). Use the sidebar to configure the number of agents, rounds, and debate topic.

### Reviewing Output Logs & History
When a simulation finishes, it creates a folder in `runs/` containing (at minimum):
- `simulation.log`: raw transcript / telemetry
- `results.csv`: flattened dataset containing `Statement_Text` and the evaluator JSON ratings

In the Streamlit UI, use **View Saved Runs** to load legacy runs and restore plots.

---

## Analysis Artifacts (Optional)
Recent commits added additional **mathematical inference / analysis artifacts** to the repository (e.g., `result_analysis.ipynb` and example CSV outputs under `simulation_csvs/`). These are intended for post-run exploration and documentation of scenario outcomes.
