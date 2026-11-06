# DCP-CCP

Descriptive comparisons of disruptive and consolidating papers citing Nobel-related focal papers, including citation dynamics and text features.

## Install

Use Python 3.11. From the repository root:

```bash
python -m venv .venv
# Activate .venv using the command for your operating system.
python -m pip install -r requirements.txt
cp config.example.json config.json
jupyter lab
```

## Configure and run

Set `data_dir`, `output_dir` and `seed` in `config.json`, then open a notebook and run its cells in order with a fresh kernel. Relative directories resolve against the configuration file location. The repository root is the Jupyter working directory.

`RESEARCH_CONFIG` selects a configuration file; `RESEARCH_DATA_DIR`, `RESEARCH_OUTPUT_DIR` and `RESEARCH_SEED` provide environment overrides. The default seed is 2026. Tables use CSV, single-CSV ZIP archives or Excel. File naming is defined in `project_utils.DATA_FILES`; `input_schema.json` specifies the table field contracts.

Figures render in Jupyter. Explicit file exports use the configured output directory. Notebooks are stored with clear execution state.

## Notebooks

- `fig 1.ipynb`
- `fig 2.ipynb`
- `fig 3 #DCP CCP.ipynb`
- `fig 4 (higher impact).ipynb`
- `fig 5 (higher impact dynamic).ipynb`
- `fig 9 Words.ipynb`

## Methods

Nobel focal papers and citing papers join through paper IDs. Citation-lag summaries show bootstrap intervals, while standard-error summaries use the sample standard deviation. Text analysis tokenizes the title-and-abstract field and lemmatizes verbs and nouns.

Install NLTK resources once with `python -m nltk.downloader stopwords punkt punkt_tab averaged_perceptron_tagger averaged_perceptron_tagger_eng wordnet omw-1.4`.

Bootstrap intervals use full-size resamples of finite observations and deterministic random generators.

## Source checks

```bash
python scripts/validate_sources.py
```

This command parses Python and notebook source, validates JSON and checks notebook execution state. GitHub Actions runs the same source checks without executing research analyses.

## Citation and license

`CITATION.cff` provides software citation metadata. Cite the associated publication using its bibliographic record. Project code and documentation use the MIT license. Third-party data retain their providers' licenses and access terms.
