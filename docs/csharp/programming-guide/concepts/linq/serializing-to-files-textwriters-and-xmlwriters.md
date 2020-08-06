---
title: Files, TextWriters 및 XmlWriters로 serialization
description: C#에서 ToString 또는 Save 메서드를 사용하여 XML 트리를 파일, TextWriter 또는 XmlWriter로 직렬화하는 옵션에 대해 알아봅니다.
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 43c51ae7e9bf1a7848d45fd900424d6186671e53
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302388"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Files, TextWriters 및 XmlWriters로 serialization

XML 트리를 <xref:System.IO.File>, <xref:System.IO.TextWriter> 또는 <xref:System.Xml.XmlWriter>로 serialize할 수 있습니다.

<xref:System.Xml.Linq.XDocument> 메서드를 사용하여 <xref:System.Xml.Linq.XElement> 및 `ToString`와 같은 XML 구성 요소를 문자열로 serialize할 수 있습니다.

문자열로 serialize할 때 서식 지정을 방지하려면 <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> 메서드를 사용하면 됩니다.

파일로 직렬화할 때의 기본 동작은 생성되는 XML 문서의 서식을 지정하는(들여쓰는) 것입니다. 들여쓰는 경우 XML 트리의 무효 공백은 유지되지 않습니다. 서식을 사용하여 serialize하려면 <xref:System.Xml.Linq.SaveOptions>를 인수로 사용하지 않는 다음 메서드의 오버로드 중 하나를 사용합니다.

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

들여쓰지 않고 XML 트리에서 무효 공백을 유지하려면 <xref:System.Xml.Linq.SaveOptions>를 인수로 사용하는 다음 메서드의 오버로드 중 하나를 사용합니다.

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

예제를 보려면 적절한 참조 항목을 참조하세요.

## <a name="see-also"></a>참조

- [XML 트리 serialize(C#)](serializing-to-files-textwriters-and-xmlwriters.md)
