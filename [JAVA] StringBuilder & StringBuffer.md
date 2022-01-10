# [JAVA] StringBuilder & StringBuffer

String은 소위 **immutable(불변) 객체**라고 한다. 따라서 값을 변경할 수 없다.

즉, **String str1 = “abc”** 라는 객체와 **String str2 = “def”** 라는 객체가 있을 때 만약 **str1 + str2** 와 같은 연산을 하게 되면 값이 변경되는 것이 아니라 **새로운 String을 생성**하게 되는 것이다.

concat(문자열 합치기)이나 + 사용 시 기존 값을 버리고 새로 할당해서

1000번 이상 수행할 경우 급격히 느려지게 되어 성능적으로 좋지 않다.

아래의 그림은 concat과 StringBuffer&StringBuilder의 성능 차이를 보여준다.

연산 횟수가 많아질수록 concat의 연산 속도가 독보적으로 느려지는 것을 확인할 수 있다.

![Untitled](%5BJAVA%5D%20StringBuilder%20&%20StringBuffer%2092e3b682c6484e0aa4856f71ae7d0abd/Untitled.png)

따라서 String에서 concat, + 를 1000번 이상 사용할 경우 해당 상황에서는 **mutable(변경 가능)한 StringBuffer와 StringBuilder**를 사용한다.

## **StringBuffer vs StringBuilder**

그렇다면 **StringBuffer와 StringBuilder의 차이점**은 무엇일까?

가장 큰 차이점은 **동기화의 유무**로써 **StringBuffer**는 동기화 키워드를 지원하여 **멀티쓰레드 환경에서 안전하다는 점(thread-safe)** 이다.  

참고로 **String**도 ****불변성을 가지기때문에 마찬가지로  **멀티쓰레드 환경에서의 안정성(thread-safe)**을 가지고 있다.

반대로 **StringBuilder**는 **동기화를 지원하지 않기**때문에 멀티쓰레드 환경에서 사용하는 것은 적합하지 않지만 동기화를 고려하지 않는 만큼 **단일쓰레드에서의 성능은 StringBuffer 보다 뛰어나다**.

즉,

<aside>
💡 **String**                :  문자열 연산이 적고 멀티쓰레드 환경일 경우

</aside>

<aside>
💡 **StringBuffer**    **** :  문자열 연산이 많고 멀티쓰레드 환경일 경우

</aside>

<aside>
💡 **StringBuilder**   :  문자열 연산이 많고 단일쓰레드이거나 동기화를 고려하지 않아도 되는 경우

</aside>

위와 같이 상황에 따라 적절하게 사용하면 되겠다.

평소 코딩할 때 StringBuilder와 StringBuffer 중 어떤 것을 써야하는지 검색을 해봤는데, **‘StringBuilder의 속도가 StringBuffer보다 약 2배정도 빠르니 StringBuilder를 사용해라’**라는 의견도 있었고 **‘StringBuffer가 더 safety하니 StringBuffer를 사용해라’**라는 의견도 있어서 평소에 BOJ나 프로그래머스 문제를 풀 때는 그냥 사용하는 사람 마음대로 써도 될듯하다.

+) ‘StringBuffer 의 경우는 내부 메소드가 Synchronized 로 구성되어 있어 싱글 쓰레드에서 성능이 떨어지니 알고리즘 문제 풀이에서 출력이 많은 경우에는 추천하지 않습니다.’ 이런 글을 발견했다.

**그냥 StringBuilder를 쓰는게 마음편할듯!**

## StringBuffer, StringBuilder의 선언 방법

```java
StringBuilder sb = new StringBuilder();
StringBuffer sb = new StringBuffer();
```

## StringBuffer, StringBuilder의 주요 메소드

**sb.append(값)**

- StringBuffer, StringBuilder 뒤에 값을 붙인다

**sb.insert(인덱스, 값)**

- 특정 인덱스부터 값을 삽입한다

**sb.delete(인덱스, 인덱스)**

- 특정 인덱스부터 인덱스까지 값을 삭제한다

**sb.indexOf(값)**

- 값이 어느 인덱스에 들어있는지 확인한다

**sb.substring(인덱스, 인덱스)**

- 인덱스부터 인덱스까지 값을 잘라온다

**sb.length()**

- 길이 확인

**sb.replace(인덱스, 인덱스, 값)**

- 인덱스부터 인덱스까지 값으로 변경

**sb.reverse()**

- 글자 순서를 뒤집는다