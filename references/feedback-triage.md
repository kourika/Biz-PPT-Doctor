# Feedback Triage (审阅意见转化)

The pain here isn't the feedback itself — it's that reviewers hand over an unordered dump of comments (chat messages, meeting notes, marked-up screenshots) and the presenter has to reconstruct what to actually do with them. This file is that reconstruction step.

## Step 1: Collect everything verbatim first

Don't start classifying while still gathering — get the complete set of comments in front of you before triaging any of them. Partial triage causes rework when comment #14 turns out to contradict how you already resolved comment #3.

## Step 2: Classify each comment

| Type | What it is | How to handle it |
|---|---|---|
| **逻辑问题** | Challenges the argument itself — wrong conclusion, missing step, unsupported leap | Highest priority. May require restructuring per `logic-frameworks.md`, not just editing the slide it was left on |
| **事实错误** | A number, date, name, or claim is wrong | Fix directly; verify against source before changing, don't just trust the reviewer's replacement number without checking |
| **表达问题** | The point is right but unclear, too dense, or ambiguously worded | Rewrite for clarity; usually the cheapest fix |
| **风格偏好** | Subjective taste — color, font, "make it feel more premium" | Flag as negotiable, not wrong. Don't silently apply — confirm with the user, since another reviewer's taste may conflict |

Comments that don't fit cleanly (e.g., a reviewer asking a question rather than stating a problem) go in their own bucket — don't force them into one of the four types.

## Step 3: Map every comment to a slide and an action

Output one row per comment, not one row per reviewer or per theme — themes can hide the fact that two different comments on the same slide need different, possibly conflicting fixes.

