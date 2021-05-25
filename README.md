# SvelteKit GraphCMS starter blog

This starter shows how to use the SvelteKit with GraphCMS. It uses
`graphql-request` and GraphCMS for the backend.

• [Demo](https://sveltekit-graphcms-starter-blog.vercel.app/)

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/spences10/sveltekit-graphcms-starter-blog/tree/main)

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#/https://github.com/spences10/sveltekit-graphcms-starter-blog)

## How to Use

See the introductory [blog post] on getting started building out this
project.

You'll need a GraphCMS account and the Blog Starter created, get the
endpoint from the "API Access" section in the project settings, check
the "Content from stage Published" checkbox for access.

Rename the `sample.env` file to `.env` and add your endpoint:

```text
VITE_GRAPHCMS_URL=your-endpoint-here
```

Add the `VITE_GRAPHCMS_URL` variable and endpoint to the "Environment
Variables" section of the Vercel project.

### Download Manually

```bash
npx degit https://github.com/spences10/sveltekit-graphcms-starter-blog sveltekit-graphcms-starter-blog
```

Install & Run:

```bash
cd sveltekit-graphcms-starter-blog
npm install
npm run dev -- --open
```

<!-- Links -->

[blog post]: ./
