# 파이썬 string 문자열처리의 달인이 되기 위한 여정

![image.png](attachment:5133770b-6289-43a6-806c-af7b4966db66.png)

프로그래밍 언어가 다루는 여러가지 데이터 타입 중에서 상당히 빈번하게 다루게 되는 타입 중 하나가 바로 String(문자열) 타입입니다.  
입력을 문자로 받기도 하고, 열심히 코딩한 결과를 가독성있게 보여주기 위해 문자열로 가공해서 출력하기도 하니까요.  

그만큼 기본이 되면서, 중요한 데이터 형식이니, 원하는 결과를 만들기 위한 방법들을 하나씩 알아봅시다. 기본기가 되어줄거에요.

## 문자열을 만들려면??

따옴표를 사용 하면 됩니다.
>" ", ' ', """, '''


```python
["String", '문자열']
```




    ['String', '문자열']



한 줄이 아닌 여러 줄로 구성된 문자열을 입력해서 String data를 만들려면 따옴표를 세번 반복하면 됩니다.


```python
"""
동해물과 백두산이 마르고 닳도록
하느님이 보우하사 우리나라만세.
남산 위에 저 소나무, 철갑을 두른 듯
바람서리 불변함은 우리 기상일세.
"""
```




    '\n동해물과 백두산이 마르고 닳도록\n하느님이 보우하사 우리나라만세.\n남산 위에 저 소나무, 철갑을 두른 듯\n바람서리 불변함은 우리 기상일세.\n'




```python
'''
Lorem Ipsum is simply dummy text of the printing and typesetting industry.
Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.
It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged.
It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.

'''
```




    "\nLorem Ipsum is simply dummy text of the printing and typesetting industry.\nLorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.\nIt has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged.\nIt was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.\n\n"



## 출력 라인 조절하기

 문자열을 출력하는 함수는 print 함수입니다. 위에서 배운 따옴표는 데이터를 입력하는 과정이고, 입력된 데이터를 출력하는 것은 print 함수를 통해서 할 수 있습니다.  
 이 함수는 한줄 또는 여러줄로 출력할 수 있는 옵션을 가지고 있습니다.


```python
print("그냥 한줄만 쓸게요")
```

    그냥 한줄만 쓸게요


한줄만 출력하려면 심플하게 출력할 문자열 데이터만 print 함수의 인자로 넣어주면 됩니다.  
그럼 여러줄로 출력하려면 어떻게 할까요?


```python
print("그냥 한줄만 쓰려다가,\n마음이 바뀌어서\n세줄이나 써버렸네..")
```

    그냥 한줄만 쓰려다가,
    마음이 바뀌어서
    세줄이나 써버렸네..


위와 같이 \n 이라는 문자를 삽입해주면 됩니다. 한줄을 띄워서 쓰라는 의미죠. 비슷한 역할을 하는 다른 문자조합들도 있는데, 대부분 \\(역슬래시)로 시작합니다.  
이런 것들을 서식 지정자라고 하는데, 이에 대해서는 아래를 참고하세요

|코드|설명|
|------|---|
%s|문자열 타입
%c|문자 1개
%d|정수 타입
%f|부동소수점
%o|8진수
%x|16진수
%%|문자 '%'


위의 예와는 반대로 여러 번 print 함수를 써서 출력한 결과들을 한줄로 모아서 보여주고 싶으면 아래처럼 하면 됩니다.


```python
print('아침은 칼국수를 먹었습니다. ', end="")
print("점심은 제육볶음을 먹었고, ", end="")
print("저녁에는 치킨을 먹고 싶어요.")
```

    아침은 칼국수를 먹었습니다. 점심은 제육볶음을 먹었고, 저녁에는 치킨을 먹고 싶어요.


print 함수의 인자로, 출력 대상이 되는 데이터 다음에, end=""라는 옵션값을 집어넣으면 됩니다.  
옵션값의 따옴표 사이에 있는 값을 기준으로 출력값들을 한 줄로 연결해 줍니다.

## 숫자를 문자열로 바꾸기

숫자와 문자를 한 줄에 동시에 출력하려면 숫자도 문자의 형태로 바꾸어 주어야 합니다.  
바꾸는 방법은 str 함수를 사용하는 것인데요.  
아래의 예시를 보고 이해해보세요.


```python
print("집에 가는 길은 " + str(10) +"분 이나 걸린다.")
```

    집에 가는 길은 10분 이나 걸린다.


## 문자열 합치기

위에서 3개의 문자열들을 하나의 문자열로 합치기 위해서 '+'연산자를 사용했죠?  
사실 다른 방법도 있습니다. join함수가 그 주인공이죠.


```python
a = "닭다리잡고"
b = "삐약삐약"

결과 = "~".join([a, b])
결과
```




    '닭다리잡고~삐약삐약'



잘 보셨죠? 한가지 조심하셔야 할 것은, 
1. join함수는 연결자의 뒤에 마침표를 찍고 사용하는 형식이라는 것.
2. 그리고 join함수는 인자로 하나의 리스트를 받기 때문에, 연결하고자 하는 문자열들을 리스트로 만들어서 집어넣어야 한다.  

라는 것입니다.

## 문자열의 특정 요소를 다른 것으로 치환하기

2022.04.04 라는 날짜의 표현 방식을 마침표가 아닌 다른 것으로 바꾸고 싶다면 어떻게 할까요?


```python
"2022.04.04".replace(".", "-")
```




    '2022-04-04'



>대상문자열.replace("바뀔 대상", "바꿀 문자열")  

의 형식으로 쓰면 됩니다!!  

하나 더 해볼까요?


```python
"마른 하늘을 달리는 달팽이".replace(" ", "_")
```




    '마른_하늘을_달리는_달팽이'



문자열 내부의 공백을 언더바로 치환 해 버렸습니다!!

여기까지 보시고 잘 익히셨으면 문자열을 다루는 기본기는 익히신 것입니다!  
이제 코딩의 결과로 얻어진 결과를 보기좋게 정돈하거나, 필요한 입력값의 형태로 조작하는 데 무리가 없으실 거라 생각합니다. 축하합니다!!!


```python

```
