# Analysis Method

## Objective

Build an inspectable YouTuber grading framework for collaboration-risk review. The framework should help a reviewer compare creators by signals that are more risk-relevant than reach alone.

## Pipeline

| Stage | Public artifact | What it contributes |
| --- | --- | --- |
| Collection experiments | `01_youtube_data_collection.ipynb`, `03_video_metadata_collection.ipynb` | Historical YouTube metadata and comment collection logic. |
| Quality checks | `04_data_quality_check.ipynb` | Missing-data and consistency checks before feature engineering. |
| Comment preprocessing | `05_comment_labeling_preprocess.ipynb` | Labeled comment preparation for sentiment modeling. |
| Sentiment modeling | `06_sentiment_lstm_modeling.ipynb` | Korean comment preprocessing, text vectorization, LSTM experiment, classification metrics, and sentiment-score export. |
| Loyalty signal | `07_comment_loyalty_score.ipynb` | Repeated or loyal audience participation proxy. |
| Upload stability | `08_upload_interval_feature.ipynb` | Average upload interval and cadence-stability signal. |
| Feature merge | `09_feature_merge.ipynb` | Combines monthly creator-level features into the scoring surface. |
| Score design | `10_grade_threshold_design.ipynb`, `11_grade_assignment.ipynb` | Designs score thresholds and calculates channel-scale/loyalty components. |
| Historical prediction experiments | `notebooks/archive/12_grade_prediction_ml.ipynb`, `notebooks/archive/13_grade_prediction_deep_learning.ipynb` | Preserved exploration only; not used as public performance evidence. |
| Visualization | `14_grade_score_visualization.ipynb` | Inspects score and grade trends by creator. |

## Feature Design

The grading surface combines several evidence classes:

- Awareness: views, subscribers, or other public scale indicators.
- Growth: monthly movement in creator performance or subscriber-related indicators.
- Sentiment: comment text converted into a sentiment score with an LSTM experiment.
- Loyalty: recurring or concentrated audience response signals.
- Upload stability: channel별 영상을 월 단위로 정렬한 뒤 평균 업로드 간격과 영상 개수를 계산합니다. 평균 업로드 간격과 업로드가 없는 달이 연속되는 길이(`null_지속`)는 `10_grade_threshold_design.ipynb`의 업로드 안정성 등급 점수에 반영하며, 관련 feature 구현은 `08_upload_interval_feature.ipynb`에 남아 있습니다.

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

Score-design evidence is inspectable through:

- `notebooks/10_grade_threshold_design.ipynb` and `notebooks/11_grade_assignment.ipynb` for threshold and component-score logic,
- `notebooks/14_grade_score_visualization.ipynb` for trend inspection.
- `assets/final-presentation.pdf` for the actual final project presentation.

Dataset-derived tables and prediction outputs are intentionally not public. The notebooks communicate the historical approach, but they are not presented as executable proof of a particular score or performance value.

## Reproducibility Boundary

The public repo is designed for inspection, not full reproduction:

- You can install the review environment described in `requirements.txt`.
- You can inspect notebooks in numeric order with [notebook 안내](../notebooks/README.md).
- You should not expect end-to-end reproduction because raw YouTube comments, collection outputs, derived data tables, model weights, and the original runtime state are intentionally excluded.
- You should treat Selenium collection notebooks as historical experiments, not as a stable public data-ingestion interface.
- You should treat `notebooks/archive/` as historical exploration, not as model-performance evidence.

## Model and Risk Limitations

- The grade is a review aid, not a deterministic approval rule.
- The scoring framework depends on collection timing, YouTube platform behavior, and available public signals.
- Sentiment modeling can misclassify sarcasm, slang, mixed-language comments, and context-dependent reactions.
- The prediction experiments are prototype evidence for the grading framework, not a production monitoring system.
