---
title: '방법: DataContractJsonSerializer 사용'
description: .NET 형식 개체를 JSON으로 인코딩된 데이터로 serialize 한 다음 이러한 데이터를 다시 .NET 형식의 인스턴스로 deserialize 하는 방법을 알아봅니다.
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 4ffa0e9dec0a677a38d244b4a0da476d91852da5
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246807"
---
# <a name="how-to-use-datacontractjsonserializer"></a><span data-ttu-id="82e92-103">DataContractJsonSerializer 사용 방법</span><span class="sxs-lookup"><span data-stu-id="82e92-103">How to use DataContractJsonSerializer</span></span>

> [!NOTE]
> <span data-ttu-id="82e92-104">이 문서는에 대 한 내용입니다 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="82e92-104">This article is about <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="82e92-105">JSON 직렬화 및 역직렬화를 포함 하는 대부분의 시나리오에서는 [네임 스페이스의System.Text.Js](../../../standard/serialization/system-text-json-overview.md)에 api를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-105">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="82e92-106">JSON(JavaScript Object Notation)은 클라이언트 브라우저 및 AJAX 사용 웹 서비스 간에 소량의 데이터를 신속하게 교환할 수 있는 효율적인 데이터 인코딩 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-106">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>

<span data-ttu-id="82e92-107">이 문서에서는 .NET 형식 개체를 JSON으로 인코딩된 데이터로 serialize 한 다음 JSON 형식의 데이터를 다시 .NET 형식의 인스턴스로 deserialize 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-107">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="82e92-108">이 예제에서는 데이터 계약을 사용 하 여 사용자 정의 형식의 serialization 및 deserialization을 보여 `Person` 주고를 사용 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 합니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-108">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<span data-ttu-id="82e92-109">일반적으로 JSON serialization 및 deserialization은 AJAX 사용 끝점을 통해 노출 되는 서비스 작업의 데이터 계약 형식을 사용할 때 WCF (Windows Communication Foundation)에 의해 자동으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-109">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="82e92-110">그러나 경우에 따라 JSON 데이터를 직접 사용 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-110">However, in some cases you may need to work with JSON data directly.</span></span>

<span data-ttu-id="82e92-111">이 문서는 [DataContractJsonSerializer 샘플](../samples/json-serialization.md)을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-111">This article is based on the [DataContractJsonSerializer sample](../samples/json-serialization.md).</span></span>

## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="82e92-112">사용자 형식에 대 한 데이터 계약을 정의 하려면</span><span class="sxs-lookup"><span data-stu-id="82e92-112">To define the data contract for a Person type</span></span>

1. <span data-ttu-id="82e92-113">`Person`를 클래스에 연결하고 <xref:System.Runtime.Serialization.DataContractAttribute> 특성을 serialize할 멤버에 연결하여 <xref:System.Runtime.Serialization.DataMemberAttribute>에 대한 데이터 계약을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-113">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="82e92-114">데이터 계약에 대 한 자세한 내용은 [서비스 계약 디자인](../designing-service-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="82e92-114">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>

    ```csharp
    [DataContract]
    internal class Person
    {
        [DataMember]
        internal string name;

        [DataMember]
        internal int age;
    }
    ```

## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="82e92-115">형식 Person의 인스턴스를 JSON으로 serialize하려면</span><span class="sxs-lookup"><span data-stu-id="82e92-115">To serialize an instance of type Person to JSON</span></span>

> [!NOTE]
> <span data-ttu-id="82e92-116">서버에서 보내는 회신을 직렬화 하는 동안 오류가 발생 하거나 다른 이유로 인해 오류가 발생 하는 경우 클라이언트에 오류로 반환 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-116">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>

1. <span data-ttu-id="82e92-117">`Person` 형식의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-117">Create an instance of the `Person` type.</span></span>

    ```csharp
    var p = new Person();
    p.name = "John";
    p.age = 42;
    ```

2. <span data-ttu-id="82e92-118">`Person`를 사용 하 여 개체를 메모리 스트림으로 Serialize <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 합니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-118">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    var stream1 = new MemoryStream();
    var ser = new DataContractJsonSerializer(typeof(Person));
    ```

3. <span data-ttu-id="82e92-119"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 메서드를 사용하여 JSON 데이터를 스트림에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-119">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>

    ```csharp
    ser.WriteObject(stream1, p);
    ```

4. <span data-ttu-id="82e92-120">JSON 출력을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-120">Show the JSON output.</span></span>

    ```csharp
    stream1.Position = 0;
    var sr = new StreamReader(stream1);
    Console.Write("JSON form of Person object: ");
    Console.WriteLine(sr.ReadToEnd());
    ```

## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="82e92-121">JSON에서 형식 Person의 인스턴스를 역직렬화하려면</span><span class="sxs-lookup"><span data-stu-id="82e92-121">To deserialize an instance of type Person from JSON</span></span>

1. <span data-ttu-id="82e92-122">`Person`의 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> 메서드를 사용하여 JSON 인코딩된 데이터를 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>의 새 인스턴스로 역직렬화합니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-122">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    stream1.Position = 0;
    var p2 = (Person)ser.ReadObject(stream1);
    ```

2. <span data-ttu-id="82e92-123">결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-123">Show the results.</span></span>

    ```csharp
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");
    ```

## <a name="example"></a><span data-ttu-id="82e92-124">예제</span><span class="sxs-lookup"><span data-stu-id="82e92-124">Example</span></span>

```csharp
// Create a User object and serialize it to a JSON stream.
public static string WriteFromObject()
{
    // Create User object.
    var user = new User("Bob", 42);

    // Create a stream to serialize the object to.
    var ms = new MemoryStream();

    // Serializer the User object to the stream.
    var ser = new DataContractJsonSerializer(typeof(User));
    ser.WriteObject(ms, user);
    byte[] json = ms.ToArray();
    ms.Close();
    return Encoding.UTF8.GetString(json, 0, json.Length);
}

// Deserialize a JSON stream to a User object.
public static User ReadToObject(string json)
{
    var deserializedUser = new User();
    var ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
    var ser = new DataContractJsonSerializer(deserializedUser.GetType());
    deserializedUser = ser.ReadObject(ms) as User;
    ms.Close();
    return deserializedUser;
}
```

> [!NOTE]
> <span data-ttu-id="82e92-125">JSON serializer는 다음 샘플 코드에서처럼 동일한 이름의 여러 멤버를 가진 데이터 계약에 대한 serialization 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="82e92-125">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>

```csharp
[DataContract]
public class TestDuplicateDataBase
{
    [DataMember]
    public int field1 = 123;
}

[DataContract]
public class TestDuplicateDataDerived : TestDuplicateDataBase
{
    [DataMember]
    public new int field1 = 999;
}
```

## <a name="see-also"></a><span data-ttu-id="82e92-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82e92-126">See also</span></span>

- [<span data-ttu-id="82e92-127">.NET의 JSON serialization</span><span class="sxs-lookup"><span data-stu-id="82e92-127">JSON serialization in .NET</span></span>](../../../standard/serialization/system-text-json-overview.md)
