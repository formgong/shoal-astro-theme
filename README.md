# Shoal

A free Astro theme for real estate agents: a full-screen photo hero, six photo tiles for your services, an agent section, area guides, short notes and a contact form that really sends.

**Live demo:** https://shoal.formgong.com · **No build step?** Download `shoal-html.zip` from the [latest release](https://github.com/formgong/shoal-astro-theme/releases/latest): plain HTML files, replace `fk_your_access_key` and `https://example.com` with your own and upload them anywhere.

[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/formgong/shoal-astro-theme) [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fformgong%2Fshoal-astro-theme&project-name=shoal&repository-name=shoal&env=PUBLIC_FORMGONG_ACCESS_KEY&envDescription=Your%20Formgong%20access%20key%20%28fk_...%29.%20Create%20a%20free%20form%20to%20get%20one.&envLink=https%3A%2F%2Fformgong.com%2Fnew%3Fname%3Dshoal)

Each button copies the theme to your GitHub, builds it and asks for one value: your Formgong access key (`fk_…`), free at https://formgong.com/new. The form works from the first deploy. Then set `url` in `src/config.ts` to your domain.

The demo agent is **Dana Whitlock**, a fictional realtor on the fictional Kestrel Sound islands. Everything on the site is sample content: phone numbers use the 555-01xx range reserved for fiction, and every email and link uses `example.com`.

- **One file to rebrand.** Name, phone, office, service tiles, island guides, notes and the form key live in `src/config.ts`.
- **Quiet motion.** Headings and captions rise into view once as you scroll, the header hides on the way down and comes back white on the way up, and the service tiles lift their title and darken on hover. No animation library.
- **A contact form that never fakes success.** It shows "Thank you" only when the form backend answers `success: true`. Errors and lost connections show an error. Without JavaScript it still works as a plain HTML form. It opens from the header, the floating "Let's Connect" button and every call to action.
- **Fast and accessible.** Static pages, two self-hosted fonts (Newsreader and Metropolis), one small script. Native `<dialog>` for the form and the menu, visible focus, `prefers-reduced-motion` respected.

Built with Astro 7 and plain CSS.

## Quick start

```bash
npm create astro@latest -- --template formgong/shoal-astro-theme
cd shoal
cp .env.example .env   # then put your access key in .env
npm run dev
```

## Set up the form

1. Create a free form at https://formgong.com/new and copy its access key (`fk_…`).
2. Put it in `.env` as `PUBLIC_FORMGONG_ACCESS_KEY=fk_…`, or in `src/config.ts` under `formgong.accessKey`.
3. Send one test message from your deployed site. It arrives in your Formgong inbox, on Telegram at once if you connect it, and by email.

The key is public by design: it only lets visitors send messages to your form. Spam is filtered with a hidden honeypot field.

## Edit the content

- `src/config.ts`: everything on the home page, the island guides (`areas`) and the notes (`notes`).
- `public/img/`: the photographs. Keep the file names or change them in `src/config.ts`.
- `src/pages/about.astro`, `buying.astro`, `selling.astro`: the longer pages.

## Deploy

`npm run build` produces a static site in `dist/` that any static host can serve. Set `url` in `src/config.ts` first so canonical links, the sitemap and the form redirect point at your domain. On Vercel or Netlify, set `PUBLIC_FORMGONG_ACCESS_KEY` in the project's build environment variables: the key is read at build time. The Deploy to Cloudflare button stores it as a Worker secret instead, and `worker.js` puts it into the form as each page is served.

## Images

The photographs were generated for this theme with FLUX.2 [klein] 4B (Apache 2.0) on Cloudflare Workers AI. Replace them with photos of your own listings and area.

## License

MIT. Use it for your own site or for clients. The "Theme Shoal by Formgong" credit in the footer is optional.
