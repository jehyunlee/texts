## New Features in Pandas 1.0

<p align="center">
  <img src='1-pandas1.png'>
</p>

* Pandas 1.0이 출시되고 일부 feature가 사라졌고(deprciated) 새로운 기능이 추가되었습니다.
* 새로 추가된 기능 중에는 사용자들이 기다리던 기능이 많습니다.
<br>

* 기존 코드 동작에 문제가 생길까봐 설치를 망설였지만  
  (1) `markdown`출력이 내장되었고 - 기존엔 이 기능이 없어서 수동으로 만들어 썼습니다.  
  (2) pip install의 기본값이 1.0으로 변경된 것을 보고 더 이상 미룰 수는 없다고 생각했습니다.  
  (3) [Deprications](https://dev.pandas.io/docs/whatsnew/v1.0.0.html#deprecations)에 제가 쓰는 기능이 거의 없습니다.  

<b> References </b>
> [What's new in 1.0.0 (pandas official)](https://dev.pandas.io/docs/whatsnew/v1.0.0.html#converting-to-markdown)  
> [Deprications](https://dev.pandas.io/docs/whatsnew/v1.0.0.html#deprecations)  
> [What's new in Pandas 1.0?](https://towardsdatascience.com/whats-new-in-pandas-1-0-ffa99bd43a58)  
> [Towards pandas 1.0](https://medium.com/@initialkommit/%EB%B2%88%EC%97%AD-towards-pandas-1-0-865296b65a5)  
> [pandas.DataFrame.convert_dtypes](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.convert_dtypes.html?highlight=convert_dtypes)
<br>


### 0. pandas 1.0을 맞이할 준비
* pandas 1.0을 사용하기 위해서는 python version이 3.6.1 이상이어야 합니다.

* pandas를 처음 맞이하는 분은 아래와 같이 설치하면 됩니다.  
  ```python
  pip install pandas
  ```
* 구 버전을 사용하고 계시던 분은, 업그레이드를 해 주시면 됩니다.
  ```python
  pip install pandas --upgrade
  ```

* 제가 사용하는 python과 pandas 버전은 다음과 같습니다.

  ```python
  # python version check
  import sys
  print(sys.version)
  ```
  * 실행 결과
  ```
  3.7.4 (default, Aug 13 2019, 20:35:49) 
  [GCC 7.3.0]
  ```

  ```python
  # pandas version check
  import pandas as pd
  print(pd.__version__)
  ```
  * 실행 결과
  ```
  1.0.0
  ```

* `pandas 1.0`의 새 기능을 시험하기 위해 Kaggle의 titanic train dataset을 사용했습니다.

  ```python
  # 파일 불러오기
  dft = pd.read_csv('01_titanic_train.csv')
  dft.info()
  ```
  * 실행 결과
  ```
  <class 'pandas.core.frame.DataFrame'>
  RangeIndex: 891 entries, 0 to 890
  Data columns (total 12 columns):
   #   Column       Non-Null Count  Dtype  
  ---  ------       --------------  -----  
   0   PassengerId  891 non-null    int64  
   1   Survived     891 non-null    int64  
   2   Pclass       891 non-null    int64  
   3   Name         891 non-null    object 
   4   Sex          891 non-null    object 
   5   Age          714 non-null    float64
   6   SibSp        891 non-null    int64  
   7   Parch        891 non-null    int64  
   8   Ticket       891 non-null    object 
   9   Fare         891 non-null    float64
  10  Cabin        204 non-null    object 
  11  Embarked     889 non-null    object 
  dtypes: float64(2), int64(5), object(5)
  memory usage: 83.7+ KB
  ```

* 기존 pandas 사용자께서는 뭔가 달라진 것을 느끼셨을 겁니다.
* pandas 1.0부터 info()에 Column 이름과 번호가 붙어 조금 알아보기 편리해졌습니다
* 아래 부분이 새로 추가된 부분입니다. 사소하지만 명료합니다.

  ```
   #   Column       Non-Null Count  Dtype  
  ---  ------       --------------  -----  
  ```
<br>

### 1. converting to Markdown
* 읽어들인 `DataFrame`의 일부를 출력해보겠습니다.

  ```python
  # 첫 세 줄 출력
  print(dft.head(3))
  ```
  * 실행 결과
  ```
  PassengerId  Survived  Pclass  \
      0            1         0       3   
      1            2         1       1   
      2            3         1       3   
      
                                                      Name     Sex   Age  SibSp  \
      0                            Braund, Mr. Owen Harris    male  22.0      1   
      1  Cumings, Mrs. John Bradley (Florence Briggs Th...  female  38.0      1   
      2                             Heikkinen, Miss. Laina  female  26.0      0   
      
         Parch            Ticket     Fare Cabin Embarked  
      0      0         A/5 21171   7.2500   NaN        S  
      1      0          PC 17599  71.2833   C85        C  
      2      0  STON/O2. 3101282   7.9250   NaN        S  
  ```

* 위 경우처럼 데이터에 따라 줄이 넘어가고 보기가 어렵기도 합니다.
* 특히 `github`등 포스팅 시에 가독성이 떨어지기 때문에 `Markdown`으로 출력해주는 함수를 만들어 사용했습니다만, pandas 1.0에서는 이를 공식적으로 지원합니다.
* 기존에 비해 훨씬 깨끗한 결과를 제공해 줍니다.

  ```python
  # 첫 세 줄을 markdown 형식으로 출력
  print(dft.head(3).to_markdown())
  ```
  * 실행 결과
  * python 실행창에 `markdown` code로 출력된 것을 `github` blog에 글로 옮기면 아래와 같이 표로 정리됩니다.

    |    |   PassengerId |   Survived |   Pclass | Name                                                | Sex    |   Age |   SibSp |   Parch | Ticket           |    Fare | Cabin   | Embarked   |
    |---:|--------------:|-----------:|---------:|:----------------------------------------------------|:-------|------:|--------:|--------:|:-----------------|--------:|:--------|:-----------|
    |  0 |             1 |          0 |        3 | Braund, Mr. Owen Harris                             | male   |    22 |       1 |       0 | A/5 21171        |  7.25   | nan     | S          |
    |  1 |             2 |          1 |        1 | Cumings, Mrs. John Bradley (Florence Briggs Thayer) | female |    38 |       1 |       0 | PC 17599         | 71.2833 | C85     | C          |
    |  2 |             3 |          1 |        3 | Heikkinen, Miss. Laina                              | female |    26 |       0 |       0 | STON/O2. 3101282 |  7.925  | nan     | S          |
<br>

### 2. pd.NA (experimental)
* pandas에서는 결측치(missing value) 표현 방식이 깔끔하지 못했습니다.
* data type에 따라 달랐는데 `NaN`은 `float`, `None`은 `object`, `NaT`는 `DateTime`. 이런 식입니다.  
  여기에 대해서는 [이 글](https://dev.to/discdiver/the-weird-world-of-missing-values-in-pandas-3kph)을 참고하시면 좋을 듯 합니다.  
* 가장 큰 문제는, `integer` column에 `NaN`이 포함되는 순간 `float`으로 바뀌고, 알아채기도 쉽지 않다는 점입니다.  
  모종의 이유로 `int` type으로 바꾸려면 아주 속이 터집니다.

  ```python
  # Series 생성 (data type 지정 안함)
  s = pd.Series([1, 2, None])
  print(s)
  ```
  * 실행 결과
    ```
    0    1.0
    1    2.0
    2    NaN
    dtype: float64
    ```

* 위와 같이 `None`이 포함된 Series (또는 DataFrame)을 만들면 자동으로 `float`으로 바뀌지만,  
  type을 `int`로 지정해 주면 정수형으로 인식합니다.

  ```python
  # Series 생성 (data type을 `Int64`로 지정)
  s = pd.Series([1, 2, None], dtype='Int64')
  print(s)
  ```
  * 실행 결과
    ```
    0       1
    1       2
    2    <NA>
    dtype: Int64
    ```

* 그렇지만 `pd.NA`를 `==`로 찾을 수는 없습니다.  
* 결측치를 찾기 위해서는 기존처럼 `df.isna()`를 사용해야 합니다.

  ```python
  # 원소 중 pd.NA 찾기 (== 사용)
  for i in range(3):
    if s.iloc[i] == pd.NA:
      print('NA found!')
  ```
  * 실행 결과
    ```
    ---------------------------------------------------------------------------
    TypeError                                 Traceback (most recent call last)
    <ipython-input-8-5bf67e6300d7> in <module>
          1 # 원소 중 pd.NA 찾기 (== 사용)
          2 for i in range(3):
    ----> 3   if s.iloc[i] == pd.NA:
          4     print('NA found!')
    
    pandas/_libs/missing.pyx in pandas._libs.missing.NAType.__bool__()
    
    TypeError: boolean value of NA is ambiguous
    ```

  ```python
  # 원소 중 pd.NA 찾기 (.isna() 사용)
  if s.isna().any():
    print('NA found!')
  ```
  * 실행 결과
    ```
    NA found!
    ```
  <br>

### 3. Boolean dtype
* 비슷하게, data type만 명기해주면 결측치가 있는 column도 `Boolean`으로 정의할 수 있습니다.
* 아래 두 명령을 비교해 봅시다.

  ```python
  import numpy as np
  
  # 결측치 포함 Series 작성 (data type 지정 안함)
  s = pd.Series([True, False, np.nan])
  print(s)
  ```
  * 실행 결과
    ```
    0     True
    1    False
    2      NaN
    dtype: object
    ```

  ```python
  # 결측치 포함 Series 작성 (data type `boolean`으로 지정함)
  s = pd.Series([True, False, np.nan], dtype='boolean')
  print(s)
  ```
  * 실행 결과
    ```
    0     True
    1    False
    2     <NA>
    dtype: boolean
    ```
<br>

### 4. String dtype
* pandas 1.0에 들어오면서 `StringDtype`이 생겼습니다.
* 기존에는 `string` 데이터는 `object`형식의 `Numpy Array`로 저장되었지만 여러 혼동을 야기하여 변경되었습니다.
* `string`을 사용하면 `string`과 `non-string`이 `object`로 묶어서 처리되는 것을 방지할 수 있다는 장점이 있습니다.

  ```python
  s = pd.Series(['abc', None, 'def'])
  print(s)
  ```
  * 실행 결과
    ```
    0     abc
    1    None
    2     def
    dtype: object
    ```

  ```python
  s = pd.Series(['abc', None, 'def'], dtype="string")
  print(s)
  ```
  * 실행 결과
    ```
    0     abc
    1    <NA>
    2     def
    dtype: string
    ```
<br>  

### 5. convert_dtypes()
* `convert_dtypes()`를 사용하면 DataFrame과 Series의 type을 `pd.NA`를 지원하는 형태들로 바꿀 수 있습니다.
* 아래와 같은 DataFrame이 있다고 합시다.

  ```python
  df = pd.DataFrame(
      {
          "a": pd.Series([1, 2, 3], dtype=np.dtype("int32")),
          "b": pd.Series(["x", "y", "z"], dtype=np.dtype("O")),
          "c": pd.Series([True, False, np.nan], dtype=np.dtype("O")),
          "d": pd.Series(["h", "i", np.nan], dtype=np.dtype("O")),
          "e": pd.Series([10, np.nan, 20], dtype=np.dtype("float")),
          "f": pd.Series([np.nan, 100.5, 200], dtype=np.dtype("float")),
      }
  )
  print(df.to_markdown())
  print(df.dtypes)
  ```
  * 실행 결과
    ```
    |    |   a | b   |   c | d   |   e |     f |
    |---:|----:|:----|----:|:----|----:|------:|
    |  0 |   1 | x   |   1 | h   |  10 | nan   |
    |  1 |   2 | y   |   0 | i   | nan | 100.5 |
    |  2 |   3 | z   | nan | nan |  20 | 200   |
  
    a      int32
    b     object
    c     object
    d     object
    e    float64
    f    float64
    dtype: object
    ```

* `convert_dtypes()`를 실행하면, 위에 있는 데이터프레임이 `pd.NA`를 지원하는 형태로 바뀝니다.
* `np.nan`도 `pd.NA`로 바뀌고, `int32`도 `Int32`로 바뀌었습니다. (대소문자!)

  ```python
  dfn = df.convert_dtypes()
  print(dfn.to_markdown())
  print(dfn.dtypes)
  ```
  * 실행 결과
  ```
    |    |   a | b   | c     | d    | e    |     f |
    |---:|----:|:----|:------|:-----|:-----|------:|
    |  0 |   1 | x   | True  | h    | 10   | nan   |
    |  1 |   2 | y   | False | i    | <NA> | 100.5 |
    |  2 |   3 | z   | <NA>  | <NA> | 20   | 200   |
    
    a      Int32
    b     string
    c    boolean
    d     string
    e      Int64
    f    float64
    dtype: object
  ```
<br>

### (많이 이른) 총평
* 앞으로 써보면서 변화를 느껴야겠지만, 오류를 유발하는 불확실성을 많이 차단한 느낌입니다.
* `Matplotlib`과 관계된 부분도 많이 바뀌었으니 `pandas.plot()`을 많이 사용하시는 분들은 특히 확인해보실 필요가 있을 것 같습니다.
