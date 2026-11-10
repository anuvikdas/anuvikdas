### 🛠️ StreamPatch · In development

I’m building [StreamPatch](https://github.com/anuvikdas/StreamPatch) around a question: if a bug has been writing the wrong inventory counts for hours, how do you fix those counts while orders are still coming in?

The goal is a C++ tool that replays Kafka events for affected products, previews what would change in PostgreSQL, and applies a repair only if the row hasn’t changed since the preview. If a sale comes in first, StreamPatch rebuilds the plan with that sale included. I want it to eventually handle resumable repairs across Kafka partitions and tell an operator when there isn’t enough event history to rebuild a row safely.

<details>
<summary><strong>What got me interested in this problem</strong></summary>

- Shopify moved inventory reservations from Redis to MySQL. Their checkout example got me thinking about what happens when a repair and a sale both touch the same inventory row. [Shopify Engineering](https://shopify.engineering/scaling-inventory-reservations)
- Netflix built a data canary to catch bad catalog transformations before they reach viewers. I wanted to explore the next question: how do you recover once incorrect data is already being served? [Netflix TechBlog](https://netflixtechblog.com/the-data-canary-how-netflix-validates-catalog-metadata-18b699d58e36)
- Uber strengthened consistency in CacheFront because asynchronous cache invalidation could leave readers seeing stale values. That got me thinking about the time between calculating a repair and applying it. [Uber Engineering](https://www.uber.com/hn/en/blog/how-uber-serves-over-150-million-reads/)

</details>

### ⏭️ SponsorSkip

I built [SponsorSkip](https://github.com/anuvikdas/YTSponsorSkip), a Chrome extension that detects and skips sponsor reads on YouTube.

> **Where would you start the skip?** A creator plugs their own photography presets, goes back to teaching, then starts a paid Squarespace read at **7:55**.

<details>
<summary><strong>See what SponsorSkip got wrong</strong></summary>

An early version grouped the preset plug and the Squarespace ad into one long skip. It caught part of the ad, but it would have skipped part of the photography lesson too.

That’s why I review videos by hand and track two numbers separately: how many seconds of the sponsor read I missed and how many seconds of the actual video I would have skipped.

</details>
