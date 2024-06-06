# 예외 만들기 및 throw

## 목차
- [예외 만들기 및 throw](#예외-만들기-및-throw)
  - [목차](#목차)
  - [예외를 throw할 때 피해야 하는 작업](#예외를-throw할-때-피해야-하는-작업)
  - [작업 반환 메서드의 예외](#작업-반환-메서드의-예외)
  - [예외 클래스 정의](#예외-클래스-정의)
  - [출처](#출처)

---
예외는 프로그램을 실행하는 동안 오류가 발생했음을 나타내는 데 사용됩니다. 오류를 설명하는 예외 개체가 만들어지고 throw 문 또는 식을 통해 throw됩니다. 그런 다음 런타임에 가장 호환성이 높은 예외 처리기를 검색합니다.

프로그래머는 다음 조건 중 하나 이상에 해당할 경우 예외를 throw해야 합니다.

 - 메서드가 정의된 기능을 완료할 수 없는 경우. 예를 들어 메서드에 대한 매개 변수에 잘못된 값이 포함된 경우입니다.
```C#
static void CopyObject(SampleClass original)
{
    _ = original ?? throw new ArgumentException("Parameter cannot be null", nameof(original));
}
```
 - 개체 상태에 따라 개체에 대한 부적절한 호출이 이루어진 경우. 한 가지 예는 읽기 전용 파일에 쓰려고 시도하는 경우입니다. 개체 상태가 작업을 허용하지 않을 경우 이 클래스의 파생에 따라 InvalidOperationException의 인스턴스 또는 개체를 throw합니다. 다음 코드는 InvalidOperationException 개체를 throw 하는 메서드의 예제입니다.
```C#
public class ProgramLog
{
    FileStream logFile = null!;
    public void OpenLog(FileInfo fileName, FileMode mode) { }

    public void WriteLog()
    {
        if (!logFile.CanWrite)
        {
            throw new InvalidOperationException("Logfile cannot be read-only");
        }
        // Else write data to the log and return.
    }
}
```
 - 메서드에 대한 인수가 예외를 일으키는 경우. 이 경우 원래 예외가 catch되고 ArgumentException 인스턴스가 만들어져야 합니다. 원래 예외를 ArgumentException의 생성자에 InnerException 매개 변수로 전달해야 합니다.
```C#
static int GetValueFromArray(int[] array, int index)
{
    try
    {
        return array[index];
    }
    catch (IndexOutOfRangeException e)
    {
        throw new ArgumentOutOfRangeException(
            "Parameter index is out of range.", e);
    }
}
```
```
참고

앞의 예제는 InnerException 속성을 사용하는 방법을 보여줍니다. 이 예제는 의도적으로 간소화되었습니다. 실제로는 인덱스를 사용하기 전에 인덱스가 범위 내에 있는지 확인해야 합니다. 매개 변수의 멤버가 멤버를 호출하기 전에 예상할 수 없는 예외를 throw할 때 예외를 래핑하는 이 기법을 사용할 수 있습니다.
```

예외에 이름이 StackTrace인 속성이 포함되어 있습니다. 이 문자열에는 현재 콜 스택에 대한 메서드의 이름과 각 메서드에 대해 예외가 throw된 파일 이름 및 줄 번호가 포함됩니다. StackTrace 개체는 throw 문의 지점에서 CLR(공용 언어 런타임)에 의해 자동으로 만들어지므로 해당 예외는 스택 추적이 시작되는 지점에서 throw되어야 합니다.

모든 예외에 이름이 Message인 속성이 포함되어 있습니다. 예외의 이유를 설명하려면 이 문자열을 설정해야 합니다. 보안이 중요한 정보는 메시지 텍스트에 넣으면 안 됩니다. Message 외에 ArgumentException에는 예외를 throw한 인수의 이름으로 설정해야 하는 ParamName 속성이 포함되어 있습니다. 속성 setter에서는 ParamName을 value로 설정해야 합니다.

public 및 protected 메서드는 의도한 함수를 완료할 수 없을 때마다 예외를 throw합니다. throw된 예외 클래스는 오류 조건에 맞을 수 있는 가장 구체적인 예외입니다. 이러한 예외는 클래스 기능의 일부로 문서화해야 하고 파생 클래스 또는 원래 클래스의 업데이트는 이전 버전과의 호환성을 위해 같은 동작을 유지해야 합니다.

---
## 예외를 throw할 때 피해야 하는 작업

다음 목록은 예외를 throw할 때 피해야 할 사례를 나타냅니다.

 - 프로그램의 흐름을 일반 실행의 일부로 변경하는 데는 예외를 사용하지 마세요. 오류 조건을 보고하고 처리하는 데 예외를 사용합니다.
 - 예외는 throw하는 대신 반환 값 또는 매개 변수로 반환하면 안 됩니다.
 - 고유한 소스 코드에서 의도적으로 System.Exception, System.SystemException, System.NullReferenceException 또는 System.IndexOutOfRangeException을 throw하지 마세요.
 - 릴리스 모드가 아닌 디버그 모드에서 throw될 수 있는 예외를 만들지 마세요. 개발 단계에서 런타임 오류를 식별하려면 대신 디버그 어설션을 사용하세요.

---
## 작업 반환 메서드의 예외

async 한정자를 사용하여 선언된 메서드에는 예외와 관련하여 몇 가지 특별한 고려 사항이 있습니다. async 메서드에서 throw된 예외는 반환된 작업에 저장되며 예컨데 작업이 대기될 때까지 나타나지 않습니다. 저장된 예외에 대한 자세한 내용은 비동기 예외를 참조하세요.

메서드의 비동기 부분을 입력하기 전에 인수의 유효성을 검사하고 해당하는 예외(예: ArgumentException 및 ArgumentNullException)를 throw하는 것이 좋습니다. 즉, 이러한 유효성 검사 예외는 작업이 시작되기 전에 동기적으로 나타나야 합니다. 다음 코드 조각은 예외가 throw되면 ArgumentException 예외가 동기적으로 나타나는 반면 InvalidOperationException은 반환된 작업에 저장되는 예를 보여줍니다.

```C#
// Non-async, task-returning method.
// Within this method (but outside of the local function),
// any thrown exceptions emerge synchronously.
public static Task<Toast> ToastBreadAsync(int slices, int toastTime)
{
    if (slices is < 1 or > 4)
    {
        throw new ArgumentException(
            "You must specify between 1 and 4 slices of bread.",
            nameof(slices));
    }

    if (toastTime < 1)
    {
        throw new ArgumentException(
            "Toast time is too short.", nameof(toastTime));
    }

    return ToastBreadAsyncCore(slices, toastTime);

    // Local async function.
    // Within this function, any thrown exceptions are stored in the task.
    static async Task<Toast> ToastBreadAsyncCore(int slices, int time)
    {
        for (int slice = 0; slice < slices; slice++)
        {
            Console.WriteLine("Putting a slice of bread in the toaster");
        }
        // Start toasting.
        await Task.Delay(time);

        if (time > 2_000)
        {
            throw new InvalidOperationException("The toaster is on fire!");
        }

        Console.WriteLine("Toast is ready!");

        return new Toast();
    }
}
```
---
## 예외 클래스 정의

프로그램에서는 System 네임스페이스의 미리 정의된 예외 클래스를 throw하거나(이전에 언급한 위치 제외) Exception에서 파생시켜 자체 예외 클래스를 만들 수 있습니다. 파생 클래스는 최소 세 개의 생성자, 즉 매개 변수 없는 생성자, 메시지 속성을 설정하는 생성자, Message 및 InnerException 속성을 모두 설정하는 생성자를 정의해야 합니다. 예시:
```C#
[Serializable]
public class InvalidDepartmentException : Exception
{
    public InvalidDepartmentException() : base() { }
    public InvalidDepartmentException(string message) : base(message) { }
    public InvalidDepartmentException(string message, Exception inner) : base(message, inner) { }
}
```
새로운 속성이 제공하는 데이터가 예외 확인에 유용할 경우 해당 속성을 예외 클래스에 추가합니다. 새 속성이 파생 예외 클래스에 추가되면 추가된 정보를 반환하기 위해 ToString()을 재정의해야 합니다.

---
## 출처
[C# 설명서>기본 사항>예외 및 오류>예외 만들기 및 throw](https://learn.microsoft.com/ko-kr/dotnet/csharp/fundamentals/exceptions/creating-and-throwing-exceptions)