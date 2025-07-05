# 🛠️ Technical Design Document

## 📌 Project Name:

**Real-Time Earnings Surprise Tracker**

---

## 🔍 Project Overview

This project aims to build a minimal but functional frontend application in Streamlit to track and filter real-time earnings results. It fetches data from the **Finnhub API**, processes it using Python’s OOP principles, and displays companies with significant earnings surprises to the user.

The goal is to reinforce Python automation, API integration, and frontend interfacing in a real-world, finance-relevant context.

---

## 🧰 Technology Stack & Justification

| Layer          | Technology                 | Justification                            |
| -------------- | -------------------------- | ---------------------------------------- |
| UI Layer       | Streamlit                  | Fast, declarative UI with Python         |
| HTTP Requests  | `requests`                 | Clean, simple REST API consumption       |
| Data Modeling  | OOP Classes                | Separation of concern, maintainability   |
| Data Filtering | `pandas`                   | Tabular filtering and manipulation       |
| Data Source    | Finnhub.io API (Free Tier) | Structured earnings data with surprise % |
| Future Data    | `yfinance`, SQLite         | Price post-result, local caching         |

---

## 🧱 Folder Structure

```
earnings_tracker/
│
├── main.py                 # Entry point to launch Streamlit
├── tracker_app.py          # Streamlit app logic
├── fetcher.py              # Finnhub API handling class
├── models.py               # EarningsEvent class
├── utils.py                # Helper functions (e.g. filtering, formatting)
├── .env / config.py        # Secrets, API key storage (excluded from git)
├── requirements.txt        # Python dependencies
└── README.md               # Setup + usage instructions
```

---

## 🧩 Component Responsibilities

### 🔹 EarningsFetcher (API Layer)

- Responsible for hitting the Finnhub `/earnings` endpoint
- Accepts a list of stock tickers
- Parses API response and returns raw structured data (list of dicts or objects)

### 🔹 EarningsEvent (Model Layer)

- Represents one earnings report
- Fields: `symbol`, `period`, `estimate`, `actual`, `surprise`, `surprise_percent`
- Methods:
  - `calculate_surprise()` (if needed)
  - `was_significant(threshold: float)`

### 🔹 EarningsProcessor (Business Logic Layer)

- Accepts raw event list
- Applies threshold filters
- Sorts and prepares for frontend display

### 🔹 TrackerApp (UI Layer)

- Renders Streamlit interface
- Responds to user inputs like refresh and threshold slider
- Displays earnings in tabular and optional chart formats

---

## 🗂️ Milestones / Timeline

| Milestone ID  | Feature                        | Est. Time | Dependencies |
| ------------- | ------------------------------ | --------- | ------------ |
| M1            | Setup Finnhub API & key        | 15 mins   | None         |
| M2            | Build `EarningsFetcher` class  | 45 mins   | M1           |
| M3            | Build `EarningsEvent` model    | 30 mins   | M2           |
| M4            | Add filtering logic            | 30 mins   | M3           |
| M5            | Build Streamlit UI layout      | 45 mins   | M3, M4       |
| M6            | Integrate refresh & slider     | 30 mins   | M5           |
| M7            | Add sorting & color formatting | 30 mins   | M6           |
| M8 (optional) | Add charts or bar graphs       | 30 mins   | M6           |

---

## 🔁 Application Flow

```
User -> Streamlit UI -> TrackerApp
                         ↓
                    EarningsFetcher (API)
                         ↓
                 List[EarningsEvent] objects
                         ↓
              EarningsProcessor (filtering)
                         ↓
               Table / Chart on Streamlit UI
```

---

## 🧪 Testing Plan

| Component         | Test Case                            | Type        |
| ----------------- | ------------------------------------ | ----------- |
| `EarningsFetcher` | Handles invalid API key or timeout   | Unit Test   |
| `EarningsEvent`   | Correct calculation of surprise %    | Unit Test   |
| `Processor`       | Filters correctly based on threshold | Unit Test   |
| `Streamlit App`   | UI loads and refresh works with data | Manual Test |

---

## 📦 Deliverables

- Streamlit web app (MVP)
- Fully OOP Python backend
- `README.md` for usage and deployment
- `.env.example` template for API key config
- Bonus: Screenshots of working UI or deployment link

---

## ✅ Summary

This document guides the development phase by defining how components will be built and integrated. Combined with the SRS, it ensures that implementation stays modular, testable, and ready for future upgrades.

The next steps would be to scaffold the class files and connect the UI logic into one cohesive tool.

