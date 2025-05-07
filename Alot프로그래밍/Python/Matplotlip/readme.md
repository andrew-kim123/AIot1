## Matplotlib 기본 문법

Matplotlib은 파이썬에서 데이터를 시각화하기 위한 가장 기본적인 라이브러리입니다. 다양한 종류의 그래프와 플롯을 생성할 수 있습니다.

### 1. 기본 플롯 생성

* **`pyplot` 모듈 사용:** Matplotlib의 주요 기능은 `pyplot` 모듈을 통해 제공됩니다.

    ```python
    import matplotlib.pyplot as plt

    # 데이터 준비
    x = [1, 2, 3, 4]
    y = [2, 4, 1, 3]

    # 선 그래프 그리기
    plt.plot(x, y)
    plt.show() # 그래프를 화면에 표시
    ```

* **제목, 레이블 추가:**

    ```python
    plt.plot(x, y)
    plt.title('My First Plot') # 그래프 제목
    plt.xlabel('X-axis')       # x축 레이블
    plt.ylabel('Y-axis')       # y축 레이블
    plt.show()
    ```

* **스타일 지정:** 선의 색상, 마커, 선 스타일 등을 변경할 수 있습니다.

    ```python
    plt.plot(x, y, color='red', linestyle='--', marker='o')
    # 'red': 빨간색, '--': 점선, 'o': 원형 마커
    plt.show()
    ```

* **범례 추가:** 여러 개의 플롯을 그릴 때 각 플롯을 설명하는 범례를 추가할 수 있습니다.

    ```python
    x = [1, 2, 3, 4]
    y1 = [2, 4, 1, 3]
    y2 = [1, 3, 2, 4]

    plt.plot(x, y1, label='Line 1')
    plt.plot(x, y2, label='Line 2')
    plt.legend() # 범례 표시
    plt.show()
    ```

### 2. 다양한 플롯 종류

* **산점도 (Scatter Plot):** 두 변수 간의 관계를 점으로 나타냅니다.

    ```python
    x = [1, 2, 3, 4, 5]
    y = [5, 2, 7, 1, 9]
    plt.scatter(x, y)
    plt.show()
    ```

* **막대 그래프 (Bar Plot):** 범주형 데이터의 값을 막대의 높이로 나타냅니다.

    ```python
    categories = ['A', 'B', 'C', 'D']
    values = [20, 35, 30, 25]
    plt.bar(categories, values)
    plt.show()

    # 가로 막대 그래프
    plt.barh(categories, values)
    plt.show()
    ```

* **히스토그램 (Histogram):** 데이터의 분포를 막대 형태로 나타냅니다.

    ```python
    data = [1, 1, 2, 3, 3, 3, 4, 5, 5, 5, 5]
    plt.hist(data, bins=5) # bins는 막대의 개수
    plt.xlabel('Value')
    plt.ylabel('Frequency')
    plt.show()
    ```

* **원형 그래프 (Pie Chart):** 전체에 대한 각 부분의 비율을 원의 부채꼴로 나타냅니다.

    ```python
    labels = ['Apples', 'Bananas', 'Cherries', 'Dates']
    sizes = [15, 30, 45, 10]
    plt.pie(sizes, labels=labels, autopct='%1.1f%%') # autopct는 비율 표시 형식
    plt.axis('equal') # 원이 찌그러지지 않게 비율을 같게 설정
    plt.show()
    ```

### 3. 서브플롯 (Subplots)

하나의 그림(Figure) 안에 여러 개의 플롯을 배치할 수 있습니다.

* **`plt.subplot()` 사용:** 행, 열, 플롯 번호를 지정합니다.

    ```python
    plt.figure(figsize=(8, 6)) # 전체 그림 크기 설정

    plt.subplot(2, 1, 1) # 2행 1열의 첫 번째 플롯
    plt.plot([1, 2, 3, 4], [2, 4, 1, 3])
    plt.title('Subplot 1')

    plt.subplot(2, 1, 2) # 2행 1열의 두 번째 플롯
    plt.scatter([1, 2, 3, 4], [5, 2, 7, 1])
    plt.title('Subplot 2')

    plt.tight_layout() # 서브플롯 간 간격 자동 조정
    plt.show()
    ```

* **`plt.subplots()` 사용:** 여러 개의 Axes 객체를 반환받아 각 객체에 플롯을 그립니다.

    ```python
    fig, axes = plt.subplots(2, 2, figsize=(10, 8)) # 2x2 형태의 서브플롯 생성

    axes[0, 0].plot([1, 2, 3], [4, 5, 6])
    axes[0, 0].set_title('Plot 1')

    axes[0, 1].scatter([1, 2, 3], [6, 5, 4])
    axes[0, 1].set_title('Plot 2')

    axes[1, 0].bar(['A', 'B', 'C'], [10, 20, 15])
    axes[1, 0].set_title('Plot 3')

    axes[1, 1].hist([1, 2, 2, 3, 3, 3])
    axes[1, 1].set_title('Plot 4')

    plt.tight_layout()
    plt.show()
    ```

### 4. 스타일 꾸미기

* **색상, 마커, 선 스타일:** `plot()`, `scatter()` 등의 함수에서 인수로 지정할 수 있습니다.
* **글꼴 설정:** `plt.rcParams`를 사용하여 전역적인 글꼴 설정을 변경하거나, 각 텍스트 관련 함수에서 `fontdict` 인수를 사용할 수 있습니다.
* **축 범위 설정:** `plt.xlim()`, `plt.ylim()`
* **눈금 설정:** `plt.xticks()`, `plt.yticks()`
* **격자 추가:** `plt.grid(True)`

