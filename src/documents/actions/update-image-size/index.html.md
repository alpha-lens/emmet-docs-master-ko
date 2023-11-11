---
layout: page
title: 이미지 크기 업데이트
menuOrder: 10
---

많은 웹 개발자들이 `<img>` 태그에 _width_ 와 _height_ 속성을 작성하는 것을 잊어버리는 경우가 많아, 이로 인해 UX가 떨어질 수 있습니다. 이 작업은 이 과정을 자동화하는 데 도움을 줍니다: 단순히 `<img>` 태그 내부에 커서를 두고 이 작업을 실행하여 width와 height 속성을 추가/업데이트하면 됩니다.

CSS에서는 `url()` 함수를 가진 속성 값 내부에 커서를 두면 현재 규칙의 width와 height 속성을 추가/업데이트할 수 있습니다.

<textarea class="movie-def">
|&lt;img src="demo.jpg" alt="" /&gt;
&lt;style&gt;
.block {
	background: url(demo.jpg);
}
&lt;/style&gt;
~~~
tooltip: 커서를 &lt;img&gt; 태그 내부에 두고 “이미지 크기 업데이트”를 실행하여 이미지 크기를 얻습니다
moveTo: 6
wait: 1000
run: emmet.update_image_size ::: “이미지 크기 업데이트” (Shift-Cmd-U)
wait: 1000
tooltip: 이미지 URL이 포함된 값 내부에 커서를 두면 규칙의 너비와 높이 속성을 업데이트합니다
moveTo: 3:22
wait: 1000
run: emmet.update_image_size
</textarea>

이 작업은 절대 URL에 대해서도 작동합니다: 요청된 파일을 호스트 파일의 폴더에서 찾기 시작하고, 그 다음 트리를 따라 올라갑니다.
