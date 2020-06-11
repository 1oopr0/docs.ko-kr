---
title: <value> - C# 프로그래밍 가이드
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: bd6630a8d5894fda39ad289c8dd584f6d84e5490
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287196"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="465c4-102">\<value>(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="465c4-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="465c4-103">구문</span><span class="sxs-lookup"><span data-stu-id="465c4-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="465c4-104">매개 변수</span><span class="sxs-lookup"><span data-stu-id="465c4-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="465c4-105">속성에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="465c4-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="465c4-106">설명</span><span class="sxs-lookup"><span data-stu-id="465c4-106">Remarks</span></span>

<span data-ttu-id="465c4-107">`<value>` 태그를 사용하면 속성이 나타내는 값을 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="465c4-107">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="465c4-108">Visual Studio .NET 개발 환경에서 코드 마법사를 통해 속성을 추가하면 새 속성에 대해 [\<summary>](./summary.md) 태그가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="465c4-108">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="465c4-109">그런 다음, `<value>` 태그를 수동으로 추가하여 속성이 나타내는 값을 설명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="465c4-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="465c4-110">[-doc](../../language-reference/compiler-options/doc-compiler-option.md)로 컴파일하여 문서 주석을 파일로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="465c4-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="465c4-111">예제</span><span class="sxs-lookup"><span data-stu-id="465c4-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="465c4-112">참조</span><span class="sxs-lookup"><span data-stu-id="465c4-112">See also</span></span>

- [<span data-ttu-id="465c4-113">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="465c4-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="465c4-114">문서 주석에 대한 권장 태그</span><span class="sxs-lookup"><span data-stu-id="465c4-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
