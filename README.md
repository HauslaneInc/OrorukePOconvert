# O'Rourke PO → Sellercloud CSV

Web app that converts O'Rourke Sales purchase-order PDFs (one or many POs per file) into a Sellercloud wholesale order CSV.

**Live app:** https://hauslaneinc.github.io/ororukepoconvert/

Everything runs in the browser — PDFs are never uploaded anywhere.

## Rules applied
- **Electronic Express** (company line contains "Electronic Express"): `ShipFirstName` = `EE - <number>`, `ShipLastName` = recipient, `ShipAddress2` blank, `BillEmail` = wes@electronicexpress.com.
- **Dealer drop-ships**: first/last name blank, DBA line (if any) → `ShipAddress2`, `BillEmail` = tjeffries@orourkesales.com.
- Billing is the fixed O'Rourke Davenport, IA block; ship country is always US.
- One CSV row per PO line; unit prices formatted to two decimals.
- PDF kerning artifacts in descriptions ("Wall Mo unt", "Under C abinet", "Convert ible") are cleaned up.
- Each PO's line count and total are checked against the totals printed on the PDF; mismatches are flagged.
- Shipping carrier, rush, shipping cost, tax and warehouse are blank by default and can be set in the "Fixed fields" panel.
