# Markets, Simplified

Detailed study notes for the LinkedIn series Markets, Simplified, built with MkDocs Material.

## Add an episode

1. Create `docs/episodes/NN-slug.md`, starting with `# NN. Title`.
2. Add it to the `nav` section of `mkdocs.yml` and to the list in `docs/index.md`.
3. Push to `main`. The GitHub Action rebuilds and deploys the site.

## Preview locally

```
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt
.venv/bin/mkdocs serve
```

Then open http://127.0.0.1:8000.
