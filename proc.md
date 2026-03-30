# Process

 1. Export Project Porfolio XLSX from Webapp
 2. Remove Unwanted Columns (right of XM-TR)
 3. Remove Tier 3 Rows (GIS Infra person mostly adds these)
 4. Run: `python update_dashboard.py Project_Portfolio.xlsx --embed index.html`
 5. Open `index.html`


```bash
python3 update_dashboard.py Project_Portfolio.xlsx --embed index_tv.html
python3 update_dashboard.py Project_Portfolio.xlsx --embed index_tv_interactive.html
python3 update_dashboard.py Project_Portfolio.xlsx --embed index_gantt.html
```

