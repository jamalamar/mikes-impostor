# How to Generate the OG Image

To create the `og-image.png` from the `og-image.html` file, you have several options:

## Option 1: Using Chrome/Edge DevTools (Easiest)
1. Open `og-image.html` in Chrome or Edge
2. Press F12 to open DevTools
3. Press Ctrl+Shift+P (or Cmd+Shift+P on Mac)
4. Type "screenshot" and select "Capture full size screenshot"
5. Save as `og-image.png` in the same folder

## Option 2: Using Online HTML to Image Converter
1. Go to https://htmlcsstoimage.com/ or similar service
2. Copy the content of `og-image.html`
3. Paste it and generate the image
4. Download as `og-image.png`

## Option 3: Using Command Line (if you have Chrome installed)
```bash
# On Mac/Linux
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --headless --screenshot=og-image.png --window-size=1200,630 --default-background-color=0 og-image.html

# On Windows
chrome --headless --screenshot=og-image.png --window-size=1200,630 --default-background-color=0 og-image.html
```

## Option 4: Using Puppeteer (Node.js)
```javascript
const puppeteer = require('puppeteer');

(async () => {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();
  await page.setViewport({ width: 1200, height: 630 });
  await page.goto('file://' + __dirname + '/og-image.html');
  await page.screenshot({ path: 'og-image.png' });
  await browser.close();
})();
```

The image should be exactly 1200x630 pixels for optimal display on WhatsApp and other social platforms.