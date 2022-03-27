# List_Inspect #2 (다이나모 기본노드 활용 시리즈-5)

---

![Untitled](List_Inspe%2099d21/Untitled.png)

[https://hnanmal.tistory.com/entry/ListInspect-1-다이나모-기본노드-활용-시리즈-4](https://hnanmal.tistory.com/entry/ListInspect-1-%EB%8B%A4%EC%9D%B4%EB%82%98%EB%AA%A8-%EA%B8%B0%EB%B3%B8%EB%85%B8%EB%93%9C-%ED%99%9C%EC%9A%A9-%EC%8B%9C%EB%A6%AC%EC%A6%88-4)

상기링크와 이어지는 포스팅 입니다.

지난번의 List_Inspect #1 포스팅에서 두 집합 비교 까지 설명했으니, 이번에는 검색대상의 인덱스 찾기 부터 시작해보겠습니다.

## 검색대상의 인덱스(위치)찾기

### List.AllIndicesOf

![Untitled](List_Inspe%2099d21/Untitled%201.png)

List.AllIndicesOf 노드는 리스트 내에 특정 항목이 몇번째에 있는지를 검색해 줍니다. 

예를 들어 살펴볼텐데, 전세계 커피 원두 산지를 여행다닌 사람의 히스토리를 리스트로 만들었다고 가정해보겠습니다.

![Untitled](List_Inspe%2099d21/Untitled%202.png)

이렇게 만들었습니다.

콜롬비아는 몇번째로 여행갔는지 알고 싶다면? 아래처럼 해보죠.

![Untitled](List_Inspe%2099d21/Untitled%203.png)

콜롬비아는 인덱스 번호 4번이라고 나오는 걸 보니, 5번째로 여행간 곳이란 걸 알 수 있습니다. 

(인덱스는 0부터 시작하니까요.)

이번에는 에티오피아와 케냐를 찾아볼까요?

![Untitled](List_Inspe%2099d21/Untitled%204.png)

검색 대상이 되는 개체를 리스트로 제공하면, 

결과값도 리스트의 각 원소에 해당하는 검색결과가 각각 중첩된, 

2개의 하위리스트를 포함하는 리스트로 반환됩니다.

그림처럼 에티오피아는 인덱스 5, 8번에 위치하고 있습니다.

케냐는 0번째와 9번째군요!

## 특정 위치의 대상 골라내기

![Untitled](List_Inspe%2099d21/Untitled%205.png)

### List.GetItemAtIndex

GetItemAtIndex라는 이름에서 바로 알수 있듯이 인덱스 번호를 인자로 주면 해당하는 아이템을 반환해줍니다.

![Untitled](List_Inspe%2099d21/Untitled%206.png)

하나의 숫자를 인덱스 인자로 주면, 그에 해당하는 **하나의 개체를 반환**합니다.

![Untitled](List_Inspe%2099d21/Untitled%207.png)

리스트로 여러개의 인덱스를 주면, 각 인덱스에 해당하는 원소들을 모아서 **리스트 개체를 반환**해 줍니다.

![Untitled](List_Inspe%2099d21/Untitled%208.png)

Index에 들어갈 인자로 Range(범위) 명령어를 활용하면, 위 그림과 같이 부분 집합을 효율적으로 구해낼 수 있습니다.

![Untitled](List_Inspe%2099d21/Untitled%209.png)

검색의 대상이 되는 리스트가 빈 리스트인 경우에는 인덱스값을 주어 실행시켜도 에러가 납니다.

해당 리스트는 인덱스를 가진 원소가 없으니 당연한 거겠죠?

## 리스트 내 유일값

### List.UniqueItems

![Untitled](List_Inspe%2099d21/Untitled%2010.png)

이 노드의 역할은,

재료로 받은 리스트의 원소들 중에 중복되는 항목들을 하나로 정리해서 보여주는 것입니다.

![Untitled](List_Inspe%2099d21/Untitled%2011.png)

그림을 보면 중복항목이 제거되어 총 10개의 원소를 가진 리스트가

7개의 원소를 가진 리스트로 변환된 것이 보이시죠?

주로 **종류**의 갯수를 파악할 때 사용하고, 리스트의 원소 개수가 눈으로 헤아리기 어려울 정도로 복잡할때 빛을 발하는 노드입니다.

위 예제에서는 좌측 리스트가 여행을 다녀온 이력 데이터라고 한다면,

우측 리스트는 여행을 한번 이라도 다녀온 나라들의 목록 데이터라고 볼 수 있겠습니다.

## 결론

리스트가 구성된 상태를 검사하거나, 데이터의 일부들을 추려내는 노드들을 위주로 살펴보았습니다.

List_Inspect #1과 #2에서 살펴본 노드들이 중요한 이유는, 복잡하고 많은 원소들을 가진 리스트에서, 

내게 필요한 일부의 데이터를 추려서 다른 곳에 활용할 수 있도록 도와주기 때문입니다.

다음 포스팅에서는 필요에 의해서 리스트의 형식이나, 구성을 바꿔주는 

List > Modify 카테고리에 대해 다뤄보도록 할게요!