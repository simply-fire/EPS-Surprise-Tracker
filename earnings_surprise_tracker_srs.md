# 📘 Software Requirements Specification (SRS)

## 💼 Project Title:
**Real-Time Earnings Surprise Tracker (Python + Streamlit)**

---

## 📌 Objective:
Design and develop a mini-project that fetches, analyzes, and displays quarterly earnings results from public companies in real time, highlighting significant EPS surprises, and providing a clean UI for monitoring. The goal is to reinforce Python (especially OOP and `requests`) in a realistic fintech automation context.

---

## 📈 Scope (For 3–4 Hour MVP Build)

### ✅ Core Features (Feasible for MVP):
1. **Fetch Latest Earnings Results**
   - Use `requests` to pull earnings data from a public API or web page (e.g., Yahoo Finance, MarketBeat, Nasdaq).
   - Data includes: Ticker, Reported EPS, Estimated EPS, Surprise % (if available), Result Date.

2. **Calculate EPS Surprise (If Raw Values Only)**
   - Formula: `(Reported EPS - Estimated EPS) / Estimated EPS * 100`
   - Filter companies with surprise above or below threshold (e.g., ±15%).

3. **Object-Oriented Structure**
   - Use classes for:
     - `EarningsEvent`: Represents one company's result with attributes like ticker, date, EPS data, and methods to calculate surprise.
     - `EarningsFetcher`: Handles all HTTP requests and parsing logic to retrieve earnings data.
     - `EarningsProcessor`: Filters and structures the data for frontend display.
     - `EarningsTrackerApp`: Manages user interaction and Streamlit rendering logic.

4. **Streamlit UI (Minimal)**
   - Table view of surprise events
   - Slider or input field for setting surprise % threshold
   - Refresh button to re-fetch and re-process data

5. **Clean Coding Practices**
   - Docstrings, typing hints, modular design, separation of concerns, and adherence to PEP8

### ❌ Excluded from MVP (For later expansion):
- Historical trend charts or price impact analysis
- Telegram/email alerts
- Caching or persistent storage
- Scheduled background tasks

---

## 🔄 Application Flow (MVP)

1. **User opens Streamlit app**
2. `EarningsTrackerApp` initializes and creates frontend layout
3. On refresh or load:
   - `EarningsFetcher` fetches the latest data (API or scraping)
   - `EarningsProcessor` parses raw data and filters based on threshold
   - Each entry is instantiated as an `EarningsEvent`
4. Filtered data is passed to `EarningsTrackerApp`, which renders it in the UI
5. User can adjust threshold slider → triggers re-filtering via `EarningsProcessor`
6. User can click refresh → re-triggers fetch and update loop

---

## 🧱 Functional Requirements

| ID  | Feature                            | Description                                                                 |
|-----|------------------------------------|-----------------------------------------------------------------------------|
| F1  | Fetch earnings data                | Pull latest earnings data using public APIs or web scraping                 |
| F2  | Calculate surprise %               | Compute percentage difference between reported and estimated EPS           |
| F3  | Filter significant results         | Filter entries based on surprise threshold                                 |
| F4  | Display results in Streamlit       | Tabular view with filter slider and refresh button                         |
| F5  | OOP structure                      | Maintain clean class-based architecture                                    |
| F6  | Modular flow                       | Distinct separation between data fetching, processing, and rendering       |

---

## ⚙️ Non-Functional Requirements

- **Performance**: MVP should work with <200 records in <5 seconds.
- **Readability**: Code must be easy to understand for review/interview.
- **Extensibility**: Modular design should allow adding alerts and pricing data later.
- **Responsiveness**: Streamlit app must update with minimal delay upon interaction.

---

## 📌 Tools and Tech Stack

| Category         | Tool                 |
|------------------|----------------------|
| Language         | Python 3.x           |
| Libraries        | `requests`, `pandas`, `streamlit` |
| Optional Parsing | `BeautifulSoup` or `re` if scraping required |
| IDE              | VS Code / PyCharm    |
| Linter/Formatter | `black`, `flake8`    |

---

## 🔭 Extended Vision (Future Scope)

> Once the MVP is working and you have more time, evolve the tracker into a full-fledged **event-driven insights tool**:

### 🚀 Next-Level Features:
- **Historical Reaction Tracker**
  - Fetch stock prices before/after earnings to analyze price reactions
- **Sector-wise Breakdown**
  - Add dropdown for filtering by sector or industry
- **Alert System**
  - Integrate Telegram Bot / Email to notify about high-impact surprises
- **Backtesting Tool**
  - Store data and run simulations: e.g., "What if I bought after every 20% surprise?"
- **Machine Learning**
  - Predict surprise likelihood based on historical patterns (as seen in Brodyu’s repo)
- **Web UI Upgrade**
  - Port to a fully styled **Next.js** dashboard or integrate with a backend like FastAPI

---

## 📦 Deliverables
- Python script/module (`main.py`, `tracker.py`, etc.)
- Streamlit app (`app.py`)
- README with setup instructions
- Sample output screenshot (optional)

---

## 🧠 Interview/Revision Concepts Covered
- Python OOP (Classes, Inheritance, Encapsulation)
- HTTP requests (`requests` module)
- Data wrangling (`pandas`)
- Streamlit UI creation
- Exception handling, logging, docstrings
- Real-world automation logic

---

## ✅ Summary
This project is practical, unique, and interview-ready. It gives you:
- Solid hands-on with core Python automation tools
- Something more insightful than a stock price viewer
- A clean MVP with strong room for growth

You’ll not only learn, but also build something useful enough to deploy or showcase.

---

