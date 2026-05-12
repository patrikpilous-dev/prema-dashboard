# prema-dashboard — i-prema.de orders + weather + map

Klouzavý rok prodejů s napojením na počasí (Berlin Open-Meteo). DE Shoptet export.

- **Live URL:** _bude doplněno po push na GitHub Pages_
- **Data:** Shoptet DE export (cp1250, sep=";"), klouzavý rok
- **Anonymizace:** GDPR — drop jméno/email/telefon/adresa/IP, ponecháno město + první 2 znaky PSČ (PLZ-Leitzahl)

## Update workflow

1. Nový export `orders (3).csv` do `C:\Users\patri\Downloads\`
2. Spustit pipeline:
   ```
   python prema_prepare.py
   python prema_analyza.py
   python prema_rozsirena_analyza.py
   python prema_dny_tydne.py
   python prema_mapa.py
   python prema_html_generator.py
   ```
3. `git add index.html mapa_bundeslander.html && git commit -m "Update YYYY-MM-DD" && git push`

## Generování dashboardu

Scripty v `C:\Users\patri\Claude Code ukládané soubory\prema_*.py` produkují:

- `prema_orders.csv` — anonymizovaný master
- `prema_korelace.png`, `prema_denni_data.csv`
- `prema_teplotni_analyza.xlsx`, `prema_dny_tydne.xlsx`
- `prema-dashboard/index.html` + `mapa_bundeslander.html`
