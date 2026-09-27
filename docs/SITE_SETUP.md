# Personal website setup

This repository uses the existing **al-folio v1** starter. The original template is retained on `backup/al-folio-initial-2026-09-27`.

## One-time GitHub Pages activation

After **Deploy site** succeeds and creates `gh-pages`:

1. Open <https://github.com/Jisay1130/homepage/settings/pages>.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select **gh-pages** and **/(root)**, then **Save**.
4. Check GitHub's Pages deployment status. The intended website address is <https://jisay1130.github.io/homepage/>.

Do not select `main`: it contains Jekyll source, not the generated website. The repository's Pages setting is an account-level step separate from committing source files.

## Editing the site

| File                         | Purpose                                                   |
| ---------------------------- | --------------------------------------------------------- |
| `_config_personal.yml`       | Name, description, URL, enabled features, demo exclusions |
| `_pages/about.md`            | Home page                                                 |
| `_pages/research.md`         | Research overview                                         |
| `_pages/cv.md`               | Web CV                                                    |
| `_bibliography/personal.bib` | Verified publications, when ready                         |

`_config.yml` retains upstream defaults. Always load `_config_personal.yml` after it; the deployment workflow does this automatically.

### Local development

With Ruby and Bundler installed:

```bash
bundle install
bundle exec jekyll serve --config _config.yml,_config_personal.yml
```

Open the local address reported by Jekyll, including `/homepage/`.

### Public-content boundaries

The initial site includes only a basic academic background, research interests, tools, and the GitHub profile link. Institution names, degree dates, contact details, photos, paper titles, award details, and a downloadable CV have not been invented. Add them once confirmed for publication.

The demo biography, sample publications, sample CV PDF, demo pages, and demo collections are excluded from this site's build. Original template files remain in source for reference. A plain web CV is used; the optional RenderCV PDF workflow is not needed for the website build.

### Future root-domain migration

A root user website would use a repository named `Jisay1130.github.io`, with `baseurl: ""`. The current setup deliberately retains the existing `homepage` repository and uses `/homepage`. Do not change only the URL without updating the repository and Pages settings consistently.

## Credits

Theme: <https://github.com/alshedivat/al-folio> (MIT). The original licence remains in the repository.

Official deployment guide: <https://github.com/alshedivat/al-folio/blob/main/docs/INSTALL.md>.
