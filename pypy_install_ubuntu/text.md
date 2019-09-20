### `ubuntu`에 `pypy` 설치하기

> `pypy` 공식 사이트 [[Link](http://pypy.org/)]  
> `Ubuntu`에 `pypy` 설치하기 [[Link](https://blog.naver.com/PostView.nhn?blogId=stop2y&logNo=221524935207&categoryNo=0&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=postView)]  
> `pypy` Library 호환성 리스트[[Link](http://packages.pypy.org/)]

#### 1. `python` vs `pypy`

* 먼저, 다음의 속도 차이를 봅시다.  

| **run by** | **python** | **pypy **|
|---|:---:|:---:|
|**std. out**|![python](/pypy_install_ubuntu/images/python.png)|![python](/pypy_install_ubuntu/images/pypy.png)  |
| **remark** | just started | finished|

`python`과 `pypy`는 각기 방금 계산을 시작한 것과 끝낸 상태의 차이가 있을 뿐, 동일한 코드 실행입니다.  
`python`은 113 시간이 걸릴 것이라고 엄살을 부리는 반면,  
`pypy`는 15분만에 계산을 끝내버렸습니다.  

#### 2. `pypy`는 왜 빠를까요?
