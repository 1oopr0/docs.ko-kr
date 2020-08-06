---
title: 단락의 텍스트 검색(C#)
description: C#에서 LINQ 쿼리를 사용하여 WordprocessingML 문서에 있는 각 단락의 텍스트를 문자열로 가져오는 방법을 알아봅니다. 이 예제에서는 연결된 쿼리를 사용합니다.
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 58a07ab848307c886927815e4e49e90806f61346
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302596"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="a0033-104">단락의 텍스트 검색(C#)</span><span class="sxs-lookup"><span data-stu-id="a0033-104">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="a0033-105">이 예제는 이전 예제 [단락 및 해당 스타일 검색(C#)](./retrieving-the-paragraphs-and-their-styles.md)을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-105">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](./retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="a0033-106">이 새 예제에서는 각 단락의 텍스트를 문자열로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-106">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="a0033-107">이 예제에서는 텍스트를 검색하기 위해 익명 형식의 컬렉션을 반복하는 추가 쿼리를 추가하고 새 멤버 `Text`가 추가된 익명 형식의 새 컬렉션을 프로젝션합니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-107">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="a0033-108">또한 <xref:System.Linq.Enumerable.Aggregate%2A> 표준 쿼리 연산자를 사용하여 여러 문자열을 한 문자열로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-108">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="a0033-109">먼저 익명 형식의 컬렉션을 프로젝션한 다음 이 컬렉션을 사용하여 익명 형식의 새 컬렉션을 프로젝션하는 방법은 일반적이고 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-109">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="a0033-110">이 쿼리는 첫 번째 익명 형식으로 프로젝션하지 않고 작성될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-110">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="a0033-111">그러나 지연 계산 때문에 이렇게 해도 추가 처리 능력이 많이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-111">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="a0033-112">이 방법은 힙에서 수명이 짧은 개체를 더 많이 만들지만 이로 인해 성능이 크게 저하되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-112">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="a0033-113">물론 단락, 각 단락의 스타일 및 각 단락의 텍스트를 검색하는 기능이 포함된 단일 쿼리를 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-113">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="a0033-114">그러나 복잡한 쿼리를 여러 쿼리로 나누면 생성되는 코드가 더욱 모듈화되고 유지 관리가 쉬워지기 때문에 유용한 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-114">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="a0033-115">또한 쿼리의 일부를 다시 사용해야 하는 경우 쿼리가 이런 방식으로 작성되면 리팩터링하기가 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-115">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="a0033-116">서로 연결된 이러한 쿼리는 [자습서: 여러 쿼리 연결(C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) 항목에서 자세히 검사된 처리 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-116">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0033-117">예제</span><span class="sxs-lookup"><span data-stu-id="a0033-117">Example</span></span>  
 <span data-ttu-id="a0033-118">이 예제에서는 WordprocessingML 문서를 처리하여 요소 노드, 스타일 이름 및 각 단락의 텍스트를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-118">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="a0033-119">이 예제는 이 자습서의 이전 예제를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-119">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="a0033-120">새 쿼리는 아래에 있는 코드의 주석에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-120">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="a0033-121">이 예제의 소스 문서 만들기에 대한 지침은 [원본 Office Open XML 문서 만들기(C#)](./creating-the-source-office-open-xml-document.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0033-121">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="a0033-122">이 예제에서는 WindowsBase 어셈블리의 클래스를 사용하고</span><span class="sxs-lookup"><span data-stu-id="a0033-122">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="a0033-123"><xref:System.IO.Packaging?displayProperty=nameWithType> 네임스페이스의 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-123">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
XDocument xDoc = null;  
XDocument styleDoc = null;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship =  
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
          docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation =  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
string defaultStyle =
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
// Find all paragraphs in the document.  
var paragraphs =  
    from para in xDoc  
                 .Root  
                 .Element(w + "body")  
                 .Descendants(w + "p")  
    let styleNode = para  
                    .Elements(w + "pPr")  
                    .Elements(w + "pStyle")  
                    .FirstOrDefault()  
    select new  
    {  
        ParagraphNode = para,  
        StyleName = styleNode != null ?  
            (string)styleNode.Attribute(w + "val") :  
            defaultStyle  
    };  
  
// Following is the new query that retrieves the text of  
// each paragraph.  
var paraWithText =  
    from para in paragraphs  
    select new  
    {  
        ParagraphNode = para.ParagraphNode,  
        StyleName = para.StyleName,  
        Text = para  
               .ParagraphNode  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .Aggregate(  
                   new StringBuilder(),  
                   (s, i) => s.Append((string)i),  
                   s => s.ToString()  
               )  
    };  
  
foreach (var p in paraWithText)  
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
```  
  
 <span data-ttu-id="a0033-124">[원본 Office Open XML 문서 만들기(C#)](./creating-the-source-office-open-xml-document.md)에서 설명하는 문서에 적용할 경우 이 예제의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-124">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
```output  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a><span data-ttu-id="a0033-125">다음 단계</span><span class="sxs-lookup"><span data-stu-id="a0033-125">Next Steps</span></span>  
 <span data-ttu-id="a0033-126">다음 예제에서는 <xref:System.Linq.Enumerable.Aggregate%2A> 대신 확장 메서드를 사용하여 여러 문자열을 하나의 문자열로 연결하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a0033-126">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="a0033-127">확장 메서드를 사용하여 리팩터링(C#)</span><span class="sxs-lookup"><span data-stu-id="a0033-127">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="a0033-128">참조</span><span class="sxs-lookup"><span data-stu-id="a0033-128">See also</span></span>

- [<span data-ttu-id="a0033-129">자습서: WordprocessingML 문서에서 내용 조작(C#)</span><span class="sxs-lookup"><span data-stu-id="a0033-129">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="a0033-130">LINQ to XML에서 지연 실행 및 지연 계산(C#)</span><span class="sxs-lookup"><span data-stu-id="a0033-130">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
