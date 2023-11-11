---
layout: page
title: 약어 확장
menuOrder: 1
---

현재 문서의 구문에 따라 [CSS와 비슷한 약어](/abbreviations/)를 HTML/XML/CSS 코드로 확장합니다. 또한, [CSS Gradient](/css-abbreviations/gradients/)를 변환하는 등의 다른 컨텍스트 작업을 수행합니다.

<textarea class="movie-def">
&lt;html&gt;
&lt;head&gt;
	&lt;title&gt;Demo&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
	|
&lt;/body&gt;
&lt;/html&gt;
~~~
tooltip: Type a CSS-like abbreviation
type: #page>(#header>ul#nav>li*4>a)+(#content>h1{Hello world}+p)+#footer
wait: 1000
tooltip: Run “Expand Abbreviation” action ::: “Expand Abbreviation” (Tab key)
run: emmet.expand_abbreviation
</textarea>

생성된 출력에는 여러 개의 *탭 정지*가 포함되어 있으며, 에디터가 이를 지원하는 경우 (Eclipse, Sublime Text 2, Espresso 등) Tab 키를 사용하여 빠르게 이동할 수 있습니다.

일부 에디터 (Eclipse, Sublime Text 2, CodeMirror)에서는 "Expand Abbreviation"을 Tab 키로 호출할 수 있습니다.
