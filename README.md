<!-- @format -->

# 📷 My Photography Portfolio

A personal photography portfolio built with [Hugo](https://gohugo.io/) and hosted on [GitHub Pages](https://pages.github.com/). The website is automatically built and deployed via GitHub Actions on every push to `main`.

**Live site:** [https://jeanyichenli.github.io/](https://jeanyichenli.github.io/)

---

## Tech Stack

- **Static Site Generator:** [Hugo](https://gohugo.io/) (Extended version)
- **Theme:** [hugo-theme-gallery](https://github.com/nicokaiser/hugo-theme-gallery)
- **Hosting:** GitHub Pages
- **CI/CD:** GitHub Actions

---

## Project Structure

```
.
├── .github/
│   └── workflows/
│       └── deploy.yml       # GitHub Actions workflow
├── content/
│   ├── album-name/          # Photo albums (each folder = one album)
│   │   ├── index.md.        # Album title and metadata
│   │   └── (photos)
│   └── _index.md            # Homepage (jeanyichenli.github.io)
|   └── about.md             # About me page
├── themes/
│   └── gallery/             # hugo-theme-gallery (git submodule)
├── .gitignore
├── .gitmodules
└── hugo.toml                # Site configuration
```

---

## Getting Started

### Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) installed on your machine
- Git

### Run Locally

```bash
# Clone the repository (including the theme submodule)
git clone --recurse-submodules https://github.com/jeanyichenli/jeanyichenli.github.io.git

cd jeanyichenli.github.io

# Start the local development server
hugo server -D
```

Then open your browser at `http://localhost:1313`.

> If you cloned without `--recurse-submodules`, run `git submodule update --init --recursive` to fetch the theme.

---

## Adding Content

### Add a New Photo Album

1. Create a new folder under `content/`:
   ```bash
   mkdir content/my-new-album-name
   ```
2. Add an `index.md` with the album metadata:
   ```markdown
   ---
   date: 2026-01-21
   title: Animals
   sort_by: Name
   menus: "main"
   resources:
     - src: PHOTO-NAME.jpg
       title: PHOTO NAME
       params:
         cover: true # choose this photo as album cover
   ---
   ```
3. Drop your `.jpg` or `.png` photos into the folder
4. Commit and push. GitHub Actions will then deploy automatically

---

## Deployment

Deployment is fully automated via GitHub Actions. Every push to the `main` branch will trigger the workflow in `.github/workflows/deploy.yml`:

1. Checks out the repository including the theme submodule
2. Installs Hugo Extended
3. Builds the site with `hugo --minify`
4. Deploys the `./public` output to GitHub Pages

No manual build step is needed on your local machine.

---

## Local vs Remote

| File type                                           | Commit to git?                 |
| --------------------------------------------------- | ------------------------------ |
| Source files (`content/`, `hugo.toml`, etc.)        | ✅ Yes                         |
| Theme (`themes/gallery/`)                           | ✅ Yes                         |
| Built output (`public/`)                            | ❌ No (record in `.gitignore`) |
| Hugo build cache (`resources/`, `.hugo_build.lock`) | ❌ No (record in `.gitignore`) |

---

## License

All photography is © Jean (Yi-Chen) Li. All rights reserved.
