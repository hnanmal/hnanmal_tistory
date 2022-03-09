# List_Inspect #1 (다이나모 기본노드 활용 시리즈-4)

---

![Untitled](List_Inspe%2073044/Untitled.png)

다이나모 기본노드 활용시리즈 4번째이고, 리스트 활용에 관한 3번째 포스팅입니다.

이번 글에서는 리스트의 구성을 파악하고, 다양하게 이루어진 리스트의 구성 중에서 사용자가 원하는 특성이나 정보를 추출해 내는 노드들을 살펴봅니다.

**내용이 많아서 포스팅을 2개로 분할합니다.**

금번 포스트에서는 두 집합 비교까지 설명하겠습니다.

카테고리는 List > Inspect 입니다.

## Inspect? 탐정인가요?

![Untitled](List_Inspe%2073044/Untitled%201.png)

붉은색 점선 안에 있는 노드들이 오늘 소개할 대상 입니다.

Generate 카테고리보다 확연히 노드들의 개수가 많죠?

Generate 기능으로 생성된 다양한 리스트들의 특성을 찾아내는 노드들이 즐비해 있습니다.

일일이 다 설명하기 보다, 사용빈도가 높은 노드들을 골라서 실 사용 예를 통해 설명해 볼게요.

## 리스트 내의 하위묶음 평가하기

주로 내포된 리스트, 즉 Nest List 에서 각각의 묶음 리스트의 내용을 평가할 때 주로 사용합니다.

물론 하나의 단일 리스트에서도 사용할 수 있습니다.

### List.AllFalse, List.AllTrue

![Untitled](List_Inspe%2073044/Untitled%202.png)

해당 리스트의 원소들이 모두 참인지 혹은 모두 거짓인지를 판별하여,

True 나 False 값을 반환해 주는 노드입니다.

어떻게 사용하는 지 한번 예시코드를 통해 살펴봅시다. 

먼저 준비물로 중첩 리스트를 준비해줍니다.

![Untitled](List_Inspe%2073044/Untitled%203.png)

가장 상위의 리스트는 하위 3개의 리스트로 구성되어 있습니다.

각각의 하위 리스트는 3개의 숫자를 원소로 갖고 있고요.

우리는 지금부터 3개의 숫자가 모두 짝수인 하위리스트를 한번 찾아보겠습니다.

![Untitled](List_Inspe%2073044/Untitled%204.png)

빈 캔버스에 더블클릭하면 Code Block 노드가 바로 생성되는 것은 아시죠?

```
a % 2?true:false;
```

라고 적어주면 간단한 if 문을 적용할 수 있습니다.(다이나모 내에서 사용되는 디자인 스크립트 문법입니다.)

해석해 보면,  

어떠한 수를 2로 나누었을 때 나머지가 0 이 아니면 true,  

나머지가 0 이면 false 를 반환해라  

라는 명령문입니다.

코드블럭이 수행한 결과를 아래 데이터 버블에서 확인할 수 있습니다.

3가지 숫자가 모두 짝수인 리스트는, 코드블럭에서 반환한 결과도 3개 다 false 이겠죠?

이럴때 List.AllFalse 노드를 사용하면 소기의 목적을 달성할 수 있습니다.

![Untitled](List_Inspe%2073044/Untitled%205.png)

List.AllFalse 노드를 연결해보면 위 그림과 같은 결과를 얻을 수 있습니다.

한가지 미리 알아야 할 것은, 리스트를 재료로 받아서 작동하는 노드이다 보니, 내포된 리스트 구조에서 어떤 층위를 기준으로 기능을 수행할 것인지를 지정해주는 버튼이 있습니다.

위 그림에서 List.AllFalse 노드 내부에 초록색 박스를 보면 화살표가 하나 있는데요.

이것을 클릭해보면 레벨 사용이라는 체크박스가 하나 등장합니다.

어떤 노드던지 꺼냈을 때에는 기본값으로 체크박스가 해제되어 있는데,

예제와 같이 리스트 구조를 활용한 결과값을 얻고 싶으면 체크해준 뒤에,

바로 옆에 있는 위아래 화살표를 통해서 몇 레벨을 기준으로 결과를 낼 지 정해주면 됩니다.

