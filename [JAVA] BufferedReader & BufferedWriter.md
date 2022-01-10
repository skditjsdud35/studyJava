# [JAVA] BufferedReader & BufferedWriter

### 부제) 당신이 PS에서 Scanner와 System.out.println()를 쓰면 안되는 이유

**BufferedReader** 

: Scanner와 유사

**BufferedWriter** 

: System.out.println()과 유사

자바를 처음 배울 때, 우리는 **Scanner**와 **System.out.println**를 사용한다.

하지만,  Scanner와 System.out.println를 사용하면 같은 로직이어도 **시간이 굉장히 오래 걸리거나 시간 초과 현상을 겪을 수**도 있다.

나는 이러한 문제를 백준 15552번에서 겪었다.

[15552번: 빠른 A+B](https://www.acmicpc.net/problem/15552)

늘상 하던대로 **Scanner**와 **System.out.println**를 사용해서 문제를 풀었는데 시간초과로 자꾸 틀렸다고 나오는 것이다.

구글링 해본 결과, **Scanner**를 사용할 경우 **BufferedReader**에 비해 약 **8배 정도 느리며, System.out.println**을 사용할 경우 **BufferedWriter**에 비해 약 **3배 정도**가 느리다는 것을 확인할 수 있었다.

따라서, 웬만하면 문제를 풀 때 **Scanner** 대신 **BufferedReader**를, **System.out.println** 대신  **BufferedWriter**를 사용하자!

## BufferedReader의 사용법

**BufferedReade**r의 메소드에는 여러개가 있지만, 사실상 우리가 PS를 위해 사용하는 메소드는 ‘**readline()**’과 ‘**close()**’ 밖에 없다.

> **readLine()** : 입력값으로 들어온 데이터를 한 줄로 읽어서 String으로 바꾸는 메소드
> 

> **close()** : 입력 스트림을 닫고 사용하던 자원을 해제하는 메소드
> 

**5**

**1 2 3 4 5**

첫 번째 줄의 5는 배열의 사이즈고, 두 번째 줄은 배열의 요소라고 하자.

이때, 5는 **readLine()** 을 통해서 읽고, **Integer.parseInt()**로 int 타입으로 바꾸면 된다.

하지만, 두 번째 줄은 요소 하나 하나를 가져와야하기 때문에 **readLine()** 을 통해서 읽고, **StringTokenizer**나 **split()**을 통해 "1", "2", ... "5" 로 따로 입력을 읽고, 배열에 집어 넣어야한다.

위의 내용을 코드로 표현하면 다음과 같다.

그리고 BufferedReader를 사용하기 위해서는 throws IOException을 해 주어야 한다는 사실을 잊지말자. 

try catch문도 사용할 수 있다는데 **대개는 throws IOException을 사용한다**고 한다.

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

	public static void main(String[] args) throws IOException {
		// BufferedReader를 사용하기 위해서는 throws IOException을 해 주어야 함.
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in)); // 선언

		int N = Integer.parseInt(br.readLine()); // readLine으로 받은 입력 데이터 String임.
		int[] arr = new int[N];

		StringTokenizer st = new StringTokenizer(br.readLine());
		for (int i = 0; i < N; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
		}

		br.close();
	}
}
```

## BufferedWriter의 사용법

**BufferedWriter**의 메소드도 여러 가지가 있지만, PS를 위해서 사용하는 메소드는 '**write()**', '**flush()**', '**close()**' 이다.

> **write()** : 출력할 내용을 담는 메소드
> 

> **flush()** : 버퍼를 비워내는 메소드
> 

> **close()** : 스트림을 닫는 메소드
> 

사용방법은 **write()**을 사용하여 출력할 내용을 담고, **flush()**을 통해서 **버퍼를 비워내는 동시에 콘솔에 출력**하면 된다.

주의할 점은 write()만 사용한다고 콘솔에 출력이 되는 것은 아니고, **반드시 flush()을 써 주어야 한다.**

그리고 출력이 끝났으면, close()을 통해서 스트림을 닫는다.

위의 내용을 코드로 표현하면 다음과 같다.

그리고 BufferedWriter도 마찬가지로 사용하기 위해서는 throws IOException을 해 주어야 한다는 사실을 잊지말자. 

```java
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.OutputStreamWriter;

public class Main {

	public static void main(String[] args) throws IOException {
		// BufferedWriter를 사용하기 위해서는 throws IOException을 해 주어야 함.
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out)); // 선언
		bw.write("Hello World");
		bw.flush(); // write로 담은 내용 출력 후, 버퍼를 비움.
		bw.close(); 
	}
}
```

## 빠른 A+B (BOJ 15552)

```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.util.Arrays;
import java.util.StringTokenizer;

public class BOJ15552 {

	public static void main(String[] args) throws IOException{
		
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		
		int num = Integer.parseInt(br.readLine());
		int[] arr = new int[num];
		
		for(int i=0;i<num;i++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			arr[i] = Integer.parseInt(st.nextToken()) + Integer.parseInt(st.nextToken());
		}
		br.close();
		
		for(int i=0;i<num;i++) {
			bw.write(arr[i]+"\n");
		}
		
		bw.flush();
		bw.close();
	}

}
```

빠른 A+B 문제를 BufferedReader와 BufferedWriter를 이용해 다시 풀었더니 맞았다.