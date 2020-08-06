---
title: 요소의 부분 값을 검색하는 방법(C#)
description: 요소의 단순 값을 가져오는 방법을 알아봅니다. 단순 값은 특정 요소 전용입니다.
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 597859e5b66606aa0cff9c1a475e79e6b66c39fc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301582"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>요소의 부분 값을 검색하는 방법(C#)
이 항목에서는 요소의 부분 값을 가져오는 방법을 보여 줍니다. 단일 문자열로 연결된 모든 하위 요소의 값을 포함하는 상세 값과 달리 부분 값은 특정 요소의 값입니다.  
  
 캐스팅을 사용하거나 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 속성을 사용하여 요소 값을 검색하는 경우에는 상세 값이 검색됩니다. 부분 값을 검색하려면 다음 예제와 같이 `ShallowValue` 확장 메서드를 사용합니다. 요소의 내용을 기준으로 요소를 선택하려는 경우에는 부분 값을 검색하는 것이 유용합니다.  
  
 다음 예제에서는 요소의 부분 값을 검색하는 확장 메서드를 선언합니다. 그런 다음 쿼리에 해당 확장명 메서드를 사용하여 계산된 값을 포함하는 모든 요소를 나열합니다.  
  
## <a name="example"></a>예제  
 아래에 있는 Report.xml 텍스트 파일은 이 예제의 소스입니다.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```csharp  
public static class MyExtensions  
{  
    public static string ShallowValue(this XElement xe)  
    {  
        return xe  
               .Nodes()  
               .OfType<XText>()  
               .Aggregate(new StringBuilder(),  
                          (s, c) => s.Append(c),  
                          s => s.ToString());  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement root = XElement.Load("Report.xml");  
  
        IEnumerable<XElement> query = from el in root.Descendants()  
                                      where el.ShallowValue().StartsWith("=")  
                                      select el;  
  
        foreach (var q in query)  
        {  
            Console.WriteLine("{0}{1}{2}",  
                q.Name.ToString().PadRight(8),  
                q.Attribute("Name").ToString().PadRight(20),  
                q.ShallowValue());  
        }  
    }  
}  
```  
  
 이 예에서 생성되는 출력은 다음과 같습니다.  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>참고 항목

- [LINQ to XML 축(C#)](./linq-to-xml-axes-overview.md)
