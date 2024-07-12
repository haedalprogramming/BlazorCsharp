# Project structure for Blazor apps

## 목차
- [Project structure for Blazor apps](#project-structure-for-blazor-apps)
  - [목차](#목차)
  - [프로젝트 파일](#프로젝트-파일)
    - [Blazor 서버 앱 프로젝트 파일](#blazor-서버-앱-프로젝트-파일)
    - [Blazor WebAssembly 앱 프로젝트 파일](#blazor-webassembly-앱-프로젝트-파일)
  - [진입점](#진입점)
    - [Blazor 서버 앱의 진입점](#blazor-서버-앱의-진입점)
    - [Blazor WebAssembly 앱의 진입점](#blazor-webassembly-앱의-진입점)
  - [정적 파일](#정적-파일)
  - [구성](#구성)
  - [Razor 컴포넌트](#razor-컴포넌트)
  - [페이지](#페이지)
  - [레이아웃](#레이아웃)
  - [Blazor 부트스트랩](#blazor-부트스트랩)
    - [Blazor 서버 앱의 호스트 페이지](#blazor-서버-앱의-호스트-페이지)
    - [Blazor WebAssembly 앱의 호스트 페이지](#blazor-webassembly-앱의-호스트-페이지)
  - [빌드 출력](#빌드-출력)
  - [Hot Reload로 앱 실행](#hot-reload로-앱-실행)
  - [출처](#출처)
  - [다음](#다음)

---

Blazor는 ASP.NET Web Forms와 다른 프로젝트 구조를 가지고 있지만, 유사한 개념을 많이 공유합니다. 여기서는 Blazor 프로젝트의 구조를 소개하고, 이를 이해하기 쉽게 설명하겠습니다.

Blazor 앱을 만들려면 Blazor 시작 단계의 지침을 따르십시오. Blazor 서버 앱 또는 ASP.NET Core에서 호스팅되는 Blazor WebAssembly 앱을 만들 수 있습니다. 호스팅 모델에 특화된 논리를 제외하면, 두 프로젝트의 대부분의 코드는 동일합니다.

## 프로젝트 파일

Blazor 프로젝트는 .NET 프로젝트로, 프로젝트 파일이 단순하게 구성되어 있습니다.

### Blazor 서버 앱 프로젝트 파일
```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <TargetFramework>net8.0</TargetFramework>
  </PropertyGroup>
</Project>
```

### Blazor WebAssembly 앱 프로젝트 파일
```xml
<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">
  <PropertyGroup>
    <TargetFramework>net8.0</TargetFramework>
    <ImplicitUsings>enable</ImplicitUsings>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly" Version="8.0.0" />
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly.DevServer" Version="8.0.0" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

Blazor WebAssembly 프로젝트는 `Microsoft.NET.Sdk.BlazorWebAssembly` SDK를 사용합니다. 이는 WebAssembly 기반 .NET 런타임에서 브라우저 내에서 실행되기 때문입니다.

## 진입점

Blazor 앱의 진입점은 *Program.cs* 파일에 정의됩니다. 이는 앱이 시작될 때 실행되는 코드를 포함합니다.

### Blazor 서버 앱의 진입점
```csharp
using Microsoft.AspNetCore.Components.Authorization;
using Microsoft.AspNetCore.Identity;
using Microsoft.EntityFrameworkCore;

var builder = WebApplication.CreateBuilder(args);

// 서비스 추가
var connectionString = builder.Configuration.GetConnectionString("DefaultConnection");
builder.Services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(connectionString));
builder.Services.AddDefaultIdentity<IdentityUser>()
    .AddEntityFrameworkStores<ApplicationDbContext>();
builder.Services.AddRazorPages();
builder.Services.AddServerSideBlazor();

var app = builder.Build();

// HTTP 요청 파이프라인 구성
if (app.Environment.IsDevelopment())
{
    app.UseDeveloperExceptionPage();
}
else
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}

app.UseHttpsRedirection();
app.UseStaticFiles();
app.UseRouting();
app.UseAuthentication();
app.UseAuthorization();

app.MapControllers();
app.MapBlazorHub();
app.MapFallbackToPage("/_Host");

app.Run();
```

### Blazor WebAssembly 앱의 진입점
```csharp
using Microsoft.AspNetCore.Components.WebAssembly.Hosting;

var builder = WebAssemblyHostBuilder.CreateDefault(args);
builder.RootComponents.Add<App>("#app");
builder.Services.AddScoped(sp => new HttpClient { BaseAddress = new Uri(builder.HostEnvironment.BaseAddress) });

await builder.Build().RunAsync();
```

Blazor 서버 앱은 HTTP 서버를 설정하는 반면, Blazor WebAssembly 앱은 브라우저 내에서 실행됩니다.

## 정적 파일

Blazor 프로젝트의 정적 파일은 *wwwroot* 폴더에 저장됩니다. 이 폴더의 파일만 웹에서 접근할 수 있습니다. 이는 보안을 강화하기 위한 설정입니다.

## 구성

Blazor 서버 앱은 ASP.NET Core 구성 시스템을 사용합니다. 예를 들어, 기본 설정은 *appsettings.json* 파일에 저장됩니다.

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

Blazor WebAssembly 앱은 현재 동일한 구성 추상화를 지원하지 않지만, 향후 추가될 수 있습니다.

## Razor 컴포넌트

Blazor 프로젝트의 주요 파일은 *.razor* 파일입니다. Razor는 HTML과 C#을 결합하여 동적 웹 UI를 생성하는 템플릿 언어입니다. Blazor 컴포넌트는 ASP.NET Web Forms의 사용자 컨트롤과 유사합니다.

```razor
@page "/counter"

<h3>Counter</h3>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        currentCount++;
    }
}
```

## 페이지

Blazor에서는 페이지가 컴포넌트에 라우트를 할당하여 정의됩니다. 예를 들어, *Pages/Counter.razor* 파일에 작성된 `Counter` 컴포넌트는 다음과 같은 라우트를 정의합니다:

```razor
@page "/counter"
```

## 레이아웃

Blazor 앱에서 공통 페이지 레이아웃은 레이아웃 컴포넌트를 사용하여 처리됩니다. 예를 들어, *Shared/MainLayout.razor* 파일에 정의할 수 있습니다.

## Blazor 부트스트랩

Blazor를 부트스트랩하려면 앱은 루트 컴포넌트와 해당 Blazor 프레임워크 스크립트를 추가해야 합니다.

### Blazor 서버 앱의 호스트 페이지
```razor
@page "/"
@namespace BlazorApp.Pages

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <component type="typeof(App)" render-mode="ServerPrerendered" />
    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

### Blazor WebAssembly 앱의 호스트 페이지
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/app.css" rel="stylesheet" />
</head>
<body>
    <div id="app">Loading...</div>
    <script src="_framework/blazor.webassembly.js"></script>
</body>
</html>
```

Blazor WebAssembly 앱의 *Program.cs* 파일에서 루트 컴포넌트를 정의합니다:

```csharp
var builder = WebAssemblyHostBuilder.CreateDefault(args);
builder.RootComponents.Add<App>("#app");
await builder.Build().RunAsync();
```

## 빌드 출력

Blazor 프로젝트가 빌드되면 모든 Razor 컴포넌트와 코드 파일이 단일 어셈블리로 컴파일됩니다.

## Hot Reload로 앱 실행

Blazor 앱은 Visual Studio에서 Hot Reload를 지원합니다. Hot Reload를 사용하면 코드 변경 사항을 브라우저에서 실시간으로 반영할 수 있습니다.

Blazor는 최신 웹 애플리케이션 개발을 위한 강력한 프레임워크입니다. 이를 통해 효율적이고 상호작용이 풍부한 웹 애플리케이션을 개발할 수 있습니다.

---
## 출처
[Project structure for Blazor apps](https://learn.microsoft.com/en-us/dotnet/architecture/blazor-for-web-forms-developers/project-structure)

---
## [다음](./05_startup.md)