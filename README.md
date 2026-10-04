# Resume — Mariana Ozaeta

Program evaluation · mixed-methods research · data analytics

**Live version:** https://t00th-blip.github.io/Resume/

A reproducible resume. All content lives in one CSV; the layout is R Markdown and CSS, so
updating a job or adding a project means editing a spreadsheet row and re-knitting — not
reformatting a document.

**Project case studies and code:** [github.com/t00th-blip/Portfolio](https://github.com/t00th-blip/Portfolio)

## Files

| File | What it does |
|---|---|
| `positions.csv` | All resume content, one row per entry. The `section` column routes each row to a section; `description_1` … `description_5` become the bullets. |
| `resume.Rmd` | The template — sidebar text, intro, and the `print_section()` calls that render each section. |
| `parsing_functions.R` | Helpers that turn CSV rows into formatted entries. `print_section()` does the work. |
| `css/styles.css` | Base theme: fonts and colors. |
| `css/custom_resume.css` | Template's layout adjustments. |
| `css/spacing.css` | Typography and spacing overrides. Five tunable variables at the top. |
| `resume.html` | Knitted output — this is what GitHub Pages serves. |
| `RESUME.md` | Plain-markdown version, readable without rendering. |
| `OzaetaResume.docx` | Word version, for applications that require a file upload. |

## Updating it

1. Edit `positions.csv`. One row per entry; set `in_resume` to `TRUE` to include it.
2. Knit `resume.Rmd` in RStudio.
3. Commit the `.Rmd`, the CSV, and the regenerated `resume.html`.

Adding a bullet to an entry means filling the next empty `description_N` column. The parsing
function gathers every column beginning with `description`, so adding a `description_6` column
works without touching any R code.

Adding a whole new section means adding rows with a new `section` value, then calling
`position_data %>% print_section('your_section')` under a new heading in `resume.Rmd`.

Set `PDF_EXPORT <- TRUE` in the setup chunk to move links into numbered footnotes for printing,
then knit and print to PDF from the browser.

## Spacing and layout

`css/spacing.css` controls leading, the gap between entries, the gap between bullets, the space
above section headings, and the page margins. Each is a CSS variable at the top of the file:

```css
--rz-line-height:  1.55;
--rz-entry-gap:    0.17in;
--rz-bullet-gap:   0.055in;
--rz-section-gap:  0.30in;
--rz-page-margin:  0.35in;
```

Too airy, reduce the gaps. Too tight, raise them. To revert to the stock template look, remove
`'css/spacing.css'` from the `css:` list in the `resume.Rmd` YAML header.

## Built with

[pagedown](https://pagedown.rbind.io) `html_resume`, from a modified version of
[Nick Strayer's CV template](https://github.com/nstrayer/cv).
