# Fi'l Sentences

Practice Egyptian Arabic (Masry) verbs in real sentences. Pick a tense and a verb, and the app generates a fresh English sentence built around that exact verb form. You write it in Masry, reveal the answer, and grade yourself.

I built it for my own Egyptian Arabic classes, because textbook drills run out of sentences fast and generic AI chat doesn't stay inside the vocabulary you actually know.

## Features

- **Sentences mode** — an LLM writes a new sentence for each verb + pronoun + tense combination, constrained to your known vocabulary, and returns the Masry answer plus a glossary of every other word it used.
- **Pool mode** — keep a small set of sentences in rotation until you get each one right.
- **Conjugate, Meaning and Modal drills** — fully deterministic, generated from conjugation rules in code (past suffixes, present prefixes, bare present after *lazem / momken / 3awez*), so they work with no AI at all.
- **Known vocabulary** — tell it which words you know and sentences stay inside that list.
- **Review list** — words from sentences you missed, with a study mode in both directions (Masry → English and English → Masry).
- **Flag corrections** — mark a generated word as wrong or invented, with the correct meaning, and keep a log of corrections.
- **Dialect guardrails** — known non-Cairene words the model occasionally slips in are corrected deterministically after generation instead of trusting the prompt alone.

## How it's built

A single dependency-free HTML file (vanilla JS + CSS, light and dark themes, mobile-first).

It was first built as a Claude artifact, where the page gets two runtime capabilities: model calls (`claude.use("sample")`) and saved data (`claude.use("db")`). [`claude-shim.js`](claude-shim.js) provides the same two APIs anywhere else:

- model calls go straight from the browser to the Anthropic Messages API with an API key the visitor enters
- saved data goes to `localStorage`

Inside claude.ai the shim detects the real runtime and does nothing.

## Run it

Open `index.html` in a browser, or serve the folder with any static host (GitHub Pages works).

- Conjugate, Meaning and Modal work immediately.
- For Sentences mode, click **Set API key** (bottom-right) and paste an Anthropic API key. The key is stored only in your browser and is sent only to `api.anthropic.com`.

## License

MIT
