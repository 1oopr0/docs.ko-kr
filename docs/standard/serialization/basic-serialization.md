---
title: 기본 serialization
description: 이 문서에서는 SerializableAttribute를 사용하여 클래스를 직렬화할 수 있도록 만드는 방법을 보여 주고 serialization 및 deserialization의 예제를 제공합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: 2b75ba6875b2a4430b6776c27dead72476884fff
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282072"
---
# <a name="basic-serialization"></a><span data-ttu-id="ad426-103">기본 serialization</span><span class="sxs-lookup"><span data-stu-id="ad426-103">Basic serialization</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="ad426-104">클래스를 직렬화 가능하도록 만드는 가장 쉬운 방법은 다음과 같이 <xref:System.SerializableAttribute> 특성으로 표시하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-104">The easiest way to make a class serializable is to mark it with the <xref:System.SerializableAttribute> as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
<span data-ttu-id="ad426-105">다음 코드 예제에서는 이 클래스의 인스턴스를 파일로 직렬화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-105">The following code example shows how an instance of this class can be serialized to a file.</span></span>  
  
```csharp  
MyObject obj = new MyObject();  
obj.n1 = 1;  
obj.n2 = 24;  
obj.str = "Some String";  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Create, FileAccess.Write, FileShare.None);  
formatter.Serialize(stream, obj);  
stream.Close();  
```  
  
<span data-ttu-id="ad426-106">이 예제에서는 이진 포맷터를 사용하여 serialization을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-106">This example uses a binary formatter to do the serialization.</span></span> <span data-ttu-id="ad426-107">사용할 포맷터와 스트림의 인스턴스를 만든 다음 포맷터에 대해 **직렬화** 메서드를 호출하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-107">All you need to do is create an instance of the stream and the formatter you intend to use, and then call the **Serialize** method on the formatter.</span></span> <span data-ttu-id="ad426-108">serialize할 스트림과 개체가 이 호출에 매개 변수로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-108">The stream and the object to serialize are provided as parameters to this call.</span></span> <span data-ttu-id="ad426-109">이 예제에서는 명확하게 보여주고 있지 않지만 전용으로 표시된 변수까지 포함한 클래스의 모든 멤버 변수가 serialize됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-109">Although it is not explicitly demonstrated in this example, all member variables of a class will be serialized—even variables marked as private.</span></span> <span data-ttu-id="ad426-110">이런 면에서 이진 serialization은 public 필드만 직렬화하는 <xref:System.Xml.Serialization.XmlSerializer> 클래스와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-110">In this aspect, binary serialization differs from the <xref:System.Xml.Serialization.XmlSerializer> class, which only serializes public fields.</span></span> <span data-ttu-id="ad426-111">이진 serialization에서 멤버 변수를 제외하는 방법에 대한 자세한 내용은 [선택적 Serialization](selective-serialization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad426-111">For information on excluding member variables from binary serialization, see [Selective Serialization](selective-serialization.md).</span></span>  
  
<span data-ttu-id="ad426-112">개체를 이전 상태로 복원하는 것도 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-112">Restoring the object back to its former state is just as easy.</span></span> <span data-ttu-id="ad426-113">먼저 읽기용 스트림과 <xref:System.Runtime.Serialization.Formatter>를 만든 다음 포맷터에 개체를 역직렬화하도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-113">First, create a stream for reading and a <xref:System.Runtime.Serialization.Formatter>, and then instruct the formatter to deserialize the object.</span></span> <span data-ttu-id="ad426-114">아래 코드 예제에서 이렇게 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-114">The code example below shows how this is done.</span></span>  
  
```csharp  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Open, FileAccess.Read, FileShare.Read);  
MyObject obj = (MyObject) formatter.Deserialize(stream);  
stream.Close();  
  
// Here's the proof.  
Console.WriteLine("n1: {0}", obj.n1);  
Console.WriteLine("n2: {0}", obj.n2);  
Console.WriteLine("str: {0}", obj.str);  
```  
  
