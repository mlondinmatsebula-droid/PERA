# Setting Up the PERA Repository

## 1. Create the repo on GitHub
- Go to https://github.com/new
- Name: `PERA` (or `PERA-framework`)
- Description: "Perturbation-Encoded Relaxation Analysis — a causal framework for protein conformational dynamics"
- Visibility: Public
- Initialize with README: NO (we have our own)

## 2. Clone locally (or use GitHub web upload)
```bash
git clone https://github.com/YOUR_USERNAME/PERA.git
cd PERA
```

## 3. Copy these files into the repo
Copy everything from this folder into your local repo.

## 4. Customize these files before pushing
- `README.md`: Add your GitHub username to the badge URLs
- `CITATION.cff`: Replace `[Your Name]` with your actual name
- `LICENSE`: Replace `[Your Name]` with your actual name
- `docs/outreach.md`: Add your actual contact info

## 5. Push to GitHub
```bash
git add .
git commit -m "PERA v2.3 — Six-structure SASA quantification, two locked predictions"
git push origin main
```

## 6. Enable GitHub features
- Go to Settings → General → Social Preview: upload `figures/six_structure_sasa.png`
- Go to Settings → Topics: add `protein-dynamics`, `NMR`, `conformational-exchange`, `allostery`
- Go to Insights → Community Standards: add Issue templates if desired

## 7. Share
- Add the GitHub link to your email signature
- Include it in outreach emails to Bouvignies and Venditti
- Tweet the six-structure figure with the repo link
