# 파이썬 기본 문법 정리

---

## 📌 1. 출력하기 (print)

```python
print("Hello, World!")  # 문자열 출력
print(1 + 2)            # 덧셈 출력
```

---

## 📌 2. 변수와 데이터 타입

```python
name = "Alice"      # 문자열
age = 25            # 정수
height = 5.7        # 실수
is_student = True   # 불리언 (참/거짓)

print(type(name))   # <class 'str'>
print(type(age))    # <class 'int'>
print(type(height)) # <class 'float'>
print(type(is_student)) # <class 'bool'>
```

---

## 📌 3. 리스트 (List)

```python
fruits = ["apple", "banana", "cherry"]
print(fruits[0])      # apple
print(len(fruits))    # 3

fruits.append("orange")  # 리스트에 요소 추가
print(fruits)            # ['apple', 'banana', 'cherry', 'orange']
```

---

## 📌 4. 조건문 (if, elif, else)

```python
age = 18

if age >= 18:
    print("Adult")
elif age >= 13:
    print("Teenager")
else:
    print("Child")
```

---

## 📌 5. 반복문 (for, while)

```python
# for 반복문
for i in range(5):
    print(i)  # 0 1 2 3 4

# while 반복문
count = 0
while count < 3:
    print(count)  # 0 1 2
    count += 1
```

---

## 📌 6. 함수 (Function)

```python
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))  # Hello, Alice!
```

---

## 📌 7. 딕셔너리 (Dictionary)

```python
person = {"name": "Alice", "age": 25, "city": "Seoul"}
print(person["name"])  # Alice

person["age"] = 26     # 값 수정
print(person)          # {'name': 'Alice', 'age': 26, 'city': 'Seoul'}
```

---

## 📌 8. 리스트 내포 (List Comprehension)

```python
numbers = [1, 2, 3, 4, 5]
squares = [n ** 2 for n in numbers]
print(squares)  # [1, 4, 9, 16, 25]
```

---

## 📌 9. 파일 입출력

```python
# 파일 쓰기
with open("example.txt", "w") as f:
    f.write("Hello, World!")

# 파일 읽기
with open("example.txt", "r") as f:
    content = f.read()
    print(content)  # Hello, World!
```

---

## 📌 10. 예외 처리 (try, except)

```python
try:
    x = 5 / 0
except ZeroDivisionError:
    print("0으로 나눌 수 없습니다.")
finally:
    print("예외 처리 완료")
```

---

혹시 **클래스**, **모듈** 또는 \*\*패키지

