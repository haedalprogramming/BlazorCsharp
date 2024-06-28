# Blazor 소개

## 목차
- [Blazor 소개](#blazor-소개)
  - [목차](#목차)
  - [ASP.NET Core Blazor](#aspnet-core-blazor)
    - [Components](#components)
    - [Build a full-stack web app with Blazor](#build-a-full-stack-web-app-with-blazor)
    - [Build a native client app with Blazor Hybrid](#build-a-native-client-app-with-blazor-hybrid)
  - [ASP.NET Core Blazor supported platforms](#aspnet-core-blazor-supported-platforms)
  - [Tooling for ASP.NET Core Blazor](#tooling-for-aspnet-core-blazor)
    - [Visual Studio solution file (.sln)](#visual-studio-solution-file-sln)
    - [Use Visual Studio Code for cross-platform Blazor development](#use-visual-studio-code-for-cross-platform-blazor-development)
    - [Blazor template options](#blazor-template-options)
  - [ASP.NET Core Blazor WebAssembly build tools and ahead-of-time (AOT) compilation](#aspnet-core-blazor-webassembly-build-tools-and-ahead-of-time-aot-compilation)
    - [.NET WebAssembly build tools for .NET 6 projects](#net-webassembly-build-tools-for-net-6-projects)
    - [Ahead-of-time (AOT) compilation](#ahead-of-time-aot-compilation)
    - [Trim .NET IL after ahead-of-time (AOT) compilation](#trim-net-il-after-ahead-of-time-aot-compilation)
    - [Heap size for some mobile device browsers](#heap-size-for-some-mobile-device-browsers)
    - [Runtime relinking](#runtime-relinking)
    - [Single Instruction, Multiple Data (SIMD)](#single-instruction-multiple-data-simd)
    - [Exception handling](#exception-handling)
  - [ASP.NET Core Blazor hosting models](#aspnet-core-blazor-hosting-models)
    - [Blazor Server](#blazor-server)
    - [Blazor WebAssembly](#blazor-webassembly)
    - [Blazor Hybrid](#blazor-hybrid)
    - [Which Blazor hosting model should I choose?](#which-blazor-hosting-model-should-i-choose)
    - [Complete .NET API compatibility](#complete-net-api-compatibility)
    - [Direct access to server and network resources](#direct-access-to-server-and-network-resources)
    - [Small payload size with fast initial load time](#small-payload-size-with-fast-initial-load-time)
    - [Near native execution speed](#near-native-execution-speed)
    - [App code secure and private on the server](#app-code-secure-and-private-on-the-server)
    - [Run apps offline once downloaded](#run-apps-offline-once-downloaded)
    - [Static site hosting](#static-site-hosting)
    - [Offloads processing to clients](#offloads-processing-to-clients)
    - [Full access to native client capabilities](#full-access-to-native-client-capabilities)
    - [Web-based deployment](#web-based-deployment)
    - [Setting a component's hosting model](#setting-a-components-hosting-model)
  - [ASP.NET Core Blazor Hybrid](#aspnet-core-blazor-hybrid)
    - [Blazor Hybrid apps with .NET MAUI](#blazor-hybrid-apps-with-net-maui)
    - [Blazor Hybrid apps with WPF and Windows Forms](#blazor-hybrid-apps-with-wpf-and-windows-forms)
    - [Web View configuration](#web-view-configuration)
    - [Unhandled exceptions in Windows Forms and WPF apps](#unhandled-exceptions-in-windows-forms-and-wpf-apps)
    - [Globalization and localization](#globalization-and-localization)
    - [Access scoped services from native UI](#access-scoped-services-from-native-ui)
  - [ASP.NET Core Blazor project structure](#aspnet-core-blazor-project-structure)
    - [Blazor Web App](#blazor-web-app)
    - [Standalone Blazor WebAssembly](#standalone-blazor-webassembly)
    - [Location of the Blazor script](#location-of-the-blazor-script)
    - [Location of \<head\> and \<body\> content](#location-of-head-and-body-content)
  - [출처](#출처)
  - [다음](#다음)

---
## ASP.NET Core Blazor

Blazor에 오신 것을 환영합니다!

Blazor는 서버 측 렌더링과 클라이언트 상호 작용을 모두 지원하는 .NET 프론트엔드 웹 프레임워크로, 다음과 같은 단일 프로그래밍 모델을 지원합니다:
 - C#을 사용하여 풍부한 대화형 UI 생성
 - .NET으로 작성된 서버 및 클라이언트 앱 로직 공유
 - 모바일 브라우저를 포함한 넓은 브라우저 지원을 위해 HTML 및 CSS로 UI 렌더링
 - .NET과 Blazor를 사용하여 하이브리드 데스크톱 및 모바일 앱 빌드

클라이언트 측 웹 개발에 .NET을 사용하는 것은 다음과 같은 장점을 제공합니다:
 - C#로 코드를 작성하여 앱 개발 및 유지 관리에서 생산성을 향상시킬 수 있습니다.
 - 기존의 .NET 라이브러리 생태계를 활용합니다.
 - .NET의 성능, 신뢰성 및 보안을 활용합니다.
 - Visual Studio 또는 Visual Studio Code와 같은 개발 환경을 사용하여 Windows, Linux 또는 macOS에서 생산성을 유지할 수 있습니다. Docker와 같은 현대적인 호스팅 플랫폼과 통합할 수 있습니다.
 - 안정적이고 기능이 풍부하며 사용하기 쉬운 공통의 언어, 프레임워크 및 도구에 빌드합니다.

### Components

Blazor 앱은 구성 요소에 기반합니다. Blazor에서 구성 요소는 페이지, 대화 상자 또는 데이터 입력 양식과 같은 UI 요소입니다.

구성 요소는 다음을 포함하는 .NET C# 클래스로 .NET 어셈블리에 내장되어 있습니다:

 - 유연한 UI 렌더링 로직 정의
 - 사용자 이벤트 처리
 - 중첩 및 재사용 가능
 - Razor 클래스 라이브러리 또는 NuGet 패키지로 공유 및 배포할 수 있음

구성 요소 클래스는 일반적으로 .razor 파일 확장자를 가진 Razor 마크업 페이지 형태로 작성됩니다. Blazor에서 구성 요소는 공식적으로 Razor 구성 요소로 참조되며, 비공식적으로 Blazor 구성 요소로 알려져 있습니다. Razor는 HTML 마크업을 C# 코드와 결합하는 구문으로, 개발자 생산성을 위해 설계되었습니다. Razor를 사용하면 Visual Studio의 IntelliSense 프로그래밍 지원을 통해 동일한 파일에서 HTML 마크업과 C# 코드를 전환할 수 있습니다.

Blazor는 UI 구성을 위해 자연 HTML 태그를 사용합니다. 다음은 사용자가 버튼을 선택할 때 카운터를 증가시키는 구성 요소를 보여주는 Razor 마크업 예시입니다.

```razor
<PageTitle>Counter</PageTitle>

<h1>Counter</h1>

<p role="status">Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        currentCount++;
    }
}
```

구성 요소는 브라우저의 문서 객체 모델(DOM)의 인메모리 표현인 렌더 트리로 렌더링되며, UI를 유연하고 효율적으로 업데이트하는 데 사용됩니다.

### Build a full-stack web app with Blazor

Blazor 웹 앱은 단일 솔루션에서 서버 측 렌더링과 완전한 클라이언트 측 상호 작용을 갖춘 구성 요소 기반 아키텍처를 제공하며, 서버 측과 클라이언트 측 렌더링 모드 사이를 전환하고 동일한 페이지에서 혼합할 수 있습니다.

Blazor 웹 앱은 요청에 응답하여 서버에서 HTML 콘텐츠를 정적으로 렌더링하여 브라우저에 빠르게 UI를 전달할 수 있습니다. 대규모 JavaScript 번들을 다운로드할 필요 없이 서버에서 UI 렌더링이 신속하게 수행되므로 페이지가 빠르게 로드됩니다. Blazor는 양식 게시와 비동기로 생성된 콘텐츠의 스트리밍 렌더링과 같은 서버 렌더링에 대한 다양한 점진적인 향상으로 사용자 경험을 더욱 개선할 수도 있습니다.

Blazor는 브라우저와의 실시간 연결을 통해 서버에서 UI 상호 작용을 처리하는 대화형 서버 측 렌더링(대화형 SSR)을 지원합니다. 대화형 SSR을 사용하면 클라이언트 앱에서 기대할 수 있는 풍부한 사용자 경험을 구현할 수 있지만, 서버 리소스에 액세스하기 위한 API 엔드포인트를 생성할 필요가 없습니다. 대화형 페이지의 콘텐츠는 사전 렌더링되어 서버에서 초기 생성되고 렌더링된 컨트롤에 대한 이벤트 핸들러를 활성화하지 않고 클라이언트로 전송됩니다. 서버는 초기 요청에 대한 응답으로 페이지의 HTML UI를 가능한 빨리 출력하여 앱이 사용자에게 더 반응적으로 느껴지도록 합니다.

Blazor 웹 앱은 .NET 런타임을 사용하여 클라이언트 측 렌더링(CSR)과 상호 작용할 수 있는 WebAssembly로 빌드됩니다. WebAssembly에서 Blazor를 실행할 때 .NET 코드는 브라우저의 전체 기능에 액세스하고 JavaScript와 상호 작용할 수 있습니다. .NET 코드는 클라이언트 기계에서 악성 작업에 대한 보호를 제공하는 보안 샌드박스 내에서 브라우저에서 실행됩니다.

Blazor 앱은 서버를 사용하지 않고 브라우저에서 완전히 WebAssembly에서 실행할 수 있습니다. 독립형 Blazor WebAssembly 앱의 경우, 자산은 정적 콘텐츠를 클라이언트에 제공할 수 있는 웹 서버 또는 서비스로 배포됩니다. 다운로드한 후에 독립형 Blazor WebAssembly 앱은 Progressive Web App (PWA)로 캐시되고 오프라인에서 실행될 수 있습니다.

### Build a native client app with Blazor Hybrid

Blazor Hybrid는 웹, 모바일 및 데스크톱 플랫폼용 원시 클라이언트 앱에서 Razor 구성 요소를 사용할 수 있도록 하며, 원시 및 웹 기술을 혼합하여 구현합니다. 코드는 .NET 프로세스에서 네이티브로 실행되며 로컬 상호 운용 채널을 사용하여 웹 UI를 임베디드 웹 뷰 컨트롤에 렌더링합니다. 하이브리드 앱에서는 WebAssembly를 사용하지 않습니다. 하이브리드 앱은 C# 및 XAML을 사용하여 네이티브 모바일 및 데스크톱 앱을 만들기 위한 크로스 플랫폼 프레임워크 인 .NET Multi-platform App UI (.NET MAUI)로 구축됩니다.

Blazor Hybrid는 이전 기술에서 .NET MAUI로 앱을 전환하기 위해 Windows Presentation Foundation (WPF) 및 Windows Forms를 지원합니다.

---
## ASP.NET Core Blazor supported platforms

Blazor은 다음 표에 표시된 모바일 및 데스크톱 플랫폼의 브라우저에서 지원됩니다.

| Browser         | Version   |
|-----------------|-----------|
| Apple Safari    | Current†  |
| Google Chrome   | Current†  |
| Microsoft Edge  | Current†  |
| Mozilla Firefox | Current†  |

Blazor Hybrid 앱의 경우, 최신 플랫폼 Web View 컨트롤 버전에서 테스트하고 지원합니다:

 - Microsoft Edge WebView2 on Windows
 - Chrome on Android
 - Safari on iOS and macOS

---
## Tooling for ASP.NET Core Blazor

이 문서에서는 다양한 플랫폼에서 Blazor 앱을 빌드하는 데 사용되는 도구를 설명합니다.

Linux 또는 macOS에서 Blazor 앱을 만들려면 다음 지침을 사용하십시오:

명령 셸에서 .NET 명령줄 인터페이스 (CLI)를 사용하여 명령을 실행합니다.

최신 버전의 .NET Core SDK를 설치하십시오. 이전에 SDK를 설치한 경우 다음 명령을 실행하여 설치된 버전을 확인할 수 있습니다:
```bash
dotnet --version
```

플랫폼에 맞는 최신 버전의 Visual Studio Code를 설치하십시오.

Visual Studio Code용 C# 개발 키트를 설치하십시오. 자세한 내용은 ASP.NET Core Blazor 앱 디버깅을 참조하십시오.

새 프로젝트 만들기:

- 기본 대화형 서버 측 렌더링을 갖는 Blazor Web App 경험을 위해 다음 명령을 사용하여 blazor 프로젝트 템플릿을 사용하는 명령 셸에서 다음 명령을 실행하십시오:
  ```bash
  dotnet new blazor -o BlazorApp
  ```
  클라이언트 측 렌더링만 활성화하려면 -int|--interactivity 옵션을 WebAssembly로 설정하십시오:
  ```bash
  dotnet new blazor -o BlazorApp -int WebAssembly
  ```
  대화형 서버 측 렌더링 다음에 클라이언트 측 렌더링을 활성화하려면 -int|--interactivity 옵션을 Auto로 설정하십시오:
  ```bash
  dotnet new blazor -o BlazorApp -int Auto
  ```
  -int|--interactivity 옵션을 None으로 설정하여 대화형을 비활성화하면 생성된 앱에 대화형이 없습니다. 앱은 정적 서버 측 렌더링에만 구성됩니다:
  ```bash
  dotnet new blazor -o BlazorApp -int None
  ```
  대화형 자동 렌더 모드는 먼저 .NET 웹 어셈블리 런타임이 브라우저에 다운로드될 때까지 대화형 서버 측 렌더링(대화형 SSR)을 사용합니다. .NET WebAssembly 런타임이 활성화되면 렌더 모드가 대화형 WebAssembly 렌더 모드로 전환됩니다.

  기본적으로 Blazor Web App 템플릿은 단일 프로젝트를 사용하여 정적 및 대화형 서버 측 렌더링을 모두 활성화합니다. 대화형 WebAssembly 렌더 모드를 활성화하는 경우 프로젝트에 웹 어셈블리 기반 구성 요소용 추가 클라이언트 프로젝트 (.Client)가 포함됩니다. 클라이언트 프로젝트에서 빌드된 출력은 브라우저에 다운로드되어 클라이언트에서 실행됩니다. 대화형 WebAssembly 또는 대화형 자동 렌더 모드를 사용하는 모든 구성 요소는 클라이언트 프로젝트에서 빌드해야 합니다.

  자세한 내용은 ASP.NET Core Blazor 렌더 모드를 참조하십시오.

  앱은 구성 요소/페이지별로 대화형 위치를 기본으로 설정합니다. 전체 앱에 대한 대화형을 설정하려면 -ai|--all-interactive 옵션을 사용하십시오:
  ```bash
  dotnet new blazor -o BlazorApp -ai
  ```
  이 옵션을 선택하면 최상위 HeadOutlet 및 Routes 구성 요소에 대한 렌더 모드를 지정하여 App 구성 요소에서 전체 앱에 대한 대화형을 설정합니다. 이러한 구성 요소에서 대화형을 설정하면 앱의 모든 하위 구성 요소에 대한 대화형이 전파됩니다.

  대화형 위치는 대화형 렌더 모드 (-int|--interactivity)가 None으로 설정되지 않았고 인증이 활성화되지 않은 경우에만 설정할 수 있습니다.

  샘플 페이지 및 스타일이 없는 앱을 만들려면 -e|--empty 옵션을 사용하십시오:
  ```bash
  dotnet new blazor -o BlazorApp -e
  ```
        
- 독립형 Blazor WebAssembly 경험을 위해 blazorwasm 템플릿을 사용하는 명령 셸에서 다음 명령을 실행하십시오:

  ```bash
  dotnet new blazorwasm -o BlazorApp
  ```
  샘플 페이지 및 스타일이 없는 독립형 Blazor WebAssembly 앱을 만들려면 -e|--empty 옵션을 사용하십시오:
  ```bash
  dotnet new blazorwasm -o BlazorApp -e
  ```

Visual Studio Code에서 BlazorApp 폴더를 엽니다.

Visual Studio Code에서 프로젝트를 빌드하고 디버그하기 위해 자산을 추가하라는 요청이 표시되면 예를 선택하십시오.

Visual Studio Code가 자동으로 빌드 및 디버그 자산을 추가하지 않는 경우 (.vscode 폴더에 launch.json 및 tasks.json 파일이 포함됨), View > Command Palette를 선택하고 검색 상자에 ".NET"을 입력하십시오. 명령 목록에서 ".NET: Generate Assets for Build and Debug" 명령을 선택하십시오.

프로젝트의 Properties/launchSettings.json 파일에는 파일의 profiles 섹션에 대한 디버깅 프록시의 inspectUri 속성이 포함되어 있습니다.
```json
"inspectUri": "{wsProtocol}://{url.hostname}:{url.port}/_framework/debug/ws-proxy?browser={browserInspectUri}",
```

### Visual Studio solution file (.sln)

솔루션은 하나 이상의 관련 코드 프로젝트를 구성하는 컨테이너입니다. Visual Studio는 솔루션에 대한 설정을 저장하기 위해 솔루션 파일 (.sln)을 사용합니다. 솔루션 파일은 고유한 형식을 사용하며 직접 편집할 목적으로 사용되지 않습니다.

Visual Studio 외부의 도구는 솔루션 파일과 상호 작용할 수 있습니다:

 - .NET CLI는 dotnet sln 명령을 통해 솔루션 파일을 생성하고 솔루션 파일 내의 프로젝트를 나열/수정할 수 있습니다. 다른 .NET CLI 명령은 다양한 게시, 테스트 및 패키지 명령에 대해 솔루션 파일의 경로를 사용합니다.
 - Visual Studio Code는 통합 터미널을 통해 dotnet sln 명령 및 다른 .NET CLI 명령을 실행할 수 있지만 솔루션 파일의 설정을 직접 사용하지 않습니다.

### Use Visual Studio Code for cross-platform Blazor development

Visual Studio Code는 오픈 소스이며, 여러 플랫폼에서 사용할 수 있는 통합 개발 환경(IDE)입니다. Visual Studio Code를 사용하여 Blazor 앱을 개발할 수 있습니다. Visual Studio Code에서 개발을 위해 새 Blazor 앱을 만들려면 .NET CLI를 사용하십시오.

### Blazor template options

Blazor 프레임워크는 새로운 앱을 생성하기 위한 템플릿을 제공합니다. 이 템플릿들은 Blazor 개발에 선택한 도구(Visual Studio, Visual Studio Code 또는 .NET 명령줄 인터페이스(CLI))에 관계없이 새로운 Blazor 프로젝트와 솔루션을 만드는 데 사용됩니다:

Blazor Web App 프로젝트 템플릿: blazor
Blazor WebAssembly Standalone 앱 프로젝트 템플릿: blazorwasm
Blazor 프로젝트 템플릿에 대한 자세한 내용은 ASP.NET Core Blazor 프로젝트 구조를 참조하십시오.

템플릿 옵션에 대한 자세한 내용은 다음 리소스를 참조하십시오:

.NET Core 문서의 dotnet new CLI 명령에 대한 .NET 기본 템플릿 문서:
- [blazor](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-new-sdk-templates#blazor)
- [blazorwasm](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-new-sdk-templates#blazorwasm)

명령 셸에서 dotnet new CLI 명령에 도움말 옵션(-h 또는 --help)을 전달하기:
- dotnet new blazor -h
- dotnet new blazorwasm -h

---
## ASP.NET Core Blazor WebAssembly build tools and ahead-of-time (AOT) compilation

이 기사에서는 독립형 Blazor WebAssembly 앱을 위한 빌드 도구와 사전 컴파일 (AOT) 컴파일을 사용하여 배포 전에 앱을 컴파일하는 방법에 대해 설명합니다.

기사는 주로 독립형 Blazor WebAssembly 앱에 중점을 두고 있지만, 일부 모바일 장치 브라우저의 힙 크기에 대한 섹션은 Blazor Web App의 클라이언트 측 프로젝트(.Client)에도 적용됩니다.

### .NET WebAssembly build tools for .NET 6 projects
.NET WebAssembly 빌드 도구는 웹 플랫폼을 위한 컴파일러 도구 체인인 Emscripten을 기반으로 합니다. 빌드 도구를 설치하려면 다음 접근 방법 중 하나를 사용하십시오:

 - Visual Studio 설치 관리자에서 ASP.NET 및 웹 개발 작업을 위해 선택 가능한 구성 요소 목록에서 .NET WebAssembly 빌드 도구 옵션을 선택합니다.
 - 관리자 명령 셸에서 `dotnet workload install wasm-tools` 명령을 실행합니다.

```
참고

.NET 6 프로젝트용 .NET WebAssembly 빌드 도구

wasm-tools 워크로드는 최신 릴리스를 위한 빌드 도구를 설치합니다. 그러나 현재 버전의 빌드 도구는 .NET 6로 빌드된 기존 프로젝트와 호환되지 않습니다. .NET 6 및 이후 릴리스를 모두 지원해야 하는 프로젝트는 다중 타겟팅을 사용해야 합니다.

.NET 7 SDK로 앱을 개발할 때는 .NET 6 프로젝트에 대해 wasm-tools-net6 워크로드를 사용하십시오. wasm-tools-net6 워크로드를 설치하려면 관리자 명령 셸에서 다음 명령을 실행하십시오:
dotnet workload install wasm-tools-net6
```

### Ahead-of-time (AOT) compilation

Blazor WebAssembly는 사전 컴파일 (AOT) 컴파일을 지원하여 .NET 코드를 직접 WebAssembly로 컴파일할 수 있습니다. AOT 컴파일은 더 큰 앱 크기와 맞바꾸어 런타임 성능을 향상시킵니다.

AOT 컴파일을 활성화하지 않으면 Blazor WebAssembly 앱은 WebAssembly로 구현된 .NET 중간 언어(IL) 인터프리터를 사용하여 브라우저에서 실행되며, 이는 부분적으로 JIT 런타임 지원을 포함하고 비공식적으로 Jiterpreter라고 합니다. .NET IL 코드가 해석되기 때문에, 앱은 서버 측 .NET JIT 런타임에서 IL 해석 없이 실행되는 것보다 일반적으로 더 느리게 실행됩니다. AOT 컴파일은 앱의 .NET 코드를 브라우저에서 네이티브 WebAssembly로 직접 컴파일하여 이 성능 문제를 해결합니다. AOT 성능 향상은 CPU 집약적인 작업을 실행하는 앱에 극적인 향상을 가져올 수 있습니다. AOT 컴파일을 사용하는 단점은 AOT로 컴파일된 앱이 IL 해석된 앱보다 일반적으로 크기가 더 크므로 처음 요청 시 클라이언트에 다운로드하는 데 더 오래 걸리는 경우가 많다는 것입니다.

.NET WebAssembly 빌드 도구 설치에 대한 안내는 ASP.NET Core Blazor WebAssembly 빌드 도구 및 사전 컴파일 (AOT) 컴파일을 참조하십시오.

WebAssembly AOT 컴파일을 활성화하려면 Blazor WebAssembly 앱의 프로젝트 파일에 \<RunAOTCompilation> 속성을 true로 설정하여 추가하십시오:

```xml
<PropertyGroup>
  <RunAOTCompilation>true</RunAOTCompilation>
</PropertyGroup>
```

앱을 WebAssembly로 컴파일하려면 앱을 게시하십시오. Release 구성으로 게시하면 .NET 중간 언어 (IL) 링크도 실행되어 게시된 앱의 크기를 줄일 수 있습니다:

```bash
dotnet publish -c Release
```

WebAssembly AOT 컴파일은 프로젝트가 게시될 때만 수행됩니다. AOT 컴파일은 개발 중 (Development 환경)에는 사용되지 않습니다. 이는 작은 프로젝트에서도 AOT 컴파일이 몇 분이 걸리고 큰 프로젝트에서는 훨씬 더 오래 걸릴 수 있기 때문입니다. AOT 컴파일의 빌드 시간을 줄이는 작업은 ASP.NET Core의 향후 릴리스에서 개발 중입니다.

AOT로 컴파일된 Blazor WebAssembly 앱의 크기는 .NET IL로 컴파일된 앱의 크기보다 일반적으로 큽니다:

앱에 따라 크기 차이는 다르지만 대부분의 AOT로 컴파일된 앱은 IL로 컴파일된 버전의 약 두 배 정도 크기입니다. 이는 AOT 컴파일을 사용하면 로드 시간 성능과 런타임 성능을 맞바꾸는 것입니다. 이 거래가 AOT 컴파일을 사용하는 가치가 있는지는 앱에 따라 다릅니다. CPU 집약적인 Blazor WebAssembly 앱은 AOT 컴파일에서 가장 많은 혜택을 얻습니다.

AOT로 컴파일된 앱의 크기가 큰 이유는 두 가지 조건 때문입니다:

고수준 .NET IL 명령을 네이티브 WebAssembly로 표현하는 데 더 많은 코드가 필요합니다.
앱이 게시될 때 AOT는 관리되는 DLL을 트림하지 않습니다. Blazor는 반사 메타데이터와 특정 .NET 런타임 기능을 지원하기 위해 DLL을 필요로 합니다. 클라이언트에서 DLL을 요구하면 다운로드 크기가 증가하지만 더 호환성 있는 .NET 경험을 제공합니다.

### Trim .NET IL after ahead-of-time (AOT) compilation

WasmStripILAfterAOT MSBuild 옵션은 WebAssembly로 AOT 컴파일을 수행한 후 컴파일된 메서드의 .NET 중간 언어(IL)를 제거하여 _framework 폴더의 크기를 줄이는 기능을 활성화합니다.

앱의 프로젝트 파일에서:

```xml
<PropertyGroup>
  <RunAOTCompilation>true</RunAOTCompilation>
  <WasmStripILAfterAOT>true</WasmStripILAfterAOT>
</PropertyGroup>
```

이 설정은 라이브러리의 메서드와 앱의 메서드를 포함하여 대부분의 컴파일된 메서드에 대한 IL 코드를 제거합니다. 일부 컴파일된 메서드는 .NET 인터프리터가 런타임에 여전히 필요하기 때문에 제거할 수 없습니다.

트리밍 옵션과 관련된 문제를 보고하려면 dotnet/runtime GitHub 리포지토리에 문제를 등록하십시오.

트리밍 속성이 앱이 정상적으로 실행되는 것을 방해하는 경우 이 속성을 비활성화하십시오:

```xml
<WasmStripILAfterAOT>false</WasmStripILAfterAOT>
```

### Heap size for some mobile device browsers

클라이언트에서 실행되고 모바일 장치 브라우저, 특히 iOS의 Safari를 대상으로 하는 Blazor 앱을 빌드할 때 MSBuild 속성 EmccMaximumHeapSize를 사용하여 앱의 최대 메모리를 줄여야 할 수 있습니다. 자세한 내용은 ASP.NET Core Blazor WebAssembly 호스트 및 배포를 참조하십시오.

### Runtime relinking

Blazor WebAssembly 앱의 가장 큰 부분 중 하나는 사용자가 브라우저를 통해 처음으로 앱에 접근할 때 브라우저가 다운로드해야 하는 WebAssembly 기반 .NET 런타임(dotnet.wasm)입니다. .NET WebAssembly 런타임을 재링크하면 사용되지 않는 런타임 코드를 트림하여 다운로드 속도를 향상시킬 수 있습니다.

런타임 재링크를 위해서는 .NET WebAssembly 빌드 도구를 설치해야 합니다. 자세한 내용은 ASP.NET Core Blazor 도구를 참조하십시오.

.NET WebAssembly 빌드 도구가 설치된 상태에서, 릴리스 구성으로 앱을 게시할 때 런타임 재링크가 자동으로 수행됩니다. 특히 글로벌화 기능을 비활성화할 때 크기 감소가 두드러집니다. 자세한 내용은 ASP.NET Core Blazor 글로벌화 및 현지화를 참조하십시오.

### Single Instruction, Multiple Data (SIMD)

WebAssembly 단일 명령, 다중 데이터(SIMD)는 단일 명령을 사용하여 여러 데이터 조각에 대해 병렬로 연산을 수행함으로써 벡터화된 계산의 처리량을 향상시킬 수 있습니다. SIMD는 기본적으로 활성화되어 있습니다.

SIMD를 비활성화하려면, 예를 들어 SIMD를 지원하지 않는 구형 브라우저나 모바일 장치의 브라우저를 대상으로 할 때, 앱의 프로젝트 파일(.csproj)에서 <WasmEnableSIMD> 속성을 false로 설정하십시오:

```xml
<PropertyGroup>
  <WasmEnableSIMD>false</WasmEnableSIMD>
</PropertyGroup>
```

자세한 내용은 .NET WebAssembly 응용 프로그램 구성 및 호스팅: SIMD - 단일 명령, 다중 데이터를 참조하십시오. 이 가이드는 버전이 지정되지 않으며 최신 공개 릴리스에 적용됩니다.

### Exception handling

예외 처리는 기본적으로 활성화되어 있습니다. 예외 처리를 비활성화하려면, 앱의 프로젝트 파일(.csproj)에 <WasmEnableExceptionHandling> 속성을 false 값으로 추가하십시오:

```xml
<PropertyGroup>
  <WasmEnableExceptionHandling>false</WasmEnableExceptionHandling>
</PropertyGroup>
```
---
## ASP.NET Core Blazor hosting models

이 기사는 Blazor 호스팅 모델에 대해 설명하며, 주로 .NET 8 이전 버전의 Blazor Server 및 Blazor WebAssembly 앱에 중점을 둡니다. 이 기사에서 제공하는 지침은 네이티브 모바일 및 데스크톱 플랫폼에서 실행되는 Blazor Hybrid 앱의 모든 .NET 릴리스에 적용됩니다. .NET 8 이상에서 Blazor Web Apps는 Razor 구성 요소가 렌더링되는 방식으로 개념화하는 것이 더 좋습니다. 이는 렌더 모드라고 설명됩니다. 렌더 모드에 대해서는 기본 개요 기사에서 간략하게 다루고 있으며, ASP.NET Core Blazor 렌더 모드의 Components 노드에서 자세히 다루고 있습니다.

Blazor는 웹 UI 구성 요소(Razor 구성 요소)를 구축하기 위한 웹 프레임워크로, 다양한 방식으로 호스팅될 수 있습니다. Razor 구성 요소는 ASP.NET Core(Blazor Server)에서 서버 측에서 실행되거나 WebAssembly 기반 .NET 런타임(Blazor WebAssembly, Blazor WASM)에서 브라우저의 클라이언트 측에서 실행될 수 있습니다. 또한, 네이티브 모바일 및 데스크톱 앱에서 임베디드 Web View 컨트롤에 렌더링되어 호스팅될 수도 있습니다(Blazor Hybrid). 호스팅 모델에 관계없이 Razor 구성 요소를 빌드하는 방법은 동일합니다. 동일한 Razor 구성 요소는 변경 없이 어떤 호스팅 모델에서도 사용할 수 있습니다.

### Blazor Server

Blazor Server 호스팅 모델을 사용하면 구성 요소가 ASP.NET Core 앱 내에서 서버에서 실행됩니다. UI 업데이트, 이벤트 처리, JavaScript 호출은 WebSockets 프로토콜을 사용하는 SignalR 연결을 통해 처리됩니다. 각 연결된 클라이언트와 관련된 서버의 상태를 회로(circuit)라고 합니다. 회로는 특정 네트워크 연결에 묶여 있지 않으며 일시적인 네트워크 중단과 연결이 끊어졌을 때 클라이언트가 서버에 다시 연결하려는 시도를 허용합니다.

전통적인 서버 렌더링 앱에서는 여러 브라우저 화면(탭 또는 iframes)에서 동일한 앱을 여는 것이 서버에 추가적인 자원 요구를 일으키지 않는 경우가 많습니다. 그러나 Blazor Server 호스팅 모델에서는 각 브라우저 화면이 별도의 회로와 서버에서 관리되는 구성 요소 상태의 별도 인스턴스를 필요로 합니다. Blazor는 브라우저 탭을 닫거나 외부 URL로 이동하는 것을 우아한 종료로 간주합니다. 우아한 종료가 발생하면 회로와 관련된 자원이 즉시 해제됩니다. 클라이언트는 또한 네트워크 중단과 같은 이유로 비우아하게 연결이 끊어질 수 있습니다. Blazor Server는 클라이언트가 다시 연결할 수 있도록 구성 가능한 간격 동안 연결이 끊긴 회로를 저장합니다.

![](../img/03_Blazor_소개/blazor-server.png)

클라이언트에서는 Blazor 스크립트가 서버와 SignalR 연결을 설정합니다. 이 스크립트는 ASP.NET Core 공유 프레임워크의 임베디드 리소스에서 제공됩니다.

Blazor Server 호스팅 모델은 여러 가지 이점을 제공합니다:

- Blazor WebAssembly 호스팅 모델을 사용할 때보다 다운로드 크기가 상당히 작고, 앱이 훨씬 빠르게 로드됩니다.
- 앱은 .NET Core API 사용을 포함하여 서버 기능을 최대한 활용합니다.
- 서버에서 .NET Core를 사용하여 앱을 실행하므로 디버깅과 같은 기존 .NET 도구를 예상대로 사용할 수 있습니다.
- 가벼운 클라이언트를 지원합니다. 예를 들어, Blazor Server는 WebAssembly를 지원하지 않는 브라우저와 자원이 제한된 장치에서도 작동합니다.
- 앱의 .NET/C# 코드 베이스, 포함된 구성 요소 코드는 클라이언트에 제공되지 않습니다.

Blazor Server 호스팅 모델에는 다음과 같은 제한 사항이 있습니다:

- 보통 더 높은 대기 시간이 존재합니다. 모든 사용자 상호 작용에는 네트워크 홉이 필요합니다.
- 오프라인 지원이 없습니다. 클라이언트 연결이 실패하면 상호 작용도 실패합니다.
- 많은 사용자가 있는 앱을 확장하려면 여러 클라이언트 연결과 클라이언트 상태를 처리하기 위한 서버 리소스가 필요합니다.
- 앱을 제공하려면 ASP.NET Core 서버가 필요합니다. 콘텐츠 배포 네트워크(CDN)에서 앱을 제공하는 것과 같은 서버리스 배포 시나리오는 불가능합니다.

Blazor Server 호스팅 모델을 채택한 앱에는 Azure SignalR 서비스를 사용하는 것이 좋습니다. 이 서비스는 많은 수의 동시 SignalR 연결로 Blazor Server 앱을 확장할 수 있도록 합니다.

### Blazor WebAssembly

Blazor WebAssembly 호스팅 모델은 WebAssembly 기반 .NET 런타임에서 브라우저의 클라이언트 측에서 구성 요소를 실행합니다. Razor 구성 요소, 그 종속성 및 .NET 런타임이 브라우저에 다운로드됩니다. 구성 요소는 브라우저 UI 스레드에서 직접 실행됩니다. UI 업데이트와 이벤트 처리는 동일한 프로세스 내에서 발생합니다. 애셋은 정적 콘텐츠를 클라이언트에 제공할 수 있는 웹 서버 또는 서비스에 정적 파일로 배포됩니다.

![](../img/03_Blazor_소개/blazor-webassembly.png)

Blazor 웹 앱은 Blazor WebAssembly 호스팅 모델을 사용하여 클라이언트 측 상호 작용을 활성화할 수 있습니다. 서버 측 렌더링 및 상호 작용 없이 Blazor WebAssembly 호스팅 모델에서만 실행되는 앱은 독립형 Blazor WebAssembly 앱이라고 합니다.

독립형 Blazor WebAssembly 앱이 백엔드 ASP.NET Core 앱을 사용하여 파일을 제공할 때, 이 앱은 호스팅된 Blazor WebAssembly 앱이라고 합니다. 호스팅된 Blazor WebAssembly를 사용하면 클라이언트와 서버 앱 간의 코드 공유, 사전 렌더링 지원 및 MVC와 Razor Pages와의 통합을 포함한 .NET을 통한 풀 스택 웹 개발 경험을 얻을 수 있습니다. 호스팅된 클라이언트 앱은 웹 API, gRPC-web, SignalR(Blazor와 함께 ASP.NET Core SignalR 사용)과 같은 다양한 메시징 프레임워크 및 프로토콜을 사용하여 백엔드 서버 앱과 네트워크를 통해 상호 작용할 수 있습니다.

Progressive Web App(PWA)로 구축된 Blazor WebAssembly 앱은 최신 브라우저 API를 사용하여 오프라인 작업, 자체 앱 창에서 실행, 호스트 운영 체제에서 시작, 푸시 알림 수신 및 백그라운드에서 자동 업데이트와 같은 네이티브 클라이언트 앱의 많은 기능을 활성화합니다.

Blazor 스크립트는 다음을 처리합니다:

- .NET 런타임, Razor 구성 요소 및 구성 요소의 종속성을 다운로드합니다.
- 런타임 초기화를 수행합니다.

게시된 앱의 크기, 즉 페이로드 크기는 앱 사용성에 중요한 성능 요소입니다. 큰 앱은 브라우저에 다운로드하는 데 상대적으로 오랜 시간이 걸리며, 이는 사용자 경험을 저하시킵니다. Blazor WebAssembly는 다운로드 시간을 줄이기 위해 페이로드 크기를 최적화합니다:

- 사용되지 않는 코드는 중간 언어(IL) 트리머에 의해 앱에서 제거됩니다.
- HTTP 응답이 압축됩니다.
- .NET 런타임과 어셈블리는 브라우저에 캐시됩니다.

Blazor WebAssembly 호스팅 모델은 여러 가지 이점을 제공합니다:

- 독립형 Blazor WebAssembly 앱의 경우, 앱이 서버에서 다운로드된 후에는 .NET 서버 측 종속성이 없으므로 서버가 오프라인 상태가 되어도 앱이 기능을 유지합니다.
- 클라이언트 리소스와 기능이 완전히 활용됩니다.
- 작업이 서버에서 클라이언트로 오프로드됩니다.
- 독립형 Blazor WebAssembly 앱의 경우, 앱을 호스팅하기 위해 ASP.NET Core 웹 서버가 필요하지 않습니다. 콘텐츠 배포 네트워크(CDN)에서 앱을 제공하는 것과 같은 서버리스 배포 시나리오가 가능합니다.

Blazor WebAssembly 호스팅 모델에는 다음과 같은 제한 사항이 있습니다:

- Razor 구성 요소는 브라우저의 기능에 제한됩니다.
- 유능한 클라이언트 하드웨어 및 소프트웨어(예: WebAssembly 지원)가 필요합니다.
- 다운로드 크기가 더 크고 구성 요소 로드 시간이 더 오래 걸립니다.
- 클라이언트에 전송된 코드는 사용자가 검사하고 조작하는 것으로부터 보호될 수 없습니다.
- .NET 중간 언어(IL) 인터프리터는 런타임 성능을 향상시키기 위해 부분적인 Just-in-Time (JIT) 런타임 지원을 포함합니다. JIT 인터프리터는 해석기 바이트코드를 작은 WebAssembly 코드 블록으로 대체하여 실행을 최적화합니다. JIT 인터프리터는 디버깅할 때를 제외하고 Blazor WebAssembly 앱에 자동으로 활성화됩니다.

Blazor는 사전 컴파일(AOT) 컴파일을 지원하여 .NET 코드를 직접 WebAssembly로 컴파일할 수 있습니다. AOT 컴파일은 더 큰 앱 크기와 맞바꾸어 런타임 성능을 향상시킵니다. 자세한 내용은 ASP.NET Core Blazor WebAssembly 빌드 도구 및 사전 컴파일(AOT) 컴파일을 참조하십시오.

AOT 컴파일에 사용되는 동일한 .NET WebAssembly 빌드 도구는 사용되지 않는 런타임 코드를 트림하기 위해 .NET WebAssembly 런타임을 재링크합니다. Blazor는 또한 .NET 프레임워크 라이브러리에서 사용되지 않는 코드를 트림합니다. .NET 컴파일러는 독립형 Blazor WebAssembly 앱을 더 작은 앱 페이로드로 사전 압축합니다.

WebAssembly로 렌더링된 Razor 구성 요소는 WebAssembly에서 실행되도록 빌드된 네이티브 종속성을 사용할 수 있습니다.

### Blazor Hybrid

Blazor는 하이브리드 접근 방식을 사용하여 네이티브 클라이언트 앱을 구축하는 데도 사용할 수 있습니다. 하이브리드 앱은 기능을 위해 웹 기술을 활용하는 네이티브 앱입니다. Blazor Hybrid 앱에서는 Razor 구성 요소가 다른 .NET 코드와 함께 네이티브 앱에서 직접 실행되며, 로컬 상호 운용 채널을 통해 HTML 및 CSS 기반의 웹 UI를 임베디드 Web View 컨트롤에 렌더링합니다.

![](../img/03_Blazor_소개/hybrid-apps-1.png)

Blazor 하이브리드 앱은 .NET MAUI, WPF, Windows Forms를 포함한 다양한 .NET 네이티브 앱 프레임워크를 사용하여 구축할 수 있습니다. Blazor는 이러한 프레임워크로 구축된 앱에 Razor 구성 요소를 추가하기 위한 BlazorWebView 컨트롤을 제공합니다. .NET MAUI를 사용하여 Blazor와 함께 크로스 플랫폼 Blazor 하이브리드 앱을 모바일 및 데스크톱용으로 쉽게 빌드할 수 있으며, WPF 및 Windows Forms와의 Blazor 통합은 기존 앱을 현대화하는 훌륭한 방법이 될 수 있습니다.

Blazor 하이브리드 앱은 네이티브 앱이기 때문에 웹 플랫폼만으로는 제공되지 않는 기능을 지원할 수 있습니다. Blazor 하이브리드 앱은 일반 .NET API를 통해 네이티브 플랫폼 기능에 완전히 접근할 수 있습니다. 또한 Blazor 하이브리드 앱은 기존 Blazor Server 또는 Blazor WebAssembly 앱과 구성 요소를 공유하고 재사용할 수 있습니다. Blazor 하이브리드 앱은 웹, 네이티브 앱, .NET 플랫폼의 이점을 결합합니다.

Blazor 하이브리드 호스팅 모델은 여러 가지 이점을 제공합니다:

- 모바일, 데스크톱 및 웹에서 공유할 수 있는 기존 구성 요소를 재사용할 수 있습니다.
- 웹 개발 기술, 경험 및 자원을 활용할 수 있습니다.
- 앱은 장치의 네이티브 기능에 완전히 접근할 수 있습니다.

Blazor 하이브리드 호스팅 모델에는 다음과 같은 제한 사항이 있습니다:

- 각 대상 플랫폼에 대해 별도의 네이티브 클라이언트 앱을 빌드, 배포 및 유지 관리해야 합니다.
- 네이티브 클라이언트 앱은 일반적으로 브라우저에서 웹 앱에 접근하는 것보다 찾고, 다운로드하고, 설치하는 데 시간이 더 오래 걸립니다.

자세한 내용은 ASP.NET Core Blazor Hybrid를 참조하십시오.

Microsoft 네이티브 클라이언트 프레임워크에 대한 자세한 내용은 다음 자료를 참조하십시오:

- .NET Multi-platform App UI (.NET MAUI)
- Windows Presentation Foundation (WPF)
- Windows Forms

### Which Blazor hosting model should I choose?

구성 요소의 호스팅 모델은 컴파일 시간 또는 런타임에 렌더 모드에 의해 설정됩니다. 이는 ASP.NET Core Blazor 렌더 모드 예제에서 설명됩니다. 다음 표는 구성 요소의 호스팅 모델을 결정하기 위해 렌더 모드를 설정할 때 주요 고려 사항을 보여줍니다. 독립형 Blazor WebAssembly 앱의 경우, 모든 앱 구성 요소는 Blazor WebAssembly 호스팅 모델을 사용하여 클라이언트에서 렌더링됩니다.

Blazor 하이브리드 앱에는 .NET MAUI, WPF, Windows Forms 프레임워크 앱이 포함됩니다.

| Feature                                        | Blazor Server  | Blazor WebAssembly (WASM) | Blazor Hybrid    |
|------------------------------------------------|----------------|---------------------------|------------------|
| Complete .NET API compatibility                | ✔️Supported    | ❌Not supported            | ✔️Supported      |
| Direct access to server and network resources  | ✔️Supported    | ❌Not supported†           | ❌Not supported†  |
| Small payload size with fast initial load time | ✔️Supported    | ❌Not supported            | ❌Not supported   |
| Near native execution speed                    | ✔️Supported    | ✔️Supported‡              | ✔️Supported      |
| App code secure and private on the server      | ✔️Supported    | ❌Not supported†           | ❌Not supported†  |
| Run apps offline once downloaded               | ❌Not supported | ✔️Supported               | ✔️Supported      |
| Static site hosting                            | ❌Not supported | ✔️Supported               | ❌Not supported   |
| Offloads processing to clients                 | ❌Not supported | ✔️Supported               | ✔️Supported      |
| Full access to native client capabilities      | ❌Not supported | ❌Not supported            | ✔️Supported      |
| Web-based deployment                           | ✔️Supported    | ✔️Supported               | ❌                |

### Complete .NET API compatibility

Blazor Server 호스팅 모델과 Blazor 하이브리드 앱을 위해 렌더링된 구성 요소는 완전한 .NET API 호환성을 가지지만, Blazor WebAssembly를 위해 렌더링된 구성 요소는 .NET API의 일부 집합에만 제한됩니다. 앱의 사양에서 WebAssembly로 렌더링된 구성 요소에서 사용할 수 없는 하나 이상의 .NET API가 필요할 때는 Blazor Server를 위해 구성 요소를 렌더링하거나 Blazor 하이브리드를 사용하십시오.

### Direct access to server and network resources

Blazor Server 호스팅 모델을 위해 렌더링된 구성 요소는 앱이 실행되는 서버 및 네트워크 리소스에 직접 접근할 수 있습니다. Blazor WebAssembly나 Blazor 하이브리드를 사용하여 호스팅된 구성 요소는 클라이언트에서 실행되기 때문에 서버 및 네트워크 리소스에 직접 접근할 수 없습니다. 구성 요소는 보호된 서버 기반 API를 통해 간접적으로 서버 및 네트워크 리소스에 접근할 수 있습니다. 서버 기반 API는 서드 파티 라이브러리, 패키지 및 서비스를 통해 제공될 수 있습니다. 다음 고려 사항을 염두에 두십시오:

- 서드 파티 라이브러리, 패키지 및 서비스는 구현 및 유지 관리 비용이 많이 들고, 지원이 약하거나 보안 위험을 초래할 수 있습니다.
- 하나 이상의 서버 기반 API가 귀 조직에서 내부적으로 개발되는 경우, 이를 구축하고 유지 관리하기 위해 추가 리소스가 필요합니다.

서버 환경에서 API를 노출할 필요가 없도록 Blazor Server 호스팅 모델을 사용하십시오.

### Small payload size with fast initial load time

서버에서 구성 요소를 렌더링하면 앱 페이로드 크기가 줄어들고 초기 로드 시간이 개선됩니다. 빠른 초기 로드 시간이 필요한 경우 Blazor Server 호스팅 모델을 사용하거나 정적 서버 측 렌더링을 고려하십시오.

### Near native execution speed

Blazor 하이브리드 앱은 대상 플랫폼에서 .NET 런타임을 네이티브로 실행하여 가능한 최고의 속도를 제공합니다.

Blazor WebAssembly 호스팅 모델(Progressive Web Apps(PWAs) 포함)을 위해 렌더링된 구성 요소와 독립형 Blazor WebAssembly 앱은 WebAssembly용 .NET 런타임을 사용하여 실행되며, 이는 플랫폼에서 직접 실행되는 것보다 느립니다. Blazor WebAssembly를 사용할 때 런타임 성능을 향상시키기 위해 사전 컴파일(AOT)을 사용하는 것을 고려하십시오.

### App code secure and private on the server

Blazor Server 호스팅 모델을 위해 렌더링된 구성 요소의 기본 기능으로 앱 코드를 안전하고 비공개로 서버에 유지할 수 있습니다. Blazor WebAssembly나 Blazor 하이브리드 호스팅 모델을 사용하여 렌더링된 구성 요소는 서버 기반 API를 사용하여 비공개 및 안전하게 유지해야 하는 기능에 접근할 수 있습니다. 서버 및 네트워크 리소스에 대한 직접 접근 섹션에서 설명한 서버 기반 API의 개발 및 유지 관리에 대한 고려 사항이 적용됩니다. 안전하고 비공개로 앱 코드를 유지하기 위해 서버 기반 API의 개발 및 유지 관리가 바람직하지 않은 경우, Blazor Server 호스팅 모델을 위해 구성 요소를 렌더링하십시오.

### Run apps offline once downloaded

Progressive Web Apps(PWAs)로 빌드된 독립형 Blazor WebAssembly 앱과 Blazor 하이브리드 앱은 오프라인에서 실행될 수 있으며, 이는 클라이언트가 인터넷에 연결할 수 없을 때 특히 유용합니다. Blazor Server 호스팅 모델로 렌더링된 구성 요소는 서버와의 연결이 끊어지면 실행에 실패합니다. 앱이 반드시 오프라인에서 실행되어야 하는 경우, 독립형 Blazor WebAssembly와 Blazor 하이브리드가 가장 좋은 선택입니다.

### Static site hosting

독립형 Blazor WebAssembly 앱은 정적 파일 세트로 클라이언트에 다운로드되기 때문에 정적 사이트 호스팅이 가능합니다. 독립형 Blazor WebAssembly 앱은 서버에서 서버 측 코드를 실행할 필요 없이 다운로드 및 실행할 수 있으며, Azure CDN과 같은 콘텐츠 배포 네트워크(CDN)를 통해 제공될 수 있습니다.

Blazor 하이브리드 앱은 하나 이상의 독립 실행형 배포 자산으로 컴파일되지만, 자산은 일반적으로 타사 앱 스토어를 통해 클라이언트에 제공됩니다. 정적 호스팅이 앱 요구 사항인 경우, 독립형 Blazor WebAssembly를 선택하십시오.


### Offloads processing to clients

Blazor WebAssembly와 Blazor 하이브리드 앱은 클라이언트에서 실행되므로 처리를 클라이언트로 오프로드합니다. Blazor Server 앱은 서버에서 실행되므로 사용자 수와 사용자당 필요한 처리량에 따라 서버 자원 수요가 증가합니다. 앱의 대부분 또는 모든 처리를 클라이언트로 오프로드할 수 있고, 앱이 상당한 양의 데이터를 처리하는 경우 Blazor WebAssembly나 Blazor 하이브리드가 가장 좋은 선택입니다.

### Full access to native client capabilities

Blazor 하이브리드 앱은 .NET 네이티브 앱 프레임워크를 통해 네이티브 클라이언트 API 기능에 완전히 접근할 수 있습니다. Blazor 하이브리드 앱에서는 Razor 구성 요소가 WebAssembly가 아닌 네이티브 앱에서 직접 실행됩니다. 클라이언트 기능이 필수 요구 사항인 경우, Blazor 하이브리드가 가장 좋은 선택입니다.

### Web-based deployment

Blazor 웹 앱은 브라우저에서 다음 앱 새로 고침 시 업데이트됩니다.

Blazor 하이브리드 앱은 일반적으로 설치 프로그램과 플랫폼별 배포 메커니즘이 필요한 네이티브 클라이언트 앱입니다.

### Setting a component's hosting model

구성 요소의 호스팅 모델을 컴파일 시간 또는 런타임에 Blazor Server 또는 Blazor WebAssembly로 설정하려면 렌더 모드를 설정합니다. 렌더 모드는 ASP.NET Core Blazor 렌더 모드 기사에서 완전히 설명되고 시연됩니다. 이 기사에서 렌더 모드 기사로 직접 이동하기 전에 두 기사 사이의 내용을 읽는 것이 좋습니다. 예를 들어, 렌더 모드는 Razor 구성 요소 예제를 통해 더 쉽게 이해할 수 있지만, 기본적인 Razor 구성 요소 구조와 기능은 ASP.NET Core Blazor 기초 기사에 도달할 때까지 다루지 않습니다. 구성 요소 예제를 렌더 모드 기사에서 다루기 전에 Blazor의 프로젝트 템플릿과 도구에 대해 배우는 것도 유용합니다.

---
## ASP.NET Core Blazor Hybrid

이 기사는 ASP.NET Core 앱에서 .NET을 사용하여 인터랙티브 클라이언트 측 웹 UI를 구축하는 방법인 ASP.NET Core Blazor Hybrid에 대해 설명합니다.

Blazor Hybrid를 사용하여 .NET과 Blazor로 데스크톱 및 모바일 네이티브 클라이언트 프레임워크를 결합하십시오.

Blazor Hybrid 앱에서는 Razor 구성 요소가 장치에서 네이티브로 실행됩니다. 구성 요소는 로컬 상호 운용 채널을 통해 임베디드 Web View 컨트롤에 렌더링됩니다. 구성 요소는 브라우저에서 실행되지 않으며 WebAssembly도 사용되지 않습니다. Razor 구성 요소는 코드를 빠르게 로드하고 실행하며, .NET 플랫폼을 통해 장치의 네이티브 기능에 완전히 접근할 수 있습니다. Web View에서 렌더링된 구성 요소 스타일은 플랫폼에 따라 다르며, 사용자 정의 스타일시트를 사용하여 플랫폼 간 렌더링 차이를 고려해야 할 수도 있습니다.

Blazor Hybrid 기사는 Razor 구성 요소를 네이티브 클라이언트 프레임워크에 통합하는 것과 관련된 주제를 다룹니다.

### Blazor Hybrid apps with .NET MAUI

Blazor Hybrid 지원은 .NET Multi-platform App UI(.NET MAUI) 프레임워크에 내장되어 있습니다. .NET MAUI에는 Razor 구성 요소를 임베디드 Web View에 렌더링할 수 있는 BlazorWebView 컨트롤이 포함되어 있습니다. .NET MAUI와 Blazor를 함께 사용하면 하나의 웹 UI 구성 요소 세트를 모바일, 데스크톱 및 웹에서 재사용할 수 있습니다.

### Blazor Hybrid apps with WPF and Windows Forms

Blazor 하이브리드 앱은 Windows Presentation Foundation(WPF) 및 Windows Forms로 구축할 수 있습니다. Blazor는 두 프레임워크(WPF BlazorWebView, Windows Forms BlazorWebView) 모두를 위한 BlazorWebView 컨트롤을 제공합니다. Razor 구성 요소는 Windows 데스크톱에서 네이티브로 실행되고 임베디드 Web View에 렌더링됩니다. WPF 및 Windows Forms에서 Blazor를 사용하면 기존 Windows 데스크톱 앱에 새로운 UI를 추가할 수 있으며, 이를 .NET MAUI나 웹에서 플랫폼 간 재사용할 수 있습니다.

### Web View configuration

Blazor Hybrid는 BlazorWebView 컨트롤의 이벤트를 통해 다양한 플랫폼의 기본 Web View 구성을 노출합니다:

- BlazorWebViewInitializing은 각 플랫폼에서 Web View를 생성하는 데 사용되는 설정에 접근할 수 있도록 합니다. 설정이 사용 가능한 경우에 해당합니다.
- BlazorWebViewInitialized는 Web View에 접근하여 설정을 추가로 구성할 수 있도록 합니다.

각 플랫폼에서 이벤트 핸들러를 이벤트에 연결하여 사용자 지정 코드를 실행하려면 선호하는 패턴을 사용하십시오.

- .NET MAUI
  - BlazorWebViewInitializing
  - BlazorWebViewInitialized
- WPF
  - BlazorWebViewInitializing
  - BlazorWebViewInitialized
- Windows Forms
  - BlazorWebViewInitializing
  - BlazorWebViewInitialized

### Unhandled exceptions in Windows Forms and WPF apps

이 섹션은 Windows Forms 및 WPF Blazor 하이브리드 앱에만 적용됩니다.

System.AppDomain.CurrentDomain 속성에서 UnhandledException에 대한 콜백을 만드십시오. 다음 예제는 컴파일러 지시문을 사용하여 오류가 발생했음을 사용자에게 알리거나 오류 정보를 개발자에게 보여주는 MessageBox를 표시합니다. 오류 정보는 error.ExceptionObject에 기록됩니다.

```csharp
AppDomain.CurrentDomain.UnhandledException += (sender, error) =>
{
#if DEBUG
    MessageBox.Show(text: error.ExceptionObject.ToString(), caption: "Error");
#else
    MessageBox.Show(text: "An error has occurred.", caption: "Error");
#endif
    
    // Log the error information (error.ExceptionObject)
};
```

### Globalization and localization

이 섹션은 .NET MAUI Blazor 하이브리드 앱에만 적용됩니다.

.NET MAUI는 장치의 환경 정보를 기반으로 CurrentCulture와 CurrentUICulture를 구성합니다.

Microsoft.Extensions.Localization 네임스페이스의 IStringLocalizer 및 기타 API는 일반적으로 예상대로 작동하며, 사용자의 문화에 따라 글로벌화된 형식 지정, 파싱 및 바인딩도 함께 작동합니다.

런타임에 앱의 문화를 동적으로 변경할 때, 문화를 반영하려면 앱을 다시 로드해야 합니다. 이렇게 하면 루트 구성 요소를 다시 렌더링하고 새 문화를 다시 렌더링된 자식 구성 요소에 전달하는 작업이 처리됩니다.

.NET의 리소스 시스템은 로컬라이즈된 이미지를(블롭 형태로) 앱에 임베드하는 것을 지원하지만, Blazor 하이브리드는 현재 Razor 구성 요소에서 임베드된 이미지를 표시할 수 없습니다. 사용자가 ResourceManager를 사용하여 이미지의 바이트를 스트림으로 읽더라도 프레임워크는 현재 Razor 구성 요소에서 가져온 이미지를 렌더링하는 것을 지원하지 않습니다.

플랫폼별로 로컬라이즈된 이미지를 포함시키는 접근 방식은 .NET의 리소스 시스템의 기능이지만, .NET MAUI Blazor 하이브리드 앱의 Razor 구성 요소의 브라우저 요소는 이러한 이미지와 상호작용할 수 없습니다.

자세한 내용은 다음 자료를 참조하십시오:

- Xamarin.Forms 문자열 및 이미지 로컬라이제이션: 이 지침은 일반적으로 Blazor 하이브리드 앱에 적용됩니다. 현재 모든 시나리오가 지원되는 것은 아닙니다.
- HTTP 엔드포인트를 통해 접근할 수 없는 이미지를 표시하기 위한 Blazor 이미지 구성 요소 (dotnet/aspnetcore #25274)

### Access scoped services from native UI

BlazorWebView에는 TryDispatchAsync 메서드가 있으며, 지정된 Action\<ServiceProvider>를 비동기적으로 호출하고 Razor 구성 요소에서 사용 가능한 범위 서비스(scoped services)를 전달합니다. 이를 통해 네이티브 UI에서 NavigationManager와 같은 범위 서비스에 접근할 수 있습니다:

```csharp
private async void MyMauiButtonHandler(object sender, EventArgs e)
{
    var wasDispatchCalled = await _blazorWebView.TryDispatchAsync(sp =>
    {
        var navMan = sp.GetRequiredService<NavigationManager>();
        navMan.CallSomeNavigationApi(...);
    });

    if (!wasDispatchCalled)
    {
        ...
    }
}
```

wasDispatchCalled가 false인 경우, 호출이 디스패치되지 않은 경우에 대한 대책을 고려하십시오. 일반적으로 디스패치가 실패해서는 안 됩니다. 실패하는 경우 OS 리소스가 고갈되었을 수 있습니다. 리소스가 고갈된 경우 메시지를 로깅하고, 예외를 던지며, 사용자에게 경고하는 것을 고려하십시오.

---
## ASP.NET Core Blazor project structure

이 기사에서는 Blazor 프로젝트 템플릿에서 생성된 Blazor 앱을 구성하는 파일 및 폴더에 대해 설명합니다.

### Blazor Web App

Blazor 웹 앱 프로젝트 템플릿: blazor

Blazor 웹 앱 프로젝트 템플릿은 서버 측 렌더링 및 클라이언트 측 렌더링 모두를 위해 Razor 구성 요소를 사용하여 웹 UI 스타일을 구축할 수 있는 단일 시작점을 제공합니다. 이 템플릿은 기존의 Blazor Server 및 Blazor WebAssembly 호스팅 모델의 장점을 결합하여 서버 측 렌더링, 스트리밍 렌더링, 향상된 탐색 및 폼 처리, 그리고 구성 요소별로 Blazor Server 또는 Blazor WebAssembly를 사용하여 상호 작용을 추가할 수 있는 기능을 제공합니다.

앱 생성 시 클라이언트 측 렌더링(CSR)과 상호 작용 서버 측 렌더링(interactive SSR)을 모두 선택한 경우, 프로젝트 템플릿은 Interactive Auto 렌더 모드를 사용합니다. 자동 렌더링 모드는 .NET 앱 번들과 런타임이 브라우저에 다운로드되는 동안 초기에는 interactive SSR을 사용합니다. .NET WebAssembly 런타임이 활성화된 후에는 렌더링이 CSR로 전환됩니다.

기본적으로 Blazor 웹 앱 템플릿은 단일 프로젝트를 사용하여 정적 및 상호 작용 서버 측 렌더링을 모두 활성화합니다. 상호 작용 WebAssembly 렌더링도 활성화하는 경우, 프로젝트에는 WebAssembly 기반 구성 요소를 위한 추가 클라이언트 프로젝트(.Client)가 포함됩니다. 클라이언트 프로젝트에서 빌드된 출력은 브라우저에 다운로드되어 클라이언트에서 실행됩니다. 상호 작용 WebAssembly 또는 Interactive Auto 렌더 모드를 사용하는 구성 요소는 .Client 프로젝트에 위치해야 합니다.

자세한 내용은 ASP.NET Core Blazor 렌더 모드를 참조하십시오.

- 서버 프로젝트:

  - Components 폴더:

    - Layout 폴더: 다음 레이아웃 구성 요소 및 스타일시트를 포함합니다:

      - MainLayout 구성 요소(MainLayout.razor): 앱의 레이아웃 구성 요소.
      - MainLayout.razor.css: 앱의 메인 레이아웃에 대한 스타일시트.
      - NavMenu 구성 요소(NavMenu.razor): 사이드바 탐색을 구현합니다. 다른 Razor 구성 요소로의 탐색 링크를 렌더링하는 NavLink 구성 요소를 포함합니다. NavLink 구성 요소는 현재 표시되는 구성 요소를 사용자에게 표시합니다.
      - NavMenu.razor.css: 앱의 탐색 메뉴에 대한 스타일시트.

    - Pages 폴더: 앱의 라우팅 가능한 서버 측 Razor 구성 요소(.razor)를 포함합니다. 각 페이지의 경로는 @page 지시문을 사용하여 지정됩니다. 템플릿에는 다음이 포함됩니다:
      - Counter 구성 요소(Counter.razor): Counter 페이지를 구현합니다.
      - Error 구성 요소(Error.razor): Error 페이지를 구현합니다.
      - Home 구성 요소(Home.razor): Home 페이지를 구현합니다.
      - Weather 구성 요소(Weather.razor): 날씨 예보 페이지를 구현합니다.
    - App 구성 요소(App.razor): HTML \<head> 마크업, Routes 구성 요소 및 Blazor \<script> 태그가 포함된 앱의 루트 구성 요소입니다. 루트 구성 요소는 앱이 로드하는 첫 번째 구성 요소입니다.
    - Routes 구성 요소(Routes.razor): Router 구성 요소를 사용하여 라우팅을 설정합니다. 클라이언트 측 상호 작용 구성 요소의 경우, Router 구성 요소는 브라우저 탐색을 가로채고 요청된 주소와 일치하는 페이지를 렌더링합니다.
    - _Imports.razor: 네임스페이스에 대한 @using 지시문과 같은 서버 렌더링된 앱 구성 요소(.razor)에 포함할 공통 Razor 지시문을 포함합니다.

  - Properties 폴더: launchSettings.json 파일에 개발 환경 구성을 저장합니다.
    ```
    참고

    launchSettings.json 파일에서 http 프로필이 https 프로필보다 앞에 있습니다. .NET CLI로 앱을 실행할 때, 첫 번째 프로필이 http이기 때문에 앱이 HTTP 엔드포인트에서 실행됩니다. 프로필 순서는 Linux 및 macOS 사용자들이 HTTPS를 채택하는 과정을 용이하게 합니다. dotnet run 명령에 -lp https 또는 --launch-profile https 옵션을 전달하지 않고도 .NET CLI로 앱을 시작하려면 파일에서 https 프로필을 http 프로필 위로 이동하십시오.
    ```
  - wwwroot 폴더: 앱의 공용 정적 자산을 포함하는 서버 프로젝트의 웹 루트 폴더입니다.

  - Program.cs 파일: ASP.NET Core 웹 애플리케이션 호스트를 설정하고 서비스 등록, 구성, 로깅 및 요청 처리 파이프라인을 포함한 앱의 시작 로직을 포함하는 서버 프로젝트의 진입점입니다.

    - Razor 구성 요소를 위한 서비스는 AddRazorComponents를 호출하여 추가됩니다. AddInteractiveServerComponents는 상호 작용 서버 구성 요소 렌더링을 지원하는 서비스를 추가합니다. AddInteractiveWebAssemblyComponents는 상호 작용 WebAssembly 구성 요소 렌더링을 지원하는 서비스를 추가합니다. 
    - MapRazorComponents는 사용 가능한 구성 요소를 검색하고 앱의 루트 구성 요소(로드되는 첫 번째 구성 요소)를 지정합니다. 기본적으로 App 구성 요소(App.razor)가 루트 구성 요소입니다. AddInteractiveServerRenderMode는 앱에 대해 상호 작용 서버 측 렌더링(interactive SSR)을 구성합니다. AddInteractiveWebAssemblyRenderMode는 앱에 대해 상호 작용 WebAssembly 렌더 모드를 구성합니다.
  - 앱 설정 파일(appsettings.Development.json, appsettings.json): 서버 프로젝트에 대한 구성 설정을 제공합니다.

- 클라이언트 프로젝트(.Client):

    - Pages 폴더: 앱의 라우팅 가능한 클라이언트 측 Razor 구성 요소(.razor)를 포함합니다. 각 페이지의 경로는 @page 지시문을 사용하여 지정됩니다. 템플릿에는 Counter 페이지를 구현하는 Counter 구성 요소(Counter.razor)가 포함됩니다.

      .Client 프로젝트의 구성 요소 폴더 구조는 Blazor 웹 앱의 주요 프로젝트 폴더 구조와 다릅니다. 주요 프로젝트는 표준 ASP.NET Core 프로젝트이므로 Blazor와 관련 없는 ASP.NET Core 프로젝트의 다른 자산을 고려해야 합니다.

      .Client 프로젝트는 순수한 Blazor 프로젝트이며 ASP.NET Core의 비 Blazor 기능 및 사양과 통합할 필요가 없으므로 덜 복잡한 구성 요소 폴더 구조를 사용합니다. 그러나 .Client 프로젝트에서 원하는 구성 요소 폴더 구조를 자유롭게 사용할 수 있습니다. .Client 프로젝트에서 주요 프로젝트의 구성 요소 폴더 레이아웃을 동일하게 사용할 수 있습니다. 구성 요소를 프로젝트 템플릿에서 사용하는 폴더와 다른 폴더로 이동하면 네임스페이스를 조정해야 할 수도 있습니다.

  - 클라이언트 측 프로젝트의 Web Root 폴더에는 클라이언트 측 프로젝트에 대한 구성 설정을 제공하는 앱 설정 파일(appsettings.Development.json, appsettings.json)을 포함한 앱의 공용 정적 자산이 포함됩니다.

  - Program.cs 파일: 서비스 등록, 구성, 로깅 및 요청 처리 파이프라인을 포함한 프로젝트의 시작 로직을 포함하는 클라이언트 측 프로젝트의 진입점으로 WebAssembly 호스트를 설정합니다.

  - _Imports.razor: 네임스페이스에 대한 @using 지시문과 같은 WebAssembly 렌더링된 앱 구성 요소(.razor)에 포함할 공통 Razor 지시문을 포함합니다.

추가 옵션이 구성된 Blazor 웹 앱 프로젝트 템플릿에서 생성된 앱에는 추가 파일 및 폴더가 나타날 수 있습니다. 예를 들어, ASP.NET Core Identity로 앱을 생성하면 인증 및 권한 부여 기능을 위한 추가 자산이 포함됩니다.

### Standalone Blazor WebAssembly

독립형 Blazor WebAssembly 프로젝트 템플릿: blazorwasm

Blazor WebAssembly 템플릿은 독립형 Blazor WebAssembly 앱의 초기 파일 및 디렉토리 구조를 생성합니다:

- blazorwasm 템플릿이 사용되면 앱에는 다음이 포함됩니다:
  - 정적 자산(weather.json)에서 데이터를 로드하는 Weather 구성 요소와 Counter 구성 요소와의 사용자 상호 작용을 시연하는 코드.
  - Bootstrap 프론트엔드 툴킷.
- blazorwasm 템플릿은 샘플 페이지와 스타일링 없이도 생성할 수 있습니다.

프로젝트 구조:

- 레이아웃 폴더: 다음 레이아웃 구성 요소 및 스타일시트를 포함합니다:

  - MainLayout 구성 요소(MainLayout.razor): 앱의 레이아웃 구성 요소.
  - MainLayout.razor.css: 앱의 메인 레이아웃에 대한 스타일시트.
  - NavMenu 구성 요소(NavMenu.razor): 사이드바 탐색을 구현합니다. 다른 Razor 구성 요소로의 탐색 링크를 렌더링하는 NavLink 구성 요소를 포함합니다. NavLink 구성 요소는 로드된 구성 요소가 선택된 상태를 자동으로 표시하여 사용자가 현재 표시된 구성 요소를 이해하는 데 도움을 줍니다.
  - NavMenu.razor.css: 앱의 탐색 메뉴에 대한 스타일시트.

- 페이지 폴더: Blazor 앱의 라우팅 가능한 Razor 구성 요소(.razor)를 포함합니다. 각 페이지의 경로는 @page 지시문을 사용하여 지정됩니다. 템플릿에는 다음 구성 요소가 포함됩니다:

  - Counter 구성 요소(Counter.razor): Counter 페이지를 구현합니다.
  - Index 구성 요소(Index.razor): Home 페이지를 구현합니다.
  - Weather 구성 요소(Weather.razor): 날씨 페이지를 구현합니다.
- _Imports.razor: 네임스페이스에 대한 @using 지시문과 같은 앱의 구성 요소(.razor)에 포함할 공통 Razor 지시문을 포함합니다.

- App.razor: Router 구성 요소를 사용하여 클라이언트 측 라우팅을 설정하는 앱의 루트 구성 요소입니다. Router 구성 요소는 브라우저 탐색을 가로채고 요청된 주소와 일치하는 페이지를 렌더링합니다.

- Properties 폴더: launchSettings.json 파일에 개발 환경 구성을 저장합니다.
  ```
  참고

  launchSettings.json 파일에서 http 프로필이 https 프로필보다 앞에 있습니다. .NET CLI로 앱을 실행할 때, 첫 번째 프로필이 http이기 때문에 앱이 HTTP 엔드포인트에서 실행됩니다. 프로필 순서는 Linux 및 macOS 사용자들이 HTTPS를 채택하는 과정을 용이하게 합니다. dotnet run 명령에 -lp https 또는 --launch-profile https 옵션을 전달하지 않고도 .NET CLI로 앱을 시작하려면 파일에서 https 프로필을 http 프로필 위로 이동하십시오.
  ```
- wwwroot 폴더: 구성 설정과 샘플 날씨 데이터(sample-data/weather.json)에 대한 앱 설정 파일(appsettings.json 및 환경 설정 파일)을 포함하여 앱의 공용 정적 자산을 포함하는 앱의 웹 루트 폴더입니다. index.html 웹페이지는 HTML 페이지로 구현된 앱의 루트 페이지입니다:

  - 앱의 모든 페이지가 처음 요청될 때 이 페이지가 렌더링되어 응답에 반환됩니다.
  - 이 페이지는 루트 App 구성 요소가 렌더링되는 위치를 지정합니다. 구성 요소는 app ID를 가진 div DOM 요소(\<div id="app">Loading...\</div>)의 위치에 렌더링됩니다.

- Program.cs: WebAssembly 호스트를 설정하는 앱의 진입점입니다:

  - App 구성 요소는 앱의 루트 구성 요소입니다. App 구성 요소는 루트 구성 요소 컬렉션에 app ID를 가진 div DOM 요소(\<div id="app">Loading...\</div> in wwwroot/index.html)로 지정됩니다(builder.RootComponents.Add\<App>("#app")).
  - 서비스가 추가되고 구성됩니다(예: builder.Services.AddSingleton\<IMyDependency, MyDependency>()).

추가 옵션이 구성된 Blazor WebAssembly 프로젝트 템플릿에서 생성된 앱에는 추가 파일 및 폴더가 나타날 수 있습니다. 예를 들어, ASP.NET Core Identity로 앱을 생성하면 인증 및 권한 부여 기능을 위한 추가 자산이 포함됩니다.

### Location of the Blazor script

Blazor 스크립트는 ASP.NET Core 공유 프레임워크의 임베디드 리소스에서 제공됩니다.

Blazor 웹 앱에서는 Blazor 스크립트가 Components/App.razor 파일에 위치합니다:

```html
<script src="_framework/blazor.web.js"></script>
```

Blazor 서버 앱에서는 Blazor 스크립트가 Pages/_Host.cshtml 파일에 위치합니다:

```html
<script src="_framework/blazor.server.js"></script>
```

Blazor WebAssembly 앱에서는 Blazor 스크립트 콘텐츠가 wwwroot/index.html 파일에 위치합니다:

```html
<script src="_framework/blazor.webassembly.js"></script>
```

### Location of \<head> and \<body> content

Blazor 웹 앱에서는 \<head> 및 \<body> 콘텐츠가 Components/App.razor 파일에 위치합니다.

Blazor WebAssembly 앱에서는 \<head> 및 \<body> 콘텐츠가 wwwroot/index.html 파일에 위치합니다.

---
## 출처
 - [ASP.NET Core Blazor](https://learn.microsoft.com/en-us/aspnet/core/blazor/?view=aspnetcore-8.0)
 - [ASP.NET Core Blazor supported platforms](https://learn.microsoft.com/en-us/aspnet/core/blazor/supported-platforms?view=aspnetcore-8.0)
 - [Tooling for ASP.NET Core Blazor](https://learn.microsoft.com/en-us/aspnet/core/blazor/tooling?view=aspnetcore-8.0&pivots=linux-macos)
 - [ASP.NET Core Blazor WebAssembly build tools and ahead-of-time (AOT) compilation](https://learn.microsoft.com/en-us/aspnet/core/blazor/webassembly-build-tools-and-aot?view=aspnetcore-8.0)
 - [ASP.NET Core Blazor hosting models](https://learn.microsoft.com/en-us/aspnet/core/blazor/hosting-models?view=aspnetcore-8.0)
 - [ASP.NET Core Blazor Hybrid](https://learn.microsoft.com/en-us/aspnet/core/blazor/hybrid/?view=aspnetcore-8.0)
 - [ASP.NET Core Blazor project structure](https://learn.microsoft.com/en-us/aspnet/core/blazor/project-structure?view=aspnetcore-8.0)

---
## [다음](./04_HTML_기초.md)



