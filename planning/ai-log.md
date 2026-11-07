# AI 활용 기록

## 기록 규칙
저장소 파일을 만들거나 고칠 때마다 아래를 지킨다.
1. 작업 전 이 파일의 규칙을 확인한다.
2. 작업 후 해당 폴더 README와 루트 README의 진행 상황을 갱신한다.
3. 이 파일의 기록표에 한 줄을 추가한다 (날짜, 작업, 모델, 추론 설정, AI가 한 일, 사람이 한 일, 관련 파일).
4. 커밋 문구 Description 끝에 `AI 활용: 모델(추론 설정) — 한 일` 줄을 넣는다.

- 기본 모델: Claude Opus 5.5 / 추론 설정: 중간
- 커밋·푸시는 사람이 GitHub Desktop으로 직접 한다.
- "사람이 한 일"에는 AI 결과를 확인·수정·결정한 내용을 적는다.

## 기록표
| 날짜 | 작업 | 모델 | 추론 설정 | AI가 한 일 | 사람이 한 일 | 관련 파일 |
|---|---|---|---|---|---|---|
| 2026-11-07 | 저장소 기본 구조 만들기 | Claude Opus 5.5 | 중간 | 폴더 구조 제안, README·기획 문서·.gitignore 초안 작성 | 프로젝트 내용 브리핑, 구조 승인, 내용 확인, 커밋·푸시 | README.md, .gitignore, planning/, data/, model/, web/, drone/, validation/ |
| 2026-11-07 | AI 활용 기록 체계 만들기 | Claude Opus 5.5 | 중간 | 기록 규칙·기록표 작성, README 링크 추가 | 기록 항목(모델·추론 설정 포함) 결정, 프로젝트 지침 등록, 커밋·푸시 | planning/ai-log.md, README.md, planning/README.md |
| 2026-11-07 | 1단계: AI Hub 데이터 조사·공개 모델 테스트 결과 정리 | Claude Opus 5.5 | 중간 | 사용자 제공 화면 캡처 분석, 수치 검산(IoU 등), 우리 계획(RGB)과의 차이 정리, 조사표·실험 기록 작성, 보고서 PDF 이름 변경·배치 | AI Hub 데이터 다운로드, 공개 모델 테스트 실행(2026-10-03)과 보고서 작성, 자료 제공, ①R·G·B 재학습 ②RGB 데이터 추가 방향 제시, 내용 확인, 커밋·푸시 | data/README.md, model/README.md, model/reports/2026-10-03_aihub-segformer-b4-test-report.pdf, README.md, planning/ai-log.md |
| 2026-11-07 | 1단계: 드론 오픈 데이터 조사 정리, 보고서 PDF 공개 제외 | Claude Opus 5.5 | 중간 | 웹 검색 8회·페이지 열기 18회로 후보 조사, 사용자 캡처 분석, 태국 BLB tif·Zenodo zip 파일 분석(밴드 순서 계산, 구성·장수 확인), 조사표 작성, AI Hub 이용정책에 맞춰 PDF를 Git 추적에서 제외 | 링크·캡처 제공, Drive·Roboflow 직접 확인, 근접 사진 제외·근거 표시 요청, PDF 처리 방식 결정, 내용 확인, 커밋·푸시 | data/README.md, model/README.md, README.md, .gitignore, planning/ai-log.md, model/reports/(추적 제외) |
| 2026-11-07 | 2단계: 병해 범위·탐지 방식·정량 목표 결정 기록, 수확기 병해 추가 조사 | Claude Opus 5.5 | 중간 | 수확기 병해 7종 드론 데이터 추가 조사(검색 14회·페이지 21회), 조사 결과로 가능한 범위와 위험·대응 정리, 결정 사항·일정 문서 반영 | 조사 대상 병해 지정, 범위·실험 방식·정량 목표·터빈크루 문의 시점 결정, 내용 확인, 커밋·푸시 | planning/decisions.md, planning/schedule.md, README.md, planning/ai-log.md |
