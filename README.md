# somdvps.org

Coming-soon landing page for SomDvps: "Something bigger is coming." SvelteKit 3 + Svelte 5, set in DM Sans, in the same black-and-white style as the content-website CMS.
    <img src="static/SomDvps%20Laptop%20Website%20Mockup.png" alt="SomDvps website mockup displayed on a laptop">


```bash
npm install
npm run dev      # http://localhost:5173
npm run build    # prerenders the page to static HTML
```

## Editing

- Text, email and portfolio link: [`src/lib/site.ts`](src/lib/site.ts)
- Page layout: [`src/routes/+page.svelte`](src/routes/+page.svelte)
- Hero portrait: `static/yusuf.png` (a transparent cutout works best)
- Shared design tokens (colors, buttons): [`src/lib/styles/global.css`](src/lib/styles/global.css)

## Deploy

`adapter-auto` works on Vercel, Netlify and Cloudflare. Push the repo, import it, then point `somdvps.org` at the deployment in your DNS settings.
# somdvps
