# A-Quantitative-Greenwashing-Index-for-the-Luxury-Sector
Built a Greenwashing Index to audit luxury fashion's "Talk-Walk" gap. Analyzing 21,150 texts via entity resolution &amp; LDA modeling on 32 brands reveals "Narrative Decoupling." Objective ESG scores show almost 0 correlation with media greenwashing risk, proving corporate reporting &amp; public environmental narratives act as entirely independent systems.

## Data Reproducibility
Due to strict licensing agreements with ProQuest TDM Studio, the raw dataset of 21,150 XML documents cannot be made public. Therefore, the Google Colab Notebook (Data Extraction) provided in this repository is **read-only** and intended for methodological and code-quality review. 

Visualizations, statistical outputs, and the final Greenwashing Index results have been extracted and are available in the [Full Project PDF](https://github.com/MuhammadAjlal2004/A-Quantitative-Greenwashing-Index-for-the-Luxury-Sector/blob/main/MuhammadAjlal_SWFullPDF.pdf). The code for this is also reproducible through the Google Colab Notebook (Data Analysis).

## Methodological Pipeline

### 1. Data Extraction & XML Parsing
- Extracted a corpus of over 6,000 relevant trade journal and wire feed articles from **ProQuest TDM Studio**.
- Developed a custom Python pipeline utilizing `BeautifulSoup` and the `xml` parser to strip HTML/XML tags and extract raw text from nested directories into a unified dataframe.

### 2. Parent-Child Entity Resolution
- Addressed the corporate consolidation challenge (where media also scrutinizes subsidiaries, but ESG scores only apply to holding companies).
- Coded a hierarchical dictionary mapping over 100 specific consumer-facing luxury search terms (e.g., Dior, Gucci) to their 32 distinct parent holding companies (e.g., LVMH, Kering) to ensure accurate cross-referencing with S&P Global CSA scores.

### 3. Context-Window Latent Dirichlet Allocation (LDA)
- Overcame the "Omnibus Document" problem (daily digests burying relevant data among noise like "Russian-Ukraine conflict" or "horse racing").
- Engineered the script to slice documents into individual sentences, feeding the LDA algorithm *only* sentences containing greenwashing keywords.
- Applied hyper-refined stopword filtering using `scikit-learn` and regular expressions to strip numerical dates, publisher boilerplate, and legal jargon.

## Key Findings
The statistical analysis revealed a profound decoupling between objective corporate disclosures and public narratives:
- **Zero Correlation:** Both the Pearson and Spearman Rank correlation between objective S&P Global CSA Scores and media greenwashing risk are near-zero.
- **Lacking Statistical Pattern:** Visualizations like the slope chart and quadrant map lack any statistical pattern.
