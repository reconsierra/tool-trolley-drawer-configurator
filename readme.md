# Würth Toolbox Configurator

A browser-based configurator for planning the insert layout of a Würth toolbox with five drawers.

The application is designed for GitHub Pages and runs from **`index.html`** together with the matching product photos in the **`images/`** folder.

## What the configurator does

- Models five independent toolbox drawers.
- Shows each drawer as two side-by-side insert lanes.
- Uses the physical drawer dimensions of **670 mm wide × 462 mm deep**.
- Represents each lane as **335 mm wide × 462 mm deep**.
- Supports the available insert patterns:
  - `8.4.1`
  - `4.4.1`
  - `6.4.1`
  - `2.4.1`
  - Unused capacity
- Filters the article catalogue by the selected insert size.
- Displays the relevant sample artwork for each insert size.
- Places the selected article into the chosen physical position.
- Shows the Würth article number on placed inserts.
- Creates an article list and copies drawer configurations for planning.

## Basic operation

### 1. Choose a drawer

Use the drawer tabs across the top of the configuration area:

- `Drawer 1`
- `Drawer 2`
- `Drawer 3`
- `Drawer 4`
- `Drawer 5`

Each drawer is configured independently.

### 2. Select a lane

Click either the **Left bay** or **Right bay** in the drawer diagram.

The selected lane is highlighted and its available layout patterns are shown in the **Choose the lane pattern** panel.

### 3. Choose an insert pattern

Select the required pattern for the active lane. The main patterns are:

- **One 8.4.1** — one full-height insert in the lane.
- **Two 4.4.1** — two 4.4.1 positions stacked vertically.
- **One 4.4.1 + one 2.4.1** — one larger position and one smaller position.
- **One 4.4.1 + two 2.4.1** — one 4.4.1 position and two 2.4.1 positions.
- **Four 2.4.1** — four smaller positions stacked vertically.
- **One 6.4.1 + one 2.4.1** — one 6.4.1 position and one 2.4.1 position.
- Patterns with open capacity where part of the lane remains unused.

Changing a lane pattern clears the article selections in that lane so that the physical positions cannot become mismatched.

### 4. Select a physical insert position

Click a coloured insert position in the drawer diagram.

The **Compatible articles for this position** area will then show every loaded article that matches that insert size. For example, selecting a `4.4.1` position shows only the articles assigned to `4.4.1`.

An open or grey position represents unused capacity and cannot have an article assigned to it.

### 5. Select an article

Click **Select this article** on the required catalogue card.

The article will be placed into the selected physical position. The article number appears as an overlay on the placed insert image.

To replace an article, select the same physical position again and choose another compatible article.

## Planning tools

The planning controls are available in the top bar and again near the bottom of the page.

### Create article list

Select **Create article list** to display a list of all articles assigned to physical positions.

The list includes:

- Drawer
- Lane
- Position
- Article number
- Insert size
- Description

### Copy article list

Select **Copy article list** to copy the assigned article list to the clipboard.

If clipboard access is blocked by the browser, the application provides a fallback copy method. If that is also unavailable, the displayed planning output can be copied manually.

### Copy drawer configurations

Select **Copy drawer configurations** to copy the layout and article assignment information for all five drawers.

This is useful for transferring a planned configuration into another document, email or planning system.

## Deploy with GitHub Pages

1. Create a new GitHub repository.
2. Upload **`index.html`** to the repository root.
3. Upload the complete **`images/`** folder, including all matching `.jpg` files, to the repository root.
4. Optionally upload this **`readme.md`** for project documentation.
5. Open **Settings → Pages**.
6. Under **Build and deployment**, choose **Deploy from a branch**.
7. Select the `main` branch and the `/ (root)` folder.
8. Select **Save** and wait for GitHub Pages to publish the site.

The live application requires both `index.html` and the `images/` folder. The Excel workbook is not required for normal operation because the article numbers, descriptions, insert sizes and image paths are already included in the application.

## Local testing

The simplest option is to open `index.html` directly in a modern browser.

For a local web server, open a terminal in the folder containing `index.html` and run:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

A local web server is recommended when testing clipboard behaviour or browser security features.

## Browser requirements

Use a current version of:

- Microsoft Edge
- Google Chrome
- Mozilla Firefox
- Safari

The application uses standard browser features including JavaScript, canvas image conversion and clipboard access. Product images are loaded from the relative `images/` folder, so keep that folder beside `index.html` when testing or deploying. The layout is responsive and can be used on smaller screens, although a larger screen is preferable when planning a complete drawer set.

## Important behaviour

- The configurator keeps changes in the current browser session only.
- There is no database or server-side save function.
- Refreshing the page or closing the browser resets the current configuration.
- Copy or create the planning output before refreshing if the configuration needs to be retained.
- The application is a layout-planning tool; it does not place orders or check stock availability.

## Updating article data or images

The current article data is stored inside the JavaScript section of `index.html`. Each record contains:

- The display article number, with Würth spacing such as `0965 905 903`.
- The normalised SAP article number used for image lookup, such as `0965905903`.
- The workbook description.
- The insert size.
- A matching relative image path in the form `images/0965905903.jpg`.

The image filename must match the normalised SAP article number exactly, apart from the `.jpg` extension. When updating the file:

1. Keep the article number and insert-size values in the same format.
2. Ensure each article has the correct insert size and description.
3. Add the corresponding product photo to the `images/` folder.
4. Keep the image filename aligned with the normalised SAP article number.
5. Test each insert size after making changes.
6. Confirm that the article counts and compatible-article filtering still work.

The current workbook contains 76 articles: 23 for `8.4.1`, 33 for `4.4.1`, 6 for `6.4.1` and 14 for `2.4.1`. The application uses the original product-photo orientation and `object-fit: contain` so the images are not rotated or unnecessarily cropped.

## Troubleshooting

### No articles appear

1. Select a drawer tab.
2. Click the left or right bay.
3. Click a coloured insert position, not an open position.
4. Check that the selected position has an insert size such as `4.4.1` or `6.4.1`.

### The article list is empty

No articles have been assigned yet. Select an insert position, choose a compatible article, and then select **Create article list**.

### Copy does not work

Try the application from a local web server or a published HTTPS GitHub Pages site. If clipboard access is still unavailable, use the visible planning output and copy it manually.

### A layout has changed unexpectedly

Changing a lane pattern intentionally clears the article selections in that lane. This prevents an article from remaining assigned to a physical position that no longer exists.

## Project files

For a basic GitHub Pages deployment, use:

```text
index.html
```

This README is documentation only; it is not required for the configurator itself.
