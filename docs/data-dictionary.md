# Data Dictionary

## Public Data Boundary

The public repo keeps processed score, grade, and aggregate files that help a reviewer inspect the model evidence. It intentionally excludes raw comments, raw crawl outputs, model weights, text-vectorizer artifacts, browser drivers, caches, and large intermediate exports.

## Processed Files

| File | Public interpretation | Reviewer use |
| --- | --- | --- |
| `final_all_data.xlsx` | Integrated feature and score table. | Inspect the combined creator-level scoring surface. |
| `최종_유튜버_데이터.xlsx` | Final creator-level data table. | Understand which creators and high-level indicators were included. |
| `분석_유튜버_목록.csv` | Creator list used for analysis. | Check scope of analyzed creators. |
| `분석_유튜버_목록(제거ver).xlsx` | Filtered creator list. | Inspect excluded or cleaned creator scope. |
| `total_year_video_df.csv` | Annual video metadata aggregate. | Inspect video-performance context. |
| `월간_구독자_데이터.xlsx` | Monthly subscriber-related data. | Inspect growth or trend inputs. |
| `감성점수.csv` | Comment sentiment score by creator/month or equivalent grouping. | Inspect sentiment signal used in grading. |
| `충성도.csv` | Loyalty score or recurring-audience proxy. | Inspect audience-stability signal. |
| `인지도부문.csv` | Awareness score inputs. | Inspect reach/visibility component. |
| `영상_간격.xlsx` | Video upload interval data. | Inspect upload-stability signal. |
| `간격_master_df.xlsx` | Aggregated upload interval table. | Inspect cadence features used in scoring. |
| `좋아요 누락 영상 개수.csv` | Count of videos with missing like information. | Inspect data-quality issue related to likes. |
| `누락영상.csv` | Missing-video records or checks. | Inspect missing-data handling. |
| `in_com_not_month.csv` | Small intermediate or exception output retained for context. | Inspect edge cases in monthly/comment merge logic. |
| `not_enough_youtuber.csv` | Creators with insufficient data. | Inspect minimum-data boundary. |
| `raw_data_score.csv` | Score construction table before final grade assignment. | Inspect grading inputs without raw comments. |
| `등급_예측.xlsx` | Grade-prediction output or prediction input/output table. | Inspect prediction experiment surface. |
| `mater_table.xlsx` | Supporting table used in modeling or grade calculation. | Inspect auxiliary modeling context. |

## Core Concepts

| Concept | Meaning |
| --- | --- |
| YouTuber / creator | Channel or creator evaluated by the framework. |
| Month | Time unit for trend and feature aggregation. |
| Awareness | Public scale or visibility signal such as views or subscribers. |
| Growth | Direction and strength of change over time. |
| Sentiment score | Model-derived comment reaction signal. |
| Loyalty | Proxy for stable or repeated audience engagement. |
| Upload interval | Time gap between videos, used as an operational stability signal. |
| Score | Composite numeric surface used before grade assignment. |
| Grade | Human-readable grouping derived from score thresholds. |

## Data Quality Notes

- Some files retain original Korean column names.
- Some historical notebooks and CSV outputs contain encoding artifacts from the original execution environment.
- Public files are intended for portfolio review, not for automated production ingestion.
- Raw rows containing comment text or collection-level personal/user-generated content are not part of the public reproducibility boundary.
