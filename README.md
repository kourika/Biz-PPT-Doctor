# Biz Deck Doctor

A [Claude Skill](https://www.anthropic.com/news/skills) that diagnoses and audits workplace/business presentations in Chinese — before or after the slides exist. It doesn't generate `.pptx` files itself; it decides what should be on them, and pairs with Anthropic's official [`pptx` skill](https://github.com/anthropics/skills) (or any other pptx-generation skill) to actually produce or edit the file.

## Why this exists

Most "AI一键生成PPT" tools solve the file-generation problem and stop there. But the research behind this skill (10+ rounds of searching real user complaints, tool reviews, and the existing Claude-skill ecosystem) kept surfacing the same pattern: the pain isn't the file format, it's

- content with no real argument behind it, propped up by design effort
- reviewing an existing deck and not being able to say *specifically* what's wrong with it, beyond "it doesn't feel right"
- a pile of unstructured feedback from a boss/advisor that takes hours to turn into actual edits
- Chinese typography and layout getting treated as an afterthought by English-first tools
- charts picked for how they look rather than what they need to prove

Every existing "generate a deck" skill (there are dozens now) tries to solve all of this by generating better on the first try. This skill takes the opposite bet: **diagnose before and after, generate never** — and let a dedicated generation skill do what it's already good at.

## What it does

| Mode | Input | Output |
|---|---|---|
| **Content Diagnosis** | Raw material — notes, data, a report, a rough idea | A structured, defensible outline (governing message → action-title slides), confirmed with you before any file is built |
| **Deck Audit（体检）** | An existing `.pptx` | A scored, page-numbered, priority-ordered fix list across logic / design consistency / data credibility / Chinese typography |
| **Feedback Triage** | A pile of reviewer/boss comments | A slide-by-slide, deck-ordered action checklist, with conflicting feedback flagged instead of silently resolved |

Plus lighter add-ons: chart-type selection guidance, and speaker-script generation matched to a deck's actual timing.

## Install

**Claude Code / Claude Cowork:**
bash
git clone https://github.com/kourika/Biz-PPT-Doctor
cp -r Biz-PPT-Doctor ~/.claude/skills/biz-deck-doctor
git clone https://github.com/anthropics/skills
cp -r skills/skills/pptx ~/.claude/skills/pptx
