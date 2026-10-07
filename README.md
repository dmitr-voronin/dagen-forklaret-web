# Dagen Forklaret

Generated static website for the Danish news podcast. The pipeline publishes
approved episodes, audio links, source references and transcripts under `public/`.

## Cloudflare Pages setup

Connect `dmitr-voronin/dagen-forklaret-web` using these settings:

- Production branch: `main`
- Framework preset: None
- Build command: `exit 0`
- Build output directory: `public`
- Root directory: repository root (leave blank)

After the first deployment, add `dagenforklaret.dk` under the Pages project's
**Custom domains**. For this apex domain, the domain must be in the same
Cloudflare account as the Pages project. Add `www.dagenforklaret.dk` there as well
if wanted. Keep `media.dagenforklaret.dk` connected to its existing R2 bucket.

Confirm the deployment URL first, then open `https://dagenforklaret.dk` after
domain activation. The generated page shows **Dagen Forklaret**, episode
navigation and the latest approved episodes.

Cloudflare instructions:
- https://developers.cloudflare.com/pages/framework-guides/deploy-anything/
- https://developers.cloudflare.com/pages/configuration/custom-domains/

## Pipeline integration

The edition-aware website publisher commits generated files under `public/`
after episode approval. Its dedicated VM checkout and write-enabled deploy key
publish to `main`; Cloudflare Pages must automatically deploy that branch.

Website publication settings:

```dotenv
WEBSITE_PUBLISH_ENABLED=true
WEBSITE_REPO_URL=git@github.com:dmitr-voronin/dagen-forklaret-web.git
WEBSITE_BRANCH=main
```

Authentication and runtime installation settings are supplied separately; do
not put private credentials in this repository.
