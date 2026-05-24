# Claude Prompts for LinkedIn Newsletter Content

Ready-to-use prompts for writing LinkedIn content from your newsletter with Claude. Works standalone or with a configured agent.

---

## Core Adaptation Prompts

### Newsletter section → LinkedIn post

```
Convert this newsletter section into a LinkedIn post.

Section:
[paste section]

Requirements:
- First line: the most surprising or counterintuitive claim (under 15 words, no "I" as first word)
- 400-800 characters total
- 3-4 short paragraphs, maximum 3 sentences each
- No external links in the body
- End with: "I write about [topic] in [Newsletter Name] every [day]. Subscribe link in first comment."
- Match a professional but direct, first-person tone
- Remove any Substack-specific references
```

### Full issue → 3 LinkedIn posts

```
I'm going to paste my newsletter issue below. Extract the 3 best LinkedIn angles.

For each angle, write a LinkedIn post using a different format:
- Post 1: Insight format (lead with a counterintuitive claim)
- Post 2: List format (numbered insights or steps)
- Post 3: Story format (open mid-action, not "Last month I...")

Requirements for each:
- 400-800 characters
- First line must work with no newsletter context
- No links in the body
- Subscribe CTA at the end
- No "I" as the first word

Newsletter issue:
[paste issue]
```

### Substack Note → LinkedIn post

```
Expand this Substack Note into a LinkedIn post.

Note:
[paste Note — under 400 characters]

Notes are written for Substack readers. This LinkedIn post is for a different audience.

Expand it by:
1. Adding one example, data point, or story (make one up or I'll provide — ask me if needed)
2. Breaking into 3-4 paragraphs
3. Removing any Substack-specific language (restacks, Notes, etc.)
4. Adding: "I write about [topic] in [newsletter] every [day]. Subscribe in first comment."

Target length: 600-900 characters.
```

---

## Batch Content Prompts

### Sunday batch: 5 LinkedIn posts from 1 newsletter

```
I want to write 5 LinkedIn posts for the coming week based on my newsletter topic: [topic]

Write 5 posts, each using a different format:
1. Counter-intuitive claim + evidence
2. Numbered list (5-7 items)
3. Before/after story
4. Question + my answer (controversial take)
5. Data-driven insight

Rules for all posts:
- 400-800 characters
- First line must stop the scroll
- No "I" as the first word
- No links in the body
- Each ends with a subscribe CTA
- Each stands alone — no "continuing from yesterday" framing

Suggested scheduling:
- Post 1: Monday 9am
- Post 2: Tuesday 12pm
- Post 3: Wednesday 9am
- Post 4: Thursday 12pm
- Post 5: Friday 10am
```

### Generate hook variations

```
I want to write a LinkedIn post about [specific insight or claim].

Give me 8 different first-line options:
- 2 counterintuitive claims
- 2 surprising statistics (approximate is fine)
- 2 story openers (start mid-action)
- 1 question
- 1 bold statement under 10 words

I'll pick the best one and write the rest of the post around it.
```

---

## Format-Specific Prompts

### The Insight Post

```
Write a LinkedIn insight post about [topic].

Structure:
1. Counter-intuitive claim as the first line (under 15 words)
2. Why most people believe the opposite (1 sentence)
3. The evidence, data, or story (2-3 sentences)
4. What this means practically (1-2 sentences)
5. Subscribe CTA

Total: 500-800 characters. No "I" as the first word. Direct, confident tone.
```

### The List Post

```
Write a LinkedIn list post about [topic].

Structure:
1. Bold setup claim (1 sentence)
2. "X things that [result/outcome]:" header
3. 5-7 short list items (each under 15 words)
4. "Most people focus on #[X]. The real leverage is #[Y]." conclusion
5. 1-2 sentence elaboration on the key item
6. Subscribe CTA

Total: 600-900 characters. Scannable. Mobile-friendly formatting.
```

### The Story Post

```
Write a LinkedIn story post about [specific situation, experience, or case study].

Rules:
- Open with action, dialogue, or a number — NOT "Last month" or "A few years ago"
- 3-4 short paragraphs
- The turn must be in paragraph 2 or 3 (not the last line)
- End with a 1-sentence lesson
- Close with an engagement CTA or subscribe CTA
- 400-700 characters total
- First-person but doesn't start with "I"
```

### The Contrarian Take

```
Write a LinkedIn contrarian post on this topic: [topic]

Structure:
1. "Hot take: [popular belief] is [wrong/overrated/missing the point]."
2. My argument: [2-3 bullet points]
3. The steelman: [acknowledge the strongest counterargument, 1-2 sentences]
4. What I actually believe: [nuanced position]
5. "Disagree? Tell me why below." or similar engagement CTA

600-800 characters. Confident but not dismissive.
```

---

## Repurposing Prompts

### Newsletter series → LinkedIn series

```
I'm writing a [X]-part newsletter series on [topic].

Plan a LinkedIn content series that accompanies it:
- Each LinkedIn post stands alone (no "Part 2 of 4" framing)
- Each post covers a different aspect of [topic]
- Together they build anticipation for the full newsletter series
- Last post in the LinkedIn series links to the newsletter

Draft all [X] posts following these rules:
- 400-700 characters each
- Different formats (insight/list/story — vary them)
- End of each post previews what's coming
- Subscribe CTA in final post

Newsletter series topic breakdown:
Part 1: [angle]
Part 2: [angle]
Part 3: [angle]
[continue as needed]
```

### Newsletter → monthly LinkedIn batch

```
I'm going to paste my last 4 newsletter issues. I want to create a month of LinkedIn content from them.

For each issue, identify the single best LinkedIn angle.

Then write 12 LinkedIn posts total:
- 4 insight posts (one main claim from each issue)
- 4 list posts (structured advice from each issue)
- 4 story posts (one example or case study from each issue)

I'll schedule 3 per week.

Issues:
[paste issues or list topics]
```

---

## Analytics and Optimization

### Analyze what worked

```
Here are my 10 best-performing LinkedIn posts from the last 90 days (ordered by impressions):

[paste post text or summaries]

Analyze:
1. What formats appear most often in the top 5?
2. What topics appear most often in the top 5?
3. What first-line patterns appear in the top performers?
4. What's different about the bottom 5?

Give me 3 specific recommendations for what to write more of next month.
```

### Optimize an underperforming post

```
This LinkedIn post got low engagement. Rewrite it to perform better.

Original post:
[paste post]

Performance: [impressions / comments / shares — whatever you know]

Likely issues to check:
- Is the first line strong enough?
- Is it too long or dense?
- Does it lack a clear CTA?
- Is the topic interesting to a LinkedIn audience?

Rewrite with fixes. Explain what you changed and why.
```

---

## Distribution Note

These prompts cover the writing step. For reliable scheduled publishing to LinkedIn with official API access (no ToS risk, no token rotation), pair with [Narrareach](https://narrareach.com). Claude writes; Narrareach distributes.
