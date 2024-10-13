# Assignment Week 6
```
이 글은 오픈소스소프트웨어실습 강좌(DASF003_43)의
Week 6 Assignment 수행을 목적으로 만들어진 문서입니다.
```
---
### 1. Review for Week 4 & 5 Assignment
이 글에서는 위 강좌의 **Week 4 & 5**에서
어떤 **Assignment**를 수행했는지에 대해 알아볼 것입니다.

---

### 2. Week 4
#### 2-1. Google Colab (Jupyter Notebook)
> [Google Colab](https://colab.research.google.com "Google Colab")

\
**Google Colab**은 구글이 무료로 **Jupyter NoteBook**을 **클라우드** 기반에서 사용할 수 있게 만든 사이트입니다.
\
많은 사람들이 이곳에서 협업, 데이터 분석, 머신러닝 학습 등을 하며, 글쓴이는 코드를 작성하여 Assignment를 풀었습니다.


**Google Colab**의 장점은 다음과 같습니다.
- 클라우드 기반에서 실행하므로 하드웨어 사양에 크게 제약을 받지 않고, 로컬 환경을 따로 만들 필요가 없다.
- 무료로 제공되는 GPU를 자원*Resource*으로 사용할 수 있다.
- 모든 웹 브라우저에서 쉽게 접근할 수 있다.
- 다른 사람들과 코드를 수정하거나 실행하여 협업을 하기 쉽다.

#### 2-2. Week 4 Assignment
Week 4의 Assignment는 다음과 같습니다.
>Google Colab내에서 주어진 문제를 풀 코드를 작성한다.

문제의 설명과 해결 코드를 아래에 적어두었습니다.

\

######문제 설명

```
#Task
  Complete isHappy function following the description below

#Happy Number
Write an algorithm to determine if a number n is happy.

A happy number is a number defined by the following process:
- Starting with any positive integer, replace the number by the sum of the squares of its digits.
- Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
- Those numbers for which this process ends in 1 are happy.
Return true if n is a happy number, and false if not.

Constraints: 1 <= n <= 2^31 -1
```

```
isHappy가 다음 설명을 만족하도록 함수를 완성한다.

Happy Number

수 n이 happy number인지 판단하는 알고리즘을 작성한다.

happy number는 다음과 같은 과정을 통해 정의된다 :
  - 임의의 양의 정수로 시작해서, 그 수의 각 자릿수의 제곱의 합을 구한다.
  - 위 과정을 반복하여 1이 되는 순간이 있다면 그 수는 happy number이며, 1이 되지 않고 끝없이 반복되면 happy number가 아니다.

happy number가 맞다면 true, 아니라면 false를 반환한다.

* 1 <= n <= 2^31 - 1

```

\

###### 해결 코드
```python
def isHappy(n):
  memory = set()
  digits = []

  while not(n in memory):
    memory.add(n)

    while (1):
      digits.append(n % 10)
      if(n // 10 == 0):
        break
      else:
        n = n // 10

    n = 0
    for i in digits:
      n += i * i

    if(n == 1):  return True
    else:
      del digits[:]
  #(n in memory)
  return False
```
