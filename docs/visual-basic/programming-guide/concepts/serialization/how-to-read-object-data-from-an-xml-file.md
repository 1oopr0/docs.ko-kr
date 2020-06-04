---
title: '방법: XML 파일에서 개체 데이터 읽기'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: 7097ec146987aea7855da40dd30f9cd3c17d8ce4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413169"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="5c23a-102">방법: XML 파일에서 개체 데이터 읽기(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c23a-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="5c23a-103">이 예제에서는 <xref:System.Xml.Serialization.XmlSerializer> 클래스를 사용하여 이전에 XML 파일에 기록된 개체 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="5c23a-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c23a-104">예제</span><span class="sxs-lookup"><span data-stu-id="5c23a-104">Example</span></span>  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="5c23a-105">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="5c23a-105">Compile the code</span></span>  
 <span data-ttu-id="5c23a-106">파일 이름 "c:\temp\SerializationOverview.xml"을 serialize된 데이터가 포함된 파일 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="5c23a-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="5c23a-107">데이터를 serialize 하는 방법에 대 한 자세한 내용은 [방법: XML 파일에 개체 데이터 쓰기 (Visual Basic)](how-to-write-object-data-to-an-xml-file.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c23a-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="5c23a-108">클래스에는 매개 변수가 없는 public 생성자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c23a-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="5c23a-109">public 속성과 필드만 역직렬화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c23a-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5c23a-110">강력한 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="5c23a-110">Robust Programming</span></span>  
 <span data-ttu-id="5c23a-111">다음 조건에서 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5c23a-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5c23a-112">serialize되는 클래스에 매개 변수가 없는 public 생성자가 없는 경우</span><span class="sxs-lookup"><span data-stu-id="5c23a-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="5c23a-113">파일의 데이터가 역직렬화할 클래스의 데이터를 나타내지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="5c23a-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="5c23a-114">파일이 없는 경우(<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="5c23a-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5c23a-115">.NET Framework 보안</span><span class="sxs-lookup"><span data-stu-id="5c23a-115">.NET Framework Security</span></span>  
 <span data-ttu-id="5c23a-116">항상 입력을 확인하고, 신뢰할 수 없는 소스의 데이터를 역직렬화하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="5c23a-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="5c23a-117">다시 생성된 개체는 역직렬화한 코드의 사용 권한으로 로컬 컴퓨터에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c23a-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="5c23a-118">애플리케이션에서 데이터를 사용하기 전에 모든 입력을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c23a-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c23a-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5c23a-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="5c23a-120">방법: XML 파일에 개체 데이터 쓰기(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c23a-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="5c23a-121">Serialization(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c23a-121">Serialization (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="5c23a-122">Visual Basic 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="5c23a-122">Visual Basic Programming Guide</span></span>](../../index.md)
