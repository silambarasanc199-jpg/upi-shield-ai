# UPI Shield AI

Explainable scam-pattern recognition prototype for digital payment security.

## Problem
Suspicious transaction patterns can be difficult to identify quickly.
UPI Shield AI demonstrates how transparent rules and an anomaly-detection
model can help prioritize transactions for human review.

## Features
- Synthetic transaction dataset
- Explainable rule-based risk assessment
- Isolation Forest anomaly detection
- Rules-versus-ML evaluation
- Analyst review queue and CSV reports
- Interactive Gradio demo

## Technology
Python, Pandas, NumPy, scikit-learn, Matplotlib, Gradio.

## Run in Google Colab
Open the project notebook and run the cells in order.
The notebook creates synthetic data, trains the model, evaluates it,
and launches the interactive demo.

## Evaluation
Record precision, recall, F1-score, confusion matrix, and false-positive
rate from the held-out synthetic test set. Include the test size and
dataset-generation method with every reported result.

## Safety and limitations
- Synthetic data only; no live UPI or bank integration.
- An anomaly is not proof of fraud.
- The risk score is not a calibrated fraud probability.
- No automatic payment blocking or initiation.
- Synthetic results do not establish real-world performance.
- Do not upload credentials, payment PINs, or personal customer data.

## Team
Add team members, institution, contributions, and contact details here.
