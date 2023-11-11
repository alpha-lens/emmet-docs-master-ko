---
layout: page
title: 약어로 감싸기
menuOrder: 3
---

Emmet 툴킷의 매우 강력한 도구입니다. 이 작업은 [약어](/abbreviations/)를 받아 확장하고, 생성된 스니펫의 마지막 요소에 현재 선택한 내용을 삽입합니다. 선택한 부분이 없는 경우, 이 작업은 [“태그 쌍 매치”](/actions/match-pair/)를 조용히 호출하여 컨텍스트 요소를 감쌉니다.

<textarea class="movie-def">
&lt;div id="page"&gt;
	&lt;p|&gt;Hello world&lt;/p&gt;
&lt;/div&gt;
~~~
tooltip: 감싸고 싶은 태그(또는 태그 내용) 내부에 커서를 두고 "약어로 감싸기" 작업을 실행합니다
prompt: {text: '.wrapper>h1{Title}+.content', title: 'Enter abbreviation'}  ::: “약어로 감싸기” (Shift-Cmd-A)
run: {command: function(editor){CodeMirror.commands.wrapWithAbbreviation(editor, 'div.wrapper>h1{Title}+.content');}}
</textarea>

## 개별 라인 감싸기

웹 개발자들은 자주 텍스트를 HTML 태그로 감싸야 하는 경우가 많습니다. 예를 들어, 클라이언트로부터 텍스트 문서를 받았을 때 각 단락을 `<p>` 태그로, 메뉴 항목 목록을 `<ul>/<li>` 구조로 감싸야 할 수 있습니다.

[문법](/abbreviations/syntax/)에서 배운 것처럼 곱셈 연산자를 사용하여 요소를 반복할 수 있다는 것을 알 수 있습니다, 예를 들면 `ul>li*5`와 같이 사용할 수 있습니다. 이와 같은 연산자를 _반복 요소를 표시하는_ 데 사용할 수 있습니다. 즉, Emmet에게 표시된 요소가 감싸진 라인 수만큼 반복되어야 한다고 알릴 수 있습니다.

<textarea class="movie-def">
&lt;div id="page"&gt;
	|
	About
	News
	Products
	Contacts
	
	Lorem ipsum dolor sit amet.
&lt;/div&gt;
~~~
tooltip: 감싸고 싶은 라인을 선택합니다.
moveTo: 2:4
select: 5:13
wait: 1000
tooltip: "약어로 감싸기" 작업을 호출하고 <em>\*</em>로 표시된 반복 요소를 포함한 약어를 입력합니다
prompt: {text: 'nav>ul.nav>li.nav-item$\*>a', title: 'Enter abbreviation'}  ::: “약어로 감싸기” (Shift-Cmd-A)
run: {command: function(editor){CodeMirror.commands.wrapWithAbbreviation(editor, 'nav>ul.nav>li.nav-item$\*>a');}}
</textarea>

감싸는 라인에 곱셈 숫자를 추가할 필요가 없다는 점에 주의하세요(예: `li*5`), 숫자 없이 `*` 연산자를 사용해야 합니다, 예를 들면 `li*`.

## 목록 마커 제거하기

Microsoft Word와 같은 텍스트 에디터에서 텍스트를 복사하면 다음과 같은 목록 블록이 생성됩니다:

    * 순서 없는 항목 1
    * 순서 없는 항목 2
    * 순서 없는 항목 3

    1. 순서 있는 항목 1
    2. 순서 있는 항목 2
    3. 순서 있는 항목 3

이러한 목록들을 `ul>li*` 약어로 감싸려고 하면 다음과 같이 생성됩니다:

    <ul>
    	<li>* 순서 없는 항목 1</li>
    	<li>* 순서 없는 항목 2</li>
    	<li>* 순서 없는 항목 3</li>
    </ul>

이는 매우 불편하게 작동합니다, 왜냐하면 목록 마커를 수동으로 제거해야 하기 때문입니다.

Emmet에게 이 작업을 대신 하게 할 수 있습니다: 간단히 "trim" (`|t`, 파이프-t) 필터를 약어에 추가하면 감싸진 내용에서 목록 마커를 자동으로 제거할 수 있습니다:

<textarea class="movie-def">
&lt;div id="page"&gt;
	|
	1. About
	2. News
	3. Products
	4. Contacts
	
	Lorem ipsum dolor sit amet.
&lt;/div&gt;
~~~
tooltip: 감싸고 싶은 라인을 선택합니다.
moveTo: 2:4
select: 5:15
wait: 1000
tooltip: "약어로 감싸기" 작업을 호출하고, 끝에 <em>|t</em> 필터가 추가된 약어를 입력합니다
prompt: {text: 'ul.nav>li.nav-item$\*>a|t', title: 'Enter abbreviation'}  ::: “약어로 감싸기” (Shift-Cmd-A)
run: {command: function(editor){CodeMirror.commands.wrapWithAbbreviation(editor, 'ul.nav>li.nav-item$\*>a|t');}}
</textarea>

[필터에 대해 더 읽어보기](/filters/)

## 출력 위치 제어하기

기본적으로, 무언가를 감싸면 Emmet은 원래의 내용을 최신 요소 내부에 둡니다. 출력 위치는 `$#` 플레이스홀더를 통해 제어할 수 있습니다. `$#`가 약어 문법의 일부가 아니므로, 속성 값이나 [텍스트 노드](/abbreviations/syntax/) 내부에 위치해야 합니다, 예를 들면 `ul>li[title=$#]*>{$#}+img[alt=$#]`와 같이 사용됩니다.

<textarea class="movie-def">
&lt;div id="page"&gt;
	|
	About
	News
	Products
	Contacts
	
	Lorem ipsum dolor sit amet.
&lt;/div&gt;
~~~
tooltip: 감싸고 싶은 라인을 선택합니다.
moveTo: 2:4
select: 5:13
wait: 1000
tooltip: "약어로 감싸기" 작업을 호출하고 <em>\*</em>로 표시된 반복 요소와 <em>$#</em> 플레이스홀더를 포함한 약어를 입력합니다
prompt: {text: 'ul>li[title=$#]\*>{$#}+img[alt=$#]', title: 'Enter abbreviation'}  ::: “약어로 감싸기” (Shift-Cmd-A)
run: {command: function(editor){CodeMirror.commands.wrapWithAbbreviation(editor, 'ul>li[title=$#]\*>{$#}+img[alt=$#]');}}
</textarea>
