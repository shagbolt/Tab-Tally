# Tab & Tally

Restaurant check calculator, splitter, and dining journal. Runs entirely on the device, including receipt reading (Tesseract.js, Apache 2.0).

## Put it on GitHub Pages
1. Create a repo (for example `shagbolt/tabtally`) and upload everything in this folder, keeping the `icons/` and `ocr/` folders.
2. Settings > Pages > Deploy from branch > `main` / root.
3. Open `https://shagbolt.github.io/tabtally/` in Safari on the iPhone, tap Share > Add to Home Screen.

The first receipt scan downloads nothing extra: the reader and English data (about 11 MB) come from this repo and are cached for offline use.
When you change `index.html`, bump `CACHE` in `sw.js` (for example tabtally-v2 to v3) so phones pick up the update.

## Read Receipt shortcut (Apple Intelligence)
Actions: Take Photo > Extract Text from Image > Use Model (prompt below, Private Cloud Compute) > Copy to Clipboard.
Then open Tab & Tally and tap Paste from Shortcut. If you use Tab & Tally in Safari instead of from the Home Screen,
you can add URL Encode > Open URLs with `https://shagbolt.github.io/tabtally/#r=` followed by the encoded result.

Prompt for Use Model:

    Read this restaurant receipt text and reply with only a JSON object, no other words and no code fences.
    Keys: "restaurant" (name of the restaurant), "address" (street address), "city", "phone", "date" (YYYY-MM-DD),
    "items" (array of objects with "name", "qty", and "price", where price is the cost of ONE unit),
    "subtotal" (food and drink before tax), "tax" (all taxes added together),
    "total" (amount including tax but BEFORE any tip), "tip" (only if a tip is printed or written).
    Use plain numbers without dollar signs. Use null for anything not on the receipt. Never make up items or amounts.
    If the receipt is a card slip showing only an amount and a tip, put that amount in "total" and leave "items" empty.

    Receipt text:
    [Extracted Text]

