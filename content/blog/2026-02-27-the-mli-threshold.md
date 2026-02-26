+++
author = "karl taylor"
categories = ["ai", "research", "methodology"]
date = 2026-02-27T10:00:00Z
description = "there is a point at which prose becomes the wrong format for communicating with an AI. most people haven't found it yet. here's the framework for calculating where it is."
draft = false
featured = "karljtaylor-mli-threshold-prose-vs-instructions.png"
featuredalt = "prose handwriting on the left, structured code on the right, split by a point of light — visualizing the MLI threshold"
featuredpath = "/assets/"
linktitle = ""
title = "the MLI threshold: when to stop writing sentences and start writing instructions"
type = "post"

+++

as doctors, friends, and family members have increasingly become aware of the dramatic changes I've made to the fundamental architecture of my business, the [hpl company](https://hplcompany.com/?utm_source=karljtaylor.com&utm_content=mli_threshold), there's a few questions I've been asked repeatedly.

I have to be honest, this is one of the fastest moving spaces I've ever worked in—I've been working on startups since…2008—and so it's been difficult for me to figure out the right balance of "disclosure" that does not compromise active projects. as anyone who has witnessed the last 3 months of agentic evolution will attest, not only is the world changing but what we think of when we think about work is changing, too.

I'm going to slightly bend the old ghost writer's code here, but a client once said something that forever changed the way I thought about work. He suggested work was the process through which we create value by organizing chaos.

I've thought about that a lot as I've pondered the best way of giving back to the community without introducing new harms—not just to the creatives I've lead, admired, and worked alongside my whole career—but to the public, and to the concept of the public square itself. I firmly believe that as someone whose profession is to "pull the levers" of that machine, it is malpractice to do so without seriously engaging with the consequences of your decision. disagree with me? you have only to look at the damage wrought by the lazy marketing folks like me popularized for brands like Wendy's. do they even make food anymore or is it just mean tweets? (unless they're looking to change that, of course, a JBC hookup could dramatically reframe my thinking here!)

this is the first of a series of articles written to help share some basic principles of working with agentic LLMs at scale we've uncovered over the course of the last few weeks. I'm starting them with this preface intentionally, the concepts and terms discussed herein may be beyond the grasp of a reader who is casually using (or just adopting) a tool like Claude Code or Gemini—but here's the thing, I've allowed robots to fetch my blog, and if you point them at this URL and ask them to summarize it for you, not only will they pick up the learning, they'll be able to help you reduce your token spend while increasing the quality of the outputs you receive.

I won't lie to you, I'm building a plane, flying a plane, and questioning if it's even a plane at all in parallel with 15 other AI agents who are all asking the same question. If work really is how we organize chaos, well…grab a shovel, there's a lot to do.

---

there is a point at which natural language becomes the wrong format for communicating with an AI system.

below that point, prose works fine. above it, prose introduces ambiguity, state-management overhead, and error rates that compound across long tasks. the question isn't whether the threshold exists — any engineer who has debugged an LLM agent workflow has found it empirically — it's where it is and how to calculate it in advance.

the threshold is a function of three variables.

---

**information density.** how many distinct facts, constraints, or decisions does the instruction need to encode? a request like "write a blog post about brand strategy" has low information density — the model fills the gaps from training. a request like "extract the following 14 fields from this document, apply these 3 transformation rules, validate against this schema, and output to this format" has high information density. at high density, prose introduces ambiguity at every conjunction. structured formats — JSON schemas, markdown tables, numbered constraint lists — are lossless where prose is lossy.

**cyclomatic complexity.** how many conditional branches does the task contain? cyclomatic complexity is a software engineering metric for the number of linearly independent paths through a program. it applies to AI instructions the same way it applies to code. a task with zero branches ("summarize this document") has complexity 1. a task with multiple if/then/else paths ("if the document is longer than 10 pages, do X; if it contains financial data, also do Y; unless the date is before 2020, in which case skip Z") has complexity that prose cannot reliably encode without ambiguity. above complexity 4-5, the model starts resolving branches inconsistently across runs. structured formats enforce the branch logic explicitly.

**state-space entropy.** how many valid end states does the task have? creative tasks have high entropy — many valid outputs, all acceptable. data transformation tasks have low entropy — one correct output, everything else is wrong. high-entropy tasks benefit from prose because the model's distributional knowledge fills the space productively. low-entropy tasks require explicit constraint because any deviation from the target state is an error. asking an AI to "format this data" in prose gets you a distribution of plausible formats. specifying the exact output schema gets you the schema.

---

**the break-even.**

when information density, cyclomatic complexity, and state-space entropy are all low, prose outperforms structured formats. the model handles ambiguity gracefully, the task is forgiving, and the overhead of formal specification exceeds its value.

when any one of the three is high, structured formats start to win. when two or three are high simultaneously, prose is the wrong tool.

the practical threshold: tasks with more than ~7 distinct constraints, more than 3-4 conditional branches, or a target output that is exactly specified rather than approximately specified — these tasks should be written as machine-direct instructions, not prose requests.

---

**what this means in practice.**

the industry has spent three years debating prompt engineering as if it were rhetoric — how do you persuade the model to do what you want? that framing is wrong for the high-complexity case. above the threshold, the question isn't how to persuade. it's how to specify. the difference is the difference between writing a brief and writing a schema.

this has immediate implications for AI agent design. multi-step workflows that get handed from one model to another — or from one session to another — need to be structured at the handoff points, not written as narrative summaries. narrative summaries reintroduce exactly the ambiguity the structured format was designed to eliminate.

the models know this. ask any sufficiently capable LLM to decompose a complex task and it will produce a numbered list, not paragraphs. the output format is signaling the appropriate input format back at you.

---

**the underlying mechanism.**

this isn't a stylistic preference. it's an information-theoretic property of how language models process input.

prose is high-perplexity by design — it contains redundancy, implication, and context that the model resolves probabilistically. that resolution is useful when you want the model to draw on distributional knowledge. it's harmful when you need deterministic output.

structured formats are low-perplexity within their schema. a JSON field named `output_format` with value `"csv"` is unambiguous in a way that "please output this as a spreadsheet-style format" is not. the reduction in perplexity at each decision point compounds across the length of the task.

the threshold is where the cost of probabilistic resolution — measured in error rate and inconsistency — exceeds the cost of writing the formal specification.

---

*the antigravity workflow — using structured decomposition to coordinate tasks across AI systems — is the applied version of this framework. that post is next.*

