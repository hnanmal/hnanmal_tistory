# re-frame your ClojureScript applications - Shaun Mahood(Clojure conj 2016 발표 번역-개인공부용)

# CLJS의 Re-frame 프레임워크

요즘 관심이 생겨서 개인적으로 Clojure 컨퍼런스 자료들을 유튜브에서 많이 찾아보고 있는데, 영어의 한계 때문인지 개략적인 흐름을 파악하는 정도로 그쳐서, 발표마다 한 문장씩 해석하면서 공부하는 걸 시작했습니다. 파파고와 구글 번역의 도움을 받아서 초벌 번역을 한 후에, 고유명사 오류를 고치고, 문장 구성을 조금 다듬는 수준에서 번역한 스크립트를 올립니다.

혹시 오번역이 있다면 의견남겨주시기 바랍니다. 공부하는 입장에서 기록 삼아 올리는 것이기 때문에 피드백이 오히려 절실합니다.

번역 및 주석 작업도 계속 업데이트 할 예정입니다.

클로저 컨퍼런스 요약 혹은 번역은 앞으로도 종종 올릴 것 같습니다.

[re-frame your ClojureScript applications - Shaun Mahood](https://youtu.be/cDzjlx6otCU)

# Eng-Kor Script

hi everybody my name is Sean Mahad and today I'm gonna be talking to you about reframe which is a closure script framework for writing single page applications.

안녕하세요 여러분, 제 이름은 Sean Mahad입니다. 오늘 저는 단일 페이지 애플리케이션 작성을 위한 클로저 스크립트 프레임워크인 reframe에 대해 이야기할 것입니다.

And my goal for this talk is to give you enough of a background and enough knowledge that you can get started building your own applications with reframe right away.

그리고 이 강연의 제 목표는 여러분이 바로 리프레임을 사용하여 자신만의 애플리케이션 구축을 시작할 수 있도록 충분한 배경 지식과 충분한 지식을 제공하는 것입니다.

you'll still have to go back to the docs and things because it's only 40 minutes and I can't cover quite everything but should be a pretty good start at least.

발표가 40분짜리이고 모든 것을 다룰 수는 없기 때문에, 제대로 알기위해 여전히 나중에 문서로 자세히 봐야 습득할 수 있습니다만, 적어도 re-frame에 대한 좋은 시작의 계기가 되는 발표가 되면 좋겠습니다.

so instead of showing a presentation I thought it would be a little more fun for us to build one runway there we go.

그래서 프리젠테이션을 보여주는 것보다 거기에 하나의 앱을 빌드하는 것이 조금 더 재미있을 것이라고 생각했습니다.

so we're starting with a blank clojure script file here and I’ve got all the CSS built already so we don’t have to deal with that.

그래서 우리는 여기에서 빈 클로저 스크립트 파일로 시작하고 있으며 이미 모든 CSS가 빌드되어 있으므로 처리할 필요가 없습니다.

and first thing we're gonna do is just add our name space and a few dependencies

가장 먼저 할 일은 이름 공간과 몇 가지 종속 항목을 추가하는 것입니다.

so we have to include 'reagent' for anything that's going to be rendering views because that's what it that's what 're-frame' uses for all your UI definition.

따라서 뷰를 렌더링하는 모든 항목에 대해 'reagent'를 포함해야 합니다. '리프레임'이 모든 UI 정의에 사용하기 때문입니다.

and we're gonna include re-frame because it would be a terrible re-frame talk otherwise.

그렇지 않으면 끔찍한 '리프레임' 이야기가 될 것이기 때문에 '리프레임'을 포함할 것입니다.

and then there's a library here re-frisk which is relatively new and immature but the developer has been doing a lot of great work with it and it's very easy to add quick visualizations.

그리고 여기 're-frisk'라는 라이브러리가 있습니다. 이 라이브러리는 상대적으로 새롭고 미성숙하지만 개발자가 이 라이브러리로 많은 작업을 해왔으며 빠른 시각화를 추가하기가 매우 쉽습니다.

and then spec because I went to the workshop and it's kind of fun.

그리고 종속 항목에 ‘spec’도 포함시킵니다. 왜냐하면 워크샵에 갔을때 재미있었고,

and then we have this as views as well that is just a little bit of helper stuff I don't want to throw in the same file

그런 다음 우리는 같은 파일에 넣고 싶지 않은 약간의 보조 항목인 뷰로 이것을 가지고 있습니다.

and I'm gonna I'm cheating by using ‘cursive’ live templates or IntelliJ’s live templates

‘cursive’ 라이브 템플릿 또는 IntelliJ의 라이브 템플릿을 사용하여 조금 쉽게 코딩을 할 것이고요.

so we're gonna start by defining a few ‘reagent’ components so we've got our main one which is this slideshow

그래서 우리는 몇 가지 'reagent' 구성 요소를 정의하는 것으로 시작할 것입니다. 그래서 우리는 이 슬라이드쇼를 메인으로 합니다

and then our title slide and a vector of slides that we can move back and forth between and if you've never used anything with with a ‘hiccup’ markup before, you know it pretty much as HTML you replace your angle brackets with square brackets and kind of squint and you can pretend you're just doing normal web development and we need to add something to render to our screen.

그런 다음 타이틀 슬라이드와 우리가 앞뒤로 움직일 수 있는 슬라이드 벡터를 사용할 수 있습니다. 이전에 hiccup 마크업으로 어떤 것도 사용해 본 적이 없다면 HTML과 마찬가지로 각괄호를 사각괄호와 콜론(:)으로 대체하고 일반적인 웹 개발을 하는 것처럼 코딩하며 화면에 렌더링할 항목을 추가할 수 있습니다.

so we use this reagent render method and it takes any valid reagent component

그래서 우리는 이 'reagent' 렌더 방법을 사용하고 그것은 유효한 'reagent' 구성 요소를 필요로 합니다.

and if i refresh the page we get our first slide up here

페이지를 새로고침하면 여기에 첫 번째 슬라이드가 표시됩니다.

but I hate having to refresh the page

하지만 나는 페이지를 새로 고쳐야 하는 것이 싫습니다.

so we're gonna put in a ‘fig wheel’ with this on-jsload hook it's all built into the project clj

그래서 우리는 이 'on-jsload' hook와 함께 'fig wheel'을 넣을 것입니다. 모두 project clj에 내장되어 있습니다.

and this run function is what we're calling straight from our HTML

그리고 이 실행 함수는 우리가 HTML에서 직접 부르는 것입니다.

so if i refresh it again we've got now live updates with fig wheel and I've added this re-frisk into it

그래서 다시 새로 고치면 우리는 지금 ‘fig wheel’로 라이브 업데이트를 받고 나는 ‘re-frisk’를 거기에 추가했습니다.

and we're gonna keep going with adding some of our views I guess

그리고 우리는 우리의 view 중 일부를 계속 추가할 것입니다.

so I'm going to add this footer for our slides

슬라이드에 이 바닥글을 추가하겠습니다.

and then we're gonna replace our title slide so that we actually have some sort of controls

그런 다음 타이틀 슬라이드를 교체하여 실제로 일종의 제어 기능을 가질 수 있도록 할 것입니다

and let's see I just have to reorder things a bit.

순서를 약간 변경해야 합니다.

and is is the the code on the side is that big enough for everyone

그리고 옆에 있는 코드가 모두에게 충분히 큰가요?

yeah perfect.

네 잘됐군요.

so now we've got these forward and back buttons but they don't do anything

그래서 이제 우리는 앞으로 버튼과 뒤로 버튼을 가지고 있지만 그것들은 아무것도 하지 않습니다.

I've got them hooked to these re-frame dispatch functions but we haven't built those yet so we should probably figure out what we're doing

이 '리프레임' 디스패치 기능에 연결했지만 아직 구축하지 않았으므로 우리가 무엇을 하고 있는지 알아내야 할 것입니다.

so I'm gonna add an extra slide here

여기에 추가 슬라이드를 추가하겠습니다.

and just replace this with our intro slide.

이것을 소개 슬라이드로 바꾸고요.

so we've got our sort of classy marketing spiel here.

그래서 여기에 우리의 품격 있는 마케팅적 홍보문구가 띄워져 있습니다.

but I'm not a huge fan of marketing so I'm gonna cheat a bit here and we're gonna add a bunch of slides down to the bottom that I've already prepared

하지만 저는 마케팅을 별로 좋아하지 않기 때문에 여기서 조금 속이고 제가 이미 준비한 슬라이드를 아래에 추가할 것입니다

clean up some of these

이 코드들 중 일부를 지우고..

let's see what's duplicated

무엇이 복사되었는지 봅시다

this is about my favorite thing about the new fig wheel because I make a lot of mistakes when I'm building a new app.

이것은 내가 새로운 'fig wheel'에서 가장 좋아하는 것에 관한 것입니다. 왜냐하면 나는 새 앱을 빌드할 때 많은 실수를 하기 때문입니다.

and since we don't know how to actually use ‘re-frame’ yet I'm just gonna cheat some more and start moving through the slides manually.

실제로 리프레임을 사용하는 방법을 아직 제대로 소개하지 않았기 때문에 좀 더 꼼수를 써서 슬라이드를 수동으로 이동하기 시작하겠습니다.

so when we're building a single page app mutation is fundamental to everything we do.

그래서 우리가 단일 페이지 앱을 만들 때 'mutation '은 우리가 하는 모든 일의 기본입니다.

we have to change our Dom, change our application state, and most of the time we want to interact with the world somehow.

우리는 Dom을 변경하고 애플리케이션 상태를 변경해야 하며 대부분의 경우 어떻게든 세상과 상호 작용하기를 원합니다.

so we're gonna be changing things on our local machine like local storage and cookies in the browser and then we're gonna be making calls to api's and databases.

따라서 우리는 브라우저의 로컬 저장소 및 쿠키와 같은 로컬 시스템의 항목을 변경한 다음 api 및 데이터베이스를 호출할 것입니다.

and particularly when we don't control those this is like a nightmare of you mutation

그리고 특히 우리가 그것들을 제어하지 않을 때, 'mutation’은 당신의 악몽과 같습니다.

and we have to build that into our app somehow

그리고 우리는 어떻게든 앱에 구축해야 합니다.

but we also really want to program functionally.

하지만 또한 우리는 정말로 함수형으로 프로그래밍하기를 원합니다.

so we want to be changing our Dom functionally which thankfully react was invented we can do that.

그래서 우리는 고맙게도 함수적으로 변경할 수 있도록  'react'가 발명된 Dom을 변경하고 싶습니다.

we want to change our application state functionally and we have all the power of clojure to do that.

우리는 애플리케이션 상태를 함수적으로 변경하고 싶고 이를 수행할 수 있는 클로저의 모든 권한이 있습니다.

and changing the world functionally is a little bit trickier.

세상을 함수적으로 바꾸는 것은 조금 까다롭습니다.

so we need to move all that mutation out to the very edges of our systems.

따라서 우리는 모든 'mutation'을 우리 시스템의 가장자리로 옮겨야 합니다.

so when we're building what our business or our clients want, we don't have to think about it all the time.

따라서 비즈니스나 고객이 원하는 것을 구축할 때 항상 그것에 대해 생각할 필요가 없습니다.

so we're gonna look at sort of the basics of how re-frame works and primarily how do we get change moving through our system.

그래서 우리는 어떻게 리프레임이 작동하는지에 대한 일종의 기본 사항과 주로 어떻게 우리 시스템을 통해 변화를 가져오는지 살펴볼 것입니다.

so re-frame is an event based system and if no events are happening the page is just gonna sit there.

따라서 리프레임은 이벤트 기반 시스템이며 이벤트가 발생하지 않으면 페이지가 그대로 유지됩니다.

so what we'll do whenever an event occurs we're gonna dispatch or whenever an action occurs so whether it's a user clicking something or something returning from an API or calling our set page we're gonna dispatch an event.

따라서 사용자가 클릭하거나, API에서 뭔가 반환되거나, 우리의 set page를 호출하는 등의 동작이 수행되면 이벤트를 dispatch 합니다.

and there's a couple things to know about events in re-frame.

그리고 리프레임의 events에 대해 알아야 할 몇 가지가 있다.

one of them is that it is the only way you should be changing anything in your system.

그것들 중 하나는 그것이 당신의 시스템에서 무언가를 바꿀수 있는 유일한 방법이 되어야 한다는 것입니다.

if you start mutating things directly it it's going to get more and more unpleasant as your application grows

만약 당신이 직접적으로 어떤 것들을 변형시키기 시작한다면 당신의 응용 프로그램이 증가함에 따라 점점 더 불쾌해질 것입니다.

and the other thing that's great about event dispatch is we're dispatching data so all we're gonna send is a vector with our event ID and whatever arguments we want in there.

그리고 이벤트 디스패치의 또 다른 좋은 점은 우리가 데이터를 디스패치한다는 것입니다. 그래서 우리는 우리의 이벤트 ID와 우리가 원하는 모든 인수를 가진 벡터를 보낼 것입니다.

and so that gets sent into re-frame’s central event router which is then which is sort of got an asynchronous first in first out queue and when it goes to actually process that event it's not going to execute any of the effects you've told it to do.

그래서 그것은 re-frame의 중앙 이벤트 라우터로 전송되고, 그 다음에는 일종의 비동기식 퍼스트 아웃 큐를 갖게 되며, 실제로 이벤트를 처리할 때 당신이 하라는 어떤 효과도 실행하지 않을 것입니다.

so if you're telling it to update the database it doesn't immediately action that.

그래서 당신이 데이터베이스를 업데이트하라고 말하면 그것은 즉시 행동하지 않습니다.

it's going to return a map with keys in this case it's gonna be a database key and it's gonna tell you what you what effect you want to have on it.

이 경우에는 키가 있는 맵을 반환할 것입니다. 이 경우에는 데이터베이스 키가 될 것이고 어떤 영향을 미치고 싶은지 알려줄 것입니다.

so again when we run these these event handlers we're getting data out the end.

그래서 다시 이 이벤트 핸들러를 실행할 때 데이터를 끝까지 가져옵니다.

and we do have to realize those effects at some point.

그리고 우리는 어느 시점에서 그 효과를 실현해야 합니다.

but re-frame handles that all for us so it's gonna go how whatever whatever you've defined or the system is defined for you for how to execute those effects re-frames gonna do it in the background you don't really have to worry about it.

하지만 re-frame은 우리를 위해 이 모든 것을 처리하기 때문에 당신이 정의한 것이나 시스템이 그러한 효과를 실행하는 방법에 대해 어떻게 정의되었든 간에 당신은 백그라운드에서 그것을 수행할 것입니다. 당신은 그것에 대해 정말로 걱정할 필요가 없다.

and so one of the expectations is after those effects are realized most of the time your application state will have changed.

따라서 예상되는 것 중 하나는 애플리케이션 상태가 변경되는 대부분의 시간에 이러한 효과가 실현된 후라는 것입니다.

so we want a way for our application state to go and change our views and re-frame does this all reactively.

그래서 우리는 애플리케이션 상태가 이동하고 뷰를 변경하고 프레임을 재구성하여 이 모든 작업을 반응적으로 수행할 수 있는 방법을 원합니다.

so we're going to define some queries on our app state to say this is the part of the data that I care about.

그래서 앱 상태에 대한 몇 가지 쿼리를 정의하여 이것이 내가 관심을 갖고 있는 데이터의 일부라고 말할 것이다.

and whenever the application state changes those query functions are going to rerun.

애플리케이션 상태가 변경될 때마다 해당 쿼리 함수가 다시 실행됩니다.

and they're gonna push out some more data.

그리고 그들은 더 많은 데이터를 내보낼 것입니다.

they're gonna compute our reagent views and update that hiccup data.

그들은 reagent views를 계산하고 해당 hiccup 데이터를 업데이트할 것입니다.

so again we're not worried about actually executing any facts even inside our system.

다시 말하지만 우리는 우리 시스템 안에서조차 어떤 사실도 실제로 실행하는 것에 대해 걱정하지 않t습니다.

those computed views are they going to be pushed by reagent out to react which is going to realize those changes and move them into the DOM.

이러한 계산된 뷰는 'reagent'에 의해 이러한 변경 사항을 인식하고 DOM으로 이동할 'react'으로 푸시될 것입니다.

and our system then is back at rest and waiting for the next event to occur.

그런 다음 우리 시스템은 다시 휴식을 취하고 다음 이벤트가 발생하기를 기다립니다.

so to get started writing a re-frame app we have a few things we need to do.

re-frame 앱 작성을 시작하려면 몇 가지 해야 할 일이 있습니다.

so we're going to define our views which we've already done a couple of.

그래서 우리는 이미 몇 가지 수행했던 뷰를 정의할 것입니다.

we want to define the initial shape of our application state.

애플리케이션 상태의 초기 모양을 정의하려고 합니다.

and this is one of the places that you have a lot of leeway but as your app gets bigger you can start adding things like spec into the initial app State so you can make sure that everything is well-formed.

그리고 이곳은 당신이 많은 여유가 있는 곳 중 하나이지만 당신의 앱이 커짐에 따라 당신은 초기 앱 상태에 스펙과 같은 것들을 추가하여 모든 것이 잘 형성되도록 할 수 있다.

you can also in this step go and pull things out either maybe you're pulling something from local storage or calling some other API to populate your initial data.

또한 이 단계에서 로컬 스토리지에서 무언가를 가져오거나 다른 API를 호출하여 초기 데이터를 채울 수 있습니다.

after that we're gonna register the events we want to run on our on our page and the queries we want to run to populate our views.

그런 다음 페이지에 실행할 이벤트와 실행할 쿼리를 등록하여 views를 채울 것입니다.

then last the last two things we kind of do are just that final plumbing so we're gonna link those queries into our views so we can populate them and link the events so that our users can actually do something.

마지막 두 가지는 최종 배관 작업이므로 쿼리를 뷰에 연결하여 사용자가 실제로 무언가를 수행할 수 있도록 이벤트를 연결합니다.

so we're gonna do here we're gonna add in our initial application state.

여기서 우리는 초기 애플리케이션 상태를 추가할 것입니다.

so we're going to set it our current slide to zero.

따라서 현재 슬라이드를 0으로 설정하겠습니다.

and we're gonna start registering our events.

이벤트 등록을 시작하겠습니다.

so this first event you'll see it we've defined we've got that unique ID which is a name spaced because this was I kind of clean these up after rich and stew stock so now everything is name spaced I think.

그래서 이 첫 번째 이벤트에서 볼 수 있듯이 우리는 고유한 ID를 정의했습니다. 이 고유 ID는 네임스페이스가 지정되어 있습니다. 왜냐하면 이것은 리치 및 스튜 스톡 이후에 이것들을 정리했기 때문입니다.(? 해석안됨) 이제 모든 것이 네임스페이스가 지정되었다고 생각합니다.

and then your function takes as an input context and we don't directly supply that context.

그러면 당신의 함수는 입력 컨텍스트로 간주되며 우리는 그 컨텍스트를 직접 제공하지 않습니다.

it occurs as a result of what's in our system and what we dispatch in our event.

그것은 우리 시스템에 있는 것과 이벤트에서 전달하는 것의 결과로 발생합니다.

so if I were to run this right now nothing happens I've no visibility on what's going on.

따라서 지금 이것을 실행하면 아무 일도 일어나지 않습니다. 무슨 일이 일어나고 있는지 알 수 없습니다.

and I'll zoom in a bit on here so we can see in in re-frisk it gives us this automatic view of our app DB which is where all your applications data is stored.

여기를 조금 확대하면 're-frisk'에서 볼 수 있습니다. 그러면 모든 애플리케이션 데이터가 저장되는 앱 DB가 자동으로 표시됩니다.

but we can also add data to it so we can do kind of the sort of sprinkling our code with all the debug statements we want.

하지만 여기에 데이터를 추가할 수도 있으므로 원하는 모든 디버그 문으로 코드를 뿌릴 수 있습니다.

so if I add this in here I'm just gonna add some data which is going to show us what's in that context.

따라서 여기에 이것을 추가하면 해당 컨텍스트에 무엇이 있는지 보여줄 데이터를 추가할 것입니다.

and if we expand this we can see it's getting in this DB key which is your application database.

이를 확장하면 애플리케이션 데이터베이스인 이 DB 키에 입력되는 것을 볼 수 있습니다.

sorry this is a difficult to move around but.

죄송하지만 이것은 움직이기 어렵네요.

and then it's also getting our event vector which we've just passed in the ID.

그런 다음 방금 ID에 전달한 이벤트 벡터도 가져옵니다.

so because we have all the power of clojure here.

그래서 여기에 클로저의 모든 힘이 있습니다.

we can destructure this and give it a little better of a debug view.

우리는 이것을 분해하고 조금 더 나은 디버그 보기를 제공할 수 있습니다.

see I might have messed something up here but we're gonna try and dispatch this again there we go.

내가 여기서 뭔가를 망쳤을 수도 있지만 우리는 이것을 다시 보내려고 노력할 것입니다.

so now we've got our context broken up into this event and DB as well which makes it a little bit easier to deal with and if you've used the previous re-frame this is essentially what was passed into the old versions of registering the event.

이제 컨텍스트를 이 이벤트와 DB로 나눠 처리하기가 조금 더 쉬워졌습니다. 이전 리프레임을 사용했다면 이는 기본적으로 이벤트 등록의 이전 버전으로 전달된 것입니다.

you just got your database in your event keys.

이제 이벤트 키에 데이터베이스를 넣었습니다.

and what we're gonna do here now is add some output to this.

이제 여기에서 우리가 할 일은 여기에 약간의 출력을 추가하는 것입니다.

I'm just gonna get rid of the old one.

예전 것을 잠시 제거하고,

and so what we've done what I've done here is I've added aspect to say is my current slide in integer because that's what we need.

그래서 제가 여기서 한 일은 제가 현재 하고 있는 슬라이드를 정수로 추가한 것입니다. 왜냐하면 그것이 우리가 필요로 하는 것이기 때문입니다.

and then if it is we're gonna pass back a map of what we want our new database to look like so I'm going to take whatever the existing database is and a so sin this current slide if the slide number is less than the total count of slides we're going to increment it and if not we're just going to return what we had.

그런 다음 새 데이터베이스의 모양에 대한 맵을 다시 전달하므로 기존 데이터베이스가 무엇이든 가져갈 것입니다. 슬라이드 번호가 총 슬라이드 수를 늘리고 그렇지 않은 경우 이전에 있던 것을 반환할 것입니다.

and if spec returns an error we're gonna just display this this error message.

spec이 오류를 반환하면 이 오류 메시지를 표시할 것입니다.

so if I were to dispatch this right now you'll see my application state has nothing in it.

따라서 지금 이것을 발송하면 내 응용 프로그램 상태에 아무것도 없는 것을 볼 수 있습니다.

so I get this spec here but well I get this thing I'm calling a spec error but it's not actually a spec error.

그래서 저는 여기서 이 spec을 얻었지만 제가 spec 오류라고 부르는 것을 얻었지만 실제로는 spec 오류가 아닙니다.

and tells us gives us this message it's not a valid.

이 메시지는 유효하지 않다고 알려줍니다.

and so we need to initialize our data in order to actually start working with it.

따라서 실제로 작업을 시작하려면 데이터를 초기화해야 합니다.

so I'm just going to register this other event slide to initialize.

그래서 이 다른 이벤트 슬라이드를 등록하여 초기화를 하려고 합니다.

we're going to destructure it so we're just worried about the database.

우리는 그것을 해체할 것이므로 데이터베이스에 대해 걱정할 뿐입니다.

and we're just going to replace it with this initial state.

그리고 우리는 이 초기 상태로 대체할 것이다.

and so we've gotten our slideshow current slide is zero.

슬라이드 쇼의 현재 슬라이드는 0입니다.

if I rerun this you'll see it now increments I don't get my spec error anymore.

이것을 다시 실행하면 이제 사양 오류가 더 이상 발생하지 않는 것을 볼 수 있습니다.

so we know our data has initialized successfully.

데이터가 성공적으로 초기화되었음을 알 수 있습니다.

all right.

좋습니다.

now what we're gonna do is just replace this run command here.

이제 우리가 할 일은 여기에서 이 실행 명령을 교체하는 것입니다.

so that along with certainly setting up a re-frisk and mounting our route it's also going to initialize our or application state.

그래서 확실히 're-frisk'을 설정하고 경로를 마운트하는 것과 함께 우리 또는 응용 프로그램 상태를 초기화할 것입니다.

so i refresh this and we zoom in again it's all there.

그래서 이것을 새로 고침하고 다시 확대하면 모든 것이 있습니다.

so we've got our next slide event.

다음 슬라이드 이벤트가 있습니다.

I am gonna want to go back again in case we go back and forth.

우리가 앞뒤로 갈 경우를 대비하여 다시 돌아가고 싶습니다.

so I'm just add a matching a matching event to move to the previous slide.

따라서 이전 슬라이드로 이동하기 위해 일치하는 일치하는 이벤트를 추가합니다.

now we can now move move back and forth in our app dB.

이제 앱 dB에서 앞뒤로 이동할 수 있습니다.

and we can we can do this as well with our buttons they're all wired up properly but our views aren't changing at all.

버튼이 제대로 연결되어 있지만 보기가 전혀 변경되지 않는 경우에도 이 작업을 수행할 수 있습니다.

so we need to get those subscriptions in there and link them up.

그래서 우리는 거기에 subscriptions을 가져와 연결해야 합니다.

so I'm gonna register a subscription that just queries our app DB says give me the key that matches this slideshow current slide and return that value.

그래서 저는 우리 앱 DB를 쿼리하는 subscription을 등록할 것입니다. 이 슬라이드쇼의 현재 슬라이드와 일치하는 키를 제공하고 해당 값을 반환합니다.

and again this subscription is returning data.

다시 이 subscription은 데이터를 반환합니다.

so we don't you know you can do whatever you want with it and this is um this is probably my favorite part of re-frame is that every single step through the system you've got a function you're returning data that data goes into another function and and there's nowhere where you really have this uncontrolled mutation which when I do this myself I usually cheat and I'll have a couple functions here where I was too lazy to make it really nice.

그래서 당신은 그것으로 당신이 원하는 무엇이든 할 수 있고 이것은 음 이것은 아마도 내가 re-frame에서 가장 좋아하는 부분일 것입니다. 시스템을 통한 모든 단일 단계는 당신이 데이터를 반환하고 데이터가 다른 기능으로 들어가는 함수를 가지고 있다는 것입니다. 이 통제되지 않은 'mutation'가 실제로 있는 곳은 어디에도 없습니다. 제가 직접 할 때 저는 보통 속임수를 쓰고 여기에 제가 너무 게을러서 정말 좋게 만들지 못하는 몇 가지 기능이 있습니다.

so we're gonna come in here and start wiring up this our slideshow of you.

그래서 우리는 여기 와서 당신의 슬라이드 쇼를 연결하기 시작할 것입니다.

there we go.

봅시다.

so I'm just gonna replace this here and you can see all we have to do is dereference a call to re-frame subscribe.

그래서 저는 이것을 여기에서 대체할 것입니다. 우리가 해야 할 일은 리프레임 구독에 대한 호출을 역참조하는 것뿐입니다.

we'll pass in the subscription ID that we want to return and this is another area where if you've used the previous version of re-frame before 0.8.

반환하려는 구독 ID를 전달합니다. 이것은 0.8 이전 버전의 re-frame을 사용했다면, 새로운 영역입니다.

this was not really a thing you could do.

이것은 실제로 당신이 할 수 있는 일이 아니었습니다.

the developers have taken it and they've they've kind of really revamped the subscriptions under the hood.

개발자들은 그것을 받아들였고 그들은 후드 아래에서 subscription을 정말 개편했습니다.

so now they are really are now a deduplicated signal graph that instantiates the only when you're looking at those particular subscriptions.

이제는 특정 구독을 볼 때만 인스턴스화하는 중복 제거된 신호 그래프가 되었습니다.

so it's it's kind of cool particularly because it means I can be a little lazier when I'm doing things

특히 내가 무언가를 할 때 조금 더 지연평가할 수 있다는 것을 의미하기 때문에 그것은 일종의 멋진 것입니다.

so when we look at it now we can actually move around in our application.

이제 우리가 그것을 볼 때 우리는 실제로 응용 프로그램에서 이동할 수 있습니다.

and what we want to do now is start growing our app larger than this starting prototype.

이제 우리가 원하는 것은 이 시작 프로토타입보다 앱을 더 크게 성장시키는 것입니다.

and there's a few ways that re-frame gives you that make it really nice to sort of decompose things and then put them back together so that you're always working with something that is understandable.

그리고 're-frame'이 데이터를 분해하고 다시 조립하는 것을 정말로 좋게 만드는 몇 가지 방법이 있습니다. 그래서 여러분은 항상 이해할 수 있는 무언가를 작업할 수 있습니다.

and all your cross-cutting concerns can be moved out into other areas.

모든 교차 절단 문제를 다른 영역으로 옮길 수 있습니다.

and again because it's all data you can test those all those portions as much as you want in different ways.

그리고 다시 모든 데이터이기 때문에 이러한 모든 부분을 다양한 방식으로 원하는 만큼 테스트할 수 있습니다.

there's as well it's all written in cljc and one of the companies who's using it heavily has really invested in the testing tools.

또한 모두 cljc로 작성되었으며 이를 많이 사용하는 회사 중 하나가 실제로 테스트 도구에 투자했습니다.

so they're testing all of their events and I believe all their subscriptions using clojure not clojure script so the runs a lot quicker you don't have to deal with anything you know that is try trim okay I can't remove the name of it but some of those other testing libraries for web apps are not fun.

그래서 그들은 모든 이벤트를 테스트하고 있으며 모든 구독이 clojure 스크립트가 아닌 clojure를 사용한다고 믿습니다. 그러나 웹 앱을 위한 다른 테스트 라이브러리 중 일부는 재미가 없습니다.

so the ways we have to grow our application one of them is with Co effects.

따라서 애플리케이션을 성장시키는 방법 중 하나는 ‘co effects'를 사용하는 것입니다.

and it took me quite a while to understand these but they're not difficult.

이것들을 이해하는 데 꽤 시간이 걸렸지만 어렵지는 않습니다.

so all it is is if an effect is the thing you are doing to the world a co effect is what that effect needs in order to run.

그래서 효과가 당신이 세상에 하고 있는 일이라면 'co effects'는 그 효과가 실행되기 위해 필요한 것입니다.

so it would be whatever parameters you've got you can pass them in through this co effect.

그래서 이 '코이펙트'를 통해 매개 변수를 전달할 수 있습니다.

and this website is really good he does not sure how to pronounce his name but he does he's doing his PhD and parts of it on Co effects and one of the really interesting things about it is you can you can sort of inject things about the world so your function never has to worry about them.

그리고 이 웹사이트는 정말 좋습니다. 그는 자신의 이름을 발음하는 방법을 잘 모르지만 Co 효과에 대한 박사 학위와 그 일부를 수행하고 있으며 정말 흥미로운 점 중 하나는 세상에 대한 정보를 주입할 수 있다는 것입니다. 그래서 당신의 함수는 그것들에 대해 걱정할 필요가 없습니다.

and and one of the examples he's got on his site is GPS coordinates so you can pull them from your phone your app just has them there when it starts.

그의 사이트에 있는 예 중 하나는 GPS 좌표이므로 앱이 시작될 때 휴대전화에서 가져올 수 있습니다.

the other side of that is we can define our own effects so the only effect we've used so far is this database effect which updates the state of our database.

다른 측면은 자체 효과를 정의할 수 있으므로 지금까지 사용한 유일한 효과는 데이터베이스 상태를 업데이트하는 이 데이터베이스 효과입니다.

but there are there are other built-in effects and there's effect libraries already available for reframe and one of them in particular is for HTTP requests.

그러나 다른 기본 제공 효과가 있고 이미 리프레임에 사용할 수 있는 효과 라이브러리가 있으며 그 중 하나는 특히 HTTP 요청용입니다.

so rather than having to build your request writing to your functions you simply add this this key HTTP effects you pass it in some data and it does all the work for you.

따라서 기능에 대한 요청 작성을 작성하는 대신 이 주요 HTTP 효과를 추가하기만 하면 일부 데이터에 전달되고 모든 작업이 수행됩니다.

and I've done some stuff where I've then further wrapped that with my own effect so I don't even have to pass in my API location or anything like that.

그리고 API 위치나 그와 비슷한 것을 전달할 필요조차 없도록 내 자신의 효과로 추가로 래핑하는 몇 가지 작업을 수행했습니다.

and it makes it really nice to sort of just decompose all of those concerns.

이러한 모든 우려 사항을 분해하는 것이 정말 좋습니다.

and the last one that we've got here is interceptors which are very similar to middleware but they give you a little bit more power.

마지막으로 우리가 가지고 있는 인터셉터는 미들웨어와 매우 유사하지만 조금 더 강력한 기능을 제공합니다.

so we're going to look at how we use those.

그래서 우리는 그것들을 어떻게 사용하는지 볼 것입니다.

and let me go right here.

여기를 보시죠.

so what we're gonna do here is I'm gonna add an interceptor that does my logging into re-frisk for me.

여기서 우리가 할 일은 're-frisk'에 로그인하는 인터셉터를 추가하는 것입니다.

so we pass it in and I an ID which is optional but it is kind of nice and then and then we build a before function and this is going to run before our regular event hat Handler.

그래서 우리는 그것을 전달하고 선택 사항이지만 일종의 친절한 ID를 전달한 다음 before 함수를 빌드하고 이것은 정규 이벤트 모자 핸들러보다 먼저 실행될 것입니다.

and we build an after function and both of these are optional so you can do one or the other.

그리고 우리는 after 함수를 만들고 둘 다 선택 사항이므로 둘 중 하나를 수행할 수 있습니다.

and so what I'm going to do here is just when my before handler runs I'm gonna pop out my context at that point and when the after function function runs I'm gonna pop out the contacts there.

여기서 내가 하려는 것은 내 before 핸들러가 실행될 때 그 시점에서 내 컨텍스트를 표시하고 after 함수 함수가 실행될 때 거기에서 연락처를 표시하는 것입니다.

all right so I moved back now and so what you can see is that in here somewhere there we go.

좋아요, 그래서 저는 이제 뒤로 이동했고 여러분이 볼 수 있는 것은 여기 어딘가에 우리가 가는 것입니다.

so I've got this event log which it's it's popped out my event ID previous slide and my before I've got you can see my interceptors can see the co effects which is our context.

그래서 저는 이 이벤트 로그를 얻었습니다. 그것은 제 이벤트 ID 이전 슬라이드에서 튀어나왔으며 제 인터셉터가 우리 컨텍스트인 co effects를 볼 수 있는 것을 볼 수 있습니다.

you can see the co effects that were there before that func that handler run.

핸들러가 실행하는 함수 이전에 있었던 효과를 볼 수 있습니다.

and then it's also got two things in here we've got a stack which is all of the handlers or effects or whatever Co effects everything that's run beforehand.

그리고 여기에는 처리기나 효과 또는 사전에 실행된 모든 것에 영향을 미치는 모든 Co-effects가 있는 스택이 두 개 있습니다.

and I'm not sure of the particular order in this view but you can go through and you can say okay what's already happened do they have a before or after function and easily find that in your code.

그리고 저는 이 보기의 특정 순서에 대해 확신할 수 없지만 훑어볼 수 있고 이미 일어난 일에 괜찮다고 말할 수 있습니다. 이전 또는 이후 함수가 있고 코드에서 쉽게 찾을 수 있습니다.

then we've also got here a queue of things that are gonna run after this particular handler went.

그런 다음 이 특정 핸들러가 실행된 후 실행될 항목의 대기열도 여기에 있습니다.

so it's very nice particular or I use it generally for logging but you can also affect those things in your interceptors.

그래서 그것은 매우 훌륭하거나 일반적으로 로깅에 사용하지만 인터셉터의 이러한 것들에도 영향을 미칠 수 있습니다.

so in our before interceptor we can mess with the context and we can inject more things in we can pull things out you know you can doesn't mean you're gonna always make good decisions about it but at least we have the power to do that.

인터셉터 이전에 우리는 컨텍스트를 망칠 수 있고 더 많은 것을 주입할 수 있습니다. 우리는 무언가를 끌어낼 수 있습니다. 당신이 할 수 있다는 것을 당신이 항상 그것에 대해 좋은 결정을 내릴 것이라는 의미는 아니지만 적어도 우리는 저것을 할 수 있는 힘이 있습니다.

and what I'm gonna do here as well is we're gonna look at oh and sorry I didn't I didn't cover this part but if you look at these functions now all my logging is out of here so my event doesn't have to worry about logging except for adding this logging interceptor.

그리고 여기서도 제가 할 일은 아 그리고 죄송합니다. 이 부분을 다루지 않았습니다. 하지만 지금 이 기능들을 보시면 제 로깅이 모두 빠져있어서 이 로깅 인터셉터를 추가하는 것을 제외하고는 로깅에 대해 걱정할 필요가 없습니다.

and if we wanted to add that through our entire system what we could do is just wrap the event registry function and add that interceptor to everything we called and then run not in our development mode with whatever logging or a testing we want pull it out in production and you're just running happily.

그리고 만약 우리가 전체 시스템을 통해 그것을 추가하고 싶다면, 우리가 할 수 있는 것은 이벤트 레지스트리 기능을 포장하고 우리가 호출한 모든 것에 인터셉터를 추가한 다음, 우리가 원하는 로깅이나 테스트를 통해 개발 모드에서 실행하지 않고 운영 중에 그것을 끄집어내면 당신은 행복하게 실행할 수 있다.

so I'm going to add another interceptor here.

그래서 여기에 또 다른 인터셉터를 추가할 것입니다.

oops oh there we go.

앗, 그렇군요.

no I'm I'm just mixed up about the order sorry.

아니요, 저는 단지 순서에 대해 혼란스러울 뿐입니다. 미안합니다.

what I'm gonna do first is I'm gonna change my initial state here.

가장 먼저 할 일은 여기에서 초기 상태를 변경하는 것입니다.

so we have this other key to test with because if I if I mess with this current slide nothing's gonna render to the page so this is kind of my lazy way of simulating a screw-up.

테스트할 다른 키가 있습니다. 왜냐하면 현재 슬라이드를 엉망으로 만들면 페이지에 아무 것도 렌더링되지 않기 때문입니다.

so I'm gonna just replace these events again and you see now I'm just passing in two interceptors.

그래서 저는 이 이벤트들을 다시 대체할 것입니다. 이제 저는 두 개의 인터셉터를 전달하고 있습니다.

so we're we're gonna move all of our spec checking out there and not not have to worry about it in our event.

그래서 우리는 모든 사양을 확인하고 이벤트에서 걱정할 필요가 없도록 이동할 것입니다.

and so so now I've got in here all of my spec handling and if I if I run my run my application and and it's working.

이제 모든 스펙을 처리하고 애플리케이션을 실행하면 작동합니다.

you can see I get this I get a spec here but I shouldn't I think that's just a bad definition on my side but what I can do is simulate in here I'm gonna look at my broken slide instead.

보시다시피, 저는 이것을 이해합니다. 저는 여기 스펙을 이해하지만, 저는 그것이 제 측면에서 나쁜 정의라고 생각하지 않습니다. 하지만 여기서 제가 할 수 있는 것은 제가 대신에 고장난 슬라이드를 보는 것입니다.

and this should give me a spec error for sure.

그리고 이것은 확실히 나에게 스펙 오류를 줄 것이다.

really all right I might have to just you might have to take this on faith or I can show you after because I made a mistake here.

정말 좋아요, 그냥 당신이 이걸 믿어야 할지도 몰라요 아니면 제가 여기서 실수를 했기 때문에 나중에 보여드릴 수도 있어요.

though an essentially but essentially what it should be doing here.

본질적으로 그러나 본질적으로 여기서 수행해야 하는 작업입니다.

sorry? no the ID doesn't matter on these.

뭐라고요? 아뇨, ID는 이것들에 중요하지 않습니다.

I think I I must have just in copy and paste mode before the talk messed it up.

대화가 엉망이 되기 전에 복사 및 붙여넣기 모드에 있어야 한다고 생각합니다.

but what it what you can do here is I can I don't know I'm gonna do is I'm gonna run my I have a complete application here that should work so.

하지만 당신이 여기서 할 수 있는 일은 내가 할 수 있을지 모른다는 것입니다. 내가 할 수 있는 완전한 애플리케이션을 여기서 실행할 것입니다.(? 해석 이상함: 강연자도 시연이 안풀려서 당황해서 아무말이나 하는 상태 ㅋ)

when the when I'm checking this spec I'm gonna I'm gonna switch it to this broken slide here and when I try and move here all right sorry about that um what you can do essentially is when I run into this error I can clear my entire queue here.

이 '사양'을 확인할 때 여기 깨진 슬라이드로 전환하고 여기로 이동하려고 할 때 죄송합니다. 음 기본적으로 할 수 있는 일은 오류 여기에서 전체 대기열을 지울 수 있습니다.

so along with sending back whatever messages you can also say none of the following events are going to run at all.

따라서 메시지를 다시 보내는 것과 함께 다음 이벤트 중 어느 것도 실행되지 않을 것이라고 말할 수 있습니다.

so it gives you a lot of power to say how do you want to handle errors do you want to kind of just warn do you want to log it do you want to stop the whole system.

따라서 오류를 어떻게 처리할 것인지, 경고만 할 것인지, 전체 시스템을 중지할 것인지를 말할 수 있는 큰 힘을 제공합니다.

and the other thing we're gonna take a quick look at here is how do what we can do with Co effects

그리고 우리가 여기서 간단히 살펴볼 또 다른 것은 코이펙트로 어떻게 할 수 있는가 하는 것이다

just can get our slideshow back.

슬라이드쇼를 다시 가져올 수 있습니다.

so so there's this demo application on the re-frame site which is doing a to-do app .

re-frame 사이트에는 할 일 앱을 수행하는 이 데모 애플리케이션이 있습니다.

and one of the and it's it's got a pretty good set of specs in here and if you're interested in that part you can take a look and see how they've done it.

그리고 그 중 하나는 여기에 꽤 좋은 사양 세트가 있고 그 부분에 관심이 있다면 살펴보고 그들이 어떻게 했는지 볼 수 있습니다.

what it what it also is doing is it's storing to local storage so if we want to declare our own Co effects what would do is we do this register Co effects.

그것은 또한 로컬 스토리지에 저장하는 것이기 때문에 우리가 우리 자신의 'Co effect'를 선언하고 싶다면 이 레지스터 'Co effect'를 실행하는 것입니다.

and here he's just reading in the - dues from the local store and you know in the in the function where we're actually setting those up you can either put those Co effects as part of an interceptor or you can find it here yeah or you can just inject it directly.

그리고 여기서 그는 로컬 저장소에서 due를 읽고 있고 실제로 설정하는 기능에서 'Co effect'를 interceptor의 일부로 넣거나 여기서 찾을 수 있거나 직접 주입할 수 있습니다.

so they're they're injecting these Co effects and then also running the spec interceptor.

그래서 그들은 이 'Co effect'를 주입하고 'spec interceptor'를 실행하고 있다.

and so that's essentially all you need to know to get started with re-frame.

그래서 re-frame을 시작하기 위해서는 기본적으로 이것이 당신이 알아야 할 전부입니다.

there's tons of stuff on the docs I they're good videos on lambda Island that he's recently released purely functional TV has one kind of one hour with re-frame.

문서에는 그가 최근 공개한 람다 섬에 대한 좋은 비디오가 있습니다. 순전히 기능적인 TV에는 '리프레임'이 포함된 1시간 분량이 있습니다.

and if you're if you're coming from the world of reagent most of what you're used to it's probably doing that stuff under the hood.

그리고 만약 당신이 당신이 'reagent'의 세계에서 온 것이라면, 당신이 익숙한 것의 대부분은 아마도 비밀리에 그 일을 하는 것일 것이다.

so you don't have to worry about how you're wiring your application together you can still build your reagent components with local atoms.

따라서 응용 프로그램을 함께 연결하는 방법에 대해 걱정할 필요가 없으며 여전히 로컬 'atom'로 'reagent' 구성 요소를 구축할 수 있습니다.

you can put cursors in if you want and do more complicated local stuff but you really want to be using re-frame for all of your application level organization communication everything along those lines.

더 복잡한 로컬 작업을 원하고 수행하려는 경우 커서를 넣을 수 있지만 해당 라인을 따라 모든 응용 프로그램 수준 조직 통신에 대해 '리프레임'을 사용하고 싶습니다.

and that is all the material I have for today.

오늘 발표 내용은 이걸로 끝입니다.

so thank you very much for coming to the talk and I'll take questions after.

강연에 와주셔서 대단히 감사합니다. 질문은 나중에 받겠습니다.

[Applause]