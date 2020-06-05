---
title: LINQ to XML과 비교 DOM 비교
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: 5813ca410e3e2b1ec284681451d0c0cec6f5e393
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389334"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a><span data-ttu-id="fb936-102">LINQ to XML과 DOM 비교(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb936-102">LINQ to XML vs. DOM (Visual Basic)</span></span>
<span data-ttu-id="fb936-103">이 섹션에서는 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]과 현재 주로 사용되는 XML 프로그래밍 API인 W3C DOM(문서 개체 모델)의 몇 가지 주요 차이점에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="fb936-104">XML 트리를 생성하는 새로운 방법</span><span class="sxs-lookup"><span data-stu-id="fb936-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="fb936-105">W3C DOM에서는 상향식으로 XML 트리를 빌드합니다. 즉, 문서를 만들고 요소를 만든 다음 요소를 문서에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="fb936-106">예를 들어, DOM의 Microsoft 구현인 <xref:System.Xml.XmlDocument>를 사용하여 XML 트리를 만드는 일반적인 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
Dim phone1 As XmlElement = doc.CreateElement("Phone")  
phone1.SetAttribute("Type", "Home")  
phone1.InnerText = "206-555-0144"  
Dim phone2 As XmlElement = doc.CreateElement("Phone")  
phone2.SetAttribute("Type", "Work")  
phone2.InnerText = "425-555-0145"  
Dim street1 As XmlElement = doc.CreateElement("Street1")  
street1.InnerText = "123 Main St"  
Dim city As XmlElement = doc.CreateElement("City")  
city.InnerText = "Mercer Island"  
Dim state As XmlElement = doc.CreateElement("State")  
state.InnerText = "WA"  
Dim postal As XmlElement = doc.CreateElement("Postal")  
postal.InnerText = "68042"  
Dim address As XmlElement = doc.CreateElement("Address")  
address.AppendChild(street1)  
address.AppendChild(city)  
address.AppendChild(state)  
address.AppendChild(postal)  
Dim contact As XmlElement = doc.CreateElement("Contact")  
contact.AppendChild(name)  
contact.AppendChild(phone1)  
contact.AppendChild(phone2)  
contact.AppendChild(address)  
Dim contacts As XmlElement = doc.CreateElement("Contacts")  
contacts.AppendChild(contact)  
doc.AppendChild(contacts)  
Console.WriteLine(doc.OuterXml)  
```  
  
 <span data-ttu-id="fb936-107">이 코딩 스타일은 XML 트리의 구조에 대한 많은 정보를 시각적으로 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb936-108">에서는 이러한 XML 트리 생성 방법을 지원하지만 다른 방법인 *함수 생성*도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-108">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="fb936-109">Visual Basic에서 함수 생성은 XML 리터럴을 사용 하 여 XML 트리를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-109">In Visual Basic, functional construction uses XML literals to build an XML tree.</span></span>  
  
 <span data-ttu-id="fb936-110">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 함수 생성을 사용하여 동일한 XML 트리를 생성하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
```vb  
Dim contacts = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="Home">206-555-0144</Phone>  
            <Phone Type="Work">425-555-0145</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 <span data-ttu-id="fb936-111">XML 트리를 생성하는 코드의 들여쓰기는 기본 XML의 구조를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="fb936-112">자세한 내용은 [XML 트리 만들기 (Visual Basic)](creating-xml-trees.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fb936-112">For more information, see [Creating XML Trees (Visual Basic)](creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="fb936-113">XML 요소로 직접 작업</span><span class="sxs-lookup"><span data-stu-id="fb936-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="fb936-114">XML을 사용하여 프로그래밍하는 경우 XML 요소를 대개 집중적으로 다루고 특성도 집중적으로 다룰 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="fb936-115">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]에서는 XML 요소 및 특성으로 직접 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="fb936-116">예를 들어, 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-116">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="fb936-117">문서 개체를 전혀 사용하지 않고 XML 요소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="fb936-118">이에 따라 XML 트리의 조각으로 작업해야 하는 경우 프로그래밍이 단순해집니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="fb936-119">XML 파일에서 `T:System.Xml.Linq.XElement` 개체를 직접 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="fb936-120">`T:System.Xml.Linq.XElement` 개체를 파일이나 스트림으로 serialize합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="fb936-121">이와 비교할 때 W3C DOM에서는 XML 문서가 XML 트리의 논리 컨테이너로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="fb936-122">DOM에서 요소 및 특성을 비롯한 XML 노드는 XML 문서의 컨텍스트에서 만들어져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="fb936-123">DOM에서 이름 요소를 만드는 코드의 조각은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 <span data-ttu-id="fb936-124">여러 문서에서 요소를 사용하려면 여러 문서의 노드를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb936-125">에서는 이러한 복잡한 작업이 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-125">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="fb936-126">LINQ to XML을 사용할 때 문서의 루트 수준에서 주석이나 처리 명령을 추가하려는 경우에만 <xref:System.Xml.Linq.XDocument> 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="fb936-127">이름 및 네임스페이스의 간단한 처리</span><span class="sxs-lookup"><span data-stu-id="fb936-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="fb936-128">이름, 네임스페이스 및 네임스페이스 접두사의 처리는 대개 XML 프로그래밍의 복잡한 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb936-129">에서는 네임스페이스 접두사를 처리해야 하는 요구 사항을 제거하여 이름과 네임스페이스를 단순화합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-129">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="fb936-130">네임스페이스 접두사를 제어하고 싶으면 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="fb936-131">그러나 네임스페이스 접두사를 명시적으로 제어하지 않도록 결정하는 경우 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]에서는 serialize할 때 필요한 경우 네임스페이스 접두사를 할당하거나, 기본 네임스페이스를 사용하여 serialize합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="fb936-132">기본 네임스페이스가 사용되는 경우 생성되는 문서에는 네임스페이스 접두사가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="fb936-133">자세한 내용은 [네임 스페이스 개요 (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fb936-133">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="fb936-134">DOM의 또 다른 문제는 노드의 이름을 변경할 수 없다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="fb936-135">대신 새 노드를 만들고 모든 자식 노드를 새 노드에 복사해야 하므로 원래 노드 ID가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb936-136">에서는 노드에서 <xref:System.Xml.Linq.XName> 속성을 설정할 수 있도록 하여 이 문제를 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-136">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="fb936-137">XML을 로드하기 위한 정적 메서드 지원</span><span class="sxs-lookup"><span data-stu-id="fb936-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb936-138">에서는 인스턴스 메서드 대신 정적 메서드를 사용하여 XML을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-138">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="fb936-139">이에 따라 로드와 구문 분석이 간단해집니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="fb936-140">자세한 내용은 [방법: 파일에서 XML 로드 (Visual Basic)](how-to-load-xml-from-a-file.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fb936-140">For more information, see [How to: Load XML from a File (Visual Basic)](how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="fb936-141">DTD 구문에 대한 지원 제거</span><span class="sxs-lookup"><span data-stu-id="fb936-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb936-142">에서는 엔터티와 엔터티 참조에 대한 지원 기능을 제거하여 XML 프로그래밍을 더욱 단순화합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-142">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="fb936-143">엔터티의 관리는 복잡하므로 드물게 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="fb936-144">이러한 지원 기능을 제거하면 성능이 향상되고 프로그래밍 인터페이스가 간단해집니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="fb936-145">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 트리가 채워지면 모든 DTD 엔터티가 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="fb936-146">조각에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="fb936-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb936-147">에서는 `XmlDocumentFragment` 클래스와 동일한 항목을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-147">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="fb936-148">그러나 대부분의 경우에 `XmlDocumentFragment` 개념은 <xref:System.Collections.Generic.IEnumerable%601>의 <xref:System.Xml.Linq.XNode>이나 <xref:System.Collections.Generic.IEnumerable%601>의 <xref:System.Xml.Linq.XElement>로 형식화된 쿼리의 결과에 의해 처리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="fb936-149">XPathNavigator에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="fb936-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb936-150">에서는 <xref:System.Xml.XPath.XPathNavigator> 네임스페이스의 확장 메서드를 통해 <xref:System.Xml.XPath?displayProperty=nameWithType>를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-150">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="fb936-151">자세한 내용은 <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb936-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="fb936-152">공백 및 들여쓰기에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="fb936-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb936-153">에서는 DOM의 경우보다 간단하게 공백을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-153">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="fb936-154">일반적인 시나리오는 들여쓴 XML을 읽고 공백 텍스트 노드 없이 메모리 내 XML 트리를 만든 다음(공백을 유지하지 않음) XML에 대한 작업을 수행하고 들여쓰기를 사용하여 XML을 저장하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="fb936-155">서식이 있는 XML을 serialize하는 경우 XML 트리의 유효 공백만 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="fb936-156">이것이 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]의 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="fb936-157">다른 일반적인 시나리오는 이미 의도적으로 들여쓴 XML을 읽고 수정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="fb936-158">이 들여쓰기를 변경하려고 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="fb936-159">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]에서는 XML을 로드하거나 구문 분석할 때 공백을 유지하고 XML을 serialize할 때 서식을 해제하는 경우 이렇게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb936-160">에서는 DOM의 경우처럼 serialize된 <xref:System.Xml.Linq.XText> 노드 형식을 사용하는 대신 <xref:System.Xml.XmlNodeType.Whitespace> 노드로 공백을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-160">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="fb936-161">주석에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="fb936-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="fb936-162">요소는 확장 가능한 주석 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-162">elements support an extensible set of annotations.</span></span> <span data-ttu-id="fb936-163">이러한 지원은 스키마 정보, 요소가 UI에 바인딩되어 있는지 여부 또는 다른 종류의 애플리케이션 관련 정보와 같은 요소에 대한 기타 정보를 추적하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="fb936-164">자세한 내용은 [LINQ to XML 주석](linq-to-xml-annotations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb936-164">For more information, see [LINQ to XML Annotations](linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="fb936-165">스키마 정보에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="fb936-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb936-166">에서는 <xref:System.Xml.Schema?displayProperty=nameWithType> 네임스페이스의 확장 메서드를 통해 XSD 유효성 검사를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-166">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="fb936-167">XML 트리가 XSD를 준수하는지 확인할 수 있으며,</span><span class="sxs-lookup"><span data-stu-id="fb936-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="fb936-168">PSVI(Post-Schema-Validation Infoset)를 사용하여 XML 트리를 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb936-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="fb936-169">자세한 내용은 [방법: XSD 및를 사용 하 여 유효성 검사](how-to-validate-using-xsd-linq-to-xml.md) 를 참조 하세요 <xref:System.Xml.Schema.Extensions> .</span><span class="sxs-lookup"><span data-stu-id="fb936-169">For more information, see [How to: Validate Using XSD](how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb936-170">참조</span><span class="sxs-lookup"><span data-stu-id="fb936-170">See also</span></span>

- [<span data-ttu-id="fb936-171">시작(LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="fb936-171">Getting Started (LINQ to XML)</span></span>](getting-started-linq-to-xml.md)
