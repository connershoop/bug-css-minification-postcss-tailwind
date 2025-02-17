# bug-css-minification-postcss-tailwind
It seems @tailwindcss/postcss is attempting to minify files which one would not expect it to.

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