# [Fetch Examples](https://www.framer.com/developers/fetch-examples#fetch-examples)
Here are some examples of backends for commonly requested Fetch use-cases. In many cases, APIs set up to be called from a front-end with generally work out of the box with Fetch. This means much of the documentation and examples around the web for small backend workers will also likely apply here.
### [A Simple Backend](https://www.framer.com/developers/fetch-examples#a-simple-backend)
At its simplest, a backend can be a small function that returns data. Fetch makes a GET request to the endpoint URL, the backend runs the code in the function, then returns the response with the JSON data. This code will work as-is in most javascript backend setups. you can try it out in the [Cloudflare Worker Playground](https://workers.cloudflare.com/playground#LYVwNgLglgDghgJwgegGYHsHALQBM4RwDcABAEbogB2+CAngLzbPYDqApmQNJQQBimYACFKNRHQAs8CQCsA5gHEYZVgEUAjDNQALVAC4WLDt14CsI6rUnT5SlRq26AsACgAwuioR2X7ABEoAGcYdEDeKE89EgwsPAJiEio4YHYGACIoGnYADwA6GUC00lQoMB9k1IysvIK01w8vHwhsABU6GHYouBgYMCgAYwIIqmQZOAA3OED+hFgIAGpgdFxwdldXHJCkElx2VDhwCBIAbxcSEim6Kn7o9gh+7QAKBHYARxB2QIgAShOXM-OJGQyBIbgA8gAlADKJG07DguwQgQB536ni+sPhiMCJAYiXYAHcSAAJLHsJGPb5EFGYhHkwK5QJ3R4AcgAgv1+p9AtgGhAEOgwNg2WAwOgCdgwbM5JkWQAaEgsgBULO+NLhdKRjOZ7M53N5nn5guFovF2AAsndtMtAvLFQoAKItBUABQAqs6SH4HQAZJ0OhVgl0tACSYIAclDVeqyVqmRBWRyuYEeXyBUKRWKJaTNbaFSy+U1Wu12NGacCSFD2GV+kc4CQ5C87pk5DS0VQMY32M2qHIcXiANppUmmgCEaQVaQ4YDRKXHk+JUHnJGH7DocGXw-QS7SAF1qYCSO2MZldtlcSRzQRtLlUGLMI8rxAbwg4DR0MBKSQlQ2m9BewyZS9s+VL-IeLwQCACBUCQEKfCEHbsPkgSeI8xw7PEURdj2fYDqeOS7iQAC+CroRq2LEaB5wkS4RHUq4hjMMYPD8IIFhiPQUhwLIijKGomg6Kg9SGkWATBKE4SRNEghxIQpBJCk6QpIQ+CEEU0SlOUilpGQYpkHU7gib4bQdF0PR9IM0CeKMKFUOsLjHGkwBwJkAD6SwrGUaR6FUZ7IWkREMYxzGmGxohWFxPF2PxjioMwrhAA) or fork the [Val Town](https://www.val.town/v/hunty/FetchBasic).
```
function worker(request) {
  // Return a random greeting from this list
  const greetings = ["Hello!", "Welcome!", "Hi!", "Heya!", "Hoi!"];
  const index = Math.floor(Math.random() * greetings.length);

  /* ...CORS Headers... */
  
  return Response.json({ data: greetings[index] }, { headers });
}
```

### [API Wrapper](https://www.framer.com/developers/fetch-examples#api-wrapper)
The following is an example of wrapping the use of an API in a small backend function. This pattern is useful for preparing data before using in Framer, and is used in the [Fetch tutorial video](https://youtu.be/dd8A90dKYKc). It follows the pattern of calling a source API, parsing the data, setting up the CORS headers, and then responding with data.
```
async function worker() {
  // Get from any API
  const data = await fetch("https://api.fetch.tools/status")
  const status = await data.json()

  /* Adjust, filter, or manipulate the data */

  return new Response(JSON.stringify(status));
}
```

### [Configuring CORS](https://www.framer.com/developers/fetch-examples#configuring-cors)
Like with all static websites, any API endpoints that are used with Fetch need to be configured to be safely accessed from within the Framer editor, as well as from the published site it will be used on. This means you’ll likely need to configure the CORS of your backend. Many tools and platforms such as [Hono](https://hono.dev/docs/middleware/builtin/cors) or [Vercel](https://vercel.com/guides/how-to-enable-cors) have built-in helps to work with CORS, but here is simple implementation of this in a worker.
```
function worker() {
  // CORS headers
  const headers = new Headers();
  headers.set('Access-Control-Allow-Origin', '*')
  headers.set('Access-Control-Allow-Methods', 'GET, PUT, DELETE, OPTIONS')
  headers.set('Access-Control-Allow-Headers', 'Content-Type')
  
  return new Response({ data: "Hi!" }, { headers });
}
```

### [Authentication: Token](https://www.framer.com/developers/fetch-examples#authentication-token)
Lets say we want to use an API like [IPinfo](https://ipinfo.io/), which requires an API key to work. This is impossible to use securely on the front-end, so we need to use a worker in-between the API and Fetch to safely store our API token. To do this, you’ll want to store the token in an environment variable, and use that within your worker.
```
async fetch(request, env) {
  // Call to source API
  const locationURL = new URL(`https://ipinfo.io/${clientIP}`)

  const IPinfoToken = env.IPINFO_TOKEN
  locationURL.searchParams.set("token", IPinfoToken)
  
  const locationResponse = await fetch(locationURL.href)

  /* ...CORS Headers... */

  return new Response(locationResponse, { headers });
}
```

### [Using Hono ](https://www.framer.com/developers/fetch-examples#using-hono)
If you’d like to introduce a small library into the mix, [Hono](https://hono.dev/) can help you easily manage multiple API routes. This can be helpful for things like OAuth that require you to serve endpoints for `/callback` and more. Additionally it has an easy way to manage CORS with its `cors()` helper.
```
import { Hono } from 'hono'
import { cors } from 'hono/cors'

const app = new Hono()

app.use('*', cors())

app.get('/', (c) => {
  return c.text('Hono!')
})

app.get('/weather', async (c) => {
  const weather = await fetch("api.weather.com").then(d => d.json())
  
  return c.json(weather)
})

export default app
```

