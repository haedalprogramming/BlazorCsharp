# Architecture comparison of ASP.NET Web Forms and Blazor

## 목차
- [Architecture comparison of ASP.NET Web Forms and Blazor](#architecture-comparison-of-aspnet-web-forms-and-blazor)
  - [목차](#목차)
  - [ASP.NET Web Forms](#aspnet-web-forms)
  - [Blazor](#blazor)
  - [출처](#출처)
  - [다음](#다음)

---

Blazor는 현대적인 클라이언트 측 웹 애플리케이션 프레임워크로, JavaScript 프레임워크인 Angular나 React와 비슷한 방식으로 동작합니다. 여기서는 Blazor와 이전의 ASP.NET Web Forms의 작동 방식과 아키텍처를 비교하여 Blazor가 어떻게 동작하는지 설명하겠습니다.

## ASP.NET Web Forms

ASP.NET Web Forms는 페이지 중심의 아키텍처를 기반으로 하는 웹 프레임워크입니다. 여기서는 각 HTTP 요청이 앱 내 특정 위치에 대한 별도의 페이지로 응답됩니다. 페이지가 요청될 때 브라우저의 내용은 요청된 페이지의 결과로 대체됩니다.

ASP.NET Web Forms 페이지는 다음과 같은 구성 요소로 이루어집니다:

- **HTML 마크업**: 페이지의 구조와 내용을 정의합니다.
- **C# 또는 Visual Basic 코드**: 페이지의 동작을 정의하는 코드입니다.
- **코드 비하인드 클래스**: 로직과 이벤트 처리 기능을 포함하며, 마크업과 분리된 파일에 저장됩니다.
- **컨트롤**: 페이지에 배치되어 상호작용할 수 있는 재사용 가능한 UI 단위입니다.

페이지는 *.aspx 파일로 구성되며, 여기에는 마크업, 컨트롤 및 일부 코드가 포함됩니다. 코드 비하인드 클래스는 *.aspx.cs 또는 *.aspx.vb 파일에 저장됩니다. 웹 서버는 이 파일들을 해석하여 변경될 때마다 컴파일합니다.

ASP.NET Web Forms에는 다양한 이벤트 라이프사이클이 존재합니다. 각 페이지는 초기화, 로드, 프리렌더 및 언로드 이벤트를 발생시켜 페이지의 코드를 실행합니다. 또한, 페이지의 컨트롤은 `ViewState`라는 숨겨진 필드에 상태 정보를 저장하여 서버와 클라이언트 간의 상호작용을 관리합니다.

## Blazor

Blazor는 클라이언트 측 웹 UI 프레임워크로, 사용자의 상호작용을 처리하고 필요한 UI 업데이트를 렌더링합니다. Blazor는 요청-응답 모델을 사용하지 않으며, 이벤트 기반으로 동작합니다. 

Blazor 앱은 HTML 페이지에 렌더링된 하나 이상의 루트 컴포넌트로 구성됩니다. 사용자가 컴포넌트를 렌더링할 위치를 지정하고, 컴포넌트는 사용자 상호작용을 처리합니다.

Blazor 컴포넌트는 재사용 가능한 UI 조각을 나타내는 .NET 클래스입니다. 각 컴포넌트는 자체 상태를 유지하고 렌더링 로직을 지정할 수 있으며, 다른 컴포넌트를 렌더링할 수도 있습니다. 컴포넌트는 특정 사용자 상호작용에 대한 이벤트 핸들러를 지정하여 상태를 업데이트합니다.

Blazor는 컴포넌트가 이벤트를 처리한 후 변경된 내용을 추적하여 효율적으로 DOM에 적용합니다. Blazor는 `RenderTree`라는 메모리 내 표현을 사용하여 컴포넌트를 렌더링하고, 새로 렌더링된 출력과 이전 출력을 비교하여 UI 차이를 계산합니다.

Blazor는 단일 논리 실행 스레드를 강제하기 위해 `SynchronizationContext`를 사용하며, 컴포넌트의 라이프사이클 메서드와 이벤트 콜백은 이 `SynchronizationContext`에서 실행됩니다.

Blazor는 현대적인 웹 애플리케이션 개발을 위해 설계된 강력한 프레임워크로, 클라이언트 측에서의 동작과 .NET의 장점을 결합하여 효율적이고 상호작용이 풍부한 사용자 경험을 제공합니다. Blazor를 통해 최신 웹 기술을 활용하여 보다 나은 웹 애플리케이션을 개발할 수 있습니다.

---
## 출처
[Architecture comparison of ASP.NET Web Forms and Blazor](https://learn.microsoft.com/en-us/dotnet/architecture/blazor-for-web-forms-developers/architecture-comparison)

---
## [다음](./03_hosting_models.md)