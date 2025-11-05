# mahabharata-role-aware-narrative-networks
Reproducible pipeline that fuses ByT5-Sanskrit morphology with English co-mention networks to produce role-colored overlays (agents/patients/means/settings) for a Vana Parvan passage—figures, notebooks, and code included.

📄 README.md

# Mahābhārata: Role-Aware Narrative Networks
_Reproducible analysis that joins ByT5-Sanskrit morphology with English co-mention graphs to produce role-colored overlays._

![Pipeline overview](figures/pipeline_overview.png)

## TL;DR
This repo delivers a simple, auditable pipeline for one Vana Parvan passage:
1) **Tag Sanskrit** with a ByT5-based workflow,  
2) **Expand morphological tags** to readable columns (Case/Number/Gender/…),  
3) **Analyze English** (co-mentions, speaker metrics, sentiment),  
4) **Stitch both** via an **agency table** (nominative share) and **directed edges**,  
5) **Overlay** role-colored arrows (Acc/Instr/Loc) on the English graph.

All figures and tables are generated from code/notebooks with fixed seeds and saved under `figures/` and `artifacts/`.

---

## Why this repo?
- **Readable + rigorous.** Keep the English view intuitive while restoring grammatical evidence from Sanskrit.
- **Role-aware networks.** See _who acts_ (nominatives), _who is acted upon_ (accusatives), _by what means_ (instrumentals), and _where_ (locatives).
- **Reproducible.** Every figure/table has a corresponding script or notebook and named output.
