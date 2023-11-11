---
layout: default
title: Emmet 문서
---

# Emmet — 웹 개발자를 위한 필수 툴킷

Emmet은 HTML & CSS 작업 흐름을 크게 향상시킬 수 있는 웹 개발자의 툴킷입니다:

<textarea class="movie-def">
&lt;!doctype html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
    &lt;title&gt;Demo&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    |
&lt;/body&gt;
&lt;/html&gt;
~~~
tooltip: CSS 같은 약어를 입력하세요
type: ul#nav>li.item$*4>a{Item $}
wait: 1000
tooltip: “약어 확장” 액션을 실행하여 HTML로 확장합니다 ::: “약어 확장” (Tab 키)
wait: 600
run: emmet.expand_abbreviation
wait: 1000
tooltip: “다음/이전 편집 지점” 동작으로 중요한 코드 지점을 이동하세요 ::: “다음 편집 지점” (Ctrl-Alt-→) <br> “이전 편집 지점” (Ctrl-Alt-←)
wait: 1000
run: {command: 'emmet.next_edit_point', times: 7}
wait: 1000
tooltip: “밸런스” 동작으로 태그를 선택하세요 ::: “밸런스” (Cmd-D)
run: {command: 'emmet.balance_outward', times: 3}
wait: 1000
moveTo: 102
tooltip: “다음/이전 항목 선택” 동작으로 중요한 부분을 선택하세요 ::: “다음 항목 선택” (Shift-Cmd-.) <br> “이전 항목 선택” (Shift-Cmd-,)
run: {command: 'emmet.select_next_item', times: 7, beforeDelay: 300}
wait: 2000
moveTo: 95
wait: 1000
tooltip: “주석 토글” 동작으로 빠르게 전체 태그를 주석 처리하세요 ::: “주석 토글” (Cmd-/)
run: {command: 'emmet.toggle_comment', times: 2, beforeDelay: 1000}
</textarea>

기본적으로, 대부분의 텍스트 에디터는 *"스니펫"*이라고 불리는 일반적으로 사용되는 코드 청크를 저장하고 재사용할 수 있게 해줍니다. 스니펫은 생산성을 향상시키는 좋은 방법이지만, 모든 구현에는 일반적인 문제점이 있습니다: 먼저 스니펫을 정의해야 하고, 런타임에는 확장할 수 없습니다.

Emmet은 스니펫 아이디어를 완전히 새로운 수준으로 끌어올립니다: _CSS와 비슷한_ 표현식을 입력할 수 있으며, 이 표현식은 동적으로 파싱되고, 약어에 입력하는 내용에 따라 출력을 생성할 수 있습니다. Emmet은 HTML/XML과 CSS에 의존하는 웹 개발자의 작업 흐름에 최적화되어 개발되었지만, 프로그래밍 언어와 함께 사용할 수도 있습니다.

[약어 구문](/abbreviations/)과 사용 가능한 [동작](/actions/)으로 Emmet 학습을 시작하세요.

<a href="http://emmet.io/download/" class="btn btn-primary download-main">다운로드 <span class="download-main__comment">당신이 가장 좋아하는 에디터를 위한 플러그인</span></a>
