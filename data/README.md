# data (데이터)

## 현재 상태
- 1단계(오픈 데이터 조사) 정리 완료
- **결론: 일반 RGB 카메라로 찍은 벼 병해 드론 데이터는 공개된 것이 거의 없음.** 병해 라벨이 있는 드론 데이터는 모두 다분광 촬영 + 분할(영역) 라벨
- 기본 방향: 다분광 데이터에서 R·G·B 밴드만 뽑아 일반 사진처럼 색을 맞춰 학습 (결정은 2단계)

## 결정된 것
- RGB 데이터 사용 (거의 확정)
- 직접 라벨링 불가 → 오픈 데이터 활용
- 잎 근접 사진 데이터는 제외, 드론 데이터만 사용

## 다음 할 일
- 2단계에서 결정: 병해 범위(도열병·BLB만 / 생육이상까지), 탐지 방식(박스 / 분할), 비행 높이·해상도 기준

## 근거 표시
[화면] 사이트 화면에서 확인 · [파일] 파일을 직접 열어 확인 · [웹] 웹 페이지를 열어 확인(요약 도구 경유) · [계산] 확인한 값으로 계산 · [추정] 파일 이름·사진 모양 등으로 판단

## 데이터셋 조사표 (드론 데이터만)
| 순위 | 데이터 | 대상 | 촬영·해상도 | 라벨 | 이미지 수 | 1장이 무엇인지 | 용량 | 이용 조건 | 메모 |
|---|---|---|---|---|---|---|---|---|---|
| **주력** | [AI Hub 벼 생육이상 인식 데이터](https://aihub.or.kr/aihubdata/data/view.do?dataSetSn=71483) | 도열병 + 도복·결주·생육부진 (병해는 도열병뿐) [화면] | 고도 약 149m, 픽셀당 약 6.6~6.8cm, 다분광 5밴드 [화면] | 폴리곤 분할, json [화면] | 200,910장 [화면] | 512×512 조각 [화면, json 예시 1건] / 약 34m [계산] | 147.83GB [화면] | 아래 이용 조건 참고 | RGB는 밴드 추출 필요. 도열병 영역 비율 2.6% [화면] |
| **주력** | [태국 BLB UAV Dataset](https://figshare.com/articles/dataset/BLB_UAV_Dataset/26955862) ([논문](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0314535), [데이터 Drive](https://drive.google.com/drive/folders/17mCuj35euNjwNEIEqNqM_bJqNdHLuXwL?usp=sharing)) | 세균성벼잎마름병(BLB) 경증·중증 [웹] | 고도 20m, DJI P4 Multispectral [웹], 픽셀당 약 1.1cm [파일] | 클래스 번호 마스크 tif: 0 미라벨, 1 기타, 2 경증, 3 중증, 4 정상 [파일·화면] | 1,857장 (train 1,299 / val 277 / test 281) [화면·사용자 확인] | 256×256 조각 [파일, 1건] / 약 2.8m [계산] | 확인 필요 | 논문 인용 조건 (정식 License 없음) [화면] | D1만 사용. RGB = 밴드 2·1·0 (아래 분석 참고) |
| **주력 후보** | [GD-RGBMS-DB (Zenodo)](https://zenodo.org/records/17008818) | 낟알 변색병 [파일: readme] | 고도 약 12m, DJI Mavic 3 Multispectral, **실제 RGB 카메라 사진 + 다분광(G·RE·NIR 3밴드) 맞춤 쌍**, 베트남 메콩델타, 2025-06 [파일: readme] | 색 마스크 png (배경 / 변색 영역) [파일] | 400세트 (train 280 / val 60 / test 60) [파일] | 1200×900 사진 [파일, 1건] | 981.7MB [웹] | CC BY 4.0 [웹] | 병든 영역이 매우 작음(예시 1장에서 0.3% [계산]). 다분광 3밴드가 AI Hub 공개 모델 입력(G·N·E)과 같은 조합 |
| 보조 | [Weedy Rice RGB-MS (Mendeley)](https://data.mendeley.com/datasets/vt4s83pxx6/1) | 잡초성 벼 (병해 아님) [화면] | DJI Mavic 3 Multispectral, RGB + 다분광 4밴드 쌍, GPS 포함 [화면] | 이진 마스크 [화면] | 734장 [화면] | 1280×960 사진 [화면] | 4.93GB [화면] | CC BY 4.0 [화면] | 다분광 RGB ↔ 실제 RGB 색 맞추기 연구용 |
| 보조 | [rice (yolov7liangcang)](https://universe.roboflow.com/yolov7liangcang-xfwrc/rice-fd2rp) | 도복 (파일명 `水稻倒伏`) [화면] | RGB 드론, 비스듬히 촬영 [추정] | 인스턴스 분할 [화면] | 135장 [화면] | 드론 영상 장면 [추정] | 확인 필요 | CC BY 4.0 [화면] | 실제 RGB 드론 영상 |
| 보조 | [Jenis Hama](https://universe.roboflow.com/muhammads-workspace-9tgy3/jenis-hama) | 해충 피해: `penggerek-batang`(줄기 해충), `wereng-coklat`(벼멸구), `padi-sehat`(건강), `matang`(익은 벼) [화면, 뜻은 추정] | RGB 드론(DJI), 낮게 비스듬히 [추정] | 큰 박스 [화면] | 185장 [화면] | 드론 사진 [추정] | 확인 필요 | CC BY 4.0 [화면] | 박스가 사진 대부분을 덮음 |
| 참고 | [Crop Disease Prediction](https://universe.roboflow.com/bnu-al2ab/crop-disease-prediction) | `leaf_rust`(잎녹병) [화면] → **밀 데이터로 추정** | 드론, 높은 곳에서 비스듬히 [추정] | 박스 [화면] | 40장 [화면] | 드론 영상 장면 [추정] | 확인 필요 | CC BY 4.0 [화면] | 벼 아님 추정. 작은 박스·타일링 형식만 참고 |
| 참고 | [RICE](https://universe.roboflow.com/rice-dtlkf/rice-iyd0q) / [RICE-2tietle](https://universe.roboflow.com/rice-dtlkf/rice-2tietle) | 도복으로 보임 [추정] | 아주 낮은 각도 [추정] | 인스턴스 분할 [화면] | 97장 [화면] | 낮은 각도 사진 [추정] | 확인 필요 | CC BY 4.0 [화면] | 두 링크는 같은 데이터 [추정] |
| 참고 | [Klasifikasi Hama Padi](https://universe.roboflow.com/joko-joestar/klasifikasi_hama_padi-ggr0w) | 해충·새 [추정] | 드론과 휴대폰 사진이 섞임 [추정] | 박스 [화면] | 118장 [화면] | 섞임 [추정] | 확인 필요 | CC BY 4.0 [화면] | |

※ Roboflow 이미지 수는 변형해서 늘린 버전을 뺀 원본 수입니다.

## 합성 데이터 (보류)
| 항목 | 내용 |
|---|---|
| 이름 | `data/raw/synthetic_rice_blast_yolo_train_262` (GitHub에는 올리지 않음) |
| 만든 방식 | 팀원이 생성 AI(GPT)에 "낟알 변색 데이터(Zenodo, 12m 항공) 기반으로 도열병 증강"을 요청해 생성 [사용자 제공]. 정확한 도구·요청문·참고 자료는 **확인 필요** |
| 구성 [파일] | 학습용만 262장 + YOLO 박스 라벨 262개(박스 506개), 1200×900, 클래스 1개 `synthetic_rice_neck_blast` |
| 점검 결과 | Zenodo 원본 400장과 비교해도 일치하는 원본 없음 → 원본을 고친 것이 아니라 새로 생성한 사진으로 추정 [계산]. 병반 색 픽셀이 박스 안에 약 2.65배 많아 라벨은 대체로 양호 [계산]. 일부 사진(#001 등)은 박스 밖에도 병반 같은 부분이 있음, 몇 장인지는 확인 필요. 병반이 비슷한 별 모양으로 반복돼 모델이 그 패턴을 외울 위험 [추정] |
| 상태 | **보류** — 만든 방법(도구·모델, 요청문, 참고 자료, 262장 선택 기준)을 기록한 뒤 사용 |
| 사용 원칙 | 학습 데이터에만 추가(검증·시험 금지). "AI Hub만" vs "AI Hub + 합성"을 AI Hub 실제 도열병 시험 데이터로 채점해 점수가 오를 때만 채택. 해상도(12m vs 149m)·라벨(박스 vs 폴리곤)·클래스(목도열병 vs 도열병) 맞춘 뒤 비교 |
| 기록을 못 찾으면 | AI Hub 실제 도열병으로 복사-붙여넣기 증강을 먼저 쓰고, 합성 데이터는 "생성 과정 불명확"으로 밝힌 참고 실험으로만 사용 |

## AI Hub 이용 조건 [중간보고서 9-4절, 2026-10-07 확인]
- 영리·비영리 연구·개발 모두 가능, 단 AI 모델 학습용으로만
- 데이터와 2차 저작물(보고서·모델)에 "한국지능정보사회진흥원 사업결과" 표기
- 승인 없이 다른 법인·단체·개인에게 열람·제공·양도·판매 금지 → 원본을 기업에 넘기려면 승인 필요, **AI Hub 이미지가 담긴 자료는 공개 저장소에 올리지 않음**
- 데이터셋 판매 등 상업적 이용은 수행기관과 별도 협의
- 확인 필요(3단계 전까지): 데이터 페이지 자체 정책, 학습한 모델 공개 가능 여부, AWS 등 클라우드 업로드 가능 여부

## 태국 BLB 파일 분석 [파일: D1·D2·D3의 image_patch_3 / label_patch_3 직접 확인]
- 이미지: 256×256, float32(0~1), 지도 좌표 포함(EPSG:32647), 값 0 = 데이터 없음
- D1 = 5밴드 / D2 = D1 + NDVI / D3 = D1 + NDRE. 세 폴더의 사진·라벨은 같음 → **D1만 사용**
- 밴드 순서: 0 파랑, 1 초록 [추정: 기체 기본 순서] / 2 빨강, 3 레드엣지, 4 근적외선 [계산: D2 6번째 밴드 = (밴드4−밴드2)/(밴드4+밴드2) 상관 0.9999, D3 6번째 밴드 = (밴드4−밴드3)/(밴드4+밴드3) 상관 1.0]
- 인용: Logavitool G, Horanont T, Thapa A, Intarat K, Wuttiwong K-o (2025) Field-scale detection of Bacterial Leaf Blight in rice based on UAV multispectral imaging and deep learning frameworks. PLoS ONE 20(1): e0314535. https://doi.org/10.1371/journal.pone.0314535

## 조사 메모
- AI Hub 공개 모델 테스트 결과: [model/README.md](../model/README.md)
- 데이터 혼합 시 주의: 해상도 차이가 크면 고해상도 쪽을 줄여서 맞춤(AI Hub와 태국 BLB는 약 6배 차이 [계산: 6.63 ÷ 1.104]), 라벨 형태·클래스 이름 통일, 평가는 데이터별로 따로
- 다분광 데이터의 RGB는 일반 카메라 사진과 밝기·색감이 달라서 색 맞추기가 필요함 [추정]
- 확인 필요: AI Hub 해상도 표기 차이(6.63cm / 6.8cm), AI Hub 페이지 수치 불일치(전체 mAcc 77.44% vs 86.69%)
- 인용 정보: GD-RGBMS-DB — Nguyen, V. H., Cong Le, D., Le Thanh, P., & Bui Thi Mai, P. (2025). Zenodo. https://doi.org/10.5281/zenodo.17008818

※ 실제 이미지 파일은 저장소에 올리지 않습니다 (`data/raw/`, `data/processed/`는 자동 제외).
