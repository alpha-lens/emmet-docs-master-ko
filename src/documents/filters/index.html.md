---
layout: page
title: 필터
menuOrder: 4
---

필터는 출력을 에디터에 전달하기 직전에 확장된 약어를 수정하는 특별한 후처리기입니다. 필터가 어떻게 작동하는지 더 잘 이해하기 위해 간단한 튜토리얼을 살펴보겠습니다.

아래의 에디터에서 다음 약어를 확장해 보세요(Tab 키를 사용하여 약어를 확장합니다): `#content>p.title`

<textarea class="cm-box" data-height="150"></textarea>

예상대로 다음 HTML 코드로 확장될 것입니다:

    <div id="content">
    	<p class="title"></p>
    </div>

이제 이 약어를 확장해 보세요: `#content>p.title|e`. 약간 다른 결과를 얻게 될 것입니다:

```xml
&lt;div id="content"&gt;
	&lt;p class="title"&gt;&lt;/p&gt;
&lt;/div&gt;
```

우리는 방금 파이프 문자 뒤에 이름을 추가함으로써 `e` (escape) 필터를 적용했습니다. 이 필터는 Emmet이 출력을 에디터에 전송하기 직전에 모든 XML-안전하지 않은 기호를 엔티티로 이스케이프했습니다. 이제 이것을 시도해 보세요: `#content>p.title|e|e`:

```xml
&amp;lt;div id="content"&amp;gt;
	&amp;lt;p class="title"&amp;gt;&amp;lt;/p&amp;gt;
&amp;lt;/div&amp;gt;
```

우리는 이중 이스케이프 코드(즉, `e` 필터를 두 번 적용했습니다)를 가지게 되었습니다. 여러분이 볼 수 있듯이, 우리는 약어에 원하는 만큼 많은 필터를 적용할 수 있고, 원하는 만큼 많은 횟수로 적용할 수 있습니다.

더 흥미로운 것을 해보겠습니다. 이 약어를 확장해 보세요: `#content>p.title|haml`

    #content
    	%p.title

멋지지 않나요? 우리는 방금 약어를 HAML 템플릿으로 확장했습니다!

여러분이 볼 수 있듯이, 필터링은 Emmet의 핵심 개념입니다. 브라우저의 DOM 모델과 비유를 들면, 약어를 확장할 때마다 먼저 트리로 변환되고, 그런 다음 필터가 각 트리 노드를 거쳐 출력을 수정합니다. 필터는 CSS 규칙 다음에 공백을 배치하는 것과 같은 작은 조정부터 결과를 다른 구문으로 출력하는 것과 같은 보다 복잡한 작업까지 어떤 것도 수행할 수 있습니다. 심지어 HTML 출력도 `html` 필터로 정의됩니다.

## 암시적 필터 호출

약어 바로 뒤에 파이프 문자와 그 이름을 추가함으로써 약어에 필터를 명시적으로 적용할 수 있습니다. 그러나 현재 편집 중인 문서 유형에 따라 필터도 암시적으로 적용될 수 있습니다. HAML 문서에서 약어를 확장할 때마다 `|haml`을 추가하고 싶지 않을 것입니다, 맞나요?

기본 필터는 [snippets.json](https://github.com/emmetio/emmet/blob/master/snippets.json) 파일의 각 구문의 `filters` 섹션에 정의됩니다:

    {
    	...
    	"html": {
    		...
    		"filters": "html"
    	}
    }

이러한 섹션이 없으면 기본적으로 `html` 필터가 적용됩니다. 기본적으로 둘 이상의 필터를 적용하려면 `filters` 섹션에 필터 이름을 쉼표 또는 파이프로 구분된 목록으로 작성할 수 있습니다:
{
...
"html": {
...
"filters": "html, e"
}
}

이제 HTML 문서에서 약어를 확장할 때마다 기본적으로 `html`과 `e` 필터가 적용됩니다.

**하지만 주의하세요!** `snippets.json` 파일의 기본 필터에서 항상 구문 필터 중 하나인 `html` 또는 `haml`을 첫 번째 위치에 두어야 합니다. 그렇지 않으면 구문 필터가 기본 출력 결과를 정의하기 때문에 출력이 비어 있게 될 것입니다.

## 사용 가능한 필터

### HAML 구문: `haml`

HAML 구문 필터: 약어를 HAML 템플릿으로 출력합니다. 기본적으로 HAML 파일에 적용됩니다.

### HTML 구문: `html`

HTML 구문 필터: 약어를 HTML/XML 태그로 출력합니다. HAML 파일을 제외한 모든 곳에 기본적으로 적용됩니다.

### 이스케이프: `e`

XML-안전하지 않은 문자를 이스케이프합니다: `<`, `>` 그리고 `&`.

예를 들어, `div#header|e`는 `&lt;div id="header"&gt;&lt;/div&gt;`로 확장됩니다. 이 필터는 웹사이트에서 코드 스니펫을 보여주고 싶은 기술 블로거/작가에게 매우 유용할 것입니다(CMS에 Emmet 지원을 추가한다면, 물론).

### 주석 태그: `c`

중요한 태그 주변에 주석을 추가합니다. 기본적으로 "중요한 태그"는 `id` 및/또는 `class` 속성을 가진 태그입니다.

    div>div#page>p.title+p|c

...는 다음으로 확장됩니다

    <div>
    	<div id="page">
    		<p class="title"></p>
    		<!-- /.title -->
    		<p></p>
    	</div>
    	<!-- /#page -->
    </div>

이 필터는 재정의할 수 있는 여러 가지 [선호도](/customization/preferences/)를 가지고 있습니다:

- `filter.commentTrigger`: 주석 출력을 트리거할 속성의 목록입니다. 기본값은 `id, class`입니다.
- `filter.commentAfter`: "중요한 태그" 바로 _다음에_ 위치해야 하는 주석의 [ERB 스타일 템플릿](http://underscorejs.org/#template)입니다. 기본값은 `
<!-- /<%= attr("id", "#") %><%= attr("class", ".") %> -->`입니다.
- `filter.commentBefore`: "중요한 태그" 바로 _앞에_ 위치해야 하는 ERB 스타일 템플릿입니다. 기본적으로 비어 있습니다.

### XSL 튜닝: `xsl`

이 필터는 `<xsl:variable>` 및 `<xsl:with-param>` 태그에서 `select` 속성을 제거합니다. _만약 그들이 자식 노드를 가지고 있다면_. 예를 들면:

    ap>wp

다음으로 확장됩니다:

    <xsl:apply-templates select="" mode="">
    	<xsl:with-param name="" select=""/>
    </xsl:apply-templates>

하지만

    ap>wp>call

...는 다음으로 확장됩니다:

    <xsl:apply-templates select="" mode="">
    	<xsl:with-param name="">
    		<xsl:call-template name=""/>
    	</xsl:with-param>
    </xsl:apply-templates>

기본적으로 XSL 파일에 적용됩니다.

### 단일 라인: `s`

변환된 약어를 단일 코드 라인으로 출력합니다. JavaScript, Python, Ruby 등의 프로그래밍 언어에서 템플릿 문자열을 작성하는데 유용합니다. 예를 들어:

`ul>li*4|s`

...는 다음으로 확장됩니다:

    <ul><li></li><li></li><li></li><li></li></ul>

### 라인 마커 자르기: `t`

약어를 감싸는 것만 유용합니다: "[Abbreviation으로 감싸기](/actions/wrap-with-abbreviation/)" 동작에서 설명한 것처럼 감싸진 라인에서 라인 마커를 제거합니다.
