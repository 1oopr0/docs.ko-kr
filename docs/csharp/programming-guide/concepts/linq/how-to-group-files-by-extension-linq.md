---
title: 확장명에 따라 파일을 그룹화하는 방법(LINQ)(C#)
description: LINQ를 사용하여 C#에서 파일 또는 폴더의 목록에 대한 고급 그룹화 및 정렬 작업을 수행하는 방법에 대해 알아봅니다. 이 예제에서는 콘솔에서 출력을 페이징하는 방법을 보여줍니다.
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: c17328980c20dd6ec32e8d0ce176081122443344
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159048"
---
# <a name="how-to-group-files-by-extension-linq-c"></a><span data-ttu-id="7f45a-104">확장명에 따라 파일을 그룹화하는 방법(LINQ)(C#)</span><span class="sxs-lookup"><span data-stu-id="7f45a-104">How to group files by extension (LINQ) (C#)</span></span>

<span data-ttu-id="7f45a-105">이 예제에서는 LINQ를 사용하여 파일 또는 폴더 목록에 대해 고급 그룹화 및 정렬 작업을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f45a-105">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="7f45a-106">또한 <xref:System.Linq.Enumerable.Skip%2A> 및 <xref:System.Linq.Enumerable.Take%2A> 메서드를 사용하여 콘솔 창에서 출력을 페이징하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f45a-106">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f45a-107">예제</span><span class="sxs-lookup"><span data-stu-id="7f45a-107">Example</span></span>  

 <span data-ttu-id="7f45a-108">다음 쿼리는 지정된 디렉터리 트리의 내용을 파일 이름 확장명으로 그룹화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f45a-108">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```csharp  
class GroupByExtension  
{  
    // This query will sort all the files under the specified folder  
    //  and subfolder into groups keyed by the file extension.  
    private static void Main()  
    {  
        // Take a snapshot of the file system.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Used in WriteLine to trim output lines.  
        int trimLength = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Create the query.  
        var queryGroupByExt =  
            from file in fileList  
            group file by file.Extension.ToLower() into fileGroup  
            orderby fileGroup.Key  
            select fileGroup;  
  
        // Display one group at a time. If the number of
        // entries is greater than the number of lines  
        // in the console window, then page the output.  
        PageOutput(trimLength, queryGroupByExt);  
    }  
  
    // This method specifically handles group queries of FileInfo objects with string keys.  
    // It can be modified to work for any long listings of data. Note that explicit typing  
    // must be used in method signatures. The groupbyExtList parameter is a query that produces  
    // groups of FileInfo objects with string keys.  
    private static void PageOutput(int rootLength,  
                                    IEnumerable<System.Linq.IGrouping<string, System.IO.FileInfo>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine(filegroup.Key == String.Empty ? "[none]" : filegroup.Key);  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var f in resultPage)  
                {  
                    Console.WriteLine("\t{0}", f.FullName.Substring(rootLength));  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="7f45a-109">이 프로그램의 출력은 로컬 파일 시스템의 세부 정보 및 `startFolder`의 설정에 따라 길어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f45a-109">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="7f45a-110">모든 결과를 볼 수 있도록, 이 예제에서는 결과를 페이징하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f45a-110">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="7f45a-111">Windows 및 웹 애플리케이션에 동일한 기법을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f45a-111">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="7f45a-112">코드에서 그룹의 항목을 페이징하기 때문에 중첩된 `foreach` 루프가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7f45a-112">Notice that because the code pages the items in a group, a nested `foreach` loop is required.</span></span> <span data-ttu-id="7f45a-113">목록에서 현재 위치를 컴퓨팅하며 사용자가 페이징을 중지하고 프로그램을 종료할 수 있도록 하는 몇 가지 추가 논리도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f45a-113">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="7f45a-114">이 특정 사례에서는 페이징 쿼리가 원래 쿼리에서 캐시된 결과에 대해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f45a-114">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="7f45a-115">LINQ to SQL 등의 다른 컨텍스트에서는 이러한 캐싱이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f45a-115">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7f45a-116">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="7f45a-116">Compiling the Code</span></span>  

 <span data-ttu-id="7f45a-117">System.Linq 및 System.IO 네임스페이스에 대한 `using` 지시문을 통해 C# 콘솔 애플리케이션 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f45a-117">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f45a-118">참조</span><span class="sxs-lookup"><span data-stu-id="7f45a-118">See also</span></span>

- [<span data-ttu-id="7f45a-119">LINQ to Objects(C#)</span><span class="sxs-lookup"><span data-stu-id="7f45a-119">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="7f45a-120">LINQ 및 파일 디렉터리(C#)</span><span class="sxs-lookup"><span data-stu-id="7f45a-120">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
