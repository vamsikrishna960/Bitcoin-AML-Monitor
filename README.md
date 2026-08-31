# Bitcoin AML Monitor — Real-Time Crypto Transaction Risk Analysis

A system that analyses live Bitcoin blockchain transactions in real time and flags them for Anti-Money Laundering (AML) risk — using the same rule-based approach that real crypto-compliance firms (like Chainalysis and Elliptic) build on.

Unlike a demo running on sample data, this pulls genuine transactions happening on the Bitcoin network right now and scores each one for suspicious activity.

💡 What It Does

Every incoming Bitcoin transaction is analysed against key crypto AML red flags:

High-value transfers — large "whale" movements worth monitoring
Unusually high fees — can signal urgency to move funds quickly
Many outputs — possible layering or splitting to obscure the money trail
Dust amounts — tiny transfers sometimes used for trail obfuscation

Each transaction is scored LOW, MEDIUM, or HIGH risk, with a clear reason explaining which red flags were detected.

🛠️ How It's Built
Stage	What Happens
1. Data ingestion	Pulls live unconfirmed transactions from the public Blockchain.com API
2. Data cleaning	Extracts the useful fields (hash, amount, fee, outputs, receiver) and converts satoshis → BTC
3. Risk scoring	Applies AML rules to score each transaction and explain the flags

Pipeline:

Live Bitcoin API → n8n → clean & structure data → AML risk scoring → risk level + reasons
🔎 AML Concepts Applied
Structuring / Smurfing — splitting funds into many small amounts to avoid detection thresholds
Layering — moving funds through multiple outputs to obscure their origin
Whale monitoring — tracking unusually large transfers
Risk combination — risk compounds when multiple red flags appear together, rather than relying on any single factor
🧪 Example Result

A real transaction of ~49 BTC with 7 outputs and a high fee was correctly flagged HIGH RISK — combining three red flags (high-value transfer, high fee, and many outputs indicating possible layering).

🛠️ Tech Stack
n8n — no-code workflow automation
Blockchain.com API — live Bitcoin transaction data
JavaScript — data extraction and rule-based risk scoring
🎯 Why I Built This

I'm an MSc Computing Science student working toward a career as an AI Product Manager. This project demonstrates the ability to work with real, live data — not just samples — and to translate domain knowledge (AML red flags) into a working risk-detection system.

🚀 What's Next
Add an LLM layer to generate natural-language risk explanations
Store results and surface them on a live dashboard
Expand the rule set with additional crypto AML patterns
👤 Author

Gali Vamsi Krishna

LinkedIn: https://linkedin.com/in/vamsi-krishna-jun302000
GitHub: https://github.com/Vamsikrishna960
