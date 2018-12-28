d="resnet">ResNet</h2>

<ol>
<li><p>Skip Connection <br>
<img src="https://datascienceschool.net/upfiles/6182312059774a81a2a26246bd4e83f2.png" alt="배경" title=""> <br>
ResNet 에서는 H(x)-y를 최소화 하는 방향이 아닌 네트워크가 H(x)-x를 얻는 것으로 목표를 수정하였다. 입력과 출력의 잔차를 F(x)=H(x)-x라고 정의를 하고 네트워크는 이 F(x)를 찾는 것이다. 이 F(x)는 잔차라고 할 수 있고, 이렇게 잔차를 학습하는 것을 Residual learning, Residual mapping이라고 한다. 결과적으로 출력 H(x)=F(x)+x가 된다. 이렇게 네트워크의 입력과 출력이 더해진 것을 다음 레이러의 입력으로 사용하는 것을 Skip connection 이라고 한다. 기존의 뉴럴넷은 H(x)가 어떻게든 정답과 같게 만드는 것이 목적이었다면, 이제 입력과 출력 사이의 잔차를 학습하는 것, 즉 최적의 경우 F(x)=0이 되어야하므로 학습의 목표가 이미 정해져 있기 때문에 학습 속도가 빨라질 것이고, 네트워크가 잔차를 학습하고 나면, 입력값의 작은 변화에도 민감하게 반응 할 것이다라는 것이 ResNet의 가설이다. <br>
<em>Skip connection을 구현 하는 것은 덧셈 연산의 추가 만으로 가능하다. 이는 추가적인 연산량이나 파라미터가 많이 필요하지 않다. 또한 Back propagation 시에는 gradient가 잘 흘러갈 수 있게 해준다는 장점도 있다.</em></p></li>
<li><p>구조 <br>
<img src="https://datascienceschool.net/upfiles/2e104ff279804e839cef46fc58ef16e7.png" alt="구조1" title=""> <br>
입력  (224,224,3) <br>
ResNet의 모델 설계는 첫번째 레이어(7x7 convolution)를 제외하고는 모든 convolution 연산에 3x3 이하 크기의 커널이 사용되었고, 피쳐맵의 크기가 같은 레이어는 출력 피쳐맵 갯수가 동일하다. 그리고 피쳐맵의 크기가 반으로 작아지는 경우 출력 피쳐맵의 갯수가 2배가 된다. pooling은 거의 사용되지 않고 convolution 연산의 스트라이드를 2로 하여 피쳐맵의 크기를 줄였다. 이미지가 반으로 작아진 경우, Identity Block이 사용되며, 입력값을 바로 더하지 않고, 1x1 convolution 연산을 스트라이드 2로 설정하여 피쳐맵의 크기와 갯수를 맞추어준 다음 더해준다. 이를 projection shortcut이라고도 한다.</p></li>
</ol>

<blockquote>
  <p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>
