---
layout: page
title: 라인 병합
menuOrder: 9
---

많은 에디터들이 비슷한 작업을 제공합니다: 선택한 라인들을 하나로 병합합니다. 하지만 선택한 부분이 없을 때, Emmet은 컨텍스트 HTML 태그를 매칭합니다.

<textarea class="movie-def">
&lt;p&gt;
	Lorem ipsum dolor sit amet.
	|Officiis animi consequuntur iure.
	Ea asperiores aperiam non necessitatibus?
	Expedita iusto cupiditate eum esse
&lt;/p&gt;
~~~
run: emmet.merge_lines ::: “라인 병합” (Shift-Cmd-M)
</textarea>
