---
title: 버전 독립적 Serialization
description: .NET Framework 2.0에는 직렬화 가능 형식을 보다 쉽게 수정할 수 있는 기능 집합인 버전 독립적 Serialization이 도입되었습니다.
ms.date: 08/08/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- version tolerant serialization
- serialization, custom serialization
- serialization, version tolerant
- serialization, controlling
- versions and serialization
- BinaryFormatter class, samples
- serialization, attributes
ms.assetid: bea0ffe3-2708-4a16-ac7d-e586ed6b8e8d
ms.openlocfilehash: afc822e1f8873bac069f6634fdf1d4665d392e69
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762593"
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="2ef68-103">버전 독립적 Serialization</span><span class="sxs-lookup"><span data-stu-id="2ef68-103">Version tolerant serialization</span></span>

<span data-ttu-id="2ef68-104">.NET Framework의 버전 1.0과 1.1에서는 버전이 다른 애플리케이션에서 재사용할 수 있는 serialize 가능한 형식을 만드는 작업에 문제가 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-104">In version 1.0 and 1.1 of the .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="2ef68-105">추가 필드를 추가하여 형식을 수정하면 다음 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-105">If a type was modified by adding extra fields, the following problems would occur:</span></span>

- <span data-ttu-id="2ef68-106">이전 형식의 새 버전을 역직렬화하도록 요청하면 애플리케이션의 이전 버전이 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-106">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>
- <span data-ttu-id="2ef68-107">데이터가 누락된 형식의 이전 버전을 역직렬화할 때 애플리케이션의 새 버전이 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-107">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>

<span data-ttu-id="2ef68-108">VTS(버전 독립적 Serialization)는 .NET Framework 2.0에 추가된 기능 집합으로, serialize 가능한 형식을 시간이 지남에 따라 더 쉽게 수정할 수 있게 해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-108">Version Tolerant Serialization (VTS) is a set of features introduced in .NET Framework 2.0 that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="2ef68-109">특히 VTS 기능은 제네릭 형식을 비롯하여 <xref:System.SerializableAttribute> 특성이 적용된 클래스에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-109">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="2ef68-110">VTS를 사용하면 형식의 다른 버전과의 호환성을 휴지하면서 해당 클래스에 새 필드를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-110">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span> <span data-ttu-id="2ef68-111">작동하는 애플리케이션 예제는 [버전 독립적 serialization 기술 샘플](basic-serialization-technology-sample.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ef68-111">For a working sample application, see [Version Tolerant Serialization Technology Sample](basic-serialization-technology-sample.md).</span></span>

