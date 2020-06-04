---
title: '방법: XmlReader에서 트리 만들기'
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: 25c15ff08563b12b26041a536dfbca1c9cce260a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414610"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a>방법: XmlReader에서 트리 만들기 (Visual Basic)

이 항목에서는 <xref:System.Xml.XmlReader>에서 XML 트리를 직접 만드는 방법을 보여 줍니다. <xref:System.Xml.Linq.XElement>에서 <xref:System.Xml.XmlReader>를 만들려면 요소 노드에 <xref:System.Xml.XmlReader>를 배치해야 합니다. <xref:System.Xml.XmlReader>는 주석과 처리 명령을 건너뛰지만 <xref:System.Xml.XmlReader>가 텍스트 노드에 배치되면 오류가 throw됩니다. 이러한 오류를 방지하려면 <xref:System.Xml.XmlReader>에서 XML 트리를 만들기 전에 항상 <xref:System.Xml.XmlReader>를 요소에 배치하세요.

## <a name="example"></a>예제

이 예제에서는 XML 문서 [샘플 XML 파일: Books(LINQ to XML)](sample-xml-file-books-linq-to-xml.md)를 사용합니다.

다음 코드에서는 `T:System.Xml.XmlReader` 개체를 만들고 첫 번째 요소 노드를 찾을 때까지 노드를 읽은 다음 <xref:System.Xml.Linq.XElement> 개체를 로드합니다.

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

이 예제는 다음과 같은 출력을 생성합니다.

```xml
<Catalog>
   <Book id="bk101">
      <Author>Garghentini, Davide</Author>
      <Title>XML Developer's Guide</Title>
      <Genre>Computer</Genre>
      <Price>44.95</Price>
      <PublishDate>2000-10-01</PublishDate>
      <Description>An in-depth look at creating applications
      with XML.</Description>
   </Book>
   <Book id="bk102">
      <Author>Garcia, Debra</Author>
      <Title>Midnight Rain</Title>
      <Genre>Fantasy</Genre>
      <Price>5.95</Price>
      <PublishDate>2000-12-16</PublishDate>
      <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>
   </Book>
</Catalog>
```

## <a name="see-also"></a>참고 항목

- [XML 구문 분석 (Visual Basic)](parsing-xml.md)
