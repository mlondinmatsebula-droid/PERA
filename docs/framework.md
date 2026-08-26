# PERA Framework Documentation

## Version
**v2.3** — Six-structure SASA quantification complete. Two predictions locked.

---

## The Causal Chain

```
Perturbation (P)
    ↓
Local Structural/Energetic Response (ΔL)
    ↓
Mechanical Redistribution (M)          ← ENM/ANM captures this
    ↓
Alternative-State Accessibility (A)    ← THE MISSING LINK
    ↓
ΔG‡ (barrier height)
    ↓
k_ex (exchange rate)
    ↓
D_obs (CPMG/CEST/NMR observation)
```

---

## The Two Axes

### Axis 1: C_A — Accommodation Complexity (CAN)
> **CAN = minimum number of residues that must move collectively (>0.5 Å or χ₁ > 60°) to geometrically accommodate the perturbation**

| System | CAN Estimate | Physical Basis |
|--------|-------------|----------------|
| L99A | ~15 | Phe114 flip + helices F/G reorganization |
| F153A | ~2–3 | Local side-chain repacking |
| L99G | ~0 | Solvent exposure, no cooperative motion |
| R96H | ~1–2 | His96 rotamer adjustment |

### Axis 2: C_E — Accommodation Cost (Local Debt)
> **Quantified by mutation-site relative SASA (REL) from FreeSASA**

| REL Range | Interpretation | Prediction | Example |
|-----------|---------------|------------|---------|
| < 3% | Locally filled | ENERGETIC | WT, R96H |
| 3–8% | Partial void, local accommodation | Weak/no exchange | F153A (4.5%) |
| > 10% (non-glycine) | Persistent buried void | DYNAMIC | L99A (15.2%) |
| Glycine | Use total SASA + literature | Context-dependent | L99G |

---

## The Triad

The three-mutation comparison (L99A / F153A / L99G) falsifies the naive hypothesis from two independent directions:

1. **F153A:** More volume loss than L99A, but flexible scaffold relaxes → no debt
2. **L99G:** Even more volume loss, but solvent-exposed → debt paid by solvent

Only **L99A** creates a persistent buried void that cannot be locally accommodated.

---

## Computational Methods Used

| Question | Tool | Status |
|----------|------|--------|
| What is the starting structure? | PDB / experimentally resolved | Done |
| What changed locally? | FreeSASA (geometric) | Done |
| Where can deformation propagate? | ENM/ANM | Done |
| What conformations are accessible? | MD (planned) | Not done |
| What is the transition barrier? | MSM / metadynamics (planned) | Not done |
| Does the model reproduce experiment? | CPMG/CEST literature | In progress |

---

## Honest Limitations

1. **SASA is geometric, not energetic.** REL measures exposure, not thermodynamic cost.
2. **CAN is estimated, not algorithmic.** The ~15 for L99A is literature-based.
3. **Glycine is a special case.** GLY99 REL is not directly comparable to ALA99 REL.
4. **The threshold is empirical.** 5% and 10% boundaries are fitted to six structures.
5. **F153A structure is C54T/C97A/F153A.** Stabilizing mutations present but do not affect core dynamics.

---

## Roadmap

### v2.4 (Next)
- [ ] Algorithmic CAN: compute minimum cooperative residue set
- [ ] Rosetta strain energy: true C_E metric
- [ ] A98L, V149G, R96P bracketing cases

### v3.0 (Future)
- [ ] Multi-protein validation (beyond T4L)
- [ ] Machine learning: predict CAN from structure
- [ ] Experimental validation: CPMG on F153A and/or L99G
