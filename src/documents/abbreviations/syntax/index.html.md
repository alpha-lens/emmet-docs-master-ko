---
layout: 페이지
title: 약어 문법
menuTitle: 문법
menuOrder: 1
---

Emmet은 생성된 트리 안에서 요소들의 위치와 요소들의 속성을 설명하기 위해 CSS 선택자와 유사한 문법을 사용합니다.

## 요소들

`div` 또는 `p`와 같은 요소 이름을 사용해 HTML 태그를 *생성*할 수 있습니다. Emmet에는 사용 가능한 태그 이름의 미리 정의된 세트가 없으며, 어떤 단어든 적어 태그로 변환할 수 있습니다: `div` → `<div></div>`, `foo` → `<foo></foo>` 등등.

## 중첩 연산자

중첩 연산자는 생성된 트리 내에서 약어 요소의 위치를 결정하는 데 사용됩니다: 해당 요소가 콘텍스트 요소 내부에 또는 근처에 배치되어야 하는지를 결정합니다.

### 자식: `>`

`>` 연산자를 사용하여 요소를 서로 중첩시킬 수 있습니다:

    div>ul>li

...는 다음과 같이 생성됩니다

    <div>
    	<ul>
    		<li></li>
    	</ul>
    </div>

### 형제: `+`

`+` 연산자를 사용하여 요소를 같은 레벨에서 서로 근처에 배치합니다:

    div+p+bq

...는 다음을 출력합니다

    <div></div>
    <p></p>
    <blockquote></blockquote>

### 올라가기: `^`

`>` 연산자를 사용하면 생성된 트리를 내려가며 모든 형제 요소의 위치는 가장 깊은 요소에 대해 결정됩니다:

    div+div>p>span+em

...는 다음으로 확장됩니다

    <div></div>
    <div>
    	<p><span></span><em></em></p>
    </div>

`^` 연산자를 사용하면 트리에서 한 레벨 올라가고 다음 요소가 나타날 콘텍스트를 변경할 수 있습니다:
div+div>p>span+em^bq
...는 다음을 출력합니다

    <div></div>
    <div>
    	<p><span></span><em></em></p>
    	<blockquote></blockquote>
    </div>

원하는 만큼 많은 `^` 연산자를 사용할 수 있으며, 각 연산자는 한 레벨씩 올라갑니다:

    div+div>p>span+em^^^bq

...는 다음을 출력합니다

    <div></div>
    <div>
    	<p><span></span><em></em></p>
    </div>
    <blockquote></blockquote>

### 곱셈: `*`

`*` 연산자를 사용하면 요소가 몇 번 출력되어야 하는지 정의할 수 있습니다:

    ul>li*5

...는 다음을 출력합니다

<ul>
<li></li>
<li></li>
<li></li>
<li></li>
<li></li>
</ul>

### 그룹: `()`

괄호는 Emmet의 파워 유저들이 복잡한 약어에서 하위 트리를 그룹화하는 데 사용됩니다:

    div>(header>ul>li*2>a)+footer>p

...는 다음으로 확장됩니다

    <div>
    	<header>
    		<ul>
    			<li><a href=""></a></li>
    			<li><a href=""></a></li>
    		</ul>
    	</header>
    	<footer>
    		<p></p>
    	</footer>
    </div>

브라우저의 DOM에서 작업하는 경우, 그룹을 Document Fragments로 생각할 수 있습니다: 각 그룹에는 약어 하위 트리가 포함되어 있으며 모든 후속 요소는 그룹의 첫 번째 요소와 같은 레벨에 삽입됩니다.

그룹을 서로 중첩시키고 곱셈 `*` 연산자와 결합할 수 있습니다:

    (div>dl>(dt+dd)*3)+footer>p

...는 다음을 생성합니다

    <div>
    	<dl>
    		<dt></dt>
    		<dd></dd>
    		<dt></dt>
    		<dd></dd>
    		<dt></dt>
    		<dd></dd>
    	</dl>
    </div>
    <footer>
    	<p></p>
    </footer>

그룹을 사용하면 단일 약어로 전체 페이지 마크업을 작성할 수 있지만, 그렇게 하지 말아 주세요.

