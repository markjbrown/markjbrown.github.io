# markjbrown.com

Personal site for Mark Brown, hosted on GitHub Pages.

Built with [Jekyll](https://jekyllrb.com/) + the
[Minima](https://github.com/jekyll/minima) theme dependency. Local layouts and a
shared stylesheet provide the site's editorial design; no frontend framework
or client-side content loading is required.

## Editing content

- `index.md` and `about.md` contain the introduction and career narrative.
- `_data/projects.yml` is the source of truth for the portfolio and home-page
  selected work. Set `featured` to group projects and `home` to select home-page
  entries. Preserve the `id` when editing an entry so its portfolio link stays
  stable. Each entry documents the purpose, developer value, my role, technology,
  repository, and public evidence; role claims should remain specific and
  attributable.
- `projects.md` presents the curated portfolio at `/projects/`; the navigation
  label is **Portfolio**. There are no live GitHub API requests.
- `blog.md` lists posts from `_posts/`. Post dates, tags, and content are rendered
  by the shared post layout.
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
