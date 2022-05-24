# 다이나모 GroupByFunction VS GroupByKey

---

여러개의 객체를 포함한 리스트는 필요에 따라 내포된 리스트 (nested list)로 재편될 필요가 있습니다.

가장 떠올리기 쉬운 사례로는 프로젝트에 존재하는 모든 그리드를 축방향에 따라서 재분류하는 사례가 있겠군요.

말 나온 김에 바로 해볼까요?

## 일단 그리드 마련하기

빈 프로젝트를 열고 그리드를 그려줍시다.

개수는 상관없고, x축 방향과 y축방향으로 적당한 개수의 그리드를 그려주면 됩니다.

![Untitled](%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A1%E1%84%86%E1%85%A9%20GroupByFunction%20VS%20GroupByKey%20d832cc3813fb47fdb5be23a0bdebb52f/Untitled.png)

이렇게 대충 그려주세요. 실습을 위한 준비물이니 그리드 간격같은 건 신경쓰지 않아도 됩니다.

그 다음에는 다이나모를 실행해야 겠죠?

다이나모를 열고 빈 캔버스에 일단 다음과 같이 작성해 봅시다.

![Untitled](%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A1%E1%84%86%E1%85%A9%20GroupByFunction%20VS%20GroupByKey%20d832cc3813fb47fdb5be23a0bdebb52f/Untitled%201.png)

이렇게 두 개의 노드를 배치하면 프로젝트 내에 존재하는 모든 Grid element들을 가져올 수 있습니다.

## X축 방향과 Y축 방향을 자동으로 분류해보자

![Untitled](%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A1%E1%84%86%E1%85%A9%20GroupByFunction%20VS%20GroupByKey%20d832cc3813fb47fdb5be23a0bdebb52f/Untitled%202.png)

일단 Element.Parameters노드를 이용해 그리드 객체에 속해있는 속성항목들을 찾아봅시다.

찾아봐도 축방향에 대한 정보는 들어있는 것이 없군요.

정보가 없으면, 직접 찾아내야겠죠?

### List.GroupByKey로 찾아보자

![Untitled](%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A1%E1%84%86%E1%85%A9%20GroupByFunction%20VS%20GroupByKey%20d832cc3813fb47fdb5be23a0bdebb52f/Untitled%203.png)

축방향을 알아내려면, 먼저 Geometry 커브 형상을 추출한 뒤에,

각 커브의 벡터값을 뽑아내면 된다는 아이디어가 떠올랐습니다.

떠올린대로 코드를 작성하면 위와 같습니다.

추출된 벡터값은 총 2종류인 것 같습니다.

List.GroupByKey로 그루핑을 시도해봅시다.

![Untitled](%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A1%E1%84%86%E1%85%A9%20GroupByFunction%20VS%20GroupByKey%20d832cc3813fb47fdb5be23a0bdebb52f/Untitled%204.png)

List.GroupByKey노드를 사용하려면

1. 어떤 리스트 (A 리스트)
2. 어떤 리스트의 속성값을 추출한 리스트 (a 리스트)

이렇게 총 2개의 리스트가 필요합니다.

속성값의 종류에 따라서 원본 리스트의 조직체계를 개편해주는 노드 인 것이죠.

그런데 결과를 보니 뭔가 이상하네요.

눈으로 확인한 벡터의 종류는 분명 2가지 였는데, 결과값은 벡터의 종류가 마치 6가지 인 것 처럼 행동하고 있군요?

![Untitled](%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A1%E1%84%86%E1%85%A9%20GroupByFunction%20VS%20GroupByKey%20d832cc3813fb47fdb5be23a0bdebb52f/Untitled%205.png)

아마도, 피트 인치 단위를 기반으로 단위 변환을 수행하는 다이나모라서 단위 변환시 보이지 않는 소수점 영역에서 차이가 있을지도 모르겠다는 생각이 들었습니다.

