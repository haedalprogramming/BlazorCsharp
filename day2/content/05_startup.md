# App startup

## 목차
- [App startup](#app-startup)
  - [목차](#목차)
  - [ASP.NET Core와 Blazor Server의 시작 구조](#aspnet-core와-blazor-server의-시작-구조)
  - [정적 자산 번들링과 최소화](#정적-자산-번들링과-최소화)
  - [출처](#출처)
  - [다음](#다음)

---

ASP.NET 애플리케이션은 일반적으로 `global.asax.cs` 파일을 가지고 있으며, 이 파일은 `Application_Start` 이벤트를 정의하여 HTML 렌더링과 .NET 처리에 사용되는 서비스를 구성하고 사용할 수 있게 합니다. 이 장에서는 ASP.NET Core와 Blazor Server에서 이러한 것들이 어떻게 다른지 살펴봅니다.

## ASP.NET Core와 Blazor Server의 시작 구조

Blazor Server 애플리케이션은 ASP.NET Core 3.0 이상 버전 위에 위치합니다. ASP.NET Core 웹 애플리케이션은 *Program.cs* 또는 *Startup.cs* 클래스의 두 가지 메서드를 통해 구성됩니다. 아래는 샘플 *Program.cs* 파일입니다:

```csharp
using BlazorApp1.Data;
using Microsoft.AspNetCore.Components;
using Microsoft.AspNetCore.Components.Web;

var builder = WebApplication.CreateBuilder(args);

// Add services to the container.
builder.Services.AddRazorPages();
builder.Services.AddServerSideBlazor();
builder.Services.AddSingleton<WeatherForecastService>();

var app = builder.Build();

// Configure the HTTP request pipeline.
if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
    app.UseHsts();
}

app.UseHttpsRedirection();
app.UseStaticFiles();
app.UseRouting();
app.MapBlazorHub();
app.MapFallbackToPage("/_Host");

app.Run();
```

앱의 필요한 서비스는 `WebApplicationBuilder` 인스턴스의 `Services` 컬렉션에 추가됩니다. 이를 통해 다양한 ASP.NET Core 프레임워크 서비스가 프레임워크의 내장된 종속성 주입 컨테이너와 함께 구성됩니다. 다양한 `builder.Services.Add*` 메서드는 인증, Razor 페이지, MVC 컨트롤러 라우팅, SignalR 및 Blazor Server 상호작용 등 많은 기능을 활성화하는 서비스를 추가합니다.

`builder`에 의해 `app`이 빌드된 후, `app`에 대한 나머지 호출은 HTTP 파이프라인을 구성합니다. 이러한 호출을 통해 애플리케이션에 전송된 모든 요청을 처리할 미들웨어를 위에서 아래로 선언합니다. 기본 구성의 대부분의 기능은 한 곳에 모여 있어 참조하기 쉬운 형태로 제공됩니다.

애플리케이션 환경이 `Development`로 표시되지 않은 경우 사용자 정의 오류 페이지가 구성되지 않으며, 항상 표시되도록 설정됩니다. 또한, ASP.NET Core 애플리케이션은 기본적으로 TLS를 사용하여 보안 페이지를 제공하도록 `UseHttpsRedirection` 메서드 호출로 구성됩니다.

ASP.NET Core에서는 정적 파일(JavaScript, CSS, 이미지 파일 등)에 대한 요청 지원을 명시적으로 활성화해야 하며, 기본적으로 애플리케이션의 *wwwroot* 폴더에 있는 파일만 공개적으로 주소 지정할 수 있습니다.

`UseRouting` 메서드는 ASP.NET Core 라우터를 파이프라인에 추가하며, 라우팅 구성에 대한 자세한 내용은 라우팅 섹션에서 확인할 수 있습니다.

이 섹션의 마지막 `app.Map*` 호출은 ASP.NET Core가 수신하는 엔드포인트를 정의합니다. 첫 번째 항목인 `MapBlazorHub`는 SignalR 허브를 구성하여 Blazor 구성 요소의 상태 및 렌더링을 처리하는 서버와의 실시간 지속 연결을 제공합니다. `MapFallbackToPage` 메서드 호출은 Blazor 애플리케이션을 시작하는 페이지의 웹 접근 가능 위치를 나타내며, 클라이언트 측에서의 심층 링크 요청을 처리하도록 애플리케이션을 구성합니다. 기본 프로젝트 템플릿에서 `/counter`와 같은 Blazor 처리 라우트로 직접 탐색할 때 이 기능이 작동하는 것을 볼 수 있습니다. 요청은 *_Host.cshtml* 폴백 페이지에 의해 처리되며, 이후 Blazor 라우터가 실행되어 카운터 페이지를 렌더링합니다.

맨 마지막 줄은 애플리케이션을 시작하는데 사용됩니다.

## 정적 자산 번들링과 최소화

CSS 스타일시트 및 JavaScript 파일과 같은 자산 번들을 위한 기술이 크게 변화했으며, 이러한 리소스를 관리하기 위한 빠르게 발전하는 도구와 기술을 제공하는 다른 기술들이 등장했습니다. 이에 따라 Grunt, Gulp, WebPack과 같은 Node 명령줄 도구를 사용하여 정적 자산을 패키징하는 것을 권장합니다.

Grunt, Gulp 및 WebPack 명령줄 도구와 관련 구성은 애플리케이션에 추가할 수 있으며, ASP.NET Core는 애플리케이션 빌드 과정에서 이러한 파일들을 조용히 무시합니다. 다음과 같은 구문을 사용하여 프로젝트 파일 내에 `Target`을 추가하여 gulp 스크립트와 해당 스크립트 내의 `min` 대상을 트리거하는 호출을 추가할 수 있습니다:

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

CSS 및 JavaScript 파일을 관리하기 위한 두 가지 전략에 대한 자세한 내용은 ASP.NET Core에서 정적 자산 번들링 및 최소화 문서에서 확인할 수 있습니다.

---
## 출처
[App startup](https://learn.microsoft.com/en-us/dotnet/architecture/blazor-for-web-forms-developers/project-structure)

---
## [다음](./06_components.md)