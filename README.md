# GDPval Results Site

Static GitHub Pages site summarizing the paired GPT-6 Astra vs. Claude Opus 5.5 GDPval run. No build step or external dependencies.

| Page | Audience |
| --- | --- |
| `index.html` | Overview: delivery, judge outcomes, retry study, coverage of the assignment |
| `tasks.html` | GDPval gold tasks: sectors, file types, rubric structure, example tasks |
| `sectors.html` | Industry overview: GPT vs. Claude by sector, with paired significance tests and two SVG charts |
| `gpt.html` | OpenAI model trainers: pitch and dataset spec |
| `claude.html` | Anthropic model trainers: pitch and dataset spec |
| `failures.html` | Delivery-failure taxonomy (85) and human-checked 30-item quality ledger |
| `audit.html` | Human audit totals, verdicts and reviewer notes for each recorded item |
| `example.html` | Worked example: one task's prompt, both artifacts and all rubric verdicts |
| `methods.html` | Protocol, slice selection, cost estimate, judge reliability, pilot, score bounds, limitations |
| `data.html` | Reproducibility: frozen settings, hashes, tests, code (linked to [yasskin/gdpval-paired-eval](https://github.com/yasskin/gdpval-paired-eval)), 220-task status matrix |
| `glossary.html` | Plain-English definitions; jargon elsewhere links here via `a.term` anchors |

Preview locally by opening `index.html` in a browser.

## Publish

1. Copy this folder's contents, including `.nojekyll`, to the root of a GitHub repository or its `docs/` folder.
2. In the repository, open **Settings > Pages** and set the source to that branch and folder.

GitHub Pages sites can be public even when the repository is private, depending on your plan. The site contains aggregate results, plus one worked example: a public GDPval prompt, the two unedited model artifacts in `artifacts/`, and the judges' verdicts for that task. Keep all other raw model outputs, dataset files and request ledgers out of the published folder.

`example.html` and `artifacts/` are generated from local grading data by `../build_site_example.py` (run `uv run --no-project python build_site_example.py` from the project folder). Regenerate them instead of editing the criterion table by hand. `tasks.html` is generated from the dataset parquet by `../build_site_tasks.py` (`uv run --no-project --with pandas --with pyarrow python build_site_tasks.py`). `sectors.html`, `sector_*.svg` and `sector_results.json` come from `../analyze_sectors.py` (`uv run --no-project --with pandas --with pyarrow --with scipy python analyze_sectors.py`) followed by `../build_site_sectors.py`. `failures.html`, `data.html`, the generated block in `methods.html` and `data/failure_ledger.csv` come from `../analyze_plan_items.py` (`uv run --no-project --with pandas --with pyarrow --with scipy python analyze_plan_items.py`, which also writes `data/status_matrix.csv`) followed by `../build_site_plan.py`.

Numbers come from [the results one-pager](../RESULTS_ONE_PAGE.md) and [provisional failure findings](../PROVISIONAL_FAILURE_FINDINGS.md). Update the HTML when those findings change.
