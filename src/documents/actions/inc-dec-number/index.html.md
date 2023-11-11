---
layout: page
title: 숫자 증가/감소
menuOrder: 12
---

이 작업은 이름에서 알 수 있듯이, 커서 아래의 숫자를 다양한 단계로 증가시키거나 감소시킵니다: 0.1, 1 또는 10.
<textarea class="movie-def">
body {
padding: 1|0px;
line-height: 1.7;
width: 100%;
}
@@@
run: {command: 'emmet.increment_number_by_1', times: 6} ::: “1씩 증가” (Ctrl-↑)<br />“1씩 감소” (Ctrl-↓)
wait: 1000
moveTo: 2:20
wait: 1000
run: {command: 'emmet.increment_number_by_01', times: 6} ::: “0.1씩 증가” (Ctrl-Alt-↑)<br />“0.1씩 감소” (Ctrl-Alt-↓)
wait: 1000
moveTo: 3:12
run: {command: 'emmet.increment_number_by_10', times: 6} ::: “10씩 증가” (Shift-Ctrl-↑)<br />“10씩 감소” (Shift-Ctrl-↓)
@@@
mode: text/css
</textarea>
