# Deployment Notes

The current app is a single-page HTML file that can run on GitHub Pages, Netlify, Vercel static hosting, or a basic web server.

## Current Dependency

The demo currently loads Tailwind CSS from CDN:

```html
<script src="https://cdn.tailwindcss.com"></script>
```

This is convenient for prototypes, but it has trade-offs:

- the UI depends on an external network request,
- the page may render poorly in offline classrooms or restricted offices,
- production performance is less predictable,
- some organizations block third-party CDNs.

## Recommended Production Upgrade

Before serious public launch, compile Tailwind locally and serve a generated CSS file from the repo.

Suggested future structure:

```text
src/styles.css
package.json
tailwind.config.js
assets/css/app.css
```

Then replace the CDN script with:

```html
<link rel="stylesheet" href="assets/css/app.css">
```

## Social Sharing

Open Graph tags are included in `index.html`. Make sure `og:url` exactly matches the final public page URL, and use Facebook Sharing Debugger after deployment to refresh cached previews.
