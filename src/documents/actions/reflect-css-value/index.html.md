---
layout: page
title: CSS 값 반영
menuOrder: 13
---

CSS 개발자에게 매우 유용한 작업입니다: 커서 아래의 CSS 속성 값을 가져와 필요한 경우 추가 변환과 함께 vendor-prefixed 변형에 복사합니다.
<textarea class="movie-def">
div {
padding: 10px;
-webkit-transform: rotate(|45deg);
-moz-transform: rotate(45deg);
-ms-transform: rotate(45deg);
-o-transform: rotate(45deg);
transform: rotate(45deg);
}
@@@
tooltip: Modify value of CSS property
wait: 500
run: {command: 'delCharAfter', times: 2}
wait: 500
type: 50
wait: 1000
tooltip: {text: 'Run “Reflect CSS Value” action to copy current value to all its vendor-prefixed variants', wait: 6000}
run: emmet.reflect_css_value ::: “Reflect CSS Value” (Cmd-B)
@@@
mode: text/css
</textarea>
