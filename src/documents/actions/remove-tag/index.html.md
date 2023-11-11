---
layout: page
title: 태그 제거
menuOrder: 8
---

빠르게 태그를 제거하고 들여쓰기를 조정합니다. 태그는 현재 커서 위치에서 "[Balance](/actions/match-pair/)" 작업을 통해 찾습니다.

<textarea class="movie-def">
&lt;body&gt;
	&lt;div |class="wrapper"&gt;
		&lt;h1&gt;Title&lt;/h1&gt;
		&lt;p&gt;Lorem ipsum dolor sit amet.&lt;/p&gt;
		&lt;p&gt;Officiis animi consequuntur iure.&lt;/p&gt;
		&lt;p&gt;Ea asperiores aperiam non necessitatibus?&lt;/p&gt;
		&lt;p&gt;Expedita iusto cupiditate eum esse.&lt;/p&gt;
	&lt;/div&gt;
&lt;/body&gt;
~~~
tooltip: Place caret somewhere “Balance” action can find tag definition
wait: 1000
run: emmet.remove_tag ::: “태그 제거” (Cmd-K)
</textarea>

---

"태그 제거" 작업은 내부적으로 "[HTML Matcher](/actions/match-pair/)"를 사용하므로, 비 HTML 구문에서도 작동할 수 있습니다.
