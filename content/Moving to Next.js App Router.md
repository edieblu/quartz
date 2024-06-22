---
tags:
  - ✅
published: true
sr-due: 2024-11-19
sr-interval: 151
sr-ease: 256
---

⬅️ [[NextJS - Routing]]
🔗 from [here](https://www.flightcontrol.dev/blog/nextjs-app-router-migration-the-good-bad-and-ugly)
## Good
- Layouts: Each layout persists, so navigation between sibling pages does not unmount and remount the parent layout.
- Suspense: For loading
- Initial data: Where basically every page is a Server Component that loads data and passes that to a client component

## Bad
- you have to add client side fetching for live UI updates
- server side errors easily swallowed or hidden: If something errors on the server and you haven’t added an `<ErrorBoundary />` in the proper spot, it will render the Suspense fallback instead and try to re-render that page on the client.
- lack of routing type safety
- abysmal dev server performance
- dev server memory leak: Every 20 minutes or so, you have to restart the dev server because it crashes. And before it crashes, it progressively gets slower and slower as you make more changes.
- hard to trace errors: Many errors you encounter are super vague, with no traceable call stack. 