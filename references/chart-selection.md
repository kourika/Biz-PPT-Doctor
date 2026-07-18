# Chart Selection (数据图表选型)

The recurring failure mode isn't "no chart" — it's a chart chosen for how it looks rather than what it needs to prove. A chart on a business slide exists to make one specific claim obvious in under three seconds; if a viewer has to study it, the wrong type was probably picked, or too much was crammed into it.

## Pick by claim, not by data type

| The claim is... | Use | Not |
|---|---|---|
| "A dominates the others" | Bar chart (sorted descending), or a single callout stat if it's really just one number | Pie chart with many similar-sized slices |
| "This changed over time" | Line chart | Bar chart per period (fine for ≤4 periods, gets noisy beyond that) |
| "These parts make up a whole" | Stacked bar (if also comparing across categories) or a simple donut *only* if there are ≤4 segments | Pie chart with more than 4–5 slices — beyond that, differences under ~5% become visually indistinguishable |
| "These two things move together / trade off" | Scatter plot, or dual-axis line only if the two series have genuinely comparable scales | Two separate charts the viewer has to mentally overlay |
| "Here's the breakdown of one category across sub-groups, at one point in time" | Horizontal bar, sorted | Radar/spider chart — reads as impressive, rarely reads as clear |
| "Here's a single important number" | A large callout number with one line of context, no chart at all | Any chart — a chart implies comparison; a lone number doesn't need one |

## One chart, one message

Every chart should have the takeaway annotated directly on it — a title above the chart stating the conclusion (an action title, per `logic-frameworks.md`), and where relevant, the single most important data point called out visually (highlighted bar, labeled peak) rather than left for the viewer to find. A chart with no annotated takeaway is asking the audience to do the analysis live, in the room.

## Data integrity

- Real data only. A chart built from placeholder or estimated numbers should say so explicitly (a footnote: "示意数据，待补充实际数字") rather than presenting a guess as fact — this is the single biggest driver of the "AI生成的PPT看起来很假" complaint: charts that are clearly not real data pretending to be.
- Match axis scales to the actual range of the data — starting a bar chart's axis somewhere other than zero (when comparing magnitudes) visually exaggerates differences and reads as manipulative even if unintentional.
- Label units explicitly (%, 万元, 同比/环比) — an unlabeled number forces the viewer to guess what it means.

## When in doubt, use a table

If the data has more than ~2 dimensions the audience needs to cross-reference (e.g., 5 products × 4 quarters × 2 metrics), a well-formatted table often communicates faster than forcing it into a chart type that wasn't built for that many dimensions. A chart that needs a paragraph of explanation to interpret has failed at its one job.
