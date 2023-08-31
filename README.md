# 🎓 About LG Aimers
[LG Aimers](https://www.lgaimers.ai/)는 최고의 교수진이 함께 하는 AI교육과 LG의 실제 데이터를 다루는 AI해커톤에 참여할 수 있는 경험의 기회를 제공하는
LG그룹의 청년 교육 프로그램이다. LG AI연구원에서 진행하며 1개월의 온라인 교육과 1개월의 해커톤으로 구성된다.
해커톤에서는 LG의 여러 계열사가 보유한 다양한 산업의 현장 Data를 직접 다루고, 문제를 해결하는 실무 경험을 쌓을 수 있다.

## LG Aimers 2기
- 주제: [스마트 공장 제품 품질 상태 분류 AI 온라인 해커톤](https://dacon.io/competitions/official/236080/overview/description)
- 기간: 2023.02.01~2023.02.28
- 결과: Public 5th, Private 135th

### Model
LightGBM classifier & Lidge classifier [[model.py]](https://github.com/riverallzero/LGAimers/blob/main/LGAimers-2/model.py)

### Conclusion
Public score와 Private score의 큰 차이의 원인은 overfitting으로 **cross-validation**을 하지않아 그런 것으로 사료됨.

## LG Aimers 3기
- 주제: [온라인 채널 제품 판매량 예측 AI 온라인 해커톤](https://dacon.io/competitions/official/236129/overview/description)
- 기간: 2023.08.01~2023.08.28
- 결과: Public 194th, Private 133th

### Model
LSTM [[model.py]](https://github.com/riverallzero/LGAimers/blob/main/LGAimers-3/model.py)

### Conclusion
시계열 예측 모델은 다양한 수학적 지식이 필요한데 이에 대해 잘 알지 못했고, **일별 판매량**만 가지고 **LSTM**으로 기본 예측만 수행해 성능 향상이 이루어지지 않음.
