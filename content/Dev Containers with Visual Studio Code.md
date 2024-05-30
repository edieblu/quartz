---
tags:
  - ✅
published: true
sr-due: 2025-10-02
sr-interval: 497
sr-ease: 250
---
⬅️ [[FEM Docker]]
- in the root of your project create a  folder `.devcontainer` 
- then two files:
	1. `Dockerfile`:
```
FROM node:12-stretch
RUN npm install -g eslint prettier
```
2.  `devcontainer.json`:
```json
{
  "name": "Frontend Masters Sample",
  "dockerFile": "Dockerfile",
  "appPort": [3000],
  "runArgs": ["-u", "node"],
  "settings": {
    "workbench.colorTheme": "Night Owl",
    // "workbench.colorTheme": "Hot Dog Stand",
    "terminal.integrated.shell.linux": "/bin/bash"
  },
  "postCreateCommand": "npm install",
  "extensions": [
    // "somekittens.hot-dog-stand",
    "sdras.night-owl",
    "dbaeumer.vscode-eslint",
    "esbenp.prettier-vscode"
  ]
}
```