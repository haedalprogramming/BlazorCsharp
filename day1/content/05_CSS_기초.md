# CSS 기초

## 목차
- [CSS 기초](#css-기초)
  - [목차](#목차)
  - [What is CSS?](#what-is-css)
    - [CSS를 누가 생성하고 유지 관리하는가?](#css를-누가-생성하고-유지-관리하는가)
    - [CSS 버전](#css-버전)
  - [CSS - Syntax](#css---syntax)
    - [타입 선택자](#타입-선택자)
    - [범용 선택자](#범용-선택자)
    - [하위 선택자](#하위-선택자)
    - [클래스 선택자](#클래스-선택자)
    - [ID 선택자](#id-선택자)
    - [자식 선택자](#자식-선택자)
    - [속성 선택자](#속성-선택자)
    - [다중 스타일 규칙](#다중-스타일-규칙)
    - [그룹화된 선택자](#그룹화된-선택자)
  - [CSS - Inclusion](#css---inclusion)
    - [속성](#속성)
    - [인라인 CSS - style 속성](#인라인-css---style-속성)
    - [속성](#속성-1)
    - [예제](#예제)
    - [외부 CSS - `<link>` 요소](#외부-css---link-요소)
    - [속성](#속성-2)
    - [예제](#예제-1)
    - [임포트된 CSS - `@import` 규칙](#임포트된-css---import-규칙)
    - [예제](#예제-2)
    - [CSS 규칙 재정의](#css-규칙-재정의)
    - [오래된 브라우저 처리](#오래된-브라우저-처리)
    - [CSS 주석](#css-주석)
    - [예제](#예제-3)
  - [CSS - Measurement Units](#css---measurement-units)
  - [CSS - Colors](#css---colors)
    - [CSS 색상 - 16진수 코드](#css-색상---16진수-코드)
    - [CSS 색상 - 짧은 16진수 코드](#css-색상---짧은-16진수-코드)
    - [CSS 색상 - RGB 값](#css-색상---rgb-값)
    - [색상 코드 생성](#색상-코드-생성)
    - [브라우저 안전 색상](#브라우저-안전-색상)
  - [CSS - Backgrounds](#css---backgrounds)
  - [CSS 교육 문서](#css-교육-문서)
    - [배경 색상 설정](#배경-색상-설정)
    - [배경 이미지 설정](#배경-이미지-설정)
    - [배경 이미지 반복](#배경-이미지-반복)
    - [배경 이미지 위치 설정](#배경-이미지-위치-설정)
    - [배경 고정 설정](#배경-고정-설정)
    - [단축 속성](#단축-속성)
  - [CSS - Fonts](#css---fonts)
    - [폰트 패밀리 설정](#폰트-패밀리-설정)
    - [폰트 스타일 설정](#폰트-스타일-설정)
    - [폰트 변형 설정](#폰트-변형-설정)
    - [폰트 두께 설정](#폰트-두께-설정)
    - [폰트 크기 설정](#폰트-크기-설정)
    - [폰트 크기 조정 설정](#폰트-크기-조정-설정)
    - [폰트 스트레치 설정](#폰트-스트레치-설정)
    - [단축 속성](#단축-속성-1)
  - [CSS - Text](#css---text)
    - [텍스트 장식 설정](#텍스트-장식-설정)
    - [텍스트 변환 설정](#텍스트-변환-설정)
    - [공백 설정](#공백-설정)
    - [텍스트 그림자 설정](#텍스트-그림자-설정)
    - [텍스트 색상 설정](#텍스트-색상-설정)
    - [텍스트 방향 설정](#텍스트-방향-설정)
    - [문자 간격 설정](#문자-간격-설정)
    - [단어 간격 설정](#단어-간격-설정)
    - [텍스트 들여쓰기 설정](#텍스트-들여쓰기-설정)
    - [텍스트 정렬 설정](#텍스트-정렬-설정)
    - [텍스트 장식 설정](#텍스트-장식-설정-1)
    - [텍스트 대소문자 설정](#텍스트-대소문자-설정)
    - [텍스트 공백 설정](#텍스트-공백-설정)
    - [텍스트 그림자 설정](#텍스트-그림자-설정-1)
  - [CSS - Using Images](#css---using-images)
    - [이미지 테두리 속성](#이미지-테두리-속성)
    - [이미지 높이 속성](#이미지-높이-속성)
    - [이미지 너비 속성](#이미지-너비-속성)
    - [-moz-opacity 속성](#-moz-opacity-속성)
  - [CSS - Links](#css---links)
    - [링크 색상 설정](#링크-색상-설정)
    - [방문한 링크 색상 설정](#방문한-링크-색상-설정)
    - [마우스를 올렸을 때 링크 색상 변경](#마우스를-올렸을-때-링크-색상-변경)
    - [활성 링크 색상 변경](#활성-링크-색상-변경)
  - [CSS - Tables](#css---tables)
    - [border-collapse 속성](#border-collapse-속성)
    - [border-spacing 속성](#border-spacing-속성)
    - [caption-side 속성](#caption-side-속성)
    - [empty-cells 속성](#empty-cells-속성)
    - [table-layout 속성](#table-layout-속성)
  - [CSS - Borders](#css---borders)
    - [border-color 속성](#border-color-속성)
    - [border-style 속성](#border-style-속성)
    - [border-width 속성](#border-width-속성)
    - [단축 속성을 사용한 테두리 설정](#단축-속성을-사용한-테두리-설정)
  - [CSS - Margins](#css---margins)
    - [margin-right 속성](#margin-right-속성)
    - [Margin 속성](#margin-속성)
    - [margin-bottom 속성](#margin-bottom-속성)
    - [margin-top 속성](#margin-top-속성)
    - [margin-left 속성](#margin-left-속성)
    - [margin-right 속성](#margin-right-속성-1)
  - [CSS - Lists](#css---lists)
    - [list-style-type 속성](#list-style-type-속성)
    - [list-style-position 속성](#list-style-position-속성)
    - [list-style-image 속성](#list-style-image-속성)
    - [list-style 속성](#list-style-속성)
    - [marker-offset 속성](#marker-offset-속성)
  - [CSS - Paddings](#css---paddings)
    - [padding-bottom 속성](#padding-bottom-속성)
    - [padding-top 속성](#padding-top-속성)
    - [padding-left 속성](#padding-left-속성)
    - [padding-right 속성](#padding-right-속성)
    - [padding 속성](#padding-속성)
  - [CSS - Cursors](#css---cursors)
  - [CSS - Outlines](#css---outlines)
    - [outline-width 속성](#outline-width-속성)
    - [outline-style 속성](#outline-style-속성)
    - [outline-color 속성](#outline-color-속성)
    - [outline 속성](#outline-속성)
  - [CSS - Dimension](#css---dimension)
    - [Height 및 Width 속성](#height-및-width-속성)
    - [line-height 속성](#line-height-속성)
    - [max-height 속성](#max-height-속성)
    - [min-height 속성](#min-height-속성)
    - [max-width 속성](#max-width-속성)
    - [min-width 속성](#min-width-속성)
  - [CSS - Scrollbars](#css---scrollbars)
  - [CSS - Visibility](#css---visibility)
  - [CSS - Positioning](#css---positioning)
    - [Absolute Positioning](#absolute-positioning)
    - [Fixed Positioning](#fixed-positioning)
  - [CSS - Layers](#css---layers)
  - [CSS - Pseudo Classes](#css---pseudo-classes)
    - [:link 가상 클래스](#link-가상-클래스)
    - [:visited 가상 클래스](#visited-가상-클래스)
    - [:hover 가상 클래스](#hover-가상-클래스)
    - [:active 가상 클래스](#active-가상-클래스)
    - [:focus 가상 클래스](#focus-가상-클래스)
    - [:first-child 가상 클래스](#first-child-가상-클래스)
    - [:lang 가상 클래스](#lang-가상-클래스)
  - [CSS - Pseudo Elements](#css---pseudo-elements)
    - [:first-line 가상 요소](#first-line-가상-요소)
    - [:first-letter 가상 요소](#first-letter-가상-요소)
    - [:before 가상 요소](#before-가상-요소)
    - [:after 가상 요소](#after-가상-요소)
  - [CSS - @ Rules](#css----rules)
    - [@import 규칙](#import-규칙)
    - [@charset 규칙](#charset-규칙)
    - [@font-face 규칙](#font-face-규칙)
    - [!important 규칙](#important-규칙)
  - [CSS Filters - Text and Image Effects](#css-filters---text-and-image-effects)
    - [예제](#예제-4)
    - [모션 블러](#모션-블러)
    - [예제](#예제-5)
    - [크로마 필터](#크로마-필터)
    - [예제](#예제-6)
    - [드롭 쉐도우 효과](#드롭-쉐도우-효과)
    - [예제](#예제-7)
    - [플립 효과](#플립-효과)
    - [예제](#예제-8)
    - [글로우 효과](#글로우-효과)
    - [예제](#예제-9)
    - [그레이스케일 효과](#그레이스케일-효과)
    - [예제](#예제-10)
    - [인버트 효과](#인버트-효과)
    - [예제](#예제-11)
    - [마스크 효과](#마스크-효과)
    - [예제](#예제-12)
    - [쉐도우 필터](#쉐도우-필터)
    - [예제](#예제-13)
    - [웨이브 효과](#웨이브-효과)
    - [예제](#예제-14)
    - [X-레이 효과](#x-레이-효과)
    - [예제](#예제-15)
  - [CSS - Media Types](#css---media-types)
    - [문서 언어](#문서-언어)
    - [인식된 미디어 유형](#인식된-미디어-유형)
  - [CSS Paged Media - @page Rule](#css-paged-media---page-rule)
    - [페이지 크기 설정](#페이지-크기-설정)
    - [왼쪽, 오른쪽 및 첫 번째 페이지](#왼쪽-오른쪽-및-첫-번째-페이지)
    - [페이지 나누기 제어](#페이지-나누기-제어)
    - [고아(Widows) 및 미망인(Orphans) 제어](#고아widows-및-미망인orphans-제어)
  - [CSS - Aural Media](#css---aural-media)
    - [azimuth 속성](#azimuth-속성)
    - [elevation 속성](#elevation-속성)
    - [cue-after 속성](#cue-after-속성)
    - [cue-before 속성](#cue-before-속성)
    - [cue 속성](#cue-속성)
    - [pause-after 속성](#pause-after-속성)
    - [pause-before 속성](#pause-before-속성)
    - [pause 속성](#pause-속성)
    - [pitch 속성](#pitch-속성)
    - [pitch-range](#pitch-range)
    - [play-during 속성](#play-during-속성)
    - [richness 속성](#richness-속성)
    - [speak 속성](#speak-속성)
    - [speak-numeral 속성](#speak-numeral-속성)
    - [speak-punctuation 속성](#speak-punctuation-속성)
    - [speech-rate 속성](#speech-rate-속성)
    - [stress 속성](#stress-속성)
    - [voice-family 속성](#voice-family-속성)
    - [volume 속성](#volume-속성)
  - [CSS Printing - @media Rule](#css-printing---media-rule)
  - [CSS - Layouts](#css---layouts)
    - [샘플 열 레이아웃](#샘플-열-레이아웃)
  - [CSS - Validations](#css---validations)
    - [HTML 코드를 유효성 검사해야 하는 이유](#html-코드를-유효성-검사해야-하는-이유)
  - [CSS3 - Tutorial](#css3---tutorial)
  - [CSS3 - Rounded Corners](#css3---rounded-corners)
  - [CSS3 - Border Image](#css3---border-image)
    - [예제](#예제-16)
  - [CSS3 - Multi Background](#css3---multi-background)
    - [예제](#예제-17)
    - [다중 배경 크기](#다중-배경-크기)
  - [CSS3 - Colors](#css3---colors)
  - [CSS3 - Gradients](#css3---gradients)
    - [Linear gradients](#linear-gradients)
    - [CSS3 Radial Gradients](#css3-radial-gradients)
    - [CSS3 Repeat Radial Gradients](#css3-repeat-radial-gradients)
  - [CSS3 - Shadow](#css3---shadow)
  - [box shadow](#box-shadow)
  - [CSS3 - Text](#css3---text)
    - [Text-overflow](#text-overflow)
    - [CSS3 Word Breaking](#css3-word-breaking)
    - [CSS Word Wrapping](#css-word-wrapping)
  - [CSS3 - Web Fonts](#css3---web-fonts)
    - [TrueType Fonts (TTF)](#truetype-fonts-ttf)
    - [OpenType Fonts (OTF)](#opentype-fonts-otf)
    - [The Web Open Font Format (WOFF)](#the-web-open-font-format-woff)
    - [SVG Fonts/Shapes](#svg-fontsshapes)
    - [Embedded OpenType Fonts (EOT)](#embedded-opentype-fonts-eot)
    - [Fonts Description](#fonts-description)
  - [CSS3 - 2d Transforms](#css3---2d-transforms)
    - [20도 회전](#20도-회전)
    - [-20도 회전](#-20도-회전)
    - [X축 기울임](#x축-기울임)
    - [Y축 기울임](#y축-기울임)
    - [행렬 변형](#행렬-변형)
  - [CSS3 - 3D Transforms](#css3---3d-transforms)
    - [X축 3D 변형](#x축-3d-변형)
    - [Y축 3D 변형](#y축-3d-변형)
    - [Z축 3D 변형](#z축-3d-변형)
  - [CSS3 - Animation](#css3---animation)
    - [왼쪽으로 움직이는 애니메이션](#왼쪽으로-움직이는-애니메이션)
    - [키프레임을 사용한 왼쪽으로 움직이는 애니메이션](#키프레임을-사용한-왼쪽으로-움직이는-애니메이션)
  - [CSS3 - Multi Columns](#css3---multi-columns)
    - [Example](#example)
  - [CSS3 - User Interface](#css3---user-interface)
    - [resize 속성의 예제](#resize-속성의-예제)
    - [CSS3 Outline offset](#css3-outline-offset)
  - [CSS3 - Box Sizing](#css3---box-sizing)
    - [CSS3 박스 사이징 속성](#css3-박스-사이징-속성)
  - [CSS - Responsive](#css---responsive)
    - [미디어 쿼리](#미디어-쿼리)
    - [부트스트랩 반응형 웹 디자인](#부트스트랩-반응형-웹-디자인)
  - [출처](#출처)
  - [다음](#다음)

---
## What is CSS?

HTML보다 우수한 스타일 − CSS는 HTML보다 훨씬 더 다양한 속성을 가지고 있어, HTML 속성에 비해 HTML 페이지에 훨씬 더 나은 외관을 제공할 수 있습니다.

다중 장치 호환성 − 스타일 시트는 여러 유형의 장치에 맞게 콘텐츠를 최적화할 수 있도록 합니다. 동일한 HTML 문서를 사용하여, PDA 및 휴대 전화와 같은 핸드헬드 장치나 인쇄용으로 다른 버전의 웹사이트를 제공할 수 있습니다.

글로벌 웹 표준 − 이제 HTML 속성은 폐기되고 CSS를 사용하는 것이 권장되고 있습니다. 따라서 미래의 브라우저와 호환되도록 모든 HTML 페이지에 CSS를 사용하는 것이 좋습니다.

### CSS를 누가 생성하고 유지 관리하는가?
CSS는 CSS 작업 그룹이라는 W3C 내의 그룹에 의해 생성되고 유지 관리됩니다. CSS 작업 그룹은 사양이라고 불리는 문서를 만듭니다. 사양이 논의되고 W3C 회원에 의해 공식적으로 비준되면, 이는 권장 사항이 됩니다.

이 비준된 사양은 W3C가 언어의 실제 구현에 대한 통제권이 없기 때문에 권장 사항이라고 합니다. 독립적인 회사 및 조직이 그 소프트웨어를 만듭니다.

참고 − 월드 와이드 웹 컨소시엄, 또는 W3C는 인터넷이 어떻게 작동하고 어떻게 발전해야 하는지에 대해 권장 사항을 만드는 그룹입니다.

### CSS 버전
캐스케이딩 스타일 시트 레벨 1 (CSS1)은 1996년 12월 W3C의 권장 사항으로 나왔습니다. 이 버전은 CSS 언어와 모든 HTML 태그에 대한 간단한 시각적 포맷 모델을 설명합니다.

CSS2는 1998년 5월 W3C의 권장 사항이 되었으며 CSS1을 기반으로 합니다. 이 버전은 프린터 및 오럴 장치 등 미디어별 스타일 시트, 다운로드 가능한 글꼴, 요소 위치 지정 및 테이블에 대한 지원을 추가합니다.

---

## CSS - Syntax

```css
selector { property: value }
```

![](../img/05_CSS_기초/syntax.png)

구문
예제 − 다음과 같이 테이블 테두리를 정의할 수 있습니다 −

```css
table{ border :1px solid #C00; }
```

여기서 table은 선택자이고 border는 속성이며, 1px solid #C00는 해당 속성의 값입니다.

편의에 따라 여러 가지 간단한 방법으로 선택자를 정의할 수 있습니다. 이제 이러한 선택자를 하나씩 살펴보겠습니다.

### 타입 선택자
이것은 우리가 앞에서 본 동일한 선택자입니다. 다시 한번, 모든 레벨 1 제목에 색상을 지정하는 또 다른 예제입니다 −

```css
h1 {
   color: #36CFFF; 
}
```

### 범용 선택자
특정 유형의 요소를 선택하는 대신, 범용 선택자는 모든 요소 유형의 이름과 일치합니다 −

```css
* { 
   color: #000000; 
}
```

이 규칙은 문서의 모든 요소 내용을 검정색으로 렌더링합니다.

### 하위 선택자
특정 요소가 특정 요소 내부에 있을 때만 스타일 규칙을 적용하고 싶다고 가정해 봅시다. 다음 예제에서와 같이, 스타일 규칙은 `<em>` 요소가 `<ul>` 태그 내부에 있을 때만 적용됩니다.

```css
ul em {
   color: #000000; 
}
```

### 클래스 선택자
요소의 class 속성을 기준으로 스타일 규칙을 정의할 수 있습니다. 해당 클래스를 가진 모든 요소는 정의된 규칙에 따라 포맷됩니다.

```css
.black {
   color: #000000; 
}
```

이 규칙은 문서에서 class 속성이 black으로 설정된 모든 요소의 내용을 검정색으로 렌더링합니다. 조금 더 구체적으로 만들 수 있습니다. 예를 들어 −

```css
h1.black {
   color: #000000; 
}
```

이 규칙은 class 속성이 black으로 설정된 `<h1>` 요소에만 내용을 검정색으로 렌더링합니다.

주어진 요소에 여러 클래스 선택자를 적용할 수 있습니다. 다음 예를 고려하십시오 −

```html
<p class = "center bold">
   이 단락은 center와 bold 클래스에 의해 스타일이 적용됩니다.
</p>
```

### ID 선택자
요소의 id 속성을 기준으로 스타일 규칙을 정의할 수 있습니다. 해당 id를 가진 모든 요소는 정의된 규칙에 따라 포맷됩니다.

```css
#black {
   color: #000000; 
}
```

이 규칙은 문서에서 id 속성이 black으로 설정된 모든 요소의 내용을 검정색으로 렌더링합니다. 조금 더 구체적으로 만들 수 있습니다. 예를 들어 −

```css
h1#black {
   color: #000000; 
}
```

이 규칙은 id 속성이 black으로 설정된 `<h1>` 요소에만 내용을 검정색으로 렌더링합니다.

id 선택자의 진정한 힘은 하위 선택자의 기초로 사용될 때 발휘됩니다. 예를 들어 −

```css
#black h2 {
   color: #000000; 
}
```

이 예제에서는 id 속성이 black으로 설정된 태그 내에 있을 때 모든 레벨 2 제목이 검정색으로 표시됩니다.

### 자식 선택자

하위 선택자를 보았습니다. 자손과 매우 유사하지만 기능이 다른 또 다른 유형의 선택자가 있습니다. 다음 예제를 고려하십시오 −

```css
body > p {
   color: #000000; 
}
```

이 규칙은 `<body>` 요소의 직접 자식인 모든 단락을 검정색으로 렌더링합니다. `<div>` 또는 `<td>`와 같은 다른 요소 내부에 있는 다른 단락은 이 규칙의 영향을 받지 않습니다.

### 속성 선택자
특정 속성이 있는 HTML 요소에 스타일을 적용할 수도 있습니다. 아래 스타일 규칙은 type 속성 값이 text인 모든 input 요소와 일치합니다 −

```css
input[type = "text"] {
   color: #000000; 
}
```

이 방법의 장점은 <input type = "submit" /> 요소에 영향을 미치지 않으며, 원하는 텍스트 필드에만 색상이 적용된다는 것입니다.

속성 선택자에 적용되는 다음 규칙이 있습니다.

- p[lang] − lang 속성이 있는 모든 단락 요소를 선택합니다.
- p[lang="fr"] − lang 속성 값이 정확히 "fr"인 모든 단락 요소를 선택합니다.
- p[lang~="fr"] − lang 속성에 "fr"이라는 단어가 포함된 모든 단락 요소를 선택합니다.
- p[lang|="en"] − lang 속성 값이 정확히 "en"이거나 "en-"으로 시작하는 모든 단락 요소를 선택합니다.

### 다중 스타일 규칙
단일 요소에 여러 스타일 규칙을 정의해야 할 수도 있습니다. 이러한 규칙을 정의하여 여러 속성과 해당 값을 하나의 블록으로 결합할 수 있습니다. 다음 예제와 같이 정의할 수 있습니다 −

```css
h1 {
   color: #36C;
   font-weight: normal;
   letter-spacing: .4em;
   margin-bottom: 1em;
   text-transform: lowercase;
}
```

여기서 모든 속성과 값 쌍은 세미콜론(;)으로 구분됩니다. 단일 줄이나 여러 줄로 유지할 수 있습니다. 가독성을 위해 우리는 별도의 줄에 유지합니다.

잠시 동안 위 블록에 언급된 속성에 대해 걱정하지 마십시오. 이러한 속성은 다가오는 장에서 설명되며 CSS 참조에서 속성에 대한 완전한 세부 정보를 찾을 수 있습니다.

### 그룹화된 선택자
원하는 경우 여러 선택자에 스타일을 적용할 수 있습니다. 다음 예제와 같이 선택자를 쉼표로 구분하기만 하면 됩니다 −

```css
h1, h2, h3 {
   color: #36C;
   font-weight: normal;
   letter-spacing: .4em;
   margin-bottom: 1em;
   text-transform: lowercase;
}
```

이 스타일 규칙은 h1, h2 및 h3 요소에도 적용됩니다. 목록의 순서는 상관이 없습니다. 선택자의 모든 요소는 해당 선언이 적용됩니다.

아래와 같이 다양한 id 선택자를 함께 결합할 수 있습니다 −

```css
#content, #footer, #supplement {
   position: absolute;
   left: 510px;
   width: 200px;
}
```

---

## CSS - Inclusion

```html
<head> <style type = "text/css" media = "all"> body { background-color: linen; } h1 { color: maroon; margin-left: 40px; } </style> </head> <body> <h1>This is a heading</h1> <p>This is a paragraph.</p> </body> </html>
```
이것은 다음과 같은 결과를 생성합니다 −

### 속성
`<style>` 요소와 관련된 속성은 다음과 같습니다 −

| 속성      | 값       | 설명                                                                                      |
|-----------|----------|-------------------------------------------------------------------------------------------|
| type      | text/css | 스타일 시트 언어를 콘텐츠 유형(MIME 유형)으로 지정합니다. 이 속성은 필수 속성입니다.         |
| media     |          | 문서가 표시될 장치를 지정합니다. 기본값은 all입니다. 이 속성은 선택적 속성입니다.          |

### 인라인 CSS - style 속성
모든 HTML 요소의 style 속성을 사용하여 스타일 규칙을 정의할 수 있습니다. 이러한 규칙은 해당 요소에만 적용됩니다. 다음은 일반 구문입니다 −

```html
<element style = "...style rules....">
```

### 속성
| 속성  | 값          | 설명                                                          |
|-------|--------------|---------------------------------------------------------------|
| style | style rules  | style 속성의 값은 세미콜론(;)으로 구분된 스타일 선언의 조합입니다. |

### 예제
다음은 위의 구문을 기반으로 한 인라인 CSS 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <h1 style = "color:#36C;"> 
         This is inline CSS 
      </h1>
   </body>
</html>
```
이것은 다음과 같은 결과를 생성합니다 −

### 외부 CSS - `<link>` 요소
`<link>` 요소는 외부 스타일 시트 파일을 `HTML` 문서에 포함하는 데 사용될 수 있습니다.

외부 스타일 시트는 `.css` 확장자를 가진 별도의 텍스트 파일입니다. 이 텍스트 파일 내에서 모든 스타일 규칙을 정의하고 `<link>` 요소를 사용하여 이 파일을 `HTML` 문서에 포함할 수 있습니다.

다음은 외부 CSS 파일을 포함하는 일반 구문입니다 −

```html
<head>
   <link type = "text/css" href = "..." media = "..." />
</head>
```

### 속성
`<link>` 요소와 관련된 속성은 다음과 같습니다 −

| 속성  | 값          | 설명                                                                                      |
|-------|--------------|-------------------------------------------------------------------------------------------|
| type  | text css     | 스타일 시트 언어를 콘텐츠 유형(MIME 유형)으로 지정합니다. 이 속성은 필수 속성입니다.         |
| href  | URL          | 스타일 규칙을 가진 스타일 시트 파일을 지정합니다. 이 속성은 필수 속성입니다.                |
| media |              | 문서가 표시될 장치를 지정합니다. 기본값은 all입니다. 이 속성은 선택적 속성입니다.          |

### 예제
다음 규칙을 가진 mystyle.css라는 이름의 간단한 스타일 시트 파일을 고려해 봅시다 −

```css
h1, h2, h3 {
   color: #36C;
   font-weight: normal;
   letter-spacing: .4em;
   margin-bottom: 1em;
   text-transform: lowercase;
}
```
이제 다음과 같이 이 파일 `mystyle.css`를 HTML 문서에 포함할 수 있습니다 −

```html
<head>
   <link type = "text/css" href = "mystyle.css" media = " all" />
</head>
```

### 임포트된 CSS - `@import` 규칙
`@import`는 `<link>` 요소와 유사한 방식으로 외부 스타일 시트를 가져오는 데 사용됩니다. 다음은 `@import` 규칙의 일반 구문입니다.

```html
<head>
   @import "URL";
</head>
```
여기서 URL은 스타일 규칙을 가진 스타일 시트 파일의 URL입니다. 다른 구문도 사용할 수 있습니다 −

```html
<head>
   @import url("URL");
</head>
```

### 예제
다음은 스타일 시트 파일을 `HTML` 문서에 임포트하는 방법을 보여주는 예제입니다 −

```html
<head>
   @import "mystyle.css";
</head>
```

### CSS 규칙 재정의

`HTML` 문서에 스타일 시트 규칙을 포함하는 네 가지 방법에 대해 논의했습니다. 여기에는 스타일 시트 규칙을 재정의하는 규칙이 있습니다.

인라인 스타일 시트는 가장 높은 우선순위를 가집니다. 따라서 `<style>...</style>` 태그 내에서 정의된 규칙이나 외부 스타일 시트 파일에 정의된 규칙을 재정의합니다.

`<style>...</style>` 태그 내에서 정의된 규칙은 외부 스타일 시트 파일에 정의된 규칙을 재정의합니다.

외부 스타일 시트 파일에 정의된 규칙은 가장 낮은 우선순위를 가지며, 위의 두 규칙이 적용되지 않는 경우에만 적용됩니다.

### 오래된 브라우저 처리
여전히 CSS를 지원하지 않는 많은 오래된 브라우저가 있습니다. 따라서 HTML 문서에서 임베디드 CSS를 작성할 때 주의해야 합니다. 다음 스니펫은 주석 태그를 사용하여 오래된 브라우저에서 CSS를 숨기는 방법을 보여줍니다 −

```html
<style type = "text/css">
   <!--
      body, td {
         color: blue;
      }
   -->
</style>
```

### CSS 주석
스타일 시트 블록에 추가 주석을 넣어야 할 때가 많습니다. 따라서 스타일 시트의 어느 부분이든 쉽게 주석 처리할 수 있습니다. 주석을 /*.....this is a comment in style sheet.....*/ 안에 넣으면 됩니다.

C 및 C++ 프로그래밍 언어에서와 유사하게 여러 줄 블록을 주석 처리하려면 /* ....*/를 사용할 수 있습니다.

### 예제
```html
<!DOCTYPE html>
<html>
   <head>
      <style>
         p {
            color: red;
            /* This is a single-line comment */
            text-align: center;
         }
         /* This is a multi-line comment */
      </style>
   </head>

   <body>
      <p>Hello World!</p>
   </body>
</html>
```
이것은 다음과 같은 결과를 생성합니다 −

---

## CSS - Measurement Units

%: 다른 값, 일반적으로 포함 요소에 상대적인 백분율로 측정을 정의합니다. 예:

```css
p {font-size: 16pt; line-height: 125%;}
```

cm: 센티미터 단위로 측정을 정의합니다. 예:

```css
div {margin-bottom: 2cm;}
```

em: em 단위로 폰트의 높이를 상대적으로 측정합니다. em 단위는 주어진 폰트의 크기와 동일하기 때문에 폰트를 12pt로 지정하면 각 "em" 단위는 12pt가 되며, 따라서 2em은 24pt가 됩니다. 예:

```css
p {letter-spacing: 7em;}
```

ex: 폰트의 x-높이에 상대적인 측정 값을 정의합니다. x-높이는 소문자 x의 높이에 따라 결정됩니다. 예:

```css
p {font-size: 24pt; line-height: 3ex;}
```

in: 인치 단위로 측정을 정의합니다. 예:

```css
p {word-spacing: .15in;}
```

mm: 밀리미터 단위로 측정을 정의합니다. 예:

```css
p {word-spacing: 15mm;}
```

pc: 파이카 단위로 측정을 정의합니다. 파이카는 12 포인트와 동일하므로 1인치에 6 파이카가 있습니다. 예:

```css
p {font-size: 20pc;}
```

pt: 포인트 단위로 측정을 정의합니다. 포인트는 1/72 인치로 정의됩니다. 예:

```css
body {font-size: 18pt;}
```

px: 화면 픽셀 단위로 측정을 정의합니다. 예:

```css
p {padding: 25px;}
```

---

## CSS - Colors

Hex Code: #RRGGBB 예:

```css
p{color:#FF0000;}
```

Short Hex Code: #RGB 예:

```css
p{color:#6A7;}
```

RGB %: rgb(rrr%, ggg%, bbb%) 예:

```css
p{color:rgb(50%,50%,50%);}
```

RGB Absolute: rgb(rrr, ggg, bbb) 예:

```css
p{color:rgb(0,0,255);}
```

keyword: aqua, black, 등 예:

```css
p{color:teal;}
```

이 형식들은 다음 섹션에서 자세히 설명됩니다 −

### CSS 색상 - 16진수 코드
16진수는 색상을 6자리로 나타내는 표현입니다. 처음 두 자릿수(RR)는 빨간색 값, 다음 두 자릿수(GG)는 녹색 값, 마지막 두 자릿수(BB)는 파란색 값을 나타냅니다.

16진수 값은 Adobe Photoshop, Jasc Paintshop Pro 또는 Advanced Paint Brush와 같은 그래픽 소프트웨어에서 가져올 수 있습니다.

각 16진수 코드는 '#' 기호로 시작합니다. 다음은 16진수 표기법을 사용하는 예제들입니다.

| 색상     | 색상 HEX   |
|----------|-------------|
| 검정색   | #000000     |
| 빨간색   | #FF0000     |
| 녹색     | #00FF00     |
| 파란색   | #0000FF     |
| 노란색   | #FFFF00     |
| 청록색   | #00FFFF     |
| 자홍색   | #FF00FF     |
| 은색     | #C0C0C0     |
| 흰색     | #FFFFFF     |

### CSS 색상 - 짧은 16진수 코드
이것은 6자리 표기법의 짧은 형태입니다. 이 형식에서는 각 자릿수가 복제되어 동등한 6자리 값이 됩니다. 예: #6A7은 #66AA77이 됩니다.

각 16진수 코드는 '#' 기호로 시작합니다. 다음은 16진수 표기법을 사용하는 예제들입니다.

| 색상     | 색상 HEX   |
|----------|-------------|
| 검정색   | #000        |
| 빨간색   | #F00        |
| 녹색     | #0F0        |
| 청록색   | #0FF        |
| 노란색   | #FF0        |
| 자홍색   | #F0F        |
| 흰색     | #FFF        |

### CSS 색상 - RGB 값
이 색상 값은 rgb( ) 속성을 사용하여 지정됩니다. 이 속성은 빨강, 초록 및 파랑에 대한 세 가지 값을 받습니다. 값은 0에서 255 사이의 정수 또는 백분율일 수 있습니다.

모든 브라우저가 rgb() 색상 속성을 지원하지 않으므로 사용하는 것이 권장되지 않습니다.

다음은 RGB 값을 사용하여 몇 가지 색상을 보여주는 예제입니다.

| 색상     | 색상 RGB          |
|----------|--------------------|
| 검정색   | rgb(0,0,0)         |
| 빨간색   | rgb(255,0,0)       |
| 녹색     | rgb(0,255,0)       |
| 파란색   | rgb(0,0,255)       |
| 노란색   | rgb(255,255,0)     |
| 청록색   | rgb(0,255,255)     |
| 자홍색   | rgb(255,0,255)     |
| 은색     | rgb(192,192,192)   |
| 흰색     | rgb(255,255,255)   |

### 색상 코드 생성
Color Code Builder를 사용하여 수백만 개의 색상 코드를 생성할 수 있습니다. HTML Color Code Builder를 확인하세요. 이 도구를 사용하려면 Java 지원 브라우저가 필요합니다.

### 브라우저 안전 색상
여기에는 가장 안전하고 컴퓨터 독립적인 색상으로 간주되는 216가지 색상의 목록이 있습니다. 이 색상은 16진수 코드 000000에서 FFFFFF까지 다양합니다. 이러한 색상은 모든 컴퓨터가 256색 팔레트를 사용할 때 색상을 올바르게 표시할 수 있도록 안전하게 사용됩니다 −

---

## CSS - Backgrounds

## CSS 교육 문서

### 배경 색상 설정
다음은 요소의 배경 색상을 설정하는 방법을 보여주는 예제입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "background-color:yellow;">
         이 텍스트는 노란색 배경을 가지고 있습니다.
      </p>
   </body>
</html>
```

### 배경 이미지 설정
다음은 로컬에 저장된 이미지를 호출하여 배경 이미지를 설정하는 방법을 보여줍니다.

```html
<html>
   <head>
      <style>
         body  {
            background-image: url("/css/images/css.jpg");
            background-color: #cccccc;
         }
      </style>
   </head>
   
   <body>
      <h1>Hello World!</h1>
   </body>
</html>
```

### 배경 이미지 반복
다음 예제는 이미지가 작을 경우 배경 이미지를 반복하는 방법을 보여줍니다. 이미지를 반복하지 않으려면 background-repeat 속성에 no-repeat 값을 사용할 수 있으며, 이 경우 이미지는 한 번만 표시됩니다.

기본적으로 background-repeat 속성은 repeat 값을 가집니다.

```html
<html>
   <head>
      <style>
         body {
            background-image: url("/css/images/css.jpg");
            background-repeat: repeat;
         }
      </style>
   </head>

   <body>
      <p>Tutorials point</p>
   </body>
</html>
```

다음 예제는 배경 이미지를 세로로 반복하는 방법을 보여줍니다.

```html
<html>
   <head>
      <style>
         body {
            background-image: url("/css/images/css.jpg");
            background-repeat: repeat-y;
         }
      </style>
   </head>

   <body>
      <p>Tutorials point</p>
   </body>
</html>
```

다음 예제는 배경 이미지를 가로로 반복하는 방법을 보여줍니다.

```html
<html>
   <head>
      <style>
         body {
            background-image: url("/css/images/css.jpg");
            background-repeat: repeat-x;
         }
      </style>
   </head>
   
   <body>
      <p>Tutorials point</p>
   </body>
</html>
```

### 배경 이미지 위치 설정
다음 예제는 배경 이미지를 왼쪽에서 100픽셀 떨어진 위치에 설정하는 방법을 보여줍니다.

```html
<html>
   <head>
      <style>
         body {
            background-image: url("/css/images/css.jpg");
            background-position:100px;
         }
      </style>
   </head>

   <body>
      <p>Tutorials point</p>
   </body>
</html>
```

다음 예제는 배경 이미지를 왼쪽에서 100픽셀, 위쪽에서 200픽셀 떨어진 위치에 설정하는 방법을 보여줍니다.

```html
<html>
   <head>
      <style>
         body {
            background-image: url("/css/images/css.jpg");
            background-position:100px 200px;
         }
      </style>
   </head>

   <body>
      <p>Tutorials point</p>
   </body>
</html>
```

### 배경 고정 설정
배경 고정은 배경 이미지가 페이지의 나머지 부분과 함께 고정되는지 스크롤되는지를 결정합니다.

다음 예제는 고정된 배경 이미지를 설정하는 방법을 보여줍니다.

```html
<!DOCTYPE html>
<html>
   <head>
      <style>
         body {
            background-image: url('/css/images/css.jpg');
            background-repeat: no-repeat;
            background-attachment: fixed;
         }
      </style>
   </head>

   <body>
      <p>배경 이미지는 고정되어 있습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있습니다. 페이지를 스크롤해 보세요.</p>
   </body>
</html>
```

다음 예제는 스크롤되는 배경 이미지를 설정하는 방법을 보여줍니다.

```html
<!DOCTYPE html>
<html>
   <head>
      <style>
         body {
            background-image: url('/css/images/css.jpg');
            background-repeat: no-repeat;
            background-attachment: scroll;
         }
      </style>
   </head>

   <body>
      <p>배경 이미지는 고정되어 있지 않습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있지 않습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있지 않습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있지 않습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있지 않습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있지 않습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있지 않습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있지 않습니다. 페이지를 스크롤해 보세요.</p>
      <p>배경 이미지는 고정되어 있지 않습니다. 페이지를 스크롤해 보세요.</p>
   </body>
</html>
```

### 단축 속성
배경 속성을 사용하여 모든 배경 속성을 한 번에 설정할 수 있습니다. 예:

```html
<p style = "background:url(/images/pattern1.gif) repeat fixed;">
   이 단락은 고정된 반복 배경 이미지를 가지고 있습니다.
</p>
```

---

## CSS - Fonts


### 폰트 패밀리 설정
다음은 요소의 폰트 패밀리를 설정하는 방법을 보여주는 예제입니다. 가능한 값은 폰트 패밀리 이름이 될 수 있습니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "font-family:georgia,garamond,serif;">
         이 텍스트는 시스템에 설치된 폰트에 따라 georgia, garamond, 또는 기본 serif 폰트로 렌더링됩니다.
      </p>
   </body>
</html>
```

### 폰트 스타일 설정
다음은 요소의 폰트 스타일을 설정하는 방법을 보여주는 예제입니다. 가능한 값은 normal, italic, oblique입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "font-style:italic;">
         이 텍스트는 이탤릭체로 렌더링됩니다.
      </p>
   </body>
</html>
```

### 폰트 변형 설정
다음은 요소의 폰트 변형을 설정하는 방법을 보여주는 예제입니다. 가능한 값은 normal과 small-caps입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "font-variant:small-caps;">
         이 텍스트는 스몰 캡스로 렌더링됩니다.
      </p>
   </body>
</html>
```

### 폰트 두께 설정
다음은 요소의 폰트 두께를 설정하는 방법을 보여주는 예제입니다. font-weight 속성은 폰트의 굵기를 지정할 수 있는 기능을 제공합니다. 가능한 값은 normal, bold, bolder, lighter, 100, 200, 300, 400, 500, 600, 700, 800, 900입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "font-weight:bold;">
         이 폰트는 bold입니다.
      </p>
      
      <p style = "font-weight:bolder;">
         이 폰트는 bolder입니다.
      </p>
      
      <p style = "font-weight:500;">
         이 폰트의 두께는 500입니다.
      </p>
   </body>
</html>
```

### 폰트 크기 설정
다음은 요소의 폰트 크기를 설정하는 방법을 보여주는 예제입니다. font-size 속성은 폰트의 크기를 조절하는 데 사용됩니다. 가능한 값은 xx-small, x-small, small, medium, large, x-large, xx-large, smaller, larger, 픽셀 또는 %로 설정할 수 있습니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "font-size:20px;">
         이 폰트 크기는 20픽셀입니다.
      </p>
      
      <p style = "font-size:small;">
         이 폰트 크기는 small입니다.
      </p>
      
      <p style = "font-size:large;">
         이 폰트 크기는 large입니다.
      </p>
   </body>
</html>
```

### 폰트 크기 조정 설정
다음은 요소의 폰트 크기 조정을 설정하는 방법을 보여주는 예제입니다. 이 속성은 x-height를 조정하여 폰트를 더 읽기 쉽게 만듭니다. 가능한 값은 숫자가 될 수 있습니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "font-size-adjust:0.61;">
         이 텍스트는 font-size-adjust 값을 사용합니다.
      </p>
   </body>
</html>
```

### 폰트 스트레치 설정
다음은 요소의 폰트 스트레치를 설정하는 방법을 보여주는 예제입니다. 이 속성은 사용자의 컴퓨터에 확장 또는 축소된 버전의 폰트가 있는지에 따라 작동합니다.

가능한 값은 normal, wider, narrower, ultra-condensed, extra-condensed, condensed, semi-condensed, semi-expanded, expanded, extra-expanded, ultra-expanded입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "font-stretch:ultra-expanded;">
         이 속성이 작동하지 않는다면, 사용자의 컴퓨터에 <br>축소되거나 확장된 버전의 폰트가 없기 때문일 수 있습니다.
      </p>
   </body>
</html>
```

### 단축 속성
font 속성을 사용하여 모든 폰트 속성을 한 번에 설정할 수 있습니다. 예:

```html
<html>
   <head>
   </head>

   <body>
      <p style = "font:italic small-caps bold 15px georgia;">
         모든 속성을 한 번에 텍스트에 적용합니다.
      </p>
   </body>
</html>
```

---

## CSS - Text

### 텍스트 장식 설정
text-decoration 속성은 텍스트에 밑줄, 윗줄, 취소선을 설정하는 데 사용됩니다.

### 텍스트 변환 설정
text-transform 속성은 텍스트를 대문자, 소문자로 변환하거나 첫 글자를 대문자로 설정하는 데 사용됩니다.

### 공백 설정
white-space 속성은 텍스트의 흐름과 형식을 제어하는 데 사용됩니다.

### 텍스트 그림자 설정
text-shadow 속성은 텍스트 주변에 그림자를 설정하는 데 사용됩니다.

### 텍스트 색상 설정
다음 예제는 텍스트 색상을 설정하는 방법을 보여줍니다. 가능한 값은 유효한 형식의 모든 색상 이름이 될 수 있습니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "color:red;">
         이 텍스트는 빨간색으로 작성됩니다.
      </p>
   </body>
</html>
```

### 텍스트 방향 설정
다음 예제는 텍스트의 방향을 설정하는 방법을 보여줍니다. 가능한 값은 ltr 또는 rtl입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "direction:rtl;">
         이 텍스트는 오른쪽에서 왼쪽으로 렌더링됩니다.
      </p>
   </body>
</html>
```

### 문자 간격 설정
다음 예제는 문자 간의 간격을 설정하는 방법을 보여줍니다. 가능한 값은 normal 또는 간격을 지정하는 숫자입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "letter-spacing:5px;">
         이 텍스트는 문자 사이에 간격이 있습니다.
      </p>
   </body>
</html>
```

### 단어 간격 설정
다음 예제는 단어 간의 간격을 설정하는 방법을 보여줍니다. 가능한 값은 normal 또는 간격을 지정하는 숫자입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "word-spacing:5px;">
         이 텍스트는 단어 사이에 간격이 있습니다.
      </p>
   </body>
</html>
```

### 텍스트 들여쓰기 설정
다음 예제는 단락의 첫 줄을 들여쓰는 방법을 보여줍니다. 가능한 값은 % 또는 들여쓰기 간격을 지정하는 숫자입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "text-indent:1cm;">
         이 텍스트는 첫 줄이 1cm 들여쓰기 되어 있으며, 이 줄은 실제 위치에 남아 있습니다. 이것은 CSS text-indent 속성에 의해 수행됩니다.
      </p>
   </body>
</html>
```

### 텍스트 정렬 설정
다음 예제는 텍스트를 정렬하는 방법을 보여줍니다. 가능한 값은 left, right, center, justify입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "text-align:right;">
         이 텍스트는 오른쪽 정렬됩니다.
      </p>
      
      <p style = "text-align:center;">
         이 텍스트는 가운데 정렬됩니다.
      </p>
      
      <p style = "text-align:left;">
         이 텍스트는 왼쪽 정렬됩니다.
      </p>
   </body>
</html>
```

### 텍스트 장식 설정
다음 예제는 텍스트를 장식하는 방법을 보여줍니다. 가능한 값은 none, underline, overline, line-through, blink입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "text-decoration:underline;">
         이 텍스트는 밑줄이 그어집니다.
      </p>
      
      <p style = "text-decoration:line-through;">
         이 텍스트는 취소선이 그어집니다.
      </p>
      
      <p style = "text-decoration:overline;">
         이 텍스트는 윗줄이 그어집니다.
      </p>
      
      <p style = "text-decoration:blink;">
         이 텍스트는 깜박이는 효과가 있습니다.
      </p>
   </body>
</html>
```

### 텍스트 대소문자 설정
다음 예제는 텍스트의 대소문자를 설정하는 방법을 보여줍니다. 가능한 값은 none, capitalize, uppercase, lowercase입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "text-transform:capitalize;">
         이 텍스트는 첫 글자가 대문자로 설정됩니다.
      </p>
      
      <p style = "text-transform:uppercase;">
         이 텍스트는 모두 대문자로 설정됩니다.
      </p>
      
      <p style = "text-transform:lowercase;">
         이 텍스트는 모두 소문자로 설정됩니다.
      </p>
   </body>
</html>
```

### 텍스트 공백 설정
다음 예제는 요소 내의 공백이 처리되는 방식을 보여줍니다. 가능한 값은 normal, pre, nowrap입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "white-space:pre;">
         이 텍스트는 줄 바꿈이 있으며, white-space pre 설정은 HTML pre 태그처럼 브라우저가 이를 존중하도록 지시합니다.
      </p>
   </body>
</html>
```

### 텍스트 그림자 설정
다음 예제는 텍스트 주변에 그림자를 설정하는 방법을 보여줍니다. 이는 모든 브라우저에서 지원되지 않을 수 있습니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "text-shadow:4px 4px 8px blue;">
         브라우저가 CSS text-shadow 속성을 지원하면, 이 텍스트는 파란색 그림자가 나타납니다.
      </p>
   </body>
</html>
```

---

## CSS - Using Images


### 이미지 테두리 속성
이미지의 border 속성은 이미지 테두리의 너비를 설정하는 데 사용됩니다. 이 속성은 길이 또는 % 값일 수 있습니다.

너비가 0 픽셀이면 테두리가 없습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <img style = "border:0px;" src = "/css/images/logo.png" />
      <br />
      <img style = "border:3px dashed red;" src = "/css/images/logo.png" />
   </body>
</html>
```

### 이미지 높이 속성
이미지의 height 속성은 이미지의 높이를 설정하는 데 사용됩니다. 이 속성은 길이 또는 % 값일 수 있습니다. % 값을 주는 경우 이미지를 포함하는 상자에 대해 적용됩니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <img style = "border:1px solid red; height:100px;" src = "/css/images/logo.png" />
      <br />
      <img style = "border:1px solid red; height:50%;" src = "/css/images/logo.png" />
   </body>
</html>
```

### 이미지 너비 속성
이미지의 width 속성은 이미지의 너비를 설정하는 데 사용됩니다. 이 속성은 길이 또는 % 값일 수 있습니다. % 값을 주는 경우 이미지를 포함하는 상자에 대해 적용됩니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <img style = "border:1px solid red; width:150px;" src = "/css/images/logo.png" />
      <br />
      <img style = "border:1px solid red; width:100%;" src = "/css/images/logo.png" />
   </body>
</html>
```

### -moz-opacity 속성
이미지의 -moz-opacity 속성은 이미지의 불투명도를 설정하는 데 사용됩니다. 이 속성은 Mozilla에서 투명 이미지를 생성하는 데 사용됩니다. IE는 filter:alpha(opacity=x)를 사용하여 투명 이미지를 생성합니다.

Mozilla에서 (-moz-opacity:x) x는 0.0 - 1.0 사이의 값이 될 수 있습니다. 값이 낮을수록 요소가 더 투명해집니다 (CSS3 유효 구문 opacity:x에서도 동일하게 적용됩니다).

IE에서 (filter:alpha(opacity=x)) x는 0 - 100 사이의 값이 될 수 있습니다. 값이 낮을수록 요소가 더 투명해집니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <img style = "border:1px solid red; -moz-opacity:0.4; filter:alpha(opacity=40);" src = "/css/images/logo.png" />
   </body>
</html>
```

---

## CSS - Links


보통, 모든 속성은 HTML 문서의 헤더 부분에 보관됩니다.

a:hover는 a:link와 a:visited 뒤에 와야 하고, a:active는 a:hover 뒤에 와야 합니다. 다음과 같이 정의합니다 −

```html
<style type = "text/css">
   a:link {color: #000000}
   a:visited {color: #006600}
   a:hover {color: #FFCC00}
   a:active {color: #FF00CC}
</style>
```

이제 이러한 속성을 사용하여 하이퍼링크에 다양한 효과를 주는 방법을 알아보겠습니다.

### 링크 색상 설정
다음 예제는 링크 색상을 설정하는 방법을 보여줍니다. 가능한 값은 유효한 형식의 모든 색상 이름이 될 수 있습니다.

```html
<html>
   <head>
      <style type = "text/css">
         a:link {color:#000000}
      </style>
   </head>

   <body>
      <a href = "">Link</a>
   </body>
</html>
```
이것은 다음과 같이 검은색 링크를 생성합니다 −

### 방문한 링크 색상 설정
다음 예제는 방문한 링크의 색상을 설정하는 방법을 보여줍니다. 가능한 값은 유효한 형식의 모든 색상 이름이 될 수 있습니다.

```html
<html>
   <head>
      <style type = "text/css">
         a:visited {color: #006600}
      </style>
   </head>

   <body>
      <a href = "">link</a> 
   </body>
</html>
```
이것은 다음과 같이 링크를 생성합니다. 이 링크를 클릭하면 색상이 초록색으로 바뀝니다.

### 마우스를 올렸을 때 링크 색상 변경
다음 예제는 링크에 마우스 포인터를 올렸을 때 링크의 색상을 변경하는 방법을 보여줍니다. 가능한 값은 유효한 형식의 모든 색상 이름이 될 수 있습니다.

```html
<html>
   <head>
      <style type = "text/css">
         a:hover {color: #FFCC00}
      </style>
   </head>

   <body>
      <a href = "">Link</a>
   </body>
</html>
```
이것은 다음과 같이 링크를 생성합니다. 이제 이 링크에 마우스를 올리면 색상이 노란색으로 바뀝니다.

### 활성 링크 색상 변경
다음 예제는 활성 링크의 색상을 변경하는 방법을 보여줍니다. 가능한 값은 유효한 형식의 모든 색상 이름이 될 수 있습니다.

```html
<html>
   <head>
      <style type = "text/css">
         a:active {color: #FF00CC}
      </style>
   </head>

   <body>
      <a href = "">Link</a>
   </body>
</html>
```
이것은 다음과 같이 링크를 생성합니다. 사용자가 클릭하면 색상이 핑크색으로 바뀝니다.

---
## CSS - Tables


이제 이러한 속성을 예제와 함께 사용하는 방법을 알아보겠습니다.

### border-collapse 속성
이 속성은 collapse와 separate 두 가지 값을 가질 수 있습니다. 다음 예제는 두 값을 모두 사용합니다 −

```html
<html>
   <head>
      <style type = "text/css">
         table.one {border-collapse:collapse;}
         table.two {border-collapse:separate;}
         
         td.a {
            border-style:dotted; 
            border-width:3px; 
            border-color:#000000; 
            padding: 10px;
         }
         td.b {
            border-style:solid; 
            border-width:3px; 
            border-color:#333333; 
            padding:10px;
         }
      </style>
   </head>

   <body>
      <table class = "one">
         <caption>Collapse Border Example</caption>
         <tr><td class = "a"> Cell A Collapse Example</td></tr>
         <tr><td class = "b"> Cell B Collapse Example</td></tr>
      </table>
      <br />
      
      <table class = "two">
         <caption>Separate Border Example</caption>
         <tr><td class = "a"> Cell A Separate Example</td></tr>
         <tr><td class = "b"> Cell B Separate Example</td></tr>
      </table>
   </body>
</html>
```

### border-spacing 속성
border-spacing 속성은 인접한 셀의 경계를 분리하는 거리를 지정합니다. 하나 또는 두 개의 값을 가질 수 있으며, 길이 단위여야 합니다.

하나의 값을 제공하면 수직 및 수평 경계에 모두 적용됩니다. 두 개의 값을 지정하면 첫 번째 값은 수평 간격, 두 번째 값은 수직 간격을 나타냅니다 −

**주의** − 이 속성은 Netscape 7 또는 IE 6에서는 작동하지 않습니다.

```html
<style type="text/css">
   /* 하나의 값을 제공하는 경우 */
   table.example {border-spacing:10px;}
   /* 두 개의 값을 제공하는 방법 */
   table.example {border-spacing:10px 15px;}
</style>
```

이제 이전 예제를 수정하고 효과를 확인해 보겠습니다 −

```html
<html>
   <head>
      <style type = "text/css">
         table.one {
            border-collapse:separate;
            width:400px;
            border-spacing:10px;
         }
         table.two {
            border-collapse:separate;
            width:400px;
            border-spacing:10px 50px;
         }
      </style>
   </head>

   <body>
   
      <table class = "one" border = "1">
         <caption>Separate Border Example with border-spacing</caption>
         <tr><td> Cell A Collapse Example</td></tr>
         <tr><td> Cell B Collapse Example</td></tr>
      </table>
      <br />
      
      <table class = "two" border = "1">
         <caption>Separate Border Example with border-spacing</caption>
         <tr><td> Cell A Separate Example</td></tr>
         <tr><td> Cell B Separate Example</td></tr>
      </table>
      
   </body>
</html>
```

### caption-side 속성
caption-side 속성은 `<caption>` 요소의 내용을 테이블에 대한 위치를 지정할 수 있도록 합니다. 이 속성은 top, bottom, left, right 중 하나의 값을 가질 수 있습니다. 다음 예제는 각 값을 사용합니다.

**주의** − 이 속성은 일부 IE 브라우저에서 작동하지 않을 수 있습니다.

```html
<html>
   <head>
      <style type = "text/css">
         caption.top {caption-side:top}
         caption.bottom {caption-side:bottom}
         caption.left {caption-side:left}
         caption.right {caption-side:right}
      </style>
   </head>

   <body>
   
      <table style = "width:400px; border:1px solid black;">
         <caption class = "top">
            이 캡션은 위에 표시됩니다
         </caption>
         <tr><td > Cell A</td></tr>
         <tr><td > Cell B</td></tr>
      </table>
      <br />
      
      <table style = "width:400px; border:1px solid black;">
         <caption class = "bottom">
            이 캡션은 아래에 표시됩니다
         </caption>
         <tr><td > Cell A</td></tr>
         <tr><td > Cell B</td></tr>
      </table>
      <br />
      
      <table style = "width:400px; border:1px solid black;">
         <caption class = "left">
            이 캡션은 왼쪽에 표시됩니다
         </caption>
         <tr><td > Cell A</td></tr>
         <tr><td > Cell B</td></tr>
      </table>
      <br />
      
      <table style = "width:400px; border:1px solid black;">
         <caption class = "right">
            이 캡션은 오른쪽에 표시됩니다
         </caption>
         <tr><td > Cell A</td></tr>
         <tr><td > Cell B</td></tr>
      </table>
      
   </body>
</html>
```

### empty-cells 속성
empty-cells 속성은 내용이 없는 셀에 테두리를 표시할지 여부를 나타냅니다.

이 속성은 show, hide, inherit 중 하나의 값을 가질 수 있습니다.

다음은 `<table>` 요소에서 빈 셀의 테두리를 숨기기 위해 empty-cells 속성을 사용하는 방법입니다.

```html
<html>
   <head>
      <style type = "text/css">
         table.empty {
            width:350px;
            border-collapse:separate;
            empty-cells:hide;
         }
         td.empty {
            padding:5px;
            border-style:solid;
            border-width:1px;
            border-color:#999999;
         }
      </style>
   </head>

   <body>
   
      <table class = "empty">
         <tr>
            <th></th>
            <th>Title one</th>
            <th>Title two</th>
         </tr>
      
         <tr>
            <th>Row Title</th>
            <td class = "empty">value</td>
            <td class = "empty">value</td>
         </tr>
      
         <tr>
            <th>Row Title</th>
            <td class = "empty">value</td>
            <td class = "empty"></td>
         </tr>
      </table>
      
   </body>
</html>
```

### table-layout 속성
table-layout 속성은 브라우저가 테이블을 렌더링하거나 배치하는 방식을 제어하는 데 도움이 됩니다.

이 속성은 fixed, auto, inherit 중 하나의 값을 가질 수 있습니다.

다음 예제는 이러한 속성의 차이를 보여줍니다.

**주의** − 이 속성은 많은 브라우저에서 지원되지 않으므로 이 속성에 의존하지 마십시오.

```html
<html>
   <head>
      <style type = "text/css">
         table.auto {
            table-layout: auto
         }
         table.fixed {
            table-layout: fixed
         }
      </style>
   </head>
   
   <body>
   
      <table class = "auto" border = "1" width = "100%">
         <tr>
            <td width = "20%">1000000000000000000000000000</td>
            <td width = "40%">10000000</td>
            <td width = "40%">100</td>
         </tr>
      </table>
      <br />
      
      <table class = "fixed" border = "1" width = "100%">
         <tr>
            <td width = "20%">1000000000000000000000000000</td>
            <td width = "40%">10000000</td>
            <td width = "40%">100</td>
         </tr>
      </table>
   
   </body>
</html>
```

---

## CSS - Borders


### border-color 속성
border-color 속성은 요소를 둘러싼 테두리의 색상을 변경할 수 있게 합니다. 각 요소의 테두리의 아래쪽, 왼쪽, 위쪽 및 오른쪽의 색상을 개별적으로 변경할 수 있습니다.

- border-bottom-color는 아래쪽 테두리의 색상을 변경합니다.
- border-top-color는 위쪽 테두리의 색상을 변경합니다.
- border-left-color는 왼쪽 테두리의 색상을 변경합니다.
- border-right-color는 오른쪽 테두리의 색상을 변경합니다.

다음 예제는 이러한 모든 속성의 효과를 보여줍니다 −

```html
<html>
   <head>
      <style type = "text/css">
         p.example1 {
            border:1px solid;
            border-bottom-color:#009900; /* Green */
            border-top-color:#FF0000;    /* Red */
            border-left-color:#330000;   /* Black */
            border-right-color:#0000CC;  /* Blue */
         }
         p.example2 {
            border:1px solid;
            border-color:#009900;        /* Green */
         }
      </style>
   </head>

   <body>
      <p class = "example1">
         이 예제는 모든 테두리가 다른 색상으로 표시됩니다.
      </p>
      
      <p class = "example2">
         이 예제는 모든 테두리가 녹색으로만 표시됩니다.
      </p>
   </body>
</html>
```

### border-style 속성
border-style 속성은 다음 중 하나의 테두리 스타일을 선택할 수 있게 합니다 −

- none − 테두리가 없습니다. (border-width:0;과 동일)
- solid − 테두리는 단일 실선입니다.
- dotted − 테두리는 일련의 점입니다.
- dashed − 테두리는 일련의 짧은 선입니다.
- double − 테두리는 두 개의 실선입니다.
- groove − 테두리는 페이지에 새겨진 것처럼 보입니다.
- ridge − 테두리는 groove의 반대처럼 보입니다.
- inset − 테두리는 상자가 페이지에 묻힌 것처럼 보입니다.
- outset − 테두리는 상자가 캔버스에서 나오는 것처럼 보입니다.
- hidden − none과 동일하지만 테이블 요소의 테두리 충돌 해결 측면에서 다릅니다.

각 요소의 아래쪽, 왼쪽, 위쪽 및 오른쪽 테두리의 스타일을 개별적으로 변경할 수 있습니다.

- border-bottom-style는 아래쪽 테두리의 스타일을 변경합니다.
- border-top-style는 위쪽 테두리의 스타일을 변경합니다.
- border-left-style는 왼쪽 테두리의 스타일을 변경합니다.
- border-right-style는 오른쪽 테두리의 스타일을 변경합니다.

다음 예제는 이러한 모든 테두리 스타일을 보여줍니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p style = "border-width:4px; border-style:none;">
         이것은 테두리가 없는 상태입니다.
      </p>
      
      <p style = "border-width:4px; border-style:solid;">
         이것은 실선 테두리입니다.
      </p>
      
      <p style = "border-width:4px; border-style:dashed;">
         이것은 점선 테두리입니다.
      </p>
      
      <p style = "border-width:4px; border-style:double;">
         이것은 이중선 테두리입니다.
      </p>
      
      <p style = "border-width:4px; border-style:groove;">
         이것은 groove 테두리입니다.
      </p>
      
      <p style = "border-width:4px; border-style:ridge">
         이것은 ridge 테두리입니다.
      </p>
      
      <p style = "border-width:4px; border-style:inset;">
         이것은 inset 테두리입니다.
      </p>
      
      <p style = "border-width:4px; border-style:outset;">
         이것은 outset 테두리입니다.
      </p>
      
      <p style = "border-width:4px; border-style:hidden;">
         이것은 숨겨진 테두리입니다.
      </p>
      
      <p style = "border-width:4px; 
         border-top-style:solid;
         border-bottom-style:dashed;
         border-left-style:groove;
         border-right-style:double;">
         이것은 네 가지 다른 스타일의 테두리입니다.
      </p>
   </body>
</html>
```

### border-width 속성
border-width 속성은 요소 테두리의 너비를 설정할 수 있게 합니다. 이 속성의 값은 px, pt 또는 cm의 길이 단위이거나 thin, medium 또는 thick으로 설정할 수 있습니다.

각 요소의 아래쪽, 위쪽, 왼쪽 및 오른쪽 테두리의 너비를 개별적으로 변경할 수 있습니다.

- border-bottom-width는 아래쪽 테두리의 너비를 변경합니다.
- border-top-width는 위쪽 테두리의 너비를 변경합니다.
- border-left-width는 왼쪽 테두리의 너비를 변경합니다.
- border-right-width는 오른쪽 테두리의 너비를 변경합니다.

다음 예제는 이러한 모든 테두리 너비를 보여줍니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p style = "border-width:4px; border-style:solid;">
         이 테두리는 너비가 4px인 실선입니다.
      </p>
      
      <p style = "border-width:4pt; border-style:solid;">
         이 테두리는 너비가 4pt인 실선입니다.
      </p>
      
      <p style = "border-width:thin; border-style:solid;">
         이 테두리는 얇은 실선입니다.
      </p>
      
      <p style = "border-width:medium; border-style:solid;">
         이 테두리는 중간 너비의 실선입니다.
      </p>
      
      <p style = "border-width:thick; border-style:solid;">
         이 테두리는 두꺼운 실선입니다.
      </p>
      
      <p style = "border-bottom-width:4px;border-top-width:10px;
         border-left-width: 2px;border-right-width:15px;border-style:solid;">
         이것은 네 가지 다른 너비의 테두리입니다.
      </p>
   </body>
</html>
```

### 단축 속성을 사용한 테두리 설정
border 속성은 하나의 속성으로 테두리의 색상, 스타일, 너비를 지정할 수 있게 합니다.

다음 예제는 세 가지 속성을 하나의 속성으로 사용하는 방법을 보여줍니다. 이것은 어떤 요소의 테두리를 설정하는 데 가장 자주 사용되는 속성입니다.

```html
<html>
   <head>
   </head>

   <body>
      <p style = "border:4px solid red;">
         이 예제는 단축 속성을 사용한 테두리를 보여줍니다.
      </p>
   </body>
</html>
```
---
## CSS - Margins


### margin-right 속성
margin-right 속성은 요소의 오른쪽 여백을 지정합니다.

이제 이러한 속성을 예제와 함께 사용하는 방법을 알아보겠습니다.

### Margin 속성
margin 속성은 네 가지 여백 속성을 하나의 선언으로 설정할 수 있게 합니다. 다음은 단락 주위에 여백을 설정하는 구문입니다 −

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p style = "margin: 15px; border:1px solid black;">
         모든 네 가지 여백이 15px로 설정됩니다.
      </p>
      
      <p style = "margin:10px 2%; border:1px solid black;">
         위쪽과 아래쪽 여백은 10px, 왼쪽과 오른쪽 여백은 문서 전체 너비의 2%로 설정됩니다.
      </p>
      
      <p style = "margin: 10px 2% -10px; border:1px solid black;">
         위쪽 여백은 10px, 왼쪽과 오른쪽 여백은 문서 전체 너비의 2%, 아래쪽 여백은 -10px로 설정됩니다.
      </p>
      
      <p style = "margin: 10px 2% -10px auto; border:1px solid black;">
         위쪽 여백은 10px, 오른쪽 여백은 문서 전체 너비의 2%, 아래쪽 여백은 -10px, 왼쪽 여백은 브라우저가 설정합니다.
      </p>
   </body>
</html>
```

### margin-bottom 속성
margin-bottom 속성은 요소의 아래쪽 여백을 설정할 수 있게 합니다. 길이, % 또는 auto 값을 가질 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <p style = "margin-bottom: 15px; border:1px solid black;">
         이 단락은 지정된 아래쪽 여백을 가지고 있습니다.
      </p>
      
      <p style = "margin-bottom: 5%; border:1px solid black;">
         이 단락은 퍼센트로 지정된 아래쪽 여백을 가지고 있습니다.
      </p>
   </body>
</html>
```

### margin-top 속성
margin-top 속성은 요소의 위쪽 여백을 설정할 수 있게 합니다. 길이, % 또는 auto 값을 가질 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <p style = "margin-top: 15px; border:1px solid black;">
         이 단락은 지정된 위쪽 여백을 가지고 있습니다.
      </p>
      
      <p style = "margin-top: 5%; border:1px solid black;">
         이 단락은 퍼센트로 지정된 위쪽 여백을 가지고 있습니다.
      </p>
   </body>
</html>
```

### margin-left 속성
margin-left 속성은 요소의 왼쪽 여백을 설정할 수 있게 합니다. 길이, % 또는 auto 값을 가질 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <p style = "margin-left: 15px; border:1px solid black;">
         이 단락은 지정된 왼쪽 여백을 가지고 있습니다.
      </p>
      
      <p style = "margin-left: 5%; border:1px solid black;">
         이 단락은 퍼센트로 지정된 위쪽 여백을 가지고 있습니다.
      </p>
   </body>
</html>
```

### margin-right 속성
margin-right 속성은 요소의 오른쪽 여백을 설정할 수 있게 합니다. 길이, % 또는 auto 값을 가질 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p style = "margin-right: 15px; border:1px solid black;">
         이 단락은 지정된 오른쪽 여백을 가지고 있습니다.
      </p>
      <p style = "margin-right: 5%; border:1px solid black;">
         이 단락은 퍼센트로 지정된 오른쪽 여백을 가지고 있습니다.
      </p>
   </body>
</html>
```
---
## CSS - Lists

이제 이러한 속성을 예제와 함께 사용하는 방법을 알아보겠습니다.

### list-style-type 속성
list-style-type 속성은 순서 없는 목록의 불릿 포인트(마커)와 순서 있는 목록의 번호 스타일을 제어할 수 있게 합니다.

순서 없는 목록에 사용할 수 있는 값은 다음과 같습니다 −

| 번호 | 값 및 설명           |
|-----|----------------------|
| 1   | none                 |
| 2   | disc (기본값)        | 채워진 원 |
| 3   | circle               | 빈 원     |
| 4   | square               | 채워진 사각형 |

순서 있는 목록에 사용할 수 있는 값은 다음과 같습니다 −

| 값                   | 설명                      | 예제                   |
|----------------------|--------------------------|------------------------|
| decimal              | 숫자                     | 1,2,3,4,5              |
| decimal-leading-zero | 숫자 앞에 0 추가          | 01, 02, 03, 04, 05     |
| lower-alpha          | 소문자 알파벳             | a, b, c, d, e          |
| upper-alpha          | 대문자 알파벳             | A, B, C, D, E          |
| lower-roman          | 소문자 로마 숫자          | i, ii, iii, iv, v      |
| upper-roman          | 대문자 로마 숫자          | I, II, III, IV, V      |
| lower-greek          | 소문자 그리스 문자        | alpha, beta, gamma     |
| lower-latin          | 소문자 라틴 문자          | a, b, c, d, e          |
| upper-latin          | 대문자 라틴 문자          | A, B, C, D, E          |
| hebrew               | 전통 히브리어 숫자        |                        |
| armenian             | 전통 아르메니아 숫자      |                        |
| georgian             | 전통 조지아 숫자          |                        |
| cjk-ideographic      | 단순한 이데오그래픽 숫자  |                        |
| hiragana             | 히라가나                  | a, i, u, e, o, ka, ki  |
| katakana             | 가타카나                  | A, I, U, E, O, KA, KI  |
| hiragana-iroha       | 히라가나 이로하           | i, ro, ha, ni, ho, he, to |
| katakana-iroha       | 가타카나 이로하           | I, RO, HA, NI, HO, HE, TO |

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <ul style = "list-style-type:circle;">
         <li>Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ul>
      
      <ul style = "list-style-type:square;">
         <li>Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ul>
      
      <ol style = "list-style-type:decimal;">
         <li>Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ol>
      
      <ol style = "list-style-type:lower-alpha;">
         <li>Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ol>
      
      <ol style = "list-style-type:lower-roman;">
         <li>Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ol>
   </body>
</html>
```

### list-style-position 속성
list-style-position 속성은 마커가 불릿 포인트 상자를 안쪽에 나타날지 바깥쪽에 나타날지를 나타냅니다. 이 속성은 두 가지 값을 가질 수 있습니다 −

| 번호 | 값 및 설명       |
|-----|------------------|
| 1   | none             |
| 2   | inside           | 텍스트가 두 번째 줄로 넘어가면 마커 아래로 줄 바꿈되며, 텍스트가 시작하는 곳에 들여쓰기가 됩니다. |
| 3   | outside          | 텍스트가 두 번째 줄로 넘어가면 첫 번째 줄 시작 부분(불릿 오른쪽)에 정렬됩니다. |

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <ul style = "list-style-type:circle; list-style-position:outside;">
         <li>Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ul>
      
      <ul style = "list-style-type:square;list-style-position:inside;">
         <li>Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ul>
      
      <ol style = "list-style-type:decimal;list-style-position:outside;">
         <li>Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ol>
      
      <ol style = "list-style-type:lower-alpha;list-style-position:inside;">
         <li>Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ol>
   </body>
</html>
```

### list-style-image 속성
list-style-image 속성은 사용자 정의 불릿 스타일을 사용할 수 있도록 이미지를 지정할 수 있게 합니다. 구문은 background-image 속성과 유사하며, 값의 시작 부분에 url이 오고 뒤에 괄호 안에 URL이 옵니다. 지정한 이미지를 찾지 못하면 기본 불릿이 사용됩니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <ul>
         <li style = "list-style-image: url(/images/bullet.gif);">Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ul>
      
      <ol>
         <li style = "list-style-image: url(/images/bullet.gif);">Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ol>
   </body>
</html>
```

### list-style 속성
list-style 속성은 모든 목록 속성을 하나의 표현으로 지정할 수 있게 합니다. 이러한 속성들은 어떤 순서로든 나타날 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <ul style = "list-style: inside square;">
         <li>Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ul>
      
      <ol style = "list-style: outside upper-alpha;">
         <li>Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ol>
   </body>
</html>
```

### marker-offset 속성
marker-offset 속성은 마커와 해당 마커에 관련된 텍스트 사이의 거리를 지정할 수 있게 합니다. 값은 길이여야 합니다.

**주의** − 이 속성은 IE 6 또는 Netscape 7에서 지원되지 않습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <ul style = "list-style: inside square; marker-offset:2em;">
         <li>Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ul>
      
      <ol style = "list-style: outside upper-alpha; marker-offset:2cm;">
         <li>Maths</li>
         <li>Social Science</li>
         <li>Physics</li>
      </ol>
   </body>
</html>
```

---

## CSS - Paddings


padding은 앞의 속성들을 간단히 나타낼 때 사용됩니다.

이제 이러한 속성을 예제와 함께 사용하는 방법을 알아보겠습니다.

### padding-bottom 속성
padding-bottom 속성은 요소의 아래쪽 패딩(공간)을 설정합니다. 길이 또는 % 값으로 설정할 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p style = "padding-bottom: 15px; border:1px solid black;">
         이 단락은 지정된 아래쪽 패딩을 가지고 있습니다.
      </p>
      
      <p style = "padding-bottom: 5%; border:1px solid black;">
         이 단락은 퍼센트로 지정된 아래쪽 패딩을 가지고 있습니다.
      </p>
   </body>
</html>
```

### padding-top 속성
padding-top 속성은 요소의 위쪽 패딩(공간)을 설정합니다. 길이 또는 % 값으로 설정할 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p style = "padding-top: 15px; border:1px solid black;">
         이 단락은 지정된 위쪽 패딩을 가지고 있습니다.
      </p>
      
      <p style = "padding-top: 5%; border:1px solid black;">
         이 단락은 퍼센트로 지정된 위쪽 패딩을 가지고 있습니다.
      </p>
   </body>
</html>
```

### padding-left 속성
padding-left 속성은 요소의 왼쪽 패딩(공간)을 설정합니다. 길이 또는 % 값으로 설정할 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p style = "padding-left: 15px; border:1px solid black;">
         이 단락은 지정된 왼쪽 패딩을 가지고 있습니다.
      </p>
      
      <p style = "padding-left: 15%; border:1px solid black;">
         이 단락은 퍼센트로 지정된 왼쪽 패딩을 가지고 있습니다.
      </p>
   </body>
</html>
```

### padding-right 속성
padding-right 속성은 요소의 오른쪽 패딩(공간)을 설정합니다. 길이 또는 % 값으로 설정할 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p style = "padding-right: 15px; border:1px solid black;">
         이 단락은 지정된 오른쪽 패딩을 가지고 있습니다.
      </p>
      
      <p style = "padding-right: 5%; border:1px solid black;">
         이 단락은 퍼센트로 지정된 오른쪽 패딩을 가지고 있습니다.
      </p>
   </body>
</html>
```

### padding 속성
padding 속성은 요소의 왼쪽, 오른쪽, 위쪽 및 아래쪽 패딩(공간)을 설정합니다. 길이 또는 % 값으로 설정할 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p style = "padding: 15px; border:1px solid black;">
         모든 네 가지 패딩이 15px로 설정됩니다.
      </p> 
      
      <p style = "padding:10px 2%; border:1px solid black;"> 
         위쪽과 아래쪽 패딩은 10px, 왼쪽과 오른쪽 패딩은 문서 전체 너비의 2%로 설정됩니다.
      </p> 
      
      <p style = "padding: 10px 2% 10px; border:1px solid black;">
         위쪽 패딩은 10px, 왼쪽과 오른쪽 패딩은 문서 전체 너비의 2%, 아래쪽 패딩은 10px로 설정됩니다.
      </p> 
      
      <p style = "padding: 10px 2% 10px 10px; border:1px solid black;">
         위쪽 패딩은 10px, 오른쪽 패딩은 문서 전체 너비의 2%, 아래쪽 패딩과 위쪽 패딩은 10px로 설정됩니다.
      </p>
   </body>
</html>
```

---

## CSS - Cursors


1  
auto  
커서의 모양은 커서가 위치한 컨텍스트 영역에 따라 달라집니다. 예를 들어, 텍스트 위에서는 I, 링크 위에서는 손 모양 등이 있습니다.

2  
crosshair  
십자선 또는 더하기 기호

3  
default  
화살표

4  
pointer  
가리키는 손 (IE 4에서는 hand 값과 동일)

5  
move  
이동하는 I 바

6  
e-resize  
상자의 가장자리를 오른쪽(동쪽)으로 이동할 것을 나타내는 커서

7  
ne-resize  
상자의 가장자리를 위쪽과 오른쪽(북동쪽)으로 이동할 것을 나타내는 커서

8  
nw-resize  
상자의 가장자리를 위쪽과 왼쪽(북서쪽)으로 이동할 것을 나타내는 커서

9  
n-resize  
상자의 가장자리를 위쪽(북쪽)으로 이동할 것을 나타내는 커서

10  
se-resize  
상자의 가장자리를 아래쪽과 오른쪽(남동쪽)으로 이동할 것을 나타내는 커서

11  
sw-resize  
상자의 가장자리를 아래쪽과 왼쪽(남서쪽)으로 이동할 것을 나타내는 커서

12  
s-resize  
상자의 가장자리를 아래쪽(남쪽)으로 이동할 것을 나타내는 커서

13  
w-resize  
상자의 가장자리를 왼쪽(서쪽)으로 이동할 것을 나타내는 커서

14  
text  
텍스트 입력 I 바

15  
wait  
모래시계

16  
help  
도움말 버튼 위에 사용할 수 있는 물음표 또는 말풍선

17  
<url>  
커서 이미지 파일의 경로

**주의** − 사용자가 기대하는 커서 모양을 사용하는 것이 좋습니다. 예를 들어, 링크 위에 십자선을 사용하는 것은 방문자를 혼란스럽게 할 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p>단어 위에 마우스를 올려 커서가 변하는 것을 확인하세요:</p>
      
      <div style = "cursor:auto">Auto</div>
      <div style = "cursor:crosshair">Crosshair</div>
      <div style = "cursor:default">Default</div>
      
      <div style = "cursor:pointer">Pointer</div>
      <div style = "cursor:move">Move</div>
      <div style = "cursor:e-resize">e-resize</div>
      <div style = "cursor:ne-resize">ne-resize</div>
      <div style = "cursor:nw-resize">nw-resize</div>
      
      <div style = "cursor:n-resize">n-resize</div>
      <div style = "cursor:se-resize">se-resize</div>
      <div style = "cursor:sw-resize">sw-resize</div>
      <div style = "cursor:s-resize">s-resize</div>
      <div style = "cursor:w-resize">w-resize</div>
      
      <div style = "cursor:text">text</div>
      <div style = "cursor:wait">wait</div>
      <div style = "cursor:help">help</div>
   </body>
</html>
```

---

## CSS - Outlines


outline-width 속성은 테두리 너비를 설정하는 데 사용됩니다.

outline-style 속성은 테두리의 선 스타일을 설정하는 데 사용됩니다.

outline-color 속성은 테두리의 색상을 설정하는 데 사용됩니다.

outline 속성은 위의 세 가지 속성을 한 번에 설정하는 데 사용됩니다.

### outline-width 속성
outline-width 속성은 상자에 추가될 테두리의 너비를 지정합니다. 값은 길이 또는 thin, medium, thick 중 하나여야 합니다. 

너비가 0 픽셀이면 테두리가 없습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p style = "outline-width:thin; outline-style:solid;">
         이 텍스트는 얇은 테두리를 가지고 있습니다.
      </p>
      <br />
      
      <p style = "outline-width:thick; outline-style:solid;">
         이 텍스트는 두꺼운 테두리를 가지고 있습니다.
      </p>
      <br />
      
      <p style = "outline-width:5px; outline-style:solid;">
         이 텍스트는 5px 테두리를 가지고 있습니다.
      </p>
   </body>
</html>
```

### outline-style 속성
outline-style 속성은 요소 주위를 감싸는 선의 스타일을 지정합니다. (실선, 점선 또는 대시) 다음 값 중 하나를 가질 수 있습니다 −

- none − 테두리가 없습니다. (outline-width:0;와 동일)
- solid − 단일 실선 테두리
- dotted − 점선 테두리
- dashed − 대시 선 테두리
- double − 두 개의 실선 테두리
- groove − 페이지에 새겨진 것처럼 보이는 테두리
- ridge − groove의 반대처럼 보이는 테두리
- inset − 페이지에 묻힌 것처럼 보이는 테두리
- outset − 캔버스에서 나오는 것처럼 보이는 테두리
- hidden − none과 동일

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p style = "outline-width:thin; outline-style:solid;">
         이 텍스트는 얇은 실선 테두리를 가지고 있습니다.
      </p>
      <br />
      
      <p style = "outline-width:thick; outline-style:dashed;">
         이 텍스트는 두꺼운 대시 선 테두리를 가지고 있습니다.
      </p>
      <br />
      
      <p style = "outline-width:5px; outline-style:dotted;">
         이 텍스트는 5px 점선 테두리를 가지고 있습니다.
      </p>
   </body>
</html>
```

### outline-color 속성
outline-color 속성은 테두리의 색상을 지정할 수 있게 합니다. 값은 색상 이름, 헥스 색상 또는 RGB 값이어야 합니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p style = "outline-width:thin; outline-style:solid; outline-color:red">
         이 텍스트는 얇은 빨간색 실선 테두리를 가지고 있습니다.
      </p>
      <br />
      
      <p style = "outline-width:thick; outline-style:dashed; outline-color:#009900">
         이 텍스트는 두꺼운 녹색 대시 선 테두리를 가지고 있습니다.
      </p>
      <br />
      
      <p style = "outline-width:5px; outline-style:dotted; outline-color:rgb(13,33,232)">
         이 텍스트는 5px 파란색 점선 테두리를 가지고 있습니다.
      </p>
   </body>
</html>
```

### outline 속성
outline 속성은 이전에 논의한 세 가지 속성의 값을 어떤 순서로든 하나의 문장에서 지정할 수 있는 단축 속성입니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>
   
   <body>
      <p style = "outline:thin solid red;">
         이 텍스트는 얇은 빨간색 실선 테두리를 가지고 있습니다.
      </p>
      <br />
      
      <p style = "outline:thick dashed #009900;">
         이 텍스트는 두꺼운 녹색 대시 선 테두리를 가지고 있습니다.
      </p>
      <br />
      
      <p style = "outline:5px dotted rgb(13,33,232);">
         이 텍스트는 5px 파란색 점선 테두리를 가지고 있습니다.
      </p>
   </body>
</html>
```
---
## CSS - Dimension


max-width 속성은 상자의 최대 너비를 설정하는 데 사용됩니다.

min-width 속성은 상자의 최소 너비를 설정하는 데 사용됩니다.

### Height 및 Width 속성
height 및 width 속성은 상자의 높이와 너비를 설정할 수 있게 합니다. 길이, 백분율 또는 auto 키워드를 값으로 가질 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <p style = "width:400px; height:100px; border:1px solid red; padding:5px; margin:10px;">
         이 단락은 너비가 400픽셀이고 높이가 100픽셀입니다.
      </p>
   </body>
</html>
```

### line-height 속성
line-height 속성은 텍스트 줄 사이의 간격을 증가시킬 수 있게 합니다. line-height 속성의 값은 숫자, 길이 또는 백분율이 될 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <p style = "width:400px; height:100px; border:1px solid red; padding:5px; margin:10px; line-height:30px;">
         이 단락은 너비가 400픽셀이고 높이가 100픽셀이며 줄 간격은 30픽셀입니다.
         이 단락은 너비가 400픽셀이고 높이가 100픽셀이며 줄 간격은 30픽셀입니다.
      </p>
   </body>
</html>
```

### max-height 속성
max-height 속성은 상자의 최대 높이를 지정할 수 있게 합니다. max-height 속성의 값은 숫자, 길이 또는 백분율이 될 수 있습니다.

**주의** − 이 속성은 Netscape 7 또는 IE 6에서 작동하지 않습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>  
   <body>
      <p style = "width:400px; max-height:10px; border:1px solid red; padding:5px; margin:10px;">
         이 단락은 너비가 400픽셀이고 최대 높이는 10픽셀입니다.
         이 단락은 너비가 400픽셀이고 최대 높이는 10픽셀입니다.
         이 단락은 너비가 400픽셀이고 최대 높이는 10픽셀입니다.
         이 단락은 너비가 400픽셀이고 최대 높이는 10픽셀입니다.
      </p>
      <br>
      <br>
      <br>
      <img alt = "logo" src = "/css/images/logo.png" width = "195" height = "84" />
   </body>
</html>
```

### min-height 속성
min-height 속성은 상자의 최소 높이를 지정할 수 있게 합니다. min-height 속성의 값은 숫자, 길이 또는 백분율이 될 수 있습니다.

**주의** − 이 속성은 Netscape 7 또는 IE 6에서 작동하지 않습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <p style = "width:400px; min-height:200px; border:1px solid red; padding:5px; margin:10px;">
         이 단락은 너비가 400픽셀이고 최소 높이는 200픽셀입니다.
         이 단락은 너비가 400픽셀이고 최소 높이는 200픽셀입니다.
         이 단락은 너비가 400픽셀이고 최소 높이는 200픽셀입니다.
         이 단락은 너비가 400픽셀이고 최소 높이는 200픽셀입니다.
      </p>
      <img alt = "logo" src = "/css/images/logo.png" width = "95" height = "84" />
   </body>
</html>
```

### max-width 속성
max-width 속성은 상자의 최대 너비를 지정할 수 있게 합니다. max-width 속성의 값은 숫자, 길이 또는 백분율이 될 수 있습니다.

**주의** − 이 속성은 Netscape 7 또는 IE 6에서 작동하지 않습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <p style = "max-width:100px; height:200px; border:1px solid red; padding:5px; margin:10px;">
         이 단락은 높이가 200픽셀이고 최대 너비는 100픽셀입니다.
         이 단락은 높이가 200픽셀이고 최대 너비는 100픽셀입니다.
         이 단락은 높이가 200픽셀이고 최대 너비는 100픽셀입니다.
         이 단락은 높이가 200픽셀이고 최대 너비는 100픽셀입니다.
         이 단락은 높이가 200픽셀이고 최대 너비는 100픽셀입니다.
      </p>
      <img alt = "logo" src = "/images/css.gif" width = "95" height = "84" />
   </body>
</html>
```

### min-width 속성
min-width 속성은 상자의 최소 너비를 지정할 수 있게 합니다. min-width 속성의 값은 숫자, 길이 또는 백분율이 될 수 있습니다.

**주의** − 이 속성은 Netscape 7 또는 IE 6에서 작동하지 않습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <p style = "min-width:400px; height:100px; border:1px solid red; padding:5px; margin:10px;">
         이 단락은 높이가 100픽셀이고 최소 너비는 400픽셀입니다.
         이 단락은 높이가 100픽셀이고 최소 너비는 400픽셀입니다.
      </p>
      <img alt = "logo" src = "/css/images/css.gif" width = "95" height = "84" />
   </body>
</html>
```

---
## CSS - Scrollbars

1  
visible  
내용이 포함 요소의 경계를 넘어서도록 허용합니다.

2  
hidden  
중첩된 요소의 내용이 포함 요소의 경계에서 잘리며 스크롤 바가 보이지 않습니다.

3  
scroll  
포함 요소의 크기는 변하지 않지만 스크롤 바가 추가되어 사용자가 내용을 보기 위해 스크롤할 수 있게 합니다.

4  
auto  
목적은 scroll과 같지만, 내용이 넘칠 경우에만 스크롤 바가 표시됩니다.

다음은 예제입니다 −

```html
<html>
   <head>
      <style type = "text/css">
         .scroll {
            display:block;
            border: 1px solid red;
            padding:5px;
            margin-top:5px;
            width:300px;
            height:50px;
            overflow:scroll;
         }
         .auto {
            display:block;
            border: 1px solid red;
            padding:5px;
            margin-top:5px;
            width:300px;
            height:50px;
            overflow:auto;
         }
      </style>
   </head>

   <body>
      <p>scroll 값의 예제:</p>
      <div class = "scroll">
         내용을 많이 넣어서 요소 상자에 오버플로우가 발생했을 때 
         스크롤 바가 어떻게 작동하는지 보여주기 위한 예제입니다. 
         이 예제는 가로 및 세로 스크롤 바를 제공합니다.
      </div>
      <br />
      
      <p>auto 값의 예제:</p>
      
      <div class = "auto">
         내용을 많이 넣어서 요소 상자에 오버플로우가 발생했을 때 
         스크롤 바가 어떻게 작동하는지 보여주기 위한 예제입니다. 
         이 예제는 가로 및 세로 스크롤 바를 제공합니다.
      </div>
   </body>
</html>
```

---
## CSS - Visibility

1  
visible  
상자와 그 내용이 사용자에게 표시됩니다.

2  
hidden  
상자와 그 내용이 보이지 않지만 여전히 페이지의 레이아웃에 영향을 미칩니다.

3  
collapse  
동적 테이블 열 및 행 효과에서만 사용됩니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <p>
         이 단락은 정상적으로 보여야 합니다.
      </p>
   
      <p style = "visibility:hidden;">
         이 단락은 보이지 않아야 합니다.
      </p>
   </body>
</html>
```
---
## CSS - Positioning

Move Up - top에 음수 값을 사용합니다.  
Move Down - top에 양수 값을 사용합니다.  
NOTE − bottom이나 right 값을 top과 left와 동일하게 사용할 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <div style = "position:relative; left:80px; top:2px; background-color:yellow;">
         이 div는 상대적 위치를 가지고 있습니다.
      </div>
   </body>
</html>
```

### Absolute Positioning
position: absolute를 가진 요소는 화면의 좌상단 모서리를 기준으로 지정된 좌표에 위치합니다.

position 속성과 함께 top과 left 두 값을 사용하여 HTML 요소를 HTML 문서 내 어디든지 이동시킬 수 있습니다.

Move Left - left에 음수 값을 사용합니다.  
Move Right - left에 양수 값을 사용합니다.  
Move Up - top에 음수 값을 사용합니다.  
Move Down - top에 양수 값을 사용합니다.  
NOTE − bottom이나 right 값을 top과 left와 동일하게 사용할 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <div style = "position:absolute; left:80px; top:20px; background-color:yellow;">
         이 div는 절대적 위치를 가지고 있습니다.
      </div>
   </body>
</html>
```

### Fixed Positioning
고정 위치 설정은 요소의 위치를 페이지의 특정 위치에 고정시키며, 스크롤링과 관계없이 해당 위치에 머물게 합니다. 지정된 좌표는 브라우저 창을 기준으로 합니다.

position 속성과 함께 top과 left 두 값을 사용하여 HTML 요소를 HTML 문서 내 어디든지 이동시킬 수 있습니다.

Move Left - left에 음수 값을 사용합니다.  
Move Right - left에 양수 값을 사용합니다.  
Move Up - top에 음수 값을 사용합니다.  
Move Down - top에 양수 값을 사용합니다.  
NOTE − bottom이나 right 값을 top과 left와 동일하게 사용할 수 있습니다.

다음은 예제입니다 −

```html
<html>
   <head>
   </head>

   <body>
      <div style = "position:fixed; left:80px; top:20px; background-color:yellow;">
         이 div는 고정 위치를 가지고 있습니다.
      </div>
   </body>
</html>
```
---
## CSS - Layers


```html
<body>
   <div style = "background-color:red; 
      width:300px; 
      height:100px; 
      position:relative; 
      top:10px; 
      left:80px; 
      z-index:2">
   </div>
      
   <div style = "background-color:yellow; 
      width:300px; 
      height:100px; 
      position:relative; 
      top:-60px; 
      left:35px; 
      z-index:1;">
   </div>
      
   <div style = "background-color:green; 
      width:300px; 
      height:100px; 
      position:relative; 
      top:-220px; 
      left:120px; 
      z-index:3;">
   </div>
</body>
```

다음과 같은 결과가 생성됩니다 −

---
## CSS - Pseudo Classes

가장 일반적으로 사용되는 가상 클래스는 다음과 같습니다 −

1  
:link  
방문하지 않은 링크에 특별한 스타일을 추가합니다.

2  
:visited  
방문한 링크에 특별한 스타일을 추가합니다.

3  
:hover  
마우스를 올렸을 때 요소에 특별한 스타일을 추가합니다.

4  
:active  
활성화된 요소에 특별한 스타일을 추가합니다.

5  
:focus  
포커스가 있는 요소에 특별한 스타일을 추가합니다.

6  
:first-child  
특정 요소의 첫 번째 자식 요소에 특별한 스타일을 추가합니다.

7  
:lang  
지정된 요소에 사용할 언어를 지정합니다.

`<style>...</style>` 블록에서 가상 클래스를 정의할 때 다음 사항을 유의해야 합니다 −

- a:hover는 CSS 정의에서 a:link 및 a:visited 뒤에 와야 효과적입니다.
- a:active는 CSS 정의에서 a:hover 뒤에 와야 효과적입니다.
- 가상 클래스 이름은 대소문자를 구분하지 않습니다.
- 가상 클래스는 CSS 클래스와 다르지만 함께 사용할 수 있습니다.

### :link 가상 클래스
다음 예제는 :link 클래스를 사용하여 링크 색상을 설정하는 방법을 보여줍니다. 가능한 값은 모든 유효한 형식의 색상 이름일 수 있습니다.

```html
<html>
   <head>
      <style type = "text/css">
         a:link {color:#000000}
      </style>
   </head>

   <body>
      <a href = "">Black Link</a>
   </body>
</html>
```

### :visited 가상 클래스
다음 예제는 :visited 클래스를 사용하여 방문한 링크의 색상을 설정하는 방법을 보여줍니다. 가능한 값은 모든 유효한 형식의 색상 이름일 수 있습니다.

```html
<html>
   <head>
      <style type = "text/css">
         a:visited {color: #006600}
      </style>
   </head>

   <body>
      <a href = "">Click this link</a>
   </body>
</html>
```

### :hover 가상 클래스
다음 예제는 :hover 클래스를 사용하여 링크 위에 마우스를 올렸을 때 링크의 색상을 변경하는 방법을 보여줍니다. 가능한 값은 모든 유효한 형식의 색상 이름일 수 있습니다.

```html
<html>
   <head>
      <style type = "text/css">
         a:hover {color: #FFCC00}
      </style>
   </head>

   <body>
      <a href = "">Bring Mouse Here</a>
   </body>
</html>
```

### :active 가상 클래스
다음 예제는 :active 클래스를 사용하여 활성 링크의 색상을 변경하는 방법을 보여줍니다. 가능한 값은 모든 유효한 형식의 색상 이름일 수 있습니다.

```html
<html>
   <head>
      <style type = "text/css">
         a:active {color: #FF00CC}
      </style>
   </head>

   <body>
      <a href = "">Click This Link</a>
   </body>
</html>
```

### :focus 가상 클래스
다음 예제는 :focus 클래스를 사용하여 포커스가 있는 링크의 색상을 변경하는 방법을 보여줍니다. 가능한 값은 모든 유효한 형식의 색상 이름일 수 있습니다.

```html
<html>
   <head>
      <style type = "text/css">
         a:focus {color: #0000FF}
      </style>
   </head>

   <body>
      <a href = "">Click this Link</a>
   </body>
</html>
```

### :first-child 가상 클래스
:first-child 가상 클래스는 특정 요소의 첫 번째 자식 요소를 선택하여 해당 요소에 특별한 스타일을 추가합니다.

IE에서 :first-child가 작동하려면 문서의 맨 위에 <!DOCTYPE>을 선언해야 합니다.

예를 들어, 모든 `<div>` 요소의 첫 번째 단락을 들여쓰기 하려면 다음 정의를 사용할 수 있습니다 −

```html
<html>
   <head>
      <style type = "text/css">
         div > p:first-child {
            text-indent: 25px;
         }
      </style>
   </head>

   <body>
      <div>
         <p>First paragraph in div. This paragraph will be indented</p>
         <p>Second paragraph in div. This paragraph will not be indented</p>
      </div>
      <p>But it will not match the paragraph in this HTML:</p>
      <div>
         <h3>Heading</h3>
         <p>The first paragraph inside the div. This paragraph will not be effected.</p>
      </div>
   </body>
</html>
```

### :lang 가상 클래스
언어 가상 클래스 :lang은 특정 태그에 대한 언어 설정을 기반으로 선택자를 구성할 수 있게 합니다.

이 클래스는 특정 언어 구문에 대한 관례가 다른 여러 언어에 호소해야 하는 문서에서 유용합니다. 예를 들어, 프랑스어는 인용 목적으로 일반적으로 꺾쇠 괄호(< 및 >)를 사용하고, 영어는 인용 부호(' 및 ')를 사용합니다.

이 차이점을 해결해야 하는 문서에서는 :lang 가상 클래스를 사용하여 인용 부호를 적절하게 변경할 수 있습니다. 다음 코드는 사용 중인 언어에 적합하게 `<blockquote>` 태그를 변경합니다 −

```html
<html>
   <head>
      <style type = "text/css">
         /* 두 언어에 대한 두 수준의 인용 부호 */
         :lang(en) { quotes: '"' '"'  "'"  "'"; }
         :lang(fr) { quotes: "<<" ">>" "<" ">"; }
      </style>
   </head>
   
   <body>
      <p>...<q lang = "fr">A quote in a paragraph</q>...</p>
   </body>
</html>
```

---

## CSS - Pseudo Elements


가장 일반적으로 사용되는 가상 요소는 다음과 같습니다 −

1  
:first-line  
이 요소를 사용하여 선택자 내 텍스트의 첫 번째 줄에 특별한 스타일을 추가합니다.

2  
:first-letter  
이 요소를 사용하여 선택자 내 텍스트의 첫 글자에 특별한 스타일을 추가합니다.

3  
:before  
이 요소를 사용하여 요소 앞에 일부 내용을 삽입합니다.

4  
:after  
이 요소를 사용하여 요소 뒤에 일부 내용을 삽입합니다.

### :first-line 가상 요소
다음 예제는 :first-line 요소를 사용하여 문서 내 요소의 첫 번째 줄에 특별한 효과를 추가하는 방법을 보여줍니다.

```html
<html>
   <head>
      <style type = "text/css">
         p:first-line { text-decoration: underline; }
         p.noline:first-line { text-decoration: none; }
      </style>
   </head>

   <body>
      <p class = "noline">
         이 줄은 noline 클래스에 속하므로 밑줄이 없습니다.
      </p>
      
      <p>
         이 단락의 첫 번째 줄은 위의 CSS 규칙에 정의된 대로 밑줄이 그어집니다. 
         이 단락의 나머지 줄은 그대로 유지됩니다. 이 예제는 :first-line 
         가상 요소를 사용하여 HTML 요소의 첫 번째 줄에 효과를 주는 방법을 보여줍니다.
      </p>
   </body>
</html>
```

### :first-letter 가상 요소
다음 예제는 :first-letter 요소를 사용하여 문서 내 요소의 첫 글자에 특별한 효과를 추가하는 방법을 보여줍니다.

```html
<html>
   <head>
      <style type = "text/css">
         p:first-letter { font-size: 5em; }
         p.normal:first-letter { font-size: 10px; }
      </style>
   </head>

   <body>
      <p class = "normal">
         이 단락의 첫 번째 문자는 정상 크기이며, 글꼴 크기는 10px입니다.
      </p>
      
      <p>
         이 단락의 첫 번째 문자는 위의 CSS 규칙에 정의된 대로 5em 크기로 커집니다. 
         이 단락의 나머지 문자는 그대로 유지됩니다. 이 예제는 :first-letter 
         가상 요소를 사용하여 HTML 요소의 첫 글자에 효과를 주는 방법을 보여줍니다.
      </p>
   </body>
</html>
```

### :before 가상 요소
다음 예제는 :before 요소를 사용하여 요소 앞에 일부 내용을 추가하는 방법을 보여줍니다.

```html
<html>
   <head>
      <style type = "text/css">
         p:before {
            content: url(/images/bullet.gif)
         }
      </style>
   </head>

   <body>
      <p> 이 줄 앞에 불릿이 표시됩니다.</p>
      <p> 이 줄 앞에 불릿이 표시됩니다.</p>
      <p> 이 줄 앞에 불릿이 표시됩니다.</p>
   </body>
</html>
```

### :after 가상 요소
다음 예제는 :after 요소를 사용하여 요소 뒤에 일부 내용을 추가하는 방법을 보여줍니다.

```html
<html>
   <head>
      <style type = "text/css">
         p:after {
            content: url(/images/bullet.gif)
         }
      </style>
   </head>

   <body>
      <p> 이 줄 뒤에 불릿이 표시됩니다.</p>
      <p> 이 줄 뒤에 불릿이 표시됩니다.</p>
      <p> 이 줄 뒤에 불릿이 표시됩니다.</p>
   </body>
</html>
```
---
## CSS - @ Rules


### @import 규칙
@import 규칙을 사용하면 다른 스타일 시트에서 스타일을 가져올 수 있습니다. 이 규칙은 스타일 시트의 시작 부분에 나와야 하며, 값은 URL입니다.

다음 두 가지 방법 중 하나로 작성할 수 있습니다 −

```html
<style type = "text/css">
   <!--
      @import "mystyle.css";
      or
      @import url("mystyle.css");
      .......other CSS rules .....
   -->
</style>
```

@import 규칙의 중요성은 모듈 방식으로 스타일 시트를 개발할 수 있게 해준다는 점입니다. 다양한 스타일 시트를 만들고 필요한 곳에 포함시킬 수 있습니다.

### @charset 규칙
ASCII 또는 ISO-8859-1이 아닌 다른 문자 집합을 사용하여 문서를 작성하는 경우, 스타일 시트 상단에 @charset 규칙을 설정하여 스타일 시트가 작성된 문자 집합을 나타낼 수 있습니다.

@charset 규칙은 스타일 시트의 맨 처음에 공백 없이 작성해야 합니다. 값은 인용 부호로 감싸야 하며, 표준 문자 집합 중 하나여야 합니다. 예를 들어 −

```html
<style type = "text/css">
   <!--
      @charset "iso-8859-1"
      .......other CSS rules .....
   -->
</style>
```

### @font-face 규칙
@font-face 규칙은 문서에서 사용할 글꼴을 자세히 설명하는 데 사용됩니다. @font-face는 다운로드할 글꼴의 위치를 정의하는 데도 사용할 수 있지만, 구현에 따라 제한이 있을 수 있습니다.

일반적으로 @font-face는 매우 복잡하며, 폰트 메트릭스 전문가를 제외하고는 사용을 권장하지 않습니다.

예를 들어 −

```html
<style type = "text/css">
   <!--
      @font-face {
         font-family: "Scarborough Light";
         src: url("http://www.font.site/s/scarbo-lt");
      }
      @font-face {
         font-family: Santiago;
         src: local ("Santiago"),
         url("http://www.font.site/s/santiago.tt")
         format("truetype");
         unicode-range: U+??,U+100-220;
         font-size: all;
         font-family: sans-serif;
      }
   -->
</style>
```

### !important 규칙
계단식 스타일 시트는 계단식으로 적용됩니다. 이는 스타일이 브라우저에 의해 읽히는 순서대로 적용된다는 의미입니다. 첫 번째 스타일이 적용되고, 그 다음 스타일이 적용되는 식입니다.

!important 규칙은 CSS가 계단식으로 적용되도록 합니다. 또한 항상 적용해야 하는 규칙을 포함합니다. !important 속성이 있는 규칙은 CSS 문서 어디에 있든 항상 적용됩니다.

예를 들어, 다음 스타일 시트에서 첫 번째 스타일 속성이 빨간색으로 적용되었음에도 불구하고 단락 텍스트는 검정색으로 표시됩니다:

```html
<style type = "text/css">
   <!--
      p { color: #ff0000; }
      p { color: #000000; }
   -->
</style>
```

따라서 속성이 항상 적용되도록 하려면 해당 태그에 !important 속성을 추가해야 합니다. 단락 텍스트를 항상 빨간색으로 만들려면 다음과 같이 작성해야 합니다 −

```html
<html>
   <head>
      <style type = "text/css">
         p { color: #ff0000 !important; }
         p { color: #000000; }
      </style>
   </head>

   <body>
      <p>Tutorialspoint.com</p>
   </body>
</html> 
```

여기서 p { color: #ff0000 !important; }를 필수로 만들었으므로, 이제 이 규칙은 p { color: #000000; } 규칙이 정의되어 있더라도 항상 적용됩니다.

---
## CSS Filters - Text and Image Effects

1  
opacity  
불투명도의 수준. 0은 완전히 투명하고, 100은 완전히 불투명합니다.

2  
finishopacity  
객체의 다른 끝에서의 불투명도 수준.

3  
style  
불투명도 그라데이션의 모양.  
0 = 균일  
1 = 선형  
2 = 방사형  
3 = 직사각형

4  
startX  
불투명도 그라데이션이 시작되는 X 좌표.

5  
startY  
불투명도 그라데이션이 시작되는 Y 좌표.

6  
finishX  
불투명도 그라데이션이 끝나는 X 좌표.

7  
finishY  
불투명도 그라데이션이 끝나는 Y 좌표.

### 예제
```html
<html>
   <head>
   </head>
   
   <body>
      <p>이미지 예제:</p>
      
      <img src = "/css/images/logo.png" alt = "CSS Logo" 
         style = "Filter: Alpha(Opacity=100, 
         FinishOpacity = 0, 
         Style = 2, 
         StartX = 20, 
         StartY = 40, 
         FinishX = 0, 
         FinishY = 0)" />
      <p>텍스트 예제:</p>
      
      <div style = "width: 357; 
         height: 50; 
         font-size: 30pt; 
         font-family: Arial Black; 
         color: blue;
         Filter: Alpha(Opacity=100, FinishOpacity=0, Style=1, StartX=0, StartY=0, FinishX=580, FinishY=0)">CSS Tutorials</div>
   </body>
</html>
```

### 모션 블러
모션 블러는 방향과 강도로 흐릿한 그림이나 텍스트를 생성하는 데 사용됩니다. 이 필터에는 다음 매개변수를 사용할 수 있습니다.

1  
add  
참 또는 거짓. 참이면 이미지를 흐릿한 이미지에 추가하고, 거짓이면 이미지를 흐릿한 이미지에 추가하지 않습니다.

2  
direction  
흐림의 방향으로, 시계 방향으로 45도 단위로 반올림됩니다. 기본값은 270 (왼쪽)입니다.  
0 = 상단  
45 = 우상단  
90 = 오른쪽  
135 = 우하단  
180 = 하단  
225 = 좌하단  
270 = 왼쪽  
315 = 좌상단

3  
strength  
흐림이 확장되는 픽셀 수. 기본값은 5픽셀입니다.

### 예제
```html
<html>
   <head>
   </head>
   
   <body>
      <p>이미지 예제:</p>
      
      <img src = "/css/images/logo.png" alt = "CSS Logo" 
         style = "Filter: Blur(Add = 0, Direction = 225, Strength = 10)">
      
      <p>텍스트 예제:</p>
      
      <div style = "width: 357; 
         height: 50; 
         font-size: 30pt; 
         font-family: Arial Black; 
         color: blue; 
         Filter: Blur(Add = 1, Direction = 225, Strength = 10)">CSS Tutorials
      </div>
   </body>
</html>
```

### 크로마 필터
크로마 필터는 특정 색상을 투명하게 만드는 데 사용되며 주로 이미지와 함께 사용됩니다. 스크롤바에도 사용할 수 있습니다. 이 필터에는 다음 매개변수를 사용할 수 있습니다.

1  
color  
투명하게 만들 색상.

### 예제
```html
<html>
   <head>
   </head>
   
   <body>
      <p>이미지 예제:</p>
      
      <img src = "/images/css.gif" 
         alt = "CSS Logo" style = "Filter: Chroma(Color = #FFFFFF)">
      
      <p>텍스트 예제:</p>
      
      <div style = "width: 580; 
         height: 50; 
         font-size: 30pt; 
         font-family: Arial Black; 
         color: #3300FF; 
         Filter: Chroma(Color = #3300FF)">CSS Tutorials</div>
   </body>
</html>
```

### 드롭 쉐도우 효과
드롭 쉐도우는 객체의 지정된 X(수평) 및 Y(수직) 오프셋과 색상에 따라 그림자를 생성하는 데 사용됩니다.

이 필터에는 다음 매개변수를 사용할 수 있습니다.

1  
color  
드롭 쉐도우의 색상, #RRGGBB 형식.

2  
offX  
시각적 객체에서 드롭 쉐도우가 오프셋되는 픽셀 수, x축을 따라. 양수는 드롭 쉐도우를 오른쪽으로 이동시키고, 음수는 드롭 쉐도우를 왼쪽으로 이동시킵니다.

3  
offY  
시각적 객체에서 드롭 쉐도우가 오프셋되는 픽셀 수, y축을 따라. 양수는 드롭 쉐도우를 아래로 이동시키고, 음수는 드롭 쉐도우를 위로 이동시킵니다.

4  
positive  
참이면 객체의 모든 불투명한 픽셀이 드롭 쉐도우를 가집니다. 거짓이면 모든 투명 픽셀이 드롭 쉐도우를 가집니다. 기본값은 참입니다.

### 예제
```html
<html>
   <head>
   </head>
   
   <body>
      <p>이미지 예제:</p>
      
      <img src = "/css/images/logo.png" 
         alt = "CSS Logo" 
         style = "filter:drop-shadow(2px 2px 1px #FF0000);">
      
      <p>텍스트 예제:</p>
      
      <div style = "width: 357; 
         height: 50; 
         font-size: 30pt; 
         font-family: Arial Black; 
         color: red; 
         filter:drop-shadow(3px 3px 2px #000000);">CSS Tutorials</div>
   </body>
</html>
```

### 플립 효과
플립 효과는 객체의 거울 이미지를 만드는 데 사용됩니다. 이 필터에는 다음 매개변수를 사용할 수 있습니다.

1  
FlipH  
수평 거울 이미지를 만듭니다.

2  
FlipV  
수직 거울 이미지를 만듭니다.

### 예제
```html
<html>
   <head>
   </head>
   
   <body>
      <p>이미지 예제:</p>
      
      <img src = "/css/images/logo.png" 
         alt = "CSS Logo" 
         style = "filter: FlipH">
      
      <img src = "/css/images/logo.png" alt = "CSS Logo" style = "filter: FlipV">
      
      <p>텍스트 예제:</p>
      
      <div style = "width: 300; 
         height: 50; 
         font-size: 30pt; 
         font-family: Arial Black; 
         color: red; 
         filter: FlipV">CSS Tutorials</div>
   </body>
</html>
```

### 글로우 효과
글로우 효과는 객체 주위에 빛나는 효과를 생성하는 데 사용됩니다. 투명한 이미지인 경우, 불투명한 픽셀 주위에 글로우가 생성됩니다. 이 필터에는 다음 매개변수를 사용할 수 있습니다.

1  
color  
글로우 색상.

2  
strength  
글로우의 강도 (1에서 255까지).

### 예제
```html
<html>
   <head>
   </head>
   
   <body>
      <p>이미지 예제:</p>
      
      <img src = "/css/images/logo.png" 
         alt = "CSS Logo" 
         style = "filter: Chroma(Color = #000000) Glow(Color=#00FF00, Strength=20)">
      
      <p>텍스트 예제:</p>
      
      <div style = "width: 357; 
         height: 50; 
         font-size: 30pt; 
         font-family: Arial Black; 
         color: red; 
         filter: Glow(Color=#00FF00, Strength=20)">CSS Tutorials</div>
   </body>
</html>
```

### 그레이스케일 효과
그레이스케일 효과는 객체의 색상을 256단계의 회색으로 변환하는 데 사용됩니다. 이 필터에는 다음 매개변수가 사용됩니다.

1  
grayscale  
객체의 색상을 256단계의 회색으로 변환합니다.

### 예제
```html
<html>
   <head>
   </head>
   
   <body>
      <p>이미지 예제:</p>
      
      <img src = "/css/images/logo.png" 
         alt = "CSS Logo" 
         style = "filter: grayscale(50%)">
      
      <p>텍스트 예제:</p>
      
      <div style = "width: 357; 
         height: 50; 
         font-size: 30pt

; 
         font-family: Arial Black; 
         color: red; 
         filter: grayscale(50%)">CSS Tutorials</div>
   </body>
</html>
```

### 인버트 효과
인버트 효과는 객체의 색상을 색상 스펙트럼에서 반대값으로 매핑하여 네거티브 이미지를 만드는 데 사용됩니다. 이 필터에는 다음 매개변수가 사용됩니다.

1  
invert  
객체의 색상을 색상 스펙트럼에서 반대값으로 매핑합니다.

### 예제
```html
<html>
   <head>
   </head>
   
   <body>
      <p>이미지 예제:</p>
      
      <img src = "/css/images/logo.png" 
         alt = "CSS Logo" 
         style = "filter: invert(100%)">
      
      <p>텍스트 예제:</p>
      
      <div style = "width: 357; 
         height: 50; 
         font-size: 30pt; 
         font-family: Arial Black; 
         color: red; 
         filter: invert(100%)">CSS Tutorials</div>
   </body>
</html>
```

### 마스크 효과
마스크 효과는 투명한 픽셀을 지정된 색상으로 바꾸고 불투명한 픽셀을 투명하게 만드는 데 사용됩니다. 이 필터에는 다음 매개변수가 사용됩니다.

1  
color  
투명한 영역이 될 색상.

### 예제
```html
<html>
   <head>
   </head>
   
   <body>
      <p>이미지 예제:</p>
      
      <img src = "/css/images/logo.png" 
         alt = "CSS Logo" 
         style = "filter: Chroma(Color = #000000) Mask(Color=#00FF00)">
      
      <p>텍스트 예제:</p>
      
      <div style = "width: 357; 
         height: 50; 
         font-size: 30pt; 
         font-family: Arial Black; 
         color: red; 
         filter: Mask(Color=#00FF00)">CSS Tutorials
      </div>
   </body>
</html>
```

### 쉐도우 필터
쉐도우 필터는 지정된 방향과 색상으로 약화된 그림자를 생성하는 데 사용됩니다. 이 필터는 드롭 쉐도우와 글로우 사이의 필터입니다. 이 필터에는 다음 매개변수를 사용할 수 있습니다.

1  
color  
그림자의 색상.

2  
direction  
시계 방향으로 45도 단위로 반올림된 흐림 방향. 기본값은 270 (왼쪽)입니다.  
0 = 상단  
45 = 우상단  
90 = 오른쪽  
135 = 우하단  
180 = 하단  
225 = 좌하단  
270 = 왼쪽  
315 = 좌상단

### 예제
```html
<html>
   <head>
   </head>
   
   <body>
      <p>이미지 예제:</p>
      
      <img src = "/css/images/logo.png" 
         alt = "CSS Logo" 
         style = "filter: Chroma(Color = #000000) Shadow(Color=#00FF00, Direction=225)">
      
      <p>텍스트 예제:</p>
      
      <div style = "width: 357; 
         height: 50; 
         font-size: 30pt; 
         font-family: 
         Arial Black; 
         color: red; 
         filter: Shadow(Color=#0000FF, Direction=225)">CSS Tutorials
      </div>
   </body>
</html>
```

### 웨이브 효과
웨이브 효과는 객체에 사인파 왜곡을 주어 물결 모양으로 보이게 합니다. 이 필터에는 다음 매개변수를 사용할 수 있습니다.

1  
add  
값이 1이면 원본 이미지를 물결 이미지에 추가하고, 0이면 추가하지 않습니다.

2  
freq  
파도의 수.

3  
light  
파도 위의 빛의 강도 (0에서 100까지).

4  
phase  
사인파가 시작해야 하는 각도 (0에서 100까지).

5  
strength  
웨이브 효과의 강도.

### 예제
```html
<html>
   <head>
   </head>
   
   <body>
      <p>이미지 예제:</p>
      
      <img src = "/css/images/logo.png" 
         alt = "CSS Logo" 
         style = "filter: Chroma(Color = #000000) 
         Wave(Add=0, Freq=1, LightStrength=10, Phase=220, Strength=10)">
      
      <p>텍스트 예제:</p>
      
      <div style = "width: 357; 
         height: 50; 
         font-size: 30pt; 
         font-family: Arial Black; 
         color: red; 
         filter: Wave(Add=0, Freq=1, LightStrength=10, Phase=20, Strength=20)">CSS Tutorials
      </div>
   </body>
</html>
```

### X-레이 효과
X-레이 효과는 색상 깊이를 회색조로 변환하고 평탄화합니다. 이 필터에는 다음 매개변수가 사용됩니다.

1  
xray  
색상 깊이를 회색조로 변환하고 평탄화합니다.

### 예제
```html
<html>
   <head>
   </head>
   
   <body>
      <p>이미지 예제:</p>
      
      <img src = "/css/images/logo.png" 
         alt = "CSS Logo" 
         style = "filter: Xray">
      
      <p>텍스트 예제:</p>
      
      <div style = "width: 357; 
         height: 50; 
         font-size: 30pt; 
         font-family: Arial Black; 
         color: red; 
         filter: Xray">CSS Tutorials
      </div>
   </body>
</html>
```

---
## CSS - Media Types

아래는 예제입니다 −

```html
<style type = "text/css">
   <!--
      @media print {
         body { font-size: 10pt }
      }
	
      @media screen {
         body { font-size: 12pt }
      }
      @media screen, print {
         body { line-height: 1.2 }
      }
   -->
</style>
```

### 문서 언어
HTML 4.0에서 LINK 요소의 media 속성은 외부 스타일 시트의 대상 매체를 지정합니다 −

다음은 예제입니다 −

```html
<style type = "text/css">
   <!--
      <!doctype html public "-//w3c//dtd html 4.0//en">
      <html>
         <head>
            <title>link to a target medium</title>
            <link rel = "stylesheet" type = "text/css" media = "print, 
               handheld" href = "foo.css">
         </head>

         <body>
            <p>the body...
         </body>
      </html>
   -->
</style>
```

### 인식된 미디어 유형
CSS 미디어 유형에 선택된 이름은 관련 속성이 의미 있는 대상 장치를 반영합니다. 미디어 유형이 참조하는 장치에 대한 느낌을 제공합니다. 아래는 다양한 미디어 유형의 목록입니다 −

1. **all**  
   모든 장치에 적합합니다.

2. **aural**  
   음성 합성기를 위한 것입니다.

3. **braille**  
   점자 촉각 피드백 장치를 위한 것입니다.

4. **embossed**  
   페이지 점자 프린터를 위한 것입니다.

5. **handheld**  
   핸드헬드 장치(일반적으로 작은 화면, 단색, 제한된 대역폭)를 위한 것입니다.

6. **print**  
   페이지 불투명 재료 및 인쇄 미리보기 모드에서 화면에 표시되는 문서를 위한 것입니다. 페이지 매체에 관한 섹션을 참조하십시오.

7. **projection**  
   프로젝터 또는 투명 필름 인쇄를 위한 투사 프레젠테이션을 위한 것입니다. 페이지 매체에 관한 섹션을 참조하십시오.

8. **screen**  
   주로 컬러 컴퓨터 화면을 위한 것입니다.

9. **tty**  
   고정 폭 문자 그리드를 사용하는 미디어, 예를 들어 텔레타이프, 터미널 또는 제한된 디스플레이 기능을 가진 휴대용 장치를 위한 것입니다.

10. **tv**  
   텔레비전형 장치를 위한 것입니다.

**NOTE** − 미디어 유형 이름은 대소문자를 구분하지 않습니다.

---
## CSS Paged Media - @page Rule


CSS2는 "페이지 박스"를 정의합니다. 페이지 박스는 콘텐츠가 렌더링되는 유한한 크기의 상자입니다. 페이지 박스는 두 영역을 포함하는 직사각형 영역입니다 −

- 페이지 영역 − 페이지 영역에는 해당 페이지에 배치된 박스들이 포함됩니다. 페이지 영역의 가장자리는 페이지 나누기 사이의 레이아웃을 위한 초기 포함 블록으로 작동합니다.
- 마진 영역 − 페이지 영역을 둘러싸는 영역입니다.

`@page` 규칙 내에서 페이지 박스의 크기, 방향, 마진 등을 지정할 수 있습니다. 페이지 박스의 크기는 `size` 속성으로 설정됩니다. 페이지 영역의 크기는 마진 영역을 뺀 페이지 박스의 크기입니다.

예를 들어, 다음 `@page` 규칙은 페이지 박스의 크기를 8.5 × 11인치로 설정하고 페이지 박스 가장자리와 페이지 영역 사이에 모든 면에 대해 2cm의 마진을 만듭니다 −

```html
<style type = "text/css">
   <!--
      @page { size:8.5in 11in; margin: 2cm }
   -->
</style>
```

`@page` 규칙 내에서 `margin`, `margin-top`, `margin-bottom`, `margin-left`, 및 `margin-right` 속성을 사용하여 페이지의 마진을 설정할 수 있습니다.

마지막으로, `marks` 속성은 `@page` 규칙 내에서 페이지 박스 외부의 대상 시트에 자르기 및 등록 마크를 생성하는 데 사용됩니다. 기본적으로 마크는 인쇄되지 않습니다. 자르기 마크와 등록 마크를 생성하기 위해 각각 `crop` 및 `cross` 키워드를 사용할 수 있습니다.

### 페이지 크기 설정
`size` 속성은 페이지 박스의 크기와 방향을 지정합니다. 페이지 크기에 사용할 수 있는 네 가지 값이 있습니다 −

- auto − 페이지 박스는 대상 시트의 크기와 방향으로 설정됩니다.
- landscape − 대상의 방향을 무시합니다. 페이지 박스는 대상과 동일한 크기이며 긴 면이 수평입니다.
- portrait − 대상의 방향을 무시합니다. 페이지 박스는 대상과 동일한 크기이며 짧은 면이 수평입니다.
- length − 'size' 속성의 길이 값은 절대 페이지 박스를 만듭니다. 길이 값이 하나만 지정된 경우 페이지 박스의 너비와 높이를 모두 설정합니다. 'size' 속성에는 백분율 값이 허용되지 않습니다.

다음 예제에서 페이지 박스의 외곽선은 대상과 일치합니다. 'margin' 속성의 백분율 값은 대상 크기에 상대적이므로 대상 시트 크기가 21.0cm × 29.7cm(A4)인 경우, 마진은 각각 2.10cm 및 2.97cm입니다.

```html
<style type = "text/css">
   <!--
      @page {
         size: auto;   /* auto는 초기 값입니다 */
         margin: 10%;
      }
   -->
</style>
```

다음 예제에서는 페이지 박스의 너비를 8.5인치, 높이를 11인치로 설정합니다. 이 예제의 페이지 박스는 8.5" × 11" 또는 더 큰 대상 시트 크기를 요구합니다.

```html
<style type = "text/css">
   <!--
      @page {
         size: 8.5in 11in;  /* 너비 높이 */
      }
   -->
</style>
```

이름이 지정된 페이지 레이아웃을 생성한 후, 문서 내의 요소에 적용된 스타일에 `page` 속성을 추가하여 문서에서 이를 사용할 수 있습니다. 예를 들어, 다음 스타일은 문서의 모든 테이블을 가로 페이지에 렌더링합니다 −

```html
<style type = "text/css">
   <!--
      @page { size : portrait }
      @page rotated { size : landscape }
      table { page : rotated }
   -->
</style>
```

위 규칙에 따라 인쇄 시 브라우저가 문서 내에서 `<table>` 요소를 만나고 현재 페이지 레이아웃이 기본 세로 레이아웃인 경우, 새 페이지를 시작하고 테이블을 가로 페이지에 인쇄합니다.

### 왼쪽, 오른쪽 및 첫 번째 페이지
양면 문서를 인쇄할 때 왼쪽과 오른쪽 페이지의 페이지 박스는 달라야 합니다. 이는 두 CSS 가상 클래스(pseudo-classes)를 통해 다음과 같이 표현할 수 있습니다 −

```html
<style type = "text/css">
   <!--
      @page :left {
         margin-left: 4cm;
         margin-right: 3cm;
      }

      @page :right {
         margin-left: 3cm;
         margin-right: 4cm;
      }
   -->
</style>
```

문서의 첫 페이지 스타일은 `:first` 가상 클래스를 사용하여 지정할 수 있습니다 −

```html
<style type = "text/css">
   <!--
      @page { margin: 2cm } /* 모든 마진을 2cm로 설정 */

      @page :first {
         margin-top: 10cm    /* 첫 페이지의 상단 마진을 10cm로 설정 */
      }
   -->
</style>
```

### 페이지 나누기 제어
별도로 지정하지 않으면 페이지 나누기는 페이지 형식이 변경되거나 현재 페이지 박스의 콘텐츠가 넘칠 때만 발생합니다. 페이지 나누기를 강제하거나 억제하려면 `page-break-before`, `page-break-after` 및 `page-break-inside` 속성을 사용하십시오.

`page-break-before` 및 `page-break-after` 속성은 `auto`, `always`, `avoid`, `left` 및 `right` 키워드를 허용합니다.

키워드 `auto`는 기본값이며, 필요에 따라 브라우저가 페이지 나누기를 생성할 수 있게 합니다. 키워드 `always`는 요소 앞이나 뒤에 항상 페이지 나누기를 강제하며, `avoid`는 요소 앞이나 뒤에 페이지 나누기를 억제합니다. 키워드 `left`와 `right`는 요소가 왼쪽 또는 오른쪽 페이지에 렌더링되도록 한두 개의 페이지 나누기를 강제합니다.

페이지 매김 속성 사용은 매우 간단합니다. 예를 들어, 문서에 1단계 헤더가 새 챕터를 시작하고 2단계 헤더가 섹션을 나타낸다고 가정해 봅시다. 각 챕터를 새로운 오른쪽 페이지에서 시작하고 싶지만 섹션 헤더가 페이지 나누기로 인해 다음 콘텐츠와 분리되지 않도록 하고 싶습니다. 다음 규칙을 사용하여 이를 달성할 수 있습니다 −

```html
<style type = "text/css">
   <!--
      h1 { page-break-before : right }
      h2 { page-break-after : avoid }
   -->
</style>
```

`page-break-inside` 속성에는 `auto`와 `avoid` 값만 사용하십시오. 테이블이 페이지를 넘어가지 않도록 하려면 다음 규칙을 작성하십시오 −

```html
<style type = "text/css">
   <!--
      table { page-break-inside : avoid }
   -->
</style>
```

### 고아(Widows) 및 미망인(Orphans) 제어
타이포그래피 용어에서 고아(orphan)는 페이지 나누기로 인해 페이지 하단에 고립된 단락의 줄을 의미하며, 미망인(widow)은 페이지 나누기 후 페이지 상단에 남은 단락의 줄을 의미합니다. 일반적으로 인쇄된 페이지는 상단이나 하단에 고립된 한 줄의 텍스트가 있으면 보기 좋지 않습니다. 대부분의 프린터는 페이지 상단이나 하단에 최소한 두 줄 이상의 텍스트를 남기려고 합니다.

`orphans` 속성은 페이지 하단에 남아 있어야 하는 단락의 최소 줄 수를 지정합니다.

`widows` 속성은 페이지 상단에 남아 있어야 하는 단락의 최소 줄 수를 지정합니다.

다음은 각 페이지의 하단에 4줄, 상단에 3줄을 생성하는 예제입니다 −

```html
<style type = "text/css">
   <!--
      @page{orphans:4; widows:2;}
   -->
</style>
```
---
## CSS - Aural Media


청각 속성을 사용할 때, 캔버스는 삼차원 물리적 공간(소리의 주위)과 시간적 공간(소리를 다른 소리 전에, 도중에, 또는 후에 지정할 수 있는)을 포함합니다.

CSS 속성은 합성 음성의 품질(음성 유형, 주파수, 억양 등)을 다양하게 설정할 수 있게 합니다.

다음은 예시입니다 −

```html
<html>
   <head>
      <style type = "text/css">
         h1, h2, h3, h4, h5, h6 {
            voice-family: paul;
            stress: 20;
            richness: 90;
            cue-before: url("../audio/pop.au");
         }
         p {
            azimuth:center-right;
         }
      </style>
   </head>

   <body>
   
      <h1>Tutorialspoint.com</h1>
      <h2>Tutorialspoint.com</h2>
      <h3>Tutorialspoint.com</h3>
      <h4>Tutorialspoint.com</h4>
      <h5>Tutorialspoint.com</h5>
      <h6>Tutorialspoint.com</h6>
      <p>Tutorialspoint.com</p>
      
   </body>
</html>
```

이 예시는 음성 합성기가 제목을 'paul'이라는 음성으로 낭독하도록 지시합니다. 평평한 톤으로 하지만 매우 풍부한 목소리로 낭독합니다. 제목을 낭독하기 전에 지정된 URL에서 사운드 샘플이 재생됩니다.

‘heidi’ 클래스의 단락은 앞 왼쪽에서 나오는 것처럼 보이고(공간 오디오를 지원하는 경우), ‘peter’ 클래스의 단락은 오른쪽에서 나오는 것처럼 보입니다.

이제 청각 미디어와 관련된 다양한 속성을 살펴보겠습니다.

### azimuth 속성
azimuth 속성은 소리가 수평으로 어디에서 나와야 하는지를 설정합니다. 가능한 값은 다음과 같습니다 −

- angle − 위치를 -360도에서 360도 범위의 각도로 설명합니다. 값 0도는 사운드 스테이지의 중앙 바로 앞을 의미합니다. 90도는 오른쪽, 180도는 뒤, 270도(또는 -90도)는 왼쪽을 의미합니다.
- left-side − '270도'와 같습니다. 'behind'와 함께 사용 시 '270도'와 같습니다.
- far-left − '300도'와 같습니다. 'behind'와 함께 사용 시 '240도'와 같습니다.
- left − '320도'와 같습니다. 'behind'와 함께 사용 시 '220도'와 같습니다.
- center-left − '340도'와 같습니다. 'behind'와 함께 사용 시 '200도'와 같습니다.
- center − '0도'와 같습니다. 'behind'와 함께 사용 시 '180도'와 같습니다.
- center-right − '20도'와 같습니다. 'behind'와 함께 사용 시 '160도'와 같습니다.
- right − '40도'와 같습니다. 'behind'와 함께 사용 시 '140도'와 같습니다.
- far-right − '60도'와 같습니다. 'behind'와 함께 사용 시 '120도'와 같습니다.
- right-side − '90도'와 같습니다. 'behind'와 함께 사용 시 '90도'와 같습니다.
- leftwards − 소리를 현재 각도에서 왼쪽으로 이동합니다. 더 정확히 말하면 20도를 뺍니다.
- rightwards − 소리를 현재 각도에서 오른쪽으로 이동합니다. 더 정확히 말하면 20도를 더합니다.

다음은 예시입니다 −

```html
<style type = "text/css">
   <!--
      h1   { azimuth: 30deg }
      td.a { azimuth: far-right }          /*  60도 */
      #12  { azimuth: behind far-right }   /* 120도 */
      p.comment { azimuth: behind }        /* 180도 */
   -->
</style>
```

### elevation 속성
elevation 속성은 소리가 수직으로 어디에서 나와야 하는지를 설정합니다. 가능한 값은 다음과 같습니다 −

- angle − -90도에서 90도 사이의 각도로 높이를 지정합니다. 0도는 전방 수평선(듣는 사람과 수평)을 의미합니다. 90도는 바로 위를, -90도는 바로 아래를 의미합니다.
- below − '-90도'와 같습니다.
- level − '0도'와 같습니다.
- above − '90도'와 같습니다.
- higher − 현재 높이에서 10도를 더합니다.
- lower − 현재 높이에서 10도를 뺍니다.

다음은 예시입니다 −

```html
<style type = "text/css">
   <!--
      h1   { elevation: above }
      tr.a { elevation: 60deg }
      tr.b { elevation: 30deg }
      tr.c { elevation: level }
   -->
</style>
```

### cue-after 속성
cue-after 속성은 다른 요소와 구분하기 위해 요소의 내용을 말한 후 재생할 소리를 지정합니다. 가능한 값은 다음과 같습니다 −

- url − 재생할 사운드 파일의 URL입니다.
- none − 아무 것도 재생하지 않습니다.

다음은 예시입니다 −

```html
<style type = "text/css">
   <!--
      a {cue-after: url("dong.wav");}
      h1 {cue-after: url("pop.au"); }
   -->
</style>
```

### cue-before 속성
cue-before 속성은 다른 요소와 구분하기 위해 요소의 내용을 말하기 전에 재생할 소리를 지정합니다. 가능한 값은 다음과 같습니다 −

- url − 재생할 사운드 파일의 URL입니다.
- none − 아무 것도 재생하지 않습니다.

다음은 예시입니다 −

```html
<style type = "text/css">
   <!--
      a {cue-before: url("bell.aiff");}
      h1 {cue-before: url("pop.au"); }
   -->
</style>
```

### cue 속성
cue 속성은 cue-before와 cue-after를 설정하는 축약형입니다. 두 값이 주어지면 첫 번째 값은 cue-before, 두 번째 값은 cue-after로 적용됩니다. 하나의 값만 주어지면 두 속성 모두에 적용됩니다.

다음 두 규칙은 동일합니다 −

```html
<style type = "text/css">
   <!--
      h1 {cue-before: url("pop.au"); cue-after: url("pop.au") }
      h1 {cue: url("pop.au") }
   -->
</style>
```

### pause-after 속성
pause-after 속성은 요소의 내용을 말한 후 멈춤 시간을 지정합니다. 가능한 값은 다음과 같습니다 −

- time − 절대 시간 단위(초 및 밀리초)로 멈춤 시간을 표현합니다.
- percentage − speech-rate 속성 값의 역수를 참조합니다. 예를 들어, speech-rate가 분당 120단어(즉, 단어 하나에 500ms가 걸림)인 경우, pause-after가 100%이면 500ms의 멈춤 시간을 의미하고 pause-after가 20%이면 100ms의 멈춤 시간을 의미합니다.

### pause-before 속성
pause-before 속성은 요소의 내용을 말하기 전에 멈춤 시간을 지정합니다. 가능한 값은 다음과 같습니다 −

- time − 절대 시간 단위(초 및 밀리초)로 멈춤 시간을 표현합니다.
- percentage − speech-rate 속성 값의 역수를 참조합니다. 예를 들어, speech-rate가 분당 120단어(즉, 단어 하나에 500ms가 걸림)인 경우, pause-before가 100%이면 500ms의 멈춤 시간을 의미하고 pause-before가 20%이면 100ms의 멈춤 시간을 의미합니다.

### pause 속성
pause 속성은 pause-before와 pause-after를 설정하는 축약형입니다. 두 값이 주어지면 첫 번째 값은 pause-before, 두 번째 값은 pause-after입니다.

다음은 예시입니다 −

```html
<style type = "text/css">
   <!--
      /* pause-before: 20ms; pause-after: 20ms */
      h1 { pause : 20ms }  
	
      /* pause-before: 30ms; pause-after: 40ms */
      h2{ pause : 30ms 40ms }  
	
      /* pause-before: ?; pause-after: 10ms */
      h3 { pause-after : 10ms }
   -->
</style>
```

### pitch 속성
pitch 속성은 말하는 목소리의 평균 피치(주파수)를 지정합니다. 목소리의 평균 피치는 음성 패밀리에 따라 다릅니다. 예를 들어, 표준 남성 목소리의 평균 피치는 약 120Hz이지만, 여성 목소리는 약 210Hz입니다. 가능한 값은 다음과 같습니다 −

- frequency − 말하는 목소리의 평균 피치를 헤르츠(Hz)로 지정합니다.
- x-low, low, medium, high, x-high − 이러한 값은 절대 주파수에 매핑되지 않으며, 음성 패밀리에 따라 다릅니다.

### pitch-range

 속성
pitch-range 속성은 평균 피치의 변화를 지정합니다. 가능한 값은 다음과 같습니다 −

- number − '0'에서 '100' 사이의 값. '0'의 피치 범위는 평평하고 단조로운 목소리를 생성합니다. 50의 피치 범위는 정상적인 억양을 생성합니다. 50 이상의 피치 범위는 애니메이션 목소리를 생성합니다.

### play-during 속성
play-during 속성은 요소의 내용이 말하는 동안 배경으로 재생할 소리를 지정합니다. 가능한 값은 다음과 같습니다 −

- URI − 이 `<uri>`에 지정된 소리가 요소의 내용이 말하는 동안 배경으로 재생됩니다.
- mix − 이 키워드가 있으면 부모 요소의 play-during 속성에서 상속된 소리가 계속 재생되고 지정된 uri의 소리가 혼합됩니다. mix가 지정되지 않으면 요소의 배경 소리가 부모의 소리를 대체합니다.
- repeat − 이 키워드가 있으면 소리가 너무 짧아서 요소의 전체 기간을 채우지 못할 경우 반복됩니다. 그렇지 않으면 소리가 한 번 재생되고 멈춥니다.
- auto − 부모 요소의 소리가 계속 재생됩니다.
- none − 이 키워드는 무음을 의미합니다.

다음은 예시입니다 −

```html
<style type = "text/css">
   <!--
      blockquote.sad { play-during: url("violins.aiff") }
      blockquote q   { play-during: url("harp.wav") mix }
      span.quiet     { play-during: none }
   -->
</style>
```

### richness 속성
richness 속성은 말하는 목소리의 풍부함 또는 밝기를 지정합니다. 가능한 값은 다음과 같습니다 −

- number − '0'에서 '100' 사이의 값. 값이 높을수록 목소리가 더 전달됩니다. 값이 낮을수록 부드럽고 감미로운 목소리가 생성됩니다.

### speak 속성
speak 속성은 텍스트를 음성으로 렌더링할지 여부와 그 방식

을 지정합니다. 가능한 값은 다음과 같습니다 −

- none − 청각 렌더링을 억제하여 요소가 렌더링하는 데 시간이 필요하지 않습니다.
- normal − 요소와 자식을 렌더링하는 데 언어 의존 발음 규칙을 사용합니다.
- spell-out − 텍스트를 한 글자씩 말합니다.

'volume' 속성이 'silent'인 요소와 'speak' 속성이 'none'인 요소의 차이를 주의하세요. 전자는 요소가 말하는 것처럼 동일한 시간을 차지하며, 요소 전후에 멈춤 시간을 포함하지만 소리가 생성되지 않습니다. 후자는 시간이 필요하지 않으며 렌더링되지 않습니다.

### speak-numeral 속성
speak-numeral 속성은 숫자가 어떻게 말할지를 제어합니다. 가능한 값은 다음과 같습니다 −

- digits − 숫자를 개별 숫자로 말합니다. 따라서 "237"은 "Two Three Seven"으로 말합니다.
- continuous − 숫자를 전체 숫자로 말합니다. 따라서 "237"은 "Two hundred thirty seven"으로 말합니다. 단어 표현은 언어에 따라 다릅니다.

### speak-punctuation 속성
speak-punctuation 속성은 구두점이 어떻게 말할지를 지정합니다. 가능한 값은 다음과 같습니다 −

- code − 세미콜론, 중괄호 등의 구두점을 문자 그대로 말합니다.
- none − 구두점을 말하지 않지만 다양한 멈춤 시간으로 자연스럽게 렌더링됩니다.

### speech-rate 속성
speech-rate 속성은 말하는 속도를 지정합니다. 절대 및 상대 키워드 값을 모두 사용할 수 있습니다. 가능한 값은 다음과 같습니다 −

- number − 분당 말하는 단어 수로 말하는 속도를 지정합니다.
- x-slow − 분당 80단어와 같습니다.
- slow − 분당 120단어와 같습니다.
- medium − 분당 180 - 200단어와 같습니다.
- fast − 분당 300단어와 같습니다.
- x-fast − 분당 500단어와 같습니다.
- faster − 현재 말하기 속도에 분당 40단어를 추가합니다.
- slower − 현재 말하기 속도에서 분당 40단어를 뺍니다.

### stress 속성
stress 속성은 목소리의 억양 곡선에서 "지역 피크"의 높이를 지정합니다. 영어는 강세 언어이며, 문장의 다른 부분은 기본, 부차, 또는 3차 강세로 지정됩니다. 가능한 값은 다음과 같습니다 −

- number − '0'에서 '100' 사이의 값. 값의 의미는 말하는 언어에 따라 다릅니다. 예를 들어, 표준 영어를 말하는 남성 목소리(평균 피치 = 122Hz)가 정상적인 억양과 강조로 말할 때 '50' 수준은 이탈리아어 목소리의 '50' 수준과 다른 의미를 가집니다.

### voice-family 속성
값은 콤마로 구분된 우선순위가 지정된 음성 패밀리 이름 목록입니다. 다음 값을 가질 수 있습니다 −

- generic-voice − 값은 음성 패밀리입니다. 가능한 값은 'male', 'female', 및 'child'입니다.
- specific-voice − 값은 특정 인스턴스(예: comedian, trinoids, carlos, lani)입니다.

다음은 예시입니다 −

```html
<style type = "text/css">
   <!--
      h1 { voice-family: announcer, male }
      p.part.romeo  { voice-family: romeo, male }
      p.part.juliet { voice-family: juliet, female }
   -->
</style>
```

### volume 속성
volume은 목소리의 중간 볼륨을 나타냅니다. 다음 값을 가질 수 있습니다 −

- numbers − '0'에서 '100' 사이의 숫자. '0'은 최소 가청 볼륨 수준을 나타내고 '100'은 최대 편안한 수준을 나타냅니다.
- percentage − 이러한 값은 상속된 값을 기준으로 계산되며 '0'에서 '100' 사이로 잘립니다.
- silent − 아무 소리도 나지 않습니다. '0' 값은 'silent'와 동일하지 않습니다.
- x-soft − '0'과 같습니다.
- soft − '25'와 같습니다.
- medium − '50'과 같습니다.
- loud − '75'와 같습니다.
- x-loud − '100'과 같습니다.

다음은 예시입니다 −

```html
<style type = "text/css">
   <!--
      P.goat  { volume: x-soft }
   -->
</style>
```

goat 클래스를 가진 단락은 매우 부드러운 소리가 날 것입니다.

---
## CSS Printing - @media Rule

```css
@media print {
   p.bodyText {font-family:georgia, times, serif;}
}
@media screen, print {
   p.bodyText {font-size:10pt}
}
```

스타일 시트를 별도의 파일에 정의하는 경우, 외부 스타일 시트에 링크할 때 media 속성을 사용할 수도 있습니다 −

```html
<link rel = "stylesheet" type = "text/css" media = "print" href = "mystyle.css">
```
---
## CSS - Layouts


CSS는 웹 문서의 미래에 중요한 역할을 하며 대부분의 브라우저에서 지원될 것입니다.

CSS는 테이블보다 더 정확하여, 브라우저 창과 관계없이 문서가 의도한 대로 보이도록 합니다.

중첩된 테이블을 관리하는 것은 매우 번거로울 수 있습니다. CSS 규칙은 잘 조직되어 읽기 쉽고 변경하기 쉽습니다.

마지막으로, 자신에게 적합한 기술을 사용하고 문서를 가장 잘 표현할 수 있는 것을 사용하기를 권장합니다.

CSS는 테이블을 더 빠르게 로드할 수 있도록 하는 table-layout 속성도 제공합니다. 다음은 예제입니다 −

```html
<table style = "table-layout:fixed;width:600px;">
   <tr height = "30">
      <td width = "150">CSS table layout cell 1</td>
      <td width = "200">CSS table layout cell 2</td>
      <td width = "250">CSS table layout cell 3</td>
   </tr>
</table>
```

큰 테이블에서 이점이 더 많이 나타납니다. 전통적인 HTML에서는 브라우저가 테이블을 렌더링하기 전에 모든 셀을 계산해야 했습니다. 그러나 table-layout 알고리즘을 fixed로 설정하면 첫 번째 행만 보면 전체 테이블을 렌더링할 수 있습니다. 이는 테이블이 고정된 열 너비와 행 높이를 가져야 함을 의미합니다.

### 샘플 열 레이아웃

다음은 CSS를 사용하여 간단한 열 레이아웃을 만드는 단계입니다 −

전체 문서의 여백과 패딩을 다음과 같이 설정합니다 −

```css
body {
   margin:9px 9px 0 9px;
   padding:0;
   background:#FFF;
}
```

이제 노란색 컬럼을 정의하고 이 규칙을 `<div>`에 적용합니다 −

```css
#level0 {
   background:#FC0;
}
```

이 시점까지는 노란색 바디를 가진 문서가 생성됩니다. 이제 level0 안에 또 다른 division을 정의합니다 −

```css
#level1 {
   margin-left:143px;
   padding-left:9px;
   background:#FFF;
}
```

이제 level1 안에 또 하나의 division을 중첩하고 배경색만 변경합니다 −

```css
#level2 {
   background:#FFF3AC;
}
```

마지막으로 동일한 기술을 사용하여 level2 안에 level3 division을 중첩하여 오른쪽 컬럼의 시각적 레이아웃을 얻습니다 −

```css
#level3 {
   margin-right:143px;
   padding-right:9px;
   background:#FFF;
}
#main {
   background:#CCC;
}
```

다음과 같이 소스 코드를 완성합니다 −

```html
<style style = "text/css">
   body {
      margin:9px 9px 0 9px;
      padding:0;
      background:#FFF;
   }
   
   #level0 {background:#FC0;}
   
   #level1 {
      margin-left:143px;
      padding-left:9px;
      background:#FFF;
   }
   
   #level2 {background:#FFF3AC;}
   
   #level3 {
      margin-right:143px;
      padding-right:9px;
      background:#FFF;
   }
   
   #main {background:#CCC;}
</style>
<body>
   <div id = "level0">
      <div id = "level1">
         <div id = "level2">
            <div id = "level3">
               <div id = "main">
                  Final Content goes here...
               </div>
            </div>
         </div>
      </div>
   </div>
</body>
```

마찬가지로 페이지 상단에 탐색 바 또는 광고 바를 추가할 수 있습니다.

이것은 다음과 같은 결과를 생성할 것입니다 −

---
## CSS - Validations

W3C CSS Validator (World Wide Web Consortium)는 파일 업로드, 직접 입력 또는 URI를 사용하여 한 번에 하나의 페이지씩 CSS를 검사합니다. 이 유효성 검사기는 CSS의 모든 오류를 찾는 데 도움이 됩니다.

WDG - CSS 유효성 검사기

WDG CSS 검사기는 직접 입력, 파일 업로드 및 URI를 사용하여 CSS를 유효성 검사할 수 있습니다. 오류가 있으면 오류는 줄 및 열 번호로 나열됩니다. 오류에는 일반적으로 오류 원인을 설명하는 링크가 포함되어 있습니다.

CSS 유효성 검사기는 CSS가 W3 컨소시엄에서 설정한 CSS 표준을 준수하는지 확인합니다. 일부 유효성 검사기는 CSS 기능이 어떤 브라우저에서 지원되는지도 알려줍니다(모든 브라우저가 동일한 CSS 구현을 가지는 것은 아니기 때문입니다).

### HTML 코드를 유효성 검사해야 하는 이유

코드를 유효성 검사해야 하는 여러 이유가 있습니다. 그러나 주요 이유는 다음과 같습니다 −

- 크로스 브라우저, 크로스 플랫폼 및 향후 호환성을 도와줍니다.

- 품질이 좋은 웹사이트는 검색 엔진 가시성을 높입니다.

- 전문성: 웹 개발자로서 방문자가 코드를 볼 때 오류가 발생하지 않도록 해야 합니다.

---
## CSS3 - Tutorial

CSS3는 CSS2 사양과 새로운 사양의 협력체로, 이를 모듈이라고 부를 수 있습니다. 일부 모듈은 다음과 같습니다 −

- 선택자(Selectors)
- 박스 모델(Box Model)
- 배경(Backgrounds)
- 이미지 값 및 대체 콘텐츠(Image Values and Replaced Content)
- 텍스트 효과(Text Effects)
- 2D 변형(2D Transformations)
- 3D 변형(3D Transformations)
- 애니메이션(Animations)
- 다중 열 레이아웃(Multiple Column Layout)
- 사용자 인터페이스(User Interface)

---
## CSS3 - Rounded Corners

다음 표는 둥근 모서리에 대한 가능한 값들을 보여줍니다 −

| 번호 | 값 및 설명 |
|------|------------|
| 1    | border-radius 이 요소는 네 개의 보더 반지름 속성을 설정하는 데 사용됩니다. |
| 2    | border-top-left-radius 이 요소는 좌측 상단 모서리의 보더를 설정하는 데 사용됩니다. |
| 3    | border-top-right-radius 이 요소는 우측 상단 모서리의 보더를 설정하는 데 사용됩니다. |
| 4    | border-bottom-right-radius  이 요소는 우측 하단 모서리의 보더를 설정하는 데 사용됩니다. |
| 5    | border-bottom-left-radius  이 요소는 좌측 하단 모서리의 보더를 설정하는 데 사용됩니다. |

예시
이 속성은 세 가지 값을 가질 수 있습니다. 다음 예제는 세 가지 값을 모두 사용합니다 −

```html
<html>
   <head>
      <style>
         #rcorners1 {
            border-radius: 25px;
            background: #8AC007;
            padding: 20px;
            width: 200px;
            height: 150px;
         }
         #rcorners2 {
            border-radius: 25px;
            border: 2px solid #8AC007;
            padding: 20px; 
            width: 200px;
            height: 150px;
         }
         #rcorners3 {
            border-radius: 25px;
            background: url(/css/images/logo.png);
            background-position: left top;
            background-repeat: repeat;
            padding: 20px; 
            width: 200px;
            height: 150px;
         }
      </style>
   </head>

   <body>
      <p id = "rcorners1">Rounded corners!</p>
      <p id = "rcorners2">Rounded corners!</p>
      <p id = "rcorners3">Rounded corners!</p>
   </body>
</html>
```
각 모서리 속성
각 모서리 속성을 아래 예제와 같이 지정할 수 있습니다 −

```html
<html>
   <head>
      <style>
         #rcorners1 {
            border-radius: 15px 50px 30px 5px;
            background: #a44170;
            padding: 20px; 
            width: 100px;
            height: 100px; 
         }
         #rcorners2 {
            border-radius: 15px 50px 30px;
            background: #a44170;
            padding: 20px;
            width: 100px;
            height: 100px; 
         }
         #rcorners3 {
            border-radius: 15px 50px;
            background: #a44170;
            padding: 20px; 
            width: 100px;
            height: 100px; 
         }
      </style>
   </head>

   <body>
      <p id = "rcorners1"></p>
      <p id = "rcorners2"></p>
      <p id = "rcorners3"></p>
   </body>
<body>
```
위 코드는 다음과 같은 결과를 생성합니다 −

---
## CSS3 - Border Image

| 번호 | 값 및 설명 |
|------|------------|
| 1    | border-image-source |
| 이미지 경로를 설정하는 데 사용됩니다. |
| 2    | border-image-slice |
| 보더 이미지를 분할하는 데 사용됩니다. |
| 3    | border-image-width |
| 보더 이미지의 너비를 설정하는 데 사용됩니다. |
| 4    | border-image-repeat |
| 보더 이미지를 둥글게, 반복하거나 늘려서 설정하는 데 사용됩니다. |

### 예제
다음은 요소에 이미지를 보더로 설정하는 예제입니다.

```html
<html>
   <head>
      <style>
         #borderimg1 { 
            border: 10px solid transparent;
            padding: 15px;
            border-image-source: url(/css/images/border.png);
            border-image-repeat: round;
            border-image-slice: 30;
            border-image-width: 10px;
         }
         #borderimg2 { 
            border: 10px solid transparent;
            padding: 15px;
            border-image-source: url(/css/images/border.png);
            border-image-repeat: round;
            border-image-slice: 30;
            border-image-width: 20px;
         }
         #borderimg3 { 
            border: 10px solid transparent;
            padding: 15px;
            border-image-source: url(/css/images/border.png);
            border-image-repeat: round;
            border-image-slice: 30;
            border-image-width: 30px;
         }
      </style>
   </head>

   <body>
      <p id = "borderimg1">This is image border example.</p>
      <p id = "borderimg2">This is image border example.</p>
      <p id = "borderimg3">This is image border example.</p>
   </body>
</html>
```
위 코드는 다음과 같은 결과를 생성합니다 −

---
## CSS3 - Multi Background

가장 자주 사용되는 값은 아래와 같습니다 −

| 번호 | 값 및 설명 |
|------|------------|
| 1    | background 모든 배경 이미지 속성을 한 섹션에서 설정하는 데 사용됩니다. |
| 2    | background-clip 배경의 페인팅 영역을 선언하는 데 사용됩니다. |
| 3    | background-image 배경 이미지를 지정하는 데 사용됩니다. |
| 4    | background-origin 배경 이미지의 위치를 지정하는 데 사용됩니다. |
| 5    | background-size 배경 이미지의 크기를 지정하는 데 사용됩니다. |

### 예제
다음은 여러 배경 이미지를 설정하는 예제입니다.

```html
<html>
   <head>
      <style>
         #multibackground {
            background-image: url(/css/images/logo.png), url(/css/images/border.png);
            background-position: left top, left top;
            background-repeat: no-repeat, repeat;
            padding: 75px;
         }
      </style>
   </head>

   <body>
   
      <div id = "multibackground">
         <h1>www.tutorialspoint.com</h1>
         <p>
            Tutorials Point originated from the idea that there exists a class of 
            readers who respond better to online content and prefer to learn new 
            skills at their own pace from the comforts of their drawing rooms. 
            The journey commenced with a single tutorial on HTML in  2006 and elated 
            by the response it generated, we worked our way to adding fresh tutorials 
            to our repository which now proudly flaunts a wealth of tutorials and 
            allied articles on topics ranging from programming languages to web designing 
            to academics and much more..
         </p>
      </div>
      
   </body>
</html>
```
위 코드는 다음과 같은 결과를 생성합니다 −

### 다중 배경 크기
다중 배경 속성은 다른 이미지에 대해 다른 크기를 추가할 수 있습니다. 다음은 예제 구문입니다 −

```css
#multibackground {
   background: url(/css/images/logo.png) left top no-repeat, url(/css/images/border.png) right bottom no-repeat, url(/css/images/css.gif) left top repeat;
   background-size: 50px, 130px, auto;
}
```
위 예제에서 각 이미지는 50px, 130px 및 auto 크기로 지정되었습니다.

---
## CSS3 - Colors


```css
#d1 {background-color: rgba(255, 0, 0, 0.5);} 
#d2 {background-color: rgba(0, 255, 0, 0.5);}  
#d3 {background-color: rgba(0, 0, 255, 0.5);}
```

HSL은 색조, 채도, 명도를 의미합니다. 색조는 색상환의 각도이며, 채도와 명도는 0에서 100% 사이의 백분율 값입니다. HSL의 샘플 구문은 다음과 같습니다 −

```css
#g1 {background-color: hsl(120, 100%, 50%);}  
#g2 {background-color: hsl(120, 100%, 75%);}  
#g3 {background-color: hsl(120, 100%, 25%);}
```

HSLA는 색조, 채도, 명도 및 알파를 의미합니다. 알파 값은 RGBA처럼 불투명도를 지정합니다. HSLA의 샘플 구문은 다음과 같습니다 −

```css
#g1 {background-color: hsla(120, 100%, 50%, 0.3);}  
#g2 {background-color: hsla(120, 100%, 75%, 0.3);}  
#g3 {background-color: hsla(120, 100%, 25%, 0.3);}  
```

불투명도(opacity)는 페인트를 얇게 만들기 위해 검은색을 추가해야 하는 경우를 의미합니다. 불투명도의 샘플 구문은 다음과 같습니다 −

```css
#g1 {background-color: rgb(255,0,0); opacity: 0.6;}  
#g2 {background-color: rgb(0,255,0); opacity: 0.6;}  
#g3 {background-color: rgb(0,0,255); opacity: 0.6;} 
```

다음 예제는 RGBA 색상 속성을 보여줍니다.

```html
<html>
   <head>
      <style>
         #p1 {background-color:rgba(255,0,0,0.3);}
         #p2 {background-color:rgba(0,255,0,0.3);}
         #p3 {background-color:rgba(0,0,255,0.3);}
      </style>
   </head>

   <body>
      <p>RGBA colors:</p>
      <p id = "p1">Red</p>
      <p id = "p2">Green</p>
      <p id = "p3">Blue</p>
   </body>
</html>
```
위 코드는 다음과 같은 결과를 생성합니다 −

다음 예제는 HSL 색상 속성을 보여줍니다.

```html
<html>
   <head>
      <style>
         #g1 {background-color:hsl(120, 100%, 50%);}
         #g2 {background-color:hsl(120,100%,75%);}
         #g3 {background-color:hsl(120,100%,25%);}
      </style>
   </head>

   <body>
      <p>HSL colors:</p>
      <p id = "g1">Green</p>
      <p id = "g2">Normal Green</p>
      <p id = "g3">Dark Green</p>
   </body>
</html>
```
위 코드는 다음과 같은 결과를 생성합니다 −

다음 예제는 HSLA 색상 속성을 보여줍니다.

```html
<html>
   <head>
      <style>
         #d1 {background-color:hsla(120,100%,50%,0.3);}
         #d2 {background-color:hsla(120,100%,75%,0.3);}
         #d3 {background-color:hsla(120,100%,25%,0.3);}
      </style>
   </head>

   <body>
      <p>HSLA colors:</p>
      <p id = "d1">Less opacity green</p>
      <p id = "d2">Green</p>
      <p id = "d3">Green</p>
   </body>
</html>
```
위 코드는 다음과 같은 결과를 생성합니다 −

다음 예제는 불투명도(opacity) 속성을 보여줍니다.

```html
<html>
   <head>
      <style>
         #m1 {background-color:rgb(255,0,0);opacity:0.6;} 
         #m2 {background-color:rgb(0,255,0);opacity:0.6;} 
         #m3 {background-color:rgb(0,0,255);opacity:0.6;}
      </style>
   </head>

   <body>
      <p>Opacity colors:</p>
      <p id = "m1">Red</p>
      <p id = "m2">Green</p>
      <p id = "m3">Blue</p>
   </body>
</html>
```
위 코드는 다음과 같은 결과를 생성합니다 −

---
## CSS3 - Gradients

### Linear gradients

선형 그라디언트는 두 가지 이상의 색상을 위에서 아래로 배치하는 데 사용됩니다.

**위에서 아래로**

```html
<html>
   <head>
      <style>
         #grad1 {
            height: 100px;
            background: -webkit-linear-gradient(pink, green);
            background: -o-linear-gradient(pink, green);
            background: -moz-linear-gradient(pink, green); 
            background: linear-gradient(pink, green); 
         }
      </style>
   </head>

   <body>
      <div id = "grad1"></div>
   </body>
</html>
```

**왼쪽에서 오른쪽으로**

```html
<html>
   <head>
      <style>
         #grad1 {
            height: 100px;
            background: -webkit-linear-gradient(left, red, blue);
            background: -o-linear-gradient(right, red, blue); 
            background: -moz-linear-gradient(right, red, blue);
            background: linear-gradient(to right, red, blue);
         }
      </style>
   </head>

   <body>
      <div id = "grad1"></div>
   </body>
</html>
```

**대각선**

대각선 그라디언트는 왼쪽 상단에서 오른쪽 하단으로 시작합니다.

```html
<html>
   <head>
      <style>
         #grad1 {
            height: 100px;
            background: -webkit-linear-gradient(left top, red, blue); 
            background: -o-linear-gradient(bottom right, red, blue); 
            background: -moz-linear-gradient(bottom right, red, blue);
            background: linear-gradient(to bottom right, red, blue); 
         }
      </style>
   </head>

   <body>
      <div id = "grad1"></div>
   </body>
</html>
```

**다중 색상**

```html
<html>
   <head>
      <style>
         #grad2 {
            height: 100px;
            background: -webkit-linear-gradient(red, orange, yellow, red, blue, green, pink); 
            background: -o-linear-gradient(red, orange, yellow, red, blue, green, pink); 
            background: -moz-linear-gradient(red, orange, yellow, red, blue, green, pink); 
            background: linear-gradient(red, orange, yellow, red, blue, green, pink); 
         }
      </style>
   </head>

   <body>
      <div id = "grad2"></div>
   </body>
</html>
```

### CSS3 Radial Gradients

방사형 그라디언트는 중앙에 나타납니다.

```html
<html>
   <head>
      <style>
         #grad1 {
            height: 100px;
            width: 550px;
            background: -webkit-radial-gradient(red 5%, green 15%, pink 60%); 
            background: -o-radial-gradient(red 5%, green 15%, pink 60%); 
            background: -moz-radial-gradient(red 5%, green 15%, pink 60%); 
            background: radial-gradient(red 5%, green 15%, pink 60%); 
         }
      </style>
   </head>

   <body>
      <div id = "grad1"></div>
   </body>
</html>
```

### CSS3 Repeat Radial Gradients

```html
<html>
   <head>
      <style>
         #grad1 {
            height: 100px;
            width: 550px;
            background: -webkit-repeating-radial-gradient(blue, yellow 10%, green 15%); 
            background: -o-repeating-radial-gradient(blue, yellow 10%, green 15%);
            background: -moz-repeating-radial-gradient(blue, yellow 10%, green 15%);
            background: repeating-radial-gradient(blue, yellow 10%, green 15%); 
         }
      </style>
   </head>

   <body>
      <div id = "grad1"></div>
   </body>
</html>
```
---
## CSS3 - Shadow

```html
<html>
   <head>
      <style>
         h1 {
            text-shadow: 2px 2px;
         }
         h2 {
            text-shadow: 2px 2px red;
         }
         h3 {
            text-shadow: 2px 2px 5px red;
         }
         h4 {
            color: white;
            text-shadow: 2px 2px 4px #000000;
         }
         h5 {
            text-shadow: 0 0 3px #FF0000;
         }
         h6 {
            text-shadow: 0 0 3px #FF0000, 0 0 5px #0000FF;
         }
         p {
            color: white;
            text-shadow: 1px 1px 2px black, 0 0 25px blue, 0 0 5px darkblue;
         }
      </style>
   </head>

   <body>
      <h1>Tutorialspoint.com</h1>
      <h2>Tutorialspoint.com</h2>
      <h3>Tutorialspoint.com</h3>
      <h4>Tutorialspoint.com</h4>
      <h5>Tutorialspoint.com</h5>
      <h6>Tutorialspoint.com</h6>
      <p>Tutorialspoint.com</p>
   </body>
</html>
```

## box shadow

요소에 그림자 효과를 추가하는 데 사용됩니다. 다음은 요소에 그림자 효과를 추가하는 예제입니다.

```html
<html>
   <head>
      <style>
         div {
            width: 300px;
            height: 100px;
            padding: 15px;
            background-color: red;
            box-shadow: 10px 10px;
         }
      </style>
   </head>

   <body>
      <div>This is a div element with a box-shadow</div>
   </body>
</html>
```

---
## CSS3 - Text

Sr.No. Value & Description

1. **text-align-last**  
   Used to align the last line of the text

2. **text-emphasis**  
   Used to emphasize text and color

3. **text-overflow**  
   Used to determine how overflowed content that is not displayed is signaled to users

4. **word-break**  
   Used to break the line based on word

5. **word-wrap**  
   Used to break the line and wrap onto the next line

### Text-overflow

The text-overflow property determines how overflowed content that is not displayed is signaled to users. The sample example of text overflow is shown as follows −

```html
<html>
   <head>
      <style>
         p.text1 {
            white-space: nowrap; 
            width: 500px; 
            border: 1px solid #000000;
            overflow: hidden;
            text-overflow: clip;
         }
         p.text2 {
            white-space: nowrap; 
            width: 500px; 
            border: 1px solid #000000;
            overflow: hidden;
            text-overflow: ellipsis;
         }
      </style>
   </head>

   <body>
   
      <b>Original Text:</b>
   
      <p>
         Tutorials Point originated from the idea that there exists a class of 
         readers who respond better to online content and prefer to learn new 
         skills at their own pace from the comforts of their drawing rooms.
      </p>
      
      <b>Text overflow: clip:</b>
   
      <p class = "text1">
         Tutorials Point originated from the idea that there exists
         a class of readers who respond better to online content and prefer 
         to learn new skills at their own pace from the comforts of their 
         drawing rooms.
      </p>
      
      <b>Text overflow: ellipsis:</b>
   
      <p class = "text2">
         Tutorials Point originated from the idea that there exists
         a class of readers who respond better to online content and 
         prefer to learn new skills at their own pace from the comforts 
         of their drawing rooms.
      </p>
      
   </body>
</html>
```

### CSS3 Word Breaking

Used to break the line, following code shows the sample code of word breaking.

```html
<html>
   <head>
      <style>
         p.text1 {
            width: 140px; 
            border: 1px solid #000000;
            word-break: keep-all;
         }
         p.text2 {
            width: 140px; 
            border: 1px solid #000000;
            word-break: break-all;
         }
      </style>
   </head>

   <body>
   
      <b>line break at hyphens:</b>
      <p class = "text1">
         Tutorials Point originated from the idea that there exists a 
         class of readers who respond better to online content and prefer 
         to learn new skills at their own pace from the comforts of 
         their drawing rooms.
      </p>
      
      <b>line break at any character:</b>
   
      <p class = "text2">
         Tutorials Point originated from the idea that there exists a 
         class of readers who respond better to online content and 
         prefer to learn new skills at their own pace from the comforts 
         of their drawing rooms.
      </p>
      
   </body>
</html>
```

### CSS Word Wrapping

Word wrapping is used to break the line and wrap onto the next line. The following code will have a sample syntax −

```css
p {
   word-wrap: break-word;
}
```
---
## CSS3 - Web Fonts

### TrueType Fonts (TTF)

TrueType는 1980년대 후반 애플과 마이크로소프트가 개발한 윤곽선 글꼴 표준으로, 윈도우와 MAC 운영 체제에서 가장 일반적인 글꼴이 되었습니다.

### OpenType Fonts (OTF)

OpenType은 마이크로소프트가 개발한 확장 가능한 컴퓨터 글꼴 형식입니다.

### The Web Open Font Format (WOFF)

WOFF는 2009년에 개발된 웹 페이지용 글꼴 형식으로, 현재 W3C 권고 사항에 의해 사용되고 있습니다.

### SVG Fonts/Shapes

SVG는 SVG 문서 내에서 SVG 글꼴을 허용합니다. 또한 font-face 속성을 사용하여 CSS를 SVG에 적용할 수 있습니다.

### Embedded OpenType Fonts (EOT)

EOT는 웹 페이지 개발에 사용되며, 웹 페이지에 포함되어 있어 타사 글꼴을 허용할 필요가 없습니다.

다음 코드는 font-face의 예제 코드입니다 −

```html
<html>
   <head>
      <style>
         @font-face {
            font-family: myFirstFont;
            src: url(/css/font/SansationLight.woff);
         }
         div {
            font-family: myFirstFont;
         }
      </Style>
   </head>
   
   <body>
      <div>This is the example of font face with CSS3.</div>
      <p><b>Original Text :</b>This is the example of font face with CSS3.</p>
   </body>
</html>
```

### Fonts Description

다음 목록은 @font-face 규칙에 포함된 모든 글꼴 설명을 포함합니다 −

Sr.No. Value & Description

1. **font-family**  
   글꼴의 이름을 정의하는 데 사용됩니다.

2. **src**  
   URL을 정의하는 데 사용됩니다.

3. **font-stretch**  
   글꼴이 어떻게 확장되어야 하는지 찾는 데 사용됩니다.

4. **font-style**  
   글꼴 스타일을 정의하는 데 사용됩니다.

5. **font-weight**  
   글꼴의 굵기(굵기)를 정의하는 데 사용됩니다.

---
## CSS3 - 2d Transforms

1. **matrix(n,n,n,n,n,n)**
   - 여섯 개의 값으로 행렬 변형을 정의하는 데 사용됩니다.

2. **translate(x,y)**
   - 요소를 x축과 y축을 따라 변형하는 데 사용됩니다.

3. **translateX(n)**
   - 요소를 x축을 따라 변형하는 데 사용됩니다.

4. **translateY(n)**
   - 요소를 y축을 따라 변형하는 데 사용됩니다.

5. **scale(x,y)**
   - 요소의 너비와 높이를 변경하는 데 사용됩니다.

6. **scaleX(n)**
   - 요소의 너비를 변경하는 데 사용됩니다.

7. **scaleY(n)**
   - 요소의 높이를 변경하는 데 사용됩니다.

8. **rotate(angle)**
   - 요소를 각도에 따라 회전시키는 데 사용됩니다.

9. **skewX(angle)**
   - x축을 따라 기울임 변형을 정의하는 데 사용됩니다.

10. **skewY(angle)**
    - y축을 따라 기울임 변형을 정의하는 데 사용됩니다.

다음 예제는 위의 모든 속성의 샘플을 보여줍니다.

### 20도 회전

20도 각도로 상자를 회전시키는 예제입니다.

```html
<html>
   <head>
      <style>
         div {
            width: 300px;
            height: 100px;
            background-color: pink;
            border: 1px solid black;
         }
         div#myDiv {
            /* IE 9 */
            -ms-transform: rotate(20deg);
            
            /* Safari */
            -webkit-transform: rotate(20deg);
            
            /* Standard syntax */
            transform: rotate(20deg);
         }
      </style>
   </head>

   <body>
      <div>
         Tutorials point.com.
      </div>
      
      <div id = "myDiv">
         Tutorials point.com
      </div>
   </body>
</html>
```

### -20도 회전

-20도 각도로 상자를 회전시키는 예제입니다.

```html
<html>
   <head>
      <style>
         div {
            width: 300px;
            height: 100px;
            background-color: pink;
            border: 1px solid black;
         }
         div#myDiv {
            /* IE 9 */
            -ms-transform: rotate(-20deg); 
         
            /* Safari */
            -webkit-transform: rotate(-20deg);
         
            /* Standard syntax */   
            transform: rotate(-20deg);
         }
      </style>
   </head>

   <body>
      <div>
         Tutorials point.com.
      </div>
      
      <div id = "myDiv">
         Tutorials point.com
      </div>
   </body>
</html>
```

### X축 기울임

x축을 따라 상자를 기울이는 예제입니다.

```html
<html>
   <head>
      <style>
         div {
            width: 300px;
            height: 100px;
            background-color: pink;
            border: 1px solid black;
         }
         div#skewDiv {
            /* IE 9 */
            -ms-transform: skewX(20deg); 
            
            /* Safari */
            -webkit-transform: skewX(20deg);
            
            /* Standard syntax */   
            transform: skewX(20deg);
         }
      </style>
   </head>

   <body>
      <div>
         Tutorials point.com.
      </div>
      
      <div id = "skewDiv">
         Tutorials point.com
      </div>
   </body>
</html>
```

### Y축 기울임

y축을 따라 상자를 기울이는 예제입니다.

```html
<html>
   <head>
      <style>
         div {
            width: 300px;
            height: 100px;
            background-color: pink;
            border: 1px solid black;
         }
         div#skewDiv {
            /* IE 9 */
            -ms-transform: skewY(20deg); 
            
            /* Safari */
            -webkit-transform: skewY(20deg); 
            
            /* Standard syntax */   
            transform: skewY(20deg);
         }
      </style>
   </head>

   <body>
      <div>
         Tutorials point.com.
      </div>
      
      <div id = "skewDiv">
         Tutorials point.com
      </div>
   </body>
</html>
```

### 행렬 변형

행렬 변형을 사용하여 상자를 변형하는 예제입니다.

```html
<html>
   <head>
      <style>
         div {
            width: 300px;
            height: 100px;
            background-color: pink;
            border: 1px solid black;
         }
         div#myDiv1 {
            /* IE 9 */
            -ms-transform: matrix(1, -0.3, 0, 1, 0, 0);
            
            /* Safari */
            -webkit-transform: matrix(1, -0.3, 0, 1, 0, 0); 
            
            /* Standard syntax */
            transform: matrix(1, -0.3, 0, 1, 0, 0); 
         }
      </style>
   </head>

   <body>
      <div>
         Tutorials point.com.
      </div>
      
      <div id = "myDiv1">
         Tutorials point.com
      </div>
   </body>
</html>
```

다른 방향으로 행렬 변형을 사용한 예제입니다.

```html
<html>
   <head>
      <style>
         div {
            width: 300px;
            height: 100px;
            background-color: pink;
            border: 1px solid black;
         }
         div#myDiv2 {
            /* IE 9 */
            -ms-transform: matrix(1, 0, 0.5, 1, 150, 0);
            
            /* Safari */ 
            -webkit-transform: matrix(1, 0, 0.5, 1, 150, 0);
            
            /* Standard syntax */
            transform: matrix(1, 0, 0.5, 1, 150, 0); 
         }
      </style>
   </head>

   <body>
      <div>
         Tutorials point.com.
      </div>
      
      <div id = "myDiv2">
         Tutorials point.com
      </div>
   </body>
</html>
```

---
## CSS3 - 3D Transforms


1. **matrix3d(n,n,n,n,n,n,n,n,n,n,n,n,n,n,n,n)**
   - 16개의 행렬 값을 사용하여 요소를 변형하는 데 사용됩니다.

2. **translate3d(x,y,z)**
   - x축, y축, z축을 사용하여 요소를 변형하는 데 사용됩니다.

3. **translateX(x)**
   - x축을 사용하여 요소를 변형하는 데 사용됩니다.

4. **translateY(y)**
   - y축을 사용하여 요소를 변형하는 데 사용됩니다.

5. **translateZ(z)**
   - z축을 사용하여 요소를 변형하는 데 사용됩니다.

6. **scaleX(x)**
   - x축을 사용하여 요소를 확대/축소하는 데 사용됩니다.

7. **scaleY(y)**
   - y축을 사용하여 요소를 확대/축소하는 데 사용됩니다.

8. **scaleZ(z)**
   - z축을 사용하여 요소를 확대/축소하는 데 사용됩니다.

9. **rotateX(angle)**
   - x축을 사용하여 요소를 회전하는 데 사용됩니다.

10. **rotateY(angle)**
    - y축을 사용하여 요소를 회전하는 데 사용됩니다.

11. **rotateZ(angle)**
    - z축을 사용하여 요소를 회전하는 데 사용됩니다.

### X축 3D 변형

다음 예제는 x축 3D 변형을 보여줍니다.

```html
<html>
   <head>
      <style>
         div {
            width: 200px;
            height: 100px;
            background-color: pink;
            border: 1px solid black;
         }
         div#myDiv {
            -webkit-transform: rotateX(150deg); 
            transform: rotateX(150deg); 
         }
      </style>
   </head>

   <body>
      <div>
         tutorials point.com
      </div>
      
      <p>Rotate X-axis</p>
      
      <div id="myDiv">
         tutorials point.com.
      </div>
   </body>
</html>
```

### Y축 3D 변형

다음 예제는 y축 3D 변형을 보여줍니다.

```html
<html>
   <head>
      <style>
         div {
            width: 200px;
            height: 100px;
            background-color: pink;
            border: 1px solid black;
         }
         div#yDiv {
            -webkit-transform: rotateY(150deg); 
            transform: rotateY(150deg); 
         }
      </style>
   </head>

   <body>
      <div>
         tutorials point.com
      </div>
      
      <p>Rotate Y axis</p>
      
      <div id="yDiv">
         tutorials point.com.
      </div>
   </body>
</html>
```

### Z축 3D 변형

다음 예제는 z축 3D 변형을 보여줍니다.

```html
<html>
   <head>
      <style>
         div {
            width: 200px;
            height: 100px;
            background-color: pink;
            border: 1px solid black;
         }
         div#zDiv {
            -webkit-transform: rotateZ(90deg); 
            transform: rotateZ(90deg); 
         }
      </style>
   </head>

   <body>
      <div>
         tutorials point.com
      </div>
      
      <p>rotate Z axis</p>
      
      <div id="zDiv">
         tutorials point.com.
      </div>
   </body>
</html>
```
---
## CSS3 - Animation


```css
div {
    width: 100px;
    height: 100px;
    background-color: red;
    animation-name: animation;
    animation-duration: 5s;
}
```

위 예제는 키프레임 구문을 사용한 애니메이션의 높이, 너비, 색상, 이름 및 지속 시간을 보여줍니다.

### 왼쪽으로 움직이는 애니메이션

```html
<html>
   <head>
      <style type="text/css">
         h1 {
            -moz-animation-duration: 3s;
            -webkit-animation-duration: 3s;
            -moz-animation-name: slidein;
            -webkit-animation-name: slidein;
         }
         @-moz-keyframes slidein {
            from {
               margin-left: 100%;
               width: 300%;
            }
            to {
               margin-left: 0%;
               width: 100%;
            }
         }
         @-webkit-keyframes slidein {
            from {
               margin-left: 100%;
               width: 300%;
            }
            to {
               margin-left: 0%;
               width: 100%;
            }
         }
      </style>
   </head>

   <body>
      <h1>Tutorials Point</h1>
      <p>이것은 왼쪽으로 움직이는 애니메이션 예제입니다.</p>
      <button onclick="myFunction()">페이지 새로고침</button>
      <script>
         function myFunction() {
            location.reload();
         }
      </script>
   </body>
</html>
```

### 키프레임을 사용한 왼쪽으로 움직이는 애니메이션

```html
<html>
   <head>
      <style type="text/css">
         h1 {
            -moz-animation-duration: 3s;
            -webkit-animation-duration: 3s;
            -moz-animation-name: slidein;
            -webkit-animation-name: slidein;
         }
         @-moz-keyframes slidein {
            from {
               margin-left: 100%;
               width: 300%;
            }
            75% {
               font-size: 300%;
               margin-left: 25%;
               width: 150%;
            }
            to {
               margin-left: 0%;
               width: 100%;
            }
         }
         @-webkit-keyframes slidein {
            from {
               margin-left: 100%;
               width: 300%;
            }
            75% {
               font-size: 300%;
               margin-left: 25%;
               width: 150%;
            }
            to {
               margin-left: 0%;
               width: 100%;
            }
         }
      </style>
   </head>

   <body>
      <h1>Tutorials Point</h1>
      <p>이것은 텍스트 변화를 위한 추가 키프레임을 포함한 왼쪽으로 애니메이션의 예입니다.</p>
      <button onclick="myFunction()">페이지 새로고침</button>
      <script>
         function myFunction() {
            location.reload();
         }
      </script>
   </body>
</html>
```
---
## CSS3 - Multi Columns


1. **column-count**

   Used to count the number of columns that element should be divided.

2. **column-fill**

   Used to decide, how to fill the columns.

3. **column-gap**

   Used to decide the gap between the columns.

4. **column-rule**

   Used to specifies the number of rules.

5. **rule-color**

   Used to specifies the column rule color.

6. **rule-style**

   Used to specifies the style rule for column.

7. **rule-width**

   Used to specifies the width.

8. **column-span**

   Used to specifies the span between columns.

### Example

Below example shows the arrangement of text as new paper structure.

```html
<html>
   <head>
      <style>
         .multi {
            /* Column count property */
            -webkit-column-count: 4;
            -moz-column-count: 4;
            column-count: 4;
            
            /* Column gap property */
            -webkit-column-gap: 40px; 
            -moz-column-gap: 40px; 
            column-gap: 40px;
            
            /* Column style property */
            -webkit-column-rule-style: solid; 
            -moz-column-rule-style: solid; 
            column-rule-style: solid;
         }
      </style>
   </head>

   <body>
   
      <div class="multi">
         Tutorials Point originated from the idea that there exists a class 
         of readers who respond better to online content and prefer to learn 
         new skills at their own pace from the comforts of their drawing rooms.
         The journey commenced with a single tutorial on HTML in 2006 and elated 
         by the response it generated, we worked our way to adding fresh tutorials
         to our repository which now proudly flaunts a wealth of tutorials and 
         allied articles on topics ranging from programming languages to web 
         designing to academics and much more.
      </div>
      
   </body>
</html>
```

For suppose, if user wants to make text as new paper without line, we can do this by removing style syntax as shown below −

```css
.multi {
   /* Column count property */
   -webkit-column-count: 4;
   -moz-column-count: 4;
   column-count: 4;
   
   /* Column gap property */
   -webkit-column-gap: 40px; 
   -moz-column-gap: 40px; 
   column-gap: 40px;
}
```
---
## CSS3 - User Interface

1. **appearance**

   요소를 사용자 인터페이스 요소로 만들 수 있도록 허용합니다.

2. **box-sizing**

   요소를 명확한 방식으로 영역에 고정할 수 있도록 합니다.

3. **icon**

   영역에 아이콘을 제공합니다.

4. **resize**

   영역에 있는 요소의 크기를 조정할 수 있도록 합니다.

5. **outline-offset**

   윤곽선을 그리는 뒤에 그려집니다.

6. **nav-down**

   키패드의 아래쪽 화살표 버튼을 눌렀을 때 아래로 이동합니다.

7. **nav-left**

   키패드의 왼쪽 화살표 버튼을 눌렀을 때 왼쪽으로 이동합니다.

8. **nav-right**

   키패드의 오른쪽 화살표 버튼을 눌렀을 때 오른쪽으로 이동합니다.

9. **nav-up**

   키패드의 위쪽 화살표 버튼을 눌렀을 때 위로 이동합니다.

### resize 속성의 예제

resize 속성은 세 가지 일반적인 값을 가집니다:

- horizontal
- vertical
- both

CSS3 사용자 인터페이스에서 both 값을 사용하는 예제:

```html
<html>
   <head>
      <style>
         div {
            border: 2px solid;
            padding: 20px; 
            width: 300px;
            resize: both;
            overflow: auto;
         }
      </style>
   </head>

   <body>
      <div>TutorialsPoint.com</div>
   </body>
</html>
```

### CSS3 Outline offset

outline은 요소의 외부 테두리에 선을 그리는 것을 의미합니다.

```html
<html>
   <head>
      <style>
         div {
            margin: 20px;
            padding: 10px;
            width: 300px; 
            height: 100px;
            border: 5px solid pink;
            outline: 5px solid green;
            outline-offset: 15px;
         }
      </style>
   </head>

   <body>
      <div>TutorialsPoint</div>
   </body>
</html>
```
---
## CSS3 - Box Sizing

```html
<html>
   <head>
      <style>
         .div1 {
            width: 200px;
            height: 100px;
            border: 1px solid green;
         }
         .div2 {
            width: 200px;
            height: 100px;    
            padding: 50px;
            border: 1px solid pink;
         }
      </style>
   </head>

   <body>
      <div class = "div1">TutorialsPoint.com</div><br />
      <div class = "div2">TutorialsPoint.com</div>
   </body>
</html>
```

위의 이미지는 두 요소가 동일한 너비와 높이를 가지지만, 두 번째 요소는 `padding` 속성을 포함하여 결과가 다르게 보입니다.

### CSS3 박스 사이징 속성

```html
<html>
   <head>
      <style>
         .div1 {
            width: 300px;
            height: 100px;
            border: 1px solid blue;
            box-sizing: border-box;
         }
         .div2 {
            width: 300px;
            height: 100px;
            padding: 50px;
            border: 1px solid red;
            box-sizing: border-box;
         }
      </style>
   </head>

   <body>
      <div class = "div1">TutorialsPoint.com</div><br />
      <div class = "div2">TutorialsPoint.com</div>
   </body>
</html>
```

위의 예제는 `box-sizing: border-box`를 사용하여 동일한 높이와 너비를 갖습니다. 따라서 두 요소 모두 동일한 결과를 보여줍니다.

---
## CSS - Responsive


```html
<html>
   <head>
      <style>
         body {
            font: 600 14px/24px "Open Sans", 
               "HelveticaNeue-Light", 
               "Helvetica Neue Light", 
               "Helvetica Neue", 
               Helvetica, Arial, 
               "Lucida Grande", 
               Sans-Serif;
         }
         h1 {
            color: #9799a7;
            font-size: 14px;
            font-weight: bold;
            margin-bottom: 6px;
         }
         .container:before, .container:after {
            content: "";
            display: table;
         }
         .container:after {
            clear: both;
         }
         .container {
            background: #eaeaed;
            margin-bottom: 24px;
            *zoom: 1;
         }
         .container-75 {
            width: 75%;
         }
         .container-50 {
            margin-bottom: 0;
            width: 50%;
         }
         .container, section, aside {
            border-radius: 6px;
         }
         section, aside {
            background: #2db34a;
            color: #fff;
            margin: 1.858736059%;
            padding: 20px 0;
            text-align: center;
         }
         section {
            float: left;
            width: 63.197026%;
         }
         aside {
            float: right;
            width: 29.3680297%;
         }
      </style>
   </head>
   
   <body>
   
      <h1>100% 너비 컨테이너</h1>
      
      <div class = "container">
         <section>섹션</section>
         <aside>사이드</aside>
      </div>
      
      <h1>75% 너비 컨테이너</h1>
      
      <div class = "container container-75">
         <section>섹션</section>
         <aside>사이드</aside>
      </div>
      
      <h1>50% 너비 컨테이너</h1>
      
      <div class = "container container-50">
         <section>섹션</section>
         <aside>사이드</aside>
      </div>
      
   </body>
</html>
```

위의 코드는 다음과 같은 결과를 생성합니다.

### 미디어 쿼리
미디어 쿼리는 모바일, 데스크탑 등 다양한 크기의 디바이스에 따라 스타일 규칙을 다르게 적용하는 데 사용됩니다.

```html
<html>
   <head>
      <style>
         body {
            background-color: lightpink;
         }
         @media screen and (max-width: 420px) {
            body {
               background-color: lightblue;
            }
         }
      </style>
   </head>

   <body>
      <p>
         화면 크기가 420px보다 작으면 배경색이 연한 파란색으로 바뀌고, 그렇지 않으면 연한 분홍색이 됩니다.
      </p>
   </body>
</html>
```

위의 코드는 다음과 같은 결과를 생성합니다.

### 부트스트랩 반응형 웹 디자인
부트스트랩은 HTML, CSS, JavaScript 기반의 가장 인기 있는 웹 디자인 프레임워크로, 모든 디바이스에 반응형 웹 페이지를 디자인하는 데 도움을 줍니다.

```html
<html>
   <head>
      <meta charset = "utf-8">
      <meta name = "viewport" content = "width=device-width, initial-scale = 1">
      <link rel = "stylesheet" 
         href = "http://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
      <style>
         body {
            color:green;
         }
      </style>
   </head>

   <body>
   
      <div class = "container">
      
         <div class = "jumbotron">
            <h1>Tutorials point</h1> 
            <p>
               Tutorials Point는 독자가 온라인 콘텐츠에 더 잘 반응하고 자신의 거실에서 편안하게 새로운 기술을 배우는 것을 선호한다는 아이디어에서 시작되었습니다.
            </p> 
         </div>
      
         <div class = "row">
            <div class = "col-md-4">
               <h2>Android</h2>
               <p>
                  안드로이드는 스마트폰 및 태블릿 컴퓨터와 같은 모바일 디바이스를 위한 오픈 소스 및 리눅스 기반 운영 체제입니다. 안드로이드는 Google과 다른 회사가 주도하는 Open Handset Alliance에 의해 개발되었습니다.
               </p>
            </div>
         
            <div class = "col-md-4">
               <h2>CSS</h2>
               <p>
                  CSS(Cascading Style Sheets)는 웹 페이지를 보다 보기 좋게 만드는 과정을 단순화하기 위해 설계된 간단한 디자인 언어입니다.
               </p>
            </div>
      
            <div class = "col-md-4">
               <h2>Java</h2>
               <p>
                  Java는 원래 Sun Microsystems에서 개발하여 1995년에 출시된 고수준 프로그래밍 언어입니다. Java는 Windows, Mac OS, 다양한 UNIX 버전 등 다양한 플랫폼에서 실행됩니다. 이 튜토리얼은 Java에 대한 완전한 이해를 제공합니다.
               </p>
            </div>
         </div>
      
   </body>
</html>
```

위의 코드는 다음과 같은 결과를 생성합니다.

---
## 출처
 - [Tutorialspoint CSS - Quick Guide](https://www.tutorialspoint.com/css/css_quick_guide.htm)
---
## [다음](./06_JS_기초.md)
