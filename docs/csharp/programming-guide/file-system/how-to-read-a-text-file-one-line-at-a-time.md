---
title: 텍스트 파일을 한 번에 한 줄씩 읽는 방법 - C# 프로그래밍 가이드
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: b54d072ce9837f9b15694f2d7100817de62e9762
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241775"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="b2bc1-102">텍스트 파일을 한 번에 한 줄씩 읽는 방법(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="b2bc1-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="b2bc1-103">이 예제에서는 `StreamReader` 클래스의 `ReadLine` 메서드를 사용하여 텍스트 파일 내용을 한 번에 한 줄씩 문자열로 읽어옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc1-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="b2bc1-104">각 텍스트 줄은 `line` 문자열에 저장되고 화면에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc1-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2bc1-105">예제</span><span class="sxs-lookup"><span data-stu-id="b2bc1-105">Example</span></span>  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2bc1-106">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="b2bc1-106">Compiling the Code</span></span>  
 <span data-ttu-id="b2bc1-107">코드를 복사하고 콘솔 애플리케이션의 `Main` 메서드에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc1-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="b2bc1-108">`"c:\test.txt"`를 실제 파일 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc1-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b2bc1-109">강력한 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="b2bc1-109">Robust Programming</span></span>  
 <span data-ttu-id="b2bc1-110">다음 조건에서 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc1-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b2bc1-111">파일이 없을 수 있는 경우</span><span class="sxs-lookup"><span data-stu-id="b2bc1-111">The file may not exist.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="b2bc1-112">.NET 보안</span><span class="sxs-lookup"><span data-stu-id="b2bc1-112">.NET Security</span></span>  
 <span data-ttu-id="b2bc1-113">파일 이름을 바탕으로 파일 내용을 판단하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc1-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="b2bc1-114">예를 들어 `myFile.cs` 파일이 C# 소스 파일이 아닐 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2bc1-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2bc1-115">참조</span><span class="sxs-lookup"><span data-stu-id="b2bc1-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="b2bc1-116">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="b2bc1-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b2bc1-117">파일 시스템 및 레지스트리(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="b2bc1-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
