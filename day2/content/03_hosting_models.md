# Blazor app hosting models

## 목차
- [Blazor app hosting models](#blazor-app-hosting-models)
  - [목차](#목차)
  - [Blazor WebAssembly 앱](#blazor-webassembly-앱)
  - [Blazor 서버 앱](#blazor-서버-앱)
  - [올바른 Blazor 호스팅 모델 선택 방법](#올바른-blazor-호스팅-모델-선택-방법)
  - [앱 배포](#앱-배포)
  - [출처](#출처)
  - [다음](#다음)

---

Blazor는 두 가지 주요 방식으로 호스팅될 수 있습니다:

- 브라우저 내에서 WebAssembly를 사용하여 클라이언트 측에서.
- ASP.NET Core 앱에서 서버 측에서.

## Blazor WebAssembly 앱

Blazor WebAssembly 앱은 WebAssembly를 기반으로 하여 브라우저 내에서 직접 실행됩니다. 이는 Angular나 React와 같은 프론트엔드 JavaScript 프레임워크와 유사하지만, JavaScript 대신 C#을 사용합니다. 

Blazor WebAssembly 앱은 다음과 같이 작동합니다:

- .NET 런타임과 앱 어셈블리 및 필요한 종속성이 브라우저로 다운로드됩니다.
- 브라우저 플러그인이나 확장이 필요 없이 작동합니다.
- 다운로드된 어셈블리는 다른 .NET 앱에서 사용하는 일반적인 .NET 어셈블리입니다.
- .NET 런타임이 시작되고 앱 어셈블리가 실행되며, 루트 컴포넌트가 렌더링됩니다.
- Blazor는 컴포넌트의 렌더링된 출력에 따라 UI 업데이트를 계산하고 DOM을 업데이트합니다.

Blazor WebAssembly 앱은 순수 클라이언트 측에서 실행되므로, GitHub Pages나 Azure Static Website Hosting과 같은 정적 사이트 호스팅 솔루션에 배포될 수 있습니다. 서버에 .NET이 전혀 필요하지 않습니다. 다만, 깊이 링크된 URL로 접근할 경우 서버에서 요청을 앱의 루트로 리디렉션해야 할 수 있습니다. 예를 들어, IIS에서는 URL 재작성 규칙을 사용하여 이를 처리할 수 있습니다.

Blazor WebAssembly 앱과 ASP.NET Core 호스트 프로젝트를 함께 사용하면 클라이언트와 서버 모두에서 .NET을 사용하여 코드를 쉽게 공유할 수 있습니다. 이를 통해 일관된 언어, 프레임워크 및 도구를 사용하여 앱을 빌드할 수 있습니다.

## Blazor 서버 앱

Blazor 서버 앱은 서버 측에서 실행되며, 컴포넌트가 서버에서 동작합니다. UI 이벤트는 실시간 연결을 통해 서버로 전송됩니다. 서버에서 이벤트를 처리하고, 변경된 UI를 계산하여 클라이언트의 DOM에 적용합니다.

Blazor 서버 앱의 작동 방식은 다음과 같습니다:

- 컴포넌트는 서버에서 실행되며, 브라우저에서 발생하는 UI 이벤트는 실시간 연결을 통해 서버로 전송됩니다.
- 컴포넌트가 이벤트를 처리하고, 계산된 UI 차이를 직렬화하여 브라우저로 전송하고, DOM을 업데이트합니다.

Blazor 서버 호스팅 모델은 클라이언트와의 활성 연결이 필요하며, 모든 UI 상태는 서버에서 유지 관리됩니다.

## 올바른 Blazor 호스팅 모델 선택 방법

Blazor 호스팅 모델은 각기 다른 장단점을 가지고 있습니다.

Blazor WebAssembly 호스팅 모델의 장점:
- .NET 서버 측 종속성이 없습니다.
- 클라이언트 리소스와 기능을 완전히 활용합니다.
- 서버리스 배포 시나리오가 가능합니다.

단점:
- 브라우저 기능에 제한을 받습니다.
- 클라이언트 하드웨어와 소프트웨어가 필요합니다.
- 다운로드 크기가 크고 앱 로드 시간이 길어질 수 있습니다.
- .NET 런타임 및 도구 지원이 덜 성숙합니다.

Blazor 서버 호스팅 모델의 장점:
- 다운로드 크기가 작고 앱 로드 시간이 빠릅니다.
- 서버 기능을 최대한 활용할 수 있습니다.
- 기존 .NET 도구와의 통합이 쉽습니다.
- 얇은 클라이언트를 지원합니다.

단점:
- UI 대기 시간이 길어질 수 있습니다.
- 오프라인 지원이 없습니다.
- 많은 사용자를 처리하는 데 있어 확장성이 어려울 수 있습니다.
- 앱을 제공하려면 ASP.NET Core 서버가 필요합니다.

Blazor 호스팅 모델은 필요에 따라 변경할 수 있습니다. 두 모델 모두 동일한 컴포넌트 모델을 사용하므로, 원칙적으로 동일한 컴포넌트를 두 가지 호스팅 모델 중 하나와 함께 사용할 수 있습니다.

## 앱 배포

Blazor 앱은 다음과 같이 호스팅할 수 있습니다:
- 정적 파일로서 또는 ASP.NET Core 앱으로 IIS에 호스팅할 수 있습니다.
- ASP.NET Core의 유연성을 활용하여 다양한 플랫폼과 서버 인프라에서 호스팅할 수 있습니다.

Blazor WebAssembly와 Blazor 서버 앱의 프로젝트 설정 방법에 대한 자세한 내용은 Blazor 호스팅 및 배포 문서를 참조하십시오.

---
## 출처
[Blazor app hosting models](https://learn.microsoft.com/en-us/dotnet/architecture/blazor-for-web-forms-developers/hosting-models)

---
## [다음](./04_Project_structure.md)