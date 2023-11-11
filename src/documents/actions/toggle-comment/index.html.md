---
layout: page
title: 주석 토글
menuOrder: 6
---

이 작업은 이름에서 알 수 있듯이, 선택한 부분에 대한 주석을 토글합니다. 거의 모든 프로그래머 텍스트 에디터에 이러한 작업이 있지만, 이 작업은 다르게 작동합니다. 선택한 부분이 없을 때, 에디터의 작업은 현재 라인에 대한 주석을 토글하는 반면 Emmet의 작업은 *현재 컨텍스트*에 대해 이를 수행합니다. HTML의 경우 전체 태그에 대해, CSS의 경우 규칙이나 전체 속성에 대해 작동합니다.

<textarea class="movie-def">
&lt;sty|le&gt;
body {
	padding: 10px; color: black;
}
&lt;/style&gt;
@@@
tooltip: {text: 'HTML 문서에서 선택하지 않고 "주석 토글" 작업을 호출하면 전체 태그에 대해 매치합니다', wait: 7000}
wait: 500
run: {command: 'emmet.toggle_comment', times: 2, beforeDelay: 1000} ::: “주석 토글” (Cmd-/)
wait: 1000
moveTo: 1:3
wait: 1000
tooltip: CSS에서는 커서 위치에 따라 규칙 또는 전체 속성에 대한 주석을 토글합니다
run: {command: 'emmet.toggle_comment', times: 2, beforeDelay: 1000}
wait: 1000
moveTo: 2:11
wait: 1000
run: {command: 'emmet.toggle_comment', times: 2, beforeDelay: 1000}
</textarea>
