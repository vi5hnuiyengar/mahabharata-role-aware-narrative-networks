# mahabharata-role-aware-narrative-networks
Reproducible pipeline that fuses ByT5-Sanskrit morphology with English co-mention networks to produce role-colored overlays (agents/patients/means/settings) for a Vana Parvan passage—figures, notebooks, and code included.

Awesome—here’s a tight package you can drop into GitHub.

⸻

✅ Repository name, description, and topics

Repo name (suggested):
mahabharata-role-aware-narrative-networks

GitHub one-line description:
Reproducible pipeline that fuses ByT5-Sanskrit morphology with English co-mention networks to produce role-colored overlays (agents/patients/means/settings) for a Vana Parvan passage—figures, notebooks, and code included.

Suggested topics/tags:
sanskrit mahabharata digital-humanities nlp byt5 morphology network-analysis pyvis spacy pandas graph-theory philology

⸻

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

---

## Repository layout

.
├─ code/
│  ├─ 01_tag_sanskrit.ipynb          # ByT5 tagging (segmentation/lemma/morph)
│  ├─ 02_expand_tags.ipynb           # Expand ~80 abbrevs → tidy columns
│  ├─ 03_sanskrit_eda.ipynb          # Case/Number/Gender, freq, co-occ
│  ├─ 04_english_networks.ipynb      # Co-mentions, centrality, speaker metrics
│  ├─ 05_joint_overlay.ipynb         # Agency table + directed edges + overlay
│  └─ utils/
│     └─ expansion_rules.py          # Morph tag expansion map
├─ data/
│  ├─ raw/                           # (You add sources here; not versioned)
│  ├─ interim/                       # Per-segment CSVs
│  └─ processed/
│     └─ facts_expanded.csv          # Final tidy token table
├─ figures/                          # PNG/PDF outputs for the paper
│  ├─ character_network.png
│  ├─ ethical_ratio_by_speaker.png
│  ├─ degree_centrality.png
│  ├─ sentiment_arc.png
│  ├─ byT5_directed_network.png
│  ├─ combined_role_directed_network.png
│  └─ pipeline_overview.png
├─ artifacts/
│  ├─ character_edges.csv
│  ├─ speaker_metrics.csv
│  ├─ byT5_directed_edges.csv
│  └─ byT5_directed_edges_by_role.csv
├─ environment.yml                   # Conda env (recommended)
├─ requirements.txt                  # Pip fallback
├─ LICENSE
├─ CITATION.cff
└─ README.md

> **Note:** The Sanskrit source text is not redistributed here. Place your DCS source under `data/raw/` following their terms.

---

## Quickstart

