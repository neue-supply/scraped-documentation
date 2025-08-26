---
title: "Oauth"
source: "https://www.framer.com/developers/oauth"
domain: "framer.com"
scraped_at: "2025-08-26T16:57:11.393Z"
---
# Oauth
###### Search
Get Started
[Overview](https://www.framer.com/developers/)
[Compare](https://www.framer.com/developers/comparison)
[FAQ](https://www.framer.com/developers/faq)
[Plugins](https://www.framer.com/)
[Introduction](https://www.framer.com/developers/plugins-introduction)
[Quick Start](https://www.framer.com/developers/plugins-quick-start)
[Publishing](https://www.framer.com/developers/publishing)
[Changelog](https://www.framer.com/developers/changelog)
[Reference](https://www.framer.com/developers/reference)
Guides
Fetch
[Introduction](https://www.framer.com/developers/fetch-introduction)
[Examples](https://www.framer.com/developers/fetch-examples)
Components
[Introduction](https://www.framer.com/developers/components-introduction)
[Examples](https://www.framer.com/developers/component-examples)
[Sharing](https://www.framer.com/developers/component-sharing)
[Auto-Sizing](https://www.framer.com/developers/auto-sizing)
[Property Controls](https://www.framer.com/developers/property-controls)
[Reference](https://www.framer.com/developers/components-reference)
Overrides
[Introduction](https://www.framer.com/developers/overrides-introduction)
[Examples](https://www.framer.com/developers/overrides-examples)
[Developers](https://www.framer.com/developers/)
![icon entry point for Site Search](https://framerusercontent.com/images/X8K2iCW5Tob8sQuioDPe6TJEU.png)
###### Search
Get Started
[Overview](https://www.framer.com/developers/)
[Compare](https://www.framer.com/developers/comparison)
[FAQ](https://www.framer.com/developers/faq)
[Plugins](https://www.framer.com/)
[Introduction](https://www.framer.com/developers/plugins-introduction)
[Quick Start](https://www.framer.com/developers/plugins-quick-start)
[Publishing](https://www.framer.com/developers/publishing)
[Changelog](https://www.framer.com/developers/changelog)
[Reference](https://www.framer.com/developers/reference)
Guides
Fetch
[Introduction](https://www.framer.com/developers/fetch-introduction)
[Examples](https://www.framer.com/developers/fetch-examples)
Components
[Introduction](https://www.framer.com/developers/components-introduction)
[Examples](https://www.framer.com/developers/component-examples)
[Sharing](https://www.framer.com/developers/component-sharing)
[Auto-Sizing](https://www.framer.com/developers/auto-sizing)
[Property Controls](https://www.framer.com/developers/property-controls)
[Reference](https://www.framer.com/developers/components-reference)
Overrides
[Introduction](https://www.framer.com/developers/overrides-introduction)
[Examples](https://www.framer.com/developers/overrides-examples)
[Developers](https://www.framer.com/developers/)
![icon entry point for Site Search](https://framerusercontent.com/images/X8K2iCW5Tob8sQuioDPe6TJEU.png)
###### Search
Get Started
[Overview](https://www.framer.com/developers/)
[Compare](https://www.framer.com/developers/comparison)
[FAQ](https://www.framer.com/developers/faq)
[Plugins](https://www.framer.com/)
[Introduction](https://www.framer.com/developers/plugins-introduction)
[Quick Start](https://www.framer.com/developers/plugins-quick-start)
[Publishing](https://www.framer.com/developers/publishing)
[Changelog](https://www.framer.com/developers/changelog)
[Reference](https://www.framer.com/developers/reference)
Guides
Fetch
[Introduction](https://www.framer.com/developers/fetch-introduction)
[Examples](https://www.framer.com/developers/fetch-examples)
Components
[Introduction](https://www.framer.com/developers/components-introduction)
[Examples](https://www.framer.com/developers/component-examples)
[Sharing](https://www.framer.com/developers/component-sharing)
[Auto-Sizing](https://www.framer.com/developers/auto-sizing)
[Property Controls](https://www.framer.com/developers/property-controls)
[Reference](https://www.framer.com/developers/components-reference)
Overrides
[Introduction](https://www.framer.com/developers/overrides-introduction)
[Examples](https://www.framer.com/developers/overrides-examples)
# [Implementing OAuth](https://www.framer.com/developers/oauth#implementing-oauth)
Plugins can use OAuth to let users log into third-party services and make use of them within Framer. For example, a Notion Plugin that can be logged into to import databases into the CMS.
## [Before you start](https://www.framer.com/developers/oauth#before-you-start)
Using the OAuth flow in plugins differs from how you’d typically implement it for a web app, which would go something like the following:
  1. Web app opens the provider (e.g Google) login screen.
  2. After the user logs in, the provider redirects to a URL controlled by the web app.
  3. The redirect URL sends tokens back to the web app using `[**window.opener.postMessage**](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage)`.

This flow doesn't work when using the Framer desktop app. This is because when the login screen opens in the web browser, it’s not possible to send tokens back to the desktop app with `postMessage`.
Instead, to **securely** send tokens to the plugin, we need to store them temporarily on a backend. The plugin polls the backend with a unique **read key.** Once the user logs in, the tokens are returned through this poll request.
## [How to setup a backend](https://www.framer.com/developers/oauth#how-to-setup-a-backend)
In this guide we use [CloudFlare Workers](https://developers.cloudflare.com/workers/). This is because it has a free plan and is easy to setup. This example guide will be enough for most OAuth implementations.
If you’re already familiar with OAuth and server side development, use this guide more as a implementation reference. The authorization flow is [outlined in this repo](https://github.com/framer/plugin-oauth?tab=readme-ov-file#how-it-works).
### [Create a developer account with the provider](https://www.framer.com/developers/oauth#create-a-developer-account-with-the-provider)
This is different for every provider, but in general you'll need to do the following:
  1. Create a developer account with the provider you want to use
  2. Create a new “app” or “project” in the providers developer dashboard
  3. Note down the **client ID** and **client secret**

For detailed instructions, follow an OAuth 2.0 guide for the service you want to use. Here are some examples:

### [Download example backend](https://www.framer.com/developers/oauth#download-example-backend)
Clone our [example backend repo](https://github.com/framer/plugin-oauth). It's a CloudFlare Worker, which is a way to run server side code without having to manage servers. The example uses CloudFlare's CLI tool [Wrangler](https://developers.cloudflare.com/workers/wrangler/) which allows you to create, develop, and deploy workers.
### [Enable Local SSL](https://www.framer.com/developers/oauth#enable-local-ssl)
Some providers require local URLs to use HTTPS. To enable this locally, run the following command in the root of the example directory.
```
mkcert localhost
```

> When deploying and running in production, **all traffic should be served over HTTPS**. Otherwise tokens sent in the body of a request won’t be encrypted!
### [Add environment variables](https://www.framer.com/developers/oauth#add-environment-variables)
Before you can run the example, you’ll need to setup the environment variables locally. Rename the `.dev.vars.example` file to `.dev.vars` and fill in the details with your own. 
Later when you deploy to production, ensure you set up the environment variables there as well. This is often done in a dashboard like [CloudFlare’s dashboard](https://developers.cloudflare.com/workers/configuration/environment-variables/#add-environment-variables-via-the-dashboard).
  * `**CLIENT_ID**`**and**`**CLIENT_SECRET**`**:** Use the **client ID** and **client secret** that you noted down earlier from the provider.
  * `**PLUGIN_URI**`**:** This is where your plugin is hosted. The default should be correct for your local setup.
  * `**REDIRECT_URI**`**:** This is the endpoint the provider will redirect to after logging in. Ensure that you’ve added this to your provider’s developer dashboard. It’s usually called “Redirect URI” or “Callback URL”. The default should be correct for your local setup. 
  * `**AUTHORIZE_ENDPOINT**`**:** This is the URL for requesting authorization from the provider. It will open a login screen for the user. This should be listed the provider’s API docs.
  * `**TOKEN_ENDPOINT**`: This is the URL for refreshing tokens on the user’s behalf. This should be listed the providers API docs.
  * `**SCOPE**`**:** A comma separated list of permissions that your plugin requires from the provider. Check the providers API docs or developer dashboard for a list of these, they vary for each service. In the case that a provider does not have scopes, leave this field blank.

> **Never store the client secret in code!** The `.dev.vars` file should be ignored by Git and never committed.
After adding the environment variables, run the following command to update the type definitions:
```
npx wrangler types
```

This will ensure references to `env` will correctly autocomplete in your editor.
### [Run the backend](https://www.framer.com/developers/oauth#run-the-backend)
You can now run the backend. In the backend directory, run the following commands:
```
# Install the dependencies.
npm install

# Setup D1 database.
npm run bootstrap

# Run the worker locally.
npm run dev
```

If it's successful you should see the URL output in the terminal. Usually it's `https://localhost:8787`
### [Plugin changes](https://www.framer.com/developers/oauth#plugin-changes)
Now that the backend is running, you can make changes to your plugin to show a login window and store tokens. Your plugin will need to poll the backend for tokens. Here is an example of a `pollForTokens` function defined inside a component:
```javascript
const pollInterval = useRef();

const pollForTokens = (readKey) => {
  // Clear any previous interval timers, one may already exist 
  // if this function was invoked multiple times.
  if (pollInterval.current) {
    clearInterval(pollInterval.current);
  }

  return new Promise((resolve) => {
    pollInterval.current = setInterval(async () => {
      const response = await fetch(
        `https://localhost:8787/poll?readKey=${readKey}`,
        { method: "POST" }
      );

      if (response.status === 200) {
        const tokens = await response.json();
        
        clearInterval(pollInterval.current);
        resolve(tokens);
      }
    }, 2500);
  });
};
```

You'll then need to add function to the component that opens the login window and start polling. Here is an example of that function:
```javascript
const [tokens, setTokens] = useState(null);

const login = async () => {
  // Retrieve the authorization URL & set of unique read/write keys
  const response = await fetch("https://localhost:8787/authorize", {
    method: "POST",
  });
  if (response.status !== 200) return;
  
  const authorize = await response.json();
  
  // Open up the provider's login window.
  window.open(authorize.url);

  // While the user is logging in, poll the backend with the
  // read key. On successful login, tokens will be returned.
  const tokens = await pollForTokens(authorize.readKey);

  // Store tokens in local storage to keep the user logged in.
  window.localStorage.setItem("tokens", JSON.stringify(tokens));

  // Update the component state.
  setTokens(tokens);
};
```

When your plugin first loads, you will want to check if tokens already exist in local storage. If they exist they can be lifted into the local state.
```
useEffect(() => {
  // Check for tokens on first load.
  const serializedTokens = window.localStorage.getItem("tokens");
  if (!serializedTokens) return;

  const tokens = JSON.parse(serializedTokens);
  setTokens(tokens);
}, []);
```

The basics are now in place to start making authorized requests!
This will depend on the API you are using, but the standard way to make an authorized request is to use a **Bearer** header. This is how you'd do that for Google's API:
```javascript
const response = await fetch(
  "https://www.googleapis.com/oauth2/v1/userinfo",
  {
    headers: {
      Authorization: `Bearer ${tokens.access_token}`,
    },
  }
);

const profile = await response.json();
console.log(profile); // Prints the user's profile info!
```

If you decide to use an OAuth library, check their docs on how to provide the library the access token.
### [Deploying](https://www.framer.com/developers/oauth#deploying)
Any URLs in the plugin will need to change dynamically depending on the environment. This is because `localhost` URLs won't work once deployed.
Within the plugin you can check the address to see if it's running locally:
```javascript
const isLocal = () => window.location.hostname.includes("localhost")
```

And then toggle between production and local URLs:
```
// Set a global variable with the endpoint.
const AUTH_BACKEND = isLocal() ? 
  "https://localhost:8787" : 
  "https://example.com";

// Use the global variable wherever you make requests
// to the backend.
const response = await fetch(`${AUTH_BACKEND}/authorize`, {
  method: "POST",
});
```

If using CloudFlare, Deploying the backend should be as simple as running the following command:
```
npx wrangler deploy
```

This will host your worker online using your CloudFlare account. See their docs for [more info on deploying](https://developers.cloudflare.com/workers/get-started/guide/#4-deploy-your-project).
## [Next steps](https://www.framer.com/developers/oauth#next-steps)
There's plenty of other things you'll need to add to your plugin to make a nice user experience. These include, but are not limited to:
  * Refreshing access tokens when they expire. Look into how to periodically refresh them when making requests.
  * Add a loading states for network requests. For example, in our [Notion plugin](https://github.com/framer/plugins/blob/main/plugins/notion/src/Authenticate.tsx#L66) we show a spinner after the user clicks the login button.
  * Handle error cases and show warnings for when authentication fails or a request times out.

### [Previous Data ](https://www.framer.com/developers/storing-data)
### [Previous Data ](https://www.framer.com/developers/storing-data)
### [Previous Data ](https://www.framer.com/developers/storing-data)
Resources
[Desktop app ](https://www.framer.com/downloads/)
[Developers ](https://www.framer.com/developers/)
[Wallpapers ](https://www.framer.com/wallpapers/)
[Community ](https://www.framer.community/)
[Live Events ](https://www.framer.com/events/)
[Meetups ](https://www.framer.com/meetups/)
Programs
[Agencies ](https://www.framer.com/agencies/)
[Students ](https://www.framer.com/students/)
[Creators ](https://www.framer.com/creators/)
[Startups ](https://www.framer.com/startups/)
[Experts ](https://www.framer.com/expert/apply/)
[Switch ](https://www.framer.com/switch/)
Compare
[Squarespace ](https://www.framer.com/compare/framer-vs-squarespace)
[Wordpress ](https://www.framer.com/compare/framer-vs-wordpress)
[Unbounce ](https://www.framer.com/compare/framer-vs-unbounce)
[Webflow ](https://www.framer.com/compare/framer-vs-webflow)
[Figma ](https://www.framer.com/compare/framer-vs-figma)
[Wix ](https://www.framer.com/compare/framer-vs-wix)
Solutions
[Figma to HTML ](https://www.framer.com/solutions/figma-to-html/)
[Website builder ](https://www.framer.com/solutions/website-builder/)
[Portfolio maker ](https://www.framer.com/solutions/portfolio-website/)
[Landing pages ](https://www.framer.com/solutions/landing-pages/)
[UI/UX design ](https://www.framer.com/solutions/ui-ux-design/)
[No-code ](https://www.framer.com/solutions/no-code-website-builder/)
Company
[Security ](https://www.framer.com/legal/security/)
[Careers ](https://www.framer.com/careers/)
[Status ](https://www.framerstatus.com)
Abuse
[Brand ](https://www.framer.com/brand)
[Legal ](https://www.framer.com/legal/terms-of-service/)
Socials
[Instagram ](https://www.instagram.com/framer)
[YouTube ](https://www.youtube.com/@framer)
[Threads ](https://www.threads.net/@framer)
[LinkedIn ](https://www.linkedin.com/company/framer)
[TikTok ](https://www.tiktok.com/@framer)
[X ](https://x.com/framer)
[](https://www.framer.com/)
Resources
[Desktop app ](https://www.framer.com/downloads/)
[Developers ](https://www.framer.com/developers/)
[Wallpapers ](https://www.framer.com/wallpapers/)
[Community ](https://www.framer.community/)
[Live Events ](https://www.framer.com/events/)
[Meetups ](https://www.framer.com/meetups/)
Programs
[Agencies ](https://www.framer.com/agencies/)
[Students ](https://www.framer.com/students/)
[Creators ](https://www.framer.com/creators/)
[Startups ](https://www.framer.com/startups/)
[Experts ](https://www.framer.com/expert/apply/)
[Switch ](https://www.framer.com/switch/)
Compare
[Squarespace ](https://www.framer.com/compare/framer-vs-squarespace)
[Wordpress ](https://www.framer.com/compare/framer-vs-wordpress)
[Unbounce ](https://www.framer.com/compare/framer-vs-unbounce)
[Webflow ](https://www.framer.com/compare/framer-vs-webflow)
[Figma ](https://www.framer.com/compare/framer-vs-figma)
[Wix ](https://www.framer.com/compare/framer-vs-wix)
Solutions
[Figma to HTML ](https://www.framer.com/solutions/figma-to-html/)
[Website builder ](https://www.framer.com/solutions/website-builder/)
[Portfolio maker ](https://www.framer.com/solutions/portfolio-website/)
[Landing pages ](https://www.framer.com/solutions/landing-pages/)
[UI/UX design ](https://www.framer.com/solutions/ui-ux-design/)
[No-code ](https://www.framer.com/solutions/no-code-website-builder/)
Company
[Security ](https://www.framer.com/legal/security/)
[Careers ](https://www.framer.com/careers/)
[Status ](https://www.framerstatus.com)
Abuse
[Brand ](https://www.framer.com/brand)
[Legal ](https://www.framer.com/legal/terms-of-service/)
Socials
[Instagram ](https://www.instagram.com/framer)
[YouTube ](https://www.youtube.com/@framer)
[Threads ](https://www.threads.net/@framer)
[LinkedIn ](https://www.linkedin.com/company/framer)
[TikTok ](https://www.tiktok.com/@framer)
[X ](https://x.com/framer)
[](https://www.framer.com/)
Resources
[Desktop app ](https://www.framer.com/downloads/)
[Developers ](https://www.framer.com/developers/)
[Wallpapers ](https://www.framer.com/wallpapers/)
[Community ](https://www.framer.community/)
[Live Events ](https://www.framer.com/events/)
[Meetups ](https://www.framer.com/meetups/)
Programs
[Agencies ](https://www.framer.com/agencies/)
[Students ](https://www.framer.com/students/)
[Creators ](https://www.framer.com/creators/)
[Startups ](https://www.framer.com/startups/)
[Experts ](https://www.framer.com/expert/apply/)
[Switch ](https://www.framer.com/switch/)
Compare
[Squarespace ](https://www.framer.com/compare/framer-vs-squarespace)
[Wordpress ](https://www.framer.com/compare/framer-vs-wordpress)
[Unbounce ](https://www.framer.com/compare/framer-vs-unbounce)
[Webflow ](https://www.framer.com/compare/framer-vs-webflow)
[Figma ](https://www.framer.com/compare/framer-vs-figma)
[Wix ](https://www.framer.com/compare/framer-vs-wix)
Solutions
[Figma to HTML ](https://www.framer.com/solutions/figma-to-html/)
[Website builder ](https://www.framer.com/solutions/website-builder/)
[Portfolio maker ](https://www.framer.com/solutions/portfolio-website/)
[Landing pages ](https://www.framer.com/solutions/landing-pages/)
[UI/UX design ](https://www.framer.com/solutions/ui-ux-design/)
[No-code ](https://www.framer.com/solutions/no-code-website-builder/)
Company
[Security ](https://www.framer.com/legal/security/)
[Careers ](https://www.framer.com/careers/)
[Status ](https://www.framerstatus.com)
Abuse
[Brand ](https://www.framer.com/brand)
[Legal ](https://www.framer.com/legal/terms-of-service/)
Socials
[Instagram ](https://www.instagram.com/framer)
[YouTube ](https://www.youtube.com/@framer)
[Threads ](https://www.threads.net/@framer)
[LinkedIn ](https://www.linkedin.com/company/framer)
[TikTok ](https://www.tiktok.com/@framer)
[X ](https://x.com/framer)
[](https://www.framer.com/)
---
*Scraped from: https://www.framer.com/developers/oauth*