
# 🏏 **T20 Cricket World Cup Analytics**

A full-stack, end-to-end data pipeline that automates the collection of live match data, processes it into star-schema tables, and creates interactive Power BI dashboards for uncovering insights on player performance and selecting the **ultimate T20 XI**.

---

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

---

## Project Overview

**T20 Cricket World Cup Analytics** aims to take cricket analytics a step further by not only exploring the data in Jupyter notebooks but by automating the collection, transformation, and visualization of key metrics for team performance, player evaluation, and match outcomes.

The pipeline scrapes live match data from **ESPN Cricinfo** and **ICC** websites, processes it into structured, star-schema tables, and then visualizes the insights through Power BI dashboards. Whether you're a coach, analyst, or cricket enthusiast, this tool helps answer questions like:

* Which bowlers are most effective in the death overs?
* Who are the most reliable middle-order anchors?
* What is the win probability for a hypothetical XI selected with specific constraints?

The process is fully automated and can be replicated for any T20 tournament.

---

## Features

| Category                   | Highlight                                                                                                                  |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| 🔎 **Web Scraping**        | Four Node scripts that pull batting, bowling, match results, and player metadata from **ICC** and **ESPN Cricinfo**        |
| 🧹 **Data Cleaning**       | Jupyter notebook (`t20_data_preprocessing.ipynb`) to clean and preprocess data, filling missing values and creating schema |
| 🗄 **Star-schema Tables**  | Generates four key star-schema tables: `dim_players`, `dim_match_summary`, `fact_batting_summary`, `fact_bowling_summary`  |
| 📊 **Power BI Dashboards** | Three fully interactive Power BI files for analyzing player performance, selecting teams, and more                         |
| 🧑‍💻 **Code-Free Tips**   | PDF guides on Power Query, dashboard layout, and DAX best practices for easy Power BI integration                          |
| 🏷 **Stand-Alone Assets**  | Excel workbook with all DAX measures and calculated columns for easy copy-paste into other Power BI projects               |
| 🚀 **Extensibility**       | Modular scripts that can be easily adapted for future tournaments by modifying only the source URLs                        |

---

## Folder Structure

```
data_analytics/
│
├── web_scrapping_codes/     # Node.js scripts for data scraping (*.js)
├── t20_json_files/          # Raw API responses (JSON)
├── t20_csv_files/           # Transformed star-schema tables (CSV format)
│   ├── dim_players.csv
│   ├── dim_match_summary.csv
│   ├── fact_batting_summary.csv
│   └── fact_bowling_summary.csv
│
├── t20_data_preprocessing.ipynb  # Jupyter notebook for data preprocessing
├── *.pbix                    # Power BI Dashboard files
├── DAX Measures and Calculated columns.xlsx  # Excel file with DAX formulas
└── docs/                     # Documentation (PDF, PPTs)
```

---

## Quick Start

To get started with this project, follow these steps:

### 1. Clone the repository

```bash
git clone https://github.com/puli-pro/data_analytics.git
cd data_analytics
```

### 2. Scrape the latest tournament data

Navigate to the `web_scrapping_codes` directory and install dependencies:

```bash
cd web_scrapping_codes
npm install  # Installs dependencies like axios, cheerio, etc.
```

Run the Node.js scripts to scrape match results, batting, bowling, and player data:

```bash
node t20_wc_match_results.js
node t20_wc_batting_summary.js
node t20_wc_bowling_summary.js
node t20_wc_player_info.js
```

### 3. Transform the data into analytics-ready tables

Install Python dependencies and run the preprocessing notebook:

```bash
cd ..
pip install -r requirements.txt  # Install pandas, numpy, jupyter
jupyter notebook t20_data_preprocessing.ipynb  # Executes all cells and generates CSVs
```

### 4. Visualize in Power BI

Open any of the `.pbix` files in **Power BI Desktop**, and click ‘Refresh’ to load the latest data. If you don’t have Power BI Desktop installed, you can publish the PBIX file to Power BI Service for cloud access.

---

## Detailed Usage

### 1️⃣ **Data Collection**

The Node.js scripts rely on **Node 18+** and Axios/Cheerio for web scraping. You can change the URLs in the scripts to collect data from other tournaments or seasons.

### 2️⃣ **Data Preparation**

The notebook `t20_data_preprocessing.ipynb` performs the following operations:

* Flattens nested JSON data.
* Aligns the schema to ensure consistency.
* Generates primary keys for joining tables (e.g., `match_id`).
* Cleans up anomalies in the `dismissal` column and string artifacts.
* Exports the data into four core tables in CSV format for further analysis.

### 3️⃣ **Analytics & Dashboarding**

The Power BI dashboards (`Stage-1.pbix`, `Stage-2.pbix`, and `Stage-3.pbix`) allow you to:

* Evaluate player performance based on role-specific KPIs (e.g., openers, finishers).
* Use slicers to filter data and test various team selections.
* Visualize player career stats and match performances.

### 4️⃣ **Extending for New Tournaments**

To add a new tournament:

1. Drop fresh JSON files into the `t20_json_files/` directory.
2. Adjust paths in the preprocessing notebook.
3. Refresh the Power BI dashboard to visualize the new data.

No changes are needed in the DAX calculations or Power BI queries.

---

## Tech Stack

| Layer                   | Technology                          |
| ----------------------- | ----------------------------------- |
| **Data Ingestion**      | Node.js, Axios, Cheerio             |
| **Data Transformation** | Python 3, Pandas, Jupyter Notebooks |
| **Storage**             | Flat files (JSON → CSV)             |
| **Semantic Modeling**   | Power BI, DAX                       |
| **Visualization**       | Power BI Desktop, Power BI Service  |

---

## Contributing

1. **Fork** the repository and create a new feature branch (e.g., `feat/your-feature`).
2. Ensure your code follows the existing code style (ESLint for JavaScript, Black for Python).
3. Commit with clear and descriptive messages.
4. Submit a **Pull Request** (PR) to merge your changes into the **main** branch. Include screenshots or GIFs for UI changes (e.g., Power BI dashboards).

---

## Roadmap

* ☑️ **Current**: 2022 T20 World Cup Dashboards
* ⏳ **Next**: Automate daily data refresh using GitHub Actions
* ⏳ **Future**: Develop a Streamlit app for quick player comparisons
* ⏳ **Stretch**: Auto-publish Power BI reports to a public workspace

---

## License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for more details.

---

## Support--

* **Issues**: Please report any bugs or issues via [GitHub Issues](https://github.com/puli-pro/data_analytics/issues)
* **Email**: [pulipavan696@gmail.com](mailto:pulipavan696@gmail.com)
* **LinkedIn**: [Solige Pullaiah](https://www.linkedin.com/in/solige-pullaiah-478462270/)

---

## Acknowledgements

* Data sources: **ICC** and **ESPN Cricinfo**.
---

*Made with ❤️ and a deep love for cricket!*

---


