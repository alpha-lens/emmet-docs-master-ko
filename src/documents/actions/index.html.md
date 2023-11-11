---
layout: page
title: 작업들
menuOrder: 3
---

Emmet은 잘 알려진 CSS 선택자를 사용하여 빛의 속도로 큰 HTML 코드 블록을 작성할 수 있게 해줍니다. 하지만 이것이 웹 개발자가 필요로 하는 유일한 것은 아닙니다: 때때로 HTML과 CSS 코드를 수정하여 버그를 수정하고 새로운 기능을 추가해야 합니다.

Emmet은 편집 경험을 크게 향상시킬 수 있는 매우 독특한 도구를 제공합니다:

<dl>
<dt>[약어 확장](./expand-abbreviation/)</dt>
<dd>네, CSS와 같은 약어를 HTML 코드로 확장하는 _그_ 작업입니다.</dd>

<dt>[태그 쌍 매치](./match-pair/)</dt>
<dd>현재 커서 위치에서 내용, 그리고/또는 열고 닫는 HTML 태그 이름을 선택합니다(즉, "밸런싱"). 비 HTML 구문에서도 _작동하는_ 슈퍼 멋진 구현입니다! 많은 Emmet 작업에서 암시적으로 사용됩니다.</dd>

<dt>[매칭 쌍으로 이동](./go-to-pair/)</dt>
<dd>열고 닫는 HTML 태그 사이를 빠르게 이동합니다.</dd>

<dt>[약어로 감싸기](./wrap-with-abbreviation/)</dt>
<dd>"약어 확장" 작업과 같지만, 선택한 내용을 지능적으로 감쌉니다.</dd>

<dt>[편집 포인트로 이동](./go-to-edit-point/)</dt>
<dd>HTML 코드의 중요한 포인트들 사이를 빠르게 이동합니다.</dd>

<dt>[항목 선택](./select-item/)</dt>
<dd>HTML과 CSS 코드의 중요한 부분들을 빠르게 선택합니다.</dd>

<dt>[주석 토글](./toggle-comment/)</dt>
<dd>주석을 토글합니다. 기본적인 에디터의 구현과 달리, 선택한 부분이 없을 때 HTML 태그, CSS 속성 또는 규칙을 매치합니다.</dd>

<dt>[태그 분리/결합](./split-join-tag/)</dt>
<dd>현재 커서 위치의 HTML/XML 태그를 분리(`<tag />` → `<tag></tag>`)하거나 결합(`<tag></tag>` → `<tag />`)합니다.</dd>

<dt>[태그 제거](./remove-tag/)</dt>
<dd>현재 커서 위치의 HTML/XML 태그를 원활하게 제거합니다.</dd>

<dt>[라인 병합](./merge-lines/)</dt>
<dd>선택한 라인들을 하나로 병합합니다. 선택한 부분이 없을 경우, 자동으로 가장 가까운 HTML 태그를 매치합니다.</dd>

<dt>[이미지 크기 업데이트](./update-image-size/)</dt>
<dd>커서 아래에 위치한 이미지의 크기로 매치된 HTML 태그나 CSS 규칙을 업데이트합니다.</dd>

<dt>[수학 표현식 계산](./evaluate-math/)</dt>
<dd>간단한 수학 표현식을 계산합니다</dd>

<dt>[숫자 증가/감소](./inc-dec-number/)</dt>
<dd>주어진 단계로 현재 커서 위치의 숫자를 증가시키거나 감소시킵니다.</dd>

<dt>[CSS 값 반영](./reflect-css-value/)</dt>
<dd>현재 커서 위치의 CSS 값을 자동으로 모든 vendor-prefixed 변형에 복사합니다.</dd>

<dt>[이미지를 data:URL로 인코딩/디코딩](./base64/)</dt>
<dd>커서 아래에 있는 이미지를 data:URL 형식으로 인코딩하거나 그 반대로 작동합니다.</dd>

</dl>
