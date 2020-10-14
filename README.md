# Electron Vue Sample App
A sample desktop app using [Electron](https://www.electronjs.org/) and  [Vue](https://vuejs.org/), built in 2020.

The goal of this repo is to build a minimal desktop app and to get to know Electron for building JS desktop apps with Vue as a frontend framework.

## Prerequisites

- Install [Node.js](https://nodejs.org/en/download/). Versions used when creating this app:
  - Node.js v12.19.0
  - NPM 6.14.8

## Resources
- [Electron Documentation - Quick Start Guide](https://www.electronjs.org/docs/tutorial/quick-start)
- [Create an Electron application with Vue and Vuetify](https://itnext.io/electron-application-with-vue-js-and-vuetify-f2a1f9c749b8)


## Steps to Re-Create the Sample App
1. npm install -g @vue/cli
2. vue create [app-name] (e.g. vue create electron-vue-sample-app)
- Please pick a preset: Manually select features
- Check the features needed for your project: Choose Vue version, Babel, TS, Router, Vuex, C
SS Pre-processors, Linter
- Choose a version of Vue.js that you want to start the project with 3.x (Preview)
- Use class-style component syntax? Yes
- Use Babel alongside TypeScript (required for modern mode, auto-detected polyfills, transpi
ling JSX)? Yes
- Use history mode for router? (Requires proper server setup for index fallback in productio
n) No
- Pick a CSS pre-processor (PostCSS, Autoprefixer and CSS Modules are supported by default):
 Sass/SCSS (with node-sass)
- Pick a linter / formatter config: Prettier
- Pick additional lint features: Lint on save
- Where do you prefer placing config for Babel, ESLint, etc.? In dedicated config files
3. vue add electron-builder
