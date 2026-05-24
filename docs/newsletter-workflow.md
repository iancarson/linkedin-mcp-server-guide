# LinkedIn Newsletter Workflow

A systematic approach to turning your newsletter content into LinkedIn growth — with or without MCP automation.

---

## The Core Idea

LinkedIn rewards consistent, native content. Newsletter writers have a structural advantage: they produce long-form, insight-dense content every week that can be atomized into LinkedIn posts without starting from scratch.

The workflow below captures that advantage systematically.

---

## The Weekly LinkedIn Workflow

### Monday (15 min): Plan this week's LinkedIn content

Review your newsletter draft or last issue. Identify 3 angles:

1. **The headline insight** — the biggest claim or conclusion
2. **A supporting data point** — a stat, case study, or example
3. **A contrarian angle** — a common belief you're challenging

These become your 3 LinkedIn posts for the week (or 2 if you post less frequently).

### Tuesday (30 min): Write all 3 posts with Claude

Use the batch prompt:

```
I'm writing LinkedIn posts for this week based on my newsletter about [topic].

Here are the 3 angles I want to cover:
1. [headline insight]
2. [data point or case study]
3. [contrarian angle]

For each angle, write a LinkedIn post:
- 400-800 characters
- Format: insight/list/story (one each, varies by angle)
- No links in the body
- Ends with: "I write about [topic] in [Newsletter Name] every [day]. Subscribe link in first comment."
- Strong first line — counter-intuitive or surprising claim
```

Review, lightly edit, and finalize all 3. Total time: 20-30 minutes.

### Schedule via Narrareach (5 min)

