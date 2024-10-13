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
> [Google Colab](https://colab.research.google.com "Google Colab")      _// 구글 코랩으로 이동하는 링크_

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

###### 문제 설명

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

수 n이 happy number인지 판단하는 함수를 완성한다.

happy number는 다음과 같은 과정을 통해 정의된다 :
  - 임의의 양의 정수로 시작해서, 그 수의 각 자릿수의 제곱의 합을 구한다.
  - 위 과정을 반복하여 1이 되는 순간이 있다면 그 수는 happy number이며, 1이 되지 않고 끝없이 반복되면 happy number가 아니다.

happy number가 맞다면 true, 아니라면 false를 반환한다.

* 1 <= n <= 2^31 - 1

```
    
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

### 3. Week 5
#### 3-1. Container & Docker
_docker에 대해 아직 정확하게 이해하지 못해, 이해한 내용만 정리했습니다._


**컨테이너**(Container)는 **가상화(Virtualization, OS-level)** 방식의 한 종류에서 나타난 개념입니다.


기존 OS 위에 여러 OS를 실행하는 가상화 플랫폼의 형태가 많이 사용되었지만, 여러 OS의 실행히 굉장히 **무겁다**는 단점이 있습니다.


이에 반해 **Container(단위 개념)** 로 application들을 묶은 가상화 방식은 본 OS 위에서 여러 개의 독립적인 App들을 실행할 수 있어, **자원 활용**이나 **독립적인 App사용**에 있어서 더 **효율적**입니다.
그리고.. **도커(Docker)** 가 바로 이런 가상화 환경을 만들도록 돕는 도구입니다.


**이미지(Image)** 라는 개념이 있습니다. 간단히 말해서 Container를 만들기 위한 청사진 정도로 보면 될 것 같습니다.
**Docker hub**가 바로 이러한 이미지들을 다운로드 할 수 있는 저장소이고요.


#### 3-2. Week 5 Assignment
Week 5의 Assignment는 다음과 같습니다.
>후에 본 과목에서 있을 실습을 위해 container 환경을 set up한다.
>
>이 환경은 다음 요소들을 요구한다.
>> 1. Linux OS
>> 2. Git
>> 3. Python3
>> 4. bind mount
>
> 다음 요소들을 만족하는 container 환경을 조성한다.

_예..._


다음 팁을 따라 Assignment를 완료하였습니다.
> - Linux OS
>   - 'ubuntu'(또는 'ossp') 기반의 image를 이용해라.
> - Git & Python installation & check
>   - 'apt-get install -y git python3' 명령어를 이용해여 설치할 수 있다.
>   - 'git --version'과 'python3 --version'명령어로 두 개의 버전을 출력 성공적으로 설치되었는지 확인한다.
> - Bind mount
>   - docker inspect --format="{{ .HostConfig.Binds }}" <container_name>’ 명령어를 입력하면 특정 container에 지정된 directory의 경로를 확인한다.
>   - 출력 형식은 [<host_directory_path>:<container_directory_path>]과 같다.
