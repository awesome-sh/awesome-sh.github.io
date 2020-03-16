---
layout: post
title:  "[OpenLayers] 시작하기"
categories: WebGIS
tags: Javascript OpenLayers Map WebGIS
---

시작하기 앞서,

<h5>OpenLayers란 무엇인가?</h5>

구글맵(GoogleMap)과 같이 웹 페이지에 동적인 맵을 표출하여

지도기반 서비스를 개발할 수 있도록 도와주는 완전히 공개 된 오픈 소스 JavaScript입니다

<hr>

<h5>OpenLayers 주요 기능</h5>

- 원하는 좌표에 마커 기능

- 그리기(Draw) 기능 ( 점, 선, 원, 다각형 등 )

- 좌표체계의 변환을 돕는 기능 내장

- 레이어 형식을 제공하여 맵위에 레이어를 쌓을 수 있음

- 객체들을 각각 관리할 수 있음

- 좌표와 좌표간 거리 측정 등 다양한 계산 기능

- PostgreSQL(PostGIS), GeoServer를 연동하여 기능을 더욱 더 확장시킬 수 있음

<hr>

<h5>OpenLayers 6.0 적용해보기</h5>

오픈레이어 공식사이트 - <https://openlayers.org/download/>

위 주소로 들어가서 원하는 방법으로 페이지에 바로 적용할 수 있습니다.

가장 간단한 방법인 CDN 방법으로 가져오도록 하겠습니다.

Project를 진행할 Workspace 안에 index.html [html파일] 과 js폴더와 css폴더를 생성합니다

구조로 보면 아래와 같이 됩니다.

```
myWorkSpace  // 프로젝트 폴더
/css
/js
index.html
```

<hr>

index.html 파일 내 <head>와 </head> 사이 아래 코드를 삽입해주세요

아래 태그가 CDN 방식으로 Openlayers를 적용하고 Import 하는 방법입니다.

```
<!-- OpenLayers CDN -->
<script src="https://cdn.rawgit.com/openlayers/openlayers.github.io/master/en/v6.1.1/build/ol.js"></script>
<link rel="stylesheet" href="https://cdn.rawgit.com/openlayers/openlayers.github.io/master/en/v6.1.1/css/ol.css">

<!-- Index CSS 지도에 스타일들을 관리하기 위한 임의 커스텀 CSS -->
<link rel="stylesheet" href="css/style.css">
```

<hr>

그다음 지도가 표출될 엘리먼트를 만들어 줍시다.

index.html 파일 body 부분에 아래 코드를 추가해줍니다.
```
<body>
    <div id="map"></div>
 
    <script src="js/map.js"></script>
</body>
```

<hr>

이제 처음 생성해두었던 [JS] 폴더에 map.js 파일을 생성합니다.

js/map.js
```
/* js/map.js */

var map = new ol.Map({
    var map = new ol.Map({
        target: 'map',  // 위 index.html에 div id가 map인 엘리먼트에 맵을 표출
        layers: [
          new ol.layer.Tile({
            source: new ol.source.OSM()
          })
        ],
        view: new ol.View({
          center: ol.proj.fromLonLat([37.41, 8.82]),  // 맵이 로딩되었을 때 보여질 기본 위치(좌표) 설정
          zoom: 4  // 줌 레벨은 말 그대로 확대 레벨 (숫자가 커질수록 확대 됨)
        })
    });
});
```

<hr>

자 이제 거의다 왔습니다.

다음은 [CSS] 폴더 안에 style.css 파일을 생성 한 뒤 아래와 같이 작성해줍시다.

css/style.css

```
/* css/style.css */
#map {
    width: 100%; // 지도 가로길이
    height: 500px;  // 지도 세로길이
}
```

이렇게 Openlayers맵을 띄우기 위한 준비가 끝났습니다.

모든 파일을 저장하시고 페이지를 새로고침 해봅시다.

<img src="{{ "/assets/191118/1.png" | relative_url }}">   

잘 적용이 되었나요?

저와 같이 대한민국을 센터로 지정하고 싶으시면

Map.js 에 center 부분을 아래와 같이 바꿔주시면 됩니다.

```
js/map.js

var map = new ol.Map({
    var map = new ol.Map({
        target: 'map', 
        layers: [
          new ol.layer.Tile({
            source: new ol.source.OSM()
          })
        ],
        view: new ol.View({
            center: ol.proj.fromLonLat([129, 35.5]),
            zoom: 4
        })
    });
});

```

이상으로 오픈레이어(Openlayers) 시작하기 포스팅을 마무리하도록 하겠습니다.

감사합니다.