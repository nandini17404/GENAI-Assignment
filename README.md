# ✦ ReviewSense — AI-Powered Product Review Sentiment Analyzer

**Transforming Customer Feedback into Actionable Business Insights**

ReviewSense is an AI-powered web application that helps businesses analyze customer reviews, classify sentiments, visualize feedback trends, and identify recurring product complaints using Google Gemini.

Built with **Python, Streamlit, Pandas, Plotly, and the Google Gemini API**, ReviewSense transforms large volumes of unstructured customer feedback into meaningful insights through an interactive analytics dashboard.

---

## 📌 Problem Statement

E-commerce platforms receive thousands of customer reviews every day. Manually reading, categorizing, and interpreting these reviews is time-consuming and inefficient.

Businesses often struggle to identify customer satisfaction levels, recurring complaints, and areas requiring improvement.

ReviewSense addresses these challenges by automating sentiment classification and generating AI-powered complaint summaries.

## 🎯 Project Objectives

- Automatically classify customer reviews as **Positive, Negative, or Neutral**.
- Process large review datasets using efficient LLM batching.
- Visualize sentiment distributions through interactive charts.
- Identify recurring customer complaints using Generative AI.
- Generate actionable recommendations for product and service improvements.
- Provide a user-friendly dashboard for exploring and exporting analyzed reviews.

## ✨ Key Features

### 1. CSV Review Upload
Upload customer review datasets in CSV format. The application automatically detects potential review-text columns and allows users to select the appropriate column.

### 2. AI-Powered Sentiment Classification
Uses the Google Gemini API to classify each review into three categories:

- **Positive:** Expresses customer satisfaction.
- **Negative:** Indicates dissatisfaction or complaints.
- **Neutral:** Contains balanced, mixed, or non-opinionated feedback.

### 3. Batch Processing
Reviews are divided into batches of **20 reviews per LLM request**, reducing the number of API calls compared with analyzing each review individually.

### 4. Interactive Analytics Dashboard
The dashboard displays:

- Total reviews analyzed
- Positive reviews
- Negative reviews
- Neutral reviews
- Sentiment distribution donut chart
- Sentiment comparison bar chart

### 5. AI Complaint Summarization
Negative reviews are analyzed using Gemini to identify common customer complaints, recurring themes, and recommended improvements.

### 6. Review Explorer
Users can search, filter, and examine classified reviews based on sentiment categories and review content.

### 7. Export Results
Download classified reviews as CSV files and AI-generated complaint insights as JSON.

### 8. Reliable API Processing
Includes retry handling for temporary Gemini API failures, model availability checks, and session-based batch checkpointing.

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core application development |
| Streamlit | Interactive web interface |
| Pandas | Data cleaning and CSV processing |
| Google Gemini API | Sentiment classification and complaint summarization |
| Google GenAI SDK | Gemini API integration |
| Plotly | Interactive charts and visualizations |
| python-dotenv | Environment variable management |

## 🏗️ System Architecture

```text
                  CUSTOMER
                     |
                     v
              STREAMLIT WEBSITE
                     |
                     v
               UPLOAD CSV FILE
                     |
                     v
           DATA PREPROCESSING
                (Pandas)
                     |
                     v
           BATCH REVIEWS (20)
                     |
                     v
              GEMINI LLM API
                     |
                     v
          SENTIMENT CLASSIFICATION
                     |
          +----------+----------+
          |          |          |
       POSITIVE   NEGATIVE    NEUTRAL
          |          |          |
          +----------+----------+
                     |
                     v
             ANALYTICS DASHBOARD
               (Plotly Charts)
                     |
                     v
             NEGATIVE REVIEWS
                     |
                     v
              GEMINI LLM API
                     |
                     v
          COMMON COMPLAINT SUMMARY
                     |
                     v
            BUSINESS RECOMMENDATIONS
                     |
                     v
                EXPORT RESULTS
```

## 📂 Project Structure

```text
ReviewSense/
│
├── app.py
├── requirements.txt
├── sample_reviews.csv
├── .env.example
└── README.md
```

## ⚙️ Installation and Setup

