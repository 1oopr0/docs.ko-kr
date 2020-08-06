---
title: <permission> - C# 프로그래밍 가이드
description: XML <permission> 태그에 대해 알아봅니다. 이 태그를 사용하면 멤버의 액세스를 문서화할 수 있고, PermissionSet 클래스를 사용하면 멤버에 대한 액세스를 지정할 수 있습니다.
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 38c87505b8b2973875e474ffd296dc02b7fb9de6
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381725"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="9f5f1-105">\<permission>(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="9f5f1-105">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="9f5f1-106">구문</span><span class="sxs-lookup"><span data-stu-id="9f5f1-106">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="9f5f1-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9f5f1-107">Parameters</span></span>

- <span data-ttu-id="9f5f1-108">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="9f5f1-108">cref = " `member`"</span></span>

  <span data-ttu-id="9f5f1-109">현재 컴파일 환경에서 호출할 수 있는 멤버 또는 필드에 대한 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f1-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="9f5f1-110">컴파일러는 지정된 코드 요소가 있으며 `member`를 출력 XML의 정식 요소 이름으로 변환하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f1-110">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="9f5f1-111">*member*는 큰따옴표(“ ”)로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f1-111">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="9f5f1-112">제네릭 형식에 대한 cref 참조를 만드는 방법에 대한 자세한 내용은 [cref 특성](./cref-attribute.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f5f1-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="9f5f1-113">멤버 액세스 권한에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f1-113">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f5f1-114">설명</span><span class="sxs-lookup"><span data-stu-id="9f5f1-114">Remarks</span></span>

<span data-ttu-id="9f5f1-115">`<permission>` 태그를 사용하면 멤버 액세스 권한을 문서화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f1-115">The `<permission>` tag lets you document the access of a member.</span></span> <span data-ttu-id="9f5f1-116"><xref:System.Security.PermissionSet> 클래스를 사용하면 멤버 액세스 권한을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f1-116">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="9f5f1-117">[-doc](../../language-reference/compiler-options/doc-compiler-option.md)로 컴파일하여 문서 주석을 파일로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f1-117">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="9f5f1-118">예제</span><span class="sxs-lookup"><span data-stu-id="9f5f1-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="9f5f1-119">참조</span><span class="sxs-lookup"><span data-stu-id="9f5f1-119">See also</span></span>

- [<span data-ttu-id="9f5f1-120">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="9f5f1-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="9f5f1-121">문서 주석에 대한 권장 태그</span><span class="sxs-lookup"><span data-stu-id="9f5f1-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