## 속성 연산자

속성 연산자는 출력된 요소의 속성을 수정하는 데 사용됩니다. 예를 들어, HTML과 XML에서는 생성된 요소에 빠르게 `class` 속성을 추가할 수 있습니다.

### ID와 CLASS

CSS에서는 `elem#id`와 `elem.class` 표기법을 사용하여 지정된 `id` 또는 `class` 속성을 가진 요소에 도달합니다. Emmet에서는 이와 동일한 문법을 사용하여 지정된 요소에 이러한 속성을 *추가*할 수 있습니다:

    div#header+div.page+div#footer.class1.class2.class3

...는 다음을 출력합니다

    <div id="header"></div>
    <div class="page"></div>
    <div id="footer" class="class1 class2 class3"></div>

### 사용자 정의 속성

`[attr]` 표기법(즉, CSS에서의 표기법)을 사용하여 요소에 사용자 정의 속성을 추가할 수 있습니다:

    td[title="Hello world!" colspan=3]

...는 다음을 출력합니다

    <td title="Hello world!" colspan="3"></td>

- 대괄호 안에 원하는 만큼 많은 속성을 위치시킬 수 있습니다.
- 속성 값을 지정할 필요는 없습니다: `td[colspan title]`은 각 빈 속성 내부에 탭 정지가 있는 `<td colspan="" title="">`을 생성합니다(편집기가 이를 지원하는 경우).
- 속성 값에 따옴표를 사용할 수 있습니다.
- 값에 공백이 없다면 따옴표 없이 값을 사용할 수 있습니다: `td[title=hello colspan=3]`은 동작합니다.

### 항목 번호 매기기: `$`

곱셈 `*` 연산자를 사용하여 요소를 반복할 수 있지만, `$`를 사용하면 그들에게 *번호*를 매길 수 있습니다. 요소의 이름, 속성의 이름 또는 속성의 값 내부에 `$` 연산자를 위치시켜 반복된 요소의 현재 번호를 출력하십시오:

    ul>li.item$*5

...는 다음을 출력합니다

    <ul>
    	<li class="item1"></li>
    	<li class="item2"></li>
    	<li class="item3"></li>
    	<li class="item4"></li>
    	<li class="item5"></li>
    </ul>

여러 개의 `$`를 연속으로 사용하여 번호 앞에 0을 채울 수 있습니다:

    ul>li.item$$$*5

...는 다음을 출력합니다

    <ul>
    	<li class="item001"></li>
    	<li class="item002"></li>
    	<li class="item003"></li>
    	<li class="item004"></li>
    	<li class="item005"></li>
    </ul>

#### 번호 매기기의 기준과 방향 변경

`@` 수정자를 사용하여 번호 매기기의 방향(오름차순 또는 내림차순)과 기준(즉, 시작 값)을 변경할 수 있습니다.

예를 들어, 방향을 변경하려면 `$` 뒤에 `@-`를 추가합니다:

    ul>li.item$@-*5

…는 다음을 출력합니다

    <ul>
    	<li class="item5"></li>
    	<li class="item4"></li>
    	<li class="item3"></li>
    	<li class="item2"></li>
    	<li class="item1"></li>
    </ul>

카운터 기준 값을 변경하려면 `$`에 `@N` 수정자를 추가합니다:

    ul>li.item$@3*5

…는 다음으로 변환됩니다

    <ul>
    	<li class="item3"></li>
    	<li class="item4"></li>
    	<li class="item5"></li>
    	<li class="item6"></li>
    	<li class="item7"></li>
    </ul>

이들 수정자를 함께 사용할 수 있습니다:

    ul>li.item$@-3*5

…는 다음으로 변환됩니다

    <ul>
    	<li class="item7"></li>
    	<li class="item6"></li>
    	<li class="item5"></li>
    	<li class="item4"></li>
    	<li class="item3"></li>
    </ul>

## 텍스트: `{}`

중괄호를 사용하여 요소에 텍스트를 추가할 수 있습니다:

    a{Click me}

...는 다음을 생성합니다

    <a href="">Click me</a>

