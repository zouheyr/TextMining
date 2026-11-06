# TextMining

An R-based academic project focused on text mining and sentiment analysis of political speeches. The repository demonstrates how to preprocess raw text, build a document-term matrix, extract frequent terms, visualize word clouds, and score sentiment using lexicon-based approaches.

## Overview

This project was developed as a text-mining exercise in R and applies NLP techniques to political speech data, with a focus on public communication, emotion detection, and thematic analysis. It combines:

- document loading and preprocessing
- stopword removal and stemming
- word frequency analysis
- term association discovery
- sentiment and emotion classification
- output-generation in HTML, Word, and PDF formats

The repository includes a main analysis notebook, multiple generated outputs, and a small Plumber API example.

## Repository structure

```text
TextMining/
├── README.md
├── TextMining.Rproj
├── TP4-Zouheyr AYAS.Rproj
├── textMining.Rmd                 # Main R notebook for text-mining analysis
├── textMining.nb.html            # Rendered notebook output
├── textMining.docx               # Word export
├── TP4- Zouheyr AYAS.Rmd         # Academic assignment notebook
├── TP4- Zouheyr AYAS.pdf         # Project submission PDF
├── Bill Clinton.txt              # Main corpus (Bill Clinton speech text)
├── data/
│   ├── Bill Clinton.txt
│   └── texte.txt
├── TextMining_api/
│   └── plumber.R                 # Plumber API example
├── .gitignore
└── .Rhistory (not tracked)
```

## Tech stack

- Language: R
- IDE: RStudio
- Text mining: `tm`, `SnowballC`
- Visualization: `ggplot2`, `wordcloud`, `RColorBrewer`
- Sentiment analysis: `syuzhet`
- Reporting: R Markdown
- API: Plumber

## Data and analysis workflow

The notebooks follow a standard text-mining flow:

1. Load text from a file
2. Build a corpus with `tm::Corpus()`
3. Clean text by removing punctuation, numbers, stop words, and whitespace
4. Normalize to lowercase and stem words
5. Create a term-document matrix
6. Explore term frequency and associations
7. Generate word clouds and bar charts
8. Compute sentiment with `syuzhet`
9. Classify emotional categories with NRC lexicons

This is especially suited for exploring the tone and thematic structure of political speeches.

## Getting started

### Prerequisites

- R 4.0 or newer
- RStudio (recommended)
- Internet access to install packages

### Install dependencies

Open R or RStudio and run:

```r
install.packages(c(
  "tm",
  "SnowballC",
  "wordcloud",
  "RColorBrewer",
  "syuzhet",
  "ggplot2",
  "dplyr",
  "stringr",
  "plumber"
))
```

### Open the project

```bash
git clone https://github.com/zouheyr/TextMining.git
cd TextMining
```

Then open `TextMining.Rproj` in RStudio.

## Running the analysis

The main notebook is:

- `textMining.Rmd`

To render it from R:

```r
rmarkdown::render("textMining.Rmd")
```

The notebook uses a file picker (`file.choose()`) to select the text source, so it is best run interactively in RStudio.

## API

The repository contains a small Plumber API in `TextMining_api/plumber.R`.

### Run the API

```r
library(plumber)
pr <- plumb("TextMining_api/plumber.R")
pr$run(port = 8000)
```

### Available routes in the current implementation

```text
GET  /echo    Returns the input message
GET  /plot    Returns a histogram image
POST /sum     Adds two numeric values
```

Note: The README originally described additional analytics endpoints such as `/analyze`, `/sentiment`, and `/wordcloud`; those routes are not currently implemented in the checked-in `plumber.R` file. The repository is currently better understood as an academic analysis project and a simple API example than as a production-ready text-analysis service.

## Example of the project goals

The analysis focuses on:

- identifying the most frequent terms in speeches
- visualizing dominant vocabulary with word clouds
- scoring positive/negative tone and emotional categories
- comparing the language patterns of major political discourse

The included corpus and notebooks demonstrate text mining from a political communication perspective, which is useful for coursework, exploratory analysis, and practice with NLP workflows in R.

## Outputs included

This repository already contains several rendered outputs:

- `textMining.nb.html`
- `textMining.docx`
- `TP4- Zouheyr AYAS.pdf`

These outputs represent snapshots of the project analysis and can be used for reporting or academic submission.

## Notes

This project is primarily an academic and educational repository rather than a packaged library or full application. It is best used as a reference for:

- R-based text processing
- sentiment lexicon analysis
- notebook-driven exploratory data analysis
- political text mining examples

## License and author

This project is part of an academic assignment and is associated with Zouheyr AYAS at UQTR (Université du Québec à Trois-Rivières).

## Future improvements

Possible next steps for this project include:

- standardizing the project notebook structure
- converting repeated analysis code into reusable functions
- creating a proper `DESCRIPTION` or package setup
- implementing real sentiment and analysis endpoints in a robust Plumber API
- adding a cleaner `README` and reproducible setup script

---

If you want, I can also turn this into a more polished version in French, since the repository description and academic context appear to be in French.
