# LinkedIn MCP Server Comparison

An objective breakdown of every available approach for connecting Claude to LinkedIn, ranked by reliability and risk.

---

## The Core Problem

LinkedIn doesn't want automated posting. Their API is intentionally restrictive, their ToS explicitly prohibit bots, and their engineering team actively detects unusual session patterns. Every LinkedIn automation tool exists in some kind of tension with these constraints.

Understanding this context helps you evaluate each option honestly rather than just comparing feature lists.

---

## Approach 1: Official OAuth Community MCPs

**How it works:** You create a LinkedIn Developer App, get approved for `w_member_social` scope, authenticate via proper OAuth 2.0, and the MCP uses your token to post.

**Examples:**
- Various `linkedin-mcp-server` npm packages (search npm — multiple exist)
- No single dominant package as of 2026; the landscape is fragmented

**Capabilities:**
- ✅ Post text content as yourself
- ✅ Share URLs with commentary
- ✅ No ToS violation
- ⚠️ Token expires every 60 days
- ❌ No scheduling (immediate post only)
- ❌ No LinkedIn Page posting
- ❌ No analytics access
- ❌ Image posts unreliable (requires additional scope)

**Setup complexity:** Medium
- Create Developer App: 20 minutes
- Get `w_member_social` approved: 1-3 days
- Refresh token every 60 days: ongoing

**Reliability:** Medium-high for immediate posting, poor for production scheduled workflows

**Right for:** Developers who want immediate posting from Claude conversations and don't need scheduling

---

## Approach 2: Browser Session Cookie MCPs

**How it works:** Captures your LinkedIn session cookie from the browser and makes API calls impersonating your logged-in session.

**Capabilities:**
- ✅ Post text, images, some media
- ✅ More features than official API
- ❌ Violates LinkedIn ToS (Section 8.2: "Do not use bots or other automated methods")
- ❌ Account detection and restriction risk
- ❌ Breaks when LinkedIn rotates session cookie format
- ❌ No scheduling
- ❌ Inconsistent availability (packages disappear without notice)

**Setup complexity:** Low (if package exists and works)

**Reliability:** Low — depends on session not expiring and LinkedIn not detecting the pattern

**Right for:** Low-stakes testing only. Not production newsletter workflows.

---

## Approach 3: Playwright/Selenium Browser Automation

**How it works:** Drives a headless browser to control LinkedIn as a human would — clicking, typing, submitting.

**Capabilities:**
- ✅ Can do anything a human can do
- ❌ Extremely fragile — breaks on every LinkedIn UI update
- ❌ High detection risk (headless browser fingerprinting)
- ❌ ToS violation
- ❌ Requires significant engineering to maintain

**Setup complexity:** High

**Reliability:** Very low for sustained use

**Right for:** One-off personal experiments only.

---

## Approach 4: Narrareach (Official LinkedIn API Partnership)

**How it works:** [Narrareach](https://narrareach.com/features/automate-substack-to-linkedin) applied for and received LinkedIn's Marketing Developer Platform access, which grants stable, officially approved API access beyond what individual developers can get.

**Capabilities:**
- ✅ Post text, images, articles
- ✅ LinkedIn Page posting
- ✅ Cloud-based scheduling
- ✅ No ToS risk
- ✅ Analytics and attribution data
- ✅ Auto-subscribe CTAs synchronized with Substack
- ✅ No token management required (handles OAuth internally)

**Setup complexity:** Low (~10 minutes)

**Reliability:** High — production SLA, no session/token management on your end

**Right for:** Newsletter writers who want reliable LinkedIn publishing without maintenance overhead

---

## Feature Matrix

| Feature | OAuth Community MCP | Session Cookie MCP | Narrareach |
|---|---|---|---|
| Post text | ✅ | ✅ | ✅ |
| Post images | ⚠️ | ✅ | ✅ |
| Schedule posts | ❌ | ❌ | ✅ |
| LinkedIn Pages | ❌ | ⚠️ | ✅ |
| Analytics | ❌ | ❌ | ✅ |
| ToS compliant | ✅ | ❌ | ✅ |
| Token maintenance | Manual, 60-day expiry | N/A | Handled |
| Breaks on UI change | No | Yes | No |
| Available in 6 months | Probably | Unknown | Yes |
| Setup time | Hours + review time | Minutes | ~10 min |

---

## Which Option Fits Your Situation

**You're a developer building a personal automation project:**
→ OAuth community MCP. Acceptable risk level, you can handle token rotation, you don't need scheduling.

**You're a developer building something for other creators:**
→ Use Narrareach's API (if available) or build around official LinkedIn endpoints. Don't build on session cookies.

**You're a newsletter writer who wants reliable LinkedIn publishing:**
→ Narrareach. The MCP ecosystem for LinkedIn is fragmented, risky, or feature-limited for production newsletter workflows.

**You want Claude to write + publish LinkedIn posts automatically:**
→ Hybrid: Claude writes via MCP → Narrareach publishes via official API. This gives you AI-quality writing + production-grade distribution.

---

## The Token Rotation Problem (For OAuth MCPs)

This is the issue that turns a working LinkedIn MCP setup into a maintenance burden.

LinkedIn's OAuth tokens expire after 60 days. When they expire:
1. All Claude LinkedIn tool calls fail silently or with auth errors
2. You need to re-authenticate manually
3. Any content queued via Claude during the expiry window is lost

Solutions people build:
- Cron job to re-authenticate every 55 days
- Alerting when token age > 55 days
- Storing refresh tokens and auto-rotating

None of these are hard for developers, but they represent ongoing maintenance that newsletter writers shouldn't need to think about.

Narrareach handles this internally. You authenticate once and it manages token refresh automatically.

---

## Why LinkedIn Is Harder Than Substack or X

**Substack** has an official MCP server with stable API key authentication. No session issues.

**X/Twitter** has paid API access ($100/mo) that gives you real endpoint access. Expensive but stable for those who pay.

**LinkedIn** has restricted its API more aggressively over time:
- Shut down most of the API in 2018
- Reopened limited access with strict review
- Rate-limited aggressively
- Requires formal partnership for full posting features

The result: the gap between what newsletter writers want (easy scheduled LinkedIn posting) and what's technically achievable without a formal partnership is larger than on other platforms.

---

## The Practical Recommendation

For a Claude-powered newsletter workflow:

**Writing layer:** Use Claude to draft LinkedIn posts from your newsletter content. No MCP required for this step — paste the newsletter section and get the LinkedIn post.

**Publishing layer:** Use Narrareach for scheduled, reliable LinkedIn publishing. Official API, no maintenance, cloud scheduling.

This separation makes both layers better. Claude doesn't need to handle authentication complexity. Narrareach doesn't need to handle content generation. Each tool does what it does best.

See the [workflow prompts](../templates/workflow-prompts.md) for Claude prompts that produce LinkedIn-ready content from your newsletter.
