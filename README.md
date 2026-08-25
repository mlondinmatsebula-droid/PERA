# PERA — Perturbation-Encoded Relaxation Analysis

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Predictions: 2 locked](https://img.shields.io/badge/Predictions-2%20locked-red)](predictions/locked_v1.2.json)

> **A causal framework connecting local structural perturbations to conformational dynamics via structural debt and cooperative accommodation.**

**What PERA stands for:** **P**erturbation-**E**ncoded **R**elaxation **A**nalysis — the analysis of how perturbations are encoded into (or relaxed by) protein structure, and whether that encoding requires cooperative motion to resolve.

---

## The Core Claim

> **Perturbation-induced conformational exchange is governed not by perturbation magnitude, but by the inability of the local environment to accommodate the resulting structural debt without recruiting cooperative motion.**

This repository contains:
- **Six-structure SASA quantification** supporting the framework
- **Two locked prospective predictions** for T4 lysozyme mutants with no published CPMG data
- **A 9-case dataset** spanning T4 lysozyme, DHFR, and HIV-1 protease
- **Falsification criteria** for each prediction

---

## Quick Start

| File | What It Is |
|------|------------|
| [`predictions/locked_v1.2.json`](predictions/locked_v1.2.json) | Immutable predictions with structural evidence |
| [`data/sasa_comparison.csv`](data/sasa_comparison.csv) | Six-structure FreeSASA comparison |
| [`data/case_table.json`](data/case_table.json) | 9-case dataset (7 validated, 2 predicted) |
| [`figures/six_structure_sasa.png`](figures/six_structure_sasa.png) | Quantitative comparison figure |
| [`docs/synthesis.md`](docs/synthesis.md) | Full framework synthesis |

---

## The Triad: Falsifying the Naive Hypothesis

The naive model — *buried volume loss → conformational exchange* — is falsified from **two independent directions**:

| Property | L99A (DYNAMIC) | F153A (PRED. ENERGETIC) | L99G (PRED. ENERGETIC) |
|----------|---------------|------------------------|------------------------|
| **Volume removed** | −57 Å³ | −68 to −74 Å³ (more) | −76 Å³ (even more) |
| **Scaffold** | Rigid | Flexible | Flexible |
| **Mutation-site REL** | **15.2%** | **4.5%** (3.4× lower) | 19.9% (glycine backbone) |
| **Total SASA vs WT** | **+242 Å²** (swells) | **−282 Å²** (contracts) | +76 Å² (small) |
| **Structural debt** | Persistent buried void | Locally accommodated | Solvent-exposed declivity |
| **CAN estimate** | ~15 | ~2–3 | ~0 |
| **CPMG** | Exchange (validated) | **No exchange (locked)** | **No exchange (locked)** |

---

## Locked Predictions

### F153A
- **Prediction:** No widespread CPMG exchange (or <5 residues local exchange)
- **Structural evidence:** ALA153 REL = 4.5%; total SASA < WT; no Phe114 signature
- **Falsification:** >10 residues showing exchange
- **Confidence:** HIGH

### L99G
- **Prediction:** No CPMG exchange
- **Structural evidence:** Solvent-accessible declivity; total SASA increase 3× < L99A
- **Falsification:** Any CPMG signal
- **Confidence:** HIGH

**Neither mutant has published CPMG or CEST data.** Both predictions are genuinely prospective.

---

## The SASA Threshold (Empirical)

```
REL < 3%      →  Locally filled → ENERGETIC
REL 3–8%      →  Partial accommodation → weak/no exchange (F153A = 4.5%)
REL > 10%     →  Persistent buried void → DYNAMIC (L99A = 15.2%)
Glycine       →  Use total SASA + literature, not direct REL
```

---

## Framework Architecture

```
Perturbation (P)
    ↓
Local Structural Response (ΔL)  ←  SASA, volume, contacts
    ↓
Mechanical Redistribution (M)   ←  ENM/ANM
    ↓
Alternative-State Accessibility (A)  ←  CAN: minimum cooperative residue set
    ↓
ΔG‡ → k_ex → D_obs            ←  CPMG/CEST/NMR
```

---

## Citation

If you use PERA in your research, please cite:

```bibtex
@software{pera2026,
  title = {PERA: Perturbation-Encoded Relaxation Analysis},
  year = {2026},
  url = {https://github.com/[your-username]/PERA},
  note = {v2.3 — Two locked prospective predictions for T4 lysozyme dynamics}
}
```

---

## License

MIT License — see [LICENSE](LICENSE).

---

## Contact

For questions about the framework or predictions, open an issue or contact [your-email].

For experimental collaboration inquiries, see [`docs/outreach.md`](docs/outreach.md).
