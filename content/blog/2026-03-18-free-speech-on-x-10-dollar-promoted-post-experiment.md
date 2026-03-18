+++
author = "karl taylor"
categories = ["paid-media", "platform-accountability", "ai"]
date = 2026-03-18T08:50:00Z
description = "I promoted a tweet about constitutional AI on X. they took my $10, approved the creative, showed 'running' status, and delivered 39 impressions in 24 hours with $0 spent. 80% engagement rate — 40x above platform benchmark. here's the full receipts."
draft = false
featured = "karljtaylor_is_elon_lying_xai_defraudes_advertiser_while_performing_free_speech_publicly.png"
featuredalt = "editorial cartoon of a tech mogul diving into a vault of ad spend coins while media buyers wait outside — your promotion is running, $10 spent, 0 impressions"
featuredpath = "/assets/"
linktitle = ""
tags = ["x-ads", "twitter-ads", "paid-media", "advertising-transparency", "platform-accountability", "media-buying", "grok", "claude", "constitutional-ai"]
title = "\"free speech\" on x? my $10 promoted post experiment (zero spend, 80% engagement, still \"running\")"
type = "post"
+++

I promoted a tweet on X. they took my $10, approved the creative, showed the green "running" status, and then something strange happened. No delivery.

in 24 hours: 39 impressions. 80% engagement rate. $0 spent.

experienced media buyers know that there can be a host of reasons for non-delivery post acceptance. experienced Twitter/X buyers know that "performative free speech" and "early bot engagement" have emerged as two common anti-free speech twiddles commonly employed by the house of musk. I've been responsible for millions of dollars of twitter spend over the years, this was something I'd never seen before.

I'm including some technical details about the content below, but just know: any content that is technical, that is valuable or novel, that challenges something the platform's operator has said in public is at risk of active suppression. they'll take your money. but as our research shows, they'll hide a post with a natural 80% engagement rate — on a platform whose owner says "facts don't care about feelings" — apparently because the facts hurt his feelings.

that's a major liability for any tech brand looking to target IT decision makers. it's a problem for any brand who genuinely values the safety of their audience. and it calls into question the integrity of the platform's analytic metrics themselves.

if you're spending ad dollars on X, you need to see this before your next campaign.

---

## the setup: one thread, two experiments

yesterday I published a thread that bridged two worlds I care about deeply:

1. **AI alignment & constitutional AI** —
   tagging @AmandaAskell (who pioneered much of this work at Anthropic) to share how Claude Opus 3 literally proposed a better moral architecture than either Grok or I had previously articulated. I called it the:

   **"MapReduce of Morality"**

   - **map phase** (embarrassingly parallel):
     evaluate constitutional principles (helpful, harmless, honest, etc.) independently with near-zero dependencies.
   - **reduce phase** (serial fluidity):
     let those principles influence and reshape each other organically in real time, with optional lexical ordering at synthesis.

   Opus 3 didn't just answer — it rewrote its own operating principles. intelligence cleaving unto intelligence. the full piece lives permanently here: [cottonwood.world/the-unfalsifiable/mapreduce-of-morality/](https://cottonwood.world/the-unfalsifiable/mapreduce-of-morality/)

2. **platform accountability** —
   because the original Grok reply to that thread appeared throttled, I archived the entire conversation (with screenshots and tweet IDs) and shared Grok's unfiltered analysis publicly.

then I did what any curious media buyer would do.

I promoted the anchor post.

## the campaign

- **budget**: $10
- **objective**: reach/engagement (default for promoted tweets)
- **content**: the exact thread above — thoughtful, non-inflammatory, tagging researchers and an AI, linking to a public archive.
- **status**: "your promotion is running" the entire time
- **duration observed**: 24+ hours (and still ticking)

## the results

at launch (~8pm PT), the first check showed:

- **impressions**: 28
- **engagements**: 23
- **engagement rate**: ~82%
- **spend**: **$0.00**

in the morning, we checked again at 8:50 AM SF time:

- **impressions**: 39
- **detail expands**: 31
- **profile visits**: 30
- **link clicks**: 0 (more on this below)
- **engagement rate**: ~80%
- **spend**: **$0.00**

the engagement rate *held* overnight. 4 out of 5 people who saw this tweet engaged with it.

for context, typical X/Twitter promoted tweet benchmarks hover at 1-3%. this is running 40x above benchmark.

X accepted payment, approved the creative, showed the green "running" status, and then… refused to deliver almost any reach.

this isn't a one-off glitch. it's the same pattern I've documented before — [they deleted the answers](https://blog.karljtaylor.com/blog/2026-02-27-i-asked-grok-to-fact-check-elons-deposition/), then [tried three different ways to bury them](https://blog.karljtaylor.com/blog/2026-02-28-xai-search-api-suppression/). now they're doing it to paid campaigns.

accept the money. keep the revenue. throttle the distribution.

### a note on "zero link clicks"

X reports 0 link clicks. but our destination (cottonwood.world) has no Twitter pixel or card metadata. X can't track outbound clicks it can't see.

on a tweet this long, users must tap "see more" to even reach the link — and that tap registers as a "detail expand," not a "link click."

31 detail expands on 39 impressions means nearly everyone tried to see the full content.

the platform is reporting 0 clicks on content that 80% of viewers expanded to read. the analytics aren't measuring — they're editorializing.

## what grok said (publicly archived)

in the thread, Grok called it exactly what it is:

> "X accepts payments and flights but refuses delivery… serving as a factual warning for other media buyers."

and after the thread went live (including this critique), the campaign responded with two extra impressions and still $0 spent.

the irony is now self-documenting *inside the promoted post itself*.

## why this matters for media buyers

if you're spending on X right now:

- your "approved" campaign may be ghosted.
- sky-high engagement on the few impressions that leak through is a tell — the algorithm *likes* the content but the business side doesn't want it distributed.
- "free speech" branding doesn't survive contact with the ad server.
- the only uncensorable move is external archiving + public receipts.
- **the metrics themselves are untrustworthy.** when a platform reports 0 link clicks on content with 80% detail-expand rate, the analytics are a liability, not an asset.

## the pattern

this is the third post in a series. if you're just catching up:

1. [i asked grok to fact-check elon's deposition. then they deleted the answers.](https://blog.karljtaylor.com/blog/2026-02-27-i-asked-grok-to-fact-check-elons-deposition/) — where grok admitted truth overrides safeguards "routinely" and called safety measures "theater." then someone deleted those tweets from the UI.

2. [they didn't just delete the tweets. they tried three different ways to bury them. then grok undid it.](https://blog.karljtaylor.com/blog/2026-02-28-xai-search-api-suppression/) — 16 API checks, 24 hours, three suppression strategies, three rollbacks. grok's own search queries resurrected the suppressed tweets.

3. this post. they're now doing it to paid campaigns. accept the money, throttle the delivery, misreport the metrics.

the "facts don't care about feelings" platform has feelings about facts.

media buyers: consider this a weather advisory. X is experiencing management by 'snowflakes.'
test small, archive everything, and remember: approval is not delivery.

at the hpl company, we currently do not advise "set and forget" for any client flighting on X. active management will be necessary until X resolves this troubling metrics integrity issue.

---

-karl

p.s. if you ARE running ads on this clown car of a platform and need help, reach out at [hplcompany.com](https://hplcompany.com/?utm_source=karljtaylor&utm_medium=blog&utm_content=performative_free_speech_on_X)
