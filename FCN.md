#Fully Convolution Networks for Semantic Segmentation

***Whale Identification***

- pixel 단위 classification 문제 : 계산량의 문제, global information 을 사용하지 못하고 window 제한된 영역의 local information 만 사용한다.
  -> local feature , global feature 모두 사용하고, 계산량의 상당량을 차지하는 fully connected layer 없앤 CNN architecture 제안

- 네트워크 구조 
(1) Feature Extraction 
    일반적인 CNN 구조의 convolution layers
(2) Feature-level Classification
    추출된 Feature map 의 pixel 하나하나마다 classification 수행. 
(3) Upsampling 
    backward strided convolution 을 통해 upsampling 하여 원래 image size로 키워준다.
(4) Segmentation 
    각 class의 upsampling 된 결과를 사용하여 하나의 segmentation 결과 이미지 만들어준다.

