# AI 연구원, 머신러닝이 연금술에 불과하다고 역설
> **원본 주소 :** https://www.sciencemag.org/news/2018/05/ai-researchers-allege-machine-learning-alchemy  
> **번역 철학 :** 매끄럽게 읽으실 수 있는 적절한 의역을 지향합니다.  
> **전문 용어 :** 가급적 <a href='http://taewan.kim/docs/ml_glossary/'>우리말 용어</a>를 사용하고자 하며, 원어를 병기합니다.  
<br>

<p align="center">
<img src='https://github.com/jehyunlee/texts/blob/master/AI_researchers_allege_that_machine_learning_is_alchemy/images/ma_0504_NID_alchemy_WEB.jpg'><br>  
3D 공간의 최소값을 찾는 알고리즘에서, 경사하강법은 시행착오에 기반한 최적화를 수행한다.
</p>
<br>  

지난 12월, 캘리포니아의 샌프란시스코에 있는 구글(Google)에서 AI 연구원으로 일하는 Ali Rahimi가 날린 한 방에 박수세례가 40초간 이어졌다. 한 AI 컨퍼런스에서 머신러닝 알고리즘이 시행착오를 통해 학습하는 [일종의 연금술이 되었음](http://www.argmin.net/2017/12/05/kitchen-sinks/)을 폭로한 것이다(본 글에서는 **연금술**이라는 단어가 '체계적인 지식이나 접근법 없이, 되면 좋고 안되면 말고 식으로 결과를 운에 맡기고 이런 저런 시도를 반복하는 행태'를 가리키는 데 쓰였다: 역자 註). Rahimi에 따르면 연구원들은 왜 어떤 알고리즘은 작동하고 다른 알고리즘은 작동하지 않는지 알지 못하며, 다른 것들을 제치고 특정한 AI 아키텍처를 선정하는 견고한 기준선이 없다. 4월 30일 캐나다 밴쿠버에서 열린 International Conference on Learning Representations에서 Rahimi와 동료들은 그들이 어떤 행위들을 연금술로 간주하는지에 대한 [사례를 공개하고](https://openreview.net/forum?id=rJWF0Fywf), AI의 신뢰성을 강화하는 방법을 제시했다.  

> Rahimi는 이렇게 말했다.  
> "이 분야는 고뇌를 피할 수 없습니다. 우리 중 대다수가 외계 기술을 다루는 것 같은 느낌을 받아요."  

이 이슈는 [AI의 재현성 문제](http://science.sciencemag.org/content/359/6377/725)(실험 및 출판 사례에서 일관성이 결여되어 서로의 연구를 재현하지 못하는 문제)와는 별개의 것이고, 흔히 말하는 머신 러닝의 '블랙 박스' 또는 '설명력' 문제([특정 AI가 어떻게 이 결론에 이르렀는지 설명](http://science.sciencemag.org/content/357/6346/22)하는데 어려움을 겪는 문제)와도 다르다. Rahimi가 말하듯, "블랙 박스인 머신 러닝과 블랙 박스가 되어버린 어떤 총체적 분야 사이에 경계선을 긋고자 한" 것이다.  

Rahimi는 연구자들이 마치 중세의 연금술사들처럼 새로운 알고리즘을 구축하고 훈련시키는데 필요한 기본 도구에 대한 깊은 이해 없이 AI를 만들어내고 있다고 말한다. 캘리포니아 마운틴 뷰에 있는 구글의 컴퓨터 과학자 프랑소와 숄레(François Chollet)는 이렇게 덧붙인다. "사람들은 화물 숭배(caro-cult: 동남아 원주민들이 2차 세계대전 중 미국과 일본의 전투기가 화물을 나르는 것을 보고, 죽은 조상들이 특별한 화물을 가지고 올 것이라고 믿는 현상: 역자 註) 같은 것에 끌립니다. 전통 신앙이나 마법의 주문 같은 것 말입니다." 예를 들면, 연구원들은 AI의 학습률(learning rate)를 조정하기 위해 일단 뭐라도 시도해보고, 결과가 신통찮으면 값을 바꿔보는 식의 방법을 사용한다. 이 때 왜 어떤 값이 다른 값보다 좋은지에 대한 이해는 없다. 한편으로는 AI 연구원들은 그들의 알고리즘을 어둠 속에서 더듬거리며 학습시키기도 한다. 실패를 최소화하기 위해 알고리즘의 파라미터에 소위 "확률적 경사하강법(stochastic gradient descent)"이라는 것을 적용하는 식이다. 해당 주제에 대한 수천건의 학술 논문과 그 방법들을 적용하기 위한 셀 수 없는 방법들이 있음에도 불구하고, 여전히 시행착오에 의존하고 있는 것이다.  

Rahimi의 논문은 발생할 수 있는 노력의 낭비와 최적화 실패에 집중하고 있다. 예를 들어, 첨단(state-of-the-art)의 번역 알고리즘에서 대부분의 복잡성을 벗겨내면, 결론은 영어를 독일어로 또는 프랑스어로 더 잘, 그리고 효율적으로 번역한다는 것 뿐이고 논문의 저자들은 부가적인 부분들이 어디에 좋은지 완전히 파악하지는 못하고 있다. 역으로 말하자면, 논문에 소위 있어 보이려고 덧붙인 부분들이 그 논문에서 유일하게 좋은 부분이라고 Ferenc Huszár (런던의 트위터 머신러닝 연구원)은 말하고 있다. 어떤 경우에 알고리즘의 코어 부분은 기술적으로 결함이 있는데 "순전히 여기 들러붙은 잔기술들 덕택에" 좋은 결론이 나온다는 것이다.  

Rahimi는 언제 어떤 알고리즘이 가장 잘 작동하는지에 대한 몇 가지의 제안을 하고 있다. 초심자들에게는 앞서 언급한 번역 알고리즘의 경우와 같이 "어블레이션 연구(ablation studies)"를 적용해야 한다고 한다. 각 부분의 기능을 확인하기 위해 알고리즘을 한 부분 한 부분 제거하면서 실행하는 방식을 말한다. 한편 알고리즘의 성능을 상세하게 분석해서 어떤 부분에서의 개선이 다른 곳에서는 비용으로 작용하는지 들여다보는 "분할 분석(sliced analysis)"을 요구한다. 또한 연구자들이 자신의 알고리즘을 많은 경우의 조건과 세팅에서 시험하고 그 성능을 모두 보고해야 한다고 주장하기도 한다.  

University of California, Berkeley의 컴퓨터 과학자이자 Rahimi의 연금술 기조 강연의 공저자인 Ben Recht는, AI는 문제를 작은 'toy problem'으로 축소해서 고민하는 기법을 물리학자들에게서 빌려올 필요가 있다고 한다. "물리학자들이 현상에 대한 설명을 이끌어내기 위한 간단한 시험을 창안하는 것을 보면 놀랍습니다". 어떤 AI 연구자들은 이미 이런 방법에 대해 논의를 시작하고, 영상 인식 알고리즘의 내부 작동원리를 더 잘 이해하기 위해 손으로 쓴 작은 흑백 글자를 대용량 컬러 사진에 앞서 넣어보기도 한다.  

런던의 DeepMind 컴퓨터 과학자인 Csaba Szepesvári는 테스트 경쟁을 좀 완화할 필요가 있다고 말한다. 그는 현재 새 알고리즘이 다른 벤치마크를 능가했을 때가 소프트웨어의 내부 알고리즘을 강조했을 때보다 더 쉽게 출판되고 있다고 꼬집는다. "과학의 목적은 지식의 생성입니다. 여러분은 다른 이들이 가져다가 반석으로 삼고 싶은 뭔가를 만들고 싶을 겁니다."  

Rahimi와 Recht의 비판에 모두가 동의하는 것은 아니다. 뉴욕의 Facebook 최고위 AI 과학자인 Yann LeCun은 너무 많은 관심이 최첨단의 기술에서 핵심(core)으로 옮겨가는 것은 혁신을 늦추고 AI의 실제 적용을 위축시킬 수 있다고 지적한다. "연금술이 아닙니다. 엔지니어링이죠. 엔지니어링은 원래 지저분한 겁니다."  

Recht는 체계적인 연구와 모험적인 연구가 공존하는 곳을 추구한다. "우리에겐 모두가 필요합니다." "우리가 튼튼한 시스템을 만들려면 어디에서 실패가 일어나는지 이해해야 하고, 더 인상적인 시스템을 만들려면 기술의 최전선을 더 앞으로 밀고 가야 합니다."

