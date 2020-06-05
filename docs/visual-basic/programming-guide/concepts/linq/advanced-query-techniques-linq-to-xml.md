---
title: 고급 쿼리 기술(LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 79be877c-fadc-4dfb-9f03-426082b13656
ms.openlocfilehash: ca4460ec4d35b1bccf1b0a48dd806cf07e79c572
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383808"
---
# <a name="advanced-query-techniques-linq-to-xml-visual-basic"></a><span data-ttu-id="2eab7-102">LINQ to XML (고급 쿼리 기술) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2eab7-102">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="2eab7-103">이 단원에서는 고급 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 쿼리 기법의 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2eab7-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2eab7-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="2eab7-104">In This Section</span></span>  
  
|<span data-ttu-id="2eab7-105">항목</span><span class="sxs-lookup"><span data-stu-id="2eab7-105">Topic</span></span>|<span data-ttu-id="2eab7-106">Description</span><span class="sxs-lookup"><span data-stu-id="2eab7-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2eab7-107">방법: 두 컬렉션 조인 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2eab7-107">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>](how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="2eab7-108">`Join` 절을 사용하여 XML 데이터의 관계를 이용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eab7-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="2eab7-109">방법: 그룹화를 사용 하 여 계층 구조 만들기 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2eab7-109">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>](how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="2eab7-110">데이터를 그룹화한 다음 그룹화에 따라 XML을 생성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eab7-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="2eab7-111">방법: XPath를 사용 하 여 LINQ to XML 쿼리 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2eab7-111">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>](how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="2eab7-112">XPath 쿼리를 기반으로 컬렉션을 검색하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eab7-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="2eab7-113">방법: LINQ to XML 축 메서드 작성 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2eab7-113">How to: Write a LINQ to XML Axis Method (Visual Basic)</span></span>](how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="2eab7-114">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 축 메서드를 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2eab7-114">Shows how to write a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axis method.</span></span>|  
|[<span data-ttu-id="2eab7-115">방법: 트리의 모든 노드 나열 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2eab7-115">How to: List All Nodes in a Tree (Visual Basic)</span></span>](how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="2eab7-116">XML 트리의 모든 노드를 나열하는 유틸리티 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2eab7-116">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="2eab7-117">이 메서드는 XML 트리를 수정하는 디버깅 코드에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2eab7-117">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="2eab7-118">방법: Office Open XML 문서에서 단락 검색 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2eab7-118">How to: Retrieve Paragraphs from an Office Open XML Document (Visual Basic)</span></span>](how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="2eab7-119">Office Open XML 문서를 열고 XElement 개체 컬렉션의 단락, 단락의 텍스트 및 단락의 스타일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="2eab7-119">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="2eab7-120">방법: Office Open XML 문서 수정 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2eab7-120">How to: Modify an Office Open XML Document (Visual Basic)</span></span>](how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="2eab7-121">Office Open XML 문서를 열고, 수정하고, 저장하는 코드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2eab7-121">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="2eab7-122">방법: 파일 시스템에서 XML 트리 채우기 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2eab7-122">How to: Populate an XML Tree from the File System (Visual Basic)</span></span>](how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="2eab7-123">파일 시스템에서 XML 트리를 만드는 코드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2eab7-123">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2eab7-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2eab7-124">See also</span></span>

- [<span data-ttu-id="2eab7-125">XML 트리 쿼리(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2eab7-125">Querying XML Trees (Visual Basic)</span></span>](querying-xml-trees.md)
