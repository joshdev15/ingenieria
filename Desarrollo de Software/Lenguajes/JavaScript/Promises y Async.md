#development #javascript

Manejo de operaciones asíncronas en JavaScript.

## Callbacks (Legacy)

```javascript
function fetchData(callback) {
    setTimeout(() => {
        callback(null, "data")
    }, 1000)
}

fetchData((err, data) => {
    if (err) console.error(err)
    else console.log(data)
})
```

## Promises

```javascript
// Crear Promise
const promise = new Promise((resolve, reject) => {
    const success = true
    if (success) resolve("data")
    else reject("error")
})

// Consumir Promise
promise
    .then(data => console.log(data))
    .catch(err => console.error(err))
    .finally(() => console.log("finalizado"))
```

## Async/Await (ES2017)

```javascript
async function fetchUser() {
    try {
        const response = await fetch("/api/user")
        const data = await response.json()
        return data
    } catch (error) {
        console.error("Error:", error)
    }
}

// Parallel requests
const [users, posts] = await Promise.all([
    fetch("/api/users").then(r => r.json()),
    fetch("/api/posts").then(r => r.json())
])
```

## Promise Methods

```javascript
Promise.all([p1, p2, p3])      // todas resueltas
Promise.allSettled([p1,p2,p3]) // todas terminadas
Promise.race([p1, p2, p3])    // primera resuelta
Promise.any([p1, p2, p3])     // primera exitosa
```

[[Desarrollo de Software/Lenguajes/JavaScript/JavaScript.md]]