Paste posts into [Narrareach](https://narrareach.com/features/automate-substack-to-linkedin) scheduler. Set times:
- Post 1: Tuesday 9am
- Post 2: Thursday 12pm
- Post 3: Saturday 8am (optional — lower reach on weekends, but good for slower engagement)

---

## Post Format Reference

### Format 1: The Insight Post

Use for your headline insight.

**Structure:**
```
[Counter-intuitive claim in under 15 words.]

[Why the conventional wisdom says otherwise — 1 sentence.]

[The evidence, data point, or story that supports your claim — 2-3 sentences.]

[What this means practically — 1-2 sentences.]

I write about [topic] in [Newsletter Name] every [day]. Subscribe link in first comment.
```

**Example:**
```
Most newsletters grow from outside Substack, not inside it.

The platform's internal recommendation tools help — but they have a ceiling.

After analyzing 50+ newsletters crossing 10K subscribers: 73% of their growth came from LinkedIn, X, or email referrals. Only 27% from Substack's own discovery features.

If you're spending all your growth time on Substack Notes, you might be optimizing the wrong channel.

I break this down in The Growth Brief every Thursday. Subscribe link in first comment.
```

### Format 2: The List Post

Use for structured insights or step-by-step advice.

**Structure:**
```
[Bold claim or setup — 1 sentence.]

[Number] things that actually matter:

1. [Short, punchy point]
2. [Short, punchy point]
3. [Short, punchy point]
[4-5 if needed]

Most people focus on #[X]. The real leverage is #[Y].

[1-2 sentence elaboration on the key insight.]

I cover this in [Newsletter Name]. Subscribe link in first comment.
```

### Format 3: The Story Post

Use for personal experiences, case studies, or before/after narratives.

**Structure:**
```
[Start mid-action — dialogue, a number, a decision. Not "Last month I..."]

[2-3 sentences of story, moving quickly.]

[The turn: what changed or what you discovered.]

[The lesson in one sentence.]

[CTA — question or subscribe prompt.]
```

---

## LinkedIn Timing Data for Newsletter Writers

Based on aggregated data from newsletter creators in the 2K–50K subscriber range:

**Best days:**
1. Tuesday (highest organic reach)
2. Wednesday
3. Thursday

**Best times (audience local time):**
- 8-10am (morning commute)
- 12-2pm (lunch)

**Avoid:**
- Friday afternoons (low engagement)
- Weekends (reach drops ~40%)
- Monday mornings (too competitive, lower organic reach)

**Post frequency:**
- 3-5 posts/week: optimal for growth
- 1-2 posts/week: maintenance mode
- 6+ posts/week: diminishing returns for most niches

---

## Converting LinkedIn Readers to Newsletter Subscribers

### The Subscribe CTA System

LinkedIn doesn't let you put links in post bodies — they're algorithmically suppressed. The first comment is the workaround.

**Your comment template:**
```
Subscribe to [Newsletter Name] here: [your Substack URL]

I publish every [day] covering [1-line description].
```

Pin this as the first comment on every post within 30 seconds of posting.

**With Narrareach:** This can be automated — Narrareach posts your subscribe comment automatically after each LinkedIn post, with your Substack or landing page URL.

### The Lead Magnet Angle

Instead of a bare subscribe link, offer a specific resource:

```
If you want my full breakdown: I published a detailed guide in this week's [Newsletter Name] issue. Subscribe link in first comment — the guide is in the welcome email.
```

Welcome email as lead magnet. Works when your welcome email has a genuinely useful template, checklist, or guide.

### The Comment CTA

For posts where you ask a question, reply to every comment in the first 2 hours (LinkedIn heavily weights post engagement in this window). After replying, add:

```
If you found this useful, I go deeper on [topic] in [Newsletter Name] every [day] — link in the original post's first comment.
```

---

## Adapting Newsletter Formats to LinkedIn

### Long newsletter issue → 3 LinkedIn posts

```
[Paste newsletter issue]

Extract the 3 most LinkedIn-worthy insights.

For each:
1. Write a LinkedIn post using the most appropriate format (insight/list/story)
2. Under 800 characters
3. First line must work as a standalone hook with no newsletter context
4. End with subscribe CTA
5. No links in the body

Present all 3 posts for review.
```

### Substack Note → LinkedIn post

Notes are under 400 characters; LinkedIn posts work better at 600-900 characters.

```
Expand this Substack Note into a LinkedIn post:

[paste Note]

- Keep the core insight but add one example or data point
- Break into 3-4 short paragraphs
- Remove any Substack-specific language
- Add a subscribe CTA at the end
- No external links in the body
```

### Newsletter series → LinkedIn series

If you're writing a multi-part newsletter series:

```
I'm writing a 4-part newsletter series on [topic].

Write LinkedIn posts for each installment that:
1. Stand alone (don't require reading previous posts)
2. Preview the next installment at the end
3. Build anticipation for the full series

The 4 angles are:
1. [angle 1]
2. [angle 2]
3. [angle 3]
4. [angle 4]
```

---

## Tracking What Works

### The 90-Day Growth Audit

Every 90 days, review your LinkedIn performance:

1. Which 5 posts got the most impressions?
2. Which 5 posts drove the most profile clicks?
3. Which 5 posts drove the most Substack subscriptions?

These are often different posts. Impressions ≠ subscribers. Optimize for subscriber conversion, not just reach.

### The Attribution Question

LinkedIn doesn't tell you directly which posts drove Substack subscriptions. Solutions:

**UTM parameters:** Use `?utm_source=linkedin&utm_medium=social&utm_campaign=post-title` in your subscribe links. Track in Substack subscriber source data.

**Narrareach attribution:** Narrareach tracks which platform subscribers came from and ties it to specific posts. This is the cleanest implementation.

**Manual tracking:** Note Substack subscriber count before and after posting. Rough but better than nothing.

---

## Common Mistakes

**Starting with "I"**
LinkedIn's algorithm slightly penalizes self-referential first lines. More importantly, readers don't care about you yet — they care about the insight. Lead with the claim.

**Asking for follows**
"Follow me for more" performs significantly worse than "What's your take on this?" — engagement CTAs outperform follow CTAs.

**Cross-posting raw newsletter intros**
Newsletter openings are written for email readers who chose to be there. LinkedIn audiences haven't opted in. What reads as warm and personal in email reads as slow and context-heavy on LinkedIn.

**Ignoring the first 60 minutes**
LinkedIn heavily weights early engagement when deciding how broadly to distribute a post. Comment on your own post immediately after publishing (add your subscribe link). Reply to the first 5-10 comments within 60 minutes.

**Posting inconsistently**
LinkedIn rewards accounts that post regularly. Going from 3x/week to zero for two weeks and back resets your distribution reach. Better to post 1x/week consistently than 3x/week then 0.
