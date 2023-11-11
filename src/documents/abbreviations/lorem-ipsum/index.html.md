---
layout: page
title: “Lorem Ipsum” 생성기
menuOrder: 4
---

[“Lorem ipsum”](http://www.lipsum.com) 더미 텍스트는 많은 웹 개발자들이 실제 데이터를 사용하여 HTML 템플릿이 어떻게 보일지 테스트하는 데 사용됩니다. 종종, 개발자들은 "Lorem ipsum" 텍스트를 생성하기 위해 서드파티 서비스를 사용하지만 이제 에디터 내에서 직접 할 수 있습니다. 단지 `lorem`이나 `lipsum` 약어를 확장하여 다음의 스니펫을 얻을 수 있습니다:

    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eligendi non quis exercitationem culpa nesciunt nihil aut nostrum explicabo reprehenderit optio amet ab temporibus asperiores quasi cupiditate. Voluptatum ducimus voluptates voluptas?

`lorem`은 단지 일반적인 스니펫이 아닙니다 — 실제로 *생성기*입니다. 매번 확장할 때마다 몇 문장으로 나뉜 30-단어 더미 텍스트를 생성합니다.

생성될 단어 수를 약어 내에서 지정할 수 있습니다. 예를 들어, `lorem100`은 100-단어 더미 텍스트를 생성합니다.

## 반복된 “Lorem ipsum”

반복된 요소 내에서 `lorem` 생성기를 사용하여 완전히 무작위 문장으로 채워진 태그를 생성할 수 있습니다. 예를 들어, `p*4>lorem` 약어는 다음과 같은 것을 생성할 것입니다:

    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Qui dicta minus molestiae vel beatae natus eveniet ratione temporibus aperiam harum alias officiis assumenda officia quibusdam deleniti eos cupiditate dolore doloribus!</p>
    <p>Ad dolore dignissimos asperiores dicta facere optio quod commodi nam tempore recusandae. Rerum sed nulla eum vero expedita ex delectus voluptates rem at neque quos facere sequi unde optio aliquam!</p>
    <p>Tenetur quod quidem in voluptatem corporis dolorum dicta sit pariatur porro quaerat autem ipsam odit quam beatae tempora quibusdam illum! Modi velit odio nam nulla unde amet odit pariatur at!</p>
    <p>Consequatur rerum amet fuga expedita sunt et tempora saepe? Iusto nihil explicabo perferendis quos provident delectus ducimus necessitatibus reiciendis optio tempora unde earum doloremque commodi laudantium ad nulla vel odio?</p>

또한, `lorem` 생성기는 `lorem` 요소가 자체 반복될 때 [암시적 태그 이름 해석기](/abbreviations/implicit-names/)를 사용하므로 약어를 줄일 수 있습니다:

`ul.generic-list>lorem10.item*4`

...는 다음을 생성합니다

    <ul class="generic-list">
    	<li class="item">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nam vero.</li>
    	<li class="item">Laboriosam quaerat sapiente minima nam minus similique illum architecto et!</li>
    	<li class="item">Incidunt vitae quae facere ducimus nostrum aliquid dolorum veritatis dicta!</li>
    	<li class="item">Tenetur laborum quod cum excepturi recusandae porro sint quas soluta!</li>
    </ul>
