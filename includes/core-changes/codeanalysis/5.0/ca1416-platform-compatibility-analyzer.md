---
ms.openlocfilehash: e3c9f23ca73ed9b85d09680ec15251ebe02c7f8e
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065219"
---
### <a name="ca1416-platform-compatibility"></a>CA1416: 플랫폼 호환성

.NET 코드 분석기 규칙 CA1416은 .NET 5.0부터 기본적으로 사용됩니다. 운영 체제를 확인하지 않는 호출 사이트에서 플랫폼별 API에 대한 호출의 빌드 경고를 생성합니다.

#### <a name="change-description"></a>변경 내용 설명

.Net 5.0부터 .Net SDK에는 [.NET 소스 코드 분석기](../../../../docs/fundamentals/productivity/code-analysis.md)가 포함됩니다. CA1416을 포함하여 해당 규칙 중 여러 개가 기본적으로 사용됩니다. 해당 규칙을 위반하는 코드가 프로젝트에 포함되고 프로젝트가 경고를 오류로 처리하도록 구성된 경우 해당 변경으로 인해 빌드의 호환성이 손상될 수 있습니다. 규칙 CA1416은 플랫폼 컨텍스트가 확인되지 않는 위치에서 플랫폼별 API를 사용하는 경우 알림을 제공합니다.

규칙 CA1416, 플랫폼 호환성 분석기는 .NET 5.0에 새로 도입된 다른 일부 기능과 함께 작동합니다. .NET 5.0에는 API가 ‘지원되거나’ ‘지원되지 않는’ 플랫폼을 지정할 수 있는 `SupportedOSPlatformAttribute` 및 `UnsupportedOSPlatformAttribute` 특성(이전 미리 보기 릴리스에서는 이름이 <xref:System.Runtime.Versioning.MinimumOSPlatformAttribute> 및 <xref:System.Runtime.Versioning.RemovedInOSPlatformAttribute>)이 도입되었습니다.  이러한 특성이 없으면 API는 모든 플랫폼에서 지원되는 것으로 간주됩니다. 해당 특성은 핵심 .NET 라이브러리의 플랫폼별 API에 적용되었습니다.

해당 API를 사용할 수 없는 플랫폼을 대상으로 하는 프로젝트에서 규칙 CA1416은 플랫폼 컨텍스트가 확인되지 않는 플랫폼별 API 호출을 플래그로 지정합니다. 현재 `SupportedOSPlatformAttribute` 및 `UnsupportedOSPlatformAttribute` 특성으로 데코레이트된 대부분의 API는 지원되지 않는 운영 체제에서 호출되는 경우 <xref:System.PlatformNotSupportedException> 예외를 throw합니다. 이러한 API는 플랫폼별로 표시되어 있으므로 규칙 CA1416을 사용하면 호출 사이트에 OS 검사를 추가하여 런타임 <xref:System.PlatformNotSupportedException> 예외를 방지하는 데 도움이 됩니다.

#### <a name="examples"></a>예제

- <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> 메서드는 Windows에서만 지원됩니다(`[SupportedOSPlatform("windows")]`으로 데코레이트됨). 다음 코드는 프로젝트가 `net5.0-windows`가 아닌 `net5.0`을 [대상](../../../../docs/standard/frameworks.md)으로 하는 경우 빌드 시 CA1416 경고를 생성합니다. 경고를 방지하기 위해 수행할 수 있는 작업은 [권장 조치](#recommended-action)를 참조하세요.

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> 메서드는 브라우저에서 지원되지 않습니다(`[UnsupportedOSPlatform("browser")]`으로 데코레이트됨). 다음 코드는 프로젝트가 Blazor WebAssembly SDK(`<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">`)를 사용하거나 프로젝트 파일에서 지원되는 플랫폼(`<SupportedPlatform Include="browser" />`)으로 `browser`를 포함하는 경우 빌드 시 CA1416 경고를 생성합니다.

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

#### <a name="version-introduced"></a>도입된 버전

5.0 RC1

#### <a name="recommended-action"></a>권장 조치

적절한 플랫폼에서 코드가 실행되는 경우에만 플랫폼별 API가 호출되도록 합니다. 플랫폼별 API를 호출하기 전에 <xref:System.OperatingSystem?displayProperty=nameWithType> 클래스에서 `Is<Platform>` 메서드 중 하나(예: `System.OperatingSystem.IsWindows()`)를 사용하여 현재 운영 체제를 확인할 수 있습니다.

`if` 문의 조건에 `Is<Platform>` 메서드 중 하나를 사용할 수 있습니다.

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

또는 런타임에 추가 `if` 문의 오버헤드를 원하지 않는다면 대신 <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>를 호출합니다.

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

API를 플랫폼에 특정한 것으로 표시할 수도 있으며, 이 경우 요구 사항을 검사할 부담은 호출자에 있습니다. 특정 메서드나 유형 또는 전체 어셈블리를 표시할 수 있습니다.

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

모든 호출 사이트를 수정하지는 않으려면 다음 옵션 중 하나를 선택하여 경고를 중지할 수 있습니다.

- 규칙 CA1416을 중지하려면 `#pragma` 또는 [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) 컴파일러 플래그를 사용하거나 editorconfig 파일에서 [규칙의 심각도](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations)를 `none`으로 설정하면 됩니다.

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- 코드 분석을 완전히 사용하지 않으려면 프로젝트 파일에서 `EnableNETAnalyzers`를 `false`로 설정합니다. 자세한 내용은 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)를 참조하세요.

#### <a name="category"></a>범주

- 코드 분석
- 핵심 .NET 라이브러리

#### <a name="affected-apis"></a>영향을 받는 API

Windows 플랫폼:

- <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md>에 나열된 모든 API
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

Blazor WebAssembly 플랫폼:

- <https://github.com/dotnet/runtime/issues/41087>에 나열된 모든 API

<!--

#### Affected APIs

- ``

-->

#### <a name="see-also"></a>참고 항목

- [.NET API 분석기](../../../../docs/standard/analyzers/api-analyzer.md)