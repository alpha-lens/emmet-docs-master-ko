---
layout: page
title: Yandex BEM/OOCSS
menuOrder: 1
---

[OOCSS](http://coding.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/)-스타일 또는 특히 [Yandex의 BEM](http://coding.smashingmagazine.com/2012/04/16/a-new-front-end-methodology-bem/) 스타일로 HTML과 CSS 코드를 작성하는 경우, 이 필터를 좋아하게 될 것입니다. 이 필터는 일반적인 블록과 요소 이름을 클래스에 자동으로 삽입하고 별칭을 제공합니다.

간단하게 말해, BEM은 CSS 클래스에 대한 세 가지 개념 유형을 도입합니다: 블록, 요소, 수정자입니다. *블록*은 HTML 페이지의 의미론적 섹션에 대한 네임스페이스의 일종이며, 예를 들어 `search-form`입니다. *요소*는 섹션의 일부이며, 예를 들어 `search-form__query-string`입니다. *수정자*는 블록과 요소의 변형을 정의합니다: `search-form_wide` 또는 `search-form_narrow`입니다. 클래스 이름에서 요소는 `__`(더블 언더스코어)로 분리되고, 수정자는 `_`(싱글 언더스코어)로 분리됩니다.

BEM/OOCSS는 CSS를 유지하고 재사용하는 좋은 방법이지만, Emmet 약어의 도움을 받아도 이러한 클래스 이름을 일반 HTML에 작성하는 것은 매우 지루할 수 있습니다. 약어의 모든 요소에 같은 블록 또는 요소 이름을 작성해야 합니다:

    form.search-form.search-form_wide>input.search-form__query-string+input:s.search-form__btn.search-form__btn_large

`bem` 필터를 사용하면 약어를 조금 더 짧게 만들 수 있습니다:

    form.search-form._wide>input.-query-string+input:s.-btn_large|bem

## 동작 방식

BEM 필터는 개념 유형에 대해 몇 가지 클래스 이름 접두사를 도입합니다: `__` 또는 `-`는 *요소 접두사*이고 `_`는 *수정자 접두사*입니다. 클래스 이름을 이러한 접두사 중 하나로 시작하면 필터가 나머지 부분을 해결해줍니다:

- 클래스 이름을 요소 접두사로 시작하면 필터는 _부모_ 노드에서 *블록 이름*을 해결합니다.
- 클래스 이름을 수정자 접두사로 시작하면 필터는 _현재 또는 부모_ 노드에서 _블록 이름_ 및/또는 *요소 이름*을 해결합니다.
- 요소와 수정자 접두사를 모두 사용하면 필터는 부모 노드에서 *블록 이름*을 해결하고 요소에 "수정되지 않은" 클래스와 "수정된" 클래스를 모두 출력합니다.
- _여러_ 요소 접두사를 사용하면 필터는 _n번째_ 부모 노드에서 블록 이름을 해결합니다.

몇 가지 예는 다음과 같습니다:

<table>
<tr>
<th>약어</th>
<th>결과</th>
</tr>
<tr>
<td>`.b_m`</td>
<td>
<pre><code>&lt;div class="b b_m">&lt;/div></code></pre>
</td>
</tr>

<tr>
<td>`.b_m1._m2`</td>
<td>
<pre><code>&lt;div class="b b\_m1 b\_m2">&lt;/div></code></pre>
</td>
</tr>

<tr>
<td>`.b>._m`</td>
<td>
<pre><code>&lt;div class="b">
	&lt;div class="b b\_m">&lt;/div>
&lt;/div></code></pre>
</td>
</tr>

<tr>
<td>`.b1>.b2_m1>.-e1+.--e2_m2`</td>
<td>
<pre><code>&lt;div class="b1"&gt;
	&lt;div class="b2 b2_m1"&gt;
		&lt;div class="b2\__e1"&gt;&lt;/div&gt;
		&lt;div class="b1\__e2 b1\__e2\_m2"&gt;&lt;/div&gt;
	&lt;/div&gt;
&lt;/div&gt;</code></pre>
</td>
</tr>

</table>

HTML 구문에 대해 `bem` 필터를 항상 기본값으로 설정할 수 있음을 기억하십시오.
