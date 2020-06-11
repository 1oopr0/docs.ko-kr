---
title: <c> - C# 프로그래밍 가이드
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: a09bcd069e2f85f4a21736cb218c42c0e481d70b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287469"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="f6a74-102">\<c>(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="f6a74-102">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="f6a74-103">구문</span><span class="sxs-lookup"><span data-stu-id="f6a74-103">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="f6a74-104">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6a74-104">Parameters</span></span>

- `text`

  <span data-ttu-id="f6a74-105">코드로 표시하려는 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="f6a74-105">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f6a74-106">설명</span><span class="sxs-lookup"><span data-stu-id="f6a74-106">Remarks</span></span>

<span data-ttu-id="f6a74-107">`<c>` 태그를 사용하면 설명 내의 텍스트를 코드로 표시해야 함을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6a74-107">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="f6a74-108">여러 줄을 코드로 지정하려면 [\<code>](./code.md)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a74-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="f6a74-109">[-doc](../../language-reference/compiler-options/doc-compiler-option.md)로 컴파일하여 문서 주석을 파일로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a74-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="f6a74-110">예제</span><span class="sxs-lookup"><span data-stu-id="f6a74-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="f6a74-111">참조</span><span class="sxs-lookup"><span data-stu-id="f6a74-111">See also</span></span>

- [<span data-ttu-id="f6a74-112">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="f6a74-112">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="f6a74-113">문서 주석에 대한 권장 태그</span><span class="sxs-lookup"><span data-stu-id="f6a74-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
