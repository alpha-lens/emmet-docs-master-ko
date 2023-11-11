---
layout: page
title: 요소 유형
menuOrder: 2
---

HTML 및 XML 문서에서 약어를 확장할 때, 모든 약어 부분이 실시간으로 HTML/XML 태그로 변환됩니다. 하지만 `a`나 `img`와 같은 특정 요소는 미리 정의된 속성이 있는 요소로 변환됩니다: `<a href=""></a>`와 `<img src="" alt="" />`. Emmet이 언제 이러한 속성을 추가해야 하는지 어떻게 알고 있는 걸까요?

모든 Emmet 요소 정의는 아래 형식으로 [snippets.json](https://github.com/emmetio/emmet/blob/master/lib/snippets.json) 파일에 저장되어 있습니다:

    {
    	"html": {
    		"abbreviations": {
    			"a": "<a href=\"\">",
    			"link": "<link rel=\"stylesheet\" href=\"\" />"
    			...
    		},
    		"snippets": {
    			"cc:ie6": "<!--[if lte IE 6]>

\t${child}|
<![endif]-->"
...
}
},
"css": {
...
}
}

첫 번째 레벨에서는 요소가 정의된 구문 이름이 있습니다. 구문 섹션 내부에는 *스니펫*과 *약어*라는 두 섹션으로 나뉜 요소 정의가 있습니다.

## 스니펫

스니펫은 모든 프로그래머의 에디터에서처럼 일반 코드 블록일 뿐입니다. 어떤 것이든 작성하면, 어떤 변환 없이 "그대로" 출력됩니다.

## 약어

약어는 실제로 데이터 힌트가 있는 빌딩 블록입니다. Emmet은 주로 HTML/XML 태그를 작성하는 데 사용되므로, _약어 정의는 요소를 설명하기 위해 XML 형식을 사용합니다_.

Emmet은 약어 정의를 파싱하고 다음 데이터를 검색합니다:

- 요소 이름;
- 기본 속성;
- 속성 순서;
- 속성의 기본 값;
- 요소가 닫는 태그를 포함해야 하는지.

위의 HTML 약어 정의를 자세히 살펴보십시오. `link` 요소는 `<link rel="stylesheet" href="" />`로 정의됩니다 (JSON에서는 더블 쿼터를 이스케이프해야 합니다; 또는 대신 싱글 쿼터를 사용하십시오). 이 정의는 `link` 약어에 대해 생성된 태그가 *link*라는 이름을 가져야 하고, 두 개의 속성을 포함해야 하며: *rel*은 기본 값으로 "stylesheet", *href*는 빈 값 (정확히 이 순서로), 그리고 생성된 요소는 닫는 태그를 포함하지 않아야 한다는 것을 말합니다.

`link` 약어를 확장하면, HTML 구문에 대해 다음 출력을 받게 됩니다:

    <link rel="stylesheet" href="">

기본 속성 값을 재정의하고 새로운 것을 추가할 수도 있습니다:

    link[rel=prefetch title="Hello world"]

...는 다음으로 확장됩니다

    <link rel="prefetch" href="" title="Hello world">

자식 요소를 추가할 수도 있으며, 이는 Emmet에게 닫는 태그를 출력하게 합니다:

    link>xsl:apply-templates

...는 다음을 출력합니다

    <link rel="stylesheet" href="">
    	<xsl:apply-templates></xsl:apply-templates>
    </link>

## 별칭

`snippets.json`의 약어 섹션에서는 *별칭*도 정의할 수 있습니다: 일반적으로 사용되는 약어를 참조하는 단축어입니다. 별칭은 다음을 정의하는 데 사용될 수 있습니다:

- 긴 태그 이름에 대한 짧은 이름;
- 일반적으로 사용되는 약어를 참조합니다.

`snippets.json` 파일에서는 다음과 같은 정의를 찾을 수 있습니다:

    ...
    "html": {
    	"abbreviations": {
    		"bq": "blockquote",
    		"ol+": "ol>li"
    	}
    }

위 예에서 `bq` 약어를 확장하면, Emmet은 `blockquote` 약어의 정의를 찾습니다. 존재하지 않는 경우, 단순히 `<blockquote></blockquote>` 요소를 출력합니다. `ol+` 약어는 사실 `ol>li`가 출력하는 것과 동일한 결과를 출력합니다.

`ol+` 정의는 끝에 `+`가 있어서 형제 연산자인 것처럼 보일 수 있습니다. Emmet은 이러한 약어를 올바르게 확장하고, 플러스 기호는 역사적인 이유로 여기에 남아 있습니다. 약어 별칭을 만드는 데 플러스 기호를 사용할 필요가 없다는 것을 기억하십시오.
