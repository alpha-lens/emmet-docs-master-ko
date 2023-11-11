---
layout: page
title: 일치하는 쌍으로 이동
menuOrder: 2.5
---

HTML에서, 이 기능을 사용하면 시작 태그와 종료 태그 사이를 빠르게 이동할 수 있습니다:

<textarea class="movie-def">
&lt;div id="page"&gt;
	&lt;section class="content"&gt;
		&lt;h1&gt;Document example&lt;/h1&gt;
		&lt;p&gt;Lorem ipsum dolor sit amet.&lt;/p&gt;
	&lt;/section&gt;
&lt;/|div&gt;
~~~
tooltip: {text: 'Place caret inside either opening or closing tag and run “Go to Matching Pair” action to go to the opposite tag pair', wait: 7000}
wait: 1000
run: {command: 'emmet.matching_pair', times: 5} ::: “Go to Matching Pair” (Cmd-T)
</textarea>

---

"일치하는 쌍으로 이동" 작업은 내부적으로 "[HTML Matcher](/actions/match-pair/)"를 사용하므로, 비 HTML 구문에서도 작동할 수 있습니다.
