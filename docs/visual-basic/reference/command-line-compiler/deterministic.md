---
title: -deterministic
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
ms.openlocfilehash: 0cf9aceef54998f269e9e377fe5d0a48492969c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408688"
---
# <a name="-deterministic"></a><span data-ttu-id="f3c96-102">-deterministic</span><span class="sxs-lookup"><span data-stu-id="f3c96-102">-deterministic</span></span>

<span data-ttu-id="f3c96-103">컴파일러에서 동일한 입력에 대한 컴파일 간에 바이트 단위(byte-for-byte) 출력이 동일한 어셈블리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f3c96-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="f3c96-104">구문</span><span class="sxs-lookup"><span data-stu-id="f3c96-104">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="f3c96-105">설명</span><span class="sxs-lookup"><span data-stu-id="f3c96-105">Remarks</span></span>

<span data-ttu-id="f3c96-106">기본적으로 컴파일러에서 타임스탬프 및 난수에서 생성된 GUID를 추가하기 때문에 지정된 입력 집합의 컴파일러 출력은 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="f3c96-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="f3c96-107">`-deterministic` 옵션을 사용하여 *결정적 어셈블리*를 생성하고, 입력이 동일하게 유지되는 한 해당 이진 콘텐츠가 컴파일 간에 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="f3c96-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="f3c96-108">결정성의 목적을 위해 컴파일러에서 고려하는 입력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f3c96-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="f3c96-109">명령줄 매개 변수의 순서</span><span class="sxs-lookup"><span data-stu-id="f3c96-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="f3c96-110">컴파일러의 .rsp 지시 파일의 내용</span><span class="sxs-lookup"><span data-stu-id="f3c96-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="f3c96-111">사용된 컴파일러의 정확한 버전 및 참조되는 어셈블리</span><span class="sxs-lookup"><span data-stu-id="f3c96-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="f3c96-112">현재 디렉터리 경로</span><span class="sxs-lookup"><span data-stu-id="f3c96-112">The current directory path.</span></span>
- <span data-ttu-id="f3c96-113">다음을 포함하여 직접 또는 간접적으로 컴파일러에 명시적으로 전달된 모든 파일의 이진 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="f3c96-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="f3c96-114">소스 파일</span><span class="sxs-lookup"><span data-stu-id="f3c96-114">Source files</span></span>
  - <span data-ttu-id="f3c96-115">참조된 어셈블리</span><span class="sxs-lookup"><span data-stu-id="f3c96-115">Referenced assemblies</span></span>
  - <span data-ttu-id="f3c96-116">참조된 모듈</span><span class="sxs-lookup"><span data-stu-id="f3c96-116">Referenced modules</span></span>
  - <span data-ttu-id="f3c96-117">리소스</span><span class="sxs-lookup"><span data-stu-id="f3c96-117">Resources</span></span>
  - <span data-ttu-id="f3c96-118">강력한 이름 키 파일</span><span class="sxs-lookup"><span data-stu-id="f3c96-118">The strong name key file</span></span>
  - <span data-ttu-id="f3c96-119">@ 지시 파일</span><span class="sxs-lookup"><span data-stu-id="f3c96-119">@ response files</span></span>
  - <span data-ttu-id="f3c96-120">분석기</span><span class="sxs-lookup"><span data-stu-id="f3c96-120">Analyzers</span></span>
  - <span data-ttu-id="f3c96-121">규칙 집합</span><span class="sxs-lookup"><span data-stu-id="f3c96-121">Rulesets</span></span>
  - <span data-ttu-id="f3c96-122">분석기에서 사용할 수 있는 추가 파일</span><span class="sxs-lookup"><span data-stu-id="f3c96-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="f3c96-123">현재 문화권(진단 및 예외 메시지가 생성되는 언어)</span><span class="sxs-lookup"><span data-stu-id="f3c96-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="f3c96-124">인코딩이 지정되지 않은 경우 기본 인코딩(또는 현재 코드 페이지)</span><span class="sxs-lookup"><span data-stu-id="f3c96-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="f3c96-125">컴파일러의 검색 경로(예: `-lib` 또는 `-recurse`로 지정)에 있는 파일의 존재 여부 및 내용</span><span class="sxs-lookup"><span data-stu-id="f3c96-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="f3c96-126">컴파일러가 실행되는 CLR 플랫폼</span><span class="sxs-lookup"><span data-stu-id="f3c96-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="f3c96-127">`%LIBPATH%` 값(분석기 종속성 로드에 영향을 줄 수 있음)</span><span class="sxs-lookup"><span data-stu-id="f3c96-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="f3c96-128">원본을 공개적으로 사용할 수 있는 경우 결정적 컴파일을 사용하여 이진 파일이 신뢰할 수 있는 원본에서 컴파일되는지 여부를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3c96-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="f3c96-129">또한 연속 빌드 시스템에서 이진 파일 변경에 종속된 빌드 단계를 실행해야 하는지 여부를 확인하는 데 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3c96-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3c96-130">참조</span><span class="sxs-lookup"><span data-stu-id="f3c96-130">See also</span></span>

- [<span data-ttu-id="f3c96-131">Visual Basic 명령줄 컴파일러</span><span class="sxs-lookup"><span data-stu-id="f3c96-131">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f3c96-132">샘플 컴파일 명령줄</span><span class="sxs-lookup"><span data-stu-id="f3c96-132">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
