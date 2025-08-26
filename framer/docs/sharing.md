# [Sharing Team Plugins](https://www.framer.com/developers/sharing#sharing-team-plugins)
Plugins are small apps that can be deployed on the web, just like a website. During the early access for Team Plugins, you can share your Plugin by deploying it to a URL and sharing the URL. Once your workspace is enrolled in our beta program, you’ll be given access to the feature. Once that is setup, if you open the Plugin menu, select “Open Plugin from URL” and paste your URL—your Plugin will appear
### [Configuring your shared Plugin](https://www.framer.com/developers/sharing#configuring-your-shared-plugin)
To customise the Name and Icon of your Plugin, you'll want to customise the `framer.json` file. You can learn more about this on the [configuration page](https://www.framer.com/).
### [Deploying a Plugin to a URL ](https://www.framer.com/developers/sharing#deploying-a-plugin-to-a-url)
Plugins are static assets and any Plugin created with `npm create framer-plugin[](https://www.framer.com/)` is already setup for easy deployment. You can choose any hosting provider but for easy setup but recommend Vercel or Cloudflare for easy setup. 
#### [Deploying with Vercel](https://www.framer.com/developers/sharing#deploying-with-vercel)
Read the [getting started](https://vercel.com/docs/frameworks/vite#getting-started) guide or follow these steps:
  1. In the root of your Plugin directory run `npx vercel`
  2. Follow the steps required to deploy to Vercel
  3. **Important:** Log into your Vercel account and disable **Vercel Authentication** under **Deployment Protection** so that your deployment is publicly accessible


Now your plugin should be shareable in the URL displayed by Vercel
#### [Deploying with Cloudflare](https://www.framer.com/developers/sharing#deploying-with-cloudflare)
  1. Follow the steps in the [getting started](https://developers.cloudflare.com/pages/framework-guides/deploy-anything/#deploy-with-cloudflare-pages) guide to setup your project
  2. During configuration set `npm run build` for the build command
  3. During configuration set `./dist` for the build output directory
  4. Confirm the deployment


Now your plugin should be shareable in the URL displayed by Cloudflare
