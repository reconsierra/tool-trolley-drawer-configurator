# Würth Toolbox Configurator

A self-contained static HTML toolbox configurator for GitHub Pages.

## Deploy with GitHub Pages

1. Create a new GitHub repository.
2. Upload `index.html` and this `README.md` to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select the `main` branch and the `/ (root)` folder, then select **Save**.
6. Wait for GitHub Pages to publish the site.

The configurator is self-contained. The sample images and the current article list are embedded in `index.html`, so no additional image or Excel files are needed for the live test.

## Updating the article data later

The current article list is embedded in the JavaScript section of `index.html`. Replace the temporary descriptions and shared sample image when the final product descriptions and article images are available.

## Local test

Open `index.html` in a modern browser, or serve the folder with a local web server:

```bash
python3 -m http.server 8000
```

Then browse to:

http://localhost:8000
