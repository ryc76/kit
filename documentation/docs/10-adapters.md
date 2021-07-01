---
title: Adapters
---

Before you can deploy your SvelteKit app, you need to _adapt_ it for your deployment target. Adapters are small plugins that take the built app as input and generate output for deployment. Many adapters are optimised for a specific hosting provider, and you can generally find information about deployment in your adapter's documentation. However, some adapters, like `adapter-static`, build output that can be hosted on numerous hosting providers, so it may also be helpful to reference the documentation of your hosting provider in these cases.

For example, if you want to run your app as a simple Node server, you would use the `@sveltejs/adapter-node` package:

```js
// svelte.config.js
import node from '@sveltejs/adapter-node';

export default {
	kit: {
		adapter: node()
	}
};
```

With this, [svelte-kit build](#command-line-interface-svelte-kit-build) will generate a self-contained Node app inside `build`. You can pass options to adapters, such as customising the output directory in `adapter-node`:

```diff
// svelte.config.js
import node from '@sveltejs/adapter-node';

export default {
	kit: {
-		adapter: node()
+		adapter: node({ out: 'my-output-directory' })
	}
};
```

A variety of official adapters exist for serverless platforms...

- [`adapter-begin`](https://github.com/sveltejs/kit/tree/master/packages/adapter-begin) — for [Begin](https://begin.com)
- [`adapter-cloudflare-workers`](https://github.com/sveltejs/kit/tree/master/packages/adapter-cloudflare-workers) — for [Cloudflare Workers](https://developers.cloudflare.com/workers/)
- [`adapter-netlify`](https://github.com/sveltejs/kit/tree/master/packages/adapter-netlify) — for [Netlify](https://netlify.com)
- [`adapter-vercel`](https://github.com/sveltejs/kit/tree/master/packages/adapter-vercel) — for [Vercel](https://vercel.com)

...and others:

- [`adapter-node`](https://github.com/sveltejs/kit/tree/master/packages/adapter-node) — for creating self-contained Node apps
- [`adapter-static`](https://github.com/sveltejs/kit/tree/master/packages/adapter-static) — for prerendering your entire site as a collection of static files

> The adapter API is still in flux and will likely change before 1.0.
