# [JAVA] StringTokenizer & spilt()

문자열을 원하는 구분자를 사용하여 분리하고 싶을 때 **StringTokenizer**와 String 메소드 **split()**을 사용할 수 있다.

속도 측면에서는 **StringTokenizer가 더 빠르다**고 볼 수 있다.

+) PS를 풀던 도중 split()은 한글자씩 자르는게 가능하지만 StringTokenizer로는 불가능하다는것을 깨달았다. 이상하다...관련해서 조금 더 찾아봐야겠다

### StringTokenizer의 생성자

**StringTokenizer(String str)** : 디폴트 생성자.

**StringTokenizer(String str, delim)** : 구분 문자(delim)를 인자로 받는 생성자.

**StringTokenizer(String str, String delim, boolean returnDelims)**

: 구분 문자(delim)와 구분문자의 반환 여부를 인자로 받는 생성자.

### StringTokenizer의 메소드

**nextToken()** : 다음 토큰을 리턴한다. (String)

**hasMoreTokens()** : 리턴할 다음 토큰이 남아있으면 true, 없으면 false (boolean)

**countTokens()** : 남아있는 토큰의 갯수를 리턴한다 (int)

예제 코드를 보자.

```java
String str = "학교,집,회사,게임방"; 

StringTokenizer tokens = new StringTokenizer( str, "," );

for( int x = 1; tokens.hasMoreElements(); x++ ){ 
    System.out.println( "문자" + x + " = " + tokens.nextToken() ); 
}
```

결과값은 다음과 같이 나온다.

```java
문자1 : 학교
문자2 : 집
문자3 : 회사
문자4 : 게임방
```

그런데 StringTokenizer의 **한가지 문제점**이 있다.

아래의 코드와 같이 중간에 문자가 비었을 경우...

```java
String str = "학교,집,,게임방"; 

StringTokenizer tokens = new StringTokenizer( str, "," );

for( int x = 1; tokens.hasMoreElements(); x++ ){ 
    System.out.println( "문자" + x + " = " + tokens.nextToken() ); 
}
```

결과값은 다음과 같이 나온다.

```java
문자1 : 학교
문자2 : 집
문자3 : 게임방
```

위처럼 중간에 비어있는 문자를 null로 처리하는 것이 아니라 그냥 생략해버린다.

그렇다면 split을 보자.

### StringTokenizer의 생성자

**String[] split(String str)** : 디폴트 생성자.

**String[] split(String str, int limit) :** 배열의 크기를 결정해서 받는 생성자.

StringTokenizer에서 다뤘던 예제 코드를 보겠다.

```java
String str = "학교,집,,게임방"; 

String[] values = str.split(",");

for( int x = 0; x < values.length; x++ ){ 
   System.out.println( "문자" + (x+1) + " = " + values[x] ); 
}
```

결과값은 다음과 같이 나온다.

```java
문자1 : 학교
문자2 : 집
문자3 : 
문자4 : 게임방
```

위와 같이 **중간에 값이 없다면 null로 처리**되어서 나온다.