요소 바로 뒤에 작성된 `{text}`는 별도의 요소(예: `div`, `p` 등)로 사용되고 파싱되지만, 요소 바로 뒤에 작성될 때는 특별한 의미를 가집니다. 예를 들어, `a{click}`와 `a>{click}`는 동일한 출력을 생성하지만, `a{click}+b{here}`와 `a>{click}+b{here}`는 그렇지 않습니다:

<!-- a{click}+b{here} -->

<a href="">click</a><b>here</b>

<!-- a>{click}+b{here} -->

<a href="">click<b>here</b></a>

두 번째 예에서 `<b>` 요소는 `<a>` 요소 _안에_ 배치됩니다. 그리고 그것이 차이점입니다: `{text}`가 요소 바로 뒤에 작성되면 부모 콘텍스트가 변경되지 않습니다. 이것이 중요한 이유를 보여주는 더 복잡한 예를 보여드리겠습니다:

    p>{Click }+a{here}+{ to continue}

...는 다음을 생성합니다

    <p>Click <a href="">here</a> to continue</p>

이 예에서, `Click here to continue`를 `<p>` 요소 안에 작성하려면 `p` 뒤에 `>` 연산자로 명시적으로 트리를 내려가야 합니다. 그러나 `a` 요소의 경우에는 그렇게 할 필요가 없습니다. 왜냐하면 우리는 `here`라는 단어만 있는 `<a>` 요소를 필요로 하며, 부모 콘텍스트를 변경할 필요가 없기 때문입니다.

비교를 위해, 여기에 자식 `>` 연산자 없이 작성된 동일한 약어가 있습니다:

    p{Click }+a{here}+{ to continue}

...는 다음을 생성합니다

    <p>Click </p>
    <a href="">here</a> to continue

## 약어 서식에 대한 참고 사항

Emmet의 약어 문법에 익숙해지면, 약어를 더 읽기 쉽게 만들기 위해 일부 서식을 사용하고 싶을 수 있습니다. 예를 들어, 요소와 연산자 사이에 공백을 사용하는 것과 같습니다:

    (header > ul.nav > li*5) + footer

하지만 이것은 작동하지 않습니다. 왜냐하면 공백은 Emmet이 약어 파싱을 중단하는 *중지 심볼*이기 때문입니다.

많은 사용자들이 각 약어는 새로운 줄에 작성해야 한다고 잘못 생각하고 있지만, 그들은 틀렸습니다: 텍스트 _어디에서나_ 약어를 입력하고 확장할 수 있습니다:

<textarea class="movie-def">
&lt;body&gt;
	|
&lt;/body&gt;
~~~
type: ul#nav>li*4
wait: 1000
run: emmet.expand_abbreviation
wait: 1000
type: Hello world span.info
wait: 1000
tooltip: You don’t need new line to expand abbreviation
wait: 600
run: emmet.expand_abbreviation
wait: 1000
moveTo: 87
wait: 1500
type: span.info
wait: 1000
tooltip:{text: "Emmet is smart enough to understand that you’re trying to expand <strong>span.info</strong> abbreviation, not the <strong>li>span.info</strong> one", wait: 5000}
run: emmet.expand_abbreviation
</textarea>

이것이 Emmet이 중지 심볼(예: 공백)이 필요한 이유입니다. 이를 통해 필요하지 않은 것을 확장하지 않도록 합니다. 아직도 복잡한 약어를 더 읽기 쉽게 만들기 위해 이러한 서식이 필요하다고 생각한다면:

- 약어는 템플릿 언어가 아닙니다, 그들은 "읽기 쉬워야"하는 것이 아니라 "빠르게 확장하고 제거할 수 있어야" 합니다.
- 실제로 복잡한 약어를 작성할 필요는 없습니다. "타이핑"이 웹 개발에서 가장 느린 과정이라고 생각하는 것을 멈추십시오. 단일 복잡한 약어를 구성하는 것은 몇 개의 짧은 약어를 구성하고 타이핑하는 것보다 훨씬 느리고 오류가 더 자주 발생한다는 것을 빠르게 알게 될 것입니다.
