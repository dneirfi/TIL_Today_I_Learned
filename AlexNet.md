# AlexNet

1. 특징
   Overlapping Pooling 사용,  ReLU , Local Response Normalization , GPU연산을 고려해 두 개의 병렬 네트워크로 구성
   **Overlapping Pooling Layer**  
    Pooling layer는 겹치지 않게 적용하는 것이 일반적인데 여기서는 stride를 좁혀 Overlapping 하도록 설정했다. 0.4%의 정확도 향상이 되지만 Overlapping을 사용하면 연산량이 증가한다  
   **ReLU**  
   **Local Response Normalization**  
    활성함수를 적용하기 전 Normalization을 적용해 일반화 능력을 높였다. 1.4% 정확도 향상 but, 이 후 VGG Network에서 이를 반증한다. 계산량만 늘어날뿐 실제 효과가 없음을 실험을 통해 확인한다.
   **Dropout**  
    1~2번째 Fully-Connected Layer에 50% Dropout 사용. Overfitting줄여준다.

2. 구조
    8개의 레이어 
    Convolution layer 5, Fully-Connected layer 3
    병렬레이어들은 하나의 이미지에 대해 각각 독립적으로 특징 추출하여 필터들을 학습시킨다.
    첫번째 레이어에서 학습된 필터를 visualize하면 상단의 네트워크는 주로 *Non-Color Feature* , 하단의 네트워크는 주로 *Color Feature* 를 학습하였다. 
    세번째 레이어는 예외적으로 이전 단계의 두 병렬 레이어들로부터 모든 필터들을 받아오는데 이것은 병렬 학습으로 인해 두 필터군의 특징 연관성이 떨어지지 않게 하기 위해 중간에 Feature들을 섞어주려고 한 것같다.

3. 결론 
   딥러닝에 GPU사용을 고려한 최초의 모델.
   많은 파라미터 수가 필요한 구조 
