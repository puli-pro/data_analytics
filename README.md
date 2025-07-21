# 🏏 T20 Cricket World Cup Analytics

A full stack, end-to-end pipeline that scrapes live match data, cleans and models it into star-schema tables, and powers interactive Power BI dashboards for uncovering player insights and selecting the **ultimate T20 XI**.

## 📚 Table of Contents
1. [Project Overview](#project-overview)
2. [Features](#features)
3. [Folder Structure](#folder-structure)
4. [Quick Start](#quick-start)
5. [Detailed Usage](#detailed-usage)
6. [Tech Stack](#tech-stack)
7. [Contributing](#contributing)
8. [Roadmap](#roadmap)
9. [License](#license)
10. [Support](#support)
11. [Acknowledgements](#acknowledgements)

## Project Overview
Cricket analytics projects often stop at notebook-level exploration. **T20 Cricket World Cup Analytics** goes further—automating data collection, producing clean fact/dimension tables, and shipping polished dashboards that help coaches or fans answer questions such as:

* Which bowlers concede the fewest runs in the death overs?  
* Who are the most reliable middle-order anchors?  
* What is the win probability for a hypothetical XI chosen on specific constraints?

Data is harvested with simple Node scripts, transformed in Python, and visualised in Power BI. The result is a reproducible workflow you can replicate for any cricket tournament.

## Features
| Category | Highlight |
|----------|-----------|
| 🔎 **Web scraping** | Four Node scripts pull batting, bowling, match results and player metadata directly from ICC/ESPNcricinfo pages [1] |
| 🧹 **Data cleaning** | Jupyter notebook `t20_data_preprocessing.ipynb` handles missing values, joins, schema creation and exports tidy CSVs |
| 🗄 **Star-schema tables** | -  `dim_players`, `dim_match_summary`  -  `fact_batting_summary`, `fact_bowling_summary` |
| 📊 **Dashboards** | Three `.pbix` files with DAX-powered KPIs, slicers and “Best 11” team selector |
| 🧑‍💻 **Code-free tips** | PDF slide-decks on parameter scoping, dashboard layout and Power Query best practices |
| 🏷 **Stand-alone assets** | Excel workbook of all DAX measures for quick copy-paste |
| 🚀 **Extensible** | Modular scripts → slot in new tournaments by changing only the source URLs |

## Folder Structure
```
data_analytics/
│
├── web_scrapping_codes/     # NodeJS scrapers (*.js)
├── t20_json_files/          # Raw API responses
├── t20_csv_files/           # Modelled star-schema tables
│   ├── dim_players.csv
│   ├── dim_match_summary.csv
│   ├── fact_batting_summary.csv
│   └── fact_bowling_summary.csv
│
├── t20_data_preprocessing.ipynb
├── *.pbix                   # Power BI dashboards
├── DAX Measures and Calculated columns.xlsx
└── docs/                    # PDFs, PPT mock-ups
```

## Quick Start
```bash
# 1. Clone
git clone https://github.com/puli-pro/data_analytics.git
cd data_analytics

# 2. Scrape latest tournament data
cd web_scrapping_codes
npm install           # installs axios / cheerio etc.
node t20_wc_match_results.js
node t20_wc_batting_summary.js
node t20_wc_bowling_summary.js
node t20_wc_player_info.js

# 3. Transform to analytics-ready tables
cd ..
pip install -r requirements.txt   # pandas, numpy, jupyter
jupyter notebook t20_data_preprocessing.ipynb
# executes all cells → writes CSVs to t20_csv_files/

# 4. Visualise
# Open any *.pbix file with Power BI Desktop and click 'Refresh'
```

> **Tip:** No local Power BI? Publish the PBIX to Power BI Service and share the live dashboard link.

## Detailed Usage

### 1 ️⃣ Data Collection  
Scripts rely on **Node 18+**. URLs are defined at the top of each file; change them to ingest different seasons.

### 2 ️⃣ Data Preparation  
The notebook performs:
* JSON flattening, schema alignment  
* Calculated `match_id` to enable table joins  
* Cleaning `dismissal` anomalies and string artefacts  
* Export to four core tables with consistent primary keys [1]

### 3 ️⃣ Analytics & Dashboarding  
Open `Stage-3.pbix` for the final “Best XI” report, featuring:
* Role-based ranking parameters (openers, finishers, pacers …)  
* What-if selectors to tune weightings  
* Tooltip pages with player career summary cards  

### 4 ️⃣ Extending  
Add a new tournament by dropping fresh JSON into `t20_json_files/`, adjusting notebook paths, and refreshing the dashboard—no DAX changes required.

## Tech Stack
| Layer | Technology |
|-------|------------|
| Data ingestion | Node.js, Axios/Cheerio |
| Transformation | Python 3, Pandas, Jupyter |
| Storage | Flat files (JSON → CSV) |
| Semantic model | Power BI, DAX |
| Visualisation | Power BI Desktop / Service |

## Contributing
1. Fork the repo and create a feature branch (`feat/`).  
2. Follow the existing code style (ESLint / Black).  
3. Commit descriptive messages, open a PR against **main**, and link any related issues.  
4. For dashboard tweaks, include a screenshot or GIF in the PR description.

## Roadmap
- ☑️ Current: 2022 T20 World Cup dashboards  
- ⏳ Next: Automate daily data refresh with GitHub Actions  
- ⏳ Future: Streamlit app for quick player comparisons  
- ⏳ Stretch: Auto-publishing to a public Power BI workspace

## License
Distributed under the **MIT License**—see [`LICENSE`](LICENSE) for details.

## Support
* **Issues:** [GitHub Issues](https://github.com/puli-pro/data_analytics/issues)  
* **Email:** `puli.pro.dev@gmail.com`  
* **LinkedIn:** Coming soon

## Acknowledgements
* Raw data courtesy of **ICC** & **ESPN Cricinfo**.  
* Dashboard inspiration from the CodeBasics “Best 11” challenge [1].  
* Thanks to the open-source cricket-analytics community for schema ideas.


Made with ❤️ and a lot of cricket fandom


[1] https://www.linkedin.com/in/sarat-dharmana
[2] https://github.com/puli-pro/data
[3] https://github.com/puli-pro/data_analytics
[4] https://github.com/puli-pro/data_analytics/blob/main/t20_data_preprocessing.ipynb
[5] https://github.com/puli-pro/data_analytics/tree/main/t20_csv_files
[6] https://github.com/puli-pro/data_analytics/tree/main/t20_json_files
[7] https://github.com/puli-pro/data_analytics/tree/main/web_scrapping_codes
[8] https://github.com/puli-pro/data_analytics/blob/main/Codebasics%20Cricket%20Best%2011.pbix
[9] https://github.com/puli
[10] https://www.scribd.com/document/836505746/Pre-Processing-techniques-ipynb-Colab
[11] https://github.com/VBS-03/T20-Cricket-World-Cup-Analysis
[12] https://www.scribd.com/document/872344193/Data-Preprocessing-for-Machine-Learning-in-Python
[13] https://www.linkedin.com/posts/sandeep-kolar-baburao_cricketanalytics-datascience-powerbi-activity-7199329943833436160-05gC
[14] https://in.linkedin.com/in/ankitha-1107-sr
[15] https://www.linkedin.com/pulse/detailed-preprocessing-process-machine-learning-python-leonardo-a
[16] https://www.kaggle.com/datasets/imrankhan17/t20matches
[17] https://github.com/manavmodi22/Preprocessing-for-Machine-Learning-in-Python/blob/main/data_preprocessing_chapter3_exercise.ipynb
[18] https://github.com/Musa70/Data-Preprocessing
[19] https://www.kaggle.com/code/mirajdobariya/preprocessing/log
[20] https://www.scribd.com/document/666089078/Copy-of-Data-preprocessing-tools-ipynb-Colaboratory
[21] https://github.com/manavmodi22/Preprocessing-for-Machine-Learning-in-Python/blob/main/data_preprocessing_chapter4_exercise.ipynb
[22] https://github.com/Snehomoy100/Data-PreProcessing-using-Python/blob/main/data_preprocessing_tools.ipynb
[23] https://github.com/arupbhunia/Data-Pre-processing/blob/master/Data_Preprocessing.ipynb
