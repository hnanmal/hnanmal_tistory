# Dynamo를 이용해서 웹페이지를 만든다는 것은

---

이번 포스트에서는 다이나모 샌드박스를 이용하여 간단한, 정말로 아주 간단한 웹페이지를 하나 만들어보려고 합니다.

도대체 왜? 다이나모로 웹페이지를 만들어야 합니까? 더 좋은 툴이 수두룩 하고, 구현할 수 있는 한계점도 명확한데? 라고 질문하고 싶으신 분들도 많을 텐데요. 사실 이런 생각이 들 정도로 배경지식이 높으신 분들은 이 포스트를 보지 않으셔도 됩니다.

이번 포스트는 명확하게 “프로그래밍을 전혀 알지 못하다가, 최근 관심이 생겨서 이것저것 알아보지만 실제로 뭔가를 아직 만들어보지는 못해서 갈증이 있는 분” 들을 대상으로 한다는 것을 서두에 밝힙니다.

html에 대한 지식이 전혀 없으신 분들도

일단 다이나모를 설치하시고 (설치과정은 깃허브에서 파일을 복사해오기만 하면 되니 정말 쉽습니다.),

순차적으로 과정을 따라하면, 초보적이지만 그래도 있을건 있는 웹페이지를 만드실 수 있게 됩니다.

## Dynamo로 html 문서를 만든다는 것은

다이나모로 웹문서를 만든다는 것은 앞서 설명했지만 비효율 적인 방식이긴 합니다.

웹문서를 생성하려는 목적으로 만들어진 툴이 아니기 때문에 당연히 간단한 것도 멀리 돌아가야만 구현할 수 있습니다. 하지만 가끔씩 이렇게 미련한 짓도 해야 사는게 재미있겠죠?

일단 다이나모를 설치해 봅시다. 설치하는 방법을 모르시면 일단 하기 링크를 따라하세요.

[https://hnanmal.tistory.com/entry/Dynamo-Sandbox-최신버전-다운받기](https://hnanmal.tistory.com/entry/Dynamo-Sandbox-%EC%B5%9C%EC%8B%A0%EB%B2%84%EC%A0%84-%EB%8B%A4%EC%9A%B4%EB%B0%9B%EA%B8%B0)

(저는 최신버전이 아닌 2.12.0.5650버전을 사용합니다. 따라하실 분들은 참고해주세요.)

### 다이나모 실행

다운받아서 원하는 경로에 압축해제 하셨으면, 폴더에 들어있는 파일 중에서 “DynamoSandbox.exe”라는 파일을 실행하면 됩니다.

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled.png)

위 그림처럼 생긴 파일입니다.

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%201.png)

더블 클릭하면 이렇게 생긴 화면이 뜨게 됩니다.

### index.html 파일 만들기

MS 워드는 문서의 확장자가 .doc입니다. PowerPoint는 .ppt 이죠?

그렇다면 웹문서의 확장자는 뭘까요?

바로 “.html”입니다.

오늘 만들 웹페이지는 index라는 이름을 가진 html 파일로 만들 겁니다.

여기까지 다이나모로 한번 해볼게요. 지금부터 따라하시면 되요.

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%202.png)

먼저 화면 좌측 상단을 보면 검색창이 하나 있는데 보이시죠? 거기에 write라고 검색해보세요.

그러면 검색결과의 3번째에 WriteText라는 노드가 있습니다.

클릭해서 캔버스에 배치해 볼게요.

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%203.png)

이 노드가 하는 일은 파일의 내용을 써주는 일입니다. (파일이 없으면 만들어주기도 합니다!)

다른 노드와 연결되는 상황을 보시면 더 쉽게 이해하실 겁니다.

이번에는 Library 검색창에 “filePath”라고 검색해 볼까요?

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%204.png)

검색결과 첫번째에 있는 항목이 우리가 찾는 녀석입니다. 클릭해서 배치해 주세요.

그 다음에 찾아보기 버튼을 누르면, 어떤 파일에 작성할지를 고를 수 있습니다.

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%205.png)

실습에 사용할 폴더를 만드신 후에, 그 폴더까지 들어가셔서 파일이름에 “index.html”이라고 적으신 후에 열기버튼을 눌러보겠습니다.

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%206.png)

그러면 File Path노드에서는 어떤 파일에 작성할 지에 대한 정보가 들어있게 되고, 이 노드의 Output을 WriteText 노드의 input에 연결하면 준비가 끝나게 됩니다!

### String 노드로 html 태그 문법을 작성해보자

이제 본격적으로 웹문서를 만들어 볼텐데요. 검색창에 string 이라고 써서, 문자열을 작성하는 노드를 꺼내봅시다.

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%207.png)

여기까지 잘 하셨죠?

이제 저 String 노드의 안쪽에 html 태그를 작성하면 되는데요. 아무 글자나 넣어서 index.html이 생성되는지 확인해보겠습니다.

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%208.png)

“hello dynamo and html !!!!!”라는 문구를 적고 경로로 지정한 폴더에 가서 확인해보니 정말로 index.html파일이 생성되어 있습니다. 

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%209.png)

웹브라우저로 열어보니 웹문서에 아까 입력했던 “hello dynamo and html !!!!!” 문장이 등장하는 것을 확인할 수 있습니다.

이제 html의 문법에 맞춰서 간단한 웹문서를 작성해봅시다.

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%2010.png)

