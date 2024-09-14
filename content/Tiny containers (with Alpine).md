---
tags:
  - ✅
published: 
sr-due: 2025-12-27
sr-interval: 540
sr-ease: 250
---
⬅️ [[FEM Docker]]

Swap the Linux distribution to Alpine (decreasing our container size from 913MB to 86MB):
```bash
FROM node:12-alpine
```
- Alpine is a bare bones alternative to Ubuntu. It's built on Busybox Linux which is a 2MB distro of Linux (Alpine is 5MB.) `node:12-alpine` itself is about 80MB and `node:latest` is about 908MB.


### Creating your own alpine container
To create your own Alpine container, create a `my-node.Dockerfile`:
```bash
FROM alpine:3.10

# uses the Alpine package manager to grab Node.js and npm
RUN apk add --update nodejs npm

# or

RUN apk add --update nodejs-current npm

RUN addgroup -S node && adduser -S node -G node

USER node

RUN mkdir /home/node/code

WORKDIR /home/node/code

COPY --chown=node:node package-lock.json package.json ./

RUN npm ci

COPY --chown=node:node . .

CMD ["node", "index.js"]

# to run (-f is file)
docker build -t my-node -f my-node.Dockerfile .
```

### Multi-stage builds
We know it's multi-stage because it has two `FROM` instructions
```yml
# build stage
FROM node:12-stretch
WORKDIR /build
COPY package-lock.json package.json ./
RUN npm ci
COPY . .

# runtime stage
FROM alpine:3.10
RUN apk add --update nodejs
RUN addgroup -S node && adduser -S node -G node
USER node
RUN mkdir /home/node/code
WORKDIR /home/node/code

# copy from the first stage
COPY --from=0 --chown=node:node /build .
CMD ["node", "index.js"]

# to run
docker build -t multi-node -f multi-node.Dockerfile .
docker run -p 3000:3000 multi-node
```

A static project with `create-react-app`, `typescript` and `nginx`

```bash
npx --ignore-existing create-react-app static-assets-project --template typescript --use-npm. 
```

And the `dockerfile`

```yml
FROM node:latest
WORKDIR /app
COPY . .
RUN npm ci && npm run build

# you could totally use nginx:alpine here too
FROM nginx:latest
COPY --from=0 /app/build /usr/share/nginx/html

# to run
docker build -t static-app .
docker run -p 8080:80 static-app
```