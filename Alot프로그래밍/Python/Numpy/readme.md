물론입니다! 아래는 NumPy 기본 문법을 마크다운 형식으로 정리한 내용입니다.

markdown
복사
편집
# NumPy 기본 문법

NumPy는 파이썬에서 과학적 계산을 할 때 자주 사용하는 라이브러리입니다. NumPy는 주로 다차원 배열 객체인 `ndarray`와 다양한 수학 함수들을 제공합니다.

## 1. NumPy 설치

```bash
pip install numpy
2. NumPy 임포트
python
복사
편집
import numpy as np
3. NumPy 배열 생성
3.1. 배열 만들기
python
복사
편집
import numpy as np

# 리스트로부터 배열 생성
arr = np.array([1, 2, 3, 4])
print(arr)
# 출력: [1 2 3 4]
3.2. 0으로 채운 배열
python
복사
편집
arr_zeros = np.zeros((2, 3))  # 2x3 배열, 0으로 채움
print(arr_zeros)
# 출력: [[0. 0. 0.]
#        [0. 0. 0.]]
3.3. 1으로 채운 배열
python
복사
편집
arr_ones = np.ones((3, 3))  # 3x3 배열, 1으로 채움
print(arr_ones)
# 출력: [[1. 1. 1.]
#        [1. 1. 1.]
#        [1. 1. 1.]]
3.4. 범위 지정 배열 (arange)
python
복사
편집
arr_range = np.arange(0, 10, 2)  # 0부터 10까지 2 간격
print(arr_range)
# 출력: [0 2 4 6 8]
3.5. 등차수열 배열 (linspace)
python
복사
편집
arr_linspace = np.linspace(0, 1, 5)  # 0에서 1까지 5개의 값을 균등하게 나눔
print(arr_linspace)
# 출력: [0.   0.25 0.5  0.75 1.  ]
4. 배열의 속성
4.1. 배열의 모양 (shape)
python
복사
편집
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr.shape)
# 출력: (2, 3)
4.2. 배열의 크기 (size)
python
복사
편집
print(arr.size)
# 출력: 6
4.3. 배열의 데이터 타입 (dtype)
python
복사
편집
print(arr.dtype)
# 출력: int64
5. 배열 연산
5.1. 배열 더하기
python
복사
편집
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])
result = arr1 + arr2
print(result)
# 출력: [5 7 9]
5.2. 배열 곱하기
python
복사
편집
result = arr1 * arr2
print(result)
# 출력: [4 10 18]
5.3. 배열의 스칼라 값과 연산
python
복사
편집
result = arr1 * 3
print(result)
# 출력: [3 6 9]
6. 배열 슬라이싱
6.1. 1차원 배열 슬라이싱
python
복사
편집
arr = np.array([1, 2, 3, 4, 5])
print(arr[1:4])
# 출력: [2 3 4]
6.2. 2차원 배열 슬라이싱
python
복사
편집
arr2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print(arr2d[1:, 1:])
# 출력: [[5 6]
#        [8 9]]
7. 배열 결합
7.1. 수평 결합 (hstack)
python
복사
편집
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])
result = np.hstack((arr1, arr2))
print(result)
# 출력: [1 2 3 4 5 6]
7.2. 수직 결합 (vstack)
python
복사
편집
result = np.vstack((arr1, arr2))
print(result)
# 출력: [[1 2 3]
#        [4 5 6]]
8. 배열의 수학적 연산
8.1. 배열의 합
python
복사
편집
arr = np.array([1, 2, 3, 4])
print(np.sum(arr))
# 출력: 10
8.2. 배열의 평균
python
복사
편집
print(np.mean(arr))
# 출력: 2.5
8.3. 배열의 표준 편차
python
복사
편집
print(np.std(arr))
# 출력: 1.118033988749895
8.4. 배열의 최소값과 최대값
python
복사
편집
print(np.min(arr))
# 출력: 1
print(np.max(arr))
# 출력: 4
9. 배열의 조건문
9.1. 조건에 맞는 값 찾기
python
복사
편집
arr = np.array([1, 2, 3, 4, 5])
print(arr[arr > 3])
# 출력: [4 5]
9.2. 조건을 만족하는 값의 인덱스
python
복사
편집
print(np.where(arr > 3))
# 출력: (array([3, 4]),)
10. 난수 생성
10.1. 랜덤 배열 생성
python
복사
편집
random_arr = np.random.rand(3, 3)  # 0과 1 사이의 난수로 3x3 배열 생성
print(random_arr)
10.2. 정수형 난수 생성
python
복사
편집
random_int_arr = np.random.randint(0, 10, size=(2, 2))  # 0에서 10 사이의 정수로 2x2 배열 생성
print(random_int_arr)
복사
편집







