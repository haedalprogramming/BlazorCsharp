# 프론트엔드 프레임워크의 기능과 ASP.NET Core Blazor 예제

## 목차
- [프론트엔드 프레임워크의 기능과 ASP.NET Core Blazor 예제](#프론트엔드-프레임워크의-기능과-aspnet-core-blazor-예제)
  - [목차](#목차)
  - [소개](#소개)
  - [1. 프론트엔드 프레임워크의 주요 기능](#1-프론트엔드-프레임워크의-주요-기능)
    - [1.1 컴포넌트 기반 아키텍처](#11-컴포넌트-기반-아키텍처)
    - [1.2 상태 관리](#12-상태-관리)
    - [1.3 라우팅](#13-라우팅)
    - [1.4 데이터 바인딩](#14-데이터-바인딩)
    - [1.5 이벤트 처리](#15-이벤트-처리)
    - [1.6 폼 처리 및 유효성 검사](#16-폼-처리-및-유효성-검사)
    - [1.7 HTTP 요청](#17-http-요청)
  - [2. ASP.NET Core Blazor 소개](#2-aspnet-core-blazor-소개)
    - [2.1 Blazor 개요](#21-blazor-개요)
    - [2.2 Blazor의 주요 기능](#22-blazor의-주요-기능)
  - [3. ASP.NET Core Blazor 예제](#3-aspnet-core-blazor-예제)
    - [3.1 프로젝트 생성](#31-프로젝트-생성)
    - [3.2 컴포넌트 작성](#32-컴포넌트-작성)
      - [`MainLayout.razor`](#mainlayoutrazor)
      - [`NavMenu.razor`](#navmenurazor)
      - [`Index.razor`](#indexrazor)
    - [3.3 상태 관리와 데이터 바인딩](#33-상태-관리와-데이터-바인딩)
      - [`Counter.razor`](#counterrazor)
    - [3.4 라우팅](#34-라우팅)
      - [`App.razor`](#apprazor)
    - [3.5 폼 처리 및 유효성 검사](#35-폼-처리-및-유효성-검사)
      - [`EditFormExample.razor`](#editformexamplerazor)
    - [3.6 HTTP 요청](#36-http-요청)
      - [`FetchData.razor`](#fetchdatarazor)
  - [결론](#결론)
  - [출처](#출처)
  - [다음](#다음)

## 소개
프론트엔드 프레임워크는 웹 애플리케이션 개발을 더 쉽고 효율적으로 만들어주는 도구입니다. 이 문서에서는 프론트엔드 프레임워크가 지원하는 주요 기능들을 소개하고, ASP.NET Core Blazor를 예시로 설명합니다.

## 1. 프론트엔드 프레임워크의 주요 기능

### 1.1 컴포넌트 기반 아키텍처
프론트엔드 프레임워크는 웹 페이지를 여러 개의 독립적인 컴포넌트로 나누어 개발할 수 있도록 지원합니다.
- **재사용 가능**: 컴포넌트는 독립적이고 재사용 가능한 코드 블록입니다.
- **모듈화**: 코드의 유지 보수성과 가독성을 높입니다.

### 1.2 상태 관리
웹 애플리케이션에서 상태를 효과적으로 관리할 수 있는 기능을 제공합니다.
- **로컬 상태**: 개별 컴포넌트의 상태 관리.
- **전역 상태**: 애플리케이션 전체에서 공유되는 상태 관리.

### 1.3 라우팅
클라이언트 측에서 페이지 이동을 관리할 수 있는 기능을 제공합니다.
- **싱글 페이지 애플리케이션(SPA)**: 전체 페이지를 다시 로드하지 않고도 다른 페이지로 이동할 수 있습니다.
- **동적 라우팅**: URL에 따라 다른 컴포넌트를 로드합니다.

### 1.4 데이터 바인딩
데이터와 UI 요소를 연결하여 상호 작용을 쉽게 만듭니다.
- **단방향 바인딩**: 데이터가 변경될 때 UI를 업데이트합니다.
- **양방향 바인딩**: UI의 변경이 데이터에 반영됩니다.

### 1.5 이벤트 처리
사용자의 입력과 상호작용을 처리할 수 있는 기능을 제공합니다.
- **클릭 이벤트**: 버튼 클릭 시 특정 동작을 실행합니다.
- **폼 이벤트**: 폼 제출 시 데이터를 처리합니다.

### 1.6 폼 처리 및 유효성 검사
사용자 입력을 처리하고, 유효성을 검사할 수 있는 기능을 제공합니다.
- **폼 데이터 바인딩**: 폼 입력을 데이터 모델과 연결합니다.
- **유효성 검사**: 사용자 입력의 유효성을 확인합니다.

### 1.7 HTTP 요청
서버와의 비동기 통신을 지원합니다.
- **AJAX 요청**: 서버에서 데이터를 가져오거나 서버로 데이터를 전송합니다.
- **API 호출**: RESTful API와 통신합니다.

## 2. ASP.NET Core Blazor 소개

### 2.1 Blazor 개요
- **Blazor**는 C#과 .NET을 사용하여 프론트엔드 웹 애플리케이션을 개발할 수 있는 프레임워크입니다.
- **컴포넌트 기반**: Blazor는 컴포넌트 기반 아키텍처를 사용하여 UI를 구성합니다.
- **웹어셈블리**: 브라우저에서 .NET 코드를 실행할 수 있습니다.

### 2.2 Blazor의 주요 기능
- **컴포넌트 기반 개발**: UI를 구성하는 독립적인 컴포넌트 작성.
- **양방향 데이터 바인딩**: 데이터와 UI 요소 간의 상호 작용을 쉽게 관리.
- **라우팅**: 클라이언트 측 라우팅을 통해 페이지 이동 관리.
- **폼 및 유효성 검사**: 사용자 입력 처리 및 유효성 검사 지원.
- **HTTP 클라이언트**: 서버와 비동기 통신 가능.

## 3. ASP.NET Core Blazor 예제

### 3.1 프로젝트 생성
```bash
dotnet new blazorwasm -o BlazorApp
cd BlazorApp
dotnet run
```
- **`dotnet new blazorwasm`**: 새로운 Blazor WebAssembly 애플리케이션 생성.
- **`dotnet run`**: 애플리케이션 실행.

### 3.2 컴포넌트 작성
Blazor 컴포넌트는 `.razor` 파일로 작성됩니다.

#### `MainLayout.razor`
```razor
@inherits LayoutComponentBase

<PageTitle>Blazor App</PageTitle>

<div class="sidebar">
    <NavMenu />
</div>

<div class="main">
    <div class="top-row px-4">
        <a href="https://docs.microsoft.com/aspnet/" target="_blank">About</a>
    </div>

    <div class="content px-4">
        @Body
    </div>
</div>
```

#### `NavMenu.razor`
```razor
<div class="nav-menu">
    <ul>
        <li><NavLink href="">Home</NavLink></li>
        <li><NavLink href="counter">Counter</NavLink></li>
    </ul>
</div>
```

#### `Index.razor`
```razor
@page "/"

<h3>Welcome to Blazor!</h3>
```

### 3.3 상태 관리와 데이터 바인딩
Blazor는 상태 관리를 위해 `@code` 블록을 사용합니다.

#### `Counter.razor`
```razor
@page "/counter"

<h3>Counter</h3>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        currentCount++;
    }
}
```

### 3.4 라우팅
Blazor는 `@page` 지시문을 사용하여 컴포넌트의 경로를 정의합니다.

#### `App.razor`
```razor
<Router AppAssembly="@typeof(App).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
        <FocusOnNavigate RouteData="@routeData" Selector="h1" />
    </Found>
    <NotFound>
        <LayoutView Layout="@typeof(MainLayout)">
            <p>Sorry, there's nothing at this address.</p>
        </LayoutView>
    </NotFound>
</Router>
```

### 3.5 폼 처리 및 유효성 검사
Blazor는 폼 입력을 처리하고 유효성을 검사할 수 있는 기능을 제공합니다.

#### `EditFormExample.razor`
```razor
@page "/editform"

<EditForm Model="@person" OnValidSubmit="HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <div>
        <label>First Name:</label>
        <InputText id="firstName" @bind-Value="person.FirstName" />
        <ValidationMessage For="@(() => person.FirstName)" />
    </div>
    <div>
        <label>Last Name:</label>
        <InputText id="lastName" @bind-Value="person.LastName" />
        <ValidationMessage For="@(() => person.LastName)" />
    </div>
    <button type="submit">Submit</button>
</EditForm>

@code {
    private Person person = new Person();

    private void HandleValidSubmit()
    {
        Console.WriteLine("Form submitted!");
    }

    public class Person
    {
        [Required]
        public string FirstName { get; set; }
        
        [Required]
        public string LastName { get; set; }
    }
}
```

### 3.6 HTTP 요청
Blazor는 `HttpClient`를 사용하여 서버와 비동기 통신을 지원합니다.

#### `FetchData.razor`
```razor
@page "/fetchdata"

@inject HttpClient Http

<h3>Weather forecast</h3>

@if (forecasts == null)
{
    <p><em>Loading...</em></p>
}
else
{
    <table class="table">
        <thead>
            <tr>
                <th>Date</th>
                <th>Temperature (C)</th>
                <th>Temperature (F)</th>
                <th>Summary</th>
            </tr>
        </thead>
        <tbody>
        @foreach (var forecast in forecasts)
        {
            <tr>
                <td>@forecast.Date.ToShortDateString()</td>
                <td>@forecast.TemperatureC</td>
                <td>@forecast.TemperatureF</td>
                <td>@forecast.Summary</td>
            </tr>
        }
        </tbody>
    </table>
}

@code {
    private WeatherForecast[] forecasts;

    protected override async Task OnInitializedAsync()
    {
        forecasts = await Http.GetFromJsonAsync<WeatherForecast[]>("sample-data/weather.json");
    }

    public class WeatherForecast
    {
        public DateTime Date { get; set; }
        public int TemperatureC { get; set; }
        public int TemperatureF { get; set; }
        public string Summary { get; set; }
    }
}
```

## 결론
프론트엔드 프레임워크는 웹 애플리케이션 개발을 단순화하고 효율적으로 만들어줍니다. ASP.NET Core Blazor는 C#과 .NET을 사용하여 프론트엔드 개발을 가능하게 하며, 컴포

넌트 기반 아키텍처, 상태 관리, 라우팅, 데이터 바인딩, 폼 처리, HTTP 요청 등의 기능을 제공합니다. 이 문서를 통해 프론트엔드 프레임워크의 주요 기능과 Blazor를 활용한 웹 애플리케이션 개발의 기초를 이해할 수 있습니다.

## 출처
- [Blazor 공식 문서](https://docs.microsoft.com/en-us/aspnet/core/blazor/)
- [MDN Web Docs - 프론트엔드 프레임워크](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks)
- [W3Schools - ASP.NET](https://www.w3schools.com/asp/)

---
## [다음](./02_03_Forntend_Web_Design.md)