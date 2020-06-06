---
title: <configuration>에 대한 <configSections> 요소
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155351"
---
# <a name="configsections-element-for-configuration"></a>\<configuration>에 대한 \<configSections> 요소

구성 섹션과 네임 스페이스 선언을 포함 합니다.

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**

## <a name="attributes"></a>특성

None

## <a name="parent-element"></a>부모 요소

|     | Description |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | 공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다. |

## <a name="child-elements"></a>자식 요소

|     | Description |
| --- | ----------- |
| [**\<section>**](section-element.md) | 구성 섹션 선언을 포함 합니다. |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | 구성 섹션에 대 한 네임 스페이스를 정의 합니다. |
| [**\<remove>**](remove-element-for-configsections.md) | 미리 정의 된 섹션 또는 섹션 그룹을 제거 합니다. |
| [**\<clear>**](clear-element-for-configsections.md) | 이전에 정의 된 모든 섹션과 섹션 그룹을 지웁니다. |

## <a name="remarks"></a>설명

이 요소가 구성 파일에 있으면 요소의 첫 번째 자식 요소 여야 합니다 **\<configuration>** .

## <a name="example"></a>예제

다음 예제에서는 구성 섹션을 정의 하 고 해당 섹션에 대 한 설정을 정의 하는 방법을 보여 줍니다.

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>구성 파일

이 요소는 응용 프로그램 구성 파일 *, 컴퓨터 구성 파일 (machine.config*) 및 응용 프로그램 디렉터리 수준에 없는 *web.config 파일* 에서 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [.NET Framework의 구성 파일 스키마](index.md)
