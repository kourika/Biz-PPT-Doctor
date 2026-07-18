---
name: biz-deck-doctor
description: "Content diagnosis and audit coach for workplace reports and business proposal presentations (职场汇报, 商业提案, 述职, 项目复盘). Use this skill whenever the user wants to turn raw material (meeting notes, data, reports) into a logically structured outline BEFORE building slides; wants an existing .pptx/.ppt reviewed, audited, diagnosed, or '体检' for logic, design consistency, data credibility, or Chinese typography problems; needs to triage a pile of reviewer or boss feedback (老板意见/评审意见/导师意见) into concrete per-slide fixes; needs help choosing the right chart type for data; or needs a speaker script matched to a deck's timing. Trigger on phrases like '这个PPT怎么样' '帮我看看这份PPT' 'PPT逻辑不清楚' '大纲怎么搭' '老板给了一堆意见改不过来' '这页用什么图表' — even if the user never says 'audit' or 'diagnose' explicitly. This skill owns CONTENT and STRUCTURE, not file generation: pair it with Anthropic's built-in pptx skill (or another pptx-generation skill) to actually create or edit the .pptx file."
license: MIT — see LICENSE
---

# Biz Deck Doctor

A content coach for workplace and business presentations. It does not generate or edit `.pptx` files — it decides what should be on the slides and whether an existing deck is actually good, then hands the technical work to the `pptx` skill.

**Why this exists:** most presentation pain isn't a file-format problem. It's unclear logic, no story, endless unstructured revision rounds, and design/typography mistakes nobody can name. This skill treats those as first-class problems instead of assuming a prettier template fixes them.

## Route first

| The user has... | Enter | Then read |
|---|---|---|
| Raw material, no deck yet (notes, data, a report, a rough idea) | **Mode 1 — Content Diagnosis** | `references/logic-frameworks.md` |
| An existing `.pptx`/`.ppt`, wants to know if it's good / what's wrong | **Mode 2 — Deck Audit** | `references/audit-rubric.md` |
| A pile of reviewer/boss/advisor comments, doesn't know how to act on them | **Mode 3 — Feedback Triage** | `references/feedback-triage.md` |
| A chart to pick, or a speaker script to write | **Add-on capabilities** | `references/chart-selection.md`, [Speaker scripts](#speaker-scripts) below |

A single request often needs more than one mode in sequence — e.g. diagnose content, hand off for slide generation, then later audit the result. Don't force a single-mode answer if the user's situation spans more than one row above.

Before doing anything content-specific, check whether a scenario pack applies — see [Scenario packs](#scenario-packs). Always apply `references/chinese-typography.md` when the deck is (or will be) in Chinese.

---

## Mode 1 — Content Diagnosis

Goal: produce a structured, defensible outline *before* anyone opens a slide tool. Skipping this is the single biggest cause of the "5 hours a week reformatting, 30% of it pointless" problem — people redesign because the underlying argument was never solid.

1. **Gather the raw material.** Ask for what exists (notes, data, a report, a transcript) rather than inventing content. If the user only has a topic and no substance, say so plainly — a deck with no real content behind it is the "AI味" problem in disguise, not a design problem. Don't manufacture fake data, fake quotes, or fake stats to fill gaps; flag the gap and ask, or mark it as `[NEEDS DATA]`.
2. **Structure the argument**, not the slides. Apply SCQA or the Pyramid Principle per `references/logic-frameworks.md`. Every deck should reduce to one governing message; every section should reduce to one sub-message.
3. **Write action titles.** Each slide title states the takeaway, not the topic ("Q3获客成本下降18%，主要来自私域渠道" not "Q3数据概览"). See `references/logic-frameworks.md` for the method and a before/after table.
4. **Run the ghost-deck test.** Read only the titles in sequence, nothing else. If they don't tell the full story on their own, the structure isn't done — fix it here, before slides exist, where it's cheap to fix.
5. **Check for a scenario pack** (`references/scenarios/`) and apply its structure conventions.
6. **Confirm the outline with the user** before generating anything. Show: governing message, section messages, per-slide action titles, and any `[NEEDS DATA]` flags.
7. **Hand off.** Once confirmed, use the `pptx` skill (or whichever generation skill is available) to build the actual file from this outline. Don't build the file yourself from inside this skill.

## Mode 2 — Deck Audit ("体检")

Goal: score an existing deck against explicit, checkable criteria and return a **prioritized, page-numbered** fix list — not vague praise or vague criticism. This is the mode most existing PPT tools skip entirely; they only generate, never diagnose.

1. Read the deck. Use the `pptx` skill's own reading approach: `markitdown deck.pptx` for text content, `python scripts/thumbnail.py deck.pptx` (from the pptx skill) for a visual grid if visual issues are in question.
2. Score against the four dimensions in `references/audit-rubric.md` (逻辑结构 / 设计一致性 / 数据可信度 / 中文排版规范). Give each dimension a score and the specific evidence for it — never a bare number.
3. Output format, always:
   - One-line overall verdict (what's the biggest problem, in one sentence)
   - Score table (4 dimensions)
   - Fix list sorted by priority: **structural fixes first** (wrong message, wrong order, missing evidence), then **design fixes** (inconsistency, density, contrast), then **polish** (wording, spacing). Each item names the slide number.
4. Don't rewrite the whole deck unprompted. Give the list, let the user decide what to act on, then execute only the fixes they confirm (via the `pptx` skill for the actual edits).

## Mode 3 — Feedback Triage

Goal: turn an unstructured pile of comments into a slide-by-slide action list. This directly targets the multi-round-review problem — reviewers rarely organize their own feedback, and untangling it manually is where hours disappear.

1. Collect all feedback verbatim (paste, screenshot transcription, meeting notes).
2. Classify each comment per `references/feedback-triage.md`: 逻辑问题 (the argument itself) / 事实错误 (wrong numbers or claims) / 表达问题 (unclear wording) / 风格偏好 (subjective taste — flag these separately, they're negotiable, not "wrong").
3. Map every comment to a specific slide and a specific action. Comments that conflict with each other or with the deck's stated goal get flagged for the user to decide, not silently resolved either way.
4. Output a checklist, grouped by slide, ordered the same way the deck is ordered (so the user can walk through it top to bottom).

---

## Scenario packs

| Scenario | File |
|---|---|
| 职场汇报（周报/月报/项目复盘/述职） | `references/scenarios/workplace-report.md` |
| 商业提案（产品方案/合作提案/预算申请） | `references/scenarios/business-proposal.md` |

If the user's scenario isn't covered yet, say so and fall back to the general logic-framework guidance rather than guessing at conventions this skill doesn't actually know.

## Speaker scripts

When asked for a matching script (讲稿/自述稿), work from the *final* action-title outline, not a fresh summary of the topic — the script should track exactly what's on each slide. Ask for (or infer from context) a time budget, then target roughly 120–150 spoken Chinese characters per minute per speaker to size each slide's script. Flag any slide where the script would need to run drastically faster than that pace — it's a sign the slide is overloaded, not a scripting problem.

## What this skill does not do

- Does not write `pptxgenjs`/`python-pptx` code or touch OOXML — that's the `pptx` skill's job.
- Does not invent data, quotes, or statistics to fill a content gap.
- Does not silently rewrite a deck's message to make it more impressive than the underlying substance supports.
