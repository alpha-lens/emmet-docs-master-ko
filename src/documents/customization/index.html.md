---
layout: page
title: 사용자 정의
menuOrder: 5
---

Emmet은 플러그인 경험을 세부 조정할 수 있는 다양한 트윅을 제공합니다. 거의 모든 공식적으로 개발된 에디터 플러그인(PSPad과 브라우저 기반을 제외하고)은 **확장 지원**을 가지고 있습니다: Emmet을 확장하기 위해 `json`과 `js` 파일을 넣을 수 있는 특별한 폴더입니다. Emmet이 확장을 위해 어디에서 찾는지 알아보려면 에디터의 플러그인과 함께 제공된 README 파일을 참조하십시오.

확장 폴더에 위치한 각 `.js` 파일은 플러그인 시작 시 로드되고 실행됩니다. `js` 파일을 사용하여 자신만의 [필터](/filters/)나 [액션](/actions/)을 생성하세요: 에디터를 자바스크립트로 스크립팅하기 위해 Emmet 모듈과 바인딩을 사용할 수 있습니다.

`.json` 파일을 사용하여 Emmet 툴킷의 다양한 부분을 세부 조정할 수 있습니다:

<dl>
	<dt>[snippets.json](./snippets/)</dt>
	<dd>자신만의 스니펫을 추가하거나 기존 스니펫을 업데이트하세요</dd>
	<dt>[preferences.json](./preferences/)</dt>
	<dd>일부 Emmet 필터와 액션의 동작을 변경하세요</dd>
	<dt>[syntaxProfiles.json](./syntax-profiles/)</dt>
	<dd>생성된 HTML/XML이 어떻게 보여야 하는지 정의하세요.</dd>
</dl>
