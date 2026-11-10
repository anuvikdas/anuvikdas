# Hi, I’m Anuvik Das 👋

I’m a computer science and math senior at Rutgers interested in **infrastructure and distributed systems**. I like building backend systems and figuring out what happens when they get slow, lose a connection, or have to make a decision with incomplete data.

I interned at **ING** in New York City, where I worked on trading infrastructure for the repo desk. I’m joining **Prophet** as a Software Engineer Intern this fall/winter, also in New York City.

## 🛠️ What I’m building

### [StreamPatch](https://github.com/anuvikdas/StreamPatch) · In development

If a bug has been writing the wrong inventory counts for hours, how do you fix those counts while orders are still coming in?

I’m building a C++ tool that replays Kafka events for affected products, previews the corrected inventory in PostgreSQL, and applies each repair only if the row still matches the version used to build the preview. If a sale comes in first, the old plan is rejected so the next one can include that sale.

The end goal is to run resumable repairs across Kafka partitions while live processing continues, keep an audit trail of what changed, and flag rows that can’t be rebuilt from the available history.

<details>
<summary><strong>What got me interested in this problem</strong></summary>

- **Shopify** moved checkout inventory reservations from Redis to MySQL. Their example of two buyers trying to claim the last unit got me thinking about what happens when a sale and a repair touch the same row. [Shopify Engineering](https://shopify.engineering/scaling-inventory-reservations)
- **Netflix** built a data canary to catch bad catalog transformations before they reach viewers. That made me curious about what recovery looks like once incorrect data is already being served. [Netflix TechBlog](https://netflixtechblog.com/the-data-canary-how-netflix-validates-catalog-metadata-18b699d58e36)
- **Uber** strengthened CacheFront’s consistency because asynchronous invalidation could leave readers seeing stale values. That got me thinking about the gap between calculating a repair and applying it. [Uber Engineering](https://www.uber.com/hn/en/blog/how-uber-serves-over-150-million-reads/)

</details>

### ⏭️ [SponsorSkip](https://github.com/anuvikdas/YTSponsorSkip) · Chrome extension

You can get an extension to block YouTube ads, but what about the sponsor reads creators put in the video itself? I got tired of pressing the right arrow over and over, so I built YTSponsorSkip. It detects sponsor segments when you load a video and automatically skips them when playback reaches them. If you want to watch the segment, hit **Undo** to jump back.

I made it for myself because I hate sitting through sponsor reads. I figured other people might want it too, so I shared it.

> **Where would you start the skip?** A creator plugs their own photography presets, goes back to teaching, and later reads a paid Squarespace ad. An early version of SponsorSkip grouped all three into one skip.

<details>
<summary><strong>See what SponsorSkip got wrong</strong></summary>

I marked the paid Squarespace read at **7:55–8:48**. The detector proposed skipping roughly **5:08–8:35**, which would have cut into the photography lesson and still missed the end of the ad. [Watch the paid read from 7:55](https://www.youtube.com/watch?v=M_Ic-6GE7gs&t=475s)

That’s why I review videos by hand and track how many seconds of the sponsor read I missed and how many seconds of regular footage I would have skipped.

</details>

## 🌱 Open source

I’m looking to contribute to open-source projects that tackle performance and reliability problems in infrastructure and distributed systems, especially under load.

🏀 Outside of code, I like playing and watching basketball.
