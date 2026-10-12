🛡️ UPI Shield AI

AI-Driven Scam Pattern Recognition for Digital Payments

Team RSG | Amazon AI Cyber Security Hackathon — Round 1

UPI Shield AI is a privacy-first prototype designed to identify potentially suspicious transaction patterns using rule-based detection, machine learning anomaly detection, and a hybrid risk assessment approach. It provides interpretable risk indicators to support human review.

«Project status: Prototype for hackathon demonstration. Uses synthetic data and is not connected to live UPI or banking systems.»

---

📌 Table of Contents

- "Problem Statement" (#-problem-statement)
- "Our Solution" (#-our-solution)
- "Key Features" (#-key-features)
- "System Architecture" (#-system-architecture)
- "Technology Stack" (#-technology-stack)
- "Detection Methodology" (#-detection-methodology)
- "Dataset" (#-dataset)
- "Evaluation Results" (#-evaluation-results)
- "Demo Workflow" (#-demo-workflow)
- "Getting Started" (#-getting-started)
- "Repository Structure" (#-repository-structure)
- "Privacy and Security" (#-privacy-and-security)
- "Limitations and Future Improvements" (#-limitations-and-future-improvements)
- "Team RSG" (#-team-rsg)
- "Documentation" (#-documentation)

🚨 Problem Statement

Digital payment systems provide convenient, fast transactions, but users may encounter scams involving unusual transaction amounts, rapid transaction bursts, unfamiliar payees, and other potentially suspicious patterns.

Simple detection rules may miss unfamiliar patterns, while machine learning models can identify anomalies that differ from expected activity. However, an anomaly does not automatically mean a transaction is fraudulent.

Our challenge: Build a prototype that identifies potentially suspicious transaction activity, combines complementary detection approaches, and explains why an event may require attention.

💡 Our Solution

UPI Shield AI combines three components:

1. Rule-based detection: Evaluates transaction features against predefined risk indicators.
2. Isolation Forest: Identifies anomalous activity relative to the reference data used for training.
3. Hybrid risk assessment: Combines rule-based signals and the anomaly indicator to produce an overall risk assessment with supporting reasons.

The prototype is intended to assist human review. It does not independently establish fraud, predict a guaranteed scam outcome, or block payments.

✨ Key Features

- Hybrid detection: Combines rule-based checks with machine learning anomaly detection.
- Risk classification: Supports LOW, MEDIUM, and HIGH risk categories.
- Explainable indicators: Provides reasons associated with detected patterns.
- Synthetic data: Demonstrates the workflow without requiring real customer transactions.
- Interactive demonstration: Includes a Gradio-based interface in the notebook, if the corresponding setup cell runs successfully.
- Review workflow: Supports reviewing flagged events and inspecting their risk assessments.
- Export support: Includes CSV/JSON reporting functionality in the notebook.
- Basic validation: Includes prototype checks for representative normal and suspicious scenarios.
- Privacy-first design: Avoids requiring real UPI credentials or live payment integration.

🏗️ System Architecture

flowchart TD
    A["Synthetic Transaction Data"] --> B["Feature Preparation"]
    B --> C["Rule-Based Detection"]
    B --> D["Isolation Forest"]
    C --> E["Hybrid Risk Assessment"]
    D --> E
    E --> F["Risk Level and Explanation"]
    F --> G["Review Queue"]
    F --> H["CSV / JSON Reports"]
    F --> I["Interactive Demo"]

Processing flow

1. Generate or enter synthetic transaction features.
2. Prepare the features for the detection components.
3. Calculate rule-based risk indicators.
4. evaluate anomalous activity using Isolation Forest.
5. Combine the outputs into a hybrid assessment.
6. Display the risk category and available explanations.
7. Allow a reviewer to inspect flagged events and export supported reports.

🧰 Technology Stack

Technology| Purpose
Python| Core implementation
Pandas| Tabular data handling
NumPy| Numerical operations
Scikit-learn| Isolation Forest and evaluation metrics
Matplotlib / Seaborn| Exploratory data visualizations, where used
Gradio| Interactive demonstration interface
Google Colab / Jupyter Notebook| Development and execution environment
GitHub| Version control and project documentation

The exact libraries and components available depend on the notebook cells and installed dependencies in the repository.

🔍 Detection Methodology

1. Rule-Based Detection

The rule-based component evaluates transaction features such as:

- Transaction amount relative to a typical amount.
- Number of transactions within a short time window.
- Whether the payee is new or unfamiliar.

The rules assign risk indicators based on configured conditions. Their effectiveness depends on the quality of the rules and the data being assessed.

2. Machine Learning Anomaly Detection

The prototype uses Isolation Forest, an unsupervised anomaly detection algorithm.

It identifies records that appear unusual relative to the reference data used to fit the model. An anomaly score or prediction is not the same as a calibrated probability of fraud.

3. Hybrid Risk Assessment

The hybrid component uses rule-based and machine learning signals to derive an overall risk assessment.

The prototype exposes fields such as:

- "rule_score"
- "rule_risk"
- "ml_anomaly"
- "final_risk"
- "reasons"

The precise assessment depends on the implemented scoring rules and model output. These fields are risk indicators for demonstration, not a definitive fraud verdict.

🧪 Dataset

UPI Shield AI uses synthetic transaction data for development and demonstration.

The notebook generates a dataset of 300 records using a fixed random seed for reproducibility. The generated features include:

Feature| Description
"transaction_id"| Synthetic transaction identifier
"amount"| Transaction amount
"typical_amount"| Reference amount used for comparison
"tx_count_10m"| Number of transactions in a ten-minute window
"new_payee"| Indicator for a new payee, where used
"label"| Synthetic label used for development and evaluation

The notebook's synthetic labels and feature-generation rules are designed for experimentation. They do not represent a verified sample of real-world fraud.

Important: Synthetic data can make detection appear easier than it would be in practice. Results must not be interpreted as evidence of real-world UPI scam detection performance.

📊 Evaluation Results

The current evaluation notes include a held-out synthetic test set of 90 events for the Isolation Forest assessment.

Isolation Forest — held-out synthetic evaluation

Metric| Result
True negatives (TN)| 71
False positives (FP)| 5
False negatives (FN)| 0
True positives (TP)| 14
Accuracy| 94.44%
Precision| 73.68%
Recall| 100.00%
F1-score| 84.85%
False-positive rate| 6.58%

These values correspond to 76 normal and 14 suspicious events in the test set.

The rule-based component has also produced 100% metrics on the synthetic evaluation used during development. Because synthetic labels may be closely related to the patterns used by the rules, this result should not be interpreted as real-world validation.

Evaluation limitations:

- The test data is synthetic, not a representative sample of actual UPI transactions.
- The evaluation does not establish performance against real scam campaigns.
- Real-world precision, recall, and false-positive rates may differ substantially.
- The anomaly indicator is not a probability that a transaction is fraudulent.
- These metrics describe a prototype evaluation, not production readiness.

🖥️ Demo Workflow

The intended demonstration workflow is:

1. Open the project notebook in Google Colab.
2. Run the notebook cells in order.
3. Generate the synthetic dataset and inspect its features.
4. Execute the rule-based detector and Isolation Forest.
5. Review the hybrid risk assessments and explanations.
6. Run the prototype checks.
7. Launch the Gradio interface if its setup cell is available and completes successfully.
8. Inspect flagged records and try the supported report-export options.

The demonstration uses synthetic examples and does not initiate payments or contact banking systems.

🚀 Getting Started

Option 1: Run in Google Colab

1. Open the "UPI Shield AI repository" (https://github.com/silambarasanc199-jpg/upi-shield-ai).
2. Open "upi_shield_ai.ipynb".
3. Open the notebook in Google Colab.
4. Review any installation instructions in the notebook.
5. Select Runtime → Run all.
6. Follow the outputs to explore the dataset, detection results, tests, and interactive demo.

If the notebook uses a Gradio launch cell, follow its output to open the demo interface.

Option 2: Clone the repository

git clone https://github.com/silambarasanc199-jpg/upi-shield-ai.git
cd upi-shield-ai

Install the dependencies required by the notebook. For example, if these packages are used by the current implementation:

pip install numpy pandas scikit-learn matplotlib seaborn gradio

Then launch Jupyter:

pip install notebook
jupyter notebook

Open "upi_shield_ai.ipynb" and execute the cells in order.

Note: These commands are a general setup guide. If the repository contains a "requirements.txt" file, use that file as the authoritative dependency list.

📂 Repository Structure

The repository includes the following documented project files:

upi-shield-ai/
├── ARCHITECTURE.md
├── DEMO_SCRIPT.md
├── README.md
├── THREAT_MODEL.md
├── Team_RSG_UPI_Shield_AI_Final_Pitch_Deck.pdf
└── upi_shield_ai.ipynb

The files serve these purposes:

- "README.md" — Project overview, setup instructions, methodology, and limitations.
- "ARCHITECTURE.md" — System architecture and component design.
- "DEMO_SCRIPT.md" — Guide for presenting the prototype.
- "THREAT_MODEL.md" — Threat considerations and security assumptions.
- "Team_RSG_UPI_Shield_AI_Final_Pitch_Deck.pdf" — Hackathon presentation deck.
- "upi_shield_ai.ipynb" — Notebook implementation and demonstration.

The tree above describes the documented project files; additional files may exist in the repository.

🔐 Privacy and Security

UPI Shield AI is designed as a prototype with a privacy-first demonstration approach.

- It uses synthetic transaction records for the described experiments.
- It does not require real UPI PINs, OTPs, passwords, or banking credentials.
- It is not connected to a live UPI payment system.
- It does not execute, authorize, reverse, or block transactions.
- It is intended to provide risk indicators for human review.
- Any future integration would require appropriate authorization, secure data handling, testing, and compliance review.

Do not upload real customer financial data, credentials, or personally identifiable information into the demonstration.

⚠️ Limitations and Future Improvements

Current limitations

- Evaluation is based on synthetic data.
- Synthetic patterns may not reflect the diversity of real scam behaviour.
- Rule-based results can be affected by how labels and rules are constructed.
- Anomaly detection can flag legitimate unusual transactions.
- Medium-risk thresholds may generate more review work than a real operational team can handle.
- The prototype is not production-ready and does not provide a definitive fraud determination.

Future improvements

- Evaluate against appropriately authorized, anonymized, representative datasets.
- Test generalization on data that was not used to design the rules.
- Tune thresholds to balance missed suspicious activity and false positives.
- Improve explanations for individual risk indicators.
- Add robust input validation and consistent output schemas.
- Measure review workload and false-positive rates across risk levels.
- Add model monitoring, reproducible experiments, and documented model versions.
- Conduct security, privacy, and compliance reviews before any real-world integration.

👥 Team RSG

Institution: Muthayammal Engineering College
Team size: 3 members

Member| Name
Member 1| SILAMBARASAN C.
Member 2| RAMANA
Member 3| GOKUL PRIYA

The team is developing UPI Shield AI as a hackathon prototype for AI-driven scam pattern recognition.

📚 Documentation

- "GitHub Repository" (https://github.com/silambarasanc199-jpg/upi-shield-ai)
- "System Architecture" (ARCHITECTURE.md)
- "Demo Script" (DEMO_SCRIPT.md)
- "Threat Model" (THREAT_MODEL.md)
- "Pitch Deck" (Team_RSG_UPI_Shield_AI_Final_Pitch_Deck.pdf)
- "Project Notebook" (upi_shield_ai.ipynb)

🏁 Conclusion

UPI Shield AI demonstrates how rule-based checks and machine learning anomaly detection can work together to highlight potentially suspicious digital payment patterns.

By combining risk indicators, supporting explanations, and a human-review workflow, the project explores a privacy-conscious approach to scam pattern recognition.

Built by Team RSG for the Amazon AI Cyber Security Hackathon — Round 1.

This project is a prototype for educational and hackathon demonstration purposes. It is not a banking product, a certified fraud detection system, or a substitute for official fraud reporting and financial institution security controls.
