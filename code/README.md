## 🎆 실험 핵심 내용

### Numba를 활용한 crop_img 전처리 코드 최적화

|Augmentation method|crop_img 최적화 여부|Training time / epoch|
|:----:|:----:|:----:|
|base|x|3.2s+-0.3|
|base|o|2.0s+-0.3|

<br/>

### Data cleansing

    - fix mislabeled points (시계방향 순서)
    - remove lines labels (학습에 방해된다고 판단)

|Augmentation method|cleansing|f1-score|
|:----:|:----:|:----:|
|base|x|0.8021|
|base|o|0.8736|

<br/>

### Crop_img 랜덤하게 적용

    - 기존 100% 확률로 적용되던 crop_img를 50%확률로 조정

|Augmentation method|crop_img applied randomly|f1-score|
|:----:|:----:|:----:|
|base|x|0.8736|
|base|o|0.8954|

<br/>

### Augrahpy 다양한 증강 적용

    - texture, words, brightness 카테고리로 분할
    - 확률적으로 카테고리별 1개를 선택해 랜덤 적용

|Augmentation method|probability|f1-score|
|:----:|:----:|:----:|
|base|x|0.8954|
|augraphy|[0.3, 0.3, 0.5]|0.8991|
|augraphy|[0.2, 0.2, 0.5]|0.9093|