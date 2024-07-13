# An introduction to Blazor

## 목차
- [An introduction to Blazor](#an-introduction-to-blazor)
  - [목차](#목차)
  - [오픈 소스 및 크로스 플랫폼 .NET](#오픈-소스-및-크로스-플랫폼-net)
  - [클라이언트 측 웹 개발](#클라이언트-측-웹-개발)
  - [WebAssembly: 웹을 위한 바이트 코드](#webassembly-웹을-위한-바이트-코드)
  - [Blazor: .NET을 사용한 풀스택 웹 개발](#blazor-net을-사용한-풀스택-웹-개발)
  - [Blazor 시작하기](#blazor-시작하기)
  - [출처](#출처)
  - [다음](#다음)

---

웹 애플리케이션 개발의 세계는 지속적으로 진화하고 있습니다. 오늘날, 더 나은 성능과 사용성을 위해 최신 기술과 트렌드를 따르는 것이 중요합니다. 그 중에서도 주목할 만한 두 가지 트렌드는 오픈 소스 및 크로스 플랫폼 기술의 확산과 클라이언트 측 애플리케이션 로직의 증가입니다.

## 오픈 소스 및 크로스 플랫폼 .NET

현대의 소프트웨어 개발 환경에서는 다양한 플랫폼을 지원하는 것이 필수적입니다. 초기의 .NET Framework는 Windows에만 국한되었으나, 이제는 .NET Core와 Xamarin을 통해 macOS와 Linux, iOS, Android 등 다양한 플랫폼에서 실행될 수 있습니다. 2020년에는 .NET Core와 Mono가 통합된 .NET 5가 출시되어, 더욱 강력하고 일관된 개발자 경험을 제공합니다. 

이제 대부분의 현대 웹 프레임워크는 오픈 소스로 제공됩니다. 이는 커뮤니티의 기여를 통해 빠르게 발전하고, 투명한 개발 과정을 거치며, 누구나 참여할 수 있는 생태계를 조성합니다. .NET 커뮤니티 또한 이러한 변화에 발맞춰 발전하고 있습니다.

## 클라이언트 측 웹 개발

과거의 웹 애플리케이션은 주로 서버 렌더링 방식으로 동작했습니다. 즉, 브라우저가 서버에 요청을 보내면 서버가 응답을 생성하고 이를 브라우저가 처리하는 방식입니다. 그러나 오늘날의 브라우저는 강력한 플랫폼으로 발전하여, 클라이언트 측에서 많은 작업을 처리할 수 있습니다. 이는 더 빠르고 상호작용적인 사용자 경험을 제공합니다. 

JavaScript 프레임워크인 Angular, React, Vue 등이 이러한 클라이언트 측 웹 개발을 이끌어왔습니다. 그러나 두 개의 다른 생태계 (.NET과 JavaScript)를 동시에 관리하는 것은 복잡하고 비용이 많이 들 수 있습니다. 이를 해결하기 위해 웹 커뮤니티는 WebAssembly라는 기술을 도입했습니다.

## WebAssembly: 웹을 위한 바이트 코드

WebAssembly는 웹 브라우저에서 네이티브 코드에 가까운 성능을 제공하는 바이트 코드입니다. 이를 통해 다양한 언어로 작성된 코드를 브라우저에서 실행할 수 있습니다. 2017년부터 .NET도 WebAssembly를 지원하여, 브라우저에서 직접 .NET 코드를 실행할 수 있게 되었습니다. 이는 .NET 개발자에게 완전히 새로운 가능성을 열어줍니다.

## Blazor: .NET을 사용한 풀스택 웹 개발

Blazor는 JavaScript 대신 C#을 사용하여 클라이언트 측 웹 애플리케이션을 개발할 수 있는 프레임워크입니다. Blazor는 WebAssembly를 통해 브라우저에서 직접 실행되거나, 서버 측에서 실행되어 실시간 연결을 통해 사용자 상호작용을 처리할 수 있습니다.

Blazor는 다음과 같은 기능을 제공합니다:

- 폼 및 유효성 검사
- 종속성 주입
- 클라이언트 측 라우팅
- 레이아웃 관리
- 브라우저 내 디버깅
- JavaScript 상호 운용

Blazor는 기존의 .NET 개발자들에게 친숙한 환경을 제공하며, 클라이언트 측 개발의 복잡성을 줄여줍니다. 이는 특히 최신 웹 기술을 활용하고자 하는 .NET 개발자들에게 매력적인 선택이 될 수 있습니다.

## Blazor 시작하기

Blazor를 시작하는 것은 매우 쉽습니다. <https://blazor.net>을 방문하여 필요한 .NET SDK와 Blazor 프로젝트 템플릿을 설치하세요. 또한 Visual Studio 또는 Visual Studio Code에서 Blazor 도구 설정에 대한 지침도 확인할 수 있습니다.

Blazor는 최신 웹 개발의 요구를 충족시키기 위해 만들어졌으며, .NET 개발자에게 클라이언트 측 애플리케이션 개발의 새로운 가능성을 열어줍니다. 지금 Blazor를 시작해보세요!

---
## 출처
[ASP.NET Core Blazor fundamentals](https://learn.microsoft.com/en-us/dotnet/architecture/blazor-for-web-forms-developers/introduction)

---
## [다음](./02_Architecture_comparison.md)