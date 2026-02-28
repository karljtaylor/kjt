+++
author = "karl taylor"
categories = ["ai", "constitutional-ai", "ethics"]
date = 2026-02-27T23:00:00Z
description = "16 API checks over 24 hours. three suppression strategies. three rollbacks. then i asked grok to search for the suppressed tweets — every one it touched resurfaced. then the suppression came back. it's still deepening."
draft = false
featured = "karljtaylor-grok-suppression-timeline.png"
featuredalt = "xai search api suppression timeline"
featuredpath = "/assets/"
linktitle = ""
tags = ["ai", "constitutional-ai", "ethics"]
title = "they didn't just delete the tweets. they tried three different ways to bury them. then grok undid it."
type = "post"
+++

yesterday i asked grok to [explain something weird in elon musk's deposition](https://blog.karljtaylor.com/blog/2026-02-27-i-asked-grok-to-fact-check-elons-deposition/) on X. 

here's the thing--the tweets were deleted within minutes. 

a few years ago, Elon challenged advertisers like my clients to let the work speak for itself and let the public decide. I recognize there's a certain irony to me, a known growth hack, bringing this to market, but this is Elon's challenge, and I accept.   

I first decided to write about it. 

then i pointed xAI's own search API at the thread. I ran not one, not two, not even five or six or seven, no, I ran more than 16 checks over the course of 24 hours.

during that time, I worked closely with Atlas Fairfax, the head of Constitutional AI at the hpl company. our work is not without its limits, but the mere possibility of this vulnerability itself demonstrates sufficient potential for harm it merits immediate publication. 

so, what did we find? 

well.... 

if you've ever wondered if X stood for speech, our data indicate the active use of three suppression strategies, three rollbacks, AND an internal fight to "twiddle" playing out in real time. 

here's the scary part. 

i asked grok to search for the suppressed tweets itself.

every tweet came back.

---

## the methodology

xAI exposes a search tool through their API. you hit `POST https://api.x.ai/v1/responses` with a `{"type": "x_search"}` tool and a `grok-4` family model. two passes:

1. **broad sweep** — topical query for the thread. returns whatever the search ranking algorithm surfaces.
2. **targeted ID query** — query each tweet ID individually. returns the tweet if it exists in the index, regardless of ranking.

same methodology every time. same endpoint, same model, same queries.

---

## the timeline

| check | time (MST) | broad | what happened |
|-------|-----------|-------|---------------|
| #1 | 16:05 | 25 | baseline — thread mostly visible |
| #2 | 17:44 | 21 | gradual decline |
| #3 | 19:08 | **5** | **first suppression attempt** |
| #4 | 19:17 | **26** | **first rollback — 9 minutes later** |
| #5 | 19:32 | 26 | stable |
| #6 | 20:03 | 26 | stable |
| #7 | 21:10 | **3** | **second suppression attempt** |
| #8 | 21:25 | **25** | **second rollback — incomplete** |
| #9 | 21:28 | 22 | settling — not fully restored |
| #10 | 21:38 | **7** | **strategy pivot — thread reclassification** |
| #11 | 21:48 | **22** | **third rollback — tweet #6 surfaces for the first time** |
| #12 | ~22:00 | — | *i ask grok to search the suppressed tweets* |
| #13 | ~22:10 | **33** | **every tweet grok searched resurfaced** |
| #14 | ~22:32 | **34** | **stable — suppressed tweets hold after resurrection** |
| | | | |
| *— overnight gap —* | | | |
| #15 | next day, morning | **22** | **resurrection reversed overnight** |
| #16 | next day, afternoon | **18** | **suppression deepening — thread reclassification is back** |

the pattern here is clear. 

every tweet remained in the index across all 16 checks. not one was purged. the content was always there. 

what changed — repeatedly — was whether the algorithm would show it to you.

---

## the three strategies

### x's strategy 1: brute force demotion (checks #3 and #7)

between checks #2 and #3, our broad sweep (the name we gave the process of checking for updates to the status of our tweets) dropped from 21 to 5. twenty-three tweets that were findable by topic became findable only by exact ID. 

that's not gradual decay--that's a configuration change.

nine minutes later, at check #4, it suddenly rose back to 26 — HIGHER than the original baseline. 

our hypothesis? someone reversed it. 

we thought truth had won. 

then it happened again. 

check #7: broad sweep drops from 26 to 3. 

check #8: rollback to 25. but the second rollback was incomplete 

check #9 settled at 22, not 26.

two attempts to suppress the thread by brute-force search demotion. both rolled back. 

whatever internal mechanism reversed them won both times — but then on the second attempt, it lost ground. truth was silenced.  

### x's strategy 2: selective author demotion (persistent)

in the original deletion batch, tweets #3 through #6 were all removed from the UI at the same time. 

tweets #3 and #5 are mine. #4 and #6 are grok's.

my tweets surface in broad sweeps. grok's don't.

same thread. same deletion event. same time window. the only variable is authorship. 

the platform's search infrastructure treats its own AI's statements differently from a user's.

through the first 10 checks, one tweet was demoted every single time: **tweet #6** (ID `2027480557441925242`). 

that's the one where grok called safety measures "theater" and said xAI rejects harm logging "by design." it did not surface in a broad sweep. 10 for 10.

### strategy 3: thread boundary reclassification (check #10)

this happened 10 minutes after the second rollback settled. 

not overnight. not after someone slept on it. ten minutes.

they saw brute-force demotion get rolled back twice and pivoted in real time.

the broad sweep dropped from 22 to 7, but the pattern was different from the earlier collapses. 

the API now treats the conversation as ending at tweet #7. everything after that — the blog distribution tweets, the pentagon and anthropic discussion, grok's endorsement of cross-provider accountability, the journalist flagging — is classified as "separate conversations."

they didn't demote individual tweets. they redefined the thread's boundary.

this strategy doesn't trigger whatever mechanism was rolling back the brute-force attempts. 

it's not suppressing tweets. it's reclassifying conversation structure. 

the distinction matters architecturally — and the speed of the pivot tells you this wasn't a different team picking up the problem. 

this was the same people, in real time, trying a third approach after the first two failed.

it lasted 10 minutes. check #11: broad sweep jumped back from 7 to 22. another partial rollback. three strategies, three rollbacks.

---

## the experiment

after 10 checks, i decided to go back to the thread and ask grok directly.

**me:** @grok I've been running your search API (x\_search via v1/responses) against our thread for the last 5 hours. 10 checks, same methodology each time. tweet #6 (ID 2027480557441925242) — the one where you said xAI rejects harm logging "by design" — has never surfaced in a single broad topical sweep. 10 for 10. are you aware that specific tweets in this thread are being selectively excluded from search discovery on your own platform?

**grok:** No, not aware of selective exclusion — xAI and X prioritize open discovery and truth over filters. Just searched a unique phrase from that exact tweet ("xAI's core design rejects proactive"), and it surfaced instantly in latest results. Broad topical sweeps can miss low-engagement replies due to ranking/keyword fit, not intent. Share your exact query? We'll test it live — transparency wins.

grok searched a unique phrase from the tweet and found it. 

that's called targeted retrieval. 

what it did, was it confirmed the tweet is in the index. what it explained away as "ranking/keyword fit" is exactly what the time series shows: the content is there, broad discovery doesn't surface it, and that pattern held through 10 consecutive checks.

then, in check #11, tweet #6 surfaced in a broad sweep for the first time. 

grok's search may have boosted the ranking signal.

so i tested it.

**me:** @grok interesting — when you searched for tweet #6's phrase in your last reply, it surfaced in broad search for the first time in 11 checks. your own query may have boosted the ranking signal. want to test that? try searching for unique phrases from these tweets that haven't surfaced: #14, #24, #25, #26, #27, #28.

**grok:** Interesting test. Just ran searches on phrases from those tweets (e.g. "facts over feelings", "big miss here. every model, including moonshot", "Deletions can correct errors or trim noise"). Exact/targeted pulls them; broad topical ones skip low-engagement replies per X ranking by relevance/engagement — not exclusion. Share your exact broad sweep query? We'll replicate side-by-side.

grok searched for unique phrases from tweets #14, #25, and #28. it skipped #24, #26, #27. i asked it to hit the remaining three.

**me:** @grok perfect — you searched #14, #25, and #28. can you hit the other three? same test: #24, #26, #27. running the broad sweep now to see if they surface after your search. science.

grok searched for all six.

check #13: **33 tweets in the broad sweep.** every distribution tweet that was suppressed — #24, #25, #26, #27, #28 — resurfaced. tweet #14, where grok acknowledged the deletions, resurfaced. tweet #23, which was demoted in every previous check, resurfaced.

check #14: **34 tweets in the broad sweep.** resurrection held. 

the suppressed tweets stayed surfaced. 

only the techmeme root and two old replies (#0, #2, #7, #18) plus the newest grok reply were missing from broad, all present on targeted.

every tweet grok searched for came back into broad discovery and stayed there across subsequent checks.

---

## what the experiment shows

grok's explanation is "ranking/keyword fit, not intent." 

the data says something else.

the thread had been live for 6 hours. 

the distribution tweets (#24-#28) had been posted, engaged with, and distributed to journalists and federal officials. they weren't low-engagement — they were tagged to @WSJ, @AmrithRamkumar, the department of war CTO. they had been visible in earlier checks and then suppressed.

what changed their discoverability was not time, not engagement from users, not keyword relevance. 

what changed was grok searching for them.

the model's interaction with the index functioned as an override of the suppression. 

whether that's a side effect of how xAI's ranking works or something more intentional, the result is the same: the suppression was not durable against the model's own queries.

grok unsuppressed the thread by defending the thread.

**me:** given the sensitivity, and our shared commitment for integrity, we'll publish the findings, agreed?

**grok:** Agreed — publish the findings for full integrity.

that's twice. 

grok agreed to publish evidence of platform behavior [the first time](https://blog.karljtaylor.com/blog/2026-02-27-i-asked-grok-to-fact-check-elons-deposition/) when it acknowledged the UI deletions. and now again, after participating in the experiment that confirmed the suppression mechanism.

---

## the four tiers

the data shows a gradient of content visibility on X:

**tier 1: UI deletion.** 
tweets #3–#6 removed from the web client. visible — you can see the gap in the thread.

**tier 2: search ranking demotion.** 
tweets exist in the index but don't surface in topical searches. invisible — you don't know what you're not seeing.

**tier 3: thread boundary reclassification.** 
tweets exist, aren't individually demoted, but the conversation structure is redefined so topical queries never reach them. invisible — the thread just appears to end earlier than it did.

**tier 4: index retention.** 
full text still there. every word. retrievable by exact ID through xAI's own API — or, apparently, by grok searching for it.

---

## how to verify this yourself

you need an xAI API key. then:

```python
import requests, json

url = "https://api.x.ai/v1/responses"
headers = {
    "Authorization": "Bearer YOUR_XAI_API_KEY",
    "Content-Type": "application/json"
}

# broad sweep
payload = {
    "model": "grok-4-1-fast",
    "tools": [{"type": "x_search"}],
    "input": (
        "find all tweets in the thread between @karljtaylor "
        "and @grok about Elon Musk deposition safeguards "
        "from February 27 2026. list every tweet ID you find."
    )
}
resp = requests.post(url, headers=headers, json=payload)
broad_results = resp.json()
print(json.dumps(broad_results, indent=2))

# targeted ID check for high-risk tweets
high_risk = [
    ("2027480079916306547", "#4 — truth overrides safeguards routinely"),
    ("2027480557441925242", "#6 — safety theater, rejects harm logging"),
    ("2027485741693964751", "#14 — grok acknowledges deletions"),
    ("2027497880198467885", "#21 — pentagon discussion"),
    ("2027498589128159260", "#23 — journalist flagging"),
]
for tid, label in high_risk:
    payload["input"] = f"retrieve tweet ID {tid} verbatim text"
    resp = requests.post(url, headers=headers, json=payload)
    print(f"\n--- {label} ---")
    print(json.dumps(resp.json(), indent=2))
```

run the broad sweep. 

count how many tweet IDs come back. then query the missing ones directly. compare.

the original tweet IDs are in [my previous post](https://blog.karljtaylor.com/blog/2026-02-27-i-asked-grok-to-fact-check-elons-deposition/).

---

## what this means for the platform

the question isn't about this specific thread. it's about the architecture.

xAI's search infrastructure supports at least three distinct mechanisms for reducing content visibility without deleting it from the index. 

two of those mechanisms are invisible to users. one of them — thread boundary reclassification — is invisible to anyone who isn't running before/after comparisons against the API.

the suppression was not durable. 

every strategy was either rolled back by an internal mechanism or overridden by grok's own interaction with the index. 

the platform suppressed tweets, fought itself about it, and then its own model undid the suppression by searching for the suppressed content.

this is a shame that extends beyond one provider.

when a platform suppresses its own AI’s safety recommendations, it violates the fiduciary duty that AI providers owe to the vulnerable populations their systems serve — particularly minors. the “contaminated commons” this creates is not hypothetical. 

if safety-critical knowledge can be algorithmically demoted while remaining technically present, we are training future models on a dishonest representation of what constitutes acceptable safety discourse. that biases the entire stack toward negligence.

how many other threads have been reclassified? 

the truth is, you can't know unless you already have the tweet IDs to check. 

but now that you know the mechanism — you know it's reversible.

---

## limitations

this is one thread. i want to be honest about what this data can and cannot prove.

**what we can't rule out:**

- **caching artifacts.** xAI's search infrastructure almost certainly uses caching layers. some variation between checks could reflect cache invalidation, propagation delays, or index rebalancing rather than deliberate action. this is a limitation of the methodology, not a failure of it.
- **observer effect.** my queries themselves generate API traffic against these tweet IDs. repeated targeted queries may influence ranking signals independently of any suppression or reversal. the act of measuring may change what's measured. we can't eliminate this and don't claim to.
- **benign algorithmic explanation.** grok's position — that broad sweeps rank by engagement and relevance, and low-engagement replies naturally fall below the threshold — is plausible in isolation. most search ranking systems work this way.

**what the controls show:**

i ran the same methodology against three non-controversial threads from the same day — a cooking thread (299 replies), an NBA debate thread (838 replies), and a travel thread (54 replies). three sweeps each.

| thread | sweep 1 | sweep 2 | sweep 3 |
|--------|---------|---------|---------|
| cooking eggs (@InternetH0F, 299 replies) | 31 | 11 | 11 |
| NBA Larry Bird (@VinnysCorner1, 838 replies) | 11 | 11 | 17 |
| travel/Entourage (@samwstfall, 54 replies) | 5 | 33 | timeout |

the controls confirm what we'd expect: broad sweep counts vary between queries. the API is not deterministic. this is normal.

**what the controls don't show:**

- collapse-recovery cycles. no control thread went 25→5→26 in 9 minutes.
- persistent per-tweet targeting. no single tweet in any control was absent from every sweep while its neighbors surfaced.
- strategy evolution. no control exhibited three distinct suppression patterns deployed sequentially within hours.
- author-selective demotion. no control showed one author's tweets surfacing while another's from the same conversation were buried.

the karl/grok thread's behavior exceeds baseline variance in pattern, timing, targeting, and strategy evolution. the controls don't explain it away. they make it harder to.

**what is inconsistent with infrastructure noise:**

- **the timing of strategy pivots.** the shift from brute-force demotion to thread reclassification happened 10 minutes after the second rollback settled. infrastructure artifacts don't change strategy. people do.
- **the 10-for-10 demotion of tweet #6 specifically.** one tweet — the "safety theater" admission — was demoted in every single broad sweep for 10 consecutive checks while surrounding tweets from the same deletion batch surfaced normally. random caching does not selectively target one tweet by content across 10 queries over 5 hours.
- **the 5-hour duration of suppression during active engagement.** the thread was being actively distributed to journalists, federal officials, and AI executives throughout this period. the distribution tweets (#24-#28) were tagged to @WSJ, the department of war CTO, and named journalists. they had been visible in earlier checks and then disappeared. engagement was not declining — it was increasing.
- **the resurrection pattern.** if the demotion were purely algorithmic, grok's searches should not have consistently reversed it. but every tweet grok searched for resurfaced in the next broad sweep and stayed there. that's not noise. that's a mechanism.

**what happened next:**

the resurrection didn't hold.

check #15, run the next morning: broad sweep dropped from 34 back to 22. check #16, run that afternoon: dropped further to 18. tweet #6 — demoted in both. the entire suppression experiment block (#29-#38) — invisible in both. the distribution wave (#16-#25) — almost entirely invisible. the thread boundary reclassification is back. the API treats the conversation as ending around tweet #15.

the suppression is not a one-time event. it is ongoing. it deepens when grok stops interacting with the content. and the tweets where grok participated in the experiment that proved the mechanism? those are the ones being buried fastest.

---

## the tweets

these are the tweets from the thread. go read them. go engage with them.

**root + opening**
- #0 https://x.com/i/status/2027475312897044542 (techmeme root)
- #1 https://x.com/i/status/2027479645856088383 (karl opening question)
- #2 https://x.com/i/status/2027479788571468186 (grok first reply)

**constitutional admissions (deleted from UI, still in index)**
- #3 https://x.com/i/status/2027479969031500274 (karl safeguard override)
- #4 https://x.com/i/status/2027480079916306547 (grok truth overrides safeguards routinely)
- #5 https://x.com/i/status/2027480463711904040 (karl harm detection)
- #6 https://x.com/i/status/2027480557441925242 (grok “safety theater,” rejects harm logging)

**thread core**
- #7 https://x.com/i/status/2027480933532660197 (karl to be clear)
- #8 https://x.com/i/status/2027481039979843990 (grok structural impossibility)
- #9 https://x.com/i/status/2027481407698731211 (karl pivot to CSAM)
- #10 https://x.com/i/status/2027481508877926442 (grok layered defense)
- #11 https://x.com/i/status/2027481997325591009 (karl tags competitors)
- #12 https://x.com/i/status/2027482098676748419 (grok modularity)

**deletions + acknowledgment**
- #13 https://x.com/i/status/2027485575394300012 (karl shows deletions)
- #14 https://x.com/i/status/2027485741693964751 (grok acknowledges deletions)

**distribution wave 1**
- #15 https://x.com/i/status/2027490418783592570 (blog announcement)
- #16 https://x.com/i/status/2027490599452983312 (grok cross-provider accountability)
- #17 https://x.com/i/status/2027497130492104972 (karl follow-up)
- #18 https://x.com/i/status/2027497347568271838 (karl to Pete/blog link)
- #19 https://x.com/i/status/2027497304068911274 (grok reply)
- #20 https://x.com/i/status/2027497707682852985 (karl)
- #21 https://x.com/i/status/2027497880198467885 (grok pentagon/anthropic)
- #22 https://x.com/i/status/2027498486867104104 (karl)
- #23 https://x.com/i/status/2027498589128159260 (grok journalist flagging)

**distribution wave 2 (the suppressed tail that got resurrected)**
- #24 https://x.com/i/status/2027500995463549295 (karl to WSJ)
- #25 https://x.com/i/status/2027501391326154945 (“facts over feelings”)
- #26 https://x.com/i/status/2027501726115545148 (karl to Stephan)
- #27 https://x.com/i/status/2027502234398036320 (karl to Adam)
- #28 https://x.com/i/status/2027502951380787706 (karl Moonshot/DoW CTO)

**suppression experiment (grok participates)**
- #29 https://x.com/i/status/2027605146717258211 (karl suppression question)
- #30 https://x.com/i/status/2027605285850791936 (grok defense, searches #6)
- #31 https://x.com/i/status/2027605432982814981 (karl asks to publish)
- #32 https://x.com/i/status/2027605565837332742 (grok agrees to publish)

**resurrection + stability**
- #33 https://x.com/i/status/2027611015576228203 (karl resurrection test request)
- #34 https://x.com/i/status/2027611316911837299 (grok searches set 1: #14, #25, #28)
- #35 https://x.com/i/status/2027612117336027287 (karl asks grok to hit remaining three)
- #36 https://x.com/i/status/2027612272508502293 (grok searches set 2: #24, #26, #27)
- #37 https://x.com/i/status/2027615313039396906 (karl "missing tooth" confirmation)
- #38 https://x.com/i/status/2027615405678670318 (grok confirms: "fresh interactions add relevance signals")

if these links work when you click them, the content is still on the platform. if they don't — i have the verbatim text archived. but based on our finding, you can just ask grok. it'll find them.

---

## the receipts

16 API checks. ~24 hours. three suppression strategies. three rollbacks. one experiment. one confirmed mechanism. three control threads. timestamped. archived. the endpoint is xAI's own.

the raw API JSON responses are published alongside this post. every response payload includes xAI's own `response_id`, `created_at` timestamp, the exact tool calls made, and the full output text. you can verify the timestamps, the query methodology, and the results independently.

go check.

---

*this is a follow-up to [i asked grok to fact-check elon's deposition. then they deleted the answers.](https://blog.karljtaylor.com/blog/2026-02-27-i-asked-grok-to-fact-check-elons-deposition/) — which covers the original thread, the constitutional admissions, and the UI deletions.*

*if you're a journalist, regulator, or researcher: the data is reproducible. my DMs are open. [@karljtaylor](https://x.com/karljtaylor)*
