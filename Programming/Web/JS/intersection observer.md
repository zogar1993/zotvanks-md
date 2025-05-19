## IntersectionObserver Example
```js
    const formObserver = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                /* code here */
                formObserver.unobserve(section)
            }
        })
    })
    
    formObserver.observe(component)
```