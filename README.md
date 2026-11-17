# GDPval Results Site

Static GitHub Pages site summarizing the paired GPT-6 Astra vs. Claude Opus 5.5 GDPval run. No build step or external dependencies.

| Page | Audience |
| --- | --- |
| `index.html` | Overview: delivery, judge outcomes, retry study |
| `tasks.html` | GDPval gold tasks: sectors, file types, rubric structure, example tasks |
| `gpt.html` | OpenAI model trainers |
| `claude.html` | Anthropic model trainers |
| `example.html` | Worked example: one task's prompt, both artifacts and all rubric verdicts |
| `methods.html` | Protocol, grading coverage, score bounds, limitations |
| `glossary.html` | Plain-English definitions; jargon elsewhere links here via `a.term` anchors |

Preview locally by opening `index.html` in a browser.

## Publish

1. Copy this folder's contents, including `.nojekyll`, to the root of a GitHub repository or its `docs/` folder.
2. In the repository, open **Settings > Pages** and set the source to that branch and folder.

GitHub Pages sites can be public even when the repository is private, depending on your plan. The site contains aggregate results, plus one worked example: a public GDPval prompt, the two unedited model artifacts in `artifacts/`, and the judges' verdicts for that task. Keep all other raw model outputs, dataset files and request ledgers out of the published folder.

`example.html` and `artifacts/` are generated from local grading data by `../build_site_example.py` (run `uv run --no-project python build_site_example.py` from the project folder). Regenerate them instead of editing the criterion table by hand. `tasks.html` is generated from the dataset parquet by `../build_site_tasks.py` (`uv run --no-project --with pandas --with pyarrow python build_site_tasks.py`).

Numbers come from [the results one-pager](../RESULTS_ONE_PAGE.md) and [provisional failure findings](../PROVISIONAL_FAILURE_FINDINGS.md). Update the HTML when those findings change.
