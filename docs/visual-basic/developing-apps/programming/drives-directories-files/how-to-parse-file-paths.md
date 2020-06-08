---
title: '방법: 파일 경로의 구문 분석'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: eb7714a8594c0bce344eb2e48ebc5053dc3bfbb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359944"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="0cc88-102">방법: Visual Basic에서 파일 경로의 구문 분석</span><span class="sxs-lookup"><span data-stu-id="0cc88-102">How to: Parse File Paths in Visual Basic</span></span>

<span data-ttu-id="0cc88-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem> 개체는 파일 경로를 구문 분석할 때 유용한 메서드 여러 개를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0cc88-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
- <span data-ttu-id="0cc88-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> 메서드는 두 개의 경로를 가져와서 적절한 형식으로 조합된 경로를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0cc88-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
- <span data-ttu-id="0cc88-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> 메서드는 제공된 경로의 상위에 대한 절대 경로를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0cc88-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
- <span data-ttu-id="0cc88-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> 메서드는 <xref:System.IO.FileInfo> 개체를 반환합니다. 이 개체를 쿼리하여 파일의 이름 및 경로 등과 같은 속성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cc88-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="0cc88-107">파일 이름 확장명에 근거하여 파일 내용을 판단하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0cc88-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="0cc88-108">예를 들어 Form1.vb 파일이 Visual Basic 소스 파일이 아닐 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cc88-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="0cc88-109">파일의 이름 및 경로를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="0cc88-109">To determine a file's name and path</span></span>  
  
- <span data-ttu-id="0cc88-110"><xref:System.IO.FileInfo.DirectoryName%2A> 개체의 <xref:System.IO.FileInfo.Name%2A> 및 <xref:System.IO.FileInfo> 속성을 사용하여 파일의 이름과 경로를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0cc88-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="0cc88-111">이 예제에서는 이름과 경로를 확인하고 이를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0cc88-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="0cc88-112">파일의 이름과 디렉터리를 결합하여 전체 경로를 만들려면</span><span class="sxs-lookup"><span data-stu-id="0cc88-112">To combine a file's name and directory to create the full path</span></span>  
  
- <span data-ttu-id="0cc88-113">디렉터리와 이름을 제공하여 `CombinePath` 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0cc88-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="0cc88-114">이 예제에서는 이전 예제에서 만들어진 문자열 `folderPath` 와 `fileName` 을 가져와서 이를 결합한 다음 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0cc88-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="0cc88-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0cc88-115">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="0cc88-116">방법: 디렉터리의 파일 컬렉션 가져오기</span><span class="sxs-lookup"><span data-stu-id="0cc88-116">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
