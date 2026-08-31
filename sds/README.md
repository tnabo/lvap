# Safety Data Sheets (SDS)

This folder holds the PDF Safety Data Sheets that are linked from the site footer.

## Expected files

The footer "Documents" section on every page links to these exact filenames — drop the PDFs
in here with these names and the links will work:

| Filename                          | Product it covers                        |
| --------------------------------- | ---------------------------------------- |
| `urinal-descaler.pdf`             | Heavy Duty Urinal Descaler / Salt Remover (all pack sizes) |
| `toilet-bowl-descaler.pdf`        | Heavy Duty Toilet Bowl Descaler (all pack sizes)           |
| `silicone-grease-food-grade.pdf`  | Food-Grade Silicone Grease 50g            |
| `silicone-grease-high-temp.pdf`   | High-Temp Silicone Grease 113g (Red)      |

## Adding a new SDS

1. Drop the PDF in this folder with a lowercase, hyphenated filename (no spaces).
2. Add a `<li>` line to the "Documents" section in each of these files' footer:
   - `index.html`
   - `products.html`
   - `contact.html`

Example:
```html
<li><a href="sds/new-product.pdf" target="_blank" rel="noopener">New Product SDS</a></li>
```

## Notes

- SDSs are only required for chemical products (descalers, grease). Mats, screens, and
  keys don't need SDSs.
- Filenames are case-sensitive on GitHub Pages — keep them lowercase.
