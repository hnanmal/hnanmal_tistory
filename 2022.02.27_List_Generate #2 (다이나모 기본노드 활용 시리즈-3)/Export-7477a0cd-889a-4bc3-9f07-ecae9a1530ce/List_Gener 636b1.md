# List_Generate #2 (다이나모 기본노드 활용 시리즈-3)

---

기본노드 활용 시리즈-2 에 이어서, List > Generate 카테고리에 있는 노드들을 소개합니다.

![Untitled](List_Gener%20636b1/Untitled.png)

붉은 점선 부분인데, List.OfRepeatedItem과 List.Combinations 노드를 위주로 설명하겠습니다.

왜냐하나면 다른 노드들은 이 2가지 노드와 사용법이 비슷하거든요.

(Empty 노드는 지금은 신경쓸 필요 없습니다.)

## 이미 존재하는 리스트를 가지고 변형 생성하는 노드

![Untitled](List_Gener%20636b1/Untitled%201.png)

Generate 카테고리에 있는 노드 중에 오늘 설명할 노드들은 모두

“이미 존재하는 리스트를 가지고 변형 생성하는 노드”

라고 보시면 됩니다.

그 말인 즉슨, 입력 포트로 어떤 재료를 받아서 동작한다는 뜻이겠죠?

말했듯이 List.OfRepeatedItem 노드는 List.Cycle 와 사용법이 비슷하고,

List.Combinations 노드는 List.Permutations 노드와 사용법이 비슷합니다.

고로 분홍색 영역을 위주로 사용법을 보여드리겠습니다.

### List.OfRepeatedItem

![Untitled](List_Gener%20636b1/Untitled%202.png)

RepeatedItem 이라는 이름에서 알 수 있듯이 대상을 반복시켜 리스트를 만들어주는 노드입니다.

여기서 대상에는 값과 리스트, 딕셔너리 등 등 대부분의 자료형이 해당됩니다. 

일단 노드를 꺼낸 후, 입력 포트에 마우스를 호버링 해보면 그림과 같이 설명이 나옵니다.

item 포트로는 반복할 대상을 연결해주면 되고,

amount 포트로는 반복할 횟수를 입력해 주면 됩니다.

집어 넣을 수 있는 데이터가 정해져 있다는 것을 알고 계시면 좋습니다.

amount 의 설명에는 아래쪽에 int라고 써있죠?

정수형의 데이터만 입력을 받을 수 있다는 뜻입니다.

![Untitled](List_Gener%20636b1/Untitled%203.png)

음수를 집어넣으면 그림처럼 오류를 뱉게 됩니다.

![Untitled](List_Gener%20636b1/Untitled%204.png)

예제를 보면 바로 이해 가능합니다.

1을 받아서 3번 반복한다!

이렇게 해석하시면 되겠죠?

![Untitled](List_Gener%20636b1/Untitled%205.png)

반복대상개체로 리스트를 전달하면 어떻게 될까요?

그림에 보다시피, 1이라는 원소를 갖는 리스트를 3번 반복해서

중첩리스트로 만들어 줍니다.

![Untitled](List_Gener%20636b1/Untitled%206.png)

조금 복잡하게 구성해 본 예제 입니다.

3의 개수가 하나씩 늘어나는 리스트가 상위리스트에 포함되는 형태로 결과가 나오죠?

이런걸 어디 써먹을 수 있을지는 한번 고민해 보시는 것도 좋습니다.

다이나모 프로그래밍을 본격적으로 시작하시면

생각보다 빨리 저런 구성을 써먹고 싶은 생각이 드실 겁니다.

### List.Combinations

![Untitled](List_Gener%20636b1/Untitled%207.png)

List.Combinations 노드는 이미 존재하는 어떤 리스트의 부분 집합들을 가능한 모든 경우의 수를 찾아서 다 만들어주는 노드입니다.

학교 수학시간에 배웠던 수열과 조합 기억나시나요?

이 노드는 그 “조합”을 만들어 주는 노드입니다.

list 포트로는 재료가 되는 리스트를 받고,

length 포트로는 부분집합을 만들 때 원소 갯수를 몇개로 할 지 , 그 숫자를 받습니다.

replace 포트는 true 와 false 두가지의 값만 받아들일 수 있는데,

false가 연결될때는, 부분집합을 만들때 사용한 원소를 재료가 되는 리스트에서 제거해 줍니다.

![Untitled](List_Gener%20636b1/Untitled%208.png)

좌측은 false를 연결했기 때문에 (1,1) 이나 (2,2) 와 같이 중복된 원소가 있는 조합이 없습니다.

반면 우측은 true를 연결했기 때문에 전체 조합의 개수가 15개로 출력됩니다.

## 결론

![Untitled](List_Gener%20636b1/Untitled%209.png)

※List.Cycle 과 List.Permutations 노드는 직접 사용해보시면 사용법을 금방 익힐 수 있습니다.

List.OfRepeatedItem 노드는 2개의 리스트를 인자로 받는 노드를 위한 재료 손질 용도로 쓰이는 경우가 많습니다.

List.Combinations 노드는 다수의 형상끼리 결합 관계를 조정하거나, 교차 형상을 처리할때 유용하게 쓰일 수 있습니다.

물론 설명드린 용도 이외에도 엄청나게 많은 활용방법들이 있으니 직접 프로그램을 만들어 보면서 실습하면 도움이 많이 될 것이라고 생각합니다.