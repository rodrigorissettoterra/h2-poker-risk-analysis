# Betting Behavior & Player Risk Analysis

> **Behavioral and financial analytics for identifying unusual patterns and potential risk signals in an online gaming platform.**

A Data Science case focused on transforming betting, customer, and financial transaction data into **interpretable indicators and operational risk signals**.

The project explores how exploratory analysis, statistical thresholds, and transparent business rules can support the identification of unusual behavior without treating an analytical flag as proof of fraud.

<p>
  <img src="https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white" alt="Pandas">
  <img src="https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white" alt="Jupyter">
  <img src="https://img.shields.io/badge/Data%20Science-Risk%20Analytics-green" alt="Risk Analytics">
</p>

---

## Business problem

Online gaming platforms generate large volumes of behavioral and financial data. Among thousands of normal interactions, some patterns may deserve additional investigation:

- unusually high returns;
- concentration of activity in specific games;
- withdrawals disproportionate to deposits;
- unusual combinations of betting and financial behavior.

The challenge is to transform those patterns into **transparent and interpretable monitoring criteria** while avoiding conclusions unsupported by the data.

---

## Analytical questions

The project was structured around five questions:

1. Which players show unusual betting or winning behavior?
2. Are high-return players concentrated in particular games?
3. Which financial movements differ substantially from the general population?
4. Which indicators can support an operational risk-monitoring process?
5. How can simple rules be designed without creating excessive false positives?

---

## Data

The original case used three datasets.

### Casino activity

Behavioral information related to games, game types, betting values, number of bets, and winnings.

### Customer data

Customer attributes, demographic characteristics, and acquisition-channel information.

### Financial activity

Deposits, withdrawal requests, and financial movement by player.

> **The original datasets are not included in this repository because they contain operational and potentially sensitive information.**

The repository focuses on the methodology, analytical reasoning, indicators, and conclusions.

---

## Analytical workflow

```text
Raw Data
   ↓
Data Quality Checks
   ↓
Exploratory Analysis
   ↓
Behavioral Indicators + Financial Indicators
   ↓
Distribution Analysis
   ↓
Statistical Thresholds
   ↓
Risk Rules
   ↓
Flagged Cases
   ↓
Business Interpretation
   ↓
Operational Recommendations
```

---

## Methodology

### 1. Exploratory analysis

The first stage evaluates:

- data structure;
- missing values;
- duplicated records;
- customer profiles;
- game popularity;
- betting distributions;
- winning distributions;
- deposits and withdrawals;
- unusual observations.

The objective is to understand the underlying population before defining any risk rule.

### 2. Behavioral indicators

#### Player return ratio

One of the main indicators compares winnings with total betting volume:

```text
player_return_ratio = total_winnings / total_bets
```

Interpretation:

```text
ratio < 1 → player lost more than they won
ratio = 1 → break-even
ratio > 1 → player won more than they bet
```

Extremely high values relative to the population may represent cases that deserve further investigation. They are **signals, not evidence of misconduct**.

#### Game-level return

The same concept is calculated by game to investigate whether certain games are associated with unusually high observed returns and whether flagged players concentrate activity in those games.

### 3. Financial indicators

#### Withdrawal-to-deposit ratio

Financial behavior is evaluated through:

```text
withdrawal_ratio = total_withdrawals / total_deposits
```

Unusually high ratios may indicate accounts that deserve further investigation, particularly when combined with other behavioral signals.

---

## Risk rules

The project proposes interpretable rules based on statistical distributions.

Examples include:

- player return above the 99th percentile;
- relevant exposure to games with unusually high observed return;
- elevated withdrawal-to-deposit ratio;
- combinations of multiple behavioral and financial signals.

The goal is to create a **first monitoring layer that business and operational teams can understand and audit**.

---

## Main findings

### 1. A small number of players displayed unusually high returns

Their behavior differed substantially from the general population and justified additional investigation.

### 2. High player returns were not explained solely by game concentration

Players flagged by return metrics were not necessarily concentrating all activity in high-return games. This indicates that simplistic one-dimensional rules can lead to misleading conclusions.

### 3. Financial ratios added a complementary risk dimension

The relationship between deposits and withdrawals helped identify patterns that were not visible from betting behavior alone.

---

## Business value

| Area | Potential use |
|---|---|
| Platform security | Identify unusual behavioral patterns |
| Financial control | Detect disproportionate financial movements |
| Operations | Prioritize cases for manual review |
| Product | Investigate games with unusual return patterns |
| Risk management | Combine multiple indicators into monitoring rules |

---

## Recommendations

### Short term

- automate alerts for extreme return ratios;
- monitor abnormal withdrawal behavior;
- combine multiple signals before escalating a case;
- keep manual review in the decision loop.

### Medium term

- create an operational monitoring dashboard;
- validate thresholds with domain specialists;
- measure false-positive rates;
- calibrate indicators using historical outcomes.

### Longer term

- create a composite risk score;
- compare rule-based detection with Machine Learning;
- incorporate temporal behavior;
- evaluate anomaly-detection models;
- integrate alerts into operational workflows.

---

## Privacy and responsible interpretation

Risk analytics requires careful interpretation. A statistical anomaly does **not** demonstrate fraud, abuse, or malicious behavior.

For this reason:

- original operational data are not published;
- analytical flags should be treated as signals for investigation;
- sensitive identifiers should never be exposed unnecessarily;
- human review should remain part of decisions with material consequences.

---

## Repository contents

```text
.
├── .gitignore
├── Case_H2.ipynb
├── Apresentação Análise de dados - H2.pdf
└── README.md
```

---

## Running the notebook

Clone the repository:

```bash
git clone https://github.com/rodrigorissettoterra/h2-poker-risk-analysis.git
cd h2-poker-risk-analysis
```

Create and activate a virtual environment, then install the main dependencies:

```bash
python -m venv .venv
pip install pandas numpy matplotlib seaborn jupyter
```

Open the notebook:

```bash
jupyter notebook Case_H2.ipynb
```

Because the original datasets are private, reproducing the complete analysis requires access to data with the same expected structure.

---

## Project artifacts

- [Analysis notebook](./Case_H2.ipynb)
- [Presentation](./Apresentação%20Análise%20de%20dados%20-%20H2.pdf)

---

## Limitations

This project represents an analytical case rather than a production fraud-detection platform.

Current limitations include:

- rule-based thresholds;
- no validated ground-truth fraud labels;
- no online monitoring;
- no temporal risk model;
- no formal false-positive / false-negative optimization;
- no production alerting system.

These limitations matter because **anomaly detection and fraud detection are not equivalent problems**.

---

## Author

**Rodrigo Terra**

Data & AI professional interested in Analytics Engineering, Data Science, Artificial Intelligence, automation, and decision-support systems.

- GitHub: [Rodrigo Terra](https://github.com/rodrigorissettoterra)
- LinkedIn: [Rodrigo Terra](https://www.linkedin.com/in/rodrigo-rissetto-terra/)
