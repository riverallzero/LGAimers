# 🎓 About LG Aimers
[LG Aimers](https://www.lgaimers.ai/)는 최고의 교수진이 함께 하는 AI교육과 LG의 실제 데이터를 다루는 AI해커톤에 참여할 수 있는 경험의 기회를 제공하는
LG그룹의 청년 교육 프로그램이다. LG AI연구원에서 진행하며 1개월의 온라인 교육과 1개월의 해커튼으로 구성된다.
해커톤에서는 LG의 여러 계열사가 보유한 다양한 산업의 현장 Data를 직접 다루고, 문제를 해결하는 실무 경험을 쌓을 수 있다.

## LG Aimers 2기
- 주제: 스마트 공장 제품 품질 상태 분류 AI 온라인 해커톤
- 기간: 2023.02.01~2023.02.28
- 결과: Public 5th, Private 135th

<details>
<summary>Data Preprocessing</summary>

- PRODUCT_CODE별 데이터 분리
  - A_31, O_31, T_31 별 결측치 확인
  - 결측치를 가진 열이 코드별 상이
  - O_31과 T_31 유사
  - **A_31과 O_31, T_31 2가지 모델을 나누어 구성**
  
- A_31 Preprocessing
  - train.csv에서 PRODUCT_CODE == "A_31"인 값 사용
  - 결측치 유지 및 모든 열 사용
  - LightGBM classifier
 
- O_31, T_31 Preprocessing
  - train.csv에서 PRODUCT_CODE == "O_31" 또는 "T_31"인 값 사용
  - def seperate_code() : Line별로 데이터를 분리 후 모든 값이 같은 열 제거
  - find_duplicate_col() : Line별로 결측치있는 열을 제거 후 교집합하여 사용할 열 결정 
  - Lidge classifier
</details>

<details>
<summary>Val Result(acc)</summary>

- **A_31** (0.747)
- **O_31 & T_31** (0.810)
</details>

<details>
<summary>Try(data preprocessing, model)</summary>

- IQR을 이용한 이상치 탐지 및 변경
  - 이상치에 대한 값을 각 열별 제 2사분위수(Q2)로 변경 후 모델링
  - 이상치에 대한 값을 NaN으로 변경 후 Tree기반 모델링
  - 이상치에 대한 개수로 값을 변경 후 분류 모델링
     
- Y_Class 데이터 불균형 해소
  - SMOTETomek와 TomekLinks를 이용한 언더샘플링 후 모델링
  - SMOTE, ADASYN을 이용한 오버샘플링 후 모델링

- Y_Quality로 Y_Class 분류
  - Y_Quality가 분류하는 Y_Class의 정확도는 0.99로 매우 정확함
  - 회귀로 Y_Quality를 예측한 후, 예측 결과로 Y_Class를 분류하는 모델링
  
-  공정 LINE 종류에 따라 구분해서 학습
  - PRODUCTCODE 뿐만 아니라 LINE 별로 분류해서 학습
</details>

<details>
<summary>Conclusion</summary>

Public score와 Private score의 큰 차이의 원인은 overfitting으로 <strong>cross-validation</strong>을 하지않아 그런 것으로 사료됨.
</details>

## LG Aimers 3기
- 주제: 
- 기간: 2023.07.01~2023.08.28
- 결과: 
