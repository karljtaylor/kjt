+++
author = "karl taylor"
categories = ["ai", "brand", "research"]
date = 2026-02-26T14:00:00Z
description = "AI style transfer has a measurable dollar figure. here's the methodology for calculating brand distinctiveness erosion — and why entertainment IP holders are carrying more exposure than their current models show."
draft = false
featured = "karljtaylor-brand-erosion-ai-style-extraction.png"
featuredalt = "a geometric brand mark dissolving into AI-generated noise — visualizing brand distinctiveness erosion"
featuredpath = "/assets/"
linktitle = ""
title = "what is 1% of brand distinctiveness worth?"
type = "post"

+++

i posted a question on twitter earlier today: *"what is 1% of brand distinctiveness worth? nobody knows. that's the problem."*

that was the short version. here's the longer one.

the entertainment and media industry is in the middle of active litigation over AI style extraction. Paramount, Disney, Netflix, and the MPA filed against ByteDance this month. *Andersen v. Stability AI* goes to trial in September 2026, with the court having already named CLIP architecture as a "trade dress database" in the August 2024 ruling. the legal frameworks are developing fast.

what hasn't developed at the same pace: the financial measurement infrastructure behind those claims.

**the gap.** courts have established that style extraction is a cognizable harm. what they don't yet have — and what the Harvard Journal on Law and Technology explicitly flagged as a gap — is a computational operationalization of *how much* style was extracted and what it's worth. without that, brand distinctiveness erosion is a qualitative argument. with it, it becomes a damages calculation.

we've been building the methodology to close that gap.

---

**the measurement stack.**

the framework operates in four layers: computational style distance → brand cohesion scoring → legal risk triage → dollar valuation.

on the measurement side, the stack runs CLIP embeddings for fast triage, DINOv2 nearest-neighbor retrieval for per-asset attribution (producing human-reviewable "10 most similar brand assets" outputs that juries and procurement committees can evaluate), and Fréchet distance between DINOv2 feature distributions for corpus-level style proximity. the Wasserstein-2 metric underlying the Fréchet calculation is a true mathematical metric with triangle inequality — it's defensible under Daubert in a way that purely perceptual similarity scores are not.

the brand cohesion measurement anchors to two validated frameworks. the Ehrenberg-Bass Distinctive Brand Asset framework scores assets on Fame (% of category buyers who recognize the asset) and Uniqueness (% who associate it exclusively with your brand). style extraction attacks Uniqueness first — the asset becomes associated with a style *genre* rather than a specific source. the Portfolio Brand Cohesion Metric (Ward, Trinh, Romaniuk et al., SAGE 2025) is algorithmically computable from visual features and validated against consumer evaluations. high-cohesion portfolios achieve 2.26x higher brand attribution accuracy — 79% vs. 35%.

PBCM before and after AI-generated style enters the market is the erosion measurement.

---

**the dollar figure.**

three models, each defensible from a different angle.

**model A — revenue premium at risk.** brand consistency is associated with a 23% revenue lift (Demand Metric / Lucidpress). for a $1.75B enterprise: 1% brand distinctiveness erosion = roughly $4M in annual revenue at risk. 10% erosion = $40M.

**model B — royalty relief.** Brand Finance's royalty relief method applies a sector-specific royalty rate to revenue enabled by assets trained on brand style. media and entertainment sector median: 6.2% of revenue. at $500M enterprise revenue with 10% style attribution, the style license owed is $3.1M annually — $11-17M NPV over a 5-10 year horizon. this is the preferred damages theory for AI style claims because it's calculable without proving specific lost profits and anchored to comparable transactions. the Disney/$1B OpenAI/Sora deal establishes a market rate for media IP licensing that anchors the upper range.

**model C — enterprise value impact.** using Damodaran's excess return method: brand equity typically represents 20-35% of enterprise value for media companies (Brand Finance, Interbrand, and Damodaran all converge on this range). a documented, ongoing style extraction capability targeting a firm moves its brand-driven equity risk premium from the lower to upper end of the 2-4% range Damodaran identifies for brand-dependent firms. on $1.3B brand equity: a 2% WACC increase = $185-260M value reduction. 1% brand distinctiveness erosion = roughly $13M in enterprise value.

**the coherent argument:** brand equity is $1.0-1.5B for a $1.75B enterprise. brand consistency drives 23% revenue lift and 2x pricing power. AI style extraction reduces PBCM scores and DBA Uniqueness by computationally measurable amounts. the dollar exposure is real, it's large, and it's now calculable.

---

**why this matters right now.**

the Andersen trial in September 2026 will require expert testimony on computational style similarity. that testimony will establish — or fail to establish — the measurement standards that subsequent IP litigation will use.

brands that have characterized their exposure before that trial are in a fundamentally different position than brands that haven't. the math isn't just useful for litigation. it's the instrument for knowing what you're negotiating from when an AI vendor shows you a TEI report.

the Interbrand 2025 data shows a 1% rise in Role of Brand produces a 2.3% average share price change. mid-range brands (brand strength score 50-70) are most sensitive — small drops produce disproportionate discount rate increases. the measurement matters most precisely where brands feel most confident they don't need it.

---

**the model is not a litigation tool.** it produces risk scores that trigger human-administered Eveready surveys. all computational outputs require human expert interpretation under the Shutiq rule. it surfaces the conversation. counsel closes it.

but the conversation is happening whether or not you've done the math.

we're publishing the foundational methodology ahead of the September 2026 Andersen trial. if you're working in entertainment IP and want to see how your brand corpus scores against the framework, [reach out](https://kjt.world/?utm_source=karljtaylor&utm_medium=blog&utm_content=brand-erosion&utm_term=contact).

