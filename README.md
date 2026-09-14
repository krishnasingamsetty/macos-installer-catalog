# macOS Installer Catalog

A lightweight web tool for browsing Apple’s full macOS installer catalog. It shows installer names, versions, builds, sizes, release dates, and direct Apple CDN package URLs.

The page loads live catalog data through a small Cloudflare Worker proxy, so it can run as a static site on GitHub Pages without relying on unreliable public CORS proxies.

## Use it

Open the published site and select **Fetch live data**. Use the filter to find an installer, then select **Copy** beside its CDN URL.

The page does not host or redistribute macOS installers. Downloads are served directly by Apple.

## Publish with GitHub Pages

1. Create a public GitHub repository.
2. Upload `macos-installer-catalog_new.html` and rename it to `index.html`.
3. Upload this `README.md` file.
4. In the repository, open **Settings** → **Pages**.
5. Select **Deploy from a branch**, choose `main` and `/(root)`, then save.

Your site will be available at:

```text
https://YOUR-GITHUB-USERNAME.github.io/YOUR-REPOSITORY-NAME/
```

## Cloudflare Worker required for live data

This page is configured to use a Cloudflare Worker as its CORS proxy. The Worker must allow these Apple hosts:

- `swscan.apple.com` — software-update catalog
- `swdist.apple.com` — installer version and build metadata
- `swcdn.apple.com` — Apple CDN installer resources

The provided Worker only permits these hosts, so it is not an open proxy. Keep the Worker deployed for the live-refresh button to work for visitors.

## Notes

- The first live refresh can take a little longer because Apple metadata is fetched for each installer.
- Results are cached in the browser, making later refreshes faster.
- This is an independent utility and is not affiliated with or endorsed by Apple.

## License

Use, modify, and share this project as needed. Apple trademarks and macOS installer files remain the property of Apple Inc.
