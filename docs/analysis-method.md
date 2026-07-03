# Analysis Method

## Objective

Build an inspectable YouTuber grading framework for collaboration-risk review. The framework should help a reviewer compare creators by signals that are more risk-relevant than reach alone.

## Pipeline

| Stage | Public artifact | What it contributes |
| --- | --- | --- |
| Collection experiments | `01_youtube_data_collection.ipynb`, `02_legacy_youtube_crawling_selenium.ipynb`, `03_video_metadata_collection.ipynb` | Historical YouTube metadata and comment collection logic. |
| Quality checks | `04_data_quality_check.ipynb` | Missing-data and consistency checks before feature engineering. |
| Comment preprocessing | `05_comment_labeling_preprocess.ipynb` | Labeled comment preparation for sentiment modeling. |
| Sentiment modeling | `06_sentiment_lstm_modeling.ipynb` | Korean comment preprocessing, text vectorization, LSTM experiment, classification metrics, and sentiment-score export. |
| Loyalty signal | `07_comment_loyalty_score.ipynb` | Repeated or loyal audience participation proxy. |
| Upload stability | `08_upload_interval_feature.ipynb` | Average upload interval and cadence-stability signal. |
| Feature merge | `09_feature_merge.ipynb` | Combines monthly creator-level features into the scoring surface. |
| Grade design | `10_grade_threshold_design.ipynb`, `11_grade_assignment.ipynb` | Translates score components into grades. |
| Prediction experiments | `12_grade_prediction_ml.ipynb`, `13_grade_prediction_deep_learning.ipynb` | Tests whether engineered feature histories can predict grade groups. |
| Visualization | `14_grade_score_visualization.ipynb` | Inspects score and grade trends by creator. |

## Feature Design

The grading surface combines several evidence classes:

- Awareness: views, subscribers, or other public scale indicators.
- Growth: monthly movement in creator performance or subscriber-related indicators.
- Sentiment: comment text converted into a sentiment score with an LSTM experiment.
- Loyalty: recurring or concentrated audience response signals.
- Upload stability: cadence and gap patterns that affect campaign reliability.

The important modeling choice is that grade evidence comes from multiple signals. A creator should not be considered low-risk only because one metric is strong.

## Sentiment-model Evidence

The public sentiment-model notebook includes:

- labeled comment preprocessing,
- label conversion,
- rare-word and length handling,
- sequence preparation,
- LSTM model training,
- metric calculation using accuracy, recall, precision, F1, AUC, classification report, and confusion matrix code,
- weighted sentiment-score export that accounts for comment like counts.

The repo documents the existence of those metric calculations but does not promote a specific metric value as portfolio evidence because raw comments, local model files, and the original runtime state are intentionally excluded.

## Grade Evidence

Grade evidence is visible through:

- `data/processed/raw_data_score.csv` for score construction context,
- `data/processed/final_all_data.xlsx` for integrated public features,
- `data/processed/등급_예측.xlsx` for grade-prediction outputs,
- `notebooks/10_grade_threshold_design.ipynb` and `notebooks/11_grade_assignment.ipynb` for threshold and assignment logic,
- `notebooks/14_grade_score_visualization.ipynb` for trend inspection.

## Reproducibility Boundary

The public repo is designed for inspection and partial reproduction:

- You can install dependencies from `requirements.txt`.
- You can inspect notebooks in numeric order.
- You can inspect public processed outputs in `data/processed/`.
- You should not expect full end-to-end reproduction from raw YouTube comments because those raw files are intentionally excluded.
- You should treat Selenium collection notebooks as historical experiments, not as a stable public data-ingestion interface.

## Model and Risk Limitations

- The grade is a review aid, not a deterministic approval rule.
- The scoring framework depends on collection timing, YouTube platform behavior, and available public signals.
- Public processed data cannot fully represent raw comment context.
- Sentiment modeling can misclassify sarcasm, slang, mixed-language comments, and context-dependent reactions.
- The prediction experiments are prototype evidence for the grading framework, not a production monitoring system.
