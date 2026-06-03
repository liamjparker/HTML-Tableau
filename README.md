# Dashboard Report Generator

A single-file web application for generating professional Tableau documentation reports from Excel workbooks. Upload a structured `.xlsx` file, preview the formatted report, then export to PDF or Word.

## Features

- **Drag & drop upload** — accepts `.xlsx`, `.xls`, and `.xlsm` files
- **Live preview** — renders a formatted report in the browser before exporting
- **PDF export** — prints the report as a clean A4 document
- **Word export** — downloads a `.doc` file with full formatting
- **No server required** — runs entirely in the browser as a single HTML file

## Excel Workbook Structure

The app looks for up to four sheets by name (partial, case-insensitive match):

| Sheet | Expected columns |
|-------|-----------------|
| **Summary** | Dashboard Name, Summary/Description, Developer, Main Users |
| **Data Source** | Name/Source, Connection/Type, Classification, Frequency, Comments |
| **Calculations** | Name, Formula/Expression, Comments |
| **Change Log** | Dashboard, Date, Type, Comments |

Column names are matched flexibly — exact names are not required as long as they contain the keywords above.

### Change Log — Type values

The `Type` column in the Change Log sheet uses colour-coded badges:

| Value contains | Badge colour |
|----------------|-------------|
| `new`, `add` | Green |
| `fix`, `bug` | Red |
| `update`, `edit` | Blue |
| `remove`, `del` | Amber |

### Data Source — Connection values

| Value contains | Badge colour |
|----------------|-------------|
| `api` | Purple |
| `sql`, `db`, `database` | Blue |
| `excel`, `csv`, `file` | Green |
| `share`, `point` | Amber |

## Usage

1. Open `index.html` in any modern browser (Chrome, Edge, Firefox, Safari).
2. Drop your Excel workbook onto the upload area, or click to browse.
3. The tab indicators turn green for each sheet that was found.
4. Review the report preview.
5. Click **Export PDF** to print/save as PDF, or **Export Word** to download a `.doc` file.
6. Click **Upload new file** to start over.

## Deployment

Because the app is a single self-contained HTML file with no build step or server dependency, deployment is straightforward:

- **Confluence** — attach `index.html` to a page and embed it with the HTML macro
- **SharePoint** — upload to a document library and open directly in the browser
- **GitHub Pages / any static host** — push `index.html` to the root and enable static hosting
- **Local** — open the file directly from your filesystem

## Dependencies

The only external dependency is loaded via CDN:

- [SheetJS (xlsx)](https://sheetjs.com/) `0.18.5` — Excel file parsing