이를 해결하기 위해 벡터 객체를, 데이터 버블에 표현된 문자열로 추출해버리는 노드인 String from Object노드를 추가로 덧붙였더니 잘 작동하는 것을 확인할 수 있습니다.

![Untitled](%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A1%E1%84%86%E1%85%A9%20GroupByFunction%20VS%20GroupByKey%20d832cc3813fb47fdb5be23a0bdebb52f/Untitled%206.png)

제가 레빗 프로젝트에서 그리드를 작성할 때,

y축 방향 그리드는 영어 알파벳으로 이름을 정했고

x축 방향 그리드는 숫자로 이름을 정했습니다.

Element.GetParameterValueByName 노드로 그리드의 이름들을 확인해보니, 각각의 축방향으로 잘 정렬된 것을 볼 수 있습니다.

![Untitled](%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A1%E1%84%86%E1%85%A9%20GroupByFunction%20VS%20GroupByKey%20d832cc3813fb47fdb5be23a0bdebb52f/Untitled%207.png)

만들땐 몰랐는데, 다 만들고 보니 좀 길다는 느낌이 듭니다.

좀더 압축해서 작성할 수는 없을까요?

### List.GroupByFunction으로도 찾아보자

![Untitled](%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A1%E1%84%86%E1%85%A9%20GroupByFunction%20VS%20GroupByKey%20d832cc3813fb47fdb5be23a0bdebb52f/Untitled%208.png)

List.GroupByFunction 노드를 사용하면 위와 같은 꼴로 코드가 작성됩니다.

그런데 붉은색 점선 안의 groupFunction이라는 입력포트에는 어떤값을 입력해줘야 할 까요?

![Untitled](%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A1%E1%84%86%E1%85%A9%20GroupByFunction%20VS%20GroupByKey%20d832cc3813fb47fdb5be23a0bdebb52f/Untitled%209.png)

그 정답은 List.GroupByKey노드의 실습에서 찾을 수 있습니다.

key 분류방법의 기준이 되었던, 그리드의 벡터 값을 구하는 적색점선 구간의 노드들이 합성되어 합성함수의 형태가 되면 groupFunction노드의 인자로 삽입될 수 있습니다.

위쪽 그림에서의 적색 박스 내부의 3개 노드가 이에 해당하겠죠?

다만 저 형태 그대로 사용할 수는 없고, 합성함수의 형태로 바꾸어 입력해야 합니다.

![Untitled](%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A1%E1%84%86%E1%85%A9%20GroupByFunction%20VS%20GroupByKey%20d832cc3813fb47fdb5be23a0bdebb52f/Untitled%2010.png)

바로 이렇게요! 함수를 합성하고 값으로 전달하는 방식에 대한 또다른 설명은 하기 링크를 참조하세요.

[https://hnanmal.tistory.com/entry/다이나모에서-ReplaceByCondition-활용-방법](https://hnanmal.tistory.com/entry/%EB%8B%A4%EC%9D%B4%EB%82%98%EB%AA%A8%EC%97%90%EC%84%9C-ReplaceByCondition-%ED%99%9C%EC%9A%A9-%EB%B0%A9%EB%B2%95)

방향에 따른 그리드 분류는 마찬가지로 아주 잘 이루어 졌습니다.

## 비교

![Untitled](%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%82%E1%85%A1%E1%84%86%E1%85%A9%20GroupByFunction%20VS%20GroupByKey%20d832cc3813fb47fdb5be23a0bdebb52f/Untitled%2011.png)

딱 봐도 길이 차이가 좀 나죠?

그렇기 때문에, 코드를 처음 짤 때,

매 단계분석하며 처리되는 데이터를 실제로 보며 진행할 때는 List.GroupByKey노드를 사용하는 것이 용이하고,

이 후에 널부러진 노드들을 정리하며 최적화 할 때에는,

List.GroupByFunction노드를 활용하는 것이 편리하겠다는 생각이 들었습니다.