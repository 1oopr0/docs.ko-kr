---
title: '방법: 디렉터리의 파일 컬렉션 가져오기'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: 055151d4b3e3aba6be9b9b03ac9abffc6eb7b734
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401617"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="adbcb-102">방법: Visual Basic에서 디렉터리의 파일 컬렉션 가져오기</span><span class="sxs-lookup"><span data-stu-id="adbcb-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>

<span data-ttu-id="adbcb-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> 메서드의 오버로드는 디렉터리 내의 파일 이름을 나타내는 문자열의 읽기 전용 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="adbcb-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
- <span data-ttu-id="adbcb-104">하위 디렉터리를 검색하지 않고 지정된 디렉터리에서 단순 파일 검색을 수행하려면 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> 오버로드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="adbcb-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
- <span data-ttu-id="adbcb-105">검색을 위한 추가 옵션을 지정하려면 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> 오버로드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="adbcb-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="adbcb-106">`wildCards` 매개 변수를 사용하면 검색 패턴을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adbcb-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="adbcb-107">검색에 하위 디렉터리를 포함하려면 `searchType` 매개 변수를 <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="adbcb-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="adbcb-108">지정한 패턴과 일치하는 파일이 없으면 빈 컬렉션이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="adbcb-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="adbcb-109">디렉터리의 파일을 나열하려면</span><span class="sxs-lookup"><span data-stu-id="adbcb-109">To list files in a directory</span></span>  
  
- <span data-ttu-id="adbcb-110"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> 메서드 오버로드 중 하나를 사용하고 `directory` 매개 변수에서 검색할 디렉터리의 이름과 경로를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="adbcb-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="adbcb-111">다음 예제에서는 디렉터리의 모든 파일을 반환하여 `ListBox1`에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="adbcb-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a><span data-ttu-id="adbcb-112">강력한 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="adbcb-112">Robust Programming</span></span>  

 <span data-ttu-id="adbcb-113">다음 조건에서 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="adbcb-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="adbcb-114">길이가 0인 문자열이거나, 공백만 포함하거나, 잘못된 문자를 포함하거나, 경로가 디바이스 경로인 경우(\\\\.\\로 시작됨)와 같은 여러 가지 이유 중 하나로 경로가 올바르지 않은 경우(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="adbcb-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="adbcb-115">경로가 `Nothing`이기 때문에 올바르지 않은 경우(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="adbcb-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="adbcb-116">`directory`가 없는 경우(<xref:System.IO.DirectoryNotFoundException>)</span><span class="sxs-lookup"><span data-stu-id="adbcb-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="adbcb-117">`directory`가 기존 파일을 가리키는 경우(<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="adbcb-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="adbcb-118">경로가 시스템 정의 최대 길이를 초과하는 경우(<xref:System.IO.PathTooLongException>)</span><span class="sxs-lookup"><span data-stu-id="adbcb-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="adbcb-119">경로의 파일 이름이나 디렉터리 이름에 콜론(:)이 있거나 이름의 형식이 잘못된 경우(<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="adbcb-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="adbcb-120">경로를 보는 데 필요한 권한이 사용자에게 없는 경우(<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="adbcb-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="adbcb-121">사용자에게 필요한 권한이 없는 경우(<xref:System.UnauthorizedAccessException>)</span><span class="sxs-lookup"><span data-stu-id="adbcb-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adbcb-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="adbcb-122">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [<span data-ttu-id="adbcb-123">방법: 특정 패턴의 파일 찾기</span><span class="sxs-lookup"><span data-stu-id="adbcb-123">How to: Find Files with a Specific Pattern</span></span>](how-to-find-files-with-a-specific-pattern.md)
- [<span data-ttu-id="adbcb-124">방법: 특정 패턴의 하위 디렉터리 찾기</span><span class="sxs-lookup"><span data-stu-id="adbcb-124">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
