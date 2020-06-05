---
title: ReDim 문
ms.date: 07/20/2015
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
ms.openlocfilehash: 82f19762865fdf3c3f32a0349e21e3b97bebd567
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404280"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="d22d5-102">ReDim 문 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d22d5-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="d22d5-103">배열 변수의 스토리지 공간을 다시 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d22d5-104">구문</span><span class="sxs-lookup"><span data-stu-id="d22d5-104">Syntax</span></span>  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d22d5-105">부분</span><span class="sxs-lookup"><span data-stu-id="d22d5-105">Parts</span></span>  
  
|<span data-ttu-id="d22d5-106">용어</span><span class="sxs-lookup"><span data-stu-id="d22d5-106">Term</span></span>|<span data-ttu-id="d22d5-107">정의</span><span class="sxs-lookup"><span data-stu-id="d22d5-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="d22d5-108">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-108">Optional.</span></span> <span data-ttu-id="d22d5-109">마지막 차원의 크기만 변경한 경우 기존 배열의 데이터를 유지하기 위해 사용되는 한정자입니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="d22d5-110">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="d22d5-110">Required.</span></span> <span data-ttu-id="d22d5-111">배열 변수의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-111">Name of the array variable.</span></span> <span data-ttu-id="d22d5-112">[Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d22d5-112">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="d22d5-113">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="d22d5-113">Required.</span></span> <span data-ttu-id="d22d5-114">다시 정의된 배열의 각 차원에 대한 범위 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d22d5-115">설명</span><span class="sxs-lookup"><span data-stu-id="d22d5-115">Remarks</span></span>  
 <span data-ttu-id="d22d5-116">`ReDim` 문을 사용하여 이미 선언된 배열의 차원 중 하나 이상의 크기를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="d22d5-117">큰 배열이 있고 요소가 더 이상 필요하지 않은 경우 `ReDim`은 배열 크기를 줄여서 메모리를 확보할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="d22d5-118">반면에 배열에 요소가 더 필요한 경우 `ReDim`은 요소를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="d22d5-119">`ReDim` 문은 배열에만 사용할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="d22d5-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="d22d5-120">스칼라(단일 값만 포함된 변수), 컬렉션 또는 구조체에서는 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="d22d5-121">변수를 `Array` 형식으로 선언하는 경우 `ReDim` 문에는 새 배열을 만들 수 있는 충분한 형식 정보가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="d22d5-122">`ReDim` 은 프로시저 수준에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="d22d5-123">따라서 변수의 선언 컨텍스트는 프로시저여야 하며, 소스 파일, 네임스페이스, 인터페이스, 클래스, 구조체, 모듈 또는 블록일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="d22d5-124">자세한 내용은 [선언 컨텍스트 및 기본 액세스 수준](declaration-contexts-and-default-access-levels.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d22d5-124">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d22d5-125">규칙</span><span class="sxs-lookup"><span data-stu-id="d22d5-125">Rules</span></span>  
  
- <span data-ttu-id="d22d5-126">**여러 변수.**</span><span class="sxs-lookup"><span data-stu-id="d22d5-126">**Multiple Variables.**</span></span> <span data-ttu-id="d22d5-127">동일한 선언문에서 여러 배열 변수의 크기를 조정 하 고 `name` 각 변수에 대해 및 부분을 지정할 수 있습니다 `boundlist` .</span><span class="sxs-lookup"><span data-stu-id="d22d5-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="d22d5-128">여러 변수는 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-128">Multiple variables are separated by commas.</span></span>  
  
- <span data-ttu-id="d22d5-129">**배열 범위입니다.**</span><span class="sxs-lookup"><span data-stu-id="d22d5-129">**Array Bounds.**</span></span> <span data-ttu-id="d22d5-130">의 각 항목 `boundlist` 은 해당 차원의 하 한과 상한을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="d22d5-131">하한은 항상 0(영)입니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="d22d5-132">상한은 해당 차원에 가능한 최대 인덱스 값이며 차원의 길이(상한에 1을 더한 값)는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="d22d5-133">각 차원의 인덱스는 0부터 상한 값까지 다양할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="d22d5-134">`boundlist`의 차원 수는 배열의 원래 차원 수(차수)와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
- <span data-ttu-id="d22d5-135">**데이터 형식.**</span><span class="sxs-lookup"><span data-stu-id="d22d5-135">**Data Types.**</span></span> <span data-ttu-id="d22d5-136">`ReDim`문은 배열 변수 또는 해당 요소의 데이터 형식을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
- <span data-ttu-id="d22d5-137">**초기.**</span><span class="sxs-lookup"><span data-stu-id="d22d5-137">**Initialization.**</span></span> <span data-ttu-id="d22d5-138">`ReDim`문은 배열 요소에 대해 새 초기화 값을 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
- <span data-ttu-id="d22d5-139">**배열.**</span><span class="sxs-lookup"><span data-stu-id="d22d5-139">**Rank.**</span></span> <span data-ttu-id="d22d5-140">`ReDim`문은 배열의 차수 (차원 수)를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
- <span data-ttu-id="d22d5-141">**Preserve를 사용한 크기 조정.**</span><span class="sxs-lookup"><span data-stu-id="d22d5-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="d22d5-142">를 사용 하는 경우 `Preserve` 배열의 마지막 차원만 크기를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="d22d5-143">다른 모든 차원의 경우에는 기존 배열의 범위를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="d22d5-144">예를 들어 배열에 차원이 하나만 있는 경우 해당 차원의 크기를 조정해도 배열의 모든 내용을 보존할 수 있습니다. 마지막이자 유일한 차원을 변경하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="d22d5-145">그러나 배열에 둘 이상의 차원이 있는 경우에는 `Preserve`를 사용하여 마지막 차원의 크기만 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
- <span data-ttu-id="d22d5-146">**정보의.**</span><span class="sxs-lookup"><span data-stu-id="d22d5-146">**Properties.**</span></span> <span data-ttu-id="d22d5-147">`ReDim`값의 배열을 포함 하는 속성에를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="d22d5-148">동작</span><span class="sxs-lookup"><span data-stu-id="d22d5-148">Behavior</span></span>  
  
