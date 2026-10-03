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

2. Create the English version next to it as `docs/episodes/NN-slug.en.md`, same markup, with `Épisode` → `Episode` and `À retenir` → `Key takeaway`. French is the default language at `/`, English lives at `/en/`, and the header switcher links each page to its translation.
3. Add it to `nav` in `mkdocs.yml` with an explicit title (`"NN. Title": episodes/NN-slug.md`, used by both languages), and add a card in both `docs/index.md` and `docs/index.en.md`. A new nav section name also needs an English entry under `nav_translations`.
4. Run `mkdocs build --strict`, then push to `main`. The GitHub Action deploys it.

## Preview locally

```
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt
.venv/bin/mkdocs serve
```

Then open http://127.0.0.1:8000.
