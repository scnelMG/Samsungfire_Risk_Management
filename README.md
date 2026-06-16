# Samsungfire Risk Management

2023 삼성화재 데이터기반 리스크관리 경진대회 프로젝트입니다. 유튜브 인플루언서 협업에서 발생할 수 있는 평판·성과 리스크를 정량화하기 위해 영상 성과, 댓글 감성, 충성도, 업로드 주기, 성장률을 결합한 유튜버 등급 평가 모델을 설계했습니다.

## Project Overview

기업이 인플루언서와 협업할 때 단순 구독자 수나 평균 조회수만 보면 실제 리스크를 놓치기 쉽습니다. 이 프로젝트는 패션·뷰티 유튜버 데이터를 바탕으로 다음 질문에 답하려 했습니다.

- 어떤 유튜버가 안정적인 협업 성과를 낼 가능성이 높은가?
- 댓글 반응과 충성 시청자 비율은 협업 리스크 판단에 얼마나 도움이 되는가?
- 월별 지표 변화로 유튜버 등급 변동을 설명하거나 예측할 수 있는가?

## Approach

분석은 네 단계로 구성했습니다.

1. **데이터 수집**: 유튜버 채널, 영상 메타데이터, 댓글 데이터를 수집했습니다.
2. **지표 설계**: 인지도, 성장률, 감성점수, 충성도, 평균 업로드 간격을 산출했습니다.
3. **등급 산정**: 신용평점 모형의 아이디어를 참고해 유튜버 리스크 등급을 부여했습니다.
4. **예측 모델링**: 머신러닝과 딥러닝 기반으로 등급 예측 가능성을 검토했습니다.

## Key Outputs

- 유튜버별 월간 성과와 댓글 기반 반응을 결합한 통합 데이터셋
- 인지도·충성도·감성점수·업로드 간격을 활용한 등급 기준
- 등급 및 점수 변화 시각화
- 협업 대상 선정과 리스크 모니터링에 활용할 수 있는 평가 프레임워크

최종 발표자료는 [assets/final-presentation.pdf](assets/final-presentation.pdf)에서 확인할 수 있습니다.

## Repository Structure

```text
.
├── assets/
│   └── final-presentation.pdf
├── data/
│   ├── README.md
│   └── processed/
├── docs/
│   ├── analysis-method.md
│   ├── data-dictionary.md
│   └── project-summary.md
├── notebooks/
│   ├── 01_youtube_data_collection.ipynb
│   ├── 06_sentiment_lstm_modeling.ipynb
│   ├── 10_grade_threshold_design.ipynb
│   ├── 12_grade_prediction_ml.ipynb
│   └── 14_grade_score_visualization.ipynb
└── requirements.txt
```

## Notebook Guide

| Step | Notebook | Purpose |
| --- | --- | --- |
| 01 | `01_youtube_data_collection.ipynb` | YouTube API 기반 데이터 수집 |
| 02-04 | `02_*` ~ `04_*` | Selenium 수집 실험과 데이터 점검 |
| 05 | `05_comment_labeling_preprocess.ipynb` | 댓글 라벨링 데이터 전처리 |
| 06 | `06_sentiment_lstm_modeling.ipynb` | LSTM 기반 댓글 감성 분석 |
| 07-09 | `07_*` ~ `09_*` | 충성도, 업로드 간격, 통합 지표 생성 |
| 10-11 | `10_*`, `11_*` | 등급 기준 산정과 등급 부여 |
| 12-13 | `12_*`, `13_*` | 등급 예측 모델링 |
| 14 | `14_grade_score_visualization.ipynb` | 등급 및 점수 변화 시각화 |

## Data Policy

이 레포는 포트폴리오 공개용으로 정리했습니다. 원천 댓글 데이터, 학습된 모델 가중치, 토크나이저, 크롬드라이버 실행 파일은 공개 후보에서 제외했습니다. 대신 최종 집계·등급·점수 산출물은 `data/processed/`에 보관했습니다.

자세한 데이터 설명은 [data/README.md](data/README.md)와 [docs/data-dictionary.md](docs/data-dictionary.md)를 참고하세요.

## Environment

주요 분석 환경은 Python/Jupyter Notebook입니다.

```bash
pip install -r requirements.txt
```

일부 수집 노트북은 Selenium, ChromeDriver, YouTube 페이지 구조에 의존합니다. 현재 포트폴리오 버전에서는 수집 재실행보다 분석 흐름과 산출물 검토를 우선합니다.

## Limitations

- 수집 시점의 YouTube 페이지 구조와 공개 지표에 의존합니다.
- 댓글 원문과 대형 모델 파일은 공개하지 않아 전체 재학습은 이 레포만으로 재현되지 않습니다.
- 일부 원본 산출물에는 당시 인코딩 문제로 깨진 컬럼명이 남아 있습니다. 문서에서는 사람이 해석 가능한 수준으로 정리했습니다.

## More Details

- [Project Summary](docs/project-summary.md)
- [Analysis Method](docs/analysis-method.md)
- [Data Dictionary](docs/data-dictionary.md)
