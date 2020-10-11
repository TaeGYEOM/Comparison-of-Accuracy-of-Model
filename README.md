# Performance Comparison of Natural Language Processing Model based on Deep Neural Networks

- 모델은 CNN, Bi-GRU, Bi-GRU+CNN까지 총 3가지입니다
- nsmc, IMDB, Reuters 말뭉치를 사용하여 3가지 모델을 학습해 정확도를 얻을 수 있습니다.
- CNN-rand, CNN-static, CNN-non-static 변수를 이용해 학습방법을 다르게 할 수 있습니다.
- IMDB와 Reuters말뭉치는 keras에서 제공하는 말뭉치를 사용했으며, nsmc는 직접 정제하여 사용했습니다.
- 크기별로 정제하는 코드는 load_data()함수에 있으며, nsmc말뭉치는 긍정적인 문장과 부정적인 문장을 각각 반씩 구성하여 5,000문장 말뭉치부터 25,000문장 말뭉치까지 따로 구성했습니다.

## 구현 환경
- OS : Ubuntu 16.04
- GPU : Titan xp
- cuda & cudnn version : 10.01 / 7.0
- Tool : Anaconda & Jupyter notebook, Tensorflow, Keras
- Language : Python

## Data processing
- 언어차이에 따른 딥러닝 모델의 성능비교를 위해 한글 영화리뷰 말뭉치(NSMC, 네이버영화리뷰)와 영문 영화리뷰 말뭉치(IMDB)를 사용했습니다. 
- 이진분류 문제와 다중분류 문제에서 성능비교를 위해 46개의 토픽으로 분류되어 있는 Reuters 말뭉치를 추가했습니다.
- 모든 데이터는 띄어쓰여진 단어를 기준으로 Tokenization을 실시했고, 한글과 영어 그리고 ?!@#$%^&*()'".,를 제외한 다른문자가 문장에 포함되어있을경우 삭제시켰습니다.
- 데이터를 학습하기 위해서는 같은 크기의 입력이 필요합니다. 하지만 문장은 모두 같은 길이를 가질 수 없기 때문에 가장 긴 문장을 기준으로 더 짧은 문장들은 padding을 사용해 늘렸습니다.
- 이후 말뭉치 속 단어들에 각각 ID값을 부여했습니다. 각자의 ID값을 가진 단어들을 사전으로 정리하고, 모델 학습을 위해 단어 단위 skip-gram 방식을 사용해 임베딩시켰습니다.

## Data structure
-NSMC: 네이버 영화 리뷰 말뭉치로 150,000개의 문장으로 이루어져 있으며 실험에서는 15,000개의 문장을 분리해 135,000개의 학습말뭉치와 15,000개의 평가말뭉치로 구성하여 사용했습니다. 문장마다 긍정적인 문장이면 1, 부정적인 문장이면 0이 라벨링 되어있습니다.
-IMDB: 영어로 된 영화 리뷰 말뭉치로 25,000개의 학습말뭉치와 25,000개의 테스트말뭉치로 나뉘어 있습니다. 긍정적인문장과 부정적인 문장이 분리되어 있으며, 각 문장별로 긍정은1, 부정은 0으로 라벨링 하여 사용했습니다.
-Reuters: : 영문 뉴스 기사 말뭉치로 원본 로이터 말뭉치의 135개 토픽 중 샘플이 많은 순서대로 총 46개의 토픽을선정해 만든 말뭉치를 사용했습니다. 1부터 46까지의 숫자로 문장별 라벨링이 되어있습니다.

## Model
- 성능비교를 위한 모델은 총 3가지로 CNN과 Bi-GRU 그리고 CNN과 Bi-GRU를 앙상블한 모델을 사용했습니다.
- filter_sizes 변수를 사용해 CNN의 필터의 크기를 바꿀 수 있습니다.
- dropout_prob 변수를 사용해 drop_out의 값을 조정할 수 있습니다.
- hidden_dims 변수를 사용해 hidden layer의 유닛의 개수를 정할 수 있습니다.
- 모델은 Static과 Non-static으로 구분됩니다. Non-static은 각 모델들이 학습중에 임베딩된 단어 벡터들도 함께 학습됩니다. 반면에 Static은 학습되지 않습니다.

## Training
- batch_size 변수를 바꿔 batch의 크기를 정할 수 있습니다.
- num_epochs 변수를 바꿔 학습 말뭉치의 학습 횟수를 정할 수 있습니다.


