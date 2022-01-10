# [JAVA] 자바 코드의 실행시간 구하기

특정 코드의 실행시간을 알고 싶을 때 사용하는 코드이다.

ms 단위로 시간을 잴 수 있다.

나는 좀 더 편하게 보기 위해 /1000을 하여 초(s)로 출력하였다.

```java
long beforeTime = System.currentTimeMillis(); //코드 실행 전에 시간 받아오기

//실행시간을 구하고 싶은 코드

long afterTime = System.currentTimeMillis(); // 코드 실행 후에 시간 받아오기
long secDiffTime = (afterTime - beforeTime)/1000; //두 시간의 차 계산
System.out.println("걸린 시간 : "+secDiffTime+"초");
```