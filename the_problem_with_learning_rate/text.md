# Learning Rate 관련 문제
> 원본 : https://iconof.com/1cycle-learning-rate-policy/

Deep Neural Network (DNN)은 어려운 전역 최적화 문제다. 
Learning Rate (LR)은 DNN 학습 조정에 결정적인 hyper-parameter인데, learning rate가 작으면 학습이 느려지고 너무 큰 값을 취하면 loss function 수렴이 어려워져 최소값 근처를 맴돌기만 하거나, 심지어 발산하기도 한다.

![Small LR](./images/lr_low-81d04746df552258b87b24e2e3da17a5.gif)
