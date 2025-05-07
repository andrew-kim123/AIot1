## Pandas 기본 문법

Pandas는 파이썬에서 데이터 분석 및 조작을 위해 널리 사용되는 라이브러리입니다. 핵심 객체인 Series와 DataFrame을 통해 데이터를 효율적으로 다룰 수 있습니다.

### 1. Series

* **생성:** 1차원 레이블이 지정된 배열입니다. 리스트, NumPy 배열, 딕셔너리 등으로 생성할 수 있습니다.

    ```python
    import pandas as pd
    import numpy as np

    # 리스트로부터 생성
    s1 = pd.Series([10, 20, 30, 40, 50])
    print(s1)
    # 출력:
    # 0    10
    # 1    20
    # 2    30
    # 3    40
    # 4    50
    # dtype: int64

    # NumPy 배열로부터 생성
    arr = np.array([100, 200, 300])
    s2 = pd.Series(arr)
    print(s2)
    # 출력:
    # 0    100
    # 1    200
    # 2    300
    # dtype: int64

    # 딕셔너리로부터 생성 (키가 인덱스, 값이 데이터)
    data = {'a': 1, 'b': 2, 'c': 3}
    s3 = pd.Series(data)
    print(s3)
    # 출력:
    # a    1
    # b    2
    # c    3
    # dtype: int64

    # 인덱스 지정
    s4 = pd.Series([1, 2, 3], index=['x', 'y', 'z'])
    print(s4)
    # 출력:
    # x    1
    # y    2
    # z    3
    # dtype: int64
    ```

* **인덱싱 및 슬라이싱:** NumPy 배열과 유사하게 정수 인덱스 또는 레이블 인덱스를 사용할 수 있습니다.

    ```python
    s = pd.Series([10, 20, 30, 40, 50], index=['a', 'b', 'c', 'd', 'e'])
    print(s[0])      # 정수 인덱싱 (출력: 10)
    print(s['a'])     # 레이블 인덱싱 (출력: 10)
    print(s[1:4])    # 정수 슬라이싱 (출력: b    20\nc    30\nd    40\ndtype: int64)
    print(s['b':'d'])  # 레이블 슬라이싱 (끝 인덱스 포함, 출력: b    20\nc    30\nd    40\ndtype: int64)
    ```

### 2. DataFrame

* **생성:** 2차원 테이블 형태의 데이터 구조입니다. 여러 개의 Series가 컬럼으로 구성된 형태입니다. 딕셔너리, 리스트의 리스트, NumPy 배열 등으로 생성할 수 있습니다.

    ```python
    import pandas as pd
    import numpy as np

    # 딕셔너리로부터 생성 (키가 컬럼명, 값이 리스트 또는 Series)
    data = {'col1': [1, 2], 'col2': [3, 4]}
    df1 = pd.DataFrame(data)
    print(df1)
    # 출력:
    #    col1  col2
    # 0     1     3
    # 1     2     4

    data2 = {'col1': pd.Series([1, 2]), 'col2': pd.Series([3, 4])}
    df2 = pd.DataFrame(data2)
    print(df2)
    # 출력:
    #    col1  col2
    # 0     1     3
    # 1     2     4

    # 리스트의 리스트로부터 생성 (columns로 컬럼명 지정)
    data3 = [[1, 3], [2, 4]]
    df3 = pd.DataFrame(data3, columns=['col1', 'col2'])
    print(df3)
    # 출력:
    #    col1  col2
    # 0     1     3
    # 1     2     4

    # NumPy 배열로부터 생성 (index와 columns 지정 가능)
    arr = np.array([[1, 3], [2, 4]])
    df4 = pd.DataFrame(arr, index=['row1', 'row2'], columns=['col1', 'col2'])
    print(df4)
    # 출력:
    #       col1  col2
    # row1     1     3
    # row2     2     4
    ```

* **컬럼 선택:**

    ```python
    df = pd.DataFrame({'col1': [1, 2], 'col2': [3, 4], 'col3': [5, 6]})
    print(df['col1'])       # Series 형태로 출력
    # 출력:
    # 0    1
    # 1    2
    # Name: col1, dtype: int64

    print(df[['col1', 'col3']])  # DataFrame 형태로 출력
    # 출력:
    #    col1  col3
    # 0     1     5
    # 1     2     6
    ```

