# Google Summer of Code 2025 – Final Report

**Contributor:** Mohamed Hany Youns

**Organization:** [Chromium](https://www.chromium.org/Home/)

**Project Title:** Enhancing INP Insights for Developers

**Mentors:** [Michal Mocny](mmocny@google.com), [Annie Sullivan](sullivan@google.com), [Johannes Henkel](johannes@chromium.org)

**GSoC Project Page:** [Project Proposal Document](https://docs.google.com/document/d/1iDVZYM9R0dVbK9by8URSCtd3_aHA5BilpJXjJ7z4Ox0)

---
**Topics:** Web Vitals, Speed Metrics, Web Performance, DevTools, Browser Internals

**Technologies:** C++, JavaScript, HTML, CSS

---

## Project Overview

The goal of this project is to **provide developers with deeper insights into Interaction to Next Paint (INP), a Core Web Vital that measures web page responsiveness, by identifying, measuring, and reporting its subparts (such as input delay, event processing time, and rendering delays)**.

This work helps the community by **integrating INP subpart data into Chromium’s reporting pipeline and experimental datasets, giving developers actionable feedback to improve site performance and usability**.

Chromium, as an open-source browser that powers major browsers like Google Chrome, Microsoft Edge, and others, plays a critical role in shaping web standards and ensuring performance metrics are consistent across the web. **By advancing INP observability in Chromium, this project strengthens the ecosystem of performance tooling, directly impacting how developers optimize responsiveness and ultimately improving user experiences across billions of devices worldwide.**

---

## Work Completed

During GSoC I worked with the [**Google Speed Metrics**](https://chromium.googlesource.com/chromium/src/+/main/docs/speed_metrics/README.md) team to improve and optimize the [**EventTiming**](https://www.w3.org/TR/event-timing/) API and the [`PerformanceEventTiming`](https://www.w3.org/TR/event-timing/#sec-performance-event-timing) Web API. These APIs are the base for [**Interaction to Next Paint (INP)**](https://web.dev/articles/inp), a Core Web Vital that affects search ranking, user experience, and site success.

### 🔹 Why it matters

* **Browsers**: Better EventTiming in all Chromium browsers (Chrome, Edge, Opera, etc.).
* **Engineers**: More powerful tracing in **Perfetto UI** than standard DevTools.
* **Developers**: Data flows into **DevTools, Lighthouse, PageSpeed Insights, CrUX, and other analytics tools** used worldwide.
* **Users**: Faster, smoother websites. Sites respond more quickly to taps, clicks, and key presses → better usability, higher engagement, and stronger search ranking.

### Impact

*For developers*: This project makes **responsiveness debugging easier** by exposing the hidden details of INP inside tools like DevTools, Lighthouse, and Perfetto. Developers can now spot whether slowness comes from input delay, event handling, or rendering.

*For users*: These improvements mean **faster, smoother websites**. By helping developers identify bottlenecks, sites respond more quickly to taps, clicks, and key presses—leading to better usability, higher engagement, and stronger search ranking.

### 🔹 Deliverables & Status

| Deliverable                                                                                                       | What it does                                               | Status          |
| ----------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------- | --------------- |
| [Request presentation time only when painting](https://chromium-review.googlesource.com/c/chromium/src/+/6760194) | Aligns presentationTime with real paints, reduces overhead | 🟡 Under Review |
| [Added fallback reason & timing](https://chromium-review.googlesource.com/c/chromium/src/+/6614684)               | Shows why and when slow interactions fall back             | ✅ Merged        |
| [New trace event: `MeasurementComplete`](https://chromium-review.googlesource.com/c/chromium/src/+/6652835)       | Marks exactly when EventTiming is reported                 | ✅ Merged        |
| [Simplified click tracking](https://chromium-review.googlesource.com/c/chromium/src/+/6700152)                    | Cleaner, more reliable logic for clicks                    | ✅ Merged        |
| [Removed old keyboard-click code](https://chromium-review.googlesource.com/c/chromium/src/+/6662558)              | Less complexity, easier to maintain                        | ✅ Merged        |
| [Removed old selection auto-scroll code](https://chromium-review.googlesource.com/c/chromium/src/+/6663358)       | Cleaned up unused logic                                    | ✅ Merged        |

TODO:

* check the links

---

## What's Left to Do

If future contributors want to extend the project:

* Implement **[feature/optimization name]** for better performance.
* Add **[specific tests or features]** for edge cases.
* Improve integration with **[related component/tool]**.

TODO:

* need to fill this part

---

## Code Contributions

All of my GSoC-related code contributions are available through Chromium Gerrit review system. The [dashboard](https://chromium-review.googlesource.com/q/owner:mohamedhyouns@gmail.com) provides a complete history of my submitted patches, code reviews, and merged changes, offering a clear view of the progress and technical impact of my work throughout the project.

---

## Challenges & Lessons Learned

**Challenges:**

* **Huge codebase:** Chromium’s millions of C++/Blink lines made it hard at first to trace how **input → compositor → renderer** connects with EventTiming.
* **Precision vs. overhead:** Adding trace events helped visibility but risked slowing performance, so I had to design **lightweight markers**.
* **Cross-team reviews:** My work touched EventTiming, Perfetto, and DevTools, so I needed to coordinate with multiple reviewers.

**Lessons Learned:**

* **Browser performance internals:** Gained hands-on knowledge of Chromium’s latency pipeline, Perfetto tracing, and Core Web Vitals.
* **Open-source best practices:** Writing clean commits, clear docs, and handling review feedback effectively.
* **Ecosystem perspective:** Saw how **low-level APIs (EventTiming)** feed into **tools (Lighthouse, CrUX, RUM)** and shape **business outcomes (SEO, UX, conversions)**.
* **Collaboration:** Improved skills in writing design docs, trade-off discussions, and clear technical communication.

---

## Resources

* **Event Timing Spec** – [https://www.w3.org/TR/event-timing/](https://www.w3.org/TR/event-timing/)
* **Interaction to Next Paint (INP) explainer** – [https://web.dev/articles/inp](https://web.dev/articles/inp)
* **Chromium Speed Metrics Team Docs** – [https://chromium.googlesource.com/chromium/src/+/main/docs/speed\_metrics/README.md](https://chromium.googlesource.com/chromium/src/+/main/docs/speed_metrics/README.md)
* **Perfetto Tracing Docs** – [https://perfetto.dev/docs/](https://perfetto.dev/docs/)
* **Core Web Vitals overview** – [https://web.dev/articles/vitals](https://web.dev/articles/vitals)
* **Google Chrome Developers Blog (Performance)** – [https://developer.chrome.com/blog/tags/performance/](https://developer.chrome.com/blog/tags/performance/)

TODO:

* need to add resources

---

## Acknowledgements

I want to thank my mentors **Michal Mocny, Annie Sullivan, and Johannes Henkel** for their guidance and support. Michal helped me understand the goals and codebase, Annie gave valuable big-picture insights, and Johannes’ detailed reviews improved my work a lot.

Thanks also to the **GSoC organizers/admins** (Sreeja, Stephanie, and Daisuke) for their constant help.

TODO:

* maybe add more people?
