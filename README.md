# SvelteKit Dynamic Routing With adapter/static
Let's Start By Create new sveltekit project 
> pnpm create svelte@latest
> pnpm add -D @sveltejs/adapter-static

### svelte.config.js
```
import adapter from '@sveltejs/adapter-static';
import { vitePreprocess } from '@sveltejs/vite-plugin-svelte';

/** @type {import('@sveltejs/kit').Config} */
const config = {
	preprocess: vitePreprocess(),

	kit: {
		adapter: adapter({
			fallback:"index.html"
		})
	}
};

export default config;
```
create new file *+layout.ts* inside src/routes

### +layout.ts
```
export const ssr = false;
export const prerender = false;
```

now create slug route example /blog/[blog_id]
and create +page.svelte 

### /src/routes/blog/[blog_id]/+page.svelte
```
<script>
    import { page } from '$app/stores';
</script>
{$page.params.blog_id}
```

now let's build the project and try it

> pnpm build

> pnpm preview

thats it
