# C# 식별자 명명 규칙 및 규칙

## 목차
- [C# 식별자 명명 규칙 및 규칙](#c-식별자-명명-규칙-및-규칙)
  - [목차](#목차)
  - [이름 지정 규칙](#이름-지정-규칙)
  - [명명 규칙](#명명-규칙)
  - [다음 예에서 public으로 표시된 요소와 관련된 지침은 protected 및 protected internal 요소로 작업할 때도 적용 가능하며, 이 요소는 모두 외부 호출자에게 표시됩니다.](#다음-예에서-public으로-표시된-요소와-관련된-지침은-protected-및-protected-internal-요소로-작업할-때도-적용-가능하며-이-요소는-모두-외부-호출자에게-표시됩니다)
  - [파스칼식 대/소문자](#파스칼식-대소문자)
  - [카멜식 대/소문자](#카멜식-대소문자)
  - [형식 매개 변수 명명 지침](#형식-매개-변수-명명-지침)
  - [추가 명명 규칙](#추가-명명-규칙)
  - [출처](#출처)

---
식별자는 형식(클래스, 인터페이스, 구조체, 대리자 또는 열거형), 멤버, 변수 또는 네임스페이스에 할당하는 이름입니다.

---
## 이름 지정 규칙

유효한 식별자는 다음 규칙을 따라야 합니다. C# 컴파일러는 다음 규칙을 따르지 않는 식별자에 대해 오류를 생성합니다.

 - 식별자는 문자나 밑줄(_)로 시작해야 합니다.
 - 식별자에는 유니코드 문자, 10진수 문자, 유니코드 연결 문자, 유니코드 조합 문자 또는 유니코드 형식 문자가 포함될 수 있습니다. 유니코드 범주에 대한 자세한 내용은 유니코드 범주 데이터베이스를 참조하세요.

식별자의 @ 접두사를 사용하여 C# 키워드와 일치하는 식별자를 선언할 수 있습니다. @은 식별자 이름의 일부가 아닙니다. 예를 들어 @if는 if라는 식별자를 선언합니다. 이러한 verbatim 식별자는 주로 다른 언어로 선언된 식별자와의 상호 운용성을 위한 것입니다.

```
중요

C# 언어 사양에서는 문자(Lu, Ll, Lt, Lm, Lo 또는 Nl), 숫자(Nd), 연결(Pc), 결합(Mn 또는 Mc) 및 서식(Cf) 범주만 허용합니다. 외부의 모든 항목은 _을 사용하여 자동으로 바뀝니다. 이는 특정 유니코드 문자에 영향을 미칠 수 있습니다.
```

---
## 명명 규칙

규칙 외에도 식별자 이름에 대한 규칙이 .NET API 전체에서 사용됩니다. 이러한 규칙은 이름에 대한 일관성을 제공하지만 컴파일러는 이를 강제하지 않습니다. 프로젝트에서 다양한 규칙을 자유롭게 사용할 수 있습니다.

규칙에 따라 C# 프로그램은 형식 이름, 네임스페이스 및 모든 공용 멤버에 PascalCase를 사용합니다. 또한 dotnet/docs 팀은 .NET 런타임 팀의 코딩 스타일에서 채택한 다음 규칙을 사용합니다.

 - 인터페이스 이름은 대문자 I로 시작합니다.
 - 특성 유형은 Attribute 단어로 끝납니다.
 - 열거형 형식은 플래그가 아닌 경우에는 단수 명사를 사용하고 플래그인 경우에는 복수 명사를 사용합니다.
 - 식별자에는 두 개의 연속된 밑줄(_) 문자가 포함될 수 없습니다. 이러한 이름은 컴파일러 생성 식별자용으로 예약되어 있습니다.
 - 변수, 메서드, 클래스에 의미 있고 설명이 포함된 이름을 사용합니다.
 - 간결함보다 명확성이 더 중요합니다.
 - 클래스 이름과 메서드 이름에는 PascalCase를 사용합니다.
 - 메서드 매개 변수 및 지역 변수에 camelCase를 사용합니다.
 - 필드와 지역 상수 모두 상수 이름에 PascalCase를 사용합니다.
 - 프라이빗 인스턴스 필드는 밑줄(_)로 시작하고 다시 기본 텍스트는 camelCased입니다.
 - 정적 필드는 s_로 시작합니다. 이 규칙은 기본 Visual Studio 동작도 아니고 프레임워크 디자인 지침의 일부도 아니지만 editorconfig에서 구성할 수 있습니다.
 - 널리 알려지고 인정되는 약어를 제외하고 이름에 약어나 머리글자어를 사용하지 마세요.
 - 역방향 도메인 이름 표기법에 따라 의미 있고 설명이 포함된 네임스페이스를 사용합니다.
 - 어셈블리의 기본 목적을 나타내는 어셈블리 이름을 선택합니다.
 - 간단한 루프 카운터를 제외하고 단일 문자 이름을 사용하지 마세요. 또한 C# 구문(construct)의 구문(syntax)을 설명하는 구문(syntax) 예에서는 C# 언어 사양에 사용된 규칙과 일치하는 다음과 같은 단일 문자 이름을 사용하는 경우가 많습니다. 구문 예는 규칙의 예외입니다.
     - 구조체에는 S를 사용하고 클래스에는 C를 사용합니다.
     - 메서드에는 M을 사용합니다.
     - 변수에는 v을, 매개 변수에는 p를 사용합니다.
     - ref 매개 변수에는 r을 사용합니다.

```
 팁

코드 스타일 명명 규칙을 사용하여 대문자, 접두사, 접미사 및 단어 구분 기호와 관련된 명명 규칙을 적용할 수 있습니다.
```

다음 예에서 public으로 표시된 요소와 관련된 지침은 protected 및 protected internal 요소로 작업할 때도 적용 가능하며, 이 요소는 모두 외부 호출자에게 표시됩니다.
---
## 파스칼식 대/소문자

class, interface, struct 또는 delegate 형식의 이름을 지정할 때 파스칼식 대/소문자("PascalCasing")를 사용합니다.

```C#
public class DataService
{
}
```
```C#
public record PhysicalAddress(
    string Street,
    string City,
    string StateOrProvince,
    string ZipCode);
```
```C#
public struct ValueCoordinate
{
}
```
```C#
public delegate void DelegateType(string message);
```
interface 이름을 지정할 때는 이름 앞에 I 접두사를 적용하고 파스칼식 대/소문자를 사용합니다. 이 접두사는 해당 항목이 interface임을 소비자에게 분명히 나타냅니다.
```C#
public interface IWorkerQueue
{
}
```
필드, 속성, 이벤트 등 형식의 public 멤버 이름을 지정할 때 파스칼식 대/소문자를 사용합니다. 또한 모든 메서드와 로컬 함수에 대해 파스칼식 대/소문자 구분을 사용합니다.
```C#
public class ExampleEvents
{
    // A public field, these should be used sparingly
    public bool IsValid;

    // An init-only property
    public IWorkerQueue WorkerQueue { get; init; }

    // An event
    public event Action EventProcessing;

    // Method
    public void StartEventProcessing()
    {
        // Local function
        static int CountQueueItems() => WorkerQueue.Count;
        // ...
    }
}
```
위치 레코드를 작성할 때는 레코드의 public 속성인 매개 변수에 파스칼식 대/소문자를 사용합니다.

```C#
public record PhysicalAddress(
    string Street,
    string City,
    string StateOrProvince,
    string ZipCode);
```

---
## 카멜식 대/소문자

private 또는 internal 필드 이름을 지정할 때 카멜식 대/소문자("camelCasing")를 사용하고 앞에 _을 붙입니다. 대리자 형식의 인스턴스를 포함하여 지역 변수의 이름을 지정할 때 카멜식 대/소문자를 사용합니다.

```C#
public class DataService
{
    private IWorkerQueue _workerQueue;
}
```
```
팁

문 완성을 지원하는 IDE에서 이러한 명명 규칙을 따르는 C# 코드를 편집할 때 _을 입력하면 개체 범위 멤버가 모두 표시됩니다.
```
private 또는 internal인 static 필드를 사용할 때는 s_ 접두사를 사용하고 스레드 정적인 경우 t_을 사용합니다.

```C#
public class DataService
{
    private static IWorkerQueue s_workerQueue;

    [ThreadStatic]
    private static TimeSpan t_timeSpan;
}
```
메서드 매개 변수를 작성할 때 카멜식 대/소문자를 사용합니다.

```C#
public T SomeMethod<T>(int someNumber, bool isValid)
{
}
```

---
## 형식 매개 변수 명명 지침

다음 지침은 제네릭 형식 매개 변수의 형식 매개 변수에 적용됩니다. 형식 매개 변수는 제네릭 형식 또는 제네릭 메서드의 인수에 대한 자리 표시자입니다. C# 프로그래밍 가이드에서 제네릭 형식 매개 변수에 대해 자세히 알아볼 수 있습니다.

 - 필수적 단일 문자 이름으로도 자체 설명이 가능하여 설명적인 이름을 굳이 사용할 필요가 없는 경우가 아니면 제네릭 형식 매개 변수 이름을 설명적인 이름으로 지정하세요.
```C#
public interface ISessionChannel<TSession> { /*...*/ }
public delegate TOutput Converter<TInput, TOutput>(TInput from);
public class List<T> { /*...*/ }
```
 - 선택적 단일 문자 형식 매개 변수를 사용하는 형식에는 형식 매개 변수 이름으로 T를 사용해 보세요.
```C#
public int IComparer<T>() { return 0; }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T : struct { /*...*/ }
```
 - 필수적 설명적인 형식 매개 변수 이름 앞에 “T”를 붙이세요.
```C#
public interface ISessionChannel<TSession>
{
    TSession Session { get; }
}
```
 - 선택적 매개 변수 이름 안에 형식 매개 변수에 적용되는 제약 조건을 나타내 보세요. 예를 들어, ISession으로 제한된 매개 변수는 TSession이라고 불릴 수 있습니다.

코드 분석 규칙 CA1715를 사용하여 형식 매개 변수의 이름이 적절하게 지정되었는지 확인할 수 있습니다.

---
## 추가 명명 규칙
 - using 지시문이 포함되지 않는 예제에서는 네임스페이스 한정을 사용합니다. 프로젝트에서 네임스페이스를 기본적으로 가져오는 경우에는 해당 네임스페이스의 이름을 정규화할 필요가 없습니다. 정규화된 이름은 한 줄에 표시하기가 너무 길면 다음 예에 나와 있는 것처럼 점(.)으로 분할할 수 있습니다.
```C#
var currentPerformanceCounterCategory = new System.Diagnostics.
    PerformanceCounterCategory();
```
 - 다른 지침에 맞도록 조정하기 위해 Visual Studio 디자이너 도구를 사용하여 만든 개체 이름을 변경할 필요는 없습니다.

---
## 출처
[C# 설명서>기본 사항>코딩 스타일>C# 식별자 이름](https://learn.microsoft.com/ko-kr/dotnet/csharp/fundamentals/coding-style/identifier-names)