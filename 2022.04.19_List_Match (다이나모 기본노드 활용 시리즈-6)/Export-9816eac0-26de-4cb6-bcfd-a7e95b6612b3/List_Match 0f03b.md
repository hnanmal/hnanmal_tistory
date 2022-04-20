# List_Match (다이나모 기본노드 활용 시리즈-6)

---

![Untitled](List_Match%200f03b/Untitled.png)

## 리스트를 매치한다는 것의 의미

다이나모 기본노드 활용 시리즈-6으로 돌아왔습니다.

Match는 영어로 “짝을 맞추다”라는 뜻이죠?

오늘 살펴볼 노드들은

집합의 원소들을 한꺼번에 조작하는 방법에 대한 노드들입니다.

List.CartesianProduct

List.Combine

List.LaceLongest

List.LaceShortest

List.Map

이 중에서 List.Map을 제외한 나머지 4개의 노드들은 인자(함수기능 수행을 위해 받아들이는 재료)로 3개 이상을 받아서 작동하게 됩니다.

“combineFunction”, 

list0, 

list1, 

listN

...

![Untitled](List_Match%200f03b/Untitled%201.png)

“+”버튼을 누르면 재료로 쓰일 리스트의 개수를 점점 늘려나갈 수 있습니다.

## 실습을 도와줄 숙련된 조교

![Untitled](List_Match%200f03b/Untitled%202.png)

오늘 실습을 도와줄 조교들을 소개합니다.

리스트가 짝 짓는 것을 보여주기 위해 2개의 점을 이어가면서 두 개 집합 간의 원소 간 관련성을 보여드리겠습니다.

그러기 위해서는 x 축 방향으로 점 10개가 필요하고

y축 방향으로 점 12개가 필요한데요.

조교들이 잘 준비해 둔 게 보이시죠?

맨 위쪽에 있는 Line.ByStartPointEndPoint 노드는 시작점과 끝점을 재료로 받아서 선분을 반환해주는 노드입니다.

이렇게 3명의 조교들과 실습을 함께 하겠습니다.

일단 별도의 리스트 매치 노드없이, 조교들만으로 선분을 만들 수도 있습니다

![Untitled](List_Match%200f03b/Untitled%203.png)

바로 이렇게 말이죠.

사실 다이나모에서 코드 스케치를 작성할 때는 이렇게 처리하고 넘어가는 경우가 대부분일 겁니다.

좀더 엄밀하고 적극적인 예외 처리와 자료형 포맷 보존을 위해서는 오늘 배울 노드를 사용해 코드를 짜는 것이 권장되고요.

자, 다시 코드가 실행된 결과를 볼까요?

선분 10개가 생겼고, Y축 방향의 점 2개는 짝을 찾지 못해서 선분을 만들지 못하고 그냥 남았군요.

Line.ByStartPointEndPoint 노드가 알아서 더 원소개수가 적은 쪽을 기준으로 매칭을 해버렸습니다.

### 미리보기: Shortest, Longest, Cross Product

![Untitled](List_Match%200f03b/Untitled%204.png)

이걸 컨트롤 하는 옵션이 바로 노드에서 우측클릭 했을 때 나오는 “Lacing” 옵션입니다.

현재는 Auto 에 체크 되어있죠? 자동으로 가장 적합해 보이는 매칭 방식을 사용한다는 걸 알 수 있습니다.

한번  이 Lacing 옵션을 “Longest”로 바꿔볼까요?

![Untitled](List_Match%200f03b/Untitled%205.png)

옵션을 바꾸었더니 이번에는 짝을 못찾던 Y축의 원소2개가 X축의 마지막 원소에 일괄적으로 연결되어 선분을 만드는 걸 볼 수 있습니다.

이걸 통해서 Longest 옵션은 둘 중 원소의 개수가 더 많은 쪽을 기준으로 원소 매칭을 해준다는 것을 알 수 있네요!

![Untitled](List_Match%200f03b/Untitled%206.png)

Shortest 옵션을 사용하면 Auto를 사용했을 때와 결과가 같습니다.

그러니 아까 Auto 옵션을 택했을 때에는, 자동으로 Shortest 방식으로 결과를 만들었던 것이군요.

이번에는 마지막 옵션인 Cross Product 옵션으로 실행해봅시다.

![Untitled](List_Match%200f03b/Untitled%207.png)

다이나모의 Lacing 옵션에서 등장하는 Cross Product는 사실 용어 때문에 오해가 있을 수 있는데요.

Cross Product를 검색하면 선형대수학에서의 벡터곱이 나오는데, 이것과는 다른 내용입니다.

사실 여기서의 Cross Product는, 선형대수학에서의 **Outer Product**와 동일한 개념입니다.

벡터의 텐서곱이라고도 하는데, 이 개념은 서로 다른 두 행렬의 모든 원소끼리 서로 곱한 결과를 말하는 거에요.

![Untitled](List_Match%200f03b/Untitled%208.png)

위키에서 정의부분을 보면 이렇습니다. 어지럽죠?

우리가 만든 예제를 통해 위의 내용을 더 쉽게 설명하자면

- x축의 첫번째 점과 Y축의 모든 점을 있는 선분 12개를 그립니다.
- 그 다음에는 x축의 2번째 점과 Y축의 모든 점을 있는 선분 12개를 그립니다.
- 그 다음에는 x축의 3번째 점과 Y축의 모든 점을 있는 선분 12개를 그립니다.
- 그 다음에는 x축의 n번째 점과 Y축의 모든 점을 있는 선분 12개를 그립니다.

...

- 그 다음에는 x축의 마지막(10번째) 점과 Y축의 모든 점을 있는 선분 12개를 그립니다.

이렇게 설명할 수 있겠네요.

