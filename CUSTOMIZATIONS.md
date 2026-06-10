# Customizations

This site is based on `academicpages/academicpages.github.io`, but a few areas have been customized for bilingual content, local rendering stability, and this resume-style homepage.

## Summary

| Area | Template default | Current implementation | Maintenance note |
|---|---|---|---|
| Language support | No built-in bilingual page switch | Chinese and English pages are separate static routes | Keep `lang` and `alternate_url` in page front matter in sync |
| Navigation | Single navigation list from `_data/navigation.yml` | Uses `main` and `main_en` navigation lists | Update both lists when adding top-level pages |
| Theme toggle | Template JavaScript provides theme switching | Theme button is restored with inline SVG icons and an extra native click handler | Keep `#theme-toggle` and `#theme-icon` IDs if editing the button |
| Font Awesome icons | Template uses Font Awesome classes | Contact icons use inline SVG to avoid font rendering issues | Prefer SVG contact icons in `_includes/contact-icon.html` |
| Author profile | Author data comes from `site.author` by default | English pages use `_data/authors.yml` with `author: en` | Add translated authors in `_data/authors.yml` if more languages are added |
| Avatar | Optional `author.avatar` | Uses `images/profile.png` with a fallback in `_includes/author-profile.html` | Replace `images/profile.png` to change the displayed avatar |
| Footer locale | Uses `site.locale` globally | Footer switches locale on English pages | Keep `page.lang` set correctly |
| HTML language | Uses `site.locale` globally | `_layouts/default.html` uses `page.lang` when present | Set `lang: en` on English pages and `lang: zh` on Chinese pages |

## Bilingual Pages

Chinese pages:

| Page | Route | Alternate |
|---|---|---|
| `_pages/about.md` | `/` | `/en/` |
| `_pages/cv.md` | `/cv/` | `/en/cv/` |
| `_pages/portfolio.html` | `/portfolio/` | `/en/portfolio/` |

English pages:

| Page | Route | Alternate |
|---|---|---|
| `_pages/about-en.md` | `/en/` | `/` |
| `_pages/cv-en.md` | `/en/cv/` | `/cv/` |
| `_pages/portfolio-en.md` | `/en/portfolio/` | `/portfolio/` |

Each bilingual page should include:

```yaml
lang: en
alternate_url: /matching/chinese/path/
```

or:

```yaml
lang: zh
alternate_url: /matching/english/path/
```

English pages also use:

```yaml
author: en
```

The `en` author is defined in `_data/authors.yml`.

## Theme Toggle

The visible theme button is defined in `_includes/masthead.html`.

The original template JavaScript still exists in `assets/js/main.min.js`, but this site also adds a small native JavaScript fallback in `_includes/scripts.html`.

That fallback:

- toggles `html[data-theme="dark"]`;
- stores the selected theme in `localStorage.theme`;
- uses capture-phase click handling on `#theme-toggle` to avoid double toggles if the template's jQuery handler also fires.

Do not remove these IDs unless the JavaScript is updated too:

```html
id="theme-toggle"
id="theme-icon"
```

The button icons are inline SVG, not Font Awesome.

## Icons

Font Awesome assets still exist in the template, but visible contact icons in the author profile intentionally use inline SVG.

Reason: in the local Windows/Jekyll/Sass build chain, Font Awesome private-use Unicode output rendered as square boxes in the browser.

Contact icons live in:

```text
_includes/contact-icon.html
```

Their shared CSS lives in:

```text
_sass/include/_utilities.scss
```

## Author Profile

The author profile include has been customized:

```text
_includes/author-profile.html
```

Changes:

- supports English labels when `page.lang: en`;
- uses `_data/authors.yml` for English author data;
- falls back to `profile.png` when no avatar is provided;
- uses inline SVG contact icons.

## Files Changed From Template Behavior

| File | Purpose |
|---|---|
| `_includes/masthead.html` | Bilingual navigation, language switch, theme button |
| `_includes/scripts.html` | Native theme toggle fallback |
| `_includes/author-profile.html` | Bilingual author profile and avatar fallback |
| `_includes/contact-icon.html` | Inline SVG contact icons |
| `_includes/footer.html` | Footer locale switching |
| `_includes/head/custom.html` | Theme icon display guard styles |
| `_layouts/default.html` | Per-page HTML language |
| `_data/navigation.yml` | Chinese and English navigation lists |
| `_data/authors.yml` | English author profile |
| `_sass/layout/_masthead.scss` | Theme button styling |
| `_sass/include/_utilities.scss` | Contact SVG icon styling |

## Local Development

Build:

```powershell
$env:Path='C:\Ruby33-x64\bin;'+$env:Path; bundle exec jekyll build
```

Serve:

```powershell
cmd /c "cd /d E:\WorkSpeace\githubPage\neomu.github.io && set PATH=C:\Ruby33-x64\bin;%PATH% && bundle exec jekyll serve --host 127.0.0.1 --port 4000 --no-watch"
```

Local URL:

```text
http://127.0.0.1:4000/neomu.github.io/
```

If changes do not appear, check for old Ruby/Jekyll processes still listening on port `4000`.
