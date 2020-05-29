---
title: <schemaImporterExtensions> 요소
description: <schemaImporterExtensions> 요소에는 XmlSchemaImporter가 XSD 형식을 .NET Framework 형식으로 매핑하기 위해 사용하는 형식이 포함되어 있습니다.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5b9820ccdf2c75bed9beda72358c4c4d82ff9ff7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379798"
---
# <a name="schemaimporterextensions-element"></a>\<schemaImporterExtensions> 요소
<xref:System.Xml.Serialization.XmlSchemaImporter>에서 XSD 형식을 .NET Framework 형식으로 매핑하는 데 사용되는 형식을 포함합니다. 구성 파일에 대한 자세한 내용은 [구성 파일 스키마](../../../docs/framework/configure-apps/file-schema/index.md)를 참조하세요.  
  
## <a name="syntax"></a>구문  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<schemaImporterExtensions>에 대한 \<add> 요소](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<xref:System.Xml.Serialization.XmlSchemaImporter>에서 매핑을 만들기 위해 사용하는 형식을 추가합니다.|  
  
## <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<system.xml.serialization> 요소](../../../docs/standard/serialization/system-xml-serialization-element.md)|XML serialization을 제어하기 위한 최상위 요소입니다.|  
  
## <a name="example"></a>예제  
 다음 코드 예제에서는 XSD 형식을 .NET Framework 형식으로 매핑할 때 <xref:System.Xml.Serialization.XmlSchemaImporter>에서 사용하는 형식을 추가하는 방법을 보여 줍니다.  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =
        "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a>참조

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [구성 파일 스키마](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> 요소](../../../docs/standard/serialization/datetimeserialization-element.md)
- [\<schemaImporterExtensions>에 대한 \<add> 요소](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization> 요소](../../../docs/standard/serialization/system-xml-serialization-element.md)
