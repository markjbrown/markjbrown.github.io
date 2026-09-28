# markjbrown.com

Personal site for Mark Brown, hosted on GitHub Pages.

Built with [Jekyll](https://jekyllrb.com/) + the
[Minima](https://github.com/jekyll/minima) theme dependency. Local layouts and a
shared stylesheet provide the site's editorial design; no frontend framework
is required. Content is rendered statically; Speaking links directly to Sessionize.

## Editing content

- `index.md` owns the career-led hero, selected impact, and career breadth;
  `about.md` provides the expanded career background.
- `_layouts/home.html` places compact supporting project links and recent writing
  after the career content.
- `_data/projects.yml` is the source of truth for the portfolio. Set `featured`
  to group projects and `home` to select supporting home-page links.
  Preserve the `id` when editing an entry so its portfolio link stays
  stable. Each entry documents the purpose, developer value, my role, technology,
  repository, and public evidence; role claims should remain specific and
  attributable.
  Optional `image` metadata adds a portfolio figure: set `src` to the local asset
  path, `width` and `height` to its intrinsic pixel dimensions, `alt` to a
  meaningful description, `caption` to contextual text, and `source_url` to the
  original public source for attribution. Images sit beside the narrative on
  wide screens and stack below it on smaller screens, preserving their aspect
  ratio within bounded dimensions without cropping or enlarging small originals.
  The image and its **View full-size image** link open the local original;
  internal asset URLs use `relative_url`. Home-page selected work stays text-only.
  Optional `sample_highlight.heading` and `sample_highlight.description` call out
  an example within an existing project without changing its role attribution.
- `projects.md` presents the curated portfolio at `/projects/`; the navigation
  label is **Portfolio**. There are no live GitHub API requests.
- `blog.md` lists posts from `_posts/`. Post dates, tags, and content are rendered
  by the shared post layout.
- Speaking links in the main navigation, home page, and footer use the Sessionize
  profile in `_config.yml` under `profile_links`. There is no local Speaking page
  or live session feed.
- `_layouts/`, `_includes/`, and `assets/css/site.css` control presentation.
  Profile links and site metadata live in `_config.yml`.

The site follows the system light/dark preference, including without JavaScript.
For design review, append `?scoutTheme=light` or `?scoutTheme=dark` to a page URL
to override the theme for that page. Internal links use Jekyll's `relative_url`
filter to support a configured `baseurl`.

## Local preview

```bash
bundle install
bundle exec jekyll serve
```

Then open <http://127.0.0.1:4000>.

## Custom domain

The `CNAME` file pins this site to `markjbrown.com`. DNS records live at the
domain registrar.
