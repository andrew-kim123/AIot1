NumPy 기본 문법
NumPy는 파이썬에서 수치 계산을 위한 핵심 라이브러리입니다. 다차원 배열 객체와 이를 다루기 위한 다양한 함수를 제공합니다.
1. NumPy 설치 및 임포트
python# 설치
pip install numpy

# 임포트
import numpy as np
2. 배열 생성
python# 리스트로부터 배열 생성
arr = np.array([1, 2, 3, 4, 5])
print(arr)  # [1 2 3 4 5]

# 다차원 배열 생성
arr_2d = np.array([[1, 2, 3], [4, 5, 6]])
print(arr_2d)  
# [[1 2 3]
#  [4 5 6]]

# 0으로 채워진 배열
zeros = np.zeros((3, 4))  # 3x4 배열
print(zeros)
# [[0. 0. 0. 0.]
#  [0. 0. 0. 0.]
#  [0. 0. 0. 0.]]

# 1로 채워진 배열
ones = np.ones((2, 3))  # 2x3 배열
print(ones)
# [[1. 1. 1.]
#  [1. 1. 1.]]

# 특정 값으로 채워진 배열
full = np.full((2, 2), 7)  # 7로 채워진 2x2 배열
print(full)
# [[7 7]
#  [7 7]]

# 단위 행렬
identity = np.eye(3)  # 3x3 단위 행렬
print(identity)
# [[1. 0. 0.]
#  [0. 1. 0.]
#  [0. 0. 1.]]

# 균일한 간격의 배열
linear = np.linspace(0, 10, 5)  # 0부터 10까지 5개의 균등한 간격의 수
print(linear)  # [ 0.   2.5  5.   7.5 10. ]

# 범위 배열
arange = np.arange(0, 10, 2)  # 0부터 10까지 2 간격으로
print(arange)  # [0 2 4 6 8]

# 난수 배열
random = np.random.random((2, 2))  # 0과 1 사이의 난수로 채워진 2x2 배열
print(random)
# 예: [[0.12345678 0.87654321]
#      [0.56789012 0.34567890]]
3. 배열 속성 및 정보
pythonarr = np.array([[1, 2, 3], [4, 5, 6]])

print(arr.shape)      # (2, 3) - 배열의 차원
print(arr.ndim)       # 2 - 배열의 축 수(차원)
print(arr.size)       # 6 - 배열의 총 요소 수
print(arr.dtype)      # int64 - 배열의 데이터 타입
print(arr.itemsize)   # 8 - 각 요소의 바이트 크기
4. 배열 인덱싱 및 슬라이싱
pythonarr = np.array([[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]])

# 인덱싱
print(arr[0, 0])     # 1 - 첫 번째 행, 첫 번째 열
print(arr[2, 3])     # 12 - 세 번째 행, 네 번째 열

# 슬라이싱
print(arr[0:2, 1:3])  
# [[2 3]
#  [6 7]] - 0~1행, 1~2열

# 고급 인덱싱
print(arr[[0, 2], [1, 3]])  # [2 12] - (0,1)과 (2,3) 위치의 요소

# 불리언 인덱싱
mask = arr > 5
print(arr[mask])  # [ 6  7  8  9 10 11 12] - 5보다 큰 요소들
5. 배열 연산
pythona = np.array([1, 2, 3])
b = np.array([4, 5, 6])

# 요소별 연산
print(a + b)       # [5 7 9]
print(a - b)       # [-3 -3 -3]
print(a * b)       # [4 10 18]
print(a / b)       # [0.25 0.4 0.5]
print(a ** 2)      # [1 4 9] - 요소별 제곱
print(np.sqrt(a))  # [1. 1.41421356 1.73205081] - 요소별 제곱근

# 행렬 연산
c = np.array([[1, 2], [3, 4]])
d = np.array([[5, 6], [7, 8]])

print(np.dot(c, d))  # 행렬 곱
# [[19 22]
#  [43 50]]
print(c @ d)         # 행렬 곱 (Python 3.5+)
# [[19 22]
#  [43 50]]

