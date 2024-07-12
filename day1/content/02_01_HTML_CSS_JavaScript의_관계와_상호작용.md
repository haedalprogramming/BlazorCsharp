# HTML, CSS, JavaScript의 관계와 상호작용

## 목차
- [HTML, CSS, JavaScript의 관계와 상호작용](#html-css-javascript의-관계와-상호작용)
  - [목차](#목차)
  - [소개](#소개)
  - [HTML (HyperText Markup Language)](#html-hypertext-markup-language)
    - [HTML의 역할](#html의-역할)
    - [기본 예제](#기본-예제)
  - [CSS (Cascading Style Sheets)](#css-cascading-style-sheets)
    - [CSS의 역할](#css의-역할)
    - [기본 예제](#기본-예제-1)
    - [HTML과 CSS의 결합](#html과-css의-결합)
  - [JavaScript](#javascript)
    - [JavaScript의 역할](#javascript의-역할)
    - [기본 예제](#기본-예제-2)
    - [HTML과 JavaScript의 결합](#html과-javascript의-결합)
  - [HTML, CSS, JavaScript의 상호작용](#html-css-javascript의-상호작용)
    - [관계 및 역할 분담](#관계-및-역할-분담)
    - [상호작용 예제](#상호작용-예제)
    - [동작 설명](#동작-설명)
  - [결론](#결론)
  - [추가 학습 자료](#추가-학습-자료)
  - [다음](#다음)

## 소개
웹 페이지는 HTML, CSS, JavaScript라는 세 가지 주요 기술로 구성됩니다. 이 문서에서는 각각의 역할과 이들이 어떻게 상호작용하는지에 대해 설명합니다.

## HTML (HyperText Markup Language)

### HTML의 역할
- **구조 정의**: HTML은 웹 페이지의 구조와 내용을 정의합니다.
- **태그 사용**: 제목, 단락, 링크, 이미지 등 다양한 요소를 태그로 표시합니다.

### 기본 예제
```html
<!DOCTYPE html>
<html>
<head>
    <title>My First Web Page</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>This is my first web page.</p>
</body>
</html>
```

## CSS (Cascading Style Sheets)

### CSS의 역할
- **스타일 적용**: CSS는 HTML 요소의 스타일(색상, 폰트, 레이아웃 등)을 정의합니다.
- **레이아웃 제어**: 페이지의 레이아웃을 조정하고 반응형 디자인을 만듭니다.

### 기본 예제
```css
body {
    font-family: Arial, sans-serif;
}

h1 {
    color: blue;
}

p {
    color: green;
}
```

### HTML과 CSS의 결합
```html
<!DOCTYPE html>
<html>
<head>
    <title>Styled Web Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        h1 {
            color: blue;
        }
        p {
            color: green;
        }
    </style>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>This is my first styled web page.</p>
</body>
</html>
```

## JavaScript

### JavaScript의 역할
- **동적 기능 추가**: JavaScript는 웹 페이지에 동적인 기능(예: 사용자 상호작용, 데이터 변경)을 추가합니다.
- **행동 제어**: 이벤트(클릭, 입력 등)에 반응하여 행동을 정의합니다.

### 기본 예제
```javascript
document.addEventListener('DOMContentLoaded', (event) => {
    document.getElementById('myButton').addEventListener('click', () => {
        alert('Button was clicked!');
    });
});
```

### HTML과 JavaScript의 결합
```html
<!DOCTYPE html>
<html>
<head>
    <title>Interactive Web Page</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>This is my first interactive web page.</p>
    <button id="myButton">Click Me!</button>
    <script>
        document.addEventListener('DOMContentLoaded', (event) => {
            document.getElementById('myButton').addEventListener('click', () => {
                alert('Button was clicked!');
            });
        });
    </script>
</body>
</html>
```

## HTML, CSS, JavaScript의 상호작용

### 관계 및 역할 분담
- **HTML**: 구조와 콘텐츠를 정의합니다.
- **CSS**: 스타일과 레이아웃을 적용합니다.
- **JavaScript**: 동적 기능과 상호작용을 추가합니다.

### 상호작용 예제
```html
<!DOCTYPE html>
<html>
<head>
    <title>Dynamic Styled Web Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        h1 {
            color: blue;
        }
        p {
            color: green;
        }
        .highlight {
            background-color: yellow;
        }
    </style>
</head>
<body>
    <h1>Hello, World!</h1>
    <p id="myParagraph">Click the button to highlight this paragraph.</p>
    <button id="myButton">Highlight</button>
    <script>
        document.addEventListener('DOMContentLoaded', (event) => {
            document.getElementById('myButton').addEventListener('click', () => {
                document.getElementById('myParagraph').classList.toggle('highlight');
            });
        });
    </script>
</body>
</html>
```

### 동작 설명
1. **HTML**: 기본 구조와 콘텐츠를 정의합니다.
2. **CSS**: 기본 스타일과 `highlight` 클래스를 정의합니다.
3. **JavaScript**: 버튼 클릭 시 `highlight` 클래스를 토글하여 문단의 배경색을 변경합니다.

## 결론
HTML, CSS, JavaScript는 각각의 역할을 통해 웹 페이지를 구성합니다. HTML은 구조를, CSS는 스타일을, JavaScript는 동적 기능을 담당하며, 이들 간의 조화로운 상호작용이 현대적인 웹 페이지를 만듭니다.

## 추가 학습 자료
- [MDN Web Docs](https://developer.mozilla.org/)
- [W3Schools](https://www.w3schools.com/)

---
## [다음](./02_02_Forntend_framework.md)