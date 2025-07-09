# Astro Issue Reproduction

This repository demonstrates a bug in `@astrojs/vercel@8.2.1`.

## The Bug

When using the `@astrojs/vercel` adapter with `imageService: true`, the `astro build` command fails with the error: `"pathToFileURL" is not exported by "__vite-browser-external"`.

This is caused by a change in version `8.2.1` that modifies Vite's `ssr.external` configuration, which leads to Vite incorrectly trying to bundle Node.js-specific modules for the browser.

## How to Reproduce

1.  Install dependencies:
    ```bash
    pnpm install
    ```

2.  Run the build:
    ```bash
    pnpm build
    ```

You should see the build fail with the aforementioned error.

## Workaround

Commenting out `imageService: true` in `astro.config.mjs` allows the build to succeed.
