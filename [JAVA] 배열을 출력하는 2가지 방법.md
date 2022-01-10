# [JAVA] 배열을 출력하는 2가지 방법

**1) for문 돌리기**

```java
public class Main {
	public static void main(String[] args) {
		
		int[] arr = {20, 30, 10, 5, 7};

		for(int i=0; i <arr.length; i++) {
        	System.out.print(arr[i]+" ");
        }

	}
}
```

출력 :

20 30 10 5 7

**2) Arrays.toString 사용**

```java
import java.util.Arrays;

public class Main {
	public static void main(String[] args) {

		int[] arr = {20, 30, 10, 5, 7};

		System.out.println(Arrays.toString(arr));

	}
}
```

출력 :

[20, 30, 10, 5, 7]