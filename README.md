# Sentiment Analysis on Sample Client Feedback

## Objective
This project runs sentiment analysis on a set of mock client feedback comments to classify each one as positive, neutral, or negative, visualize the overall distribution, and flag the most negative comments so they can be prioritized for follow-up.

## Approach
The dataset consists of 27 mock client feedback comments written to reflect realistic themes a business would actually receive: product quality, customer support experience, delivery, pricing, and usability. The comments intentionally cover a natural spread of sentiment rather than an artificially even split.

Sentiment scoring was done using VADER (Valence Aware Dictionary and sEntiment Reasoner), a lexicon and rule-based sentiment tool built specifically for short, informal text such as reviews and social media comments. VADER was chosen over TextBlob because it handles punctuation emphasis, capitalization, and intensifying words more reliably for this kind of short-form feedback, and it requires no model training or downloads.

Each comment receives a compound score between -1 (most negative) and +1 (most positive), which is then mapped to a category:

- Positive: compound score of 0.05 or higher
- Negative: compound score of -0.05 or lower
- Neutral: anything in between

## Steps performed
1. Compiled 27 sample client feedback comments.
2. Ran each comment through VADER's sentiment analyzer to get positive, neutral, negative, and compound scores.
3. Classified each comment and summarized the distribution in a bar chart.
4. Sorted comments by compound score and flagged the 3 most negative for follow-up.
5. Exported the full results and the flagged comments to CSV files for easy sharing.

## Results
Out of 27 comments analyzed:
- 15 were classified as Positive
- 10 were classified as Negative
- 2 were classified as Neutral

See `sentiment_distribution_chart.png` for the visual breakdown.

## Top 3 flagged comments for follow-up
1. "Very disappointed with the lack of communication during the delay."
2. "Terrible experience, the product broke after just two days of use."
3. "Worst experience ever, I want a refund immediately."

These were selected because they carry the lowest (most negative) compound sentiment scores, indicating the strongest expressed dissatisfaction. In a real business setting, these would be the first tickets a support or account management team follows up on.

## Files included
- `sentiment_analysis.ipynb` — full notebook with all code, explanations, and outputs
- `sentiment_distribution_chart.png` — bar chart of sentiment distribution
- `sentiment_analysis_results.csv` — full scored dataset
- `flagged_negative_comments.csv` — the 3 flagged comments with scores

## How to run
Open `sentiment_analysis.ipynb` in Google Colab or Jupyter and run all cells top to bottom. The only dependency, `vaderSentiment`, installs automatically in the first cell.

## Tools used
Python, pandas, matplotlib, VADER (vaderSentiment library)