* **행 선택:**

    * `.loc[]`: 레이블 기반으로 행 선택
    * `.iloc[]`: 정수 기반으로 행 선택

    ```python
    df = pd.DataFrame({'col1': [1, 2], 'col2': [3, 4]}, index=['row1', 'row2'])
    print(df.loc['row1'])   # 레이블 'row1'인 행 선택 (Series 형태로 출력)
    # 출력:
    # col1    1
    # col2    3
    # Name: row1, dtype: int64

    print(df.iloc[0])    # 0번째 행 선택 (Series 형태로 출력)
    # 출력:
    # col1    1
    # col2    3
    # Name: row1, dtype: int64

    print(df.loc[['row1', 'row2']]) # 여러 행 선택 (DataFrame 형태로 출력)
    # 출력:
    #       col1  col2
    # row1     1     3
    # row2     2     4

    print(df.iloc[[0, 1]])  # 여러 행 선택 (DataFrame 형태로 출력)
    # 출력:
    #       col1  col2
    # row1     1     3
    # row2     2     4

    print(df.loc['row1', 'col1']) # 특정 행, 특정 컬럼 값 접근 (출력: 1)
    print(df.iloc[0, 0])      # 특정 행, 특정 컬럼 값 접근 (출력: 1)
    ```

* **데이터 필터링:**

    ```python
    df = pd.DataFrame({'col1': [1, 2, 3, 4], 'col2': [5, 6, 7, 8]})
    print(df[df['col1'] > 2])
    # 출력:
    #    col1  col2
    # 2     3     7
    # 3     4     8

    print(df[(df['col1'] > 1) & (df['col2'] < 8)]) # and 조건
    # 출력:
    #    col1  col2
    # 1     2     6
    # 2     3     7

    print(df[(df['col1'] == 1) | (df['col2'] == 8)]) # or 조건
    # 출력:
    #    col1  col2
    # 0     1     5
    # 3     4     8
    ```

* **데이터 정렬:**

    ```python
    df = pd.DataFrame({'col1': [2, 1, 4, 3], 'col2': [6, 5, 8, 7]})
    print(df.sort_values(by='col1')) # 'col1' 컬럼 기준으로 오름차순 정렬
    # 출력:
    #    col1  col2
    # 1     1     5
    # 0     2     6
    # 3     3     7
    # 2     4     8

    print(df.sort_values(by='col2', ascending=False)) # 'col2' 컬럼 기준으로 내림차순 정렬
    # 출력:
    #    col1  col2
    # 2     4     8
    # 3     3     7
    # 0     2     6
    # 1     1     5
    ```

* **기본 통계:**

    ```python
    df = pd.DataFrame({'col1': [1, 2, 3, 4], 'col2': [5, 6, 7, 8]})
    print(df.describe()) # 기술 통계 정보 요약
    # 출력:
    #        col1  col2
    # count  4.000000  4.000000
    # mean   2.500000  6.500000
    # std    1.290994  1.290994
    # min    1.000000  5.000000
    # 25%    1.750000  5.750000
    # 50%    2.500000  6.500000
    # 75%    3.250000  7.250000
    # max    4.000000  8.000000

    print(df.mean())   # 각 컬럼의 평균
    # 출력:
    # col1    2.5
    # col2    6.5
    # dtype: float64

    print(df['col1'].sum()) # 'col1' 컬럼의 합 (출력: 10)
    ```

* **결측치 처리:**

    ```python
    df = pd.DataFrame({'col1': [1, np.nan, 3], 'col2': [4, 5, np.nan]})
    print(df.isnull()) # 결측치 여부 (True: 결측치, False: 아님)
    # 출력:
    #    col1   col2
    # 0  False  False
    # 1   True  False
    # 2  False   True

    print(df.fillna(0)) # 결측치를 0으로 채우기
    # 출력:
    #    col1  col2
    # 0   1.0   4.0
    # 1   0.0   5.0
    # 2   3.0   0.0

    print(df.dropna()) # 결측치가 있는 행 제거
    # 출력:
    #    col1  col2
    # 0   1.0   4.0
    ```
