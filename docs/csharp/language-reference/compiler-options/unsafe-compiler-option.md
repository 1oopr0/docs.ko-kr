---
description: -unsafe(C# 컴파일러 옵션)
title: -unsafe(C# 컴파일러 옵션)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 0f6d94dd25a020d96430746c4b5e7aefd0f679da
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140843"
---
# <a name="-unsafe-c-compiler-options"></a>-unsafe(C# 컴파일러 옵션)

**-unsafe** 컴파일러 옵션을 사용하면 [unsafe](../keywords/unsafe.md) 키워드를 사용하는 코드를 컴파일할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>설명

안전하지 않은 코드에 대한 자세한 내용은 [안전하지 않은 코드 및 포인터](../../programming-guide/unsafe-code-pointers/index.md)를 참조하세요.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면  
  
1. 프로젝트 **속성** 페이지를 엽니다.  
  
2. **빌드** 속성 페이지를 클릭합니다.  
  
3. **안전하지 않은 코드 허용** 확인란을 선택합니다.  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>이 옵션을 csproj 파일에 추가하려면

프로젝트에 대한 .csproj 파일을 열고 다음 요소를 추가합니다.

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 이 컴파일러 옵션을 프로그래밍 방식으로 설정하는 방법에 대한 자세한 내용은 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>을 참조하십시오.  
  
## <a name="example"></a>예제

안전하지 않은 모드에 대해 `in.cs` 컴파일:  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>참고 항목

- [C# 컴파일러 옵션](index.md)
- [프로젝트 및 솔루션 속성 관리](/visualstudio/ide/managing-project-and-solution-properties)
