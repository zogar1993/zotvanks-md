
Pros:
- Locally-scoped styles (no cascading)
- Collocation (html, css and js all together by domain)
- You can use JavaScript variables in styles

Cons:
- Adds runtime overhead
- Increases your bundle size
- Adds a layer of indirection

For enterprise software, I personally favor css-in-js unless I want a super optimized static page. Then again, many of the issues with css-in-js can be solved with compile time resolution, by only loosing the capacity for dynamic variables.

For personal projects I have learned to like minimalistic non framework css only approach.

## Sources
- https://dev.to/srmagura/why-were-breaking-up-wiht-css-in-js-4g9b
