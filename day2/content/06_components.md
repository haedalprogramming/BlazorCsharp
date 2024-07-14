# Build reusable UI components with Blazor

## 목차
- [Build reusable UI components with Blazor](#build-reusable-ui-components-with-blazor)
  - [목차](#목차)
  - [Blazor 소개](#blazor-소개)
  - [Razor 소개](#razor-소개)
  - [컴포넌트 사용](#컴포넌트-사용)
  - [컴포넌트에서 페이지 제목 수정](#컴포넌트에서-페이지-제목-수정)
  - [컴포넌트 매개변수](#컴포넌트-매개변수)
    - [쿼리 문자열 매개변수](#쿼리-문자열-매개변수)
  - [컴포넌트와 오류 경계](#컴포넌트와-오류-경계)
  - [이벤트 핸들러](#이벤트-핸들러)
  - [데이터 바인딩](#데이터-바인딩)
  - [상태 변경](#상태-변경)
  - [컴포넌트 라이프사이클](#컴포넌트-라이프사이클)
    - [OnInitialized](#oninitialized)
    - [OnParametersSet](#onparametersset)
    - [OnAfterRender](#onafterrender)
    - [IDisposable](#idisposable)
  - [컴포넌트 참조 캡처](#컴포넌트-참조-캡처)
  - [요소 참조 캡처](#요소-참조-캡처)
  - [템플릿화된 컴포넌트](#템플릿화된-컴포넌트)
    - [자식 콘텐츠](#자식-콘텐츠)
    - [템플릿 매개변수](#템플릿-매개변수)
  - [코드 비하인드](#코드-비하인드)
  - [출처](#출처)
  - [다음](#다음)

---

## Blazor 소개

Blazor는 웹 애플리케이션의 사용자 인터페이스(UI)를 만드는 데 사용되는 프레임워크로, 컴포넌트를 통해 UI 캡슐화를 지원합니다. 컴포넌트는:

- 자가 포함된 UI 조각입니다.
- 자체 상태와 렌더링 로직을 유지합니다.
- UI 이벤트 핸들러를 정의하고 입력 데이터를 바인딩하며 자체 라이프사이클을 관리할 수 있습니다.
- 일반적으로 Razor 구문을 사용하는 *.razor* 파일로 정의됩니다.

## Razor 소개

Razor는 HTML과 C#을 기반으로 하는 경량 마크업 템플릿 언어입니다. Razor를 사용하면 마크업과 C# 코드 간에 원활하게 전환하여 컴포넌트 렌더링 로직을 정의할 수 있습니다. *.razor* 파일이 컴파일될 때, 렌더링 로직은 .NET 클래스에 구조화된 방식으로 캡처됩니다. 컴파일된 클래스의 이름은 *.razor* 파일 이름에서 가져옵니다. 네임스페이스는 프로젝트의 기본 네임스페이스와 폴더 경로에서 가져오거나 `@namespace` 지시어를 사용하여 명시적으로 지정할 수 있습니다.

컴포넌트의 렌더링 로직은 일반 HTML 마크업을 사용하여 작성되며, 동적 로직은 C#을 사용하여 추가됩니다. `@` 문자는 C#으로 전환하는 데 사용됩니다. Razor는 일반적으로 HTML로 돌아갈 때를 자동으로 인식합니다. 예를 들어, 다음 컴포넌트는 현재 시간을 포함하는 `<p>` 태그를 렌더링합니다:

```razor
<p>@DateTime.Now</p>
```

C# 표현식의 시작과 끝을 명시적으로 지정하려면 괄호를 사용합니다:

```razor
<p>@(DateTime.Now)</p>
```

Razor는 렌더링 로직에서 C# 제어 흐름을 사용하는 것도 쉽게 만듭니다. 예를 들어, 조건부로 일부 HTML을 렌더링할 수 있습니다:

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

또는 일반 C# `foreach` 루프를 사용하여 항목 목록을 생성할 수 있습니다:

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

Razor 지시어는 컴포넌트가 컴파일되는 방식을 제어합니다. 예에는 컴포넌트의 네임스페이스, 기본 클래스, 구현된 인터페이스, 제네릭 매개변수, 가져온 네임스페이스, 라우트 등이 포함됩니다.

Razor 지시어는 `@` 문자로 시작하며, 일반적으로 파일의 시작 부분에 새로운 줄로 사용됩니다. 예를 들어, `@namespace` 지시어는 컴포넌트의 네임스페이스를 정의합니다:

```razor
@namespace MyComponentNamespace
```

다음 표는 Blazor에서 사용되는 다양한 Razor 지시어와 해당하는 ASP.NET Web Forms의 지시어를 요약한 것입니다.

|지시어|설명|예제|
|------|----|---|
|`@attribute`|클래스 수준 속성을 컴포넌트에 추가|`@attribute [Authorize]`|
|`@code`|클래스 멤버를 컴포넌트에 추가|`@code { ... }`|
|`@implements`|지정된 인터페이스를 구현|`@implements IDisposable`|
|`@inherits`|지정된 기본 클래스로부터 상속|`@inherits MyComponentBase`|
|`@inject`|서비스를 컴포넌트에 주입|`@inject IJSRuntime JS`|
|`@layout`|컴포넌트에 대한 레이아웃 컴포넌트를 지정|`@layout MainLayout`|
|`@namespace`|컴포넌트의 네임스페이스를 설정|`@namespace MyNamespace`|
|`@page`|컴포넌트의 라우트를 지정|`@page "/product/{id}"`|
|`@typeparam`|컴포넌트에 제네릭 타입 매개변수를 지정|`@typeparam TItem`|
|`@using`|가져올 네임스페이스를 지정|`@using MyComponentNamespace`|

Razor 컴포넌트는 컴파일되는 다양한 측면을 제어하기 위해 요소에 지시어 속성을 광범위하게 사용합니다(이벤트 핸들링, 데이터 바인딩, 컴포넌트 및 요소 참조 등). 지시어 속성은 모두 공통의 일반 구문을 따르며, 괄호 안의 값은 선택 사항입니다:

```razor
@directive(-suffix(:name))(="value")
```

다음 표는 Blazor에서 사용되는 다양한 Razor 지시어 속성을 요약한 것입니다.

|속성|설명|예제|
|---|---|---|
|`@attributes`|속성 사전을 렌더링|`<input @attributes="ExtraAttributes" />`|
|`@bind`|양방향 데이터 바인딩 생성|`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}`|지정된 이벤트에 대한 이벤트 핸들러 추가|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`|컬렉션의 요소를 보존하기 위한 diffing 알고리즘에 사용할 키 지정|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`|컴포넌트 또는 HTML 요소에 대한 참조 캡처|`<MyDialog @ref="myDialog" />`|

Blazor에서 사용되는 다양한 지시어 속성(`@onclick`, `@bind`, `@ref` 등)은 아래 섹션과 이후 장에서 다룹니다.

## 컴포넌트 사용

일반 HTML 외에도 컴포넌트는 렌더링 로직의 일부로 다른 컴포넌트를 사용할 수 있습니다. Razor에서 컴포넌트를 사용하는 구문은 매우 직관적입니다. 컴포넌트는 컴포넌트의 타입 이름과 일치하는 요소 태그를 사용하여 지정됩니다. 예를 들어, `Counter` 컴포넌트를 다음과 같이 추가할 수 있습니다:

```razor
<Counter />
```

Blazor의 컴포넌트는 요소 접두어를 사용하지 않으며, 페이지나 *web.config*에 등록할 필요가 없습니다. Razor 컴포넌트를 .NET 타입처럼 생각해보세요. 컴포넌트를 포함하는 어셈블리가 참조되면 컴포넌트는 사용 가능합니다. 컴포넌트의 네임스페이스를 스코프로 가져오려면 `@using` 지시어를 적용합니다:

```razor
@using MyComponentLib

<Counter />
```

기본 Blazor 프로젝트에서 볼 수 있듯이, `@using` 지시어를 *_Imports.razor* 파일에 넣어 동일한 디렉터리와 하위 디렉터리의 모든 *.razor* 파일에 가져오는 것이 일반적입니다.

컴포넌트의 네임스페이스가 스코프에 없으면 C#에서처럼 전체 타입 이름을 사용하여 컴포넌트를 지정할 수 있습니다:

```razor
<MyComponentLib.Counter />
```

## 컴포넌트에서 페이지 제목 수정

SPA 스타일 앱을 빌드할 때, 페이지의 일부가 전체 페이지를 다시 로드하지 않고 다시 로드되는 경우가 많습니다. 그렇다 하더라도 현재 로드된 컴포넌트에 따라 페이지 제목이 변경되는 것이 유용할 수 있습니다. 이를 위해 컴포넌트의 Razor 페이지에 `<PageTitle>` 태그를 포함할 수 있습니다:

```razor
@page "/"
<PageTitle>Home</PageTitle>
```

이 요소의 내용은 동적일 수 있으며, 예를 들어 현재 메시지 수를 표시할 수 있습니다:

```razor
<PageTitle>@MessageCount messages</PageTitle>
```

특정 페이지에 여러 컴포넌트가 `<PageTitle>` 태그를 포함하고 있으면 마지막 태그만 표시됩니다(각 태그가 이전 태그를 덮어쓰기 때문입니다).

## 컴포넌트 매개변수

Blazor의 컴포넌트는 컴포넌트 속성을 사용하여 매개변수와 데이터를 전달받을 수 있습니다. 이러한 속성은 마크업에서 속성을 사용하여 설정할 수 있으며, 코드에서 직접 설정할 수도 있습니다. 컴포넌트 속성은 컴포넌트 매개변수로 간주되려면 `[Parameter]` 속성으로 표시되어야 합니다.

다음 `Counter` 컴포넌트는 버튼을 클릭할 때마다 `Counter`가 증가해야 하는 양을 지정할 수 있는 `IncrementAmount`라는 컴포넌트 매개변수를 정의합니다.

```razor
<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    void IncrementCount()
    {
        currentCount += IncrementAmount;
    }
}
```

Blazor에서 컴포넌트 매개변수를 지정하려면 속성을 사용합니다:

```razor
<Counter IncrementAmount="10" />
```

### 쿼리 문자열 매개변수

Razor 컴포넌트는 렌더링되는 페이지의 쿼리 문자열 값을 매개변수 소스로 활용할 수도 있습니다. 이를 활성화하려면 `[SupplyParameterFromQuery]` 속성을 매개변수에 추가합니다. 예를 들어, 다음 매개변수 정의는 `?IncBy=2` 형식의 요청에서 값을 가져옵니다:

```csharp
[Parameter]
[SupplyParameterFromQuery(Name = "IncBy")]
public int IncrementAmount { get; set; } = 1;
```

`[SupplyParameterFromQuery]` 속성에 사용자 지정 `Name`을 제공하지 않으면 기본적으로 속성 이름(`IncrementAmount`와 같은)과 일치합니다.

## 컴포넌트와 오류 경계

기본적으로 Blazor 앱은 처리되지 않은 예외를 감지하고 페이지 하단에 추가 세부 정보 없이 오류 메시지를 표시합니다. 예를 들어 단일 컴포넌트로 영향을 제한하려는 경우처럼 앱의 영향을 받는 부분을 제한하려면 `<ErrorBoundary>` 태그를 컴포넌트 선언 주위에 감쌀 수 있습니다.

예를 들어, `Counter` 컴포넌트에서 발생할 수 있는 예외를 방지하려면 `<ErrorBoundary>` 내에 선언하고 예외가 발생하면 표시할 메시지를 선택적으로 지정합니다:

```razor
<ErrorBoundary>
    <ChildContent>
        <Counter />
    </ChildContent>
    <ErrorContent>
        Oops! The counter isn't working right now; please try again later.
    </ErrorContent>
</ErrorBoundary>
```

사용자 지정 오류 내용을 지정할 필요가 없다면 컴포넌트를 직접 감싸기만 하면 됩니다:

```razor
<ErrorBoundary>
  <Counter />
</ErrorBoundary>
```

처리되지 않은 예외가 발생하면 "An error has occurred."라는 기본 메시지가 표시됩니다.

## 이벤트 핸들러

Blazor는 UI 이벤트를 처리하기 위한 이벤트 기반 프로그래밍 모델을 제공합니다. 이러한 이벤트의 예로는 버튼 클릭과 텍스트 입력이 있습니다. Blazor에서는 `@on{event}` 형식의 지시어 속성을 사용하여 DOM UI 이벤트에 대한 핸들러를 직접 등록할 수 있습니다. `{event}` 자리 표시자는 이벤트 이름을 나타냅니다. 예를 들어, 버튼 클릭을 감지하려면 다음과 같이 합니다:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

이벤트 핸들러는 선택적인 이벤트별 인수를 받아 이벤트에 대한 추가 정보를 제공할 수 있습니다. 예를 들어, 마우스 이벤트는 `MouseEventArgs` 인수를 받을 수 있지만 필수는 아닙니다.

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

이벤트 핸들러에 대한 메서드 그룹을 참조하는 대신 람다 표현식을 사용할 수 있습니다. 람다 표현식은 다른 스코프 내 값을 포함할 수 있게 합니다.

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

이벤트 핸들러는 동기적으로 또는 비동기적으로 실행될 수 있습니다. 예를 들어, 다음 `OnClick` 이벤트 핸들러는 비동기적으로 실행됩니다:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

이벤트가 처리된 후 컴포넌트는 컴포넌트 상태 변경 사항을 반영하기 위해 렌더링됩니다. 비동기 이벤트 핸들러의 경우, 비동기 `Task`가 완료된 후 컴포넌트가 다시 렌더링됩니다. 이 비동기 실행 모드는 비동기 `Task`가 여전히 진행 중일 때 적절한 UI를 렌더링할 기회를 제공합니다.

```razor
<button @onclick="ShowMessage">Get message</button>

@if (showMessage)
{
    @if (message == null)
    {
        <p><em>Loading...</em></p>
    }
    else
    {
        <p>The message is: @message</p>
    }
}

@code
{
    bool showMessage = false;
    string message;

    public async Task ShowMessage()
    {
        showMessage = true;
        message = await MessageService.GetMessageAsync();
    }
}
```

컴포넌트는 또한 `EventCallback<TValue>` 타입의 컴포넌트 매개변수를 정의하여 자체 이벤트를 정의할 수 있습니다. 이벤트 콜백은 DOM UI 이벤트 핸들러의 모든 변형을 지원합니다: 선택적 인수, 동기 또는 비동기, 메서드 그룹 또는 람다 표현식.

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## 데이터 바인딩

Blazor는 UI 컴포넌트에서 컴포넌트의 상태로 데이터를 바인딩하는 간단한 메커니즘을 제공합니다. 이 접근 방식은 ASP.NET Web Forms에서 데이터 소스에서 UI 컨트롤로 데이터를 바인딩하는 기능과 다릅니다. 다양한 데이터 소스에서 데이터를 처리하는 방법에 대해서는 데이터 처리 섹션에서 다룹니다.

UI 컴포넌트에서 컴포넌트의 상태로 양방향 데이터 바인딩을 생성하려면 `@bind` 지시어 속성을 사용합니다. 다음 예제에서 체크박스의 값은 `isChecked` 필드에 바인딩됩니다.

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

컴포넌트가 렌더링될 때, 체크박스의 값은 `isChecked` 필드의 값으로 설정됩니다. 사용자가 체크박스를 토글하면 `onchange` 이벤트가 발생하고 `isChecked` 필드는 새 값으로 설정됩니다. 이 경우 `@bind` 구문은 다음 마크업과 동일합니다:

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

바인딩에 사용되는 이벤트를 변경하려면 `@bind:event` 속성을 사용합니다.

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

컴포넌트는 매개변수에 데이터 바인딩을 지원할 수도 있습니다. 데이터 바인딩을 생성하려면, 바인딩 가능한 매개변수와 동일한 이름의 이벤트 콜백 매개변수를 정의합니다. 이름에 "Changed" 접미사가 추가됩니다.

*PasswordBox.razor*

```razor
Password: <input
    value="@Password"
    @oninput="OnPasswordChanged"
    type="@(showPassword ? "text" : "password")" />

<label><input type="checkbox" @bind="showPassword" />Show password</label>

@code {
    private bool showPassword;

    [Parameter]
    public string Password { get; set; }

    [Parameter]
    public EventCallback<string> PasswordChanged { get; set; }

    private Task OnPasswordChanged(ChangeEventArgs e)
    {
        Password = e.Value.ToString();
        return PasswordChanged.InvokeAsync(Password);
    }
}
```

기본 UI 요소에 데이터 바인딩을 체인하려면 `@bind` 속성을 사용하지 않고 값과 이벤트를 직접 UI 요소에 설정합니다.

컴포넌트 매개변수에 바인딩하려면 `@bind-{Parameter}` 속성을 사용하여 바인딩하려는 매개변수를 지정합니다.

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## 상태 변경

컴포넌트의 상태가 정상적인 UI 이벤트나 이벤트 콜백 외부에서 변경된 경우, 컴포넌트는 다시 렌더링되어야 함을 수동으로 신호해야 합니다. 컴포넌트의 상태가 변경되었음을 신호하려면 `StateHasChanged` 메서드를 호출합니다.

아래 예제에서 컴포넌트는 `AppState` 서비스의 메시지를 표시하며, 이 메시지는 앱의 다른 부분에서 업데이트될 수 있습니다. 컴포넌트는 `AppState.OnChange` 이벤트와 함께 `StateHasChanged` 메서드를 등록하여 메시지가 업데이트될 때마다 컴포넌트가 렌더링되도록 합니다.

```csharp
public class AppState
{
    public string Message { get; }

    // 컴포넌트가 변경 알림을 받을 수 있도록 합니다.
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        Message = message;
        NotifyStateChanged();
    }

    private void NotifyStateChanged() => OnChange?.Invoke();
}
```

```razor
@inject AppState AppState

<p>App message: @AppState.Message</p>

@code {
    protected override void OnInitialized()
    {
        AppState.OnChange += StateHasChanged;
    }
}
```

## 컴포넌트 라이프사이클

Blazor의 모든 컴포넌트 라이프사이클 메서드에는 동기 및 비동기 버전이 있습니다. 컴포넌트 렌더링은 동기적입니다. 컴포넌트 렌더링의 일부로 비동기 로직을 실행할 수 없습니다. 모든 비동기 로직은 `async` 라이프사이클 메서드의 일부로 실행되어야 합니다.

### OnInitialized

`OnInitialized` 및 `OnInitializedAsync` 메서드는 컴포넌트를 초기화하는 데 사용됩니다. 컴포넌트는 처음 렌더링된 후에 일반적으로 초기화됩니다. 컴포넌트가 초기화된 후 여러 번 렌더링될 수 있으며, 결국 폐기됩니다. `OnInitialized` 메서드는 ASP.NET Web Forms 페이지 및 컨트롤의 `Page_Load` 이벤트와 유사합니다.

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### OnParametersSet

`OnParametersSet` 및 `OnParametersSetAsync` 메서드는 컴포넌트가 부모로부터 매개변수를 받았을 때 호출되며, 값은 속성에 할당됩니다. 이러한 메서드는 컴포넌트 초기화 후 *및 각 컴포넌트가 렌더링될 때마다* 실행됩니다.

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### OnAfterRender

`OnAfterRender` 및 `OnAfterRenderAsync` 메서드는 컴포넌트가 렌더링된 후에 호출됩니다. 이 시점에서 요소 및 컴포넌트 참조가 채워집니다. 이 시점에서 브라우저와의 상호작용이 활성화됩니다. DOM 및 JavaScript 실행과의 상호작용이 안전하게 이루어질 수 있습니다.

```csharp
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender)
    {
        ...
    }
}
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        await ...
    }
}
```

`OnAfterRender` 및 `OnAfterRenderAsync`는 *서버에서 사전 렌더링될 때 호출되지 않습니다*.

`firstRender` 매개변수는 컴포넌트가 처음 렌더링될 때 `true`이며, 그렇지 않은 경우 `false`입니다.

### IDisposable

Razor 컴포넌트는 UI에서 제거될 때 리소스를 폐기하기 위해 `IDisposable`을 구현할 수 있습니다. Razor 컴포넌트는 `@implements` 지시어를 사용하여 `IDisposable`을 구현할 수 있습니다:

```razor
@using System
@implements IDisposable

...

@code {
    public void Dispose()
    {
        ...
    }
}
```

## 컴포넌트 참조 캡처

Blazor에서 컴포넌트 참조를 캡처하려면 `@ref` 지시어 속성을 사용합니다. 속성 값은 참조된 컴포넌트와 동일한 타입의 설정 가능한 필드 이름과 일치해야 합니다.

```razor
<MyLoginDialog @ref="loginDialog" ... />

@code {
    MyLoginDialog loginDialog = default!;

    void OnSomething()
    {
        loginDialog.Show();
    }
}
```

부모 컴포넌트가 렌더링될 때 필드는 자식 컴포넌트 인스턴스로 채워집니다. 그런 다음 컴포넌트 인스턴스에서 메서드를 호출하거나 다른 방식으로 조작할 수 있습니다.

컴포넌트 참조를 사용하여 컴포넌트 상태를 직접 조작하는 것은 권장되지 않습니다. 이렇게 하면 컴포넌트가 적절한 시간에 자동으로 렌더링되는 것을 방지합니다.

## 요소 참조 캡처

Razor 컴포넌트는 요소에 대한 참조를 캡처할 수 있습니다. Blazor에서는 요소 참조를 사용하여 DOM을 직접 조작할 수 없습니다. Blazor는 DOM 상호작용의 대부분을 DOM diffing 알고리즘을 사용하여 처리합니다. Blazor에서 캡처된 요소 참조는 불투명합니다. 그러나 이는 특정 요소 참조를 JavaScript interop 호출에 전달하는 데 사용됩니다.

## 템플릿화된 컴포넌트

Blazor 컴포넌트는 `RenderFragment` 또는 `RenderFragment<T>` 타입의 컴포넌트 매개변수를 정의하여 템플릿화될 수 있습니다. `RenderFragment`는 컴포넌트에 의해 렌더링될 수 있는 Razor 마크업 조각을 나타냅니다. `RenderFragment<T>`는 렌더링될 때 지정할 수 있는 매개변수를 받는 Razor 마크업 조각입니다.

### 자식 콘텐츠

Razor 컴포넌트는 `RenderFragment`로 자식 콘텐츠를 캡처하고 해당 콘텐츠를 컴포넌트 렌더링의 일부로 렌더링할 수 있습니다. 자식 콘텐츠를 캡처하려면 `RenderFragment` 타입의 컴포넌트 매개변수를 정의하고 이를 `ChildContent`라고 명명합니다.

*ChildContentComponent.razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

부모 컴포넌트는 일반 Razor 구문을 사용하여 자식 콘텐츠를 제공할 수 있습니다.

```razor
<ChildContentComponent>
    <ChildContent>
        <p>The time is @DateTime.Now</p>
    </ChildContent>
</ChildContentComponent>
```

### 템플릿 매개변수

템플릿화된 Razor 컴포넌트는 `RenderFragment` 또는 `RenderFragment<T>` 타입의 여러 컴포넌트 매개변수를 정의할 수 있습니다. `RenderFragment<T>`의 매개변수는 렌더링될 때 지정할 수 있습니다. 컴포넌트에 대한 제네릭 타입 매개변수를 지정하려면 `@typeparam` Razor 지시어를 사용합니다.

*SimpleListView.razor*

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in Items)
{
    <li>@ItemTemplate(item)</li>
}
</ul>

@code {
    [Parameter]
    public RenderFragment Heading { get; set; }

    [Parameter]
    public RenderFragment<TItem> ItemTemplate { get; set; }

    [Parameter]
    public IEnumerable<TItem> Items { get; set; }
}
```

템플릿화된 컴포넌트를 사용할 때 템플릿 매개변수는 매개변수의 이름과 일치하는 자식 요소를 사용하여 지정할 수 있습니다. 요소로 전달된 `RenderFragment<T>` 타입의 컴포넌트 인수는 기본적으로 `context`라는 암시적 매개변수를 가집니다. 이 암시적 매개변수의 이름은 자식 요소의 `Context` 속성을 사용하여 변경할 수 있습니다. 제네릭 타입 매개변수는 해당 타입 매개변수 이름과 일치하는 속성을 사용하여 지정할 수 있습니다. 타입 매개변수는 가능한 경우 추론됩니다:

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Context="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

이 컴포넌트의 출력은 다음과 같습니다:

```html
<h1>My list</h1>
<ul>
    <li><p>The message is: message1</p></li>
    <li><p>The message is: message2</p></li>
<ul>
```

## 코드 비하인드

Razor 컴포넌트는 일반적으로 단일 *.razor* 파일에서 작성됩니다. 그러나 코드와 마크업을 코드 비하인드 파일을 사용하여 분리할 수도 있습니다. 컴포넌트 파일을 사용하려면 컴포넌트 파일 이름과 일치하는 C# 파일을 추가하되, *.cs* 확장을 추가합니다(*Counter.razor.cs*). C# 파일을 사용하여 컴포넌트의 기본 클래스를

 정의합니다. 기본 클래스의 이름은 자유롭게 지을 수 있지만, 일반적으로 컴포넌트 클래스와 동일한 이름을 사용하고 `Base` 접미사를 추가합니다(`CounterBase`). 컴포넌트 기반 클래스는 `ComponentBase`를 상속받아야 합니다. 그런 다음 Razor 컴포넌트 파일에서 `@inherits` 지시어를 추가하여 컴포넌트의 기본 클래스를 지정합니다(`@inherits CounterBase`).

*Counter.razor*

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

*Counter.razor.cs*

```csharp
public class CounterBase : ComponentBase
{
    protected int currentCount = 0;

    protected void IncrementCount()
    {
        currentCount++;
    }
}
```

기본 클래스에서 컴포넌트의 멤버 가시성은 컴포넌트 클래스에서 보이도록 `protected` 또는 `public`이어야 합니다.

---
## 출처
[Build reusable UI components with Blazor](https://learn.microsoft.com/en-us/dotnet/architecture/blazor-for-web-forms-developers/components)

---
## [다음](./07_page_routing_layout.md)