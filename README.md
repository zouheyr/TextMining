# 📝 TextMining — Text Exploration & Sentiment Analysis

> An R-based academic project for **text mining** and **sentiment analysis**,  
> applied to political speeches — developed as part of a Master’s program at **UQTR**  
> *(Université du Québec à Trois-Rivières)*.

-----

## 📌 Overview

This project implements a complete **text mining pipeline** in R, from raw text ingestion to
sentiment scoring and visualisation. It uses Bill Clinton’s political speeches as the primary
corpus to demonstrate key NLP techniques, and exposes core functionality through a lightweight
REST API.

-----

## 🗂️ Repository Structure

```
TextMining/
├── TextMining_api/          # REST API exposing text mining endpoints
├── data/                    # Raw and processed datasets
├── textMining.Rmd           # Main R Markdown analysis notebook
├── textMining.nb.html       # Rendered HTML output
├── textMining.docx          # Word document output
├── TP4- Zouheyr AYAS.Rmd   # Academic assignment version (TP4)
├── TP4- Zouheyr AYAS.pdf   # PDF report submission
├── Bill Clinton.txt         # Text corpus — Bill Clinton speeches
├── TextMining.Rproj         # RStudio project file
└── README.md
```

-----

## 🔧 Tech Stack

|Layer        |Tools / Libraries                                |
|-------------|-------------------------------------------------|
|Language     |R                                                |
|Text Mining  |`tm`, `tidytext`, `SnowballC`                    |
|Sentiment    |`syuzhet`, `tidytext` (NRC, AFINN, Bing lexicons)|
|Visualisation|`ggplot2`, `wordcloud`, `RColorBrewer`           |
|API          |R Plumber *(see API section below)*              |
|Reporting    |R Markdown → HTML / PDF / Word                   |

-----

## 🚀 Installation & How to Run

### Prerequisites

- R ≥ 4.0
- RStudio (recommended)

### 1. Clone the repository

```bash
git clone https://github.com/zouheyr/TextMining.git
cd TextMining
```

### 2. Install R dependencies

Open R or RStudio and run:

```r
install.packages(c(
  "tm", "tidytext", "SnowballC", "syuzhet",
  "ggplot2", "wordcloud", "RColorBrewer",
  "dplyr", "stringr", "plumber"
))
```

### 3. Run the analysis notebook

Open `TextMining.Rproj` in RStudio, then open and **Knit** `textMining.Rmd`.

```r
rmarkdown::render("textMining.Rmd")
```

-----

## 🌐 API Usage

The `TextMining_api/` folder contains a **Plumber REST API** that exposes text mining
functions programmatically.

### Start the API

```r
library(plumber)
pr <- plumb("TextMining_api/api.R")
pr$run(port = 8000)
```

### Endpoints

|Method|Endpoint    |Description                              |Parameters     |
|------|------------|-----------------------------------------|---------------|
|`POST`|`/analyze`  |Full text mining analysis on input text  |`text` (string)|
|`POST`|`/sentiment`|Returns sentiment scores (NRC/AFINN/Bing)|`text` (string)|
|`GET` |`/wordcloud`|Generates a word frequency word cloud    |`text` (string)|
|`GET` |`/health`   |API health check                         |—              |


> ⚠️ *Endpoints are indicative — refer to `TextMining_api/` source files for the exact routes.*

### Example Request

```bash
curl -X POST http://localhost:8000/sentiment \
  -H "Content-Type: application/json" \
  -d '{"text": "We must build a future of peace, hope, and shared prosperity."}'
```

```json
{
  "positive": 3,
  "negative": 0,
  "trust": 2,
  "anticipation": 1,
  "sentiment_score": 2.4
}
```

-----

## 📊 Key Analyses

- **Pre-processing** — tokenisation, lowercasing, stopword removal, stemming
- **Term Frequency & TF-IDF** — identify most significant terms in the corpus
- **Word Cloud** — visual representation of term frequency
- **Sentiment Analysis** — scoring with three lexicons:
  - `NRC` — emotion categories (joy, anger, fear, trust…)
  - `AFINN` — numeric sentiment score (−5 to +5)
  - `Bing` — binary positive / negative classification
- **Sentiment Over Time** — track emotional arc across a speech

-----

## 🎓 Academic Context

|Field     |Details                                         |
|----------|------------------------------------------------|
|University|Université du Québec à Trois-Rivières **(UQTR)**|
|Level     |Master’s program                                |
|Assignment|TP4 — Text Mining & Sentiment Analysis          |
|Author    |Zouheyr AYAS                                    |

-----

## 👤 Author

**Zouheyr AYAS**  
[![GitHub](https://img.shields.io/badge/GitHub-zouheyr-181717?logo=github)](https://github.com/zouheyr)

-----

## 📄 License

This project is for academic purposes. All rights reserved © Zouheyr AYAS — UQTR.
