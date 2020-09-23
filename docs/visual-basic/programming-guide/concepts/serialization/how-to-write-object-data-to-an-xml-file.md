---
title: '방법: XML 파일에 개체 데이터 쓰기'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: af62d10b29e76701668fd3d595b967bd1754a22c
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077230"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="87cb5-102">방법: XML 파일에 개체 데이터 쓰기(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87cb5-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>

<span data-ttu-id="87cb5-103">이 예제에서는 <xref:System.Xml.Serialization.XmlSerializer> 클래스를 사용하여 XML 파일에 클래스의 개체를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="87cb5-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87cb5-104">예제</span><span class="sxs-lookup"><span data-stu-id="87cb5-104">Example</span></span>  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="87cb5-105">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="87cb5-105">Compile the code</span></span>  

 <span data-ttu-id="87cb5-106">클래스에는 매개 변수가 없는 public 생성자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cb5-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="87cb5-107">강력한 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="87cb5-107">Robust Programming</span></span>  

 <span data-ttu-id="87cb5-108">다음 조건에서 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="87cb5-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="87cb5-109">serialize되는 클래스에 매개 변수가 없는 public 생성자가 없는 경우</span><span class="sxs-lookup"><span data-stu-id="87cb5-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="87cb5-110">파일이 있지만 읽기 전용인 경우(<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="87cb5-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="87cb5-111">경로가 너무 긴 경우(<xref:System.IO.PathTooLongException>)</span><span class="sxs-lookup"><span data-stu-id="87cb5-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="87cb5-112">디스크가 꽉 찬 경우(<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="87cb5-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="87cb5-113">.NET Framework 보안</span><span class="sxs-lookup"><span data-stu-id="87cb5-113">.NET Framework Security</span></span>  

 <span data-ttu-id="87cb5-114">이 예제에서는 파일이 아직 없는 경우 새 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="87cb5-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="87cb5-115">애플리케이션에서 파일을 만들어야 하는 경우 해당 애플리케이션에 폴더에 대한 `Create` 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87cb5-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="87cb5-116">파일이 이미 있는 경우 애플리케이션에 더 낮은 권한인 `Write` 권한만 있으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87cb5-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="87cb5-117">가능한 경우 배포하는 동안 파일을 만들고, 폴더에 대한 `Create` 권한 대신 단일 파일에 대해 `Read` 권한만 부여하는 것이 더 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="87cb5-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87cb5-118">참조</span><span class="sxs-lookup"><span data-stu-id="87cb5-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="87cb5-119">방법: XML 파일에서 개체 데이터 읽기(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87cb5-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="87cb5-120">Serialization(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87cb5-120">Serialization (Visual Basic)</span></span>](index.md)
