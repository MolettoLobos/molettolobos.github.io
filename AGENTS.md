# AGENTS

## Overview

This repository contains a static CV site. There is no build step or framework.

- Main page: [index.html](/Users/molettolobos/projects/molettolobos.github.io/index.html)
- Styling: [style.css](/Users/molettolobos/projects/molettolobos.github.io/style.css) and inline CSS inside `index.html`
- Content source: root-level JSON files such as `header.json`, `education.json`, `experience.json`, `projects.json`, `skills.json`, `science.json`, `press.json`, and `personal.json`
- Translation source: [glossary.json](/Users/molettolobos/projects/molettolobos.github.io/glossary.json)

## How Content Is Rendered

`index.html` fetches the JSON files on load, stores them in `dataStore`, and renders sections dynamically with plain JavaScript.

- Section labels use `T(key)` and `glossary.json -> ui`
- Free-text content uses `translateText(text)` and `glossary.json -> content`
- Degree and role titles use `getTitleTranslation()` and `glossary.json -> titles`

## Translation Rule

If you add or edit human-readable text in any JSON content file, also update `glossary.json`.

- For section labels or UI strings, add entries under `ui`
- For sentences, bullets, and descriptions coming from data files, add exact source strings under `content.es` and any other supported languages you want to keep in sync
- If a sentence in `skills.json` or `experience.json` does not translate, the most common cause is that the exact English source string is missing from `glossary.json`

## Editing Guidance

- Keep content edits in the JSON files, not hardcoded in `index.html`
- Preserve the current data shape unless you are also updating the render logic
- Test language changes by switching the selector in the page and checking `Skills`, `Experience`, and PDF output
- Be careful with punctuation changes in source JSON: translation matching depends on exact strings
