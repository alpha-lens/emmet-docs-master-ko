---
layout: page
title: "preferences.json"
menuOrder: 2
---

`preferences.json` 파일은 Emmet의 일부 동작과 리졸버를 수정하는 데 사용됩니다. 이 파일은 키-값 쌍의 간단한 딕셔너리를 포함하고 있습니다.

예를 들어, "[CSS 그라디언트](/css-abbreviations/gradients/)"에서는 정의가 확장될 때 `background-color` 값에 대한 폴백을 활성화하는 `css.gradient.fallback` 옵션에 대한 설명이 있습니다. 이를 활성화하려면, 단순히 이 키를 `preferences.json` 파일에 추가하면 됩니다:

    {
        "css.gradient.fallback": true
    }

다음은 현재 사용 가능한 옵션의 목록입니다:

<div class="emmet-preferences"></div>
