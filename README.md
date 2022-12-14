# Remix + Deno

An example with [Deno](https://deno.land/) template for [Remix](https://remix.run/docs).

## Before getting started

1. Make sure you have installed [Node.js 14 or higher](https://nodejs.org/en/) on your machine. You can use [nvm](https://github.com/nvm-sh/nvm) to manage multiple node version on your machine.
2. Make sure you have installed [deno 1.22.0 or higher](https://deno.land/)

## Getting started

You can setup this project using npm or yarn package managers.

> I would recommend to installed or enabled [yarn 3.1.1 or higher](https://yarnpkg.com/getting-started) package manager on your machine.

### Clone repo

```sh
git clone https://github.com/binodnepali/remix-on-deno.git
#or
git clone git@github.com:binodnepali/remix-on-deno.git
```

### Navigate to cloned repo

```sh
cd remix-on-deno
```

### Install dependencies

```sh
npm install
#or 
yarn install
```

## Development

From your terminal:

```sh
npm run dev
#or
yarn dev
```

This starts your app in development mode, rebuilding assets on file changes.

### Manage dependencies

 
 [learn more how to manage dependencies for Remix projects using Deno](https://github.com/remix-run/remix/blob/main/decisions/0001-use-npm-to-manage-npm-dependencies-for-deno-projects.md).

### Type hints

This template provides type hinting to VS Code via a
[dedicated import map](./.vscode/resolve_npm_imports.json).

To get types in another editor, use an extension for Deno that supports import
maps and point your editor to `./.vscode/resolve_npm_imports.json` .

[Learn more interop between Deno and NPM](https://github.com/remix-run/remix/blob/main/decisions/0001-use-npm-to-manage-npm-dependencies-for-deno-projects.md#vs-code-type-hints).

## Production

First, build your app for production:

```sh
npm run build
#or
yarn build
```

Then run the app in production mode:

```sh
npm start
#or
yarn start
```

## Deployment

Building the Deno app ( `npm run build` or `yarn build` ) results in two outputs:

* `build/` (server bundle)
* `public/build/` (browser bundle)

You can deploy these bundles to any host that runs Deno, but here we'll focus on
deploying to [Deno Deploy](https://deno.com/deploy).

### Setting up Deno Deploy

1. [Sign up](https://dash.deno.com/signin) for Deno Deploy.

2. [Create a new Deno Deploy project](https://dash.deno.com/new) for this app.

3. Replace `<your deno deploy project>` in the `deploy` script in `package.json`
   with your Deno Deploy project name:

```json
{
  "scripts": {
    "deploy": "deployctl deploy --project=<your deno deploy project> --include=.cache,build,public ./build/index.js"
  }
}
```

4. [Create a personal access token](https://dash.deno.com/account) for the Deno
   Deploy API and export it as `DENO_DEPLOY_TOKEN` :

```sh
export DENO_DEPLOY_TOKEN=<your Deno Deploy API token>
```

You may want to add this to your `rc` file (e.g. `.bashrc` or `.zshrc` ) to make
it available for new terminal sessions, but make sure you don't commit this
token into `git` . If you want to use this token in GitHub Actions, set it as a
GitHub secret.

5. Install the Deno Deploy CLI,
   [ `deployctl` ](https://github.com/denoland/deployctl):

```sh
deno install --allow-read --allow-write --allow-env --allow-net --allow-run --no-check -r -f https://deno.land/x/deploy/deployctl.ts
```

6. If you have previously installed the Deno Deploy CLI, you should update it to
   the latest version:

```sh
deployctl upgrade
```

### Deploying to Deno Deploy

After you've set up Deno Deploy, run:

```sh
npm run deploy
#or
yarn deploy
```
