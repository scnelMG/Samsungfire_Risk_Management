# Data Dictionary

## Public Data Boundary

이 문서는 공개 데이터 파일의 목록이 아니라, 원래 분석에 사용한 개념의 정의입니다. 이 저장소는 raw data뿐 아니라 파생·집계 테이블도 공개하지 않습니다. 데이터마다 재배포 조건, 수집 시점, 채널·영상 단위 식별 가능성을 이 공개본에서 독립적으로 검증할 수 없기 때문입니다.

## Core Concepts

| Concept | Meaning |
| --- | --- |
| YouTuber / creator | Channel or creator evaluated by the framework. |
| Month | Time unit for trend and feature aggregation. |
| Awareness | Public scale or visibility signal such as views or subscribers. |
| Growth | Direction and strength of change over time. |
| Sentiment score | Model-derived comment reaction signal. |
| Loyalty | Proxy for stable or repeated audience engagement. |
| Upload interval | Channel별 월간 영상 업로드 일자 차이의 평균. `10_grade_threshold_design.ipynb`에서 점수 구간 설계에 사용. 영상 개수와 업로드가 없는 연속 월수(`null_지속`)는 보조 진단값. |
| Score | Composite numeric surface used before grade assignment. |
| Grade | Human-readable grouping derived from score thresholds. |

## Historical Data Quality Notes

- Historical notebook과 CSV 출력에는 원래의 한글 컬럼명과 인코딩 차이가 남아 있을 수 있습니다.
- 원본 댓글과 수집 단위 사용자 생성 콘텐츠는 공개 재현 경계에 포함하지 않습니다.
- 이 공개본은 자동화된 데이터 ingestion이나 완전 재현용 패키지가 아니라 프로젝트의 분석 설계와 구현 흐름을 검토하기 위한 포트폴리오입니다.
