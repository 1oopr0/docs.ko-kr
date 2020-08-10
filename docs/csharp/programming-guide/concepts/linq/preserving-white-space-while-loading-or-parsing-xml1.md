---
title: XML을 로드 또는 구문 분석할 때 공백 유지
description: Xml을 로드하거나 구문 분석하는 동안 공백 동작, 특히 XML 트리를 채우는 메서드의 동작을 제어하는 방법을 알아봅니다.
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: 3c044937d38f9f89ebc114af3eddbf5116c392ad
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302843"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a><span data-ttu-id="570e2-103">XML을 로드 또는 구문 분석할 때 공백 유지</span><span class="sxs-lookup"><span data-stu-id="570e2-103">Preserving White Space while Loading or Parsing XML</span></span>
<span data-ttu-id="570e2-104">이 항목에서는 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]의 공백 동작을 제어하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-104">This topic describes how to control the white-space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="570e2-105">일반적인 시나리오는 들여쓴 XML을 읽고 공백 텍스트 노드 없이 메모리 내 XML 트리를 만든 다음(공백을 유지하지 않음) XML에 대한 작업을 수행하고 들여쓰기를 사용하여 XML을 저장하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-105">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="570e2-106">서식이 있는 XML을 serialize하는 경우 XML 트리의 유효 공백만 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-106">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="570e2-107">이것이 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]의 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-107">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="570e2-108">다른 일반적인 시나리오는 이미 의도적으로 들여쓴 XML을 읽고 수정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-108">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="570e2-109">이 들여쓰기를 변경하려고 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-109">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="570e2-110">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]에서는 XML을 로드하거나 구문 분석할 때 공백을 유지하고 XML을 serialize할 때 서식을 해제하는 경우 이렇게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-110">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
 <span data-ttu-id="570e2-111">이 항목에서는 XML 트리를 채우는 메서드의 공백 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-111">This topic describes the white-space behavior of methods that populate XML trees.</span></span> <span data-ttu-id="570e2-112">XML 트리를 serialize할 때 공백을 제어하는 방법에 대한 자세한 내용은 [serialize할 때 공백 유지](./preserving-white-space-while-serializing.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="570e2-112">For information about controlling white space when you serialize XML trees, see [Preserving White Space While Serializing](./preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a><span data-ttu-id="570e2-113">XML 트리를 채우는 메서드의 동작</span><span class="sxs-lookup"><span data-stu-id="570e2-113">Behavior of Methods that Populate XML Trees</span></span>  
 <span data-ttu-id="570e2-114"><xref:System.Xml.Linq.XElement> 및 <xref:System.Xml.Linq.XDocument> 클래스의 다음 메서드는 XML 트리를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-114">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes populate an XML tree.</span></span> <span data-ttu-id="570e2-115">파일, <xref:System.IO.TextReader>, <xref:System.Xml.XmlReader> 또는 문자열에서 XML 트리를 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-115">You can populate an XML tree from a file, a <xref:System.IO.TextReader>, an <xref:System.Xml.XmlReader>, or a string:</span></span>  
  
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="570e2-116">메서드에서 <xref:System.Xml.Linq.LoadOptions>를 인수로 사용하지 않는 경우 무효 공백을 유지하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-116">If the method does not take <xref:System.Xml.Linq.LoadOptions> as an argument, the method will not preserve insignificant white space.</span></span>  
  
 <span data-ttu-id="570e2-117">대부분의 경우 메서드에서 <xref:System.Xml.Linq.LoadOptions>를 인수로 사용하면 XML 트리의 텍스트 노드로 무효 공백을 선택적으로 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-117">In most cases, if the method takes <xref:System.Xml.Linq.LoadOptions> as an argument, you can optionally preserve insignificant white space as text nodes in the XML tree.</span></span> <span data-ttu-id="570e2-118">그러나 메서드가 <xref:System.Xml.XmlReader>에서 XML을 로드하는 경우에는 <xref:System.Xml.XmlReader>가 공백을 유지할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-118">However, if the method is loading the XML from an <xref:System.Xml.XmlReader>, then the <xref:System.Xml.XmlReader> determines whether white space will be preserved or not.</span></span> <span data-ttu-id="570e2-119"><xref:System.Xml.Linq.LoadOptions.PreserveWhitespace>를 설정해도 아무런 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-119">Setting <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> will have no effect.</span></span>  
  
 <span data-ttu-id="570e2-120">이러한 메서드를 사용하는 경우 공백이 유지되면 무효 공백이 XML 트리에 <xref:System.Xml.Linq.XText> 노드로 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-120">With these methods, if white space is preserved, insignificant white space is inserted into the XML tree as <xref:System.Xml.Linq.XText> nodes.</span></span> <span data-ttu-id="570e2-121">공백이 유지되지 않으면 텍스트 노드가 삽입되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-121">If white space is not preserved, text nodes are not inserted.</span></span>  
  
 <span data-ttu-id="570e2-122"><xref:System.Xml.XmlWriter>를 사용하여 XML 트리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-122">You can create an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="570e2-123"><xref:System.Xml.XmlWriter>에 쓴 노드가 트리에 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-123">Nodes that are written to the <xref:System.Xml.XmlWriter> are populated in the tree.</span></span> <span data-ttu-id="570e2-124">그러나 이 메서드를 사용하여 XML 트리를 빌드하면 노드가 공백인지 여부나 유효한지 여부에 관계없이 모든 노드가 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="570e2-124">However, when you build an XML tree using this method, all nodes are preserved, regardless of whether the node is white space or not, or whether the white space is significant or not.</span></span>  
  