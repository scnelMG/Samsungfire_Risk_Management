# Notebook Guide

이 디렉터리는 경진대회 당시의 분석 흐름을 보존한 notebook 모음입니다. 데이터와 모델 산출물은 공개하지 않으므로, 공개본은 **구현 검토용**이며 위에서 아래로 실행해 동일한 결과를 재현하는 패키지는 아닙니다.

## 검토 순서

| 단계 | Notebook | 목적 |
| --- | --- | --- |
| 수집 | `01_youtube_data_collection.ipynb`, `03_video_metadata_collection.ipynb` | YouTube 댓글·메타데이터 수집 실험 |
| 품질·전처리 | `04_data_quality_check.ipynb`, `05_comment_labeling_preprocess.ipynb` | 결측 점검과 감성 학습용 댓글 준비 |
| 감성·신호 | `06_sentiment_lstm_modeling.ipynb`, `07_comment_loyalty_score.ipynb`, `08_upload_interval_feature.ipynb` | 감성, 충성도, 업로드 안정성 신호 구성 |
| 통합·등급 | `09_feature_merge.ipynb`, `10_grade_threshold_design.ipynb`, `11_grade_assignment.ipynb` | feature 결합, threshold 설계, 등급 부여 |
| 확인 | `14_grade_score_visualization.ipynb` | score·grade 추이 확인 |

`12`, `13`의 예측 실험은 [archive](archive/README.md)로 분리했습니다. 이 저장소의 포트폴리오 핵심 경로는 감성 분석과 등급 설계이며, archive의 성능 수치는 인용하지 않습니다.

## 실행 경계

- `01`, `03`의 수집 코드는 API·브라우저·수집 시점에 의존하는 과거 실험입니다.
- `06`은 원본 학습 데이터와 당시 runtime state가 없으므로 성능값을 재현하거나 비교하는 근거로 사용하지 않습니다.
- notebook에는 당시 탐색 과정이 남아 있을 수 있습니다. 포트폴리오의 검토 근거는 코드 구조, [분석 방법](../docs/analysis-method.md), 그리고 [실제 최종 발표자료](../assets/final-presentation.pdf)를 함께 확인하는 것입니다.
- 새 visual을 추가할 때는 실제 실행 결과 또는 실제 발표 산출물만 사용합니다. 인공적으로 생성한 이미지는 사용하지 않습니다.
