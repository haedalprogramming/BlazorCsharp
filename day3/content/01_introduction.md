# An introduction to Blazor for ASP.NET Web Forms developers

## 목차
- [An introduction to Blazor for ASP.NET Web Forms developers](#an-introduction-to-blazor-for-aspnet-web-forms-developers)
  - [목차](#목차)
  - [오픈 소스 및 크로스 플랫폼 .NET](#오픈-소스-및-크로스-플랫폼-net)
  - [클라이언트 측 웹 개발](#클라이언트-측-웹-개발)
  - [WebAssembly는 필요를 충족시킵니다](#webassembly는-필요를-충족시킵니다)
  - [Blazor: .NET을 사용한 풀스택 웹 개발](#blazor-net을-사용한-풀스택-웹-개발)
  - [Blazor 시작하기](#blazor-시작하기)
  - [출처](#출처)
  - [다음](#다음)

---

ASP.NET Web Forms 프레임워크는 2002년 .NET Framework가 처음 출시된 이후 .NET 웹 개발의 기본 요소로 자리 잡았습니다. 웹이 아직 초기 단계였을 때, ASP.NET Web Forms는 데스크톱 개발에 사용되던 많은 패턴을 채택하여 웹 애플리케이션 구축을 쉽고 생산적으로 만들었습니다. ASP.NET Web Forms에서는 재사용 가능한 UI 컨트롤로 웹 페이지를 빠르게 구성할 수 있습니다. 사용자 상호 작용은 이벤트로 자연스럽게 처리됩니다. Microsoft와 컨트롤 공급업체에서 제공하는 풍부한 Web Forms UI 컨트롤 생태계가 있습니다. 이러한 컨트롤은 데이터 소스에 연결하고 풍부한 데이터 시각화를 표시하는 노력을 덜어줍니다. 시각적으로 쉽게 관리할 수 있도록 Web Forms 디자이너는 컨트롤을 관리하기 위한 간단한 드래그 앤 드롭 인터페이스를 제공합니다.

수년 동안 Microsoft는 웹 개발 트렌드를 반영하여 새로운 ASP.NET 기반 웹 프레임워크를 도입했습니다. 이러한 웹 프레임워크에는 ASP.NET MVC, ASP.NET Web Pages, 최근의 ASP.NET Core 등이 포함됩니다. 각 새로운 프레임워크와 함께 일부는 ASP.NET Web Forms의 급격한 쇠퇴를 예측하며 이를 구식의 웹 프레임워크로 비판했습니다. 이러한 예측에도 불구하고 많은 .NET 웹 개발자는 여전히 ASP.NET Web Forms를 간단하고 안정적이며 생산적인 방법으로 사용하고 있습니다.

작성 시점에서 거의 50만 명의 웹 개발자가 매달 ASP.NET Web Forms를 사용하고 있습니다. ASP.NET Web Forms 프레임워크는 매우 안정적이어서 10년 전의 문서, 샘플, 책 및 블로그 게시물도 여전히 유용하고 관련성이 있습니다. 많은 .NET 웹 개발자에게 "ASP.NET"은 여전히 "ASP.NET Web Forms"과 동의어로 남아 있습니다. ASP.NET Web Forms를 다른 새로운 .NET 웹 프레임워크와 비교하는 논쟁은 계속될 수 있습니다. ASP.NET Web Forms는 여전히 웹 애플리케이션을 만드는 인기 있는 프레임워크입니다.

그럼에도 불구하고 소프트웨어 개발의 혁신은 멈추지 않습니다. 모든 소프트웨어 개발자는 새로운 기술과 트렌드를 따라가야 합니다. 특히 다음 두 가지 트렌드는 고려할 가치가 있습니다:

1. 오픈 소스 및 크로스 플랫폼으로의 이동
2. 애플리케이션 로직의 클라이언트로의 이동

## 오픈 소스 및 크로스 플랫폼 .NET

.NET과 ASP.NET Web Forms가 처음 출시되었을 때 플랫폼 생태계는 현재와 많이 달랐습니다. 데스크톱 및 서버 시장은 Windows가 지배하고 있었습니다. macOS와 Linux와 같은 대체 플랫폼은 아직 자리를 잡지 못하고 있었습니다. ASP.NET Web Forms는 Windows 전용 구성 요소로 .NET Framework와 함께 제공되므로 ASP.NET Web Forms 애플리케이션은 Windows Server 머신에서만 실행할 수 있습니다. 현대 환경에서는 서버와 개발 머신에 다양한 플랫폼을 사용하는 경우가 많아 많은 사용자에게 크로스 플랫폼 지원이 절대적으로 필요합니다.

대부분의 현대 웹 프레임워크는 이제 오픈 소스이기도 합니다. 이는 여러 가지 이점이 있습니다. 사용자는 버그를 수정하고 기능을 추가하는 단일 프로젝트 소유자에 의존하지 않습니다. 오픈 소스 프로젝트는 개발 진행 상황과 향후 변경 사항에 대한 투명성을 제공합니다. 오픈 소스 프로젝트는 전체 커뮤니티의 기여를 통해 혜택을 얻고 지원적인 오픈 소스 생태계를 조성합니다. 오픈 소스의 위험에도 불구하고 많은 소비자와 기여자는 기여자 라이선스 계약, 친화적인 라이선스, 계보 스캔 및 지원 재단과 같은 적절한 완화책을 통해 안전하고 합리적인 방식으로 오픈 소스 생태계의 이점을 누리고 있습니다.

.NET 커뮤니티는 크로스 플랫폼 지원과 오픈 소스를 모두 수용했습니다. .NET Core는 Windows, macOS 및 다양한 Linux 배포판을 포함한 여러 플랫폼에서 실행되는 오픈 소스 및 크로스 플랫폼 .NET 구현입니다. Xamarin은 Mono라는 오픈 소스 버전의 .NET을 제공합니다. Mono는 Android, iOS 및 시계와 스마트 TV를 포함한 다양한 형태에서 실행됩니다. 2020년, Microsoft는 .NET Core와 Mono를 "어디서나 사용할 수 있고 일관된 런타임 동작과 개발자 경험을 제공하는 단일 .NET 런타임 및 프레임워크"로 통합한 [.NET 5](https://devblogs.microsoft.com/dotnet/announcing-net-5-0/)를 발표했습니다.

ASP.NET Web Forms가 오픈 소스 및 크로스 플랫폼 지원의 혜택을 받을 수 있을까요? 불행히도 답은 아니오입니다. 적어도 플랫폼의 나머지 부분과 동일한 정도로는 아닙니다. .NET 팀은 ASP.NET Web Forms가 .NET Core 또는 .NET 8로 포팅되지 않을 것임을 [분명히 했습니다](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/). 왜 그럴까요?

.NET Core의 초기 시절에 ASP.NET Web Forms를 포팅하려는 노력이 있었습니다. 그러나 요구되는 변경 사항의 수가 너무 많았습니다. 또한 Microsoft조차 동시에 지원할 수 있는 웹 프레임워크의 수에는 한계가 있다는 점을 인정합니다. 아마도 커뮤니티의 누군가가 ASP.NET Web Forms의 오픈 소스 및 크로스 플랫폼 버전을 만드는 일을 맡을 것입니다. ASP.NET Web Forms의 [소스 코드는 참조 형식으로 공개](https://github.com/microsoft/referencesource)되었습니다. 그러나 현재로서는 ASP.NET Web Forms가 Windows 전용으로 남아 있고 오픈 소스 기여 모델이 없을 것 같습니다. 크로스 플랫폼 지원이나 오픈 소스가 시나리오에서 중요해진다면 새로운 것을 찾아야 합니다.

이것이 ASP.NET Web Forms가 *죽었다*는 의미일까요? 전혀 그렇지 않습니다! .NET Framework가 Windows의 일부로 제공되는 한 ASP.NET Web Forms는 지원되는 프레임워크로 남아 있을 것입니다. 많은 Web Forms 개발자에게 크로스 플랫폼 및 오픈 소스 지원의 부족은 문제가 되지 않습니다. 크로스 플랫폼 지원, 오픈 소스 또는 .NET Core나 .NET 8의 다른 새로운 기능이 필요하지 않다면 Windows에서 ASP.NET Web Forms를 계속 사용하는 것은 괜찮습니다. ASP.NET Web Forms는 앞으로도 수년간 웹 애플리케이션을 작성하는 생산적인 방법으로 남을 것입니다.

그러나 고려할 가치가 있는 또 다른 트렌드가 있으며, 그것은 클라이언트로의 이동입니다.

## 클라이언트 측 웹 개발

ASP.NET Web Forms를 포함한 모든 .NET 기반 웹 프레임워크는 역사적으로 하나의 공통점을 가지고 있습니다. 그것은 *서버 렌더링*된다는 것입니다. 서버 렌더링 웹 애플리케이션에서는 브라우저가 서버에 요청을 보내고, 서버는 응답을 생성하기 위해 코드를 실행합니다 (ASP.NET 애플리케이션에서는 .NET 코드). 그 응답은 브라우저로 다시 보내져 처리됩니다. 이 모델에서 브라우저는 얇은 렌더링 엔진으로 사용됩니다. UI 생성, 비즈니스 로직 실행 및 상태 관리는 서버에서 발생합니다.

그러나 브라우저는 다재다능한 플랫폼이 되었습니다. 브라우저는 사용자 기기의 기능에 접근할 수 있는 점점 더 많은 오픈 웹 표준을 구현합니다. 클라이언트 디바이스의 컴퓨팅 파워, 저장소, 메모리 및 기타 자원을 활용하지 않겠습니까? 특히 UI 상호 작용은 클라이언트 측에서 처리될 때 더 풍부하고 상호작용적인 느낌을 받을 수 있습니다. 서버에서 처리되어야 하는 로직과 데이터는 여전히 서버 측에서 처리할 수 있습니다. Web API 호출이나 실시간 프로토콜 (예: WebSockets)을 사용할 수 있습니다. 이러한 이점은 JavaScript를 작성할 의향이 있는 웹 개발자에게 무료로 제공됩니다. Angular, React 및 Vue와 같은 클라이언트 측 UI 프레임워크는 클라이언트 측 웹 개발을 단순화하고 인기를 끌었습니다. ASP.NET Web Forms 개발자도 클라이언트를 활용할 수 있으며 ASP.NET AJAX와 같은 통합 JavaScript 프레임워크를 통해 일부 기본 지원을 받을 수 있습니다.

그러나 두 가지 다른 플랫폼과 생태계 (.NET과 JavaScript)를 연결하는 것은 비용이 듭니다. 두 개의 병렬 세계에서 다른 언어, 프레임워크 및 도구에 대한 전문 지식이 필요합니다. 클라이언트와 서버 간에 코드를 쉽게 공유할 수 없으며, 이는 중복과 엔지니어링 오버헤드를 초래합니다. JavaScript 생태계를 따라가기도 어려울 수 있습니다. JavaScript 생태계는 매우 빠르게 진화하는 역사를 가지고 있습니다. 프론트엔

드 프레임워크와 빌드 도구의 선호도가 빠르게 변합니다. 업계는 Grunt에서 Gulp로, Gulp에서 Webpack으로의 진행을 목격했습니다. 동일한 불안한 변화는 jQuery, Knockout, Angular, React 및 Vue와 같은 프론트엔드 프레임워크에서도 발생했습니다. 그러나 JavaScript의 브라우저 독점 때문에 선택의 여지가 거의 없었습니다. 그러다가 웹 커뮤니티가 모여서 *기적*을 일으켰습니다!

## WebAssembly는 필요를 충족시킵니다

2015년, 주요 브라우저 공급업체들은 W3C 커뮤니티 그룹에 합류하여 WebAssembly라는 새로운 오픈 웹 표준을 만들었습니다. WebAssembly는 웹을 위한 바이트 코드입니다. 코드를 WebAssembly로 컴파일할 수 있다면, 이는 네이티브 속도에 가까운 속도로 모든 플랫폼의 모든 브라우저에서 실행될 수 있습니다. 초기 노력은 C/C++에 초점을 맞췄습니다. 그 결과 플러그인 없이 브라우저에서 네이티브 3D 그래픽 엔진을 실행하는 극적인 시연이 이루어졌습니다. WebAssembly는 이후 표준화되어 모든 주요 브라우저에 의해 구현되었습니다.

.NET을 WebAssembly에서 실행하는 작업은 2017년 말에 발표되었고 2020년에 출시되었습니다. 여기에는 .NET 5 및 이후 버전에 대한 지원이 포함됩니다. 브라우저에서 직접 .NET 코드를 실행할 수 있는 기능은 .NET을 사용한 풀스택 웹 개발을 가능하게 합니다.

## Blazor: .NET을 사용한 풀스택 웹 개발

자체적으로 브라우저에서 .NET 코드를 실행할 수 있는 기능은 클라이언트 측 웹 애플리케이션을 만드는 엔드투엔드 경험을 제공하지 않습니다. 여기에서 Blazor가 등장합니다. Blazor는 JavaScript 대신 C#을 기반으로 하는 클라이언트 측 웹 UI 프레임워크입니다. Blazor는 WebAssembly를 통해 브라우저에서 직접 실행될 수 있습니다. 브라우저 플러그인이 필요하지 않습니다. 또는 Blazor 애플리케이션은 서버 측에서 .NET에서 실행될 수 있으며, 모든 사용자 상호작용은 브라우저와의 실시간 연결을 통해 처리됩니다.

Blazor는 Visual Studio 및 Visual Studio Code에서 훌륭한 도구 지원을 제공합니다. 프레임워크에는 전체 UI 구성 요소 모델이 포함되어 있으며 다음과 같은 내장 기능이 있습니다:

- 폼 및 유효성 검사
- 종속성 주입
- 클라이언트 측 라우팅
- 레이아웃
- 브라우저 내 디버깅
- JavaScript 상호 운용

Blazor는 ASP.NET Web Forms와 많은 공통점을 가지고 있습니다. 두 프레임워크 모두 구성 요소 기반, 이벤트 중심, 상태 유지 UI 프로그래밍 모델을 제공합니다. 주요 아키텍처 차이점은 ASP.NET Web Forms는 서버에서만 실행된다는 것입니다. Blazor는 브라우저에서 클라이언트 측에서 실행될 수 있습니다. 그러나 ASP.NET Web Forms 배경에서 오는 경우 Blazor에서 익숙한 많은 것을 발견할 수 있을 것입니다. Blazor는 클라이언트 측 개발과 .NET의 오픈 소스, 크로스 플랫폼 미래를 활용하고자 하는 ASP.NET Web Forms 개발자에게 자연스러운 솔루션입니다.

이 책은 ASP.NET Web Forms 개발자에게 특별히 맞춘 Blazor에 대한 소개를 제공합니다. 각 Blazor 개념은 유사한 ASP.NET Web Forms 기능 및 관행의 맥락에서 제시됩니다. 이 책이 끝날 때쯤에는 다음을 이해하게 될 것입니다:

- Blazor 애플리케이션을 빌드하는 방법.
- Blazor가 작동하는 방식.
- Blazor와 .NET의 관계.
- 기존 ASP.NET Web Forms 애플리케이션을 적절한 경우 Blazor로 마이그레이션하기 위한 합리적인 전략.

## Blazor 시작하기

Blazor 시작하기는 쉽습니다. <https://blazor.net>으로 이동하여 적절한 .NET SDK 및 Blazor 프로젝트 템플릿을 설치하는 링크를 따르십시오. Visual Studio 또는 Visual Studio Code에서 Blazor 도구 설정에 대한 지침도 찾을 수 있습니다.

---
## 출처
[ASP.NET Core Blazor fundamentals](https://learn.microsoft.com/en-us/dotnet/architecture/blazor-for-web-forms-developers/introduction)

---
## [다음](./02_Architecture_comparison.md)