# The Daily Anomaly

A minimalist, Jekyll-powered daily digest for edge science and anomaly reporting. Built to run natively on GitHub Pages with no external build tooling.

## Features
- Newspaper-inspired layout with a sepia palette and Libre Baskerville headlines.
- Automatic evidence badges, drop caps, and source lists for each story.
- Editions archive with newest issues first, plus homepage auto-linking to the latest edition.
- Pure HTML/Liquid/CSS stack—no Node or asset pipelines required.

## Project Structure
```
_config.yml          # Jekyll configuration and front matter defaults
_includes/           # Header and footer partials
_layouts/            # Default, story, and edition templates
assets/style.css     # Core typography, layout, and print styles
content/YYYY-MM-DD/  # Individual story markdown files
editions/            # One markdown file per daily edition (+ archive index)
index.md             # Homepage pointing at the latest edition
```

## Local Development
1. Ensure you have Ruby, Bundler, and Jekyll installed locally (`gem install bundler jekyll`).
2. Install dependencies (only Jekyll itself):
   ```bash
   bundle install
   ```
3. Start the local preview server:
   ```bash
   bundle exec jekyll serve --livereload
   ```
4. Visit `http://127.0.0.1:4000` (or the URL printed in the console) to browse the site.

## Adding Content
1. Create a new edition file under `editions/YYYY-MM-DD.md` with front matter `title`, optional `date`, and a Markdown list of stories. Use the `{% link %}` tag for internal links so URLs always respect `site.baseurl`.
2. Add individual stories in `content/YYYY-MM-DD/<slug>.md` with front matter keys:
   - `title`, `date`, `edition`, `category`
   - `evidence_level` (`High`, `Medium`, `Low`, etc.)
   - `sources` (array of absolute URLs)
   - Optional `image` and `image_alt`
3. The story layout automatically renders the headline, evidence badge, hero image, and sources list.

## Deploying on GitHub Pages
1. Commit and push changes to the `main` branch.
2. In the repository settings, enable GitHub Pages and choose the `main` branch (`/` root) as the publishing source.
3. The site will publish to `https://<username>.github.io/<repo>/` or to your configured custom domain.

### Switching Between Repo Pages and a Custom Domain
- **GitHub Pages (default repo URL)**
  - Set `_config.yml`:
    ```yaml
    url: https://<username>.github.io
    baseurl: "/the-daily-anomaly"
    ```
  - Remove or rename any `CNAME` file if you no longer use a custom domain.
- **Custom Domain (e.g., news.promireclabs.work)**
  - Set `_config.yml`:
    ```yaml
    url: https://news.promireclabs.work
    baseurl: ""
    ```
  - Add a `CNAME` file containing the domain (already present in this repo).
  - Configure DNS: create a `CNAME` record pointing your subdomain to `<username>.github.io`.
  - In GitHub Pages settings, specify the custom domain so GitHub can provision TLS.

After changing `url` or `baseurl`, redeploy (push or trigger a rebuild) so all canonical and internal links update automatically.

## Verification Checklist
- `bundle exec jekyll build` completes without warnings.
- Visit a story page (e.g., `/content/2025-09-25/cryptocurrency-scammers-are-trying-to-exploit-typos-in-your-digital-wallet.html`) and confirm the evidence badge, drop cap, hero image, and sources render correctly.
- Visit `/editions/2025-09-25.html` to confirm the two-column story list on desktop and single column on mobile.
- Visit `/editions/` to see all editions listed newest first.
- Use browser dev tools Lighthouse audit to confirm accessibility contrast stays above WCAG AA.
