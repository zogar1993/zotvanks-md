## Create Next App with Typescript

    yarn create next-app --typescript

In case of using styled-components remember to configure it for ssr:
- [ Explanation](https://dev.to/aprietof/nextjs--styled-components-the-really-simple-guide----101c)
- [Example](https://github.com/vercel/next.js/tree/master/examples/with-styled-components)

## Pages in Next.js
In Next.js, a page is a React Component exported from a file in the "pages" directory.

The component can have any name, but you must export it as a default export.

Pages are associated with routes based on their file names. For example:
- "pages/index.js" is associated with the "/" route.
- "pages/posts/a-post.js" is associated with the "/posts/a-post" route.
- "pages/posts/[id].js" is associated with any "/posts/*" route.

## Assets
Next.js can serve static assets, under the top-level "public" directory. Files inside public can be referenced from the root of the application.

The public directory is also useful for robots.txt, favicon.ico, images, Google Site Verification, and any other static files (including .html).

Comments:
- Be sure to not have a static file with the same name as a file in the "pages" directory, as this will result in an error.
- Only assets that are in the public directory at build time will be served by Next.js. Files added at runtime won't be available. For persistent file storage use a third party service like AWS S3.

## Next.js Components
### Link
For internal server side navigation.

```jsx
import Link from 'next/link'

function ALink() {
  <Link href="/posts/a-post">
    <a>A Link</a>
  </Link>
}
```

Comments:
- <a/> inside <Link/> is awful. A good practice would be to style the <a/> instead of the Link, and wrap it in a custom Link.
- "prefetch={false}" inside the Link disables the prefetch behaviour.
- Next.js does code splitting automatically, that means when a page is rendered, the code for other pages is not served initially.
- In a production build of Next.js, whenever Link components appear in the browser’s viewport, Next.js automatically prefetches the code for the linked page in the background.
- In case of external navigation, simply use "a".
- Link enables client-side navigation between two pages in the same Next.js app. Client-side navigation means that the page transition happens using JavaScript, which is faster than the default navigation done by the browser.

### Image
This automatically implements Image Optimization. This allows for resizing, optimizing, and serving images in modern formats like WebP when the browser supports it.

```jsx
import Image from 'next/image'

function YourImage () {
  <Image
    src="/images/profile.jpg"
    height={144}
    width={144}
    alt="Your Name"
  />
}
```

Comments:
- Automatic Image Optimization works even if the image is hosted by an external data source.
- Images are lazy loaded by default. Images load as they are scrolled into viewport.
- Images are always rendered in such a way as to avoid [Cumulative Layout Shift](https://web.dev/cls/), a Core Web Vital.

### Head
If we wanted to modify the metadata of the page, appending elements to the "head" element.

```jsx
import Head from 'next/head'

export default function FirstPost() {
  return (
    <>
      <Head>
        <title>A Title</title>
      </Head>
    </>
  )
}
```

Comments:
- We recommend using "next/script" in your component instead of manually creating a "script" in "next/head"
- Children need to be contained as direct children of the "Head" element.
- If you want to customize the "html" tag, for example to add the "lang" attribute, you can do so by creating a [pages/_document.js file](https://nextjs.org/docs/advanced-features/custom-document).

## Global CSS

To load global CSS files, create a file called pages/_app.js with the following content, and import global css there:

```jsx
export default function App({ Component, pageProps }) {
  return <Component {...pageProps} />
}
```

comments:
- There is local css modules for components, using "{component}.module.css", but I prefer CSS in JS for that.
- You need to restart the development server when you add "pages/_app.js".

## Static Generation
"getStaticProps" runs at build time in production. Inside the function, you can fetch external data and send it as props to the page.

```jsx
export default function AComponent({wea}) {
  return <div>{wea}</div>
}

export async function getStaticProps() {
  return {
    props: { wea: "fome" }
  }
}
```

comments:
- In development mode, getStaticProps runs on each request.
- The code inside getStaticProps is not sent to the browser.

## Server Side Rendering
If you need to fetch data at request time instead of at build time

Because "getServerSideProps" is called at request time, its parameter "(context)" contains request specific parameters.

```jsx
export default function AComponent({wea}) {
  return <div>{wea}</div>
}

export async function getServerSideProps(context) {
  return {
    props: { wea: "fome" }
  }
}
```

comments:
- The code inside getStaticProps is not sent to the browser.

## Client Side Rendering
It is advised to use [SWR](https://swr.vercel.app)

```jsx
import useSWR from 'swr'

function Profile() {
  const { data, error } = useSWR('/api/user', fetch)

  if (error) return <div>failed to load</div>
  if (!data) return <div>loading...</div>
  return <div>hello {data.name}!</div>
}
```

comments:
- Instead of simply routing, it handles caching, revalidation, focus tracking, refetching on interval, and more.

## Dynamic Routes
[Dinamic Routes](https://nextjs.org/docs/routing/dynamic-routes)

For valid pahts on dynamic routes, add "getStaticPaths":

```jsx
export async function getStaticPaths() {
  return {
    paths:[
      {
        id: "some-id"
      },
      {
        id: "another-id"
      }
    ],
    fallback: false
  }
}
```

If fallback is false, then any paths not returned by getStaticPaths will result in a 404 page.

If fallback is true, then the behavior of getStaticProps changes:

- The paths returned from getStaticPaths will be rendered to HTML at build time.
- The paths that have not been generated at build time will not result in a 404 page. Instead, Next.js will serve a “fallback” version of the page on the first request to such a path.
- In the background, Next.js will statically generate the requested path. Subsequent requests to the same path will serve the generated page, just like other pages pre-rendered at build time.

If fallback is blocking, then new paths will be server-side rendered with getStaticProps, and cached for future requests so it only happens once per path.

## 404
To create a custom 404 page, create pages/404.js. This file is statically generated at build time.

## Api Routes
[API Routes](https://nextjs.org/docs/api-routes/introduction)

## useRouter
```jsx
import { useRouter } from 'next/router'

function ActiveLink({ children, href }) {
  const router = useRouter()
  const style = {
    marginRight: 10,
    color: router.asPath === href ? 'red' : 'black',
  }

  const handleClick = (e) => {
    e.preventDefault()
    router.push(href)
  }

  return (
    <a href={href} onClick={handleClick} style={style}>
      {children}
    </a>
  )
}
```