- <span data-ttu-id="d22d5-149">**배열 바꾸기.**</span><span class="sxs-lookup"><span data-stu-id="d22d5-149">**Array Replacement.**</span></span> <span data-ttu-id="d22d5-150">`ReDim`기존 배열을 해제 하 고 동일한 순위로 새 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="d22d5-151">새 배열은 배열 변수에서 해제된 배열을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-151">The new array replaces the released array in the array variable.</span></span>  
  
- <span data-ttu-id="d22d5-152">**Preserve를 사용하지 않는 초기화.**</span><span class="sxs-lookup"><span data-stu-id="d22d5-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="d22d5-153">을 지정 하지 않으면 `Preserve` `ReDim` 는 해당 데이터 형식에 대 한 기본값을 사용 하 여 새 배열의 요소를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
- <span data-ttu-id="d22d5-154">**Preserve를 사용하는 초기화.**</span><span class="sxs-lookup"><span data-stu-id="d22d5-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="d22d5-155">을 지정 하는 경우 `Preserve` Visual Basic 기존 배열의 요소를 새 배열에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d22d5-156">예제</span><span class="sxs-lookup"><span data-stu-id="d22d5-156">Example</span></span>  
 <span data-ttu-id="d22d5-157">다음 예제에서는 배열의 기존 데이터를 손실하지 않고 동적 배열의 마지막 차원 크기를 늘린 다음 데이터를 부분적으로 손실하며 크기를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="d22d5-158">마지막으로 크기를 원래 값으로 다시 줄이고 모든 배열 요소를 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 <span data-ttu-id="d22d5-159">`Dim` 문은 차원이 세 개인 새 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="d22d5-160">각 차원은 범위 10으로 선언되므로 각 차원의 배열 인덱스는 0에서 10까지의 범위일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="d22d5-161">다음 설명에서는 세 개의 차원이 계층, 행 및 열로 지칭됩니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="d22d5-162">첫 번째 `ReDim`은 `intArray` 변수의 기존 배열을 대체하는 새 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="d22d5-163">`ReDim`은 기존 배열의 모든 요소를 새 배열에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="d22d5-164">또한 모든 계층에 있는 각 행의 끝에 열 10개를 더 추가하고 이러한 새 열의 요소를 0(배열의 요소 형식인 `Integer`의 기본값)으로 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="d22d5-165">두 번째 `ReDim`은 새 배열을 하나 더 만들고 적합한 모든 요소를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="d22d5-166">그러나 5개의 열이 각 계층에 있는 각 행의 끝에서 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="d22d5-167">이는 해당 열의 사용을 마친 경우 문제가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="d22d5-168">큰 배열의 크기를 줄이면 더 이상 필요하지 않은 메모리를 확보할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="d22d5-169">세 번째 `ReDim`은 새 배열을 하나 더 만들고 각 계층에 있는 각 행의 끝에서 5개의 열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="d22d5-170">이번에는 기존 요소를 복사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="d22d5-171">이 문은 배열을 원래 크기로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="d22d5-172">이 문은 `Preserve` 한정자를 포함하지 않기 때문에 모든 배열 요소를 원래 기본값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d22d5-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="d22d5-173">추가 예제는 [배열](../../programming-guide/language-features/arrays/index.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d22d5-173">For additional examples, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d22d5-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d22d5-174">See also</span></span>

- <xref:System.IndexOutOfRangeException>
- [<span data-ttu-id="d22d5-175">Const 문</span><span class="sxs-lookup"><span data-stu-id="d22d5-175">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="d22d5-176">Dim 문</span><span class="sxs-lookup"><span data-stu-id="d22d5-176">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="d22d5-177">Erase 문</span><span class="sxs-lookup"><span data-stu-id="d22d5-177">Erase Statement</span></span>](erase-statement.md)
- [<span data-ttu-id="d22d5-178">Nothing</span><span class="sxs-lookup"><span data-stu-id="d22d5-178">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="d22d5-179">배열</span><span class="sxs-lookup"><span data-stu-id="d22d5-179">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
