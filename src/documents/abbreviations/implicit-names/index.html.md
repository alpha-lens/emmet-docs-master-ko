---
layout: page
title: 암시적 태그 이름
menuOrder: 3
---

강력한 약어 엔진을 가진 Emmet은 짧은 약어에서 큰 HTML 구조를 확장할 수 있지만, 태그 이름을 작성하는 것은 매우 지루할 수 있습니다.

많은 경우에서 태그 이름을 입력하지 않고 Emmet이 대신하여 대체해줍니다. 예를 들어, `div.content` 대신에 `.content`를 작성하고 이를 `<div class="content"></div>`로 확장할 수 있습니다.

## 작동 원리

약어를 확장할 때, Emmet은 부모 컨텍스트, 즉 약어를 확장하고 있는 HTML 요소를 잡으려고 시도합니다. 컨텍스트를 성공적으로 잡으면, Emmet은 이를 사용하여 암시적 이름을 해결합니다:

<textarea class="movie-def">
&lt;body&gt;
	&lt;div&gt;
		|
	&lt;/div&gt;
	
	&lt;span&gt;&lt;/span&gt;
	
	&lt;ul class="nav"&gt;
		|
	&lt;/ul&gt;
	
&lt;/body&gt;
~~~
type: .item
wait: 1000
tooltip: Expanding abbreviation inside block element, default tag name is *div*
run: emmet.expand_abbreviation
wait: 1000
moveTo: 5:10
type: .item
tooltip: Expanding abbreviation inside inline element, default tag name is *span*
run: emmet.expand_abbreviation
wait: 1000
moveTo: 8:8
type: .item
tooltip: Expanding abbreviation inside list, default tag name is *li*
run: emmet.expand_abbreviation
</textarea>

위의 예에서 볼 수 있듯이, Emmet은 암시적 이름으로 약어를 확장할 때마다 부모 태그 이름을 확인합니다. 다음은 일부 부모 요소에 대해 이름을 해결하는 방법입니다:

- `ul`과 `ol`에 대해 `li`
- `table`, `tbody`, `thead` 및 `tfoot`에 대해 `tr`
- `tr`에 대해 `td`
- `select`와 `optgroup`에 대해 `option`

암시적 및 명시적 태그 이름이 있는 일부 약어 동등물을 살펴보십시오:

<table>
	<tr>
		<td>`.wrap>.content`</td>
		<td>`div.wrap>div.content`</td>
	</tr>
	<tr>
		<td>`em>.info`</td>
		<td>`em>span.info`</td>
	</tr>
	<tr>
		<td>`ul>.item*3`</td>
		<td>`ul>li.item*3`</td>
	</tr>
	<tr>
		<td>`table>#row$*4>[colspan=2]`</td>
		<td>`table>tr#row$*4>td[colspan=2]`</td>
	</tr>
</table>
