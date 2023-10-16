This is a starter template for [Learn Next.js](https://nextjs.org/learn).

# What I Learned

## Routes

* Route segments are organized as nested directories
* On the server, your application code is automatically code-split by route segments
* On the client, Next.js prefetches and caches the route segments
* Prefetching using `<Link/>` or router.prefetch()

## Images

* `<Image/>` component
* Optimizes images on-demand, as users request them
* Lazy-loaded
* Best format supported by the client
* Smallest size needed

## Metadata and Scripts

* Use the `<Head/>` component to customize `<head/>` per page or component
* Use the `<Script/>` component to add third-party or inline scripts and control when scripts are loaded

## Styling

* By using CSS Modules, Next.js code-splits CSS files and avoids CSS class name colisions

## Custom App and Document

* Custom App:
  * `pages/_app.js`
  * You can override the default App component to create a shared layout, inject data into pages or add global CSS
* Custom Document:
  * `pages/_document.js`
  * You can override the default Document component to customize the `<html>` and `<body/>` tags.

## Pre-rendering

* By default, Next.js pre-renders every page.
* Each generated HTML is associated with minimal JavaScript code necessary for that page.
* Hydration: once HTML is served, the browser runs its JavaScript code and makes the page interactive.
* Each page can choose which type of pre-rendering to use: Static Generation or Server-side Rendering.
  * Static Generation
    * Generates HTML at build time
    * getStaticProps: each page can implement this function to fetch any data necessary to generate the page.
    * getStaticPaths: if you have dynamic routes, this function tells Next.js which paths are to be generated.
    * Fallback: when using getStaticPaths, you can tell Next.js to use a fallback or not.
      * `fallback: false`: generate static HTML for all paths returned by `getStaticPaths`
      * `fallback: true`: same as `false` and additionally, for the remaining pages, generate static HTML asynchronosuly on every request (show loading state)
      * `fallback: 'blocking'`: same as `true`, but synchronous (useful for SEO)
  * Server-side Rendering
    * Generates HTML on each request
    * `getServerSideProps`: each page can implement this function to fetch data on the server-side (synchronous, request blocking)
* 404 pages: create `pages/404.js` and it will be statically generated at build time.

# Questions I still have

* When you request a page, Next.js documentation says it will only server-side-render the parts of the page that changed. How does it know what parts changed?
