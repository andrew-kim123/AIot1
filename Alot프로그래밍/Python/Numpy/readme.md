## NumPy 기본 문법

NumPy는 파이썬의 수치 계산을 위한 핵심 라이브러리입니다. 다차원 배열 객체와 배열을 조작하기 위한 다양한 도구를 제공합니다.

### 1. NumPy 배열 (ndarray)

* **생성:** `np.array()` 함수를 사용하여 파이썬 리스트, 튜플 등을 NumPy 배열로 변환합니다.

    ```python
    import numpy as np

    # 1차원 배열
    a = np.array([1, 2, 3])
    print(a)  # 출력: [1 2 3]

    # 2차원 배열
    b = np.array([[1, 2], [3, 4]])
    print(b)
    # 출력:
    # [[1 2]
    #  [3 4]]

    # 0으로 초기화된 배열
    zeros = np.zeros((2, 3))  # 2x3 형태의 0으로 채워진 배열
    print(zeros)
    # 출력:
    # [[0. 0. 0.]
    #  [0. 0. 0.]]

    # 1로 초기화된 배열
    ones = np.ones((3, 2))  # 3x2 형태의 1로 채워진 배열
    print(ones)
    # 출력:
    # [[1. 1.]
    #  [1. 1.]
    #  [1. 1.]]

    # 특정 값으로 채워진 배열
    full = np.full((2, 2), 7)  # 2x2 형태의 7로 채워진 배열
    print(full)
    # 출력:
    # [[7 7]
    #  [7 7]]

    # 연속적인 값을 갖는 배열
    arange = np.arange(10)  # 0부터 9까지의 정수 배열
    print(arange)  # 출력: [0 1 2 3 4 5 6 7 8 9]

    arange_step = np.arange(0, 10, 2)  # 0부터 9까지 2씩 증가하는 배열
    print(arange_step)  # 출력: [0 2 4 6 8]

    # 균등한 간격의 실수 배열
    linspace = np.linspace(0, 1, 5)  # 0부터 1까지 5개의 균등한 간격의 실수 배열
    print(linspace)  # 출력: [0.   0.25 0.5  0.75 1.  ]

    # 무작위 값으로 채워진 배열
    random = np.random.rand(2, 2)  # 0부터 1 사이의 균등 분포를 갖는 2x2 배열
    print(random)
    ```

* **배열 속성:**

    * `.ndim`: 배열의 차원 수
    * `.shape`: 배열의 형태 (각 차원의 크기를 튜플로 표현)
    * `.size`: 배열의 총 요소 수
    * `.dtype`: 배열 요소의 데이터 타입

    ```python
    arr = np.array([[1, 2, 3], [4, 5, 6]])
    print(f"차원: {arr.ndim}")    # 출력: 차원: 2
    print(f"형태: {arr.shape}")   # 출력: 형태: (2, 3)
    print(f"크기: {arr.size}")    # 출력: 크기: 6
    print(f"데이터 타입: {arr.dtype}") # 출력: 데이터 타입: int64
    ```

### 2. 배열 인덱싱 및 슬라이싱

* **인덱싱:** 파이썬 리스트와 유사하게 각 요소에 접근합니다. 다차원 배열의 경우 각 차원에 대한 인덱스를 쉼표로 구분하여 지정합니다.

    ```python
    arr = np.array([10, 20, 30, 40, 50])
    print(arr[0])   # 출력: 10
    print(arr[-1])  # 출력: 50

    multi_arr = np.array([[1, 2, 3], [4, 5, 6]])
    print(multi_arr[0, 0])  # 출력: 1 (0행 0열)
    print(multi_arr[1, 2])  # 출력: 6 (1행 2열)
    ```

* **슬라이싱:** 배열의 일부분을 추출합니다. `[시작:끝:간격]` 형식을 사용합니다.

    ```python
    arr = np.array([10, 20, 30, 40, 50])
    print(arr[1:4])    # 출력: [20 30 40] (인덱스 1부터 3까지)
    print(arr[:3])     # 출력: [10 20 30] (처음부터 인덱스 2까지)
    print(arr[2:])     # 출력: [30 40 50] (인덱스 2부터 끝까지)
    print(arr[::2])    # 출력: [10 30 50] (처음부터 끝까지 2씩 건너뛰며)

    multi_arr = np.array([[1, 2, 3], [4, 5, 6]])
    print(multi_arr[0, 1:])  # 출력: [2 3] (0행의 인덱스 1부터 끝까지)
    print(multi_arr[:, 0])  # 출력: [1 4] (모든 행의 0열)
    ```

### 3. 배열 연산

* **요소별 연산:** 배열의 각 요소에 대해 사칙연산, 비교 연산 등을 수행합니다. 배열의 형태가 동일해야 합니다.

    ```python
    a = np.array([1, 2, 3])
    b = np.array([4, 5, 6])

    print(a + b)   # 출력: [5 7 9]
    print(a - b)   # 출력: [-3 -3 -3]
    print(a * b)   # 출력: [ 4 10 18]
    print(a / b)   # 출력: [0.25 0.4  0.5 ]
    print(a ** 2)  # 출력: [1 4 9]
    print(a > 2)   # 출력: [False False  True]
    ```

