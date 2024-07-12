# App configuration

## 목차
- [App configuration](#app-configuration)
  - [목차](#목차)
  - [구성 소스](#구성-소스)
  - [appsettings.json 형식 및 액세스](#appsettingsjson-형식-및-액세스)
  - [사용자 비밀](#사용자-비밀)
  - [환경 변수](#환경-변수)
  - [명령줄 인수](#명령줄-인수)
  - [web.config의 반환](#webconfig의-반환)
  - [앱에서 구성 읽기](#앱에서-구성-읽기)
  - [강력한 형식의 구성](#강력한-형식의-구성)
  - [출처](#출처)
  - [다음](#다음)

---

앱 구성 로드의 주요 방법은 서버의 *web.config* 파일 또는 관련 구성 파일에 항목을 추가하는 것입니다. `ConfigurationManager` 정적 객체를 사용하여 앱 설정, 데이터 저장소 연결 문자열 및 기타 구성 공급자와 상호작용할 수 있습니다. 다음 코드에서 볼 수 있듯이 앱 구성과 상호작용하는 것이 일반적입니다:

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

ASP.NET Core 및 서버 측 Blazor에서는 *web.config* 파일이 존재할 수 있지만, `ConfigurationManager`와의 상호작용은 없습니다. 대신 다른 소스에서 더 구조화된 앱 구성을 받습니다. 이제 구성 정보를 수집하는 방법과 *web.config* 파일에서 구성 정보를 여전히 액세스할 수 있는 방법을 살펴보겠습니다.

## 구성 소스

ASP.NET Core는 앱에 사용할 수 있는 다양한 구성 소스를 인식합니다. 프레임워크는 기본적으로 이러한 소스 중 최상의 기능을 제공하려고 합니다. 구성은 다양한 소스에서 읽고 집계되며, 동일한 구성 키에 대해 나중에 로드된 값이 이전 값보다 우선합니다.

ASP.NET Core는 클라우드를 인식하고 운영자와 개발자 모두에게 앱 구성을 더 쉽게 만들기 위해 설계되었습니다. ASP.NET Core는 환경을 인식하고 `Production` 또는 `Development` 환경에서 실행 중인지 알고 있으며, 환경 지시자는 `ASPNETCORE_ENVIRONMENT` 시스템 환경 변수에 설정됩니다. 값이 구성되지 않은 경우, 앱은 기본적으로 `Production` 환경에서 실행됩니다.

앱은 환경의 이름을 기반으로 여러 소스에서 구성을 트리거하고 추가할 수 있습니다. 기본적으로 구성은 다음 리소스에서 나열된 순서대로 로드됩니다:

1. *appsettings.json* 파일
1. *appsettings.{ENVIRONMENT_NAME}.json* 파일
1. 사용자 비밀 파일 (디스크에 저장된 경우)
1. 환경 변수
1. 명령줄 인수

## appsettings.json 형식 및 액세스

*appsettings.json* 파일은 다음과 같은 JSON 형식의 값으로 계층 구조를 가질 수 있습니다:

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

위의 JSON이 제공되면, 구성 시스템은 자식 값을 평탄화하고 계층 구조 경로의 완전히 정의된 경로를 참조합니다. 예를 들어, `section1:key0` 구성 키는 `section1` 객체의 `key0` 값을 액세스합니다.

## 사용자 비밀

사용자 비밀은 앱 개발 폴더 외부의 개발자 워크스테이션에 있는 JSON 파일에 저장된 구성 값입니다. 이는 `Development` 환경에서 실행 중일 때만 로드되며 특정 앱과 연관됩니다. .NET CLI의 `user-secrets` 명령을 사용하여 관리됩니다.

앱을 비밀 저장소에 설정하려면 `user-secrets` 명령을 실행하십시오:

```dotnetcli
dotnet user-secrets init
```

이 명령은 프로젝트 파일에 `UserSecretsId` 요소를 추가합니다. 그런 다음 `set` 명령으로 비밀을 정의할 수 있습니다:

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

위의 명령은 개발자 워크스테이션에서 `Parent:ApiKey` 구성 키를 값 `12345`로 사용할 수 있게 합니다. 

## 환경 변수

다음으로 로드된 값 집합은 시스템의 환경 변수입니다. 이제 구성 API를 통해 시스템의 모든 환경 변수 설정에 액세스할 수 있습니다. 계층 구조 값은 앱 내에서 읽을 때 평탄화되고 콜론 문자로 구분됩니다. 그러나 일부 운영 체제는 환경 변수 이름에서 콜론 문자를 허용하지 않기 때문에, ASP.NET Core는 두 개의 밑줄(`__`)이 있는 값을 콜론으로 변환하여 이 제한을 해결합니다. 예를 들어, `Parent:ApiKey` 값은 환경 변수 `Parent__ApiKey`로 재정의할 수 있습니다.

## 명령줄 인수

구성은 앱이 시작될 때 명령줄 인수로 제공될 수도 있습니다. 설정할 구성 값의 이름을 표시하고 구성할 값을 표시하려면 더블 대시(`--`) 또는 슬래시(`/`) 표기법을 사용하십시오. 구문은 다음과 같습니다:

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## web.config의 반환

앱을 Windows의 IIS에 배포한 경우, *web.config* 파일은 여전히 IIS가 앱을 관리하도록 구성합니다. 기본적으로 IIS는 ASP.NET Core 모듈(ANCM)에 대한 참조를 추가합니다. ANCM은 Kestrel 웹 서버 대신 앱을 호스팅하는 IIS의 네이티브 모듈입니다. 이 *web.config* 섹션은 다음 XML 마크업과 유사합니다:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

앱별 구성은 `aspNetCore` 요소 내에 `environmentVariables` 요소를 중첩하여 정의할 수 있습니다. 이 섹션에 정의된 값은 환경 변수로 ASP.NET Core 앱에 제공됩니다. 환경 변수는 앱 시작 시 적절히 로드됩니다.

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## 앱에서 구성 읽기

ASP.NET Core는 `IConfiguration` 인터페이스를 통해 앱 구성을 제공합니다. 이 구성 인터페이스는 Blazor 구성 요소, Blazor 페이지 및 구성에 액세스해야 하는 기타 ASP.NET Core 관리 클래스에서 요청할 수 있습니다. ASP.NET Core 프레임워크는 이전에 구성된 해결된 구성으로 이 인터페이스를 자동으로 채울 것입니다. Blazor 페이지 또는 구성 요소의 Razor 마크업에서, *razor* 파일 상단에 `@inject` 지시문을 사용하여 `IConfiguration` 객체를 주입할 수 있습니다:

```razor
@inject IConfiguration Configuration
```

위의 문장은 Razor 템플릿의 나머지 부분에서 `Configuration` 변수로 `IConfiguration` 객체를 사용할 수 있게 합니다.

개별 구성 설정은 인덱서 매개변수로 찾고자 하는 구성 설정 계층 구조를 지정하여 읽을 수 있습니다:

```csharp
var mySetting = Configuration["section1:key0"];
```

`GetSection` 메서드를 사용하여 특정 위치의 키 컬렉션을 검색하여 전체 구성 섹션을 가져올 수 있습니다. 예를 들어, `GetSection("section1")` 구문을 사용하여 앞서 예에서 section1의 구성을 검색할 수 있습니다.

## 강력한 형식의 구성

ASP.NET Core에서는 구성 값을 받을 클래스 계층 구조를 지정할 수 있습니다. 이러한 클래스는 부모 클래스에서 상속할 필요 없이 캡처하려는 구성 구조에 대한 속성 및 타입 참조와 일치하는 `public` 속성을 포함해야 합니다.

앞서의 *appsettings.json* 예제를 위해 다음 클래스를 정의하여 값을 캡처할 수 있습니다:

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

이 클래스 계층 구조는 `Startup.ConfigureServices` 메서드(또는 *Program.cs*의 적절한 위치에서 `builder.Services` 속성을 사용하여)에서 다음 줄을 추가하여 채울 수 있습니다:

```csharp
services.Configure<MyConfig>(Configuration);
```

앱의 나머지 부분에서는 `IOptions<MyConfig>` 형식의 입력 매개변수를 클래스에 추가하거나 Razor 템플릿에서 `@inject` 지시문을 사용하여 강력한 형식의 구성 설정을 받을 수 있습니다. `IOptions<MyConfig>.Value` 속성은 구성 설정에서 채워진 `MyConfig` 값을 반환합니다.

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

옵션 기능에 대한 자세한 내용은 [ASP.NET Core의 옵션 패턴] 문서를 참조하십시오.
 
---
## 출처
[App configuration](https://learn.microsoft.com/en-us/dotnet/architecture/blazor-for-web-forms-developers/config)

---
## [다음](./13_Blazor를_사용하여_첫_번째_웹앱_빌드.md)