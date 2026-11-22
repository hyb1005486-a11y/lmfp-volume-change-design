# LMFP 양극재의 충방전 부피 변화 — Mn 비율과 Mg 도핑 설계

인공지능재료설계 개인 프로젝트 (2026-2학기)

## 설계 질문
올리빈 LiFePO₄ 의 Fe 를 Mn 으로 0~100 % 바꾸고(LMFP), Mg 를 25 % 넣으면 방전(LiMPO₄) ↔ 충전(MPO₄) 사이의 부피 변화와 이론 용량이 어떻게 변하는가?

## 방법
- Materials Project 구조 · 전극 데이터 (`mp-api`, `pymatgen`)
- 범용 머신러닝 포텐셜로 방전 · 충전 두 상태의 구조 최적화 (`matgl`, `M3GNet-PES-MatPES-r2SCAN-2025.2`, fmax 0.05 eV/Å, relax_cell=True)
- 포텐셜 4종(M3GNet PBE/r2SCAN, CHGNet r2SCAN, TensorNet r2SCAN)을 MP 전극 데이터와 비교해 선택 — LiFePO₄ · LiMnPO₄ 의 부피 변화를 재현한 M3GNet r2SCAN 사용

## 결과
- 검증: LiFePO₄ 6.25 % (MP 6.4 %), LiMnPO₄ 6.90 % (MP 6.6 %)
- Fe 와 Mn 을 섞은 조성(Mn 25 · 50 · 75 %)은 양 끝 조성보다 부피 변화가 크다 (7.2 ~ 7.9 %)
- Mg 25 % 도핑: LMFP 50 % 의 부피 변화 7.2 → 4.7 %, 이론 용량 170 → 135 mAh/g

## 한계
- LiCoPO₄ · LiNiPO₄ 는 네 포텐셜 모두 MP 값을 재현하지 못해 설계에서 제외
- 28원자 셀, 완전 방전 · 충전 두 끝점만 계산 (중간 상 · 이방성 변형 미고려), 0 K

## 참고
- 코드 작성과 발표 슬라이드 제작에 LLM(Claude)의 도움을 받았으며, 계산 실행과 결과 검증 · 판단은 직접 수행함
- 수업 튜토리얼(Ch.9 09a · 09b)의 구조 최적화 · 치환 코드를 바탕으로 함

## 실행
`Project_LMFP_VolumeChange_final.ipynb` 를 Google Colab 에서 열고 위에서부터 실행. Materials Project API key 는 실행 중 입력창에 넣는다 (코드에 저장되지 않음).
