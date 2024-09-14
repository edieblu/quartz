---
tags:
  - ✅
published: true
sr-due: 2025-07-09
sr-interval: 312
sr-ease: 300
---
⬅️ [[NodeJS Best Practice]]

🔗 [GH](https://github.com/goldbergyoni/nodebestpractices?tab=readme-ov-file#8-docker-best-practices)

- use multi-stage builds
- Since Docker is often used in continuous integration environments it is recommended to use the `npm ci` command (instead of `npm install`). It is faster, stricter and reduces inconsistencies by using only the versions specified in the package-lock.json
- Include a `.dockerignore` file that filters out common secret files and development artifacts
- Rebuilding a whole docker image from cache can be nearly instantaneous if done correctly. The less updated instructions should be at the top of your Dockerfile and the ones constantly changing (like app code) should be at the bottom.
- Specify an explicit image digest or versioned label, never refer to `latest`. Developers are often led to believe that specifying the `latest` tag will provide them with the most recent image in the repository however this is not the case. Using a digest guarantees that every instance of the service is running exactly the same code.
- Large images lead to higher exposure to vulnerabilities and increased resource consumption. Using leaner Docker images, such as Slim and Alpine Linux variants, mitigates this issue.
- Lint your Dockerfile ([here](https://github.com/goldbergyoni/nodebestpractices/blob/master/sections/docker/lint-dockerfile.md))

# Common Node.js Docker best practices ([here](https://github.com/goldbergyoni/nodebestpractices/blob/master/sections/docker/generic-tips.md))

- P**refer COPY over ADD command**: COPY is safer as it copies local files only while ADD supports fancier fetches like downloading binaries from remote sites
- **Avoid updating the base OS**: Updating the local binaries during build (e.g. apt-get update) creates inconsistent images every time it runs and also demands elevated privileges. Instead use base images that are updated frequently
- **Classify images using label**s: Providing metadata for each image might help Ops professionals treat it adequately. For example, include the maintainer name, build date and other information that might prove useful when someone needs to reason about an image
- **Use unprivileged containers**: Privileged container have the same permissions and capabilities as the root user over the host machine. This is rarely needed and as a rule of thumb one should use the 'node' user that is created within official Node images
- I**nspect and verify the final result**: Sometimes it's easy to overlook side effects in the build process like leaked secrets or unnecessary files. Inspecting the produced image using tools like Dive can easily help to identify such issues
- **Perform integrity check:** While pulling base or final images, the network might be mislead and redirected to download malicious images. Nothing in the standard Docker protocol prevents this unless signing and verifying the content. Docker Notary is one of the tools to achieve this