# UPI Shield AI — Threat Model

## Assets to protect
- Transaction data and user privacy
- Model and detection rules
- Review reports and evaluation results
- Integrity of the demo and repository

## Threats
1. Sensitive information accidentally entered into a demo.
2. False positives that flag legitimate activity.
3. False negatives that miss suspicious activity.
4. Manipulated inputs designed to evade detection.
5. Misleading claims based on synthetic test results.
6. Unauthorized access to any future hosted service.

## Safeguards in this prototype
- Synthetic data only.
- No payment-network credentials or payment actions.
- Input checks and bounded demo risk score.
- Human review recommendation instead of automatic blocking.
- Separate reporting of rules and ML outputs.
- Clear documentation of dataset and model limitations.

## Future production requirements
- Authorized representative datasets and privacy/legal review.
- Authentication, authorization, and secure audit logging.
- Rate limiting, input validation, and monitoring.
- Robust adversarial testing and model drift monitoring.
- Independent evaluation and human escalation procedures.
