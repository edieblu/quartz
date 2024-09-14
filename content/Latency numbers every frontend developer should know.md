---
tags:
  - ✅
sr-due: 2025-02-16
sr-interval: 194
sr-ease: 293
---

⬅️ [[Performance]]
- from [here](https://vercel.com/blog/latency-numbers-every-web-developer-should-know)

| Metric | Estimate | Metric Impact |
|--------|----------|---------------|
| **Wifi latency to internet**<br><br>Wifi adds minimal latency to a connection. This can increase with a weak signal or older hardware. | 1-4ms | [TTFB, FCP, LCP](https://vercel.com/docs/speed-insights/metrics#core-web-vitals-explained) |
| [**5G high-band (millimeter wave)**](https://www.qualcomm.com/research/5g/5g-nr/mmwave) **latency to internet**<br><br>Millimeter wave is the fastest deployed mobile technology. However, it is only practical to use in dense urban areas with a line of sight to the radio tower. | 1-5ms | TTFB, FCP, LCP |
| **User-space budget per** [**frame**](https://en.wikipedia.org/wiki/Frame_rate) **for 60 frames per second**<br><br>On a 60fps device, a frame is painted every 16ms. However, the device needs some time for the actual processing of the frame. The time here is the time available for your code to compute what should be painted. | 5-10ms | Smooth framerate |
| [**5G**](https://en.wikipedia.org/wiki/5G) **mid-band latency to internet**<br><br>This is the regular 5G latency. Experience may vary in case of bad signal or an overloaded tower. | 10-30ms | TTFB, FCP, LCP |
| **Round trip latency to a service or database in same cloud region**<br><br>This is the latency to a different service that is deployed close to you without going to the internet. | 10ms | TTFB, FCP, LCP |
| [**LTE**](https://en.wikipedia.org/wiki/LTE_(telecommunication)) **latency to internet**<br><br>Typical latency for LTE, aka 4G cellular networks. | 15-50ms | TTFB, FCP, LCP |
| **Frame-duration at** [**60 frames per second**](https://en.wikipedia.org/wiki/Frame_rate)<br><br>60 frames per second is the most popular frame rate for display devices. However, some newer devices support higher frame rates like 90 or 120 fps. | 16ms | Smooth frame rate |
| **Round trip latency to other city on the same continent**<br><br>This is the latency you can expect if you deploy to a region on the same continent as your user. It's calculated for a distance of 5000 kilometers, so the actual latency may be slightly higher or lower. | 33ms | TTFB, FCP, LCP |
| **Shortest duration of time perceived by humans as time having passed**<br><br>When responding to user input, staying below this duration means that your user will perceive the response as instant. [Citation](https://www.researchgate.net/publication/225761257_Cognitive_processing_and_time_perception) | 40-80ms | [INP](https://vercel.com/resources/how-vercel-improves-your-websites-search-engine-ranking#optimizing-inp-stay-off-the-main-thread) |
| **Time to parse 1MB of CSS**<br><br>Parsing CSS is part of the work the browser has to perform to render a web page. | 100ms | FCP, LCP |
| **Time to parse 1MB of HTML**<br><br>Parsing HTML is part of the work the browser has to perform to render a web page. While it is often negligible for shorter web pages, it can become a major factor for very long articles. | 120ms | FCP, LCP |
| [**3G**](https://en.wikipedia.org/wiki/3G) **latency to internet**<br><br>3G is the slowest cellular standard in common use today. | 150ms | TTFB, FCP, LCP |
| **Round trip latency to other side of earth with a high quality network** [**(cold potato routing)**](https://www.usenix.org/legacy/publications/library/proceedings/usenix02/full_papers/subramanian/subramanian_html/node28.html)<br><br>This is the worst-case latency you should see if you deploy a service to a single region. | 150ms | TTFB, FCP, LCP |
| **Time to parse 1MB of JS**<br><br>Parsing JavaScript can have a major impact on page load time as it often grows more quickly than CSS and JS. [Code-splitting](https://web.dev/articles/code-splitting-with-dynamic-imports-in-nextjs) is the primary technique to minimize JS size. | 150ms | FCP, LCP, INP |
| **Duration of time perceived by humans as sluggish**<br><br>When reacting to user input, a response slower than this value will be perceived as having to wait. 200ms is also the threshold for ["Needs improvement" in INP.](https://web.dev/articles/inp#good-score) | 200ms | INP |
| **Round trip latency to other side of earth without leased fiber** [**(hot potato routing)**](https://en.wikipedia.org/wiki/Hot-potato_routing)<br><br>When users directly connect to a faraway server or when using a low-cost CDN, then latencies for users may double from passing bytes through the cheapest path possible. | 300ms | TTFB, FCP, LCP |
