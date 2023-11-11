---
layout: page
title: 항목 선택
menuOrder: 5
---

이 작업은 ["편집 지점으로 이동"](/actions/go-to-edit-point/)과 비슷하지만, 중요한 코드 부분을 선택합니다.

HTML에서는 태그 이름, 전체 속성, 속성 값이 이에 해당합니다. class 속성의 경우, 구별되는 클래스도 선택합니다.

<textarea class="movie-def">
|&lt;section&gt;
	&lt;p&gt;&lt;/p&gt;
	&lt;div class="main footer"&gt;&lt;/div&gt;

    &lt;script&gt;var str = '<div class="main footer"></div>';&lt;/script&gt;

&lt;/section&gt;
@@@
run: {command: 'emmet.select_next_item', times: 7} ::: “다음 항목 선택” (Shift-Cmd-.)
wait: 1000
run: {command: 'emmet.select_previous_item', times: 6} ::: “이전 항목 선택” (Shift-Cmd-,)
wait: 1000
moveTo: 4:12
wait: 1000
tooltip: “항목 선택” 작업은 비 HTML 구문에서도 작동할 수 있습니다.
wait: 500
run: {command: 'emmet.select_next_item', times: 5}
</textarea>

CSS에서는 선택자, 전체 속성, 속성 값을 매칭합니다. `1px solid red` 또는 `url(image.jpg)`와 같은 복잡한 값과 함수의 경우, 일부를 선택합니다.

<textarea class="movie-def">
|body {
	border: 1px solid black;
	background: url(image.jpg) #ccc no-repeat;
}
@@@
run: {command: 'emmet.select_next_item', times: 12} ::: “다음 항목 선택” (Shift-Cmd-.)
wait: 1000
run: {command: 'emmet.select_previous_item', times: 11} ::: “이전 항목 선택” (Shift-Cmd-,)
@@@
mode: text/css
</textarea>
