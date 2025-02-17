# bug-css-minification-postcss-tailwind
This repo was created using `npx create-next-app --example reproduction-template reproduction-app` and then following https://tailwindcss.com/docs/installation/framework-guides/nextjs guide to setup postcss and tailwindcss.

It seems @tailwindcss/postcss is attempting to minify arbitrary files which one would not expect it to.

## steps to reproduce
- `cd reproduction-app`
- `npm i`
- `npm run build`

## Fixes: 
- The removal of `./reproduction-app/unspecifiedDirectory/problematicFile.test` fixes the issue.
- The removal of `@import "tailwindcss";` from `./reproduction-app/app/global.css` fixes the issue.
- The addition of `minify:false`
```
  plugins: {
    '@tailwindcss/postcss': {
      optimize: { minify: false },
    },
  },
```
to `./postcss.config.mjs` fixes the issue.