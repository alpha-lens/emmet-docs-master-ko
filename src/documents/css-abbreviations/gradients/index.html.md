---
layout: page
title: 그라디언트
menuOrder: 2
---

그라디언트는 CSS3 특성 중 쓰기 어려운 항목 중 하나입니다. 다른 벤더 접두사로 긴 그라디언트 정의를 여러 번 반복해야 합니다. 또한, 모든 그라디언트를 지원하는 브라우저를 커버하려면 세 가지 다른 표기법을 사용해야 합니다: 이전의 웹킷, 현재 지원되는 (`linear-gradient(top, ...)`) 그리고 W3C가 제안한 (`linear-gradient(to bottom, ...)`).

보통 사용자들은 그라디언트 정의를 생성하기 위해 서드파티 GUI를 사용하는 것을 선호하지만, 에디터 내에서 더 빠르게 동일한 작업을 수행할 수 있습니다.

Emmet에는 모든 어려운 작업을 대신 해줄 수 있는 CSS3 그라디언트 생성기가 있습니다:

<textarea class="movie-def">
div {
	|
}
@@@
tooltip: CSS 규칙 내부에서 <strong>lg(...)</strong>로 일반적인 CSS 그라디언트 정의를 입력하세요
type: lg(left, #fc0 30%, red)
wait: 1000
tooltip: 그라디언트 정의를 변환하기 위해 “약어 확장” 작업을 실행합니다 ::: “약어 확장” (Tab 키)
run: emmet.expand_abbreviation
wait: 1000
run: goCharRight
run: {command: "newlineAndIndent", times: 2}
wait: 500
type: border-image: 
tooltip: 속성 값으로 <strong>lg(...)</strong> 정의를 작성하면, Emmet는 그것의 속성 이름을 상속합니다
type: lg(left, #fc0 30%, red)
wait: 500
run: emmet.expand_abbreviation
wait: 1000
moveTo: 9:51
select: 9:54
tooltip: {text: "생성된 그라디언트 정의를 수정하고 “약어 확장” 작업을 다시 실행하여 동일한 CSS 속성 이름을 가진 다른 그라디언트에 변경 사항을 반영할 수 있습니다", wait: 7000}
type: black
wait: 500
run: emmet.expand_abbreviation
@@@
mode: text/css
</textarea>

위의 예에서 볼 수 있듯이, `lg(...)` (또는 `linear-gradient(...)`) 함수로 일반적인 그라디언트 정의를 입력하고 약어를 확장할 수 있습니다. 그라디언트 정의를 속성 값으로 작성하면, Emmet은 이를 분석하고 새 CSS 속성에 대한 참조로 이름을 사용합니다.

## 대체 값

환경 설정에서 `css.gradient.fallback` 옵션을 활성화하여 `background-*` CSS 속성에 대한 그라디언트 정의가 확장될 때마다 대체 `background-color` CSS 속성을 생성할 수 있습니다. 이 대체 속성은 그라디언트 정의의 첫 번째 색상을 포함할 것입니다.

이 옵션은 기본적으로 꺼져 있습니다. 이는 컨텐츠가 이 배경에서 읽을 수 있도록 수동으로 업데이트해야 할 `background-color` 값을 생성하기 때문입니다. 오래된 브라우저에 대해 크게 신경 쓰지 않는다면 이 옵션을 활성화할 수 있습니다.
