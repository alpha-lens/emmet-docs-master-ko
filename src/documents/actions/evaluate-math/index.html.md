---
layout: page
title: 수학 표현식 평가
menuOrder: 11
---

`2*4`나 `10/2`와 같은 간단한 수학 표현식을 평가하고 그 결과를 출력합니다. `round(a/b)`에 해당하는 `\` 연산자를 사용할 수 있습니다.

숫자 값이 자주 수정되어야 하는 CSS에서 매우 유용합니다.

<textarea class="movie-def">
|
~~~
tooltip: Enter simple math expression and run “Evaluate Math Expression” action
type: 2\*6
wait: 1000
run: emmet.evaluate_math_expression ::: “Evaluate Math Expression” (Shift-Cmd-Y)
wait: 1000
type: {text: ' 10\\\\3'}
wait: 1000
run: emmet.evaluate_math_expression
wait: 1000
type: {text: ' 20\*4+10'}
wait: 1000
run: emmet.evaluate_math_expression
</textarea>
