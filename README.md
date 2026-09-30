# Dagen Forklaret

Static website for the Danish news podcast. The initial landing page is a domain
connection test; no episodes or feed are published by this repository yet.

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
domain activation. The expected page says **Dagen Forklaret**, **Nyheder på let
dansk**, and **Hjemmesiden er klar**.

Cloudflare instructions:
- https://developers.cloudflare.com/pages/framework-guides/deploy-anything/
- https://developers.cloudflare.com/pages/configuration/custom-domains/

## Pipeline integration

The edition-aware website publisher commits generated files under `public/`.
This layout matches the existing Dutch website repository. Future publication
will replace the placeholder with the generated Danish site.

Operational inputs for the future Danish installation:

```dotenv
WEBSITE_REPO_URL=https://github.com/dmitr-voronin/dagen-forklaret-web.git
WEBSITE_BRANCH=main
```

Authentication and runtime installation settings are supplied separately; do
not put private credentials in this repository.
