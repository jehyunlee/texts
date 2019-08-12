# 내 심층신경망에 맞는 최적 학습률 평가
> **원본 주소 :** https://towardsdatascience.com/estimating-optimal-learning-rate-for-a-deep-neural-network-ce32f2556ce0  
> **번역 철학 :** 매끄럽게 읽으실 수 있는 적절한 의역을 지향합니다.  
> **전문 용어 :** 가급적 <a href='http://taewan.kim/docs/ml_glossary/'>우리말 용어</a>를 사용하고자 하며, 원어를 병기합니다.  

<p align="center">
  <img src="./images/1_ymwavXYarjSn8OlTSIrr9A.jpeg">
  <br>
  Source : https://www.hellobc.com.au/british-columbia/things-to-do/winter-activities/skiing-snowboarding.aspx
</p>

<br>
학습률은 심층신경망을 학습시킬 때 조정하는 가장 중요한 하이퍼파라미터 중 하나다.  

본 글에서, 내가 <a href='http://www.fast.ai/'>fast.ai 딥러닝 과정</a>에서 배운 합리적인 학습률을 찾는 간단하면서도 강력한 방법으로 소개하고자 한다. 나는 이 과정의 새로운 버전을 <a href='https://www.usfca.edu/data-institute/certificates/deep-learning-part-one'>샌프란시스코 대학</a>에서 직접 수강하고 있다. 아직 일반 대중에게는 공개되지 않았지만, 올 연말께 <a href='http://course.fast.ai/'>course.fast.ai</a>를 통해 공개될 것으로 보인다. (현재는 작년 버전이 업로드되어 있다)  

