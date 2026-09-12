# 🌐 Automated Twitter/X OSINT Scraping & Geopolitical Sentiment Intelligence
> **Bypassing Social Media API Paywalls to Mine 5,300+ Tweets on US–Iran International Conflict Discourse using Dual-Engine Scraping & NLP**

---

## 📌 Executive Summary

Following Twitter/X's transition to enterprise-tier API pricing ($100 to $5,000+/month), acquiring large-scale social intelligence for geopolitical risk analysis became economically prohibitive for academic and independent researchers. 

This project engineers an end-to-end **Open-Source Intelligence (OSINT)** data collection and text analytics framework. The pipeline captures, standardizes, and evaluates public discourse surrounding the US–Iran geopolitical escalation and World War III concerns. By combining **dual scraping architectures** (session-authenticated Selenium WebDriver and token-based Tweet-Harvest CLI), the system collected over **5,345 original English tweets** without incurring API fees.

The collected data then flows through an NLP preprocessing pipeline—featuring custom linguistic safeguards (preserving the entity "US" before case folding), WordNet POS-aware lemmatization, Bag-of-Words/Word Cloud lexical clustering, and **VADER Sentiment Analysis** to quantify civilian anxiety, economic concerns, and anti-war rhetoric.

---

## 📁 Project Architecture & File Structure

```
📁 atwitterX/
│
├── 📓 01_scraping_tweet_harvest.ipynb    ← Token-based CLI scraping engine (Tweet-Harvest)
├── 📓 02_scraping_selenium.ipynb         ← Dynamic browser automation engine (Selenium WebDriver)
├── 📓 03_nlp_sentiment_analysis.ipynb    ← Master Analytics: Preprocessing, BoW, WordCloud & VADER Sentiment
│
├── 📁 data/
│   ├── 📁 raw/                           ← Raw scraped datasets (5,345 records in datasetWW3.csv & batch files)
│   └── 📁 processed/                     ← Cleaned, normalized, and sentiment-scored dataset
│
├── 📄 requirements.txt                   ← Python dependencies
├── 📄 .gitignore                         ← Git security rules (ignoring tokens, cookies, caches)
└── 📄 README.md                          ← Project documentation & analytical report
```

---

## 🔍 Advanced Query Design

To capture high-relevance geopolitical discourse while filtering spam and automated retweets, the scrapers employ Boolean query operators:

```text
("world war" OR ww3 OR wwiii) (iran OR tehran) (america OR us OR usa OR washington) lang:en -filter:retweets
```

### Syntax Breakdown:
| Parameter | Function |
| :--- | :--- |
| `("world war" OR ww3 OR wwiii)` | Restricts collection to conflict escalation terminology |
| `(iran OR tehran)` | Targets the Iranian geopolitical sphere |
| `(america OR us OR usa OR washington)` | Targets the United States geopolitical sphere |
| `lang:en` | Filters for English-language discourse |
| `-filter:retweets` | Eliminates duplicated retweets, ensuring only original author posts |

---

## ⚙️ Dual-Engine Scraping Comparison

| Feature | Tweet-Harvest Engine (`01`) | Selenium WebDriver Engine (`02`) |
| :--- | :---: | :---: |
| **Primary Mechanism** | Chromium Headless + Session Auth Token | Real Browser DOM Traversal + Cookie Injection |
| **Speed & Throughput** | ⚡ High (~150–200 tweets/min) | ⏳ Moderate (~40–60 tweets/min) |
| **DOM Dependency** | Low (Internal API response intercept) | High (Virtual DOM scroll & element parsing) |
| **Authentication** | Single `auth_token` input | Session cookie `.pkl` or interactive login |
| **Best Use Case** | Rapid historical bulk collection | Real-time monitoring & resilient DOM fallback |

> 🔒 **Security Notice:** Both notebooks include interactive, non-echoing credential prompts (`getpass`) or environment variable detection, guaranteeing that private session tokens are never hardcoded or committed to version control.

---

## 📊 Analytics & NLP Pipeline (`03_nlp_sentiment_analysis.ipynb`)

### 1. Linguistic Preprocessing & Entity Safeguard
A recurring error in automated sentiment analysis of international politics is lowercase folding turning `"US"` (United States) into the pronoun `"us"`. This pipeline implements a contextual regex safeguard:
```python
# Safeguard 'US' as country before case-folding and stopword removal
text = re.sub(r'\bUS\b(?=\s+(military|government|forces|troops|sanctions|debt|policy))', '__UNITED_STATES__', text)
text = re.sub(r'\b(in|of|by|against|with|to)\s+US\b', r'\1 __UNITED_STATES__', text)
```

### 2. Lexical Topic Extraction
- **Noise Elimination:** URL elimination, @mention stripping, non-ASCII emoji cleaning, punctuation removal.
- **Stopwords & Lemmatization:** NLTK English stopwords pruned with domain preservation; WordNet lemmatizer standardizing plurals and verb inflections.
- **Top Discourse Themes:** Distinct clustering around `military expenditure`, `national debt`, `weapons`, `nuclear sanctions`, and `peace negotiations`.

### 3. VADER Sentiment Polarity
Using NLTK's Valence Aware Dictionary and sEntiment Reasoner (VADER), tweets are scored across compound polarity thresholds:
- **Negative Sentiment (~50%):** Dominated by fears of military escalation, civilian casualties, inflation, and government overspending on warfare.
- **Neutral Sentiment (~26%):** Breaking news reports, geopolitical updates, and factual diplomatic statements.
- **Positive Sentiment (~24%):** Anti-war advocacy, calls for diplomatic resolutions, and de-escalation optimism.

---

## 🚀 Quickstart & Reproducibility

### 1. Prerequisites
```bash
# Clone the repository
git clone https://github.com/username/atwitterX.git
cd atwitterX

# Install Python dependencies
pip install -r requirements.txt

# (Optional for Notebook 01) Ensure Node.js >= 18 is installed
node --version
```

### 2. Running the Pipeline
1. **Scraping Data:**
   - Open `01_scraping_tweet_harvest.ipynb` or `02_scraping_selenium.ipynb`.
   - Run the dedicated **Authentication Cell** and enter your `auth_token` when prompted.
   - Harvested data is automatically stored in `data/raw/`.
2. **Executing NLP & Sentiment Analysis:**
   - Open `03_nlp_sentiment_analysis.ipynb`.
   - Run all cells sequentially to reproduce data cleaning, topic modeling, word cloud generation, and sentiment scoring.
   - Clean tabular output is saved to `data/processed/clean_ww3_sentiment.csv`.

---

## ⚖️ Ethical Considerations & Data Governance
- **Compliance:** Data was gathered strictly from publicly accessible posts for research and educational purposes under fair use.
- **Privacy:** User IDs, avatars, and profile links are isolated; the final processed dataset focuses on linguistic text sentiment rather than individual identity profiling.