웹문서는 'html' 이라는 태그로 시작하고, '/html' 이라는 태그로 끝나게 됩니다.

화면과 동일하게 코드를 한번 작성해 보세요. (<meta charset="utf-8">부분은 굳이 이해하지 않아도 됩니다.)

복사할 수 있게 아래에 써 드리기도 하겠습니다.

```html
<html>

<head>
<title>WEB1 - html by Dynamo Sandbox</title>
<meta charset="utf-8">
</head>

</html>
```

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%2011.png)

이 상태로 코드를 실행하고 아까전의 index.html 파일을 다시 열어보면,

웹페이지의 내용은 아무것도 없어집니다.

왜냐하면 'head' 태그는 웹문서를 설명하는 역할을 하기 때문에, 아직 'body' 태그를 작성하지 않은 우리의 웹문서는 보여줄 게 없기 때문입니다.

대신에 화면처럼 탭 아이콘에 마우스를 가져다 놓으면 팝업이 하나 뜨면서 웹페이지의 타이틀을 띄워주는데요. 여기에 아까 우리가 작성했던 “WEB1 - html by Dynamo Sandbox” 이라는 문구가 들어가 있습니다.

### 번호가 적힌 목록 만들어보기

이제 웹페이지의 내용을 채워볼까요?

본문이 등장하기 전에 대략적인 흐름을 볼 수 있는 목차가 먼저 등장하면 좋겠죠?

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%2012.png)

'body'태그를 작성하고, 이어서 굵은 글씨로 “목차”라는 항목이 나오게 하고 싶었습니다. 그 아래에는 오늘 실습 과정을 크게 3단계로 나누어서 목차 항목들을 구성했고요.

ol 태그는 Ordered List의 약자입니다. 숫자가 붙은 리스트를 만들어주는 태그이고, ol태그의 하위항목으로 li태그를 쓴다는 것을 이해하시면 됩니다. (당연히 li는 list의 줄임말 이겠죠?)

```html
<html>

<head>
<title>WEB1 - html by Dynamo Sandbox</title>
<meta charset="utf-8">
</head>

<body>
<h2>목차</h2>
<ol>
    <li>Dynamo로 html 문서를 만드는 것은</li>
    <li>String노드와 CodeBlock</li>
    <li>Open html with Browser</li>
</ol>
</body>

</html>
```

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%2013.png)

### 본문 작성하기

생각했던대로 웹문서가 만들어졌습니다.

목차가 생겼으니 이제 본문이 등장할 차례네요. 첫번째 목차의 내용을 복사해서 'h2' 태그를 만들어 그 안쪽에 배치해줍니다.

```html
<html>

<head>
<title>WEB1 - html by Dynamo Sandbox</title>
<meta charset="utf-8">
</head>

<body>
<h2>목차</h2>
<ol>
    <li>Dynamo로 html 문서를 만드는 것은</li>
    <li>String노드와 CodeBlock</li>
    <li>Open html with Browser</li>
</ol>

<h2>Dynamo로 html 문서를 만드는 것은</h2>

</body>

</html>
```

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%2014.png)

제목밑에는 본문 내용을 배치해야겠죠?

문단으로 나뉜 글을 쓸 때는 'p' 태그를 사용합니다.

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%2015.png)

```html
<html>

<head>
<title>WEB1 - html by Dynamo Sandbox</title>
<meta charset="utf-8">
</head>

<body>
<h2>목차</h2>
<ol>
    <li>Dynamo로 html 문서를 만드는 것은</li>
    <li>String노드와 CodeBlock</li>
    <li>Open html with Browser</li>
</ol>

<h2>Dynamo로 html 문서를 만드는 것은</h2>

<p>예를 들면 야구방망이로 글씨를 쓰는 것과 비슷합니다. <br>시간은 오래걸리고, 기능도 한정적인데다가 완성품의 퀄리티를 놓고 봐도 당연히 따라잡기 어렵죠.</p>
<p>그런데도 이런걸  해보는 이유는 뭘까요?<br>다이나모 샌드박스도 프로그래밍 툴이고, 다른 프로그래밍 툴이 할 수 있는 일은 다이나모도 할 수 있다는 것을 보여드림으로써 동기부여가 되었으면 좋겠다는 마음때문입니다.</p>

</body>

</html>
```

자 웹페이지를 실행해볼까요?

![Untitled](Dynamo%E1%84%85%E1%85%B3%E1%86%AF%20%2061ba8/Untitled%2016.png)

웹페이지로 렌더링 된 결과는 위 스크린 샷과 같습니다!!!

나름 블로그 포스팅의 꼴을 갖춘 하나의 웹문서가 탄생했네요!!!

## 결론

사실 다이나모로 이런 웹문서를 만드는 건 우스꽝 스러운 작업이긴 합니다.

그런데, 프로그래밍과 코딩이라는 분야에 처음 도전하는 분들은 비주얼프로그래밍 툴을 통해 접근장벅을 많이 낮출 수 있습니다.

그리고 비주얼프로그래밍 툴로도 모든 것을 구현할 수 있다는 믿음이 있어야 몰두하고 동기부여가 되어 꾸준히 공부해 나갈 수 있을겁니다. (제가 그랬거든요)

꼭 따라해보시고, 프로그래밍에 한 발짝 더 친숙하게 다가가는 계기가 되셨으면 합니다.