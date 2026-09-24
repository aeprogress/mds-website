# mds-website

My personal website for the UBC Master of Data Science program, built with
Quarto and hosted on GitHub Pages at <https://aeprogress.github.io/mds-website/>.
It includes two computational blog posts: one in Python and one in R.

## Requirements

Install these first. Versions are the ones I used:

- [Quarto](https://quarto.org/docs/get-started/) 1.10.18
- [uv](https://docs.astral.sh/uv/getting-started/installation/) 0.12.7
  (uv installs Python 3.14 for you)
- [R](https://cran.r-project.org/) 4.6.1

You do not need to install renv; it bootstraps itself from `renv/activate.R`.

## Build the site

Run every command below in a terminal from the top level of the repository
(the folder that contains `_quarto.yml`).

1. Clone the repository and move into it:

```bash
   git clone https://github.com/aeprogress/mds-website.git
   cd mds-website
```

2. Create the Python environment from `uv.lock`:

```bash
   uv sync
```

3. Restore the R packages from `renv.lock`:

```bash
   Rscript -e 'renv::restore(prompt = FALSE)'
```

4. Render the site with the project's Python environment:

```bash
   uv run quarto render
```

## View the built site

The rendered site is written to `docs/`. Open `docs/index.html` in a browser:

- macOS: `open docs/index.html`
- Windows (Git Bash): `start docs/index.html`
- Linux: `xdg-open docs/index.html`

## Data

Both posts use the [Palmer Penguins](https://allisonhorst.github.io/palmerpenguins/)
data (CC0), loaded from the `palmerpenguins` package in Python and R.
No data files are committed to this repository.

Steps 2 and 3 need the internet to download packages. Rendering (step 4)
does not, because the data ships inside the packages.