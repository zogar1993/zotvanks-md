## How do I call an async API from inside a useEffect correctly?

"ignore" lets us disregard obsolete changes if "aValue" changes.  

```jsx
  useEffect(() => {
    let ignore = false;

    (async () {
      const result = await someAsyncAPI(aValue);
      if (!ignore) setWea(result);
    })()

    return () => { ignore = true; }
  }, [aValue]);
```

## How do I manipulate a DOM reference before render?

```jsx
  function WeaComponent() {
    const [height, setHeight] = useState(0);

    const measuredRef = useCallback(node => {
      if (node !== null) {
        setHeight(node.getBoundingClientRect().height);
      }
    }, []);

    return <div ref={measuredRef}>Fome</h1>;
  }
```

### But what if I also need the ref for later?

Just add a simple useRef and set it inside of the callback. It may be weird convention-wise tho, since the "useRef" will not be used in the "ref={}" of the component. Bear in mind when using Typescript that "useRef(null)" is not assignable, but "useRef()" is.

## How do I change a styled-component element tag while keeping its style?

    export const ArticleCard = styled.article`
    	display: flex;
    	flex-direction: column;
    `

    const LinkCard = ArticleCard.withComponent("a")
