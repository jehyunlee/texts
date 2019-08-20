# `Fast.ai` v0.7 사용을 위한 환경 설정
> [Hiromi Suenaga](https://medium.com/@hiromi_suenaga)의 `Fast.ai` [강의노트](https://medium.com/@hiromi_suenaga/machine-learning-1-lesson-1-84a1dc2b5236) 번역에 앞서, `Fast.ai` 0.7 설치를 위한 환경 설정이 필요합니다.  
> 본 글에서는 [공식 홈페이지](https://forums.fast.ai/t/moving-the-fastai-0-7-folder-do-not-use-pip-for-the-mooc/23667)를 따라 Fast.ai 강의노트 실행을 위한 환경 설정 방법을 안내하고,  
> 알려진 [0.7 이슈](https://forums.fast.ai/t/fastai-v0-7-install-issues-thread/24652)에 더해 필자가 겪은 주의사항을 함께 기술합니다.  
> 기본적으로 [공식 문서](https://forums.fast.ai/t/moving-the-fastai-0-7-folder-do-not-use-pip-for-the-mooc/23667)를 Ubuntu 16.04 기준에서 번역하였습니다.

`Fast.ai`는 현재 [v1](http://www.fast.ai/2018/10/02/fastai-ai/)이 공개되었는데, 밑바닥부터 새로 작성되었습니다.  
기존 튜토리얼에 사용된 코드들은 fastai/ 폴더에서 /old/fastai/ 폴더로 옮겨졌고 심볼릭 링크도 업데이트 되었습니다. 
`conda` 환경을 사용하신다면 모든 기능을 그대로 사용할 수 있고 아무런 문제가 없으실 겁니다.  
pip 버전은 v1에 맞추어 설정될 것이기 때문에 앞으로 사용이 불가능하며, 강의와도 호환성이 없습니다. 
<br>  

### [course.fast.ai](http://course.fast.ai/) 224 수강생 필독  
`course.fasta.ai`의 어떤 코스를 듣던 간에, 그냥 pip나 conda를 이용해서 fast.ai를 설치하지 마.십.시.오.  
공지된 설치방법은 v1 용인데 강의를 들으려면 v0.7이 필요합니다.  
강의용 v0.7을 설치하려면 `conda env update`가 필요한데, 자세한 방법은 아래에 설명하겠습니다. 여기엔 예제로 제공되는 노트북 파일이 정상 작동하기 위한 old/fastai/로의 심볼릭 링크가 포함되어 있습니다.  
<br>  

### `Fast.ai` v0.7 설치
