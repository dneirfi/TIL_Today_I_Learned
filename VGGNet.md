d="vggnet">VGGNet</h2>

<ol>
<li><p>개요 <br>
VGG는 Oxford University에서 개발되었으며, 2014 ImageNet Challenge에서 GoogLeNet에 근소한 차이로 밀려 아쉽게 2위를 차지한 네트워크이다. 우승작에 비해 굉장히 <em>간단한 구조</em>로 이루어져 있음에도 큰 차이를 보이지 않는 높은 성능을 냄으로써 신경망의 깊이가 딥러닝의 정확도에 큰 영향을 미친다는 것을 보여준다.</p></li>
<li><p>구조 <br>
<img src="https://cdn-images-1.medium.com/max/1600/1*0Tk4JclhGOCR_uLe6RKvUQ.png" alt="vgg구조" title=""> <br>
<img src="http://nmhkahn.github.io/assets/Casestudy-CNN/vgg-arch1.png" alt="vgg구조2" title=""> <br>
입력 : 224x224의 고정된 RGB 이미지, 트레이닝 셋 전체의 RGB 채널 평균 값을 입력 이미지의 각 픽셀마다 substract하여 입력을 zero-centerd되게 한다. <br>
구조 : 8~16 Convolutional Layer + 3 Fully-Connected Layer</p>

<ul><li>Convolutional Layer (3x3 filter, stride = 1, padding = True) : 레이어 갯수에 변화를 주어가며 정확도에 대한 신경망 깊이의 영향력을 실험했고, 패딩을 적용해 이미지 사이즈 유지</li>
<li>Max-Pooling Layer (2x2 filter, stride = 2) : 5장을 사용했으며, 겹치치 않으므로 특징 맵을 1/4로 줄여줌</li>
<li>1x1 Conv Layer (1x1 filter, stride = 1) : 차원축소로 인한 연산량 감소가 목적</li>
<li>Fully-Connected Layer (4096 -&gt; 4096 -&gt; 1000) : 세 장으로 고정된 FCL 사용</li></ul></li>
<li><p>특징</p>

<ul><li><p>모든 Convolution layer에 3x3필터 적용 </p>

<ol><li>파라미터 수를 줄일 수 있기 때문이다</li>
<li>여러 개의 ReLU non-linear를 사용할 수 있다 : 큰 필터를 작은 필터 여러개로 나누었기 때문에 들어 갈 곳이 더 많아진다 = decision function 이 더 discriminative 하다는 의미</li>
<li>학습해야할 weight의 수가 많이 줄어든다. 비교를 위해 3x3 conv 레이어 3 개와 7x7 conv 레이어 1 개가 있다고 가정하자. 이 때 두 레이어 모두 C개의 채널을 가진다. <br>
두 레이어의 parameter의 개수를 계산해보자. 7x7 conv 레이어의 parameter의 개수는 72C2=49C2이다. 3개의 3x3 conv 레이어는 3∗(32C2)=27C2 이다. 당연하게도 학습해야할 parameter의 개수가 적다면 regularization 측면에서 큰 이점을 보인다.</li></ol></li>
<li><p>1x1 Convolution layer사용 : GoogleNet 과 마찬가지로 <em>Network in Network</em> 에 영향을 받음, 연산량 감소보다는 의사결정함수에 Non-linearity를 부여할 목적으로 사용됨.</p></li>
<li><p>다섯개의 Max Pooling layer 사용</p></li></ul></li>
</ol>

<blockquote>
  <p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>
