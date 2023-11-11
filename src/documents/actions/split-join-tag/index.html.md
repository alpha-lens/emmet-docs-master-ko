---
layout: page
title: 태그 분리/결합
menuOrder: 7
---

이 작업은 태그 정의를 분리하고 결합합니다, 예를 들어 `<tag/>`를 `<tag></tag>`로 변환하거나 그 반대로 변환합니다. XML/XSL 개발자에게 매우 유용합니다.
<textarea class="movie-def">
&lt;example&gt;
|Lorem ipsum dolor sit amet
&lt;/example&gt;

```
run: emmet.split_join_tag ::: “태그 분리/결합” (Cmd-J)
wait: 1000
moveTo: 6
wait: 1000
run: emmet.split_join_tag
</textarea>

----------------

"태그 분리/결합" 작업은 내부적으로 "[HTML Matcher](/actions/match-pair/)"를 사용하므로, 비 HTML 구문에서도 작동할 수 있습니다.
```
