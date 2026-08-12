# Notebook Guide

이 디렉터리는 두 가지 성격의 notebook을 함께 보관합니다.

1. **공개 데모**: 현재 공개 저장소에서 위에서 아래로 실행 가능한 검토 경로
2. **역사적 분석 기록**: 경진대회 당시의 구현 흐름을 보존한 참고 자료

원본 댓글·수집 결과·파생 테이블·모델 가중치는 공개하지 않습니다. 따라서 역사적 notebook은 동일 결과를 재현하는 패키지가 아니라 구현 방식과 프로젝트 맥락을 검토하는 자료입니다.

## 공개 실행 경로

| Notebook | 목적 | 입력 | 실행 범위 |
| --- | --- | --- | --- |
| [`00_public_scoring_demo.ipynb`](00_public_scoring_demo.ipynb) | 다섯 신호를 score와 A/B/C grade로 연결하는 설명용 흐름 | [`examples/public_scoring_demo.csv`](../examples/public_scoring_demo.csv) | **현재 실행 가능**. 표본·가중치·threshold는 모두 가상 예시이며 실제 결과를 재현하지 않음 |

repository root에서 다음 명령으로 실행을 확인할 수 있습니다.

```bash
python -m jupyter nbconvert --execute --to notebook --stdout notebooks/00_public_scoring_demo.ipynb
```

## 역사적 분석 흐름

| 단계 | Notebook | 목적 | 공개 실행 경계 |
| --- | --- | --- | --- |
| 수집 | `01_youtube_data_collection.ipynb`, `03_video_metadata_collection.ipynb` | YouTube 댓글·메타데이터 수집 실험 | 수집 API·브라우저·ChromeDriver·수집 시점 및 비공개 입력에 의존 |
| 품질·전처리 | `04_data_quality_check.ipynb`, `05_comment_labeling_preprocess.ipynb` | 결측 점검과 감성 학습용 댓글 준비 | 비공개 원본/라벨 댓글 테이블 필요 |
| 감성·신호 | `06_sentiment_lstm_modeling.ipynb`, `07_comment_loyalty_score.ipynb`, `08_upload_interval_feature.ipynb` | 감성, 충성도, 업로드 안정성 신호 구성 | 비공개 학습·평가 데이터와 model weight 필요 |
| 통합·점수화 | `09_feature_merge.ipynb`, `10_grade_threshold_design.ipynb`, `11_grade_assignment.ipynb` | feature 결합, threshold 설계, component score 산정 | 당시 Colab/개인 Drive 경로와 비공개 파생 테이블에 의존 |
| 확인 | `14_grade_score_visualization.ipynb` | score·grade 추이 확인 | 비공개 최종 통합 테이블에 의존 |

`12`, `13`의 예측 실험은 [archive](archive/README.md)로 분리했습니다. 이 저장소의 포트폴리오 핵심 경로는 score 설계와 등급화이며, archive의 성능 수치는 인용하지 않습니다.

## 검토 기준

- 실제 대회 검증 기록은 [최종 발표자료](../assets/final-presentation.pdf)와 [README의 결과 표](../README.md#최종-발표자료-기준-검증-결과)에서 확인합니다.
- 역사적 감성 노트북의 AUC 계산은 확률값을 사용하도록 수정했습니다. 공개 데이터가 없으므로 이 수정으로 과거 지표를 재산출하거나 새로운 성능을 주장하지는 않습니다.
- 새 visual은 실제 실행 결과 또는 실제 발표 산출물만 사용합니다. 인공적으로 생성한 이미지는 사용하지 않습니다.
- 데이터 공개 정책은 [data/README.md](../data/README.md)와 [공개 안전성 검토](../docs/public-safety.md)를 확인하세요.
