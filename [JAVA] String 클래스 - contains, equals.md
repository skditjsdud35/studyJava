# [JAVA] String 클래스 - contains, equals

> **contains 메서드**
> 

contains( ) 메서드는 **특정 문자열이 포함되어 있는지 확인하는 기능**을 한다. 특정 문자열이 포함되어 있다면 true를 없다면 false를 반환한다.

```java
System.out.println("apple 이 있는가 ? " + p.contains("apple"));
```

> **equals 메서드**
> 

두 문자열이 같은거라고 비교를 하기 위해서는 equals( ) 메서드를 이용하면 된다. 문자열 비교를 위해 == 를 사용해도 되는 게 아닌가 싶지만 **꼭 equals( )를 사용해야 하는 이유가 있다.**

equals( ) 메서드는 두 객체가 같은지 비교를 하는 기능을 하는데, **String은 엄밀히 객체이므로 정확한 비교를 위해서는 객체를 비교할 수 있는 equals( )를 사용**해야 하는 것이다.

즉 **== 로 비교할 경우 같은 문자열을 가지고 있어도 주소값이 다른 경우 false**가 나오게 된다.

따라서 문자열을 정확하게 비교하기 위해서는 == 이 아니라 equals( )를 이용해야 한다. 그래야만 잘못 판단하는 경우를 피할 수 있다.

```java
System.out.println(a1.equals(a2));
```