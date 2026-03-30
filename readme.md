# PulsePoint

A lightweight portfolio management dashboard for visualizing project health, status, and progress across programs. Built with vanilla HTML/CSS/JS — no frameworks, no build step, works directly from the file system.

## Features

- **KPI summary cards** — total projects, health/status breakdowns at a glance
- **Health & program charts** — visual distribution of Green/Yellow/Red status
- **Search & filter** — full-text search plus filters for health, status, program, and coordinator
- **Table & card views** — toggle between a sortable data table and a card grid
- **Detail drawer** — click any project to see full details in a side panel
- **Dark/light theme** — toggle between themes
- **Multiple display modes** — standard dashboard, TV display (read-only), TV interactive, and Gantt chart views
- **Fully offline** — data embeds directly into HTML; no server required

## Quick Start

### Prerequisites

- Python 3.6+ with `openpyxl`
- A modern web browser

### Setup

```bash
# Install the Python dependency
pip install openpyxl

# Generate dashboard data from an Excel export
python update_dashboard.py Project_Portfolio.xlsx

# Or embed data directly into an HTML file (recommended for standalone use)
python update_dashboard.py Project_Portfolio.xlsx --embed index.html
```

Then open the HTML file in your browser — `file://` works fine.

### Display Variants

| File | Purpose |
|------|---------|
| `index.html` | Full interactive dashboard |
| `index_gantt.html` | Gantt chart timeline view |
| `index_tv.html` | TV/monitor display (read-only) |
| `index_tv_interactive.html` | TV display with filters |

Embed data into any variant:

```bash
python update_dashboard.py Project_Portfolio.xlsx --embed index_tv.html
```

## Data Flow

```
Excel (.xlsx)  -->  update_dashboard.py  -->  JSON  -->  Embedded in HTML
                     (openpyxl)                          (window.__PULSEPOINT_DATA__)
```

The Python script parses the Excel export, transforms it into structured JSON with project records and summary metadata, then either writes `dashboard_data.json` or injects the data directly into the HTML `<head>`.

## Excel Schema

The source spreadsheet should have these 15 columns (in order):

New, MTP, Program/Office, Subprogram, Project or Task, Health, Status, Project Name, Coordinator, Start Date, End Date, AGDT, Latest Update, Lookahead, XM-TR

## Tech Stack

- **Data processing** — Python 3, openpyxl
- **Frontend** — Vanilla JavaScript, CSS3 with custom properties
- **Typography** — Outfit (UI), IBM Plex Mono (data)
- **No build tools, no frameworks, no runtime dependencies**
