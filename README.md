# People Extraction Flow

## Overview

A sustainability and ESG leadership contact extraction pipeline. It reads company data from a Google Sheet (Carbon Unbound project), extracts company website domains, builds Apollo people search queries targeting sustainability/ESG/climate/carbon leadership titles (CSO, VP Sustainability, Head of ESG, Director of Climate, etc.) across US and European locations, and saves the extracted contacts to a separate "people" tab. The workflow processes companies in batches of 15 with delays to manage API rate limits.

## How It Works

```
Manual Trigger -> Google Sheets (read companies) -> Loop in batches of 15 -> Build Apollo search body (41 sustainability titles + company domains + US/Europe filter) -> Apollo People Search -> Extract people data -> Clean contacts (name, title, LinkedIn, company, website) -> Save to Google Sheet (people tab)
```

### Workflow Diagram

```mermaid
flowchart TD
    A["Manual Trigger"] --> B["Google Sheets\nRead Companies"]
    B --> C["Loop\nBatches of 15"]
    C --> D["Code\nBuild Apollo Search\n(41 ESG/Sustainability Titles)"]
    D --> E["Apollo\nPeople Search"]
    E --> F["Clean\nContact Data"]
    F --> G["Google Sheets\nSave to People Tab"]
    G --> C

    style A fill:#1B3A4B,color:#fff
    style B fill:#2C5F7C,color:#fff
    style D fill:#3D5A80,color:#fff
    style E fill:#4A6D7C,color:#fff
    style G fill:#274C36,color:#fff
```

## Integrations

- **Google Sheets** - Company data source and contact output
- **Apollo** - People search targeting sustainability/ESG leadership

## Setup

1. Import `people_extarction_flow.json` into your n8n instance.
2. Configure Google Sheets and Apollo credentials.
3. Update the Google Sheet document ID.
4. Execute manually.
