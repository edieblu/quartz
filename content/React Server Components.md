---
published: true
tags:
  - ✅
sr-due: 2024-07-03
sr-interval: 31
sr-ease: 275
---
⬅️ [[NextJS]]
⬅️ [[React]]
🔗 from [here](https://vercel.com/blog/understanding-react-server-components)

- brings data-fetching and remote client-server communication

## SSR
- SSR focuses on initial page load, sending pre-rendered HTML to the client that must then be hydrated with downloaded JavaScript before it behaves as a typical React app. SSR also only happens one time: when directly navigating to a page.
- By wrapping a component with `<Suspense>`, you can tell the server to deprioritize that component's rendering and hydration, letting other components load in without getting blocked by the heavier ones.

## RSC
- RSCs individually fetch data and render entirely on the server, and the resulting HTML is streamed into the client-side React component tree, interleaving with other Server and Client Components as necessary.
- eliminates the need for client-side re-rendering, thereby improving performance.
- the server, far more powerful and physically closer to your data sources, deals with compute-intensive rendering and ships to the client just the interactive pieces of code.
- **The base client-side runtime is cacheable and predictable in size, and does not increase as your application grows.**

### Limitations
- All code written for Server Components must be serializable, which means you can’t use lifecycle hooks, such as `useEffect()` or state.

### How to use?
- inside App Router all components are Server Components by default
- Opting into a Client Component is a matter of writing "use client" at the top
- consider leveraging RSCs for server-side rendering and data fetching, while relying on Client Components for locally interactive features and user experiences.
- In the Next.js App Router, all fetched data is now static by default, rendered at build time.

## Resources
- https://nextjs.org/docs/app/building-your-application/rendering
- https://vercel.com/templates/next.js/app-directory
- https://www.mux.com/blog/what-are-react-server-components
- https://dagster.io/blog/dbt-docs-on-react
- https://formidable.dev/blog/2023/powering-our-website-s-evolution-next-js-app-router-and-sanity-cms-in-action/