# Forms and validation

## 목차
- [Forms and validation](#forms-and-validation)
  - [목차](#목차)
  - [출처](#출처)
  - [다음](#다음)

---
ASP.NET Web Forms 프레임워크에는 폼에 입력된 사용자 입력을 검증하는 여러 서버 유효성 검사 컨트롤(`RequiredFieldValidator`, `CompareValidator`, `RangeValidator` 등)이 포함되어 있습니다. 또한 ASP.NET Web Forms 프레임워크는 데이터 주석(`Required`, `StringLength`, `Range` 등)을 기반으로 모델 바인딩 및 모델 유효성 검사도 지원합니다. 유효성 검사 로직은 비침투적 JavaScript 기반 유효성 검사를 사용하여 서버와 클라이언트 양쪽에서 적용할 수 있습니다. `ValidationSummary` 서버 컨트롤은 사용자에게 유효성 검사 오류 요약을 표시하는 데 사용됩니다.

Blazor는 클라이언트와 서버 간에 유효성 검사 로직을 공유할 수 있도록 지원합니다. ASP.NET은 많은 일반적인 서버 유효성 검사의 JavaScript 구현을 제공합니다. 많은 경우, 개발자는 여전히 애플리케이션 특정 유효성 검사 로직을 완전히 구현하기 위해 JavaScript를 작성해야 합니다. 동일한 모델 타입, 데이터 주석 및 유효성 검사 로직을 서버와 클라이언트 모두에서 사용할 수 있습니다.

Blazor는 입력 컴포넌트 집합을 제공합니다. 입력 컴포넌트는 필드 데이터를 모델에 바인딩하고 폼이 제출될 때 사용자 입력을 검증합니다.

|입력 컴포넌트  |렌더링된 HTML 요소      |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

`EditForm` 컴포넌트는 이러한 입력 컴포넌트를 감싸고 `EditContext`를 통해 유효성 검사 프로세스를 조정합니다. `EditForm`을 생성할 때 `Model` 매개변수를 사용하여 바인딩할 모델 인스턴스를 지정합니다. 유효성 검사는 일반적으로 데이터 주석을 사용하여 수행되며, 이는 확장 가능합니다. 데이터 주석 기반 유효성 검사를 활성화하려면 `DataAnnotationsValidator` 컴포넌트를 `EditForm`의 자식으로 추가합니다. `EditForm` 컴포넌트는 유효한 제출(`OnValidSubmit`)과 유효하지 않은 제출(`OnInvalidSubmit`)을 처리하는 편리한 이벤트를 제공합니다. 또한 유효성을 직접 트리거하고 처리할 수 있는 보다 일반적인 `OnSubmit` 이벤트도 있습니다.

유효성 검사 오류 요약을 표시하려면 `ValidationSummary` 컴포넌트를 사용하십시오. 특정 입력 필드에 대한 유효성 검사 메시지를 표시하려면 `For` 매개변수에 적절한 모델 멤버를 가리키는 람다 식을 지정하여 `ValidationMessage` 컴포넌트를 사용하십시오.

다음 모델 타입은 데이터 주석을 사용하여 여러 유효성 검사 규칙을 정의합니다:

```csharp
using System;
using System.ComponentModel.DataAnnotations;

public class Starship
{
    [Required]
    [StringLength(16,
        ErrorMessage = "Identifier too long (16 character limit).")]
    public string Identifier { get; set; }

    public string Description { get; set; }

    [Required]
    public string Classification { get; set; }

    [Range(1, 100000,
        ErrorMessage = "Accommodation invalid (1-100000).")]
    public int MaximumAccommodation { get; set; }

    [Required]
    [Range(typeof(bool), "true", "true",
        ErrorMessage = "This form disallows unapproved ships.")]
    public bool IsValidatedDesign { get; set; }

    [Required]
    public DateTime ProductionDate { get; set; }
}
```

다음 컴포넌트는 `Starship` 모델 타입을 기반으로 폼을 작성하는 방법을 보여줍니다:

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => starship.Identifier" />
    </p>
    <p>
        <label for="description">Description (optional): </label>
        <InputTextArea id="description" @bind-Value="starship.Description" />
    </p>
    <p>
        <label for="classification">Primary Classification: </label>
        <InputSelect id="classification" @bind-Value="starship.Classification">
            <option value="">Select classification ...</option>
            <option value="Exploration">Exploration</option>
            <option value="Diplomacy">Diplomacy</option>
            <option value="Defense">Defense</option>
        </InputSelect>
        <ValidationMessage For="() => starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => starship.ProductionDate" />
    </p>

    <button type="submit">Submit</button>
</EditForm>

@code {
    private Starship starship = new Starship();

    private void HandleValidSubmit()
    {
        // Save the data
    }
}
```

폼 제출 후, 모델 바인딩된 데이터는 데이터베이스와 같은 데이터 저장소에 저장되지 않았습니다. Blazor WebAssembly 앱에서는 데이터를 서버로 전송해야 합니다. 예를 들어 HTTP POST 요청을 사용합니다. Blazor Server 앱에서는 데이터가 이미 서버에 있지만, 이를 지속시켜야 합니다. Blazor 앱에서 데이터 액세스를 처리하는 방법은 데이터 처리 섹션에서 다룹니다.

---
## 출처
[Forms and validation](https://learn.microsoft.com/en-us/dotnet/architecture/blazor-for-web-forms-developers/forms-validation)

---
## [다음](./10_data.md)