* **배열 간 연산 (브로드캐스팅):** 형태가 다른 배열 간의 연산을 가능하게 하는 NumPy의 강력한 기능입니다. 특정 조건 하에 작은 배열이 큰 배열의 형태에 맞춰 확장되어 연산됩니다.

    ```python
    a = np.array([1, 2, 3])
    scalar = 10
    print(a + scalar)  # 출력: [11 12 13] (스칼라가 배열의 각 요소에 더해짐)

    b = np.array([[1, 2, 3], [4, 5, 6]])
    c = np.array([10, 20, 30])
    print(b + c)
    # 출력:
    # [[11 22 33]
    #  [14 25 36]] (c 배열이 각 행에 더해짐)
    ```

* **행렬 연산:**

    * `np.dot(a, b)` 또는 `a @ b`: 행렬 곱셈
    * `np.transpose(a)` 또는 `a.T`: 전치 행렬
    * `np.linalg.inv(a)`: 역행렬
    * `np.linalg.det(a)`: 행렬식

    ```python
    a = np.array([[1, 2], [3, 4]])
    b = np.array([[5, 6], [7, 8]])

    print(np.dot(a, b))
    # 출력:
    # [[19 22]
    #  [43 50]]

    print(a.T)
    # 출력:
    # [[1 3]
    #  [2 4]]
    ```

### 4. 유니버설 함수 (ufunc)

NumPy는 배열의 각 요소에 대해 독립적으로 작동하는 다양한 유니버설 함수를 제공합니다.

* **수학 함수:** `np.abs()`, `np.sqrt()`, `np.exp()`, `np.log()`, `np.sin()`, `np.cos()` 등
* **통계 함수:** `np.mean()`, `np.median()`, `np.std()`, `np.sum()`, `np.max()`, `np.min()` 등

    ```python
    arr = np.array([1, 4, 9, 16])
    print(np.sqrt(arr))  # 출력: [1. 2. 3. 4.]

    matrix = np.array([[1, 2], [3, 4]])
    print(np.sum(matrix))       # 출력: 10 (모든 요소의 합)
    print(np.sum(matrix, axis=0)) # 출력: [4 6] (각 열의 합)
    print(np.sum(matrix, axis=1)) # 출력: [3 7] (각 행의 합)
    ```

### 5. 배열 형태 변경

* `reshape()`: 배열의 형태를 변경합니다. 요소의 총 개수는 유지되어야 합니다.
* `flatten()` 또는 `ravel()`: 다차원 배열을 1차원 배열로 평탄화합니다.

    ```python
    arr = np.arange(6)
    reshaped = arr.reshape(2, 3)
    print(reshaped)
    # 출력:
    # [[0 1 2]
    #  [3 4 5]]

    multi_arr = np.array([[1, 2, 3], [4, 5, 6]])
    flattened = multi_arr.flatten()
    print(flattened)  # 출력: [1 2 3 4 5 6]
    ```

### 6. 배열 연결 및 분할

* `np.concatenate((a, b), axis=0)`: 주어진 축을 따라 배열을 연결합니다.
* `np.stack((a, b), axis=0)`: 새로운 축을 따라 배열을 쌓습니다.
* `np.split(arr, indices_or_sections, axis=0)`: 배열을 여러 하위 배열로 분할합니다.

    ```python
    a = np.array([1, 2])
    b = np.array([3, 4])
    concatenated = np.concatenate((a, b))
    print(concatenated)  # 출력: [1 2 3 4]

    stacked = np.stack((a, b))
    print(stacked)
    # 출력:
    # [[1 2]
    #  [3 4]]

    arr = np.arange(10)
    splitted = np.split(arr, 2)  # 2개의 하위 배열로 분할
    print(splitted)  # 출력: [array([0, 1, 2, 3, 4]), array([5, 6, 7, 8, 9])]
    ```

### 7. NumPy를 사용한 파일 입출력

* `np.save('filename.npy', arr)`: 배열을 바이너리 파일로 저장합니다.
* `np.load('filename.npy')`: 저장된 배열을 로드합니다.
* `np.savetxt('filename.txt', arr, delimiter=',')`: 배열을 텍스트 파일로 저장합니다.
* `np.loadtxt('filename.txt', delimiter=',')`: 텍스트 파일에서 배열을 로드합니다.

    ```python
    arr = np.array([1, 2, 3, 4, 5])
    np.save('my_array.npy', arr)
    loaded_arr = np.load('my_array.npy')
    print(loaded_arr)  # 출력: [1 2 3 4 5]

    np.savetxt('my_array.txt', arr, delimiter=',')
    loaded_txt = np.loadtxt('my_array.txt', delimiter=',')
    print(loaded_txt)  # 출력: [1. 2. 3. 4. 5.]
    ```


