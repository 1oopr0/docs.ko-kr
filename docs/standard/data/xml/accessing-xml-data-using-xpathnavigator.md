---
title: XPathNavigator를 사용하여 XML 데이터 액세스
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: c57b46e6-5c77-408f-bc4e-67a5dcc9cc05
ms.openlocfilehash: 717937ebca9b5775619b0dde749f0566c73ca116
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290930"
---
# <a name="accessing-xml-data-using-xpathnavigator"></a><span data-ttu-id="6d6c7-102">XPathNavigator를 사용하여 XML 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="6d6c7-102">Accessing XML Data using XPathNavigator</span></span>
<span data-ttu-id="6d6c7-103"><xref:System.Xml.XPath.XPathNavigator> 클래스는 <xref:System.Xml.XPath.XPathDocument> 또는 <xref:System.Xml.XmlDocument> 개체에서 노드를 탐색하고 XML 데이터를 추출하고 강력한 형식의 XML 데이터에 액세스하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6d6c7-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d6c7-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="6d6c7-104">In This Section</span></span>  
 [<span data-ttu-id="6d6c7-105">XPathNavigator를 사용하여 노드 집합 탐색</span><span class="sxs-lookup"><span data-stu-id="6d6c7-105">Node Set Navigation Using XPathNavigator</span></span>](node-set-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="6d6c7-106"><xref:System.Xml.XPath.XPathNavigator> 또는 <xref:System.Xml.XPath.XPathDocument> 개체에서 노드를 탐색하는 데 사용하는 <xref:System.Xml.XmlDocument> 클래스의 노드 집합 탐색 메서드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6d6c7-106">Describes the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="6d6c7-107">XPathNavigator를 사용하여 특성 및 네임스페이스 노드 탐색</span><span class="sxs-lookup"><span data-stu-id="6d6c7-107">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="6d6c7-108"><xref:System.Xml.XPath.XPathNavigator> 클래스의 특성 및 네임스페이스 노드 탐색 메서드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6d6c7-108">Describes the attribute and namespace node navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="6d6c7-109">XPathNavigator를 사용하여 XML 데이터 추출</span><span class="sxs-lookup"><span data-stu-id="6d6c7-109">Extract XML Data Using XPathNavigator</span></span>](extract-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="6d6c7-110"><xref:System.Xml.XPath.XPathDocument> 또는 <xref:System.Xml.XmlDocument> 개체에서 XML 데이터를 추출하는 다양한 메서드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6d6c7-110">Describes the various methods of extracting XML data from an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="6d6c7-111">XPathNavigator를 사용하여 강력한 형식의 XML 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="6d6c7-111">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](accessing-strongly-typed-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="6d6c7-112"><xref:System.Xml.XPath.XPathNavigator> 클래스를 사용하여 <xref:System.Xml.XPath.XPathDocument> 또는 <xref:System.Xml.XmlDocument> 개체에서 강력한 형식의 XML 데이터에 액세스하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6d6c7-112">Describes accessing strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="6d6c7-113">사용자 정의 함수 및 변수</span><span class="sxs-lookup"><span data-stu-id="6d6c7-113">User Defined Functions and Variables</span></span>](user-defined-functions-and-variables.md)  
 <span data-ttu-id="6d6c7-114">확장 함수 및 변수를 지원하는 인터페이스 <xref:System.Xml.Xsl.XsltContext> 및 <xref:System.Xml.Xsl.IXsltContextFunction>과 함께 사용자 지정 <xref:System.Xml.Xsl.IXsltContextVariable> 클래스 구현에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6d6c7-114">Describes implementing a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d6c7-115">참조</span><span class="sxs-lookup"><span data-stu-id="6d6c7-115">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="6d6c7-116">XPath 데이터 모델을 사용하여 XML 데이터 처리</span><span class="sxs-lookup"><span data-stu-id="6d6c7-116">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="6d6c7-117">XPathDocument 및 XmlDocument를 사용하여 XML 데이터 읽기</span><span class="sxs-lookup"><span data-stu-id="6d6c7-117">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="6d6c7-118">XPathNavigator를 사용하여 XML 데이터 선택, 평가 및 일치시키기</span><span class="sxs-lookup"><span data-stu-id="6d6c7-118">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="6d6c7-119">XPathNavigator를 사용하여 XML 데이터 편집</span><span class="sxs-lookup"><span data-stu-id="6d6c7-119">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="6d6c7-120">XPathNavigator를 사용하여 스키마 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="6d6c7-120">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)