# 통계 함수
arr = np.array([1, 2, 3, 4])
print(np.sum(arr))        # 10 - 합계
print(np.mean(arr))       # 2.5 - 평균
print(np.std(arr))        # 1.118... - 표준편차
print(np.var(arr))        # 1.25 - 분산
print(np.min(arr))        # 1 - 최솟값
print(np.max(arr))        # 4 - 최댓값
print(np.argmin(arr))     # 0 - 최솟값의 인덱스
print(np.argmax(arr))     # 3 - 최댓값의 인덱스
6. 배열 형태 변환
pythonarr = np.array([[1, 2, 3], [4, 5, 6]])

# 형태 변환
print(arr.reshape((3, 2)))  
# [[1 2]
#  [3 4]
#  [5 6]]

# 전치(transpose)
print(arr.T)  
# [[1 4]
#  [2 5]
#  [3 6]]

# 1차원으로 펼치기
print(arr.flatten())  # [1 2 3 4 5 6]
print(arr.ravel())    # [1 2 3 4 5 6]

# 배열 크기 변경
resized = np.resize(arr, (3, 3))  # 크기를 3x3으로 변경 (필요시 값 반복)
print(resized)
# [[1 2 3]
#  [4 5 6]
#  [1 2 3]]
7. 배열 결합 및 분할
pythona = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6], [7, 8]])

# 배열 결합
print(np.vstack((a, b)))  # 수직 결합
# [[1 2]
#  [3 4]
#  [5 6]
#  [7 8]]

print(np.hstack((a, b)))  # 수평 결합
# [[1 2 5 6]
#  [3 4 7 8]]

print(np.concatenate((a, b), axis=0))  # 축 0을 따라 결합 (수직)
# [[1 2]
#  [3 4]
#  [5 6]
#  [7 8]]

print(np.concatenate((a, b), axis=1))  # 축 1을 따라 결합 (수평)
# [[1 2 5 6]
#  [3 4 7 8]]

# 배열 분할
arr = np.array([[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]])

print(np.hsplit(arr, 2))  # 수평 분할
# [array([[1, 2],
#        [5, 6],
#        [9, 10]]), array([[ 3,  4],
#        [ 7,  8],
#        [11, 12]])]

print(np.vsplit(arr, 3))  # 수직 분할
# [array([[1, 2, 3, 4]]), array([[5, 6, 7, 8]]), array([[ 9, 10, 11, 12]])]
8. 브로드캐스팅
브로드캐스팅은 다른 형태의 배열 간에 연산을 수행할 때 자동으로 형태를 맞춰주는 기능입니다.
python# 스칼라와 배열 연산
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr + 10)  
# [[11 12 13]
#  [14 15 16]]

# 다른 형태의 배열 간 연산
a = np.array([[1, 2, 3]])  # 1x3 배열
b = np.array([[1], [2], [3]])  # 3x1 배열
print(a + b)  
# [[2 3 4]
#  [3 4 5]
#  [4 5 6]]
9. 조건부 연산 및 마스킹
pythonarr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

# 조건부 마스크 생성
mask = arr > 5
print(mask)  
# [[False False False]
#  [False False  True]
#  [ True  True  True]]

# 마스크로 값 필터링
print(arr[mask])  # [6 7 8 9]

# 조건부 값 변경
arr[arr > 5] = 0
print(arr)  
# [[1 2 3]
#  [4 5 0]
#  [0 0 0]]

# where 함수 - 조건에 따라 값 선택
arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print(np.where(arr > 5, arr, -1))  
# [[-1 -1 -1]
#  [-1 -1  6]
#  [ 7  8  9]]
10. 파일 입출력
pythonarr = np.array([[1, 2, 3], [4, 5, 6]])

# 파일에 저장
np.save('array.npy', arr)  # .npy 형식으로 저장
np.savetxt('array.txt', arr)  # 텍스트 파일로 저장
np.savez('arrays.npz', a=arr, b=arr*2)  # 여러 배열 저장

# 파일에서 불러오기
loaded_arr = np.load('array.npy')  # .npy 파일 불러오기
loaded_txt = np.loadtxt('array.txt')  # 텍스트 파일 불러오기
loaded_npz = np.load('arrays.npz')  # .npz 파일 불러오기
print(loaded_npz['a'])  # 첫 번째 배열
print(loaded_npz['b'])  # 두 번째 배열
