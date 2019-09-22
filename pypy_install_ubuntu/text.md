### `ubuntu`에 `pypy` 설치하기

> `pypy` 공식 사이트 [[Link](http://pypy.org/)]  
> `Ubuntu`에 `pypy` 설치하기 [[Link](https://blog.naver.com/PostView.nhn?blogId=stop2y&logNo=221524935207&categoryNo=0&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=postView)]  
> `pypy` Library 호환성 리스트[[Link](http://packages.pypy.org/)]  
> `pypy` 나무위키 설명 [[Link](https://namu.wiki/w/PyPy)]  

#### 1. `python` vs `pypy`

* 먼저, 다음의 속도 차이를 봅시다.  

| **run by** | **python** | **pypy**|
|---|:---:|:---:|
|**std. out**|![python](/pypy_install_ubuntu/images/python.png)|![python](/pypy_install_ubuntu/images/pypy.png)  |
| **remark** | just started | finished|

`python`과 `pypy`는 각기 방금 계산을 시작한 것과 끝낸 상태의 차이가 있을 뿐, 동일한 코드 실행입니다.  
`python`은 113 시간이 걸릴 것이라고 엄살을 부리는 반면,  
`pypy`는 15분만에 계산을 끝내버렸습니다. `python`에 비해 450배 정도 빠른 것입니다. 
<br>  

#### 2. `pypy`는 뭔가요?
1. `pypy`는 JIT(just-in-time) 컴파일하는 파이썬으로 개발되었습니다.  
2. `나무위키`에는 원리가 다음과 같이 정리되어 있습니다.  
> 1. 먼저 RPython이라고 하는, 파이썬 문법을 엄격하게 만들어 컴파일이 되게 만든 해석기(translate.py)를 Python 코드로 작성한다.  
> 2. RPython의 효과적인 컴파일을 위해 다른 언어로 툴체인을 만든다.  
> 3. Python 구현(런타임)을 RPython 해석기로 컴파일한다.  
> 4. 3에서 만든 구현을 1 또는 2에서 만든 RPython 해석기로 컴파일한다.  
> 5. 4로 만든 후보를 이전 또는 다른 구현과 비교(성능 측정), 만족스럽지 않으면 수정한다.(nightly builds)  
> 6. 5에서 만족스러운 결과를 냈다면 출시하고 1 또는 2부터 다시 시작한다.  
3. 그래서 로고가 자기 꼬리를 물고 있는 뱀(우로보로스)입니다.  
![logo](/pypy_install_ubuntu/images/pypy_logo.png)
3. `python`을 개발한 귀도 반 로썸 (Guide van Rossum)은 다음과 같이 말하고 있습니다.  
> "If you want your code to run faster, you should probably just use PyPy."
<br>  

#### 3. `ubuntu`에 `pypy` 설치하기.  
> 따라한 링크 : [Link](https://blog.naver.com/PostView.nhn?blogId=stop2y&logNo=221524935207&categoryNo=0&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=postView)

1. pypy 홈페이지에서 본인 환경에 맞는 버전을 다운받습니다.  
> http://pypy.org/download.html  

  * 필자는 `WSL`환경의 `Ubuntu 16.04`에서 `python 3.6`을 사용중이므로, 여기에 맞는 버전을 다운받습니다.
> https://bitbucket.org/pypy/pypy/downloads/pypy3.5-v7.0.0-linux64.tar.bz2  

2. 압축을 해제한 뒤에 파일을 아래 장소에 옮겨줍니다.  
> /usr/local/bin/**[pypy 폴더]**

3. 설치 시작.  
* 에러 메시지를 체크하면서, 해결하면서 진행합니다. 
* 저는 원 글의 명령을 실행 시 root 권한 문제(writing Permission error)가 있어 모든 줄에 sudo를 붙이고 실행했습니다.  
```bash
$ cd /usr/local/bin  
$ sudo ln -s /usr/local/bin/[pypy 폴더]/bin/pypy3 pypy3  
$ sudo curl -O http://python-distribute.org/distribute_setup.py  
$ sudo wget https://bootstrap.pypa.io/get-pip.py  
$ pypy3 distribute_setup.py  
$ pypy3 get-pip.py  
$ sudo ln -s /usr/local/bin/[pypy 폴더]/bin/pip pypy3-pip  
$ sudo ln -s /usr/local/bin/[pypy 폴더]/bin/easy_install pypy3-easy_install

# 선택사항  
$ sudo apt-get install upgrade  
$ sudo apt-get install update  
```
<br>  

#### 4. 실행해보기.
* 기존 `.py`파일을 그대로 실행할 수 있습니다.  
```bash
$ python3 test.py      하던 걸,
$ pypy3 test.py        로만 하면 됩니다.
```
<br>

#### 5. pypy 모듈 설치하기.  
* `python`에 설치된 모듈과 `pypy`에 설치된 모듈은 별개입니다.  
* 여러분의 `.py`코드에 설치한 라이브러리를 모두 `pypy`버전으로 설치해야 합니다.  
* 그런데 아직 `pypy`와 `python`이 100% 호환되지 않습니다. 필요한 라이브러리를 지원하는지 확인([Link](http://packages.pypy.org/))해보시기 바랍니다.  
* 예컨대 `tensorflow`는 `pypy`로 구동할 수 없습니다.
* 필자가 `pypy`를 처음 만났던 2015년에는 `numpy`를 지원하지 않아 `numpypy`라는 녀석을 설치하거나 `numpy`함수를 `scratch`레벨로 풀어서 코딩해야 했습니다만, 현재 `numpy`와 `pandas`를 모두 지원합니다.
* 설치는 다음과 같은 방식으로 가능합니다.  

```bash
$ pypy3 -m pip install numpy  
```
