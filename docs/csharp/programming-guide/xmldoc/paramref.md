---
title: <paramref> - C# 프로그래밍 가이드
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 4f3b521d24c8b4677a05b0b145cb36c31b2793f2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287313"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="f515d-102">\<paramref>(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="f515d-102">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="f515d-103">구문</span><span class="sxs-lookup"><span data-stu-id="f515d-103">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="f515d-104">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f515d-104">Parameters</span></span>

- `name`

  <span data-ttu-id="f515d-105">참조할 매개 변수의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f515d-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="f515d-106">이름을 큰따옴표(“ ”)로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="f515d-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="f515d-107">설명</span><span class="sxs-lookup"><span data-stu-id="f515d-107">Remarks</span></span>

<span data-ttu-id="f515d-108">`<paramref>` 태그를 사용하면 `<summary>` 또는 `<remarks>` 블록 등의 코드 주석에 포함된 단어가 매개 변수를 참조함을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f515d-108">The `<paramref>` tag gives you a way to indicate that a word in the code comments, for example in a `<summary>` or `<remarks>` block refers to a parameter.</span></span> <span data-ttu-id="f515d-109">XML 파일을 처리하여 굵게, 기울임꼴 글꼴 등의 고유한 방식으로 이 단어에 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f515d-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="f515d-110">[-doc](../../language-reference/compiler-options/doc-compiler-option.md)로 컴파일하여 문서 주석을 파일로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f515d-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="f515d-111">예제</span><span class="sxs-lookup"><span data-stu-id="f515d-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="f515d-112">참조</span><span class="sxs-lookup"><span data-stu-id="f515d-112">See also</span></span>

- [<span data-ttu-id="f515d-113">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="f515d-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f515d-114">문서 주석에 대한 권장 태그</span><span class="sxs-lookup"><span data-stu-id="f515d-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
