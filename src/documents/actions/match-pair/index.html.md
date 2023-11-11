---
layout: page
title: 균형 맞춤
menuOrder: 2
---

잘 알려진 태그 균형 맞춤 기능입니다: 현재 커서 위치에서 태그 또는 태그의 내용 경계를 검색하고 선택합니다. 여러 번 호출하면 선택 범위를 확장(외부 균형)하거나 축소(내부 균형)합니다. 일부 구현 문제로 인해 모든 에디터가 내부 및 외부 균형 모두를 지원하지는 않으며, 대부분의 에디터는 외부 균형만을 지원합니다.

<textarea class="movie-def">
&lt;div id="page"&gt;
	&lt;section class="content"&gt;
		&lt;h1&gt;Document example&lt;/h1&gt;
		&lt;p&gt;Lorem ipsum |dolor sit amet.&lt;/p&gt;
	&lt;/section&gt;
&lt;/div&gt;
@@@
tooltip: Place caret inside tag’s content and run “Balance” action to select it
run: emmet.balance_outward ::: “외부로 균형 맞춤” (Cmd-D)
wait: 1000
tooltip: Run action multiple times to expand selection
run: {command: 'emmet.balance_outward', times: 5}
wait: 1000
tooltip: Run “Balance Inward” action to shrink selection
wait: 1000
run: {command: 'emmet.balance_inward', times: 5} ::: “내부로 균형 맞춤 (Shift-Cmd-D)
</textarea>

Emmet의 태그 균형 맞춤은 매우 독특합니다. 다른 구현과 달리, 이 기능은 문서의 시작이 아닌 커서 위치에서 태그 경계를 검색합니다. 이는 비 HTML 문서에서도 태그 균형 맞춤을 사용할 수 있음을 의미합니다.

<textarea class="movie-def">
function test(data) {
	var out = '&lt;table&gt;';
	for (var i = data.rows.length - 1; i >= 0; i--) {
		var row = data.rows[i];
		out += '&lt;tr&gt;';

    	for (var j = row.cells.length - 1; j >= 0; j--) {
    		out += '&lt;td&gt;' + row.|cells[j] + '&lt;/td&gt;';
    	}

    	out += '&lt;/tr&gt;';
    }

    out += '&lt;/table&gt;';
    return out;

}
@@@
tooltip: {text: 'Place caret somewhere between opening and closing tag. Run “Balance” action and, if tag definitions are consistent enough, they will match', wait: 7000}
run: {command: 'emmet.balance_outward', times: 6} ::: Balance” (Cmd-D)
@@@
mode: text/javascript
</textarea>

태그 정의가 문자열을 연결하여 만들어진 경우, 예를 들어 `var cell = '<td class="' + (data.odd ? 'odd' : 'even') + '">';`와 같은 경우, HTML 외부에서 태그 매칭이 작동하지 않을 수 있음을 참고하세요.
