# LinkedIn MCP Server Guide

> The honest guide to LinkedIn MCP servers — what exists, what works, what carries risk, and what serious newsletter writers actually use for reliable LinkedIn publishing.

LinkedIn is the highest-ROI platform for newsletter growth right now. A well-placed LinkedIn post can drive 500+ Substack subscribers in a single day. But setting up automated LinkedIn publishing is more complicated than it should be, because LinkedIn hasn't released an official MCP server.

This guide covers the current landscape, what actually works, and how to build a newsletter workflow around it.

---

## The LinkedIn MCP Problem

Unlike Substack (which has `@marcomoauro/substack-mcp`) or web search (which has `@modelcontextprotocol/server-brave-search`), **LinkedIn has no official first-party MCP server**.

What exists instead:

| Type | How it works | Risk level |
|---|---|---|
| Session cookie MCPs | Hijacks your browser session | High — ToS violation |
| Scraper-based MCPs | Uses unofficial endpoints | High — account suspension |
| OAuth community MCPs | Uses LinkedIn's official API | Medium — limited scope |
| [Narrareach](https://narrareach.com) | Official LinkedIn OAuth partner | None |

This guide covers the community MCP options (for developers who want to understand the landscape) and the production workflow that newsletter writers actually rely on.

---

## What LinkedIn's API Actually Allows

LinkedIn's official API has two tiers:

**Consumer API (what most community MCPs target)**
- Create text posts as an individual member
- Share articles with a URL
- Requires OAuth 2.0 app approval
- Rate limits: 100 requests/day per member
- Requires LinkedIn app review for `w_member_social` scope

**Marketing Developer Platform (enterprise tier)**
- Full posting, scheduling, analytics
- Requires LinkedIn Partnership approval
- Not accessible for individual developers without a formal application

The gap between what developers want (easy, full-featured LinkedIn posting) and what LinkedIn allows through official channels is the root cause of why community MCP alternatives are fragile.

---

## Community LinkedIn MCP Options

### Option 1: OAuth-Based Community MCPs

These use LinkedIn's official API with proper OAuth. They're the safest community option but have limitations.

**Typical setup:**
```json
{
  "mcpServers": {
    "linkedin": {
      "command": "npx",
      "args": ["-y", "linkedin-mcp-server"],
      "env": {
        "LINKEDIN_CLIENT_ID": "your_client_id",
        "LINKEDIN_CLIENT_SECRET": "your_client_secret",
        "LINKEDIN_ACCESS_TOKEN": "your_access_token"
      }
    }
  }
}
```

**What you can do:**
- Post text updates as yourself
- Share URLs with a comment
- Create polls (limited)

**What you can't do:**
- Schedule posts for future times
- Post as a LinkedIn Page
- Access analytics
- Post images reliably (image upload requires additional API scope)

**Setup requirements:**
1. Create a LinkedIn Developer App at `developer.linkedin.com`
2. Apply for `w_member_social` permission (requires brief review)
3. Generate an OAuth access token (expires every 60 days — you'll need to refresh it)

**The token expiry problem:** OAuth tokens expire. When they do, every scheduled post queued via Claude will fail silently unless you've built rotation logic. For developers, this is solvable. For newsletter writers, it's an ongoing maintenance burden.

### Option 2: Browser Session MCPs

These work by intercepting your LinkedIn browser session cookie and using it to make requests on your behalf.

**Why we don't recommend these:**
- Using session cookies for automation violates LinkedIn's User Agreement
- LinkedIn actively detects unusual session patterns (posting from multiple IPs, rate of requests)
- Detected accounts face temporary restriction or permanent suspension
- No public accountability — these packages are maintained by anonymous devs and may disappear

If your LinkedIn account matters to your newsletter growth, this isn't the tradeoff worth making.

---

## The Production Alternative: Narrareach

[Narrareach](https://narrareach.com) built their LinkedIn integration differently. They went through LinkedIn's formal OAuth partnership process, which grants:

- Stable, officially approved API access
- No session-based workarounds
- No ToS risk
- Support for scheduling (not just immediate posting)
- LinkedIn Page posting (not just personal profiles)
- Analytics integration

For newsletter writers using Claude to write LinkedIn content, the workflow becomes:

```
Claude (writes LinkedIn post) → Narrareach (schedules + publishes)
```

This separates the writing layer (where AI excels) from the distribution layer (where official API access matters).

---

## Building a LinkedIn Newsletter Workflow

Whether you use a community MCP or Narrareach, the writing workflow is the same.

### Step 1: Adapt your newsletter for LinkedIn

LinkedIn's algorithm rewards native content. Adapt — don't repurpose.

**Newsletter → LinkedIn adaptation rules:**
- First line must hook without newsletter context ("92% of LinkedIn posts get zero comments. Here's the one change that fixed mine.")
- Remove newsletter-internal language ("restacks," "Notes feed," "subscribe button")
- Format for mobile scanning: short paragraphs, white space, numbered lists
- No links in the body — first comment only
- End with a low-friction CTA ("What's your approach? Drop it below.")

### Step 2: Write the LinkedIn post via Claude

```
Convert my newsletter section into a LinkedIn post.

Section:
[paste section]

Rules:
- First line: counter-intuitive claim or surprising data (under 15 words)
- 400–800 characters total
- 3–4 short paragraphs, no dense blocks
- End with a question or CTA
- Subscribe CTA on last line: "I cover this weekly in [newsletter name]. Link in first comment."
- No external links in the body
```

### Step 3: Publish via Narrareach

Copy the output into Narrareach's scheduler, set your optimal posting time (typically Tuesday-Thursday, 8-10am or 12-2pm in your audience's timezone), and connect it to your Substack cross-posting sequence.

---

## LinkedIn Content Formats That Work for Newsletter Writers

### The Insight Hook

```
[Counterintuitive claim].

[Why most people believe the opposite].

[The data or story that changed your mind].

[What this means for you].

Follow me for more on [topic]. Full newsletter: link in comments.
```

**Best for:** Thought leadership, positioning

### The List Post

```
[Number] things I learned after [milestone]:

1. [Short, punchy insight]
2. [Short, punchy insight]
3. [Short, punchy insight]

Most people focus on #[X]. The real leverage is #[Y].

[1-2 sentence elaboration on the key insight]

I break this down in my [newsletter name] newsletter every [day].
```

**Best for:** Expertise, credibility

### The Story

```
[First sentence: action or dialogue, not scene-setting]

[2-3 sentences of story]

[The turn: what changed or what you realized]

[The lesson in 1 sentence]

[CTA to subscribe or engage]
```

**Best for:** Engagement, reach

### The Contrarian Take

```
Hot take: [popular opinion] is wrong.

Here's why: [your argument in 2-3 points]

The counterargument: [steelman the opposing view]

What I actually believe: [nuanced position]

Disagree? Tell me why below.
```

**Best for:** Reach, comments, shares

---

## Claude Prompts for LinkedIn Content

### Adapt newsletter to LinkedIn

```
I have a newsletter section I want to adapt for LinkedIn.

[Paste section]

Write a LinkedIn post that:
- Starts with the most surprising or counterintuitive claim from this section
- Is 400-700 characters
- Has no links (I'll add in first comment)
- Ends with: "I cover [topic] weekly in [Newsletter Name]. Subscribe link in first comment."
- Matches a professional but direct tone
```

### Generate LinkedIn posts from Substack Notes

```
I have a Substack Note I want to expand into a LinkedIn post.

Note: [paste Note]

Notes are under 400 characters; LinkedIn posts should be 600-900 characters.

Expand this by:
- Adding one example or data point
- Breaking it into shorter paragraphs
- Adding a clear CTA
- Removing any Substack-specific references
```

### Batch LinkedIn content from a newsletter issue

```
Read my latest newsletter issue [or: paste content below].

Extract the 3 most LinkedIn-worthy insights and write a LinkedIn post for each.

For each post:
- Use a different format (insight/list/story — one each)
- 400-800 characters
- No links in the body
- CTA to subscribe

Present all 3 for my review.
```

---

## FAQ

### Can Claude post directly to LinkedIn via MCP?

With community MCPs — yes, for immediate posting, with the caveats above. For scheduled posting, you'll need either custom scheduling logic or a tool like Narrareach that handles cloud scheduling.

### What's the safest LinkedIn MCP setup?

OAuth-based community MCPs (not session-based). They use LinkedIn's official API, so you're not violating ToS. The downside is token management and limited feature scope.

### Do I need a LinkedIn MCP for an AI newsletter workflow?

No. Many high-output newsletter writers use Claude for writing and a separate publishing tool for distribution. The writing step (where AI adds value) is separate from the publishing step (where API reliability matters).

### What are the alternatives to LinkedIn automation for newsletter growth?

If you're not automating LinkedIn posts, the highest-ROI manual action is commenting on 10 posts in your niche per day. LinkedIn's algorithm heavily weights comment-generated connections for content distribution.

### Will LinkedIn release an official MCP server?

No announcement as of 2026. LinkedIn's API policy has historically been more restrictive than Twitter's or Meta's. The most reliable path to LinkedIn MCP access remains going through the official OAuth partner program — which is what Narrareach did.

---

## The Writing Stack

For newsletter writers who want AI-assisted LinkedIn content without the MCP complexity:

1. **Claude** writes your LinkedIn posts from your newsletter content
2. **[Narrareach](https://narrareach.com)** schedules and publishes with official LinkedIn API access

This stack gives you the writing quality of a dedicated AI agent + the reliability of an official LinkedIn integration, without maintaining OAuth tokens or debugging MCP configurations.

See also:
- [Newsletter Cross-Posting MCP](https://github.com/iancarson/newsletter-cross-posting-mcp) — full MCP stack for cross-posting
- [Substack MCP Guide](https://github.com/iancarson/substack-mcp-guide) — the Substack side of the MCP stack
- [Newsletter AI Agent](https://github.com/iancarson/newsletter-ai-agent) — the full Claude agent setup

---

## License

MIT
