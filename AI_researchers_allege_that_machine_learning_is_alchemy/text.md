# AI 연구원, 머신러닝을 연금술이라고 주장
> **원본 주소 :** https://www.sciencemag.org/news/2018/05/ai-researchers-allege-machine-learning-alchemy  
> **번역 철학 :** 매끄럽게 읽으실 수 있는 적절한 의역을 지향합니다.  
> **전문 용어 :** 가급적 <a href='http://taewan.kim/docs/ml_glossary/'>우리말 용어</a>를 사용하고자 하며, 원어를 병기합니다.  
<br>

![SGD](https://github.com/jehyunlee/texts/blob/master/AI_researchers_allege_that_machine_learning_is_alchemy/images/ma_0504_NID_alchemy_WEB.jpg)  
3D 공간의 최소값을 찾는 알고리즘에서, 경사하강법은 시행착오에 기반한 최적화를 수행한다.

<br>  

캘리포니아의 샌프란시스코에 있는 구글(Google)에서 AI 연구원으로 일하는 Ali Rahimi는 지난 12월 강렬한 한 방을 날리고 40초간 이어지는 박수세례를 받았다. AI 컨퍼런스에서 시행착오를 통해 학습하는 머신러닝 알고리즘이 [일종의 연금술이 되었음](http://www.argmin.net/2017/12/05/kitchen-sinks/)을 발표한 것이다. Rahimi에 따르면 연구원들은 왜 어떤 알고리즘은 작동하고 다른 알고리즘은 작동하지 않는지 알지 못하며, 다른 것들을 제치고 특정한 AI 아키텍처를 선정하는 견고한 기준선이 없다. 4월 30일 캐나다 밴쿠버에서 열린 International Conference on Learning Representations에서 Rahimi와 동료들은 그들이 연금술 문제에서 무엇을 보는지에 대한 [사례를 공개하고](https://openreview.net/forum?id=rJWF0Fywf), 그리고 AI의 신뢰성을 강화하는 방법을 제시했다.  

> Rahimi는 이렇게 말했다.  
> "이 분야는 진짜 고통스럽습니다. 우리 중 대다수가 외계 기술을 다루는 것 같은 느낌을 받아요."  

이 이슈는 실험 및 출판 사례에서 일관성이 결여되어 서로의 연구를 재현하지 못하는 [AI의 재현성 문제](http://science.sciencemag.org/content/359/6377/725)와는 별개의 것이고, [특정 AI가 어떻게 이 결론에 이르렀는지 설명](http://science.sciencemag.org/content/357/6346/22)하는데 어려움을 겪는, 흔히 말하는 머신 러닝의 '블랙 박스' 또는 '설명력' 문제와도 다르다. Rahimi가 말하듯, "블랙 박스인 머신 러닝과 블랙 박스가 되어버린 총체적 분야 사이에 경계선을 긋고자 한" 것이다.  

Rahimi는 연구원들이 중세의 연금술사들처럼 새로운 알고리즘을 구축하고 훈련시키는데 필요한 기본 도구에 대한 깊은 이해 없이 AI를 만들어내고 있다고 말한다. 캘리포니아 마운틴 뷰에 있는 구글의 컴퓨터 과학자 프랑소와 숄레(François Chollet)는 이렇게 덧붙인다. "사람들은 화물 숭배(caro-cult: 동남아 원주민들이 2차 세계대전 중 미국과 일본의 전투기가 화물을 나르는 것을 보고, 죽은 조상들이 특별한 화물을 가지고 올 것이라고 믿는 현상: 역자 註) 같은 것에 끌립니다. 전통 신앙이나 마법의 주문 같은 것 말입니다." 예를 들면, 연구원들은 AI의 학습률(learning rate)를 조정하기 위해 일단 해보고, 결과가 신통찮으면 값을 바꿔보는 식의 방법을 사용한다. 왜 어떤 값이 다른 값보다 좋은지 모른 채로. 또 다른 경우에서, AI 연구원들은 그들의 알고리즘을 어둠 속에서 더듬거리며 학습시킨다. 실패를 최소화하기 위해 알고리즘의 파라미터를 "확률적 경사하강법(stochastic gradient descent)"인지 뭔지를 적용하는 식이다. 해당 주제에 대한 수천건의 학술 논문과 그 방법들을 적용하기 위한 셀 수 없는 방법들이 있음에도 불구하고, 여전히 시행착오에 의존하고 있는 것이다.  

