# Markets, Simplified

Detailed study notes for the LinkedIn series Markets, Simplified, built with MkDocs Material and styled to match the carousel design (cream, royal blue, Poppins). Styling lives in `docs/stylesheets/brand.css`.

## Add an episode

1. Create `docs/episodes/NN-slug.md` using this template:

```
<p class="ms-kicker">Épisode NN</p>

# Solid Words <span class="ms-outline">LastWord.</span>

## Pourquoi cet épisode

...

<div class="ms-takeaway" markdown>

## À retenir

...

</div>
```

   The last word of the title (or the parenthetical, or the only word) goes in the outline span, with a period.

2. Add it to `nav` in `mkdocs.yml` with an explicit title (`"NN. Title": episodes/NN-slug.md`) and add a card in `docs/index.md`.
3. Run `mkdocs build --strict`, then push to `main`. The GitHub Action deploys it.

## Preview locally

```
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt
.venv/bin/mkdocs serve
```

Then open http://127.0.0.1:8000.
