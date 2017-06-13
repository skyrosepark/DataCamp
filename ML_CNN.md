
[수식없이 이해하는 CNN(Convolution Neural Network)과 RNN(Recurrent Neural Network)|작성자 zzozzo](http://horajjan.blog.me/220989551317)

'최신 인공지능, 쉽게 이해하고 넓게 활용하기' 인용

딥러닝의 사고나 기법은 새로운 것이 아닙니다. 그럼 왜 최근 몇 년동안 급격하게 딥러닝이 주목받게 된 것일까요?

#### 딥러닝의 과제인 '과적합'(over-fitting)의 회피
'구글의 고양이', 'DQN', '알파고'와 세계적인 이미지 대회인 'ILSVRC'에서도 딥러닝이 좋은 성적을 거뒀습니다. 이 정도의 성과를 올리기 시작한 배경에는 돌파구라고 할 만한 기술적인 진전이 있었습니다. 컴퓨터ㅣ 성능이 향상됐고 빅데이터를 이용할 수 있게 됐으며, 또 딥러닝 특유의 과제인 '과적합'을 회피할 수 있었던 것입니다
심층 신경망(Deep Learning)은 중간층을 다층화시켜 더욱 깊게 사고할 수 있습니다. 다층이 될수록 뉴런 처리와 전달, 산출되는 특징값이 늘어나며 이에 따라 답의 정확도가 올라갈 것이라는 사실은 이전부터 연구된 것입니다
'과적합'(over-fitting)이라고 불리는 문제는 심층 신경망을 마구잡이로 다층화해 파라미터의 수가 너무 많아질 때 발생하기 쉽다고 합니다. 과적합의 영향으로 인한 악영향으로 낯익은 훈련 데이터에는 정확도가 높은 답을 할 수 있는 한편, 훈련 데이터가 없는 미지의 데이터인 경우 정밀도가 내려가는(훈련 데이터의 영향을 너무 많이 받음) 현상이 있습니다. 즉, 훈련할 때는 성적이 좋았는데 실전에 가서는 성과를 내지 못하는 상태를 말합니다. 이것은 범용성이 부족하다는 과제를 낳았고 딥러닝에게는 정체기라고도 할 수 있는 시간을 불러왔습니다

#### 합성곱 신경망(CNN, Convolution Neural Network)
이 과제의 구체적인 해결책이 바로 '합성곱 신경망' 또는 '컨볼루션 신경망'(CNN)입니다
뉴런이 많고 복잡해지면 원래는 아무 관계도 없던 결합이 늘어나고 그것이 결국 악영향을 미쳐 '과적합'의 원인을 만들기도 합니다. 기계 정답률을 올리려면 층을 늘리는 한편 '아무 관계도 없는 결합을 끊어내는' 것이 중요합니다
또한 '오차역전파법'(Backpropagation)에 의해 출력 쪽에서 오차를 확인하게 하는 방법도 소개한 바 있는데, 모두 결합한 후 다층으로 만든 상태에서 오차역전파법을 써버리면 오차 전파가 분산되어 전혀 학습이 진전되지 않기 때문에 그 사태를 피하기 위해서는 아무 관계도 없는 결합을 잘라 버려야 한다는 이론도 있습니다.

'합성곱 신경망'의 특징 중 하나가 아무 관계도 없는 결합을 잘라 관계성이 높은 결합을 남긴다는 것입니다. 실제로 합성곱 신경망에서는 파라미터의 수가 격감하며 많은 경우에서 성과가 향상됩니다

그럼 '합성곱 신경망'이란 어떤 구조로 돼 있을까요? 자세히 이해하고 싶다면 기술자용 전문서를 읽어보는 것을 권장하고 싶지만 그 특징을 나타내자면 아래 그림과 같습니다. 이미지 분석을 예로 들어 설명해 보겠습니다
이미지의 정보를 뉴런에 전달할 때 이미지의 일부 범위로 좁혀서 분석하고 그 범위를 조금씩 잘라내며 분석을 반복합니다. 펭귄 이미지를 예로 들자면, 이미지의 왼쪽 끝에서 특정한 픽셀 수로 일부 범위를 잘라 정보를 분석한 후 그 창을 미끄러뜨리듯 다음 범위로 이동해 분석하는 과정을 반복하며 전체 모습을 분석해 나가는 것입니다

이것은 이미지로 말하자면 공간을 파악하는 효과도 동반합니다. 예를 들어, 아래 그림과 같이 멀리 떨어진 영역인 A와 Z는 관계성이 희박해서 A와 Z를 결합한다고 해도 정답을 도출하는 데는 별 도움이 되지 않습니다기존의 딥러닝에서는 A의 영역 정보도 B의 영역 정보고 모두 다음 층의 똑같은 뉴런으로 전달했습니다. 여기서 A의 영역 정보는 A와 관계가 깊은 뉴런으로, B의 영역 정보는 B와 관계가 깊은 뉴런에만 전달합니다. 이는 층간 결합을 제한하게 하는데, 이에 따라 오차역전파법의 효율도 올라가고 학습 성과도 올라가는 경우를 많이 볼 수 있게 됐습니다. '정답을 도출하기 위해 관계가 없는 결합을 자른' 것입니다
위와 같이 합성곱 신경망으로 머신러닝과 딥러닝에 의한 성과가 크게 향상되었습니다.

#### 순환 신경망(RNN, Recurrent Neural Network)
최근에는 '순환 신경망'(RNN)이 주목받고 있습니다
기존의 신경망은 '정적 데이터'로 취급하는 게 잘 어울렸기 때문에 '동적 데이터'는 익숙하지 않다고만 여겨져 왔습니다. 정적 데이터란 움직임이 없는, 혹은 움직임이 적은 데이터를 말하는데 예를 들면, 정지 화면, 텍스트, 수치, 최신 통계 데이터 같은 것이 여기에 해당합니다. 개와 고양이의 이미지를 식별하는 것은 정적 데이터입니다

한편 동적 데이터란 움직임이 큰, 또는 시간적인 상관관계가 중요한 데이터와 시계열 데이터 등을 말합니다. 대화, 동영상, 음성, 시계열의 통계 데이터와 로그 데이터 같은 것들 말입니다. RNN은 이러한 시계열 분석을 가능하게 만들어 준 동적 데이터와 호환되는 딥러닝입니다. 최근 자연어 대화 등의 분야에서 성과가 올라가고 있는 만큼 향후 RNN을 이용한 많은 성과들이 나타날 것입니다.