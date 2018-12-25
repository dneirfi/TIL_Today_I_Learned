# LeNet-5

> CNN고전이라 부를 수 있는 LeNet-5 
  LeCun 교수님이 1998년에 만든 모델, 6개의 hidden layer

  1. Input - 32x32x1. 흑백 이미지. (필터 5x5, stride 1)
  2. C1 -  28x28x6. feature maps 6개. (필터 2x2, subsampling)
  3. S2 - 14x14x6. feature maps 6개. (필터 5x5, stride 1)
  4. C3 - 10x10x16. feature maps 16개
  5. S4 - 5x5x16. feature maps 16개.
  6. C5 - FC(Full Connection )120개
  7. F6 - FC(Full Connection) 84개
  8. Output - GC(Gaussian Connections) 10개. (최종 분류)

> LeNet-1 때는 컴퓨팅 능력이 아무래도 떨어지니까 parameter 수가 작은 망을 개발

> Convolution kernel 개수 늘리고, fully-connected layer크기 키우고, input image 크기 키우는 방향으로 
  LeNet-1 에서는 16x16 크기로 샘플 이미지 크기를 줄인 후 28x28 중앙에 위치
  LeNet-5 에선ㄴ 28x28 이미지를 32x32 중앙에 위치시켰다.
  -> 좀 더 큰 크기의 영상을 사용해 down-size 영상보다 디테일에 대한 고려가 많아지고 성능도 우수해졌다.

> Convolution layer 3, Sub-sampling 2 , fully-connected layer 1
  convolution 뒤에 sub-sampling 으로 인해 영상 크기가 1/4로 줄어든다.
  zero-padding 지원하지 않아서 boundary정보가 사라진다. 
  Convoution kernel 의 parameter는 사전에 결정x , 학습으로 최적의 결과 결정 