### 0) Clone
```bash
git clone https://github.com/USER/mahabharata-role-aware-narrative-networks.git
cd mahabharata-role-aware-narrative-networks

1) Environment

Conda (recommended)

conda env create -f environment.yml
conda activate mbh-net
python -m spacy download en_core_web_sm

Pip

python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python -m spacy download en_core_web_sm

2) Data placement

Place your Sanskrit passage(s) as UTF-8 text files in:

data/raw/vanaparvan_01.txt

If your text is Devanāgarī or non-IAST, see 03_sanskrit_eda.ipynb for normalization hints.

3) Run notebooks

Open the notebooks in order under code/. Each notebook saves outputs to data/processed/, figures/, and artifacts/.

Minimal one-liner to rebuild the overlay after you already have facts_expanded.csv:

jupyter nbconvert --to notebook --execute code/05_joint_overlay.ipynb


⸻

Key outputs (for your paper)
	•	Figures: figures/*.png:
	•	character_network.png, ethical_ratio_by_speaker.png, degree_centrality.png,
	•	sentiment_arc.png, byT5_directed_network.png, combined_role_directed_network.png,
	•	pipeline_overview.png.
	•	Tables/CSVs: artifacts/*.csv:
	•	character_edges.csv, speaker_metrics.csv,
	•	byT5_directed_edges.csv, byT5_directed_edges_by_role.csv.
	•	Token table: data/processed/facts_expanded.csv.

⸻

Reproducibility
	•	Random seeds are fixed in network layouts and sampling (numpy, networkx).
	•	Versions are pinned in environment.yml / requirements.txt.
	•	Provenance: outputs include stable filenames; commit hashes in your paper link back here.
	•	Hardware: runs on a laptop (tagging may take longer); no GPU required for the analysis stages.

⸻

Citation

If you use this repo, please cite:

@software{iyengar_mahapipeline_2025,
  author  = {Vishnuvallabha Iyengar},
  title   = {Mahābhārata: Role-Aware Narrative Networks},
  year    = {2025},
  url     = {https://github.com/USER/mahabharata-role-aware-narrative-networks}
}

Also cite the data/model foundations:

@misc{hellwig_dcs,
  author = {Oliver Hellwig},
  title  = {DCS—The Digital Corpus of Sanskrit},
  year   = {2010--2020},
  url    = {https://www.sanskrit-linguistics.org/dcs/}
}

@article{xue2022byt5,
  title={ByT5: Towards a Token-Free Future with Pre-trained Byte-to-Byte Models},
  author={Linting Xue and Aditya Barua and Noah Constant et al.},
  journal={Transactions of the ACL},
  year={2022}
}

@inproceedings{elson2010extracting,
  title={Extracting Social Networks from Literary Fiction},
  author={Elson, David and Dames, Nicholas and McKeown, Kathleen},
  booktitle={ACL},
  year={2010}
}


⸻

License

Code is released under the MIT License (see LICENSE).
Respect third-party licenses (e.g., DCS text, any model weights you use).

⸻

Acknowledgments
	•	DCS — Digital Corpus of Sanskrit (Hellwig).
	•	ByT5 architecture (Xue et al.).
	•	networkx, spaCy, pandas, matplotlib, pyvis.

⸻

Roadmap
	•	Add optional dependency parsing + coreference for richer roles.
	•	Release a minimal CLI (mbhnet) to run the overlay in one command.
	•	Extend to more subchapters and to Sanskrit kṛtis with section-aware segmentation.

⸻

FAQ

Q: My text isn’t IAST—can I still run this?
A: Yes. Normalize to a consistent script first (see notes in 03_sanskrit_eda.ipynb).
Q: I don’t have all CSVs yet—can I still publish the figures?
A: Absolutely. The notebooks regenerate missing artifacts; this repo anchors the workflow and paths.
Q: Do I need a GPU?
A: No, for analysis. Tagging speed improves with GPU but isn’t required.

⸻


---

## 🔧 Bonus templates

**`environment.yml`**
```yaml
name: mbh-net
channels: [conda-forge, defaults]
dependencies:
  - python=3.10
  - jupyterlab
  - pandas
  - numpy
  - matplotlib
  - networkx
  - spacy
  - pip
  - pip:
      - pyvis
      - scikit-learn
      - vaderSentiment

requirements.txt

pandas
numpy
matplotlib
networkx
spacy
pyvis
scikit-learn
vaderSentiment

CITATION.cff

cff-version: 1.2.0
title: "Mahābhārata: Role-Aware Narrative Networks"
authors:
  - family-names: Iyengar
    given-names: Vishnuvallabha
date-released: 2025-11-04
repository-code: "https://github.com/USER/mahabharata-role-aware-narrative-networks"
version: "v0.1.0"
license: "MIT"

.gitignore

# Python
__pycache__/
*.pyc
.venv/
# Jupyter
.ipynb_checkpoints/
# Data
data/raw/*
!data/raw/.gitkeep
data/interim/*
data/processed/*.tmp
# Outputs
figures/*.tmp
artifacts/*.tmp
# OS/IDE
.DS_Store
.vscode/

Swap USER with your GitHub handle, commit, and you’re set.
