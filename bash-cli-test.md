---
layout: page
title: "GitHub Pages + UniFuncs Publisher"
permalink: /bash-cli-test/
---

---
name: gh-pages-unifuncs-publisher
description: Publish article markdown to GitHub Pages and then push to UniFuncs. Input should be keyword and article.md path.
---

# GitHub Pages + UniFuncs Publisher

## Purpose

Take minimal user input (`keyword`, `article.md`) and complete:
1. Publish markdown as a page on GitHub Pages
2. Push published URL to UniFuncs
3. Return publish URL and UniFuncs task result

## Inputs

Required from user:
1. `keyword`
2. `article_md` (workspace path)

Settings-driven (from `setting.json`):
1. `github.token`
2. `unifuncs.api_key`
3. Optional defaults (repo, branch, language, prompt, promotion fields)

## Mandatory Flow

1. Ensure `setting.json` exists (copy from `setting.json.example` if needed).
2. Ask user only for `keyword` and `article_md`.
3. Execute publish command.
4. Report:
- `publish_url`
- `unifuncs.data.task_id` when present
- full error payload on failure

## Command

```powershell
powershell -ExecutionPolicy Bypass -File .\cil\cil-gh-pages-publisher.ps1 publish --keyword "<KEYWORD>" --article_md "<ARTICLE_MD_PATH>" --setting_file ".\setting.json"
```

## Dry Run

```powershell
powershell -ExecutionPolicy Bypass -File .\cil\cil-gh-pages-publisher.ps1 publish --keyword "<KEYWORD>" --article_md "<ARTICLE_MD_PATH>" --setting_file ".\setting.json" --dry_run
```
