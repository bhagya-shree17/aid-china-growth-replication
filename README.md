# Aid, China, and Growth: A Replication Study

A from-scratch Python replication of Dreher et al. (2021), reproducing, extending, and diagnosing the original panel analysis of Chinese development finance and economic growth.

> Course project — Economic Data Analysis (ECO613M), IIT Kanpur

## Overview

This project replicates the core results of Dreher, Fuchs, Parks, Strange, and Tierney (2021), *Aid, China, and Growth: Evidence from a New Global Development Finance Dataset*, on a panel of **4,304 Chinese-financed projects across 138 countries**. The entire pipeline is implemented in Python rather than Stata — including estimators that no standard Python library reproduces exactly.

## What this replication does

- **Matches the OLS baseline exactly** and recovers the 2SLS estimates within the paper's reported range.
- **Implements Swamy-Arora random-effects GLS and cluster-robust variance estimators from scratch**, since no Python library reproduces Stata's `xtreg` behaviour.
- **Extends the panel to 2016** to test lag structure.
- **Diagnoses every divergence** from the published results — including a first-stage Kleibergen-Paap *F* of **8,097** in the Western-aid regressions, which revealed instrument collinearity collapsing 2SLS toward OLS.

## Data

*[Note the source of the Chinese Official Finance data (AidData) and the growth/covariate series, and how to obtain them. If licensing restricts redistribution, do **not** commit the raw data — provide a download script or instructions instead, and keep data paths in `.gitignore`.]*

## Repository structure

```
.
├── data/            # not committed — see Data section
├── src/
│   ├── estimators.py    # Swamy-Arora GLS, cluster-robust SEs
│   ├── replication.py   # OLS + 2SLS baseline
│   └── diagnostics.py   # instrument-strength tests
├── results/
├── requirements.txt
└── README.md
```

## Running the replication

```bash
pip install -r requirements.txt
python -m src.replication
```

Random seeds are fixed for reproducibility.

## Reference

Original paper:

> Dreher, A., Fuchs, A., Parks, B., Strange, A. M., & Tierney, M. J. (2021). Aid, China, and Growth: Evidence from a New Global Development Finance Dataset. *American Economic Journal: Applied Economics*, 13(2), 135–174.

*(Verify volume/issue/pages against your copy before publishing.)*

This repository is an independent replication for educational purposes and is not affiliated with the original authors.

## License

*[MIT recommended for the code.]*
