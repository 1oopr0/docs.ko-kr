---
title: '방법: Office Open XML 문서 수정'
ms.date: 07/20/2015
ms.assetid: 1cefd7f5-8e39-44c4-869c-f8021538a777
ms.openlocfilehash: 9fb046f43686405a3d84cb68b49cd6dcd34e0839
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398027"
---
# <a name="how-to-modify-an-office-open-xml-document-visual-basic"></a><span data-ttu-id="fc1c1-102">방법: Office Open XML 문서 수정 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc1c1-102">How to: Modify an Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="fc1c1-103">이 항목에서는 Office Open XML 문서를 열고, 수정하고, 저장하는 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fc1c1-103">This topic presents an example that opens an Office Open XML document, modifies it, and saves it.</span></span>  
  
 <span data-ttu-id="fc1c1-104">Office Open XML에 대 한 자세한 내용은 [Eric 흰색의 블로그](http://www.ericwhite.com)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fc1c1-104">For more information on Office Open XML, see [Eric White's Blog](http://www.ericwhite.com).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc1c1-105">예제</span><span class="sxs-lookup"><span data-stu-id="fc1c1-105">Example</span></span>  
 <span data-ttu-id="fc1c1-106">이 예제에서는 문서의 첫 번째 단락 요소를 찾고</span><span class="sxs-lookup"><span data-stu-id="fc1c1-106">This example finds the first paragraph element in the document.</span></span> <span data-ttu-id="fc1c1-107">단락에서 텍스트를 검색한 다음 단락의 모든 텍스트 실행을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="fc1c1-107">It retrieves the text from the paragraph, and then deletes all text runs in the paragraph.</span></span> <span data-ttu-id="fc1c1-108">또한 대문자로 변환된 첫 번째 단락 텍스트로 구성된 새로운 텍스트 실행을 만들고</span><span class="sxs-lookup"><span data-stu-id="fc1c1-108">It creates a new text run that consists of the first paragraph text that has been converted to upper case.</span></span> <span data-ttu-id="fc1c1-109">변경된 XML을 Open XML 패키지로 serialize한 후 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="fc1c1-109">It then serializes the changed XML into the Open XML package and closes it.</span></span>  
  
 <span data-ttu-id="fc1c1-110">이 예제에서는 WindowsBase 어셈블리의 클래스를 사용하고</span><span class="sxs-lookup"><span data-stu-id="fc1c1-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="fc1c1-111"><xref:System.IO.Packaging?displayProperty=nameWithType> 네임스페이스의 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fc1c1-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As String In source  
            sb.Append(s)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item))  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As T In source  
            sb.Append(s).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String), ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item)).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    Public Function ParagraphText(ByVal e As XElement) As String  
        Dim w As XNamespace = e.Name.Namespace  
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))  
    End Function  
  
    ' Following function is required because Visual Basic does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _  
                                         ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = _  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.ReadWrite)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                    .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", _  
                            UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart _  
                        .GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                Dim stylePart As PackagePart = Nothing  
                Dim styleDoc As XDocument = Nothing  
  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri( _  
                            documentUri, styleRelation.TargetUri)  
                    stylePart = wdPackage.GetPart(styleUri)  
  
                    ' Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
  
                Dim paraNode As XElement = xDoc.Root.<w:body>...<w:p>.FirstOrDefault()  
  
                Dim paraText As String = ParagraphText(paraNode)  
  
                ' Remove all text runs.  
                paraNode...<w:r>.Remove()  
  
                paraNode.Add(<w:r><w:t><%= paraText.ToUpper() %></w:t></w:r>)  
  
                ' Save the XML into the package.  
                Using xw As XmlWriter = _  
                  XmlWriter.Create(documentPart.GetStream(FileMode.Create, FileAccess.Write))  
                    xDoc.Save(xw)  
                End Using  
  
                Console.WriteLine("New first paragraph: >{0}<", paraText.ToUpper())  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="fc1c1-112">이 프로그램을 실행한 후 `SampleDoc.docx`를 열면 이 프로그램에서 해당 문서의 첫 번째 단락을 대문자로 변환한 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc1c1-112">If you open `SampleDoc.docx` after running this program, you can see that this program converted the first paragraph in the document to upper case.</span></span>  
  
 <span data-ttu-id="fc1c1-113">[원본 Office OPEN Xml 문서 만들기 (Visual Basic)](creating-the-source-office-open-xml-document.md)에 설명 된 샘플 Open xml 문서를 사용 하 여 실행 하는 경우이 예제는 다음과 같은 출력을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc1c1-113">When run with the sample Open XML document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md), this example produces the following output:</span></span>  
  
```console  
New first paragraph: >PARSING WORDPROCESSINGML WITH LINQ TO XML<  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc1c1-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc1c1-114">See also</span></span>

- [<span data-ttu-id="fc1c1-115">LINQ to XML (고급 쿼리 기술) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc1c1-115">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)
