---
title: XDocument 클래스 개요
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: 90c97349006407b2eca861be31080ec17901fa5b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413234"
---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="e7203-102">XDocument 클래스 개요 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7203-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="e7203-103">이 항목에서는 <xref:System.Xml.Linq.XDocument> 클래스에 대해 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="e7203-104">XDocument 클래스 개요</span><span class="sxs-lookup"><span data-stu-id="e7203-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="e7203-105"><xref:System.Xml.Linq.XDocument> 클래스에는 유효한 XML 문서에 필요한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="e7203-106">여기에는 XML 선언, 처리 명령 및 주석이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="e7203-107"><xref:System.Xml.Linq.XDocument> 클래스에서 제공하는 특정 기능이 필요한 경우 <xref:System.Xml.Linq.XDocument> 개체만 만들면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="e7203-108">대부분의 경우 <xref:System.Xml.Linq.XElement>로 직접 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="e7203-109"><xref:System.Xml.Linq.XElement>로 직접 작업하는 것이 더 간단한 프로그래밍 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="e7203-110"><xref:System.Xml.Linq.XDocument>은 <xref:System.Xml.Linq.XContainer>로부터 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="e7203-111">자식 노드를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="e7203-112">그러나 <xref:System.Xml.Linq.XDocument> 개체에는 자식 <xref:System.Xml.Linq.XElement> 노드가 하나만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="e7203-113">이는 XML 문서에 루트 요소가 하나만 있어야 하는 XML 표준을 반영하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="e7203-114">XDocument의 구성 요소</span><span class="sxs-lookup"><span data-stu-id="e7203-114">Components of XDocument</span></span>  
 <span data-ttu-id="e7203-115"><xref:System.Xml.Linq.XDocument>에는 다음과 같은 요소가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="e7203-116"><xref:System.Xml.Linq.XDeclaration> 개체 하나.</span><span class="sxs-lookup"><span data-stu-id="e7203-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="e7203-117"><xref:System.Xml.Linq.XDeclaration>을 통해 XML 선언의 관련 부분인 XML 버전, 문서의 인코딩 및 XML 문서가 독립 실행형인지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="e7203-118"><xref:System.Xml.Linq.XElement> 개체 하나.</span><span class="sxs-lookup"><span data-stu-id="e7203-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="e7203-119">이 개체는 XML 문서의 루트 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="e7203-120"><xref:System.Xml.Linq.XProcessingInstruction> 개체(수에 제한 없음).</span><span class="sxs-lookup"><span data-stu-id="e7203-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="e7203-121">처리 명령은 XML을 처리하는 정보를 애플리케이션에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="e7203-122"><xref:System.Xml.Linq.XComment> 개체(수에 제한 없음).</span><span class="sxs-lookup"><span data-stu-id="e7203-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="e7203-123">주석은 루트 요소의 형제입니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="e7203-124">XML 문서는 주석으로 시작될 수 없으므로 <xref:System.Xml.Linq.XComment> 개체는 목록의 첫 번째 인수일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="e7203-125">DTD에 대한 <xref:System.Xml.Linq.XDocumentType> 하나</span><span class="sxs-lookup"><span data-stu-id="e7203-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="e7203-126"><xref:System.Xml.Linq.XDocument>를 serialize할 때 `XDocument.Declaration`이 `null`인 경우에도 작성기의 `Writer.Settings.OmitXmlDeclaration`이 `false`(기본값)로 설정되어 있으면 출력에 XML 선언이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="e7203-127">기본적으로 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]에서는 버전을 "1.0"으로 설정하고 인코딩을 "utf-8"로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="e7203-128">XDocument 없이 XElement 사용</span><span class="sxs-lookup"><span data-stu-id="e7203-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="e7203-129">앞에서 설명했듯이 <xref:System.Xml.Linq.XElement> 클래스는 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 프로그래밍 인터페이스의 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="e7203-130">애플리케이션에서는 대부분의 경우 문서를 만들도록 요구하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="e7203-131"><xref:System.Xml.Linq.XElement> 클래스를 사용하여 XML 트리를 만들고, XML 트리에 다른 XML 트리를 추가하고, XML 트리를 수정 및 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="e7203-132">XDocument 사용</span><span class="sxs-lookup"><span data-stu-id="e7203-132">Using XDocument</span></span>  
 <span data-ttu-id="e7203-133"><xref:System.Xml.Linq.XDocument>를 생성하려면 <xref:System.Xml.Linq.XElement> 개체를 생성할 때와 마찬가지로 함수 생성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="e7203-134">다음 코드에서는 <xref:System.Xml.Linq.XDocument> 개체와 포함된 관련 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 <span data-ttu-id="e7203-135">test.xml 파일을 검사할 때 다음과 같은 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7203-135">When you examine the file test.xml, you get the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7203-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7203-136">See also</span></span>

- [<span data-ttu-id="e7203-137">LINQ to XML 프로그래밍 개요 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7203-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
