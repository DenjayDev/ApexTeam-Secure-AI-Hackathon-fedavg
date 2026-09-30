# APEX: Secure AI Hackathon (Advanced track, primary)

Federated intrusion detection on NSL-KDD with five banks, non-IID data,
and one malicious client (client 1: label flip + 15x update scaling).

## Result (same held-out NSL-KDD test split, seed 42)
| | F1 |
|---|---|
| Naive FedAvg under attack (before) | 0.0511 |
| Detect + exclude (after) | 0.7154 |
| F1 recovered | +0.6643 |

Two-seed mean (seeds 42, 1): naive 0.1220, detect + exclude 0.7179.

## Method
Each round, flag any client whose update norm exceeds 3x the median norm,
exclude flagged clients, and average the rest. It flagged client 1 in all
8 attack rounds and nobody on clean data.

## Supporting work (Intermediate)
Uniform + trust weighting raised clean non-IID F1 from 0.7110 to 0.7777
(two-seed means). Detect + trust did not beat its parents.

## Limitations
The 3x threshold is tuned to a 15x attack. Two seeds only. Methods were
chosen using the same test set we report on.

## Reproduce
Open the notebook in Kaggle (internet on) and run all cells top to bottom.
The final cell regenerates `model_scripted.pt` and `submission.json`.
