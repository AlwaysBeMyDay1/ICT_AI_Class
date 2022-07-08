## 1. 행렬과 벡터
벡터 : 1차원 행렬(텐서)
(텐서 : <https://rekt77.tistory.com/102>)

### 1) 행렬 연산
- 행렬의 합, 차
- 행렬의 실수배
- 행렬의 곱
(m*l 행렬) * (l*n 행렬) = (m*n 행렬)
즉, 행렬 A 열의 개수와 행렬 B 행의 개수가 같을 때만 행렬곱 계산 가능
※ A*B != B*A


------


## 1. Python
interpreter language -> 느림


※Colab
<https://colab.research.google.com/>




## 2. Python 자료형
### 1) 자료형을 가지는 이유
컴퓨터에 배정해야할 공간의 크기를 정해두기 위해.
그래야 불필요한 공간의 사용을 방지
#### ㄱ. 파이썬 문자열의 강력함
i. index에 음수 사용 가능
ii. index에 slicing 사용 가능 (ex. [2:-4])
### 2) cast
input() 함수의 입력 자료형은 항상 문자열이므로
입력받은 문자열을 숫자 연산에 활용하기 위해 숫자로 변환
#### ㄱ. int()
#### ㄴ. float()
### 3) 문자열 관련 함수
#### ㄱ. split()
csv (common separated value)에 사용하기 좋음




## 3. Python 함수
### 1) 파이썬 매개변수와 인수
매개변수(parameter)와 인수(argument)는 혼용해서 사용되는 헷갈리는 용어다.
매개변수는 함수에 입력으로 전달된 값을 받는 변수를 의미하고,
인수는 함수를 호출할 때 전달하는 입력값을 의미한다.
ex.
```
def add(a,b) <!-- ## a, b는 매개변수 -->
    return a + b
print(add(3,4)) <!-- 3, 4는 인수-->
```


### 2) 함수의 종류
i. 일반적인 함수
ii. 입력값이 없는 함수
iii. 결괏값이 없는 함수
iv. 입력값과 결괏값 모두 없는 함수


### 3) *args
입력값이 몇 개가 될지 모를 때 사용
ex.
```
def add_many(*args):
    result = 0
    for i in args:
        result = result + i
    return result
```
- add_many(1,2,3) 처럼 이 함수를 쓰면 args = (1,2,3) 즉, 변수는 튜플 형식
- arg 대신 아무 이름이나 써도 된다.
- def add_mul(choice, *arg) 처럼 다른 매개변수와 함께 사용할 수 있다.


### 4) **kwargs (keyword arguments)
매개변수 이름 앞에 **을 붙이면 매개변수 kwargs는 딕셔너리가 되고
모든 key = value 형태의 결괏값이 그 딕셔너리에 저장된다.
ex.
```
def print_kwargs(**kwargs):
    print(kwargs)
```
```
>>> print_kwargs(name='foo', age=3)
{'age':3, 'name':'foo'}
```


### 5) 매개변수에 초깃값 미리 설정하기
매개변수로 (name, old, man=True)는 되지만
(name, man=True, old)는 안 된다.
초기화시키고 싶은 매개변수는 항상 뒤쪽에 놓기.


### 6) lambda
lambda는 함수를 생성할 때 사용하는 예약어로
def와 동일한 역할을 한다.
lambda 예약어로 만든 함수는 return 명령어가 없어도 결괏값을 돌려준다.
보통 함수를 간결하게 만들 때 사용한다.
우리 말로는 '람다'라고 읽고,
def를 사용해야 할 정도로 복잡하지 않거나,
def를 사용할 수 없는 곳에 주로 쓰인다.
> 사용법
```
lambda param1, param2, ... : param들을 이용한 표현식
```
ex.
```
>>> add = lambda a,b : a+b
>>> result = add(3, 4)
>>> print(result)
7
```
⬇️ 하는 일 완전 동일 ⬆️
```
>>> def add(a, b):
...    return a+b
>>> result = add(3, 4)
>>> print(result)
7
```




## 4. 사용자 입력&출력
### 1) 입력
nput은 입력되는 모든 것을 문자열로 취급하기 때문에
number를 입력해도 숫자가 아닌 문자열임에 주의하자.


### 2) 출력
#### ㄱ. 큰따옴표(")로 둘러싸인 문자열은 + 연산과 동일하다
```
>>> print("life" "is" "too short") ## ①
lifeistoo short
>>> print("life"+"is"+"too short") ## ②
lifeistoo short
```
위 예에서 ①과 ②는 완전히 동일한 결괏값을 출력한다.
즉, 따옴표로 둘러싸인 문자열을 연속해서 쓰면 + 연산을 한 것과 같다.

#### ㄴ. 문자열 띄어쓰기는 콤마로 한다
```
>>> print("life", "is", "too short")
life is too short
```
콤마(,)를 사용하면 문자열 사이에 띄어쓰기를 할 수 있다.

#### ㄷ. 한 줄에 결괏값 출력하기
03-3에서 for문을 배울 때 만들었던 구구단 프로그램에서 보았듯이
한 줄에 결괏값을 계속 이어서 출력하려면
매개변수 end를 사용해 끝 문자를 지정해야 한다.
```
>>> for i in range(10):
...     print(i, end=' ')
...
0 1 2 3 4 5 6 7 8 9
```




## 5. 파일 읽고 쓰기
### 1) 파일 생성하기
```
파일 객체 = open(파일 이름, 파일 열기 모드)
```
#### ㄱ. 파일 열기 모드
i. r : 읽기모드 - 파일을 읽기만 할 때
ii. w : 쓰기모드 - 파일에 내용을 쓸 때(내용 이미 있으면 덮어 씀)
iii. a : 추가모드 - 파일을 이어쓸 때
#### ㄴ. .close()
파일 객체를 닫아 주는 역할을 하는데, 사실 생략해도 된다.
프로그램을 종료할 때 파이썬 프로그램이
열려 있는 파일 객체를 자동으로 닫아주기 때문인데,
그래도 ! .close()를 사용해 직접 닫아 주는 것이 좋다.
쓰기모드로 열었던 파일을 닫지 않고 다시 사용하려고 하면 오류가 발생하기 때문이다.
#### ㄷ. 파일 경로와 slash(/)
파이썬 코드에서 파일 경로를 표시할 때
"C:/doit/새파일.txt" 처럼 슬래시(/)를 사용할 수 있다.
만약 역슬래시(\)를 사용한다면 "C:\\doit\\새파일.txt" 처럼
역슬래시를 2개 사용하거나
r"C:\doit\새파일.txt"와 같이
문자열 앞에 r 문자(Raw String)를 덧붙여 사용해야 한다.
왜냐하면 "C:\note\test.txt"처럼 파일 경로에 \n과 같은 이스케이프 문자가 있을 경우
줄바꿈 문자로 해석되어 의도했던 파일 경로와 달라지기 때문이다.


### 2) 파일에 쓰기
open -> write -> close
```
f = open("file.txt", 'w')
f.write("data")
f.close()
```


### 3) 파일 읽기
#### ㄱ. readline
```
f = open("C:/doit/새파일.txt", 'r')
line = f.readline()
print(line)
f.close()
```
readline으로 파일의 모든 줄을 읽고 싶다면
```
f = open("C:/doit/새파일.txt", 'r')
while True:
    line = f.readline()
    if not line: break
    print(line)
f.close()
```
#### ㄴ. readlines
파일의 모든 줄을 읽어서 각각의 줄을 요소로 갖는 list를 돌려준다.
```
>>> f = open("C:/doit/새파일.txt", 'r')
>>> lines = f.readlines()
>>> for line in lines:
...    print(line)
>>> f.close()
["1 번째 줄입니다.\n", "2 번째 줄입니다.\n", ..., "10 번째 줄입니다.\n"]
```
#### ㄷ. read
파일의 내용 전체를 문자열로 돌려준다.
```
f = open("C:/doit/새파일.txt", 'r')
data = f.read()
print(data)
f.close()
```
### 4) with
조건문과 반복문을 통해 파일을 열다 보면, 닫지 않는 실수를 하는 경우가 생긴다.
이때, with를 사용하면 파일을 자동으로 닫아준다.
```
f = open("foo.txt", 'w')
f.write("Life is too short, you need python")
f.close()
```
⬆️ 결과 동일 ⬇️
```
with open("foo.txt", "w") as f:
    f.write("Life is too short, you need python")
```