<span data-ttu-id="2ef68-112">VTS 기능은 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>를 사용할 때 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-112">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="2ef68-113">또한 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>를 사용할 때 잘못 사용된 데이터 허용 범위를 제외한 모든 기능도 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-113">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="2ef68-114">serialization에 이러한 클래스를 사용하는 방법에 대한 자세한 내용은 [이진 serialization](binary-serialization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ef68-114">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="2ef68-115">기능 목록</span><span class="sxs-lookup"><span data-stu-id="2ef68-115">Feature list</span></span>

<span data-ttu-id="2ef68-116">이러한 기능 집합에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-116">The set of features includes the following:</span></span>

- <span data-ttu-id="2ef68-117">잘못 사용된 또는 예기치 않은 데이터의 허용 범위.</span><span class="sxs-lookup"><span data-stu-id="2ef68-117">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="2ef68-118">이를 통해 형식의 새 버전이 데이터를 이전 버전으로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-118">This enables newer versions of the type to send data to older versions.</span></span>
- <span data-ttu-id="2ef68-119">누락된 선택적 데이터의 허용 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-119">Tolerance of missing optional data.</span></span> <span data-ttu-id="2ef68-120">이전 버전이 새 버전에 데이터를 전송할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-120">This enables older versions to send data to newer versions.</span></span>
- <span data-ttu-id="2ef68-121">콜백 serialization.</span><span class="sxs-lookup"><span data-stu-id="2ef68-121">Serialization callbacks.</span></span> <span data-ttu-id="2ef68-122">이를 통해 데이터가 누락되었을 때 지능적으로 기본값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-122">This enables intelligent default value setting in cases where data is missing.</span></span>

<span data-ttu-id="2ef68-123">또한 새 선택적 필드가 추가되었을 때 선언하기 위한 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-123">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="2ef68-124">이것은 <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> 특성의 <xref:System.Runtime.Serialization.OptionalFieldAttribute> 속성</span><span class="sxs-lookup"><span data-stu-id="2ef68-124">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>

<span data-ttu-id="2ef68-125">다음 섹션에서는 이러한 기능에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-125">These features are discussed in greater detail in the following sections.</span></span>

### <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="2ef68-126">잘못 사용된 또는 예기치 않은 데이터의 허용치</span><span class="sxs-lookup"><span data-stu-id="2ef68-126">Tolerance of extraneous or unexpected data</span></span>

<span data-ttu-id="2ef68-127">과거에는 deserialization 도중 모든 잘못 사용된 데이터나 예기치 않은 데이터로 인해 예외를 throw하는 경우가 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-127">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="2ef68-128">VTS를 사용하면 같은 상황에서 잘못 사용된 데이터나 예기치 않은 데이터가 예외를 throw하는 대신 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-128">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="2ef68-129">이를 통해 형식의 새 버전(즉, 더 많은 필드가 포함된 버전)을 사용하는 애플리케이션이 같은 형식의 이전 버전으로 예상되는 애플리케이션에 정보를 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-129">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>

<span data-ttu-id="2ef68-130">다음 예제에서는 이전 애플리케이션이 새 버전을 역직렬화할 때 `CountryField` 클래스 버전 2.0의 `Address`에 포함된 추가 데이터가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-130">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>

```csharp  
// Version 1 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
}  
// Version 2.0 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    // The older application ignores this data.  
    public string CountryField;  
}  
```  
  
```vb  
' Version 1 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
End Class  
  
' Version 2.0 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    ' The older application ignores this data.  
    Public CountryField As String  
End Class  
```  

### <a name="tolerance-of-missing-data"></a><span data-ttu-id="2ef68-131">누락된 데이터의 허용치</span><span class="sxs-lookup"><span data-stu-id="2ef68-131">Tolerance of missing data</span></span>

<span data-ttu-id="2ef68-132">필드에 <xref:System.Runtime.Serialization.OptionalFieldAttribute> 특성을 적용하여 해당 필드를 선택 사항으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-132">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="2ef68-133">deserialization 도중 선택적 데이터가 누락된 경우 serialization 엔진은 이를 무시하고 예외를 throw하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-133">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="2ef68-134">따라서 형식의 이전 버전이 필요한 애플리케이션은 같은 형식의 새 버전이 필요한 애플리케이션에 데이터를 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-134">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>

<span data-ttu-id="2ef68-135">다음 예제에서는 `Address` 필드가 선택 사항으로 표시된 `CountryField` 클래스의 버전 2.0을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-135">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="2ef68-136">이전 애플리케이션이 버전 2.0이 필요한 새 애플리케이션에 버전 1을 전송하면 데이터의 부재가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-136">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;

    [OptionalField]
    public string CountryField;
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String

    <OptionalField> _
    Public CountryField As String
End Class
```
  
### <a name="serialization-callbacks"></a><span data-ttu-id="2ef68-137">serialization 콜백</span><span class="sxs-lookup"><span data-stu-id="2ef68-137">Serialization callbacks</span></span>

<span data-ttu-id="2ef68-138">콜백 serialization은 네 지점에서 serialization/deserialization 프로세스에 대한 후킹을 제공하는 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-138">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>

|<span data-ttu-id="2ef68-139">특성</span><span class="sxs-lookup"><span data-stu-id="2ef68-139">Attribute</span></span>|<span data-ttu-id="2ef68-140">연결된 메서드가 호출된 경우</span><span class="sxs-lookup"><span data-stu-id="2ef68-140">When the Associated Method is Called</span></span>|<span data-ttu-id="2ef68-141">일반적인 용도</span><span class="sxs-lookup"><span data-stu-id="2ef68-141">Typical Use</span></span>|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="2ef68-142">deserialization 이전.\*</span><span class="sxs-lookup"><span data-stu-id="2ef68-142">Before deserialization.\*</span></span>|<span data-ttu-id="2ef68-143">선택적 필드에 대한 기본 값을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-143">Initialize default values for optional fields.</span></span>|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="2ef68-144">deserialization 후</span><span class="sxs-lookup"><span data-stu-id="2ef68-144">After deserialization.</span></span>|<span data-ttu-id="2ef68-145">선택된 필드 값을 다른 필드의 내용에 따라 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-145">Fix optional field values based on contents of other fields.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="2ef68-146">serialization 이전</span><span class="sxs-lookup"><span data-stu-id="2ef68-146">Before serialization.</span></span>|<span data-ttu-id="2ef68-147">serialization을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-147">Prepare for serialization.</span></span> <span data-ttu-id="2ef68-148">예를 들어 선택적 데이터 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-148">For example, create optional data structures.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="2ef68-149">serialization 이후</span><span class="sxs-lookup"><span data-stu-id="2ef68-149">After serialization.</span></span>|<span data-ttu-id="2ef68-150">serialization 이벤트를 로그합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-150">Log serialization events.</span></span>|

 <span data-ttu-id="2ef68-151">\* 이 콜백은 deserialization 생성자(있는 경우)보다 먼저 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-151">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>

#### <a name="using-callbacks"></a><span data-ttu-id="2ef68-152">콜백 사용</span><span class="sxs-lookup"><span data-stu-id="2ef68-152">Using callbacks</span></span>

<span data-ttu-id="2ef68-153">콜백을 사용하려면 <xref:System.Runtime.Serialization.StreamingContext> 매개 변수를 받는 메서드에 적절한 특성을 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-153">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="2ef68-154">클래스당 하나의 메서드만 이들 각 속성으로 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-154">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="2ef68-155">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="2ef68-155">For example:</span></span>

```csharp
[OnDeserializing]
private void SetCountryRegionDefault(StreamingContext sc)
{
    CountryField = "Japan";
}
```

```vb
<OnDeserializing>
Private Sub SetCountryRegionDefault(sc As StreamingContext)
    CountryField = "Japan"
End Sub
```

<span data-ttu-id="2ef68-156">이 메서드의 용도 중에는 버전 관리 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-156">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="2ef68-157">deserialization 도중 필드에 대한 데이터가 없으면 선택적 필드가 올바르게 초기화되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-157">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="2ef68-158">이 문제는 올바른 값을 할당하는 메서드를 만들고 **OnDeserializingAttribute** 또는 **OnDeserializedAttribute** 특성을 메서드에 적용하여 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-158">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>

<span data-ttu-id="2ef68-159">다음 예제에서는 형식의 컨텍스트에서 메서드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-159">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="2ef68-160">애플리케이션의 이전 버전이 `Address` 클래스의 인스턴스를 애플리케이션의 새 버전으로 전송하면 `CountryField` 필드 데이터가 누락됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-160">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="2ef68-161">하지만 deserialization 이후에는 필드가 기본값인 "Japan"으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-161">But after deserialization, the field will be set to a default value "Japan".</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;
    [OptionalField]
    public string CountryField;

    [OnDeserializing]
    private void SetCountryRegionDefault(StreamingContext sc)
    {
        CountryField = "Japan";
    }
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String
    <OptionalField> _
    Public CountryField As String

    <OnDeserializing> _
    Private Sub SetCountryRegionDefault(sc As StreamingContext)
        CountryField = "Japan"
    End Sub
End Class
```

## <a name="the-versionadded-property"></a><span data-ttu-id="2ef68-162">VersionAdded 속성</span><span class="sxs-lookup"><span data-stu-id="2ef68-162">The VersionAdded property</span></span>

<span data-ttu-id="2ef68-163">**OptionalFieldAttribute**에는 **VersionAdded** 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-163">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="2ef68-164">.NET Framework의 버전 2.0에서는 이 속성이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-164">In version 2.0 of the .NET Framework, this isn't used.</span></span> <span data-ttu-id="2ef68-165">하지만 형식이 미래의 serialization 엔진과 호환되도록 이 속성을 올바르게 설정하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-165">However, it's important to set this property correctly to ensure that the type will be compatible with future serialization engines.</span></span>

<span data-ttu-id="2ef68-166">속성은 해당 필드가 추가된 형식의 버전을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-166">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="2ef68-167">다음 예제처럼 형식이 수정될 때마다 1씩(2부터 시작) 증가되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-167">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>

```csharp
// Version 1.0
[Serializable]
public class Person
{
    public string FullName;
}

// Version 2.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded = 2)]
    public string NickName;
    [OptionalField(VersionAdded = 2)]
    public DateTime BirthDate;
}

// Version 3.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded=2)]
    public string NickName;
    [OptionalField(VersionAdded=2)]
    public DateTime BirthDate;

    [OptionalField(VersionAdded=3)]
    public int Weight;
}
```

```vb
' Version 1.0
<Serializable> _
Public Class Person
    Public FullName
End Class

' Version 2.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime
End Class

' Version 3.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime

    <OptionalField(VersionAdded := 3)> _
    Public Weight As Integer
End Class
```

## <a name="serializationbinder"></a><span data-ttu-id="2ef68-168">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="2ef68-168">SerializationBinder</span></span>

<span data-ttu-id="2ef68-169">서버와 클라이언트에서 서로 다른 버전의 클래스를 필요로 하므로 일부 사용자는 직렬화 및 역직렬화할 클래스를 제어해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-169">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="2ef68-170"><xref:System.Runtime.Serialization.SerializationBinder>는 serialization 및 deserialization 중에 사용되는 실제 형식을 제어하는 데 사용되는 추상 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-170"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="2ef68-171">이 클래스를 사용하려면 <xref:System.Runtime.Serialization.SerializationBinder>에서 클래스를 파생시키고 <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> 및 <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-171">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> <span data-ttu-id="2ef68-172">자세한 내용은 [SerializationBinder를 사용하여 serialization 및 deserialization 제어](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ef68-172">For more information, see [Controlling Serialization and Deserialization with SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>

## <a name="best-practices"></a><span data-ttu-id="2ef68-173">최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="2ef68-173">Best practices</span></span>

<span data-ttu-id="2ef68-174">적절한 버전 관리 동작을 구현하려면 버전 간에 형식을 수정할 때 다음과 같은 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-174">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>

- <span data-ttu-id="2ef68-175">serialize된 필드를 제거하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="2ef68-175">Never remove a serialized field.</span></span>
- <span data-ttu-id="2ef68-176">특성이 이전 버전에서 필드에 적용되지 않은 경우에는 <xref:System.NonSerializedAttribute> 특성을 필드에 적용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="2ef68-176">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>
- <span data-ttu-id="2ef68-177">serialize된 필드의 이름이나 형식을 변경하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="2ef68-177">Never change the name or the type of a serialized field.</span></span>
- <span data-ttu-id="2ef68-178">새 직렬화된 필드를 추가할 때 **OptionalFieldAttribute** 특성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-178">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="2ef68-179">**NonSerializedAttribute** 특성을 필드에서 제거할 때(이전 버전에서는 직렬화할 수 없었음) **OptionalFieldAttribute** 특성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-179">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="2ef68-180">모든 선택적 필드에 대해 0 또는 **null**을 기본값으로 사용할 수 있는 경우 이외에는 serialization 콜백을 사용하여 의미 있는 기본값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-180">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>

<span data-ttu-id="2ef68-181">형식이 미래의 serialization 엔진과 호환되도록 이 속성을 올바르게 설정하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-181">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>

- <span data-ttu-id="2ef68-182">항상 **OptionalFieldAttribute** 특성의 **VersionAdded** 속성을 올바르게 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2ef68-182">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>
- <span data-ttu-id="2ef68-183">버전 관리 침해 방지</span><span class="sxs-lookup"><span data-stu-id="2ef68-183">Avoid branched versioning.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ef68-184">참조</span><span class="sxs-lookup"><span data-stu-id="2ef68-184">See also</span></span>

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [<span data-ttu-id="2ef68-185">이진 serialization</span><span class="sxs-lookup"><span data-stu-id="2ef68-185">Binary Serialization</span></span>](binary-serialization.md)