![Untitled](List_Inspe%2073044/Untitled%206.png)

결과 값을 보니 index 1번의 하위리스트가 true 로 반환 되었음을 확인했습니다.

짝수로만 이루어진 리스트는 index 1번의 리스트군요!

이번 예제의 경우에는 코드블럭에서 초록색으로 표시한 @L2 기준으로 기능을 수행하도록 지정하였습니다.

List.AllTrue 노드의 경우에도 사용방법은 동일하겠죠?

### List.AnyFalse, List.AnyTrue

![Untitled](List_Inspe%2073044/Untitled%207.png)

이번에는 짝수를 하나라도 포함하는 하위리스트가 어떤 것인지 확인해 볼까요?

![Untitled](List_Inspe%2073044/Untitled%208.png)

아까 작성했던 예제에서 List.AllFalse 노드를 List.AnyFalse 노드로 대체하기만 하면 됩니다.

결과값을 보니 0, 1번째 리스트에 적어도 하나의 짝수가 들어있군요!

## 개수세기

### List.Count

Inspect 카테고리에는 리스트를 구성하는 원소들의 개수를 세는 노드도 있습니다.

List.Count 노드 입니다.

![Untitled](List_Inspe%2073044/Untitled%209.png)

맨처음에 만들었던 예제로 돌아가서 List.Count 노드를 연결해보겠습니다.

![Untitled](List_Inspe%2073044/Untitled%2010.png)

결과값이 3으로 나오는 군요.

얼핏 생각하면 9개로 나와야 할 것 같은데 왜 이렇게 되었을까요?

아까 List.AllFalse 에서 설명했던 리스트 구조 때문입니다. 그림으로 한번 보세요.

<@L1>

![Untitled](List_Inspe%2073044/Untitled%2011.png)

<@L2>

![Untitled](List_Inspe%2073044/Untitled%2012.png)

<@L3>

![Untitled](List_Inspe%2073044/Untitled%2013.png)

기준이 되는 리스트레벨에 따라서 원소의 갯수를 계산해서 보여줍니다.

## 대표값

### List.MaximumItem, List.MinimumItem

![Untitled](List_Inspe%2073044/Untitled%2014.png)

List.MaximumItem, List.MinimumItem 노드는 이름에서 보이듯이 가장 큰 값과 가장 작은 값을 반환해 주는 노드입니다.

![Untitled](List_Inspe%2073044/Untitled%2015.png)

예제에서 보이듯이 가장 큰 숫자 혹은 가장 작은 숫자를 반환합니다.

문자열의 경우 문자열 코드값으로 최대값, 최소값을 리턴합니다.

## 최외각 값

### List.FirstItem, List.LastItem

![Untitled](List_Inspe%2073044/Untitled%2016.png)

이름에서 유추할 수 있듯이, 리스트의 처음과 끝 원소를 알려줍니다.

![Untitled](List_Inspe%2073044/Untitled%2017.png)

가장 상위리스트인 L3 기준으로 첫번째원소인 [1,2,3] 리스트와 마지막 원소인 [9,11,13]을 반환하고 있습니다.

그런데 하위리스트 각각의 처음과 끝을 반환하려면 어떻게 해야할까요?

![Untitled](List_Inspe%2073044/Untitled%2018.png)

그림처럼 L2 로 지정해서 수행하게 하면 되는군요. 

## 두 집합 비교

### List.SetIntersection

![Untitled](List_Inspe%2073044/Untitled%2019.png)

이것도 쉬운 노드입니다. 두 리스트를 비교해서 교집합을 구해줍니다.

아래는 예제입니다.

![Untitled](List_Inspe%2073044/Untitled%2020.png)

자주 사용하게 되는 노드들이니 예제를 한번씩 꼭! 전부! 따라해보시면 좋습니다.

파이썬도 실행가능한 비주얼 프로그래밍 툴인

다이나모 프로그램이 궁금하신 분들은 하기 링크 참고해서 다운받고 써보세요.

[https://hnanmal.tistory.com/4](https://hnanmal.tistory.com/4)

다음 포스팅에서 뵈어요~