# Gradient Descent 의 문제점

사실 이건 2019년 선린 인공지능 동아리에서 경사하강법의 문제점을 조사해오라는 숙제였다. 레포지토리 정리를 하다 생각이 나서 정리해본다.

## Gradient Descent 란?

경사 하강법은 함수를 어떤 목적함수의 함수값을 최적회시키는 파라미터를 찾는 최적화(Optimization) 문제를 해결 하는 방법중 하나이다.

목적함수의 최소값 위치를 찾기 위해 비용 함수(Cost Function)의 그레디언트 반대 방향으로 정의한 step size를 가지고 조금씩 움직여 가면서 최적의 파라미터를 찾으려는 방법이다.

여기서 경사는 파라미터에 대해 편미분한 벡터를 의미하며 이 파라미터를 반복적으로 조금씩 움직이는 것이 관건이다.

하지만 이 경사하강법에는 두가지 문제점이 있다. 이 두가지의 문제점에 대해 정리 해보려 한다.

## Local Minima(Minimum) 문제

Optimizer는 비용 함수(Cost Function)에서 Global Minimun, 또는 Global Maximum 을 찾는 것이 목표이다.

하지만, Optimizer가 착각하여 수 많은 Local Minimum 중 Global Miminum 이 아닌 어떤 Local Minimum 을 찾는 경우가 있다.

왜냐하면, Optimizer 의 입장에서 당시에 경사를 따라 내려가서 찾은 Local Minimum 을 Global Minimum 으로 판단해버릴 수 있기 때문이다.

위키피디아에 있는 사진을 예로 가져오겠다.

![Wikipedia Local Extremum](https://upload.wikimedia.org/wikipedia/commons/thumb/6/68/Extrema_example_original.svg/440px-Extrema_example_original.svg.png)

Optimizer가 오른쪽에서 왼쪽의 방향으로 경사를 따라 내려가면서 오른쪽의 Local Mimimum 을 찾고, Global Maximum 을 지나야 Global Minimum 을 찾을 수 있지만, 이를 지나지 않고 Local Minimum 을 Global Minimum으로 착각하는 경우가 생기는 것 이다.

왜냐하면, Global Minimum에 도달하지 않았는데도, 어느 지점에 들어가니 평평형하고, 더 진행하려니 Loss 가 늘어나서 멈춰버리기 때문이다.

## Oscillation 문제

진동 문제는 Gradient Descent 에서 학습률이 높을 때에 최솟값 근처에서 왔다 갔다 하면서 시간을 낭비하는 현상을 Oscilllation (진동) 문제라 한다.


## 해결방안

위 두 개의 문제는 Momentum 방식을 통해 해결할 수 있다.

Momentum은 Gradient Descent 를 통해 이동하는 과정에서 '관성'을 주는 것이다. 과거에 이동했던 방식을 기억하면서, 그 방향으로 어느 정도를 추가적으로 이동하는 방식이다.

### Local Minima

Local Minima 에 빠지게 되면, Gradient가 0이 되어 이동할 수가 없지만, Momemtum 방식을 통해서, 기존에 이동했던 방향에 관성이 더해져서 Local Mimima 를 빠져나오고 Global Minima로 이동하는 것을 기대할 수 있다.

### Oscillation

SDG 가 최적점으로 이동하는 상황에서, 한번의 Step 에서 움직일 수 있는 Step Size 는 한계가 있으므로, 좌우로 계속 진동하는 경우가 있다고 가정하자.

Momemtum 방식을 통해서, 자주 이동하는 방향에 관성이 붙게 되고, 진동을 하더라도 최적점으로 가는 방향으로 더 가기 때문에 SDG 보다 빠르게 이동 할 수 있다.

### Momentum 의 문제점 ?

문제라 하기 보단, Momentum 을 사용 할 경우, 기존의 변수들인 ![epsilon](https://latex.codecogs.com/svg.latex?\epsilon) 외에도 과거에 이동했던 양을 저장해야 하는데, 변수에 대한 메모리가 기존의 두 배로 필요하게 된다는 점이 있다.