이제 거미줄 처럼 복잡했던 예제코드 실행결과가 이해가 되시죠?

“서로 가능한 모든 짝짓기 조합을 찾아서 수행한다” 라고 보시면 되겠습니다.

## List.CartesianProduct

CartesianProduct 는 또 뭘까요?

이게 아까 말했던 선형대수학에서의 **Outer Product**와 똑같은 말입니다!

이름이 또 왜 달라졌냐 하면, CartesianProduct는 동일한 방식을 집합론에서 부르는 이름입니다.

헷갈리지 마세요.

적어도 이 포스트에서는 Product란 이름이 들어간 개념은 양쪽의 원소끼리 짝 지을 수 있는 모든 경우의 수를 의미합니다.

그러니 이 노드의 실행결과는, 아까 조교들끼리 실행했던 결과 중 Cross Product를 수행한 결과랑 동일하겠죠?

![Untitled](List_Match%200f03b/Untitled%209.png)

정확하게 동일합니다! 

이번에는 Z축 까지 포함해서  CartesianProduct를 수행해볼까요?

선을 만드는 명령어는 점 2개로만 수행되는 명령이니, 이번에는 3점을 갖고 원을 만드는 코드를 짜보겠습니다.

![Untitled](List_Match%200f03b/Untitled%2010.png)

엄청 복잡한 결과가 나와버렸군요.

![Untitled](List_Match%200f03b/Untitled%2011.png)

결과를 좀 더 잘 이해하기 위해서 다른 방향에서 본 결과입니다.

x축 점의 개수 10개 x Y축 점의 개수 12개 x Z축 점의 개수 3개 = 총 360개의 결과가 나와야 겠죠?

![Untitled](List_Match%200f03b/Untitled%2012.png)

노드 아래쪽의 결과창(데이터버블)을 보니 360개의 결과 값이 나왔다는 것을 알 수 있습니다.

## List.Combine

이번에는 List.Combine 노드를 볼 차례입니다.

다짜고짜 연결해보겠습니다.

![Untitled](List_Match%200f03b/Untitled%2013.png)

아까 조교들끼리 실행했던 결과 중 Shortest를 수행한 결과랑 동일하군요.

이해하시는데 무리가 없을 거라 생각하고 Z축까지 추가하여 추가 실습을 해보겠습니다.

![Untitled](List_Match%200f03b/Untitled%2014.png)

CartesianProduct와는 다르게 결과가 딱 3개만 나오네요?

리스트 중 가장 원소의 개수가 적은 Z축의 점들을 기준으로 해서,

각 축의 1번째 점들끼리,

각 축의 2번째 점들끼리,

각 축의 3번째 점들끼리

이렇게 총 3개의 결과값이 나온 것을 확인할 수 있습니다.

그런데 궁금한 점이 하나 생겼습니다.

List.Combine 노드와  List.LaceShortest 노드의 결과가 같을 것으로 예상되는데,

왜 두개의 명령어가 따로 존재하는 걸까요?

## List.LaceShortest

![Untitled](List_Match%200f03b/Untitled%2015.png)

List.Combine 노드와  List.LaceShortest 노드를 실행 시킨 결과를 동시에 확인하면 이유를 알 수 있습니다.

눈치채셨나요?

List.Combine노드의 경우에는 한쪽의 원소 개수가 많아서 매칭이 이루어지지 않은 경우에도, 결과를 생략하지 않고 “null”로 반환하고 있습니다. 즉 원소의 개수가 많은 쪽 기준으로 결과값이 반환됩니다.

반면 List.LaceShortest노드에서는 원소의 개수가 많은 쪽 기준으로 결과값이 반환됩니다.

뒤쪽으로 연결될 코드에서, 어떤 쪽의 리스트 원소 개수가 기준이 되어야 하는 지에 따라 적절하게 선택하면 될 것 같습니다.

List.LaceLongest 노드는 레이싱 옵션의 Longest와 똑같으니 설명을 생략할게요.

## List.Map

이 노드의 기능은 간단합니다.

재료로 받아들인 리스트의 모든 원소에 같은 규칙(함수: Function)을 적용해서 그 결과를 반환하는 것이죠.

파이썬의 map( ) 함수와 동일하다고 보시면 됩니다.

[https://hnanmal.tistory.com/entry/python-map-함수의-비정함](https://hnanmal.tistory.com/entry/python-map-%ED%95%A8%EC%88%98%EC%9D%98-%EB%B9%84%EC%A0%95%ED%95%A8)

혹시나 참고하실 분들은 위 링크의 내용도 보시면 좋습니다.

그래서 [List.Map](http://List.Map) 노드 실습에서는,

2번 조교의 내용을 바꾸어서 점 10개가 아닌 점 1개 짜리로 바꾸겠습니다.

![Untitled](List_Match%200f03b/Untitled%2016.png)

한개로 바꾼 뒤, Line.ByStartPointEndPoint의 startPoint에 연결해 줍니다.

그리고 나서 Line.ByStartPointEndPoint노드의 실행결과를 보니 Function이라고 되어 있죠?

즉 이 노드는 이제부터, 시작점과 끝점을 받아서 선분을 만드는 노드가 아닙니다.

시작점은 x축 상의 점인 (3, 0)으로 고정시켜놓고, 끝점을 입력받는 대로 선분을 만들어주는 Function이 된것이죠.

이렇게 하면 1번 조교 + 2번 조교가 하나의 Function이 되었고,

3번 조교는 리스트로 남아있습니다.

[List.Map](http://List.Map) 노드가 필요로 하는 재료들이 다 준비된 셈이죠.

연결해볼까요?

![Untitled](List_Match%200f03b/Untitled%2017.png)

시작점이 (3,0)이고, 3번 조교의 점 12개를 각각 끝점으로 하는 12개의 선분이 완성되었습니다!!!