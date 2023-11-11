---
layout: page
title: 편집 지점으로 이동
menuOrder: 4
---

이 작업은 HTML 코드 블록에 대해 작동하며, 중요한 코드 지점 사이를 빠르게 이동할 수 있게 해줍니다:

- 태그 사이
- 빈 속성
- 들여쓰기가 있는 새 줄

<textarea class="movie-def">
|&lt;ul&gt;
	&lt;li&gt;&lt;a href=""&gt;&lt;/a&gt;&lt;/li&gt;
	&lt;li&gt;&lt;a href=""&gt;&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
&lt;div&gt;
	|
&lt;/div&gt;

&lt;script&gt;
var str = '&lt;ul&gt;&lt;li&gt;&lt;a&gt;&lt;/a&gt;&lt;/li&gt;&lt;/ul&gt;';
&lt;/script&gt;

```
run: {command: 'emmet.next_edit_point', times: 9} ::: “Next Edit Point” (Ctrl-Alt-→)
wait: 1000
run: {command: 'emmet.prev_edit_point', times: 9} ::: “Previous Edit Point” (Ctrl-Alt-←)
wait: 1000
moveTo: 9:4
wait: 500
tooltip: You can use “Go to Edit Point” action in non-HTML documents too
run: {command: 'emmet.next_edit_point', times: 4}
</textarea>
```
