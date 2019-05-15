# Performance-Comparison-of-Natural-Language-Processing-Model-based-on-Deep-Neural-Networks

- 모델은 CNN, Bi-GRU, Bi-GRU+CNN까지 총 3가지입니다
- nsmc, IMDB, Reuters 말뭉치를 사용하여 3가지 모델을 학습해 정확도를 얻을 수 있습니다.
- CNN-rand, CNN-static, CNN-non-static 변수를 이용해 학습방법을 다르게 할 수 있습니다.
- IMDB와 Reuters말뭉치는 keras에서 제공하는 말뭉치를 사용했으며, nsmc는 직접 정제하여 사용했습니다.
- 크기별로 정제하는 코드는 load_data()함수에 있으며, nsmc말뭉치는 긍정적인 문장과 부정적인 문장을 각각 반씩 구성하여 5,000문장 말뭉치부터 25,000문장 말뭉치까지 따로 구성했습니다.

## 구현 환경
OS : Ubuntu 16.04
GPU : Titan xp
cuda & cudnn version : 10.01 / 7.0
Tool : Anaconda & Jupyter notebook

## Model Parameters
- filter_sizes 변수를 사용해 CNN의 필터의 크기를 바꿀 수 있습니다.
- dropout_prob 변수를 사용해 drop_out의 값을 조정할 수 있습니다.
- hidden_dims 변수를 사용해 hidden layer의 유닛의 개수를 정할 수 있습니다.

## Training parameters
- batch_size 변수를 바꿔 batch의 크기를 정할 수 있습니다.
- num_epochs 변수를 바꿔 학습 말뭉치의 학습 횟수를 정할 수 있습니다.



### 현재 이 코드는 오픈소스 https://github.com/fozziethebeat/S-Space 의 코드를 참고하여 논문의 실험에 맞게 바꾼것임을 알립니다.
