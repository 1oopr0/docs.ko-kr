---
title: XML의 포함 식
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 44a6c3408b57fa7f89e2834aa677fe8801ef21f3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058315"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="d30ad-102">XML의 포함 식(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d30ad-102">Embedded Expressions in XML (Visual Basic)</span></span>

<span data-ttu-id="d30ad-103">포함 식을 사용 하면 런타임에 계산 되는 식을 포함 하는 XML 리터럴을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="d30ad-104">포함 식의 구문은 이며 `<%=` `expression` `%>` , ASP.NET에 사용 되는 구문과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in ASP.NET.</span></span>  
  
 <span data-ttu-id="d30ad-105">예를 들어, 포함 된 식을 리터럴 텍스트 콘텐츠와 결합 하 여 XML 요소 리터럴을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 <span data-ttu-id="d30ad-106">에 `isbnNumber` 정수 12345이 포함 되어 있고 `modifiedDate` 이 코드가 실행 될 때 날짜 3/5/2006를 포함 하는 경우의 값 `book` 은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="d30ad-107">포함 식 위치 및 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="d30ad-107">Embedded Expression Location and Validation</span></span>  

 <span data-ttu-id="d30ad-108">포함 식은 XML 리터럴 식 내의 특정 위치에만 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="d30ad-109">식 위치는 식에서 반환할 수 있는 형식과를 처리 하는 방법을 제어 합니다 `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="d30ad-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="d30ad-110">다음 표에서는 허용 되는 위치 및 포함 식의 유형에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="d30ad-111">리터럴의 위치</span><span class="sxs-lookup"><span data-stu-id="d30ad-111">Location in literal</span></span>|<span data-ttu-id="d30ad-112">식의 형식</span><span class="sxs-lookup"><span data-stu-id="d30ad-112">Type of expression</span></span>|<span data-ttu-id="d30ad-113">처리 `Nothing`</span><span class="sxs-lookup"><span data-stu-id="d30ad-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="d30ad-114">XML 요소 이름</span><span class="sxs-lookup"><span data-stu-id="d30ad-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="d30ad-115">Error</span><span class="sxs-lookup"><span data-stu-id="d30ad-115">Error</span></span>|  
|<span data-ttu-id="d30ad-116">XML 요소 내용</span><span class="sxs-lookup"><span data-stu-id="d30ad-116">XML element content</span></span>|<span data-ttu-id="d30ad-117">`Object` 또는 배열 `Object`</span><span class="sxs-lookup"><span data-stu-id="d30ad-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="d30ad-118">무시됨</span><span class="sxs-lookup"><span data-stu-id="d30ad-118">Ignored</span></span>|  
|<span data-ttu-id="d30ad-119">XML 요소 특성 이름</span><span class="sxs-lookup"><span data-stu-id="d30ad-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="d30ad-120">특성 값이 없는 경우 오류가 발생 합니다. `Nothing`</span><span class="sxs-lookup"><span data-stu-id="d30ad-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="d30ad-121">XML 요소 특성 값</span><span class="sxs-lookup"><span data-stu-id="d30ad-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="d30ad-122">특성 선언이 무시 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="d30ad-123">XML 요소 특성</span><span class="sxs-lookup"><span data-stu-id="d30ad-123">XML element attribute</span></span>|<span data-ttu-id="d30ad-124"><xref:System.Xml.Linq.XAttribute> 또는 컬렉션 <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="d30ad-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="d30ad-125">무시됨</span><span class="sxs-lookup"><span data-stu-id="d30ad-125">Ignored</span></span>|  
|<span data-ttu-id="d30ad-126">XML 문서 루트 요소</span><span class="sxs-lookup"><span data-stu-id="d30ad-126">XML document root element</span></span>|<span data-ttu-id="d30ad-127"><xref:System.Xml.Linq.XElement> 또는 하나의 <xref:System.Xml.Linq.XElement> 개체와 임의의 수의 <xref:System.Xml.Linq.XProcessingInstruction> 및 <xref:System.Xml.Linq.XComment> 개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="d30ad-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="d30ad-128">무시됨</span><span class="sxs-lookup"><span data-stu-id="d30ad-128">Ignored</span></span>|  
  
- <span data-ttu-id="d30ad-129">XML 요소 이름에 포함 된 식의 예:</span><span class="sxs-lookup"><span data-stu-id="d30ad-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- <span data-ttu-id="d30ad-130">XML 요소 내용에 포함 된 식의 예:</span><span class="sxs-lookup"><span data-stu-id="d30ad-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- <span data-ttu-id="d30ad-131">XML 요소 특성 이름에 포함 된 식의 예:</span><span class="sxs-lookup"><span data-stu-id="d30ad-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- <span data-ttu-id="d30ad-132">XML 요소 특성 값의 포함 식 예제:</span><span class="sxs-lookup"><span data-stu-id="d30ad-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- <span data-ttu-id="d30ad-133">XML 요소 특성에 포함 된 식의 예:</span><span class="sxs-lookup"><span data-stu-id="d30ad-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- <span data-ttu-id="d30ad-134">XML 문서 루트 요소에 포함 된 식의 예:</span><span class="sxs-lookup"><span data-stu-id="d30ad-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 <span data-ttu-id="d30ad-135">를 사용 하는 경우 `Option Strict` 컴파일러는 각 포함 된 식의 형식이 필요한 형식으로 확대 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="d30ad-136">유일한 예외는 XML 문서의 루트 요소입니다 .이 요소는 코드가 실행 될 때 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="d30ad-137">없이 컴파일하는 경우 `Option Strict` 형식의 식을 포함 `Object` 하 고 런타임에 해당 형식을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="d30ad-138">콘텐츠가 선택적인 위치에서를 포함 하는 포함 식은 `Nothing` 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="d30ad-139">즉, `Nothing` XML 리터럴을 사용 하기 전에 요소 내용, 특성 값 및 배열 요소를 확인 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="d30ad-140">요소 및 특성 이름과 같은 필수 값은 일 수 없습니다 `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="d30ad-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="d30ad-141">특정 형식의 리터럴에 포함 된 식을 사용 하는 방법에 대 한 자세한 내용은 [Xml 문서 리터럴](../../../language-reference/xml-literals/xml-document-literal.md), [xml 요소 리터럴](../../../language-reference/xml-literals/xml-element-literal.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d30ad-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="d30ad-142">범위 지정 규칙</span><span class="sxs-lookup"><span data-stu-id="d30ad-142">Scoping Rules</span></span>  

 <span data-ttu-id="d30ad-143">컴파일러는 각 XML 리터럴을 적절 한 리터럴 형식에 대 한 생성자 호출로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="d30ad-144">XML 리터럴의 리터럴 콘텐츠 및 포함 식은 생성자에 인수로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="d30ad-145">즉, XML 리터럴에 사용할 수 있는 모든 Visual Basic 프로그래밍 요소는 포함 된 식에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="d30ad-146">XML 리터럴 내에서 문으로 선언 된 XML 네임 스페이스 접두사에 액세스할 수 있습니다 `Imports` .</span><span class="sxs-lookup"><span data-stu-id="d30ad-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="d30ad-147">특성을 사용 하 여 요소에서 새 XML 네임 스페이스 접두사를 선언 하거나 기존 XML 네임 스페이스 접두사를 숨길 수 있습니다 `xmlns` .</span><span class="sxs-lookup"><span data-stu-id="d30ad-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="d30ad-148">새 네임 스페이스는 해당 요소의 자식 노드에서 사용할 수 있지만 포함 식의 XML 리터럴이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d30ad-149">네임 스페이스 특성을 사용 하 여 XML 네임 스페이스 접두사를 선언 하는 경우 `xmlns` 특성 값은 상수 문자열 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="d30ad-150">이와 관련 하 여 특성을 사용 하는 `xmlns` 것은 문을 사용 하 여 `Imports` XML 네임 스페이스를 선언 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="d30ad-151">포함 식을 사용 하 여 XML 네임 스페이스 값을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d30ad-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d30ad-152">참조</span><span class="sxs-lookup"><span data-stu-id="d30ad-152">See also</span></span>

- [<span data-ttu-id="d30ad-153">Visual Basic에서 XML 만들기</span><span class="sxs-lookup"><span data-stu-id="d30ad-153">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="d30ad-154">XML 문서 리터럴</span><span class="sxs-lookup"><span data-stu-id="d30ad-154">XML Document Literal</span></span>](../../../language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="d30ad-155">XML 요소 리터럴</span><span class="sxs-lookup"><span data-stu-id="d30ad-155">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="d30ad-156">Option Strict 문</span><span class="sxs-lookup"><span data-stu-id="d30ad-156">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="d30ad-157">Imports 문(.NET 네임스페이스 및 형식)</span><span class="sxs-lookup"><span data-stu-id="d30ad-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="d30ad-158">XML 리터럴 개요</span><span class="sxs-lookup"><span data-stu-id="d30ad-158">XML Literals Overview</span></span>](xml-literals-overview.md)
