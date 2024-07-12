# Modules, handlers, and middleware

## 목차
- [Work with data](#work-with-data)
  - [목차](#목차)
  - [출처](#출처)
  - [다음](#다음)

---

ASP.NET Core 앱은 *미들웨어*로 구성됩니다. 미들웨어는 요청 및 응답을 처리하기 위해 파이프라인으로 배열된 핸들러입니다. ASP.NET Core에서는 모듈, 핸들러, *Global.asax.cs*, 그리고 앱 수명 주기가 미들웨어로 대체됩니다. 이 장에서는 Blazor 앱의 맥락에서 미들웨어에 대해 배우게 됩니다.

## 개요

ASP.NET Core 요청 파이프라인은 일련의 요청 대리자로 구성되며, 이는 차례로 호출됩니다. 다음 다이어그램은 이 개념을 보여줍니다. 실행의 스레드는 검은색 화살표를 따라갑니다.

![pipeline](../img/11_middleware/request-delegate-pipeline.png)

위의 다이어그램에는 수명 주기 이벤트의 개념이 없습니다. 이 시스템은 어떤 프로세스가 발생하는지 이해하기 쉽게 하며, 미들웨어를 어떤 지점에든 삽입할 수 있게 해줍니다. 미들웨어는 요청 파이프라인에 추가된 순서대로 실행됩니다. 이는 주로 *Startup.cs* 파일의 코드에서 추가됩니다.

## Katana

Katana에 익숙한 독자는 ASP.NET Core에서도 편안함을 느낄 것입니다. 사실, Katana는 ASP.NET Core가 파생된 프레임워크입니다. 이는 ASP.NET 4.x를 위한 유사한 미들웨어 및 파이프라인 패턴을 도입했습니다. Katana를 위해 설계된 미들웨어는 ASP.NET Core 파이프라인과 함께 작동하도록 조정될 수 있습니다.

## 일반적인 미들웨어

ASP.NET 4.x는 많은 모듈을 포함하고 있습니다. 유사하게, ASP.NET Core에는 많은 미들웨어 구성 요소가 있습니다. 일부 경우에는 ASP.NET Core와 함께 IIS 모듈을 사용할 수 있습니다. 다른 경우에는 기본 ASP.NET Core 미들웨어가 제공될 수 있습니다.

다음 표는 ASP.NET Core에서 대체 미들웨어 및 구성 요소를 나열합니다.

|모듈                    |ASP.NET 4.x 모듈                |ASP.NET Core 옵션|
|------------------------|------------------------------|-----------------|
|HTTP 오류               |`CustomErrorModule`           |상태 코드 페이지 미들웨어|
|기본 문서               |`DefaultDocumentModule`       |기본 파일 미들웨어|
|디렉터리 브라우징       |`DirectoryListingModule`      |디렉터리 브라우징 미들웨어|
|동적 압축               |`DynamicCompressionModule`    |응답 압축 미들웨어|
|실패한 요청 추적       |`FailedRequestsTracingModule` |ASP.NET Core 로깅|
|파일 캐싱               |`FileCacheModule`             |응답 캐싱 미들웨어|
|HTTP 캐싱               |`HttpCacheModule`             |응답 캐싱 미들웨어|
|HTTP 로깅               |`HttpLoggingModule`           |ASP.NET Core 로깅|
|HTTP 리디렉션           |`HttpRedirectionModule`       |URL 재작성 미들웨어|
|ISAPI 필터              |`IsapiFilterModule`           |미들웨어|
|ISAPI                   |`IsapiModule`                 |미들웨어|
|요청 필터링             |`RequestFilteringModule`      |URL 재작성 미들웨어 IRule|
|URL 재작성&#8224;       |`RewriteModule`               |URL 재작성 미들웨어|
|정적 압축               |`StaticCompressionModule`     |응답 압축 미들웨어|
|정적 콘텐츠             |`StaticFileModule`            |정적 파일 미들웨어|
|URL 인증                |`UrlAuthorizationModule`      |ASP.NET Core Identity|

이 목록은 포괄적이지 않지만 두 프레임워크 간의 매핑이 어떻게 이루어지는지에 대한 아이디어를 제공합니다. 더 자세한 목록은 [ASP.NET Core와 함께 사용하는 IIS 모듈]을 참조하십시오.

## 사용자 정의 미들웨어

내장된 미들웨어가 앱에 필요한 모든 시나리오를 처리하지 못할 수도 있습니다. 이런 경우에는 사용자 정의 미들웨어를 만드는 것이 좋습니다. 여러 가지 방법으로 미들웨어를 정의할 수 있으며, 가장 간단한 방법은 간단한 대리자를 사용하는 것입니다. 다음은 쿼리 문자열에서 문화 요청을 수락하는 미들웨어 예제입니다:

```csharp
public class Startup
{
    public void Configure(IApplicationBuilder app)
    {
        app.Use(async (context, next) =>
        {
            var cultureQuery = context.Request.Query["culture"];

            if (!string.IsNullOrWhiteSpace(cultureQuery))
            {
                var culture = new CultureInfo(cultureQuery);

                CultureInfo.CurrentCulture = culture;
                CultureInfo.CurrentUICulture = culture;
            }

            // 파이프라인의 다음 대리자/미들웨어를 호출합니다.
            await next();
        });

        app.Run(async (context) =>
            await context.Response.WriteAsync(
                $"Hello {CultureInfo.CurrentCulture.DisplayName}"));
    }
}
```

미들웨어는 또한 클래스로 정의될 수 있으며, `IMiddleware` 인터페이스를 구현하거나 미들웨어 규칙을 따를 수 있습니다. 자세한 내용은 `사용자 정의 ASP.NET Core 미들웨어 작성`을 참조하십시오.
 
---
## 출처
[Modules, handlers, and middleware](https://learn.microsoft.com/en-us/dotnet/architecture/blazor-for-web-forms-developers/middleware)

---
## [다음](./12_config.md)