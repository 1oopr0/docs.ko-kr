---
title: XElement 및 XDocument 개체의 유효한 콘텐츠3
description: 생성자에 전달될 수 있는 유효한 인수에 대해 알아보고 요소 및 문서에 콘텐츠를 추가하는 데 사용하는 메서드에 대해 알아봅니다.
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: dfafbe76b078db6c22b475770ebadaff38c75ba8
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302258"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="6c38f-103">XElement 및 XDocument 개체의 올바른 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="6c38f-103">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="6c38f-104">이 항목에서는 생성자에 전달될 수 있는 유효한 인수에 대해 설명하고 내용을 요소와 문서에 추가하는 데 사용하는 메서드에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-104">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="6c38f-105">유효한 내용</span><span class="sxs-lookup"><span data-stu-id="6c38f-105">Valid Content</span></span>  
 <span data-ttu-id="6c38f-106">쿼리는 흔히 <xref:System.Collections.Generic.IEnumerable%601>의 <xref:System.Xml.Linq.XElement> 또는 <xref:System.Collections.Generic.IEnumerable%601>의 <xref:System.Xml.Linq.XAttribute>로 확인되며,</span><span class="sxs-lookup"><span data-stu-id="6c38f-106">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="6c38f-107"><xref:System.Xml.Linq.XElement> 또는 <xref:System.Xml.Linq.XAttribute> 개체의 컬렉션은 <xref:System.Xml.Linq.XElement> 생성자로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-107">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="6c38f-108">따라서 XML 트리를 채우는 데 사용하는 메서드와 생성자에 쿼리의 결과를 내용으로 전달하는 것이 편리합니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-108">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="6c38f-109">간단한 내용을 추가할 때 다양한 형식이 이 메서드에 전달될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-109">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="6c38f-110">유효한 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-110">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="6c38f-111">`Object.ToString`을 구현하는 임의의 형식</span><span class="sxs-lookup"><span data-stu-id="6c38f-111">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="6c38f-112"><xref:System.Collections.Generic.IEnumerable%601>을 구현하는 임의의 형식</span><span class="sxs-lookup"><span data-stu-id="6c38f-112">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="6c38f-113">복잡한 내용을 추가할 때 다양한 형식이 이 메서드에 전달될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-113">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="6c38f-114"><xref:System.Collections.Generic.IEnumerable%601>을 구현하는 임의의 형식</span><span class="sxs-lookup"><span data-stu-id="6c38f-114">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="6c38f-115">개체가 <xref:System.Collections.Generic.IEnumerable%601>을 구현하는 경우 개체의 컬렉션이 열거되고 컬렉션의 모든 항목이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-115">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="6c38f-116">컬렉션에 <xref:System.Xml.Linq.XNode> 또는 <xref:System.Xml.Linq.XAttribute> 개체가 포함되어 있으면 컬렉션의 각 항목이 개별적으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-116">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="6c38f-117">컬렉션에 텍스트(또는 텍스트로 변환된 개체)가 포함되어 있으면 컬렉션의 텍스트가 연결되어 단일 텍스트 노드로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-117">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="6c38f-118">내용이 `null`이면 아무 것도 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-118">If content is `null`, nothing is added.</span></span> <span data-ttu-id="6c38f-119">컬렉션을 전달할 때 컬렉션의 항목은 `null`일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-119">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="6c38f-120">컬렉션의 `null` 항목은 트리에 아무 영향도 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-120">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="6c38f-121">추가된 특성은 포함하는 요소에서 고유한 이름을 갖고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-121">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="6c38f-122"><xref:System.Xml.Linq.XNode> 또는 <xref:System.Xml.Linq.XAttribute> 개체를 추가할 때 새 내용에 부모가 없으면 개체가 XML 트리에 추가되기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-122">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="6c38f-123">새 내용이 이미 부모를 갖고 있고 다른 XML 트리의 일부이면 새 내용이 복제되고 새로 복제된 내용이 XML 트리에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-123">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="6c38f-124">문서의 유효한 내용</span><span class="sxs-lookup"><span data-stu-id="6c38f-124">Valid Content for Documents</span></span>  
 <span data-ttu-id="6c38f-125">특성과 간단한 내용은 문서에 추가될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-125">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="6c38f-126"><xref:System.Xml.Linq.XDocument>를 만들어야 하는 시나리오는 많지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-126">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="6c38f-127">대신 일반적으로 <xref:System.Xml.Linq.XElement> 루트 노드를 사용하여 XML 트리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-127">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="6c38f-128">문서를 만들어야 하는 특정 요구 사항(예를 들어, 최상위 수준에서 처리 명령과 주석을 만들어야 하거나 문서 형식을 지원해야 하는 경우)이 없는 한 <xref:System.Xml.Linq.XElement>를 루트 노드로 사용하는 것이 더 편리한 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-128">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="6c38f-129">문서의 유효한 내용은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-129">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="6c38f-130">0개나 1개의 <xref:System.Xml.Linq.XDocumentType> 개체.</span><span class="sxs-lookup"><span data-stu-id="6c38f-130">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="6c38f-131">문서 형식이 요소 앞에 나와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-131">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="6c38f-132">0개나 1개의 요소</span><span class="sxs-lookup"><span data-stu-id="6c38f-132">Zero or one element.</span></span>  
  
- <span data-ttu-id="6c38f-133">0개 이상의 주석</span><span class="sxs-lookup"><span data-stu-id="6c38f-133">Zero or more comments.</span></span>  
  
- <span data-ttu-id="6c38f-134">0개 이상의 처리 명령</span><span class="sxs-lookup"><span data-stu-id="6c38f-134">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="6c38f-135">공백만 포함된 0개 이상의 텍스트 노드</span><span class="sxs-lookup"><span data-stu-id="6c38f-135">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="6c38f-136">내용 추가를 허용하는 생성자 및 함수</span><span class="sxs-lookup"><span data-stu-id="6c38f-136">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="6c38f-137">다음 메서드를 사용하여 자식 내용을 <xref:System.Xml.Linq.XElement> 또는 <xref:System.Xml.Linq.XDocument>에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-137">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="6c38f-138">메서드</span><span class="sxs-lookup"><span data-stu-id="6c38f-138">Method</span></span>|<span data-ttu-id="6c38f-139">설명</span><span class="sxs-lookup"><span data-stu-id="6c38f-139">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="6c38f-140"><xref:System.Xml.Linq.XElement>를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-140">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="6c38f-141"><xref:System.Xml.Linq.XDocument>를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-141">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="6c38f-142"><xref:System.Xml.Linq.XElement> 또는 <xref:System.Xml.Linq.XDocument>의 자식 내용 끝 부분에 내용을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-142">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="6c38f-143"><xref:System.Xml.Linq.XNode> 뒤에 내용을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-143">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="6c38f-144"><xref:System.Xml.Linq.XNode> 앞에 내용을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-144">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="6c38f-145"><xref:System.Xml.Linq.XContainer>의 자식 내용 시작 부분에 내용을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-145">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="6c38f-146"><xref:System.Xml.Linq.XElement>의 모든 내용(자식 노드 및 특성)을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-146">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="6c38f-147"><xref:System.Xml.Linq.XElement>의 특성을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-147">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="6c38f-148">자식 노드를 새 내용으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-148">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="6c38f-149">노드를 새 내용으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6c38f-149">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c38f-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6c38f-150">See also</span></span>

- [<span data-ttu-id="6c38f-151">XML 트리 만들기(C#)</span><span class="sxs-lookup"><span data-stu-id="6c38f-151">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
