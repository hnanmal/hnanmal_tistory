# 프로그래밍 언어 Top10 순위 구경하기 (Hello World 박물관)

---

![Untitled](%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%84%86%E1%85%B5%20de2cf/Untitled.png)

이 그림은 세상에 존재하는 수많은 프로그래밍 언어를 다이어그램으로 나타낸 그림입니다.

어지럽고, 처음들어보는 이름도 정말 많습니다.

이 수많은 언어들 중에서 어떤것들은 너무 오래되어 잊혀가는 것들도 있고,

어떤 언어들은 관심을 받으며 조명되고 있기도 합니다.

그러면 오늘은 TIOBE라는 사이트를 기준으로

요즘 사람들에게 가장 인기있는 언어 TOP 10을 소개하고,

각 언어의 모습을 구경하는 시간을 가져보도록 하겠습니다.

## ****Top 10 (2021년 12월 기준)****

[https://www.tiobe.com/tiobe-index/](https://www.tiobe.com/tiobe-index/)

위의 링크를 통해 언어별 인기 순위를 확인할 수 있습니다.

사실 정확한 인기를 반영하는 것은 아니고, 검색 엔진에서 검색되는 빈도수에 따라 측정된 순위이기 때문에

실제 인기의 척도는 아니라는 것을 말씀드립니다.

하지만 관련 내용이 인터넷 상에서 큰 비중을 차지한다는 것 자체는 사실이겠죠?

<**Apr 2022 기준입니다.>**

1. Python
2. C
3. Java
4. C++
5. C#
6. Visual Basic
7. JavaScript
8. Assembly language
9. SQL
10. PHP

## 구경하기

### Python

1. 특징: 스크립트 언어이고 동적 타입을 지원하는 언어입니다. 플랫폼 독립적이기 때문에 운영체제와 상관없이 동작합니다.
2. 장점: 문법이 쉬운 편이라 진입장벽이 낮고, 빠른 개발속도를 자랑합니다.
3. 단점: 컴파일 언어에 비해 느린 편이고, 싱글 스레드만 지원합니다. (엄밀히 말하자면 조금은 틀린 표현이지만 넘어가주세요.)

**헬로월드**

```python
print("Hello, World!")
```

### C

1. 특징: C언어는 고급 언어이면서 하드웨어를 직접 제어할 수 있는 저급 언어로써의 능력도 탁월하다는 장점이 있습니다.
2. 장점: 임베디드부터 대형 컴퓨터에 이르기 까지 이식성이 뛰어나다고 거의 대부분의 분야에서 사용될 정도로 다양성을 가진다는 장점이 있습니다.
3. 단점: 이후에 등장한 고급언어들에 비해서는 비교적 배우기가 어렵습니다. 코드가 모듈화되지 않으면 자신도 파악하기 어려운 코드가 될 수 있습니다.

**헬로월드**

```c
#include <stdio.h>

int main()
{
    printf("Hello, world!\n");

    return 0;
}
```

### Java

1. 특징: “Write Once, Run Anywhere” 라는 슬로건으로 개발된 언어입니다. 어떤 환경에서도 실행할 수 있는 공통의 런타임 위에서 돌아가는 언어라고 이해하면 좋겠습니다.
2. 장점: 객체지향적언어이고, 이식성이 높으며 멀티스레드를 구현하며 오픈소스 라이브러리가 굉장히 풍부합니다. (생태계가 잘 조성되어 있음)
3. 단점: 실행을 위해서 자바 가상머신을 거쳐야 하기 때문에 속도가 조금 느린편이며, 다른 언어에 비해 작성하게 되는 코드의 길이가 긴 편입니다.

**헬로월드**

```java
public class HelloWorld
{
    public static void main(String[] args)
		{
        System.out.println("Hello, World!");
    }
}
```

### C++

1. 특징: C언어에 객체지향적 문법 요소를 도입한 확장된 버전의 C언어입니다.
2. 장점: 효율적이고 간결하며, C와 마찬가지로 하드웨어 제어가 가능한 저수준 프로그래밍이 가능합니다.
3. 단점: 문자열 자료형이 없다는 것과, 간단한 기능 구현에도 예외처리를 일일이 직접 해주어야 한다는 것은 단점으로 볼 수 있습니다.

**헬로월드**

```cpp
#include <iostream>

int main(int argc, char* argv[]) {
    std::cout << "Hello, World!" << std::endl;

    return 0;
}
```

### C#

1. 특징: MS에 의해 만들어진, JAVA의 대항마 언어입니다. 
2. 장점: 수많은 라이브러리와 특화된 IDE(Visual Studio)를 통해 생산성을 높힌 언어입니다.
3. 단점: 자바와 마찬가지로 실행을 위해서 가상머신을 거쳐야 하기 때문에 속도가 조금 느린편입니다.

**헬로월드**

```csharp
using System;
 
namespace Hello_World
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

### Visual Basic

1. 특징: MS에서 쉽고 빠르게 Windows 운영체제 프로그램을 만들도록 하기 위해 출시한 언어입니다.
2. 장점: 인터페이스가 쉽고 간편합니다. 도구상자의 객체들을 드래그하여 “비주얼”하게 프로그래밍 할 수 있다는 것이 장점입니다.
3. 단점: 어플리케이션이 복잡해질수록 생산성이 하락하며, 윈도우 운영체제에 종속성이 심하기에 크로스 플랫폼은 꿈도 꿀 수 없다는 것이 단점입니다.

**헬로월드**

```visual-basic
Imports System

Module Program
	Sub Main(args As String())
		Console.WriteLine("Hello, World!")
	End Sub
End Module
```

### JavaScript

1. 특징: 자바스크립트는 웹페이지라는 문서가 유저의 동작에 반응할 수 있도록 만들어진 프로그래밍 언어입니다.
2. 장점: 배우기 쉬운 언어로써 진입장벽이 상대적으로 낮습니다. NodeJS를 통해 백엔드도 개발할 수 있습니다.
3. 단점: 디버깅 기능이 부족한 편이며, 객체지향적 프로그래밍을 할 때 추상화 기능에 한계가 있다는 것은 아쉬운 점입니다.

**헬로월드**

```jsx
<script language = "javascript" type = "text/javascript"> 
    document.write("Hello, World!")
</script>
```

### Assembly language

1. 특징: Assembly language는 하드웨어와 소프트웨어의 가장 낮은 층위에 있는 언어로 불릴 만큼 low level 언어라고 할 수 있습니다.
2. 장점: 명령 실행 속도가 가장! 빠르고 프로그램 크기가 아주 작으며 어떤 프로그램도 만들 수 있다는 것은 장점입니다.
3. 단점: 배우기가 너무 어려우며, 덩치 큰 프로그램을 수작업으로 만들기는 거의 불가능에 가깝습니다. 디버깅이 어려운 것도 한 몫하겠죠?

**헬로월드**

```
section .data
	msg db "Hello World!"
   
section .text
	global _start
    
 _start:
 	mov rax, 1
    	mov rdi, 1
        mov rsi, msg
        mov rdx, 12
        syscall
        
        mov rax, 60
        mov rdi, 0
        syscall
```

### SQL

1. 특징: SQL은 Structured Query Language의 줄임말입니다. 관계형 Database system에서 자료관리를 위해 설계된 언어라고 이해하시면 됩니다.
2. 장점: 우리가 알고 있는 일반적 수준의 영어단어와 문장으로 문법이 이루어 지기에 접근성이 좋습니다.
3. 단점: 여러개의 행을 입력해야 하는 경우 하나의 문장으로 동시에 처리하는 것이 불가능하고, 반복적인 구문들을 Library화 할 수 없다는 것은 단점으로 보입니다.

**헬로월드**

```sql
CREATE TABLE helloworld (phrase TEXT);
INSERT INTO helloworld VALUES ("Hello, World!");
INSERT INTO helloworld VALUES ("Goodbye, World!");
SELECT COUNT(*) FROM helloworld;
```

### PHP

1. 특징: 웹개발에 특화된 언어이며 C언어 기반입니다.
2. 장점: 대부분의 운영체제에서 운용이 가능하고, 빠른 생산성과 저렴한 운영 비용이 장점으로 여겨집니다.
3. 단점: 웹 사이트의 규모가 커지게 되면 사후관리가 어려워진다는 단점과 다른 프로그래머들이 쉽게 접근할 수 있기에 생기는 보안문제가 있습니다.

**헬로월드**

```php
<!DOCTYPE html>
<html>
<body>
<?php
echo "Hello World";
?>
</body>
</html>

```

여러가지 프로그래밍 언어들 구경 잘 하셨죠?

이 중에 마음에 드는 것 하나를 정해서 코딩 Life를 시작해보시는 건 어떠세요?