Bitcoin AML Monitor — Real-Time Crypto Transaction Risk Analysis

A system that analyses live Bitcoin blockchain transactions in real time and flags them for Anti-Money Laundering (AML) risk — using the same rule-based approach that real crypto-compliance firms (like Chainalysis and Elliptic) build on.

Unlike a demo running on sample data, this pulls genuine transactions happening on the Bitcoin network right now and scores each one for suspicious activity.

🎥 Demo & Live Links
▶️ Video walkthrough (V2 — Structuring Detection): https://youtu.be/lnmPTF57m9s
🌐 Live dashboard: https://vamsikrishna960.github.io/Bitcoin-AML-Monitor/
💡 What It Does

Every incoming Bitcoin transaction is analysed against key crypto AML red flags:

High-value transfers — large "whale" movements worth monitoring
Unusually high fees — can signal urgency to move funds quickly
Many outputs — possible layering or splitting to obscure the money trail
Dust amounts — tiny transfers sometimes used for trail obfuscation

Each transaction is scored LOW, MEDIUM, or HIGH risk, with a clear reason explaining which red flags were detected. An LLM then generates a professional analysis for flagged transactions.

🆕 Version 2 — Structuring Detection

V1 scored each transaction individually — which missed a key laundering pattern: structuring (splitting money into many small transfers to one address, where each looks harmless on its own).

V2 adds aggregation detection:

Groups transactions by receiving address
Counts how many transfers each address receives
Flags addresses receiving an unusual number of transactions (POSSIBLE STRUCTURING)
Feeds this pattern back into the risk score

Result on live data: V2 flagged a single wallet address that received 62 tiny transactions — a structuring pattern that single-transaction scoring would have completely ignored.

🛠️ How It's Built
Stage	What Happens
1. Data ingestion	Pulls live unconfirmed transactions from the public Blockchain.com API
2. Data cleaning	Extracts the useful fields (hash, amount, fee, outputs, receiver) and converts satoshis → BTC
3. Structuring detection	Groups by receiver address and flags repeated-transfer patterns
4. Risk scoring	Applies AML rules to score each transaction and explain the flags
5. AI analysis	An LLM generates professional analysis for flagged transactions
6. Live dashboard	Results are displayed on a real-time dashboard

Pipeline:

Live Bitcoin API → clean data → structuring detection → risk scoring → AI analysis → live dashboard
🔎 AML Concepts Applied
Structuring / Smurfing — splitting funds into many small amounts to avoid detection thresholds
Layering — moving funds through multiple outputs to obscure their origin
Whale monitoring — tracking unusually large transfers
Aggregation detection — analysing patterns across transactions, not just individual ones
Risk combination — risk compounds when multiple red flags appear together
🛠️ Tech Stack
n8n — no-code workflow automation
Blockchain.com API — live Bitcoin transaction data
Groq LLM — professional AML analysis
JavaScript — data extraction, structuring detection, and rule-based risk scoring
GitHub Pages — live dashboard hosting
🎯 Why I Built This

I'm an MSc Computing Science student working toward a career as an AI Product Manager. This project demonstrates the ability to work with real, live data — and the real work of product management: not just building a feature, but noticing what it fails to catch and iterating to close the gap.

👤 Author

Gali Vamsi Krishna

LinkedIn: https://linkedin.com/in/vamsi-krishna-jun302000
GitHub: https://github.com/Vamsikrishna960
