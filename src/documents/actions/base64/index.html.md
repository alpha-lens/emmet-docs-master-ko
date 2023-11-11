---
layout: page
title: "이미지를 data:URL로 인코딩/디코딩"
menuOrder: 14
---

HTML과 CSS는 [data:URL](http://en.wikipedia.org/wiki/Data_URI_scheme) 스키마를 사용하여 외부 리소스를 기본값으로 직접 포함시킬 수 있습니다. 보통, 이미지를 base64로 변환하는 것은 외부 온라인 서비스나 제3자 자산 빌더를 통해 이루어집니다.

그러나 이러한 도구들에는 단점이 있습니다: 온라인 도구에 추가적인 시간을 소비하거나, base64로 변환해야 하는 이미지에 대한 통제를 잃습니다.

Emmet을 사용하면, 에디터 내에서 이미지를 data:URL로 변환할 수 있고, *외부 파일로 다시 변환*할 수도 있습니다.

<textarea class="movie-def">
body {
    background: url(demo.png);
}
@@@
tooltip: Move caret inside image path
wait: 1000
moveTo: 1:24
wait: 1000
tooltip: Run “Encode/Decode Image to data:URL” action ::: “Encode/Decode Image to data:URL” (Shift-Cmd-I)
run: emmet.encode_decode_data_url
@@@
mode: text/css
</textarea>
