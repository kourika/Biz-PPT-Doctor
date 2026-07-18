# Chinese Typography (中文排版规范)

International AI presentation tools consistently handle this badly — rendering is stiff, spacing rules get ignored, and the result reads as translated rather than native. This file exists so decks in Chinese don't inherit those defaults.

## Font pairing

- Headings: a Chinese sans-serif with real weight range — Source Han Sans (思源黑体) / Alibaba PuHuiTi (阿里巴巴普惠体) / PingFang (苹方, macOS) — set **Bold or Medium**, not the default Regular pulling double duty as a "heavy" weight.
- Body: the same family at Regular, or a slightly more neutral sans if the heading font is very stylized. Don't pair a Chinese sans heading with a Chinese serif body unless the deck is intentionally editorial (rare for workplace decks).
- Never use a Latin font's fallback rendering for Chinese characters — if a font doesn't ship proper Chinese glyphs, the system substitutes something inconsistent with the rest of the design. Confirm CJK coverage before committing to a font.
- Two families maximum for the whole deck: one for headings, one for body/labels. A third "accent" font is a common way decks quietly become inconsistent.

## Sizing and hierarchy

- Titles: 32–40pt. Body: 16–20pt. Captions/sources: 10–12pt. Keep at least a 2-step visual jump between title and body — a title only a few points larger than body text doesn't read as a hierarchy.
- Chinese characters read denser than Latin text at the same point size — when a slide feels crowded, check point size before assuming the content itself needs cutting.

## Line spacing

- 1.3–1.5x line height for body paragraphs. Below 1.2x, characters crowd vertically; above 1.6x, dense Chinese paragraphs start to feel disconnected line to line.
- Space bulleted items with consistent paragraph spacing (not line-height hacks) — mixing the two produces uneven-looking gaps between bullets.

## Mixed Chinese/English/number text

- Add a small visual gap (a genuine thin space or letter-spacing, not literal ASCII spaces stacked) between Chinese characters and adjacent Latin letters or digits — "2024年Q3增长18%" reads better with light separation around "2024", "Q3", and "18%" than jammed against the Chinese characters on both sides.
- Never break a line so a single Chinese character is orphaned alone on the next line (孤字/寡字). Check line breaks near the end of wrapped Chinese text specifically — this is the most common overlooked defect.
- Use full-width punctuation（，。：；！？「」）for Chinese sentences and half-width punctuation for embedded English/numeric fragments — don't mix a half-width comma into a Chinese sentence.

## Avoid the "AI味" look

These are the specific, nameable tells that make a deck read as AI-generated filler rather than a real business document — avoid all of them by default:

- Generic stock photography that doesn't depict the user's actual business: handshake photos, gear/globe icons, "business people pointing at a chart" images, abstract circuit-board backgrounds.
- Decorative accent bars or edge stripes with no informational purpose.
- Charts with fabricated-looking data (perfectly round numbers, suspiciously smooth trend lines) standing in for real numbers.
- A cover slide with a beautiful abstract background and a title, followed immediately by dense plain-bullet slides with no visual continuity — commit to one level of design polish throughout, not just the cover.

## Quick self-check before calling a deck done

1. Read every wrapped line — any orphaned single characters?
2. Count font families used — more than 2?
3. Pick any two body slides at random — same title size, same body size, same line spacing?
4. Any number on the deck without a visible source or obvious first-party origin?
