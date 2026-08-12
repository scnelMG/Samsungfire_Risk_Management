# GitHub Support 요청 기준

현재 공개 브랜치와 Git 이력에서는 제거됐지만 GitHub 캐시에 남을 수 있는 historical object에 대한 안내입니다.

## GitHub 정책상 가능한 경우

GitHub Support는 history rewrite와 force-push 이후에도 **민감한 개인정보 또는 구체적인 보안 위험을 만드는 자료**에 한해 서버 측 garbage collection·캐시 제거 등을 지원할 수 있다고 안내합니다. 단순히 공개를 원하지 않는 일반 데이터는 이 절차로 삭제를 보장받을 수 없습니다.

따라서 아래 조건을 모두 충족할 때만 Support ticket을 제출합니다.

- 실제 민감 정보 또는 보안 위험이 존재한다.
- 위험의 성격을 과장 없이 구체적으로 설명할 수 있다.
- history rewrite와 정리된 현재 공개 트리를 이미 push했다.

관련 GitHub 안내: [Removing sensitive data from a repository](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository)

## 현재 확인된 객체

- Repository: `https://github.com/scnelMG/Samsungfire_Risk_Management`
- Historical commit: `839362df386440d7e3947b66fa60c586700907a6`
- File path: `data/processed/total_year_video_df.csv`

현재 이 문서만으로는 해당 파일이 GitHub의 민감 정보 삭제 기준을 충족한다고 단정할 수 없습니다. 민감 정보·보안 위험의 사실관계는 데이터 보관자만 판단할 수 있습니다.

## 제출 전 확인 문구

Support 화면의 설명에는 다음 세 가지를 사실대로 적습니다.

1. repository URL, historical commit SHA, file path
2. 구체적인 민감 정보 또는 보안 위험의 종류
3. history rewrite와 force-push를 완료한 사실

민감 정보 또는 보안 위험이 없다면 티켓을 제출하지 않습니다. 현재 공개 트리·태그·문서에서 자료를 제거하고 `.gitignore`로 재유입을 막는 조치가 이 저장소에서 가능한 안전한 범위입니다.
