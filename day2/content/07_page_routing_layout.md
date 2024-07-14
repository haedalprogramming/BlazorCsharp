# Pages, routing, and layouts

## 목차
- [Pages, routing, and layouts](#pages-routing-and-layouts)
  - [목차](#목차)
  - [페이지 생성](#페이지-생성)
  - [Router 컴포넌트](#router-컴포넌트)
  - [탐색](#탐색)
  - [기본 URL](#기본-url)
  - [페이지 레이아웃](#페이지-레이아웃)
  - [출처](#출처)
  - [다음](#다음)

---

Blazor는 .NET 개발 환경에서 최신 웹 애플리케이션을 개발할 수 있는 강력한 프레임워크입니다. 각 페이지는 일반적으로 *.razor* 파일에 정의된 컴포넌트로 구성되며, 하나 이상의 지정된 라우트를 가집니다. 라우팅은 주로 클라이언트 측에서 발생하며, 특정 서버 요청을 수반하지 않습니다. 브라우저는 먼저 앱의 루트 주소에 요청을 보냅니다. Blazor 앱의 루트 `Router` 컴포넌트가 탐색 요청을 가로채고 올바른 컴포넌트로 전달합니다.

Blazor는 또한 *딥 링크*를 지원합니다. 딥 링크는 브라우저가 앱의 루트가 아닌 특정 경로에 요청을 보낼 때 발생합니다. 서버로 전송된 딥 링크 요청은 Blazor 앱으로 라우팅되며, 이후 해당 요청을 클라이언트 측에서 올바른 컴포넌트로 라우팅합니다.

다음은 Blazor에서 간단한 페이지를 구성하는 예입니다:

*Name.razor*

```razor
@page "/Name"
@layout MainLayout

<div>
    What is your name?<br />
    <input @bind="text" />
    <button @onclick="OnClick">Submit</button>
</div>
<div>
    @if (name != null)
    {
        @:Hello @name
    }
</div>

@code {
    string text;
    string name;

    void OnClick() {
        name = text;
    }
}
```

## 페이지 생성

Blazor에서 페이지를 생성하려면 컴포넌트를 생성하고 `@page` Razor 지시어를 추가하여 컴포넌트의 경로를 지정합니다. `@page` 지시어는 해당 컴포넌트에 추가할 경로 템플릿을 매개변수로 받습니다.

```razor
@page "/counter"
```

경로 템플릿 매개변수는 필수입니다. Blazor 컴포넌트의 경로는 파일 위치에서 추론되지 않습니다(이 기능은 나중에 추가될 수 있습니다).

경로 템플릿 구문은 ASP.NET Web Forms의 라우팅에서 사용되는 기본 구문과 동일합니다. 경로 매개변수는 중괄호를 사용하여 템플릿에 지정됩니다. Blazor는 경로 값을 동일한 이름(대소문자 구분 안 함)의 컴포넌트 매개변수에 바인딩합니다.

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

또한 경로 매개변수 값에 대한 제약 조건을 지정할 수도 있습니다. 예를 들어, 제품 ID를 `int`로 제한하려면 다음과 같이 합니다:

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

Blazor에서 지원하는 경로 제약 조건의 전체 목록은 Route constraints를 참조하세요.

## Router 컴포넌트

Blazor에서 라우팅은 `Router` 컴포넌트에 의해 처리됩니다. `Router` 컴포넌트는 일반적으로 앱의 루트 컴포넌트(*App.razor*)에서 사용됩니다.

```razor
<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <LayoutView Layout="@typeof(MainLayout)">
            <p>Sorry, there's nothing at this address.</p>
        </LayoutView>
    </NotFound>
</Router>
```

`Router` 컴포넌트는 지정된 `AppAssembly`와 선택적으로 지정된 `AdditionalAssemblies`에서 라우팅 가능한 컴포넌트를 검색합니다. 브라우저가 탐색하면 `Router`는 탐색을 가로채고 주소와 일치하는 경로가 있는 경우 추출된 `RouteData`와 함께 `Found` 매개변수의 내용을 렌더링하며, 그렇지 않으면 `NotFound` 매개변수를 렌더링합니다.

`RouteView` 컴포넌트는 `RouteData`에 의해 지정된 일치하는 컴포넌트를 해당 레이아웃과 함께 렌더링합니다. 일치하는 컴포넌트에 레이아웃이 없는 경우 선택적으로 지정된 `DefaultLayout`이 사용됩니다.

`LayoutView` 컴포넌트는 지정된 레이아웃 내에서 자식 콘텐츠를 렌더링합니다. 레이아웃에 대한 자세한 내용은 이 장의 뒷부분에서 다룰 것입니다.

## 탐색

Blazor는 `NavigationManager` 서비스를 제공하여 다음을 수행할 수 있습니다:

- 현재 브라우저 주소 가져오기
- 기본 주소 가져오기
- 탐색 트리거
- 주소 변경 시 알림 받기

다른 주소로 탐색하려면 `NavigateTo` 메서드를 사용합니다:

```razor
@page "/"
@inject NavigationManager NavigationManager

<button @onclick="Navigate">Navigate</button>

@code {
    void Navigate() {
        NavigationManager.NavigateTo("counter");
    }
}
```

`NavigationManager`의 모든 멤버에 대한 설명은 URI 및 탐색 상태 도우미를 참조하세요.

## 기본 URL

Blazor 앱이 기본 경로 아래에 배포된 경우 라우팅이 올바르게 작동하려면 페이지 메타데이터에 `<base>` 태그를 사용하여 기본 URL을 지정해야 합니다. 앱의 호스트 페이지가 Razor를 사용하여 서버 렌더링되는 경우 `~/` 구문을 사용하여 앱의 기본 주소를 지정할 수 있습니다. 호스트 페이지가 정적 HTML인 경우 기본 URL을 명시적으로 지정해야 합니다.

```html
<base href="~/" />
```

## 페이지 레이아웃

Blazor에서는 레이아웃 컴포넌트를 사용하여 페이지 레이아웃을 처리합니다. 레이아웃 컴포넌트는 `LayoutComponentBase`를 상속하며, 단일 `Body` 속성(타입: `RenderFragment`)을 정의하여 페이지의 내용을 렌더링하는 데 사용합니다.

*MainLayout.razor*

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

레이아웃이 지정된 페이지가 렌더링될 때, 페이지는 레이아웃이 `Body` 속성을 렌더링하는 위치에 있는 지정된 레이아웃의 내용 내에서 렌더링됩니다.

페이지에 레이아웃을 적용하려면 `@layout` 지시어를 사용합니다:

```razor
@layout MainLayout
```

폴더 및 하위 폴더의 모든 컴포넌트에 대해 레이아웃을 지정하려면 *_Imports.razor* 파일을 사용할 수 있습니다. 또한 Router 컴포넌트를 사용하여 모든 페이지의 기본 레이아웃을 지정할 수 있습니다.

Blazor의 레이아웃 컴포넌트는 중첩될 수 있습니다. 레이아웃 컴포넌트를 레이아웃 컴포넌트에 적용할 수 있습니다. 내부 레이아웃의 내용은 외부 레이아웃 내에서 렌더링됩니다.

*ChildLayout.razor*

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

*Index.razor*

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

페이지의 렌더링된 출력은 다음과 같습니다:

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

Blazor의 레이아웃은 일반적으로 페이지의 루트 HTML 요소(`<html>`, `<body>`, `<head>` 등)를 정의하지 않습니다. 루트 HTML 요소는 대신 Blazor 앱의 호스트 페이지에 정의되며, 이는 앱의 초기 HTML 콘텐츠를 렌더링하는 데 사용됩니다(자세한 내용은 Bootstrap Blazor 참조). 호스트 페이지는 주변 마크업과 함께 앱의 여러 루트 컴포넌트를 렌더링할 수 있습니다.

Blazor의 컴포넌트, 페이지를 포함하여 `<script>` 태그를 렌더링할 수 없습니다. 이 렌더링 제한은 `<script>` 태그가 한 번 로드된 후 변경될 수 없기 때문에 존재합니다. Razor 구문을 사용하여 태그를 동적으로 렌더링하려고 하면 예기치 않은 동작이 발생할 수 있습니다. 대신 모든 `<script>` 태그는 앱의 호스트 페이지에 추가해야 합니다.

---
## 출처
[Pages, routing, and layouts](https://learn.microsoft.com/en-us/dotnet/architecture/blazor-for-web-forms-developers/pages-routing-layouts)

---
## [다음](./08_state.md)