# [JAVA] int형 숫자의 자릿수 구하기

숫자의 자릿수를 확인하는데는 두가지 방법이 존재한다.

1. **int -> string으로 변환하여 해당 문자열의 길이를 length 함수를 이용해 구하는 방법**
2. **math 함수를 이용해 int형 변수 자체의 길이를 구하는 방법**

2번의 경우는 조금 생소하다고 느낄수도 있겠다. 코드는 다음과 같다.

> (int)( Math.log10(num)+1 )
> 

예제를 함께 살펴보자

![https://blog.kakaocdn.net/dn/4LCD0/btriRXMuuLu/3HnxjRV3xImnn3k5N7C0Kk/img.png](https://blog.kakaocdn.net/dn/4LCD0/btriRXMuuLu/3HnxjRV3xImnn3k5N7C0Kk/img.png)

결과는 7이 나온다.

💥 주의사항으로는, 자릿수는 **최대 10자리까지만 측정**된다는 것이다.

int형의 범위는 -2147483648 ~ 2147483647

그래서 10자리가 넘어가면 오류가 난다.

![https://blog.kakaocdn.net/dn/eH9LAQ/btriYnCUBD2/mgoH8Ky1kIaOfZF4d4mxY0/img.png](https://blog.kakaocdn.net/dn/eH9LAQ/btriYnCUBD2/mgoH8Ky1kIaOfZF4d4mxY0/img.png)