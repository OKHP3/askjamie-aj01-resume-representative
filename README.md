# AskJamie™ — GPT‑AJ01: Résumé Representative  
**Your résumé, reimagined as an AI agent.**

GPT‑AJ01 turns a static résumé into a living, conversational career representative that can help draft role‑specific résumés, cover letters, interview answers, and recruiter‑ready talking points — in your voice.

This repo is the **storage + version history** for the GPT‑AJ01 blueprint: system prompts, curated knowledge files, a build & usage playbook, and evaluation tests. It’s designed so you can maintain a **base agent** and create **job‑specific clones** tuned to each opportunity.

---

## Canonical links (source of truth)
- **Lens page (public):** https://askjamie.bot/lens-system/resume-representative/  
- **Live demo GPT:** https://chatgpt.com/g/g-691fb05c86c881919eec171e62fe1e00-resume-representative-by-askjamietm  
- **Notion brief (internal):** https://www.notion.so/overkillhill/AJ01-R-sum-Representative-514a9d658325466ca36aba2bb864fd9d  
- **Support / tips:** https://ko-fi.com/overkillhillp3  
- **Contact:** contact@askjamie.bot  

---

## What’s in this repository
- `prompts/` — instruction architecture: role, tone, guardrails, workflows  
- `knowledge/` — knowledge starter kit (modern hiring, ATS‑friendly structure, dynamic cover letters, compensation framing, interview prep patterns)  
- `playbook/` — build & usage guide: how to create your own custom GPT, attach knowledge, test, refine, and share safely  
- `eval/` — regression prompts + rubrics (quality and drift control)  
- `build/` — compiled “packs” ready to upload into a Custom GPT (few files, big coverage)  
- `ops/` — release checklist + maintenance notes

---

## Quickstart (build your own résumé representative)
1) Start with the **base agent**: review `prompts/` and the latest files in `build/`.  
2) Create a Custom GPT in ChatGPT and upload the `build/` packs as Knowledge.  
3) Run the tests in `eval/` to verify tone, accuracy, and guardrails.  
4) For a specific job: provide the job description + company context and generate a tailored résumé, cover letter, and talking points.  
5) **Clone the agent** per opportunity (rename it per role/company) so each hiring team can interact with the most relevant “version of you.”

---

## Status
⚠️ Work‑in‑progress. Sections and flows may move as the AJ01 lens is wired up.

---

## Privacy & data handling (recommended)
If you use real career history, **don’t commit sensitive personal data** to a public repo. Use redacted examples here and keep private source files in a private repo or encrypted storage.

---

© 2025 AskJamie™. All rights reserved.