### Step 1: Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/ReviewSense.git
cd ReviewSense
```

Replace `YOUR_USERNAME` with your GitHub username.

### Step 2: Install Dependencies

Ensure Python 3.10 or later is installed.

```bash
python -m pip install -r requirements.txt
```

### Step 3: Configure Gemini API

Generate an API key from [Google AI Studio](https://aistudio.google.com/apikey).

Create a `.env` file in the project directory:

```env
GEMINI_API_KEY=your_api_key_here
GEMINI_MODEL=gemini-3.8-flash
```

Replace the model value if it is unavailable to your API key.

**Security:** Never commit your `.env` file or API key to GitHub.

### Step 4: Run the Application

```bash
python -m streamlit run app.py
```

Open the application at:

`http://localhost:8501`

## 📊 Sample Dataset

The application includes `sample_reviews.csv` for demonstration.

Example:

| Review | Expected Sentiment |
|---|---|
| Excellent product quality and fast delivery! | Positive |
| The package arrived damaged and late. | Negative |
| The product is average for its price. | Neutral |
| Very satisfied with the purchase. | Positive |
| Customer support was unhelpful. | Negative |

These are illustrative labels; actual model classifications may differ.

## 🔄 Application Workflow

**Step 1 — Upload:** The user uploads a CSV containing product reviews.

**Step 2 — Preprocess:** Pandas loads the dataset, removes missing or empty review entries, and prepares the review text.

**Step 3 — Batch:** The application divides reviews into batches of 20.

**Step 4 — Classify:** Gemini returns structured JSON containing a sentiment label for each review.

**Step 5 — Validate:** The application validates returned review IDs and sentiment categories.

**Step 6 — Visualize:** Plotly generates sentiment distribution and comparison charts.

**Step 7 — Summarize:** Negative reviews are sent to Gemini for complaint analysis.

**Step 8 — Export:** Users download classified reviews and AI-generated insights.

## 📈 Sample Output

For an illustrative dataset containing 25 customer reviews:

| Sentiment | Reviews | Percentage |
|---|---:|---:|
| Positive | 16 | 64% |
| Negative | 6 | 24% |
| Neutral | 3 | 12% |
| **Total** | **25** | **100%** |

### Example AI-Generated Complaint Summary

> Negative feedback primarily highlights delayed deliveries, damaged packaging, and difficulties with refunds. Businesses should improve shipping reliability, packaging quality, and refund processing.

**Note:** These are demonstration results, not verified output from a live Gemini analysis.

## 🧠 Core Concepts

**Natural Language Processing (NLP):** Interprets and categorizes human-written customer feedback.

**Large Language Models (LLMs):** Gemini analyzes review context and generates structured sentiment classifications.

**Prompt Engineering:** Classification prompts enforce consistent labels and structured JSON responses.

**Batch Processing:** Groups multiple reviews into one request for efficient LLM usage.

**Generative AI Summarization:** Converts negative customer feedback into concise complaint themes and recommendations.

**Data Visualization:** Presents sentiment patterns through interactive charts.

## ⚠️ Limitations

- Sentiment classification accuracy depends on the selected LLM.
- Sarcasm, mixed sentiment, and ambiguous language can affect results.
- Gemini API rate limits and temporary server outages may interrupt processing.
- Large negative-review datasets may require sampling or hierarchical summarization.
- AI-generated recommendations should be verified against original customer reviews.
- API usage may incur costs depending on the selected model and usage tier.

## 🚀 Future Enhancements

- Multilingual customer review analysis
- Aspect-based sentiment analysis
- Product-wise sentiment comparison
- Trend analysis over time
- Automatic complaint prioritization
- PDF report generation
- Topic clustering and keyword extraction
- Integration with e-commerce review platforms

## 🎓 Applications

ReviewSense can support:

- E-commerce businesses
- Retail product analysis
- Customer experience teams
- Product quality monitoring
- Brand reputation analysis
- Customer feedback management

## 📝 Conclusion

ReviewSense demonstrates how **Generative AI, Natural Language Processing, and Data Analytics** can work together to transform unstructured customer reviews into actionable business intelligence.

By combining automated sentiment classification, interactive visualizations, and AI-generated complaint summaries, the system helps businesses understand customer feedback more efficiently and identify opportunities for continuous improvement.

---

**ReviewSense | AI-Powered Customer Intelligence**

*Built using Python, Streamlit, Google Gemini API, Pandas, and Plotly.*
