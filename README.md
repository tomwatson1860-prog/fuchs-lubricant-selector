# Fuchs Lubricant Selector

Website: https://tomwatson1860-prog.github.io/fuchs-lubricant-selector/

The selector scores the FUCHS lubricants on the US product finder for 16 applications, using each product's published base oil, viscosity, thickener and temperature range. Each result links to the product's page on fuchs.com.

The site asks for an access code. The selector itself is stored in `index.html` in encrypted form (AES-GCM, with the key derived from the access code) and is decrypted in the visitor's browser, so this repository holds no readable copy of it. Ask the owner for the code.

Not an official FUCHS tool. Product data comes from fuchs.com and published FUCHS and Nye data sheets; check the current product data sheet before specifying a product.
