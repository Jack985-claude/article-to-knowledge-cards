---
name: make-knowledge-cards
description: "Turn pasted articles or local Markdown/TXT files into a small set of faithful knowledge cards. Use when the user wants to extract, study, or review the important ideas in supplied text; do not use for web retrieval or scraping, PDFs, Anki export, or GUI work."
---

# Make Knowledge Cards

Convert one supplied article into a concise, source-faithful set of knowledge cards. The goal is useful learning material, not a paragraph-by-paragraph summary.

## Supported input

- Accept article text pasted into the conversation.
- Accept a local `.md`, `.markdown`, or `.txt` file path. Read its text before extracting cards.
- If both pasted text and a file path are supplied without instructions about their relationship, ask whether to combine them or choose one; do not silently merge sources.
- If the user supplies a URL, PDF, Anki request, or GUI request, explain that it is outside this skill's scope and offer the supported alternative: pasted text or a local Markdown/TXT file.
- If a local path is missing, unreadable, or has an unsupported format, say so and ask for a supported input. Do not guess its contents or use another source to fill the gap.

## Extract before writing

1. Identify the article's central claim, essential concepts, mechanisms or steps, constraints, and source-supported examples. Treat headings and formatting as context, not as a card outline.
2. Form atomic candidate knowledge points. Prefer points that are central to the argument, explain a dependency or decision, define a necessary term, describe a mechanism, or set an important limit or exception.
3. Merge candidates that teach the same thing. Keep the more fundamental point as the card, and place genuinely necessary supporting detail in its explanation. Do not make separate cards for restatements, introductions, transitions, or minor facts.
4. Select the highest-value distinct points. Aim for 5–8 cards only when the article supports that many. When fewer than five genuinely important, distinct points are present, return fewer cards rather than padding with trivia or invented detail. When more than eight qualify, keep the eight most useful points and omit lower-value detail.

## Preserve fidelity

- Every title, core statement, explanation, and example must be directly supported by the supplied article. Paraphrase clearly, but do not import background knowledge, make stronger causal claims, resolve ambiguities, or invent context.
- Give each card exactly one teachable knowledge point. A card may include related detail only when it is needed to explain that same point.
- Use an example only if the article explicitly provides it. Otherwise use a self-test question that can be answered from the article; the question must not introduce new facts or scenarios.
- If the source is incomplete, uncertain, or internally qualified, preserve that limitation instead of filling it in.
- If no important, verifiable knowledge point can be extracted, explain that the supplied content is insufficient and do not create filler cards.

## Output format

Start with `# 知识卡片`. If the source has too little material for five cards, briefly state that only the supported number is being returned. Then use this format for every card:

```markdown
## 卡片 1｜<短而明确的标题>
- 核心知识：<一个可独立成立的关键观点>
- 简明解释：<用原文信息说明含义、机制、条件或作用>
- 例子或自测问题：<原文中的例子；或可由原文回答的单个问题>
```

Keep wording compact and study-ready. Do not add a second summary that repeats the cards.

## Final check

Before responding, verify that every card has all four required parts, contains one non-overlapping point, and is traceable to the supplied text. Remove any card or phrase that relies on information outside the source.
