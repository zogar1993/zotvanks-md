## Incremental Static Regeneration
If you do not want to have to rebuild everything just to let pages update, you can set an expiration time for pages. This way, after the expiration time has passed, the page will lazily rebuild upon receiving a request.

```jsx
export async function getStaticProps() {
  const wea = await getWea()

  // Next.js will attempt to re-generate the page:
  // - When a request comes in
  // - At most once every 10 seconds
  return { props: { wea }, revalidate: 10 }
}
```

## Part Static Generation
All paths that are on getStaticPaths will be generated at build time, but if you need others to be generated lazily upon call, then you may use fallback "true" or "blocking". Both will basically do SSR on first call and SSG on subsequent. The difference is that fallback true will show a fallback until the page is generated, which is the same page but without props. You may know that you are in a fallback state with the router.isFallback property, like below:

```jsx
function Post({ wea }) {
  const router = useRouter()

  if (router.isFallback) return <div>This is a fallback</div>

  return <div>{wea}</div>
}
```

## Absolute Imports


tsconfig.json
```json
{
  "compilerOptions": {
    "baseUrl": "./",
    "paths": {
      "@components/*": ["src/components/*"],
      "@designsystem/*": ["src/designsystem/*"],
      "@buttons/*": ["src/designsystem/buttons"]
    }
  }
}
```

```ts
import Button from '@buttons/Button'
```


## Redirects
### Build time Redirect
At the moment fo writing, there is no dynamic buildtime redirect. Only this static way: https://github.com/vercel/next.js/blob/canary/examples/redirects/next.config.js

### SSR Redirect
https://github.com/nicosh/next-redirect-examples/blob/main/pages/server.js

### Do something while redirecting
Sometimes you are redirecting to a slow SSG page, and you want to show a spinner or whatever while redirecting. For such, you can do:

```jsx
const [isRedirecting, setIsRedirecting] = useState(false)
const router = useRouter()

useEffect(() => {
	const handleRouteChange = (url: string) => {
		if (url.match(/^\/characters\/[A-Fa-f0-9]+$/)) setIsRedirecting(true)
	}
	router.events.on("routeChangeStart", handleRouteChange)
	return () => router.events.off("routeChangeStart", handleRouteChange)
}, []) 
```