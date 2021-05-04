# SvelteKit GraphCMS blog-starter example

Bare bones example of dynamic routing and data fetching in Svelte with
SvelteKit.

Uses the GraphCMS `blog-starter` template, make sure to enable the API
Access `Content from stage Published` setting when trying to fetch
data.

## Made with `create-svelte`

```bash
# create a new project in the current directory
npm init svelte@next
# create a new project in my-app
npm init svelte@next my-app
```

> Note: the `@next` is temporary

## Developing

Once you've created a project and installed dependencies with
`npm install` (or `pnpm install` or `yarn`), start a development
server:

```bash
npm run dev
# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

Before creating a production version of your app, install an
[adapter](https://kit.svelte.dev/docs#adapters) for your target
environment. Then:

```bash
npm run build
```

> You can preview the built app with `npm run preview`, regardless of
> whether you installed an adapter. This should _not_ be used to serve
> your app in production.
