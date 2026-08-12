# Project Summary

## One-line Summary

This project reframes influencer selection as a risk-management workflow and grades YouTube creators by combining audience scale, growth, comment sentiment, loyalty, and upload stability.

## Project Facts

| Item | Record |
| --- | --- |
| Competition | Samsung Fire & Marine Insurance X POSTECH, 2nd Data-Based Risk Management Competition |
| Period | August–November 2023 (approximately three months) |
| Team | Four-person team, 정규함수 |
| Outcome | Encouragement Award |
| Scope | Approximately 450,000 YouTube comments and channel/video metadata; raw and derived data are not public. |

## Problem

Follower count and average views are not enough for a brand or insurer evaluating creator partnerships. A high-reach channel can still expose a campaign to risk when:

- recent growth is slowing or volatile,
- comment sentiment is negative,
- loyal audience participation is weak,
- upload cadence is unstable,
- the channel's public indicators do not support repeated collaboration confidence.

The project turns those concerns into an inspectable scoring and grading framework for YouTubers.

## Role and Contribution Boundary

| Member | Responsibility |
| --- | --- |
| Park Minkyu | YouTube data analysis, upload-interval feature engineering, risk-signal flow, and public-portfolio documentation. |
| Ham Dahyun | Score-table integration, final grading, and grade-assignment logic. |
| Park Sojeong | Grade-threshold design and K-S/PSI suitability review. |
| Moon Changsu | Domain research, insurance-use scenarios, and final-presentation composition. |

This portfolio repo presents Park Minkyu's contribution through the artifacts that are public and reviewable here:

- YouTube data analysis and upload-interval feature engineering,
- risk-signal flow and reviewer-oriented notebook organization,
- public-safe documentation of data boundaries,
- explanation of model evidence, final-presentation sources, and limitations.

The original work was a team competition project. This repo does not claim sole authorship of the full team deliverable, and it does not publish raw or private materials needed for unrestricted reruns.

## Reviewer Path

1. Start with `README.md` for the public story and safety boundary.
2. Read `docs/analysis-method.md` for the technical pipeline.
3. Read `docs/data-dictionary.md` to understand the historical feature concepts and data boundary.
4. Inspect notebooks `06`, `10`, `11`, and `14` for the sentiment and grade-design flow.
5. Open `assets/final-presentation.pdf` for the actual final project presentation.

## Evidence Map

| Evidence | Public artifact |
| --- | --- |
| Risk-management framing | `README.md`, this file |
| Sentiment-model workflow | `notebooks/06_sentiment_lstm_modeling.ipynb` |
| Loyalty and upload-stability signals | `notebooks/07_comment_loyalty_score.ipynb`, `notebooks/08_upload_interval_feature.ipynb` |
| Feature integration | `notebooks/09_feature_merge.ipynb` |
| Grade thresholds and assignment | `notebooks/10_grade_threshold_design.ipynb`, `notebooks/11_grade_assignment.ipynb` |
| Historical prediction experiments | `notebooks/archive/` (not used as performance evidence) |
| Score and grade visualization | `notebooks/14_grade_score_visualization.ipynb` |
| Public scope and reproducibility boundary | `data/README.md`, `docs/public-safety.md`, `notebooks/README.md` |
| Final presentation result record | `assets/presentation/sentiment-evaluation-slide.png`, `assets/presentation/grade-validation-slide.png` |

## Public-safe Artifacts

The repo keeps explanatory docs, notebooks, requirements, and an actual final presentation PDF. Raw data, derived data tables, local execution files, model weights, text-vectorizer artifacts, browser drivers, and large intermediate exports are outside the public portfolio boundary.

## Limitations

- The project is a prototype scoring framework, not a deployed risk product.
- The grade should be interpreted as a review signal, not as an automated sponsorship decision.
- The public repo supports inspection and partial reproduction, but not full raw-data collection or model-training reproduction.
- Public docs avoid unsupported performance values because the raw training data and original runtime state are not fully included.
- Performance figures shown in README are explicitly attributed to the final presentation record, not a rerun of this public repository.