<span data-ttu-id="ad426-115">위에서 사용된 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>는 매우 효율적이며 작은 크기의 바이트 스트림을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-115">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> used above is very efficient and produces a compact byte stream.</span></span> <span data-ttu-id="ad426-116">이 포맷터로 직렬화된 모든 개체는 해당 포맷터로 역직렬화할 수 있기 때문에 .NET에서 역직렬화될 개체의 직렬화에 이상적인 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-116">All objects serialized with this formatter can also be deserialized with it, which makes it an ideal tool for serializing objects that will be deserialized on .NET.</span></span> <span data-ttu-id="ad426-117">개체가 역직렬화될 때 생성자가 호출되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-117">It is important to note that constructors are not called when an object is deserialized.</span></span> <span data-ttu-id="ad426-118">이러한 제약 조건은 성능상의 이유로 deserialization에 적용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-118">This constraint is placed on deserialization for performance reasons.</span></span> <span data-ttu-id="ad426-119">하지만 이는 런타임과 개체 작성자 간의 일부 계약에 위배되며, 개발자는 개체를 serialize 가능으로 표시할 때 결과를 잘 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-119">However, this violates some of the usual contracts the runtime makes with the object writer, and developers should ensure that they understand the ramifications when marking an object as serializable.</span></span>  
  
<span data-ttu-id="ad426-120">이식성이 필요한 경우에는 대신 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="ad426-120">If portability is a requirement, use the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> instead.</span></span> <span data-ttu-id="ad426-121">위의 코드에서 **BinaryFormatter** 를 **SoapFormatter** 로 바꾸고 이전처럼 **직렬화** 및 **역직렬화** 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-121">Simply replace the **BinaryFormatter** in the code above with **SoapFormatter,** and call **Serialize** and **Deserialize** as before.</span></span> <span data-ttu-id="ad426-122">이 포맷터는 위에서 사용된 예제에 대해 다음 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-122">This formatter produces the following output for the example used above.</span></span>  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:a1="http://schemas.microsoft.com/clr/assem/ToFile">  
  
  <SOAP-ENV:Body>  
    <a1:MyObject id="ref-1">  
      <n1>1</n1>  
      <n2>24</n2>  
      <str id="ref-3">Some String</str>  
    </a1:MyObject>  
  </SOAP-ENV:Body>  
</SOAP-ENV:Envelope>  
```  
  
<span data-ttu-id="ad426-123">[Serializable](xref:System.SerializableAttribute) 특성은 상속할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-123">It's important to note that the [Serializable](xref:System.SerializableAttribute) attribute cannot be inherited.</span></span> <span data-ttu-id="ad426-124">`MyObject`에서 새 클래스를 파생할 때는 새 클래스도 특성으로 표시해야 하며 그렇지 않으면 serialize할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-124">If you derive a new class from `MyObject`, the new class must be marked with the attribute as well, or it cannot be serialized.</span></span> <span data-ttu-id="ad426-125">예를 들어 아래 클래스의 인스턴스를 직렬화하려고 할 때 `MyStuff` 형식이 직렬화 가능으로 표시되지 않았음을 알리는 <xref:System.Runtime.Serialization.SerializationException>이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-125">For example, when you attempt to serialize an instance of the class below, you'll get a <xref:System.Runtime.Serialization.SerializationException> informing you that the `MyStuff` type is not marked as serializable.</span></span>  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 <span data-ttu-id="ad426-126">[Serializable](xref:System.SerializableAttribute) 특성을 사용하면 편리하지만 앞에서 설명한 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-126">Using the [Serializable](xref:System.SerializableAttribute) attribute is convenient, but it has limitations as previously demonstrated.</span></span> <span data-ttu-id="ad426-127">클래스를 직렬화되도록 표시하는 시점에 대한 자세한 내용은 [Serialization 지침](serialization-guidelines.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad426-127">Refer to the [Serialization Guidelines](serialization-guidelines.md) for information about when you should mark a class for serialization.</span></span> <span data-ttu-id="ad426-128">컴파일된 뒤에는 serialization을 클래스에 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad426-128">Serialization cannot be added to a class after it has been compiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad426-129">참조</span><span class="sxs-lookup"><span data-stu-id="ad426-129">See also</span></span>

- [<span data-ttu-id="ad426-130">이진 serialization</span><span class="sxs-lookup"><span data-stu-id="ad426-130">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="ad426-131">XML 및 SOAP serialization</span><span class="sxs-lookup"><span data-stu-id="ad426-131">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
