# Fuchs Lubricant Selector

Website: https://tomwatson1860-prog.github.io/fuchs-lubricant-selector/

The selector scores the FUCHS lubricants on the US product finder for 16 applications, using each product's published base oil, viscosity, thickener and temperature range. Each result links to the product's page on fuchs.com.

The site asks for an access code. The selector itself is stored in `index.html` in encrypted form (AES-GCM, with the key derived from the access code) and is decrypted in the visitor's browser, so this repository holds no readable copy of it. Ask the owner for the code.

Not an official FUCHS tool. Product data comes from fuchs.com and published FUCHS and Nye data sheets; check the current product data sheet before specifying a product.

## Updating the site

Rebuild from the selector's published page, then check it in a headless browser:

```
ACCESS_CODE=<code> node tools/build_site.js <selector index.html> - index.html
ACCESS_CODE=<code> NODE_PATH=$(npm root -g) node tools/check_site.js index.html - --expect "#list .row"
```

## Safety

- Everything the page needs is served from this site. The page uses no outside script libraries. The fonts are in `fonts/`. Each of these files is fingerprinted (Subresource Integrity, SHA-384), so a browser refuses any copy that has been altered.
- The code screen sets a Content Security Policy that blocks loading anything from other servers, and sends no referrer when visitors follow a link out.
- No cookies, analytics or forms that send data; the access code is checked in the visitor's browser and never leaves it.
- `tools/build_site.js` stops if the page tries to load a script that isn't pinned and fingerprinted in `tools/libs.json`, or anything else from another server. `tools/check_site.js` only passes when the browser makes no outside requests and refuses deliberately altered copies of the fingerprinted files.
