# Würth Toolbox Configurator

A browser-based configurator for planning Würth toolbox drawer layouts and assigning compatible products to individual insert positions.

The app is designed around a five-drawer toolbox, with each drawer containing two independent insert lanes.

## Features

- Configure five toolbox drawers independently.
- Display each drawer as two physical lanes:
  - Left lane: 335 mm wide × 462 mm deep
  - Right lane: 335 mm wide × 462 mm deep
- Select from available lane layouts, including:
  - `8.4.1`
  - `4.4.1`
  - `6.4.1`
  - `2.4.1`
  - Unused capacity
- Select a specific insert position within a lane.
- Display only compatible articles for the selected insert size.
- Present every matching article number as an individual selectable choice.
- Place the selected article image into the chosen drawer position.
- Use portrait display for `8.4.1` inserts.
- Use landscape display for `6.4.1`, `4.4.1` and `2.4.1` inserts.
- Retain independent configurations for all five drawers.
- Use embedded sample data and images for testing.
- Operate as a self-contained static HTML application.

## Physical drawer model

Each drawer has the following internal footprint:

```text
670 mm wide × 462 mm deep
```

The drawer is divided into two side-by-side lanes:

```text
┌───────────────────────┬───────────────────────┐
│       Left lane       │      Right lane       │
│     335 × 462 mm      │     335 × 462 mm      │
└───────────────────────┴───────────────────────┘
```

Each lane can be configured independently.

## User workflow

1. Select a toolbox drawer.
2. Select the left or right lane.
3. Choose a lane layout.
4. Select a specific insert position.
5. Review the compatible article list.
6. Select an article number.
7. The sample image is placed into the selected drawer position.
8. Repeat the process for the remaining positions and drawers.

## Current article data

The current prototype contains 76 article records from the insert article spreadsheet.

Article counts by insert size:

| Insert size | Article count |
|---|---:|
| `8.4.1` | 23 |
| `4.4.1` | 33 |
| `2.4.1` | 14 |
| `6.4.1` | 6 |
| **Total** | **76** |

The current records contain:

- Article number
- Page number
- Insert size
- Temporary description
- Shared sample image

The descriptions and images are placeholders for testing and can be replaced with the final product data later.

## Repository contents

```text
.
├── index.html
├── README.md
└── .nojekyll
```

The application is contained entirely in `index.html`.

No separate Excel file, image folder or server-side database is required for the current test version.

## Deploy with GitHub Pages

### 1. Create a repository

Create a new repository in GitHub.

For example:

```text
wurth-toolbox-configurator
```

### 2. Upload the files

Upload the following files to the repository root:

- `index.html`
- `README.md`
- `.nojekyll`

### 3. Enable GitHub Pages

1. Open the repository on GitHub.
2. Select **Settings**.
3. Select **Pages** in the left-hand menu.
4. Under **Build and deployment**, select:
   - **Source:** Deploy from a branch
   - **Branch:** `main`
   - **Folder:** `/ (root)`
5. Select **Save**.

GitHub will publish the application and provide the live website address.

## Run locally

You can open `index.html` directly in a modern browser.

Alternatively, start a local web server from the repository folder:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

## Updating article data

The article list is currently embedded in the JavaScript section of `index.html`.

To update the article data:

1. Open `index.html` in a code editor.
2. Locate the `spreadsheetArticles` array.
3. Add or update the article records.
4. Replace the temporary description.
5. Replace the shared sample image with the correct product image.
6. Save the file.
7. Commit and push the changes to GitHub.

Each article record follows this structure:

```javascript
{
  size: '8.4.1',
  article: '0965 905 903',
  page: '4',
  description: 'Sample product description',
  image: sharedSampleImage
}
```

## Adding final product images

The current prototype uses one shared sample image for every article.

For the final version, each article can use its own image:

```javascript
{
  size: '8.4.1',
  article: '0965 905 903',
  page: '4',
  description: 'Final product description',
  image: 'images/0965-905-903.png'
}
```

If separate image files are used, the repository could be organised as follows:

```text
.
├── index.html
├── README.md
├── .nojekyll
└── images
    ├── 0965-905-903.png
    ├── 0965-905-921.png
    └── ...
```

The image path in the JavaScript must match the image filename and folder location.

## Browser compatibility

The app is intended for current versions of:

- Google Chrome
- Microsoft Edge
- Mozilla Firefox
- Apple Safari

JavaScript must be enabled in the browser.

## Technology

The application uses:

- HTML
- CSS
- JavaScript
- Embedded image data
- GitHub Pages for static hosting

No build process or package installation is required.

## Project status

This is a functional prototype for live testing.

Current placeholders include:

- Product descriptions
- Product images
- Some catalogue metadata

The physical drawer geometry and lane-selection workflow are implemented for testing.
