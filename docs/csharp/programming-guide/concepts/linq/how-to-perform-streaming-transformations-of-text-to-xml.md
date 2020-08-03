---
title: 텍스트를 XML로 변환 스트리밍을 수행하는 방법(C#)
description: 텍스트 파일을 한 번에 한 줄씩 스트리밍하고 LINQ 쿼리를 사용하여 텍스트 파일을 처리하는 C#의 XML로 텍스트의 스트리밍을 변환하는 방법에 대해 알아봅니다.
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: f933064be70d39b59cf7dbe51b4ee92e5226647a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104749"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>텍스트를 XML로 변환 스트리밍을 수행하는 방법(C#)

텍스트 파일을 처리하는 한 가지 방법은 `yield return` 구문을 사용하여 한 번에 한 줄씩 텍스트 파일을 스트리밍하는 확장 메서드를 작성하는 것입니다. 그런 다음 지연된 방식으로 텍스트 파일을 처리하는 LINQ 쿼리를 작성할 수 있습니다. <xref:System.Xml.Linq.XStreamingElement>를 사용하여 출력을 스트림하면 소스 텍스트 파일의 크기에 관계없이 최소 메모리 크기를 사용하는 XML로 텍스트 파일을 변환할 수 있습니다.

 스트리밍 변환과 관련된 몇 가지 주의 사항이 있습니다. 스트리밍 변환은 전체 파일을 한 번만 처리할 수 있는 경우와 소스 문서에서 발생하는 순서대로 줄을 처리할 수 있는 경우에 가장 효과적으로 적용됩니다. 파일을 두 번 이상 처리해야 하거나 줄을 처리하기 전에 정렬해야 하는 경우에는 스트리밍 기법 사용의 많은 이점을 얻을 수 없습니다.

## <a name="example"></a>예제

 아래에 있는 People.txt 텍스트 파일은 이 예제의 소스입니다.

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 다음 코드에는 지연된 방식으로 텍스트 파일의 줄을 스트림하는 확장 메서드가 포함되어 있습니다.

```csharp
public static class StreamReaderSequence
{
    public static IEnumerable<string> Lines(this StreamReader source)
    {
        if (source == null)
            throw new ArgumentNullException(nameof(source));

        string line;
        while ((line = source.ReadLine()) != null)
        {
            yield return line;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        var sr = new StreamReader("People.txt");
        var xmlTree = new XStreamingElement("Root",
            from line in sr.Lines()
            let items = line.Split(',')
            where !line.StartsWith("#")
            select new XElement("Person",
                       new XAttribute("ID", items[0]),
                       new XElement("First", items[1]),
                       new XElement("Last", items[2]),
                       new XElement("Occupation", items[3])
                   )
        );
        Console.WriteLine(xmlTree);
        sr.Close();
    }
}
```

 이 예에서 생성되는 출력은 다음과 같습니다.

```xml
<Root>
  <Person ID="1">
    <First>Tai</First>
    <Last>Yee</Last>
    <Occupation>Writer</Occupation>
  </Person>
  <Person ID="2">
    <First>Nikolay</First>
    <Last>Grachev</Last>
    <Occupation>Programmer</Occupation>
  </Person>
  <Person ID="3">
    <First>David</First>
    <Last>Wright</Last>
    <Occupation>Inventor</Occupation>
  </Person>
</Root>
```

## <a name="see-also"></a>참고 항목

- <xref:System.Xml.Linq.XStreamingElement>
