# Deployment

This project is preconfigured for static documentation publishing via MkDocs.

## Local build

```bash
mkdocs build --clean
```

Output directory: `site/`

## Local preview

```bash
mkdocs serve
```

Preview URL: `http://127.0.0.1:8000`

## GitHub Pages deployment

From repository root:

```bash
mkdocs gh-deploy --clean
```

This command builds docs and publishes to the `gh-pages` branch.

## Alternative static hosts

Any static host can deploy the generated `site/` directory:

- Netlify
- Vercel (static mode)
- Cloudflare Pages
- S3 + CloudFront

## Recommended CI step

Use CI to prevent broken docs:

```bash
mkdocs build --strict --clean
```

This fails the pipeline if navigation references missing pages or Markdown issues become blocking.
