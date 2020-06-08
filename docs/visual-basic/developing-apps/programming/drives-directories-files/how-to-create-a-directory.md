---
title: '방법: 디렉터리 만들기'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 0da915054a2e38c778f15bc0b472fe9b02521189
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401669"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="1e4c6-102">방법: Visual Basic에서 디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="1e4c6-102">How to: Create a Directory in Visual Basic</span></span>

<span data-ttu-id="1e4c6-103">`My.Computer.FileSystem` 개체의 `CreateDirectory` 메서드를 사용하여 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e4c6-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="1e4c6-104">디렉터리가 이미 있는 경우 예외가 throw되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e4c6-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="1e4c6-105">디렉터리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="1e4c6-105">To create a directory</span></span>  
  
- <span data-ttu-id="1e4c6-106">디렉터리를 만들어야 하는 위치의 전체 경로를 지정하여 `CreateDirectory` 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1e4c6-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="1e4c6-107">이 예제에서는 `C:\Documents and Settings\All Users\Documents`에 `NewDirectory` 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e4c6-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1e4c6-108">강력한 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="1e4c6-108">Robust Programming</span></span>  

 <span data-ttu-id="1e4c6-109">다음 조건에서 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="1e4c6-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="1e4c6-110">디렉터리 이름 형식이 잘못된 경우.</span><span class="sxs-lookup"><span data-stu-id="1e4c6-110">The directory name is malformed.</span></span> <span data-ttu-id="1e4c6-111">예를 들어 잘못된 문자를 포함하거나 공백만으로 이루어져 있습니다(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="1e4c6-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="1e4c6-112">만들 디렉터리의 부모 디렉터리가 읽기 전용인 경우(<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="1e4c6-112">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="1e4c6-113">디렉터리 이름이 `Nothing`인 경우(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="1e4c6-113">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="1e4c6-114">디렉터리 이름이 너무 긴 경우(<xref:System.IO.PathTooLongException>)</span><span class="sxs-lookup"><span data-stu-id="1e4c6-114">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="1e4c6-115">디렉터리 이름이 콜론 “:”인 경우(<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="1e4c6-115">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="1e4c6-116">사용자에게 디렉터리를 만들 수 있는 권한이 없는 경우(<xref:System.UnauthorizedAccessException>)</span><span class="sxs-lookup"><span data-stu-id="1e4c6-116">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="1e4c6-117">부분 신뢰 상황에서 사용자에게 권한이 없는 경우(<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="1e4c6-117">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e4c6-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e4c6-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [<span data-ttu-id="1e4c6-119">파일/디렉터리 만들기, 삭제 및 이동</span><span class="sxs-lookup"><span data-stu-id="1e4c6-119">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)
