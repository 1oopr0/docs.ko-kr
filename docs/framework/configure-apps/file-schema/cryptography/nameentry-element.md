---
title: <nameEntry> 요소
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: a339638587f8b544bbc1b0073553f6232ce09694
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71699775"
---
# <a name="nameentry-element"></a><span data-ttu-id="7ddb8-102">\<nameEntry> 요소</span><span class="sxs-lookup"><span data-stu-id="7ddb8-102">\<nameEntry> Element</span></span>
<span data-ttu-id="7ddb8-103">클래스 이름을 알고리즘 이름에 매핑하며, 이를 통해 하나의 클래스가 여러 이름을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**  
  
## <a name="syntax"></a><span data-ttu-id="7ddb8-104">구문</span><span class="sxs-lookup"><span data-stu-id="7ddb8-104">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ddb8-105">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="7ddb8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7ddb8-106">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ddb8-107">특성</span><span class="sxs-lookup"><span data-stu-id="7ddb8-107">Attributes</span></span>  
  
|<span data-ttu-id="7ddb8-108">attribute</span><span class="sxs-lookup"><span data-stu-id="7ddb8-108">Attribute</span></span>|<span data-ttu-id="7ddb8-109">Description</span><span class="sxs-lookup"><span data-stu-id="7ddb8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7ddb8-110">**name**</span><span class="sxs-lookup"><span data-stu-id="7ddb8-110">**name**</span></span>|<span data-ttu-id="7ddb8-111">필수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="7ddb8-112">암호화 클래스가 구현 하는 알고리즘의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-112">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="7ddb8-113">**class**</span><span class="sxs-lookup"><span data-stu-id="7ddb8-113">**class**</span></span>|<span data-ttu-id="7ddb8-114">필수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="7ddb8-115">요소의 **name** 특성에 대 한 값을 지정 합니다 [\<cryptoClass>](cryptoclass-element.md) .</span><span class="sxs-lookup"><span data-stu-id="7ddb8-115">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ddb8-116">자식 요소</span><span class="sxs-lookup"><span data-stu-id="7ddb8-116">Child Elements</span></span>  
 <span data-ttu-id="7ddb8-117">없음</span><span class="sxs-lookup"><span data-stu-id="7ddb8-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ddb8-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="7ddb8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7ddb8-119">요소</span><span class="sxs-lookup"><span data-stu-id="7ddb8-119">Element</span></span>|<span data-ttu-id="7ddb8-120">Description</span><span class="sxs-lookup"><span data-stu-id="7ddb8-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7ddb8-121">공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="7ddb8-122">ASP.NET 구성 섹션의 루트 요소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-122">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ddb8-123">설명</span><span class="sxs-lookup"><span data-stu-id="7ddb8-123">Remarks</span></span>  
 <span data-ttu-id="7ddb8-124">**Name** 특성은 네임 스페이스에 있는 추상 클래스 중 하나의 이름일 수 있습니다 <xref:System.Security.Cryptography> .</span><span class="sxs-lookup"><span data-stu-id="7ddb8-124">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="7ddb8-125">추상 암호화 클래스에서 **Create** 메서드를 호출 하는 경우 추상 클래스 이름이 메서드에 전달 됩니다 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> .</span><span class="sxs-lookup"><span data-stu-id="7ddb8-125">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="7ddb8-126">**Createfromname** 은 **클래스** 특성이 나타내는 형식의 인스턴스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-126">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="7ddb8-127">**이름** 특성이 RSA와 같은 짧은 이름인 경우 **createfromname** 메서드를 호출할 때 해당 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-127">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ddb8-128">예제</span><span class="sxs-lookup"><span data-stu-id="7ddb8-128">Example</span></span>  
 <span data-ttu-id="7ddb8-129">다음 예제에서는 요소를 사용 하 여 **\<nameEntry>** 암호화 클래스를 참조 하 고 런타임을 구성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ddb8-129">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="7ddb8-130">그런 다음 "RSA" 문자열을 메서드에 전달 하 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 고 메서드를 사용 하 여 개체를 반환할 수 있습니다 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> `MyCryptoRSAClass` .</span><span class="sxs-lookup"><span data-stu-id="7ddb8-130">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ddb8-131">참조</span><span class="sxs-lookup"><span data-stu-id="7ddb8-131">See also</span></span>

- [<span data-ttu-id="7ddb8-132">구성 파일 스키마</span><span class="sxs-lookup"><span data-stu-id="7ddb8-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7ddb8-133">암호화 설정 스키마</span><span class="sxs-lookup"><span data-stu-id="7ddb8-133">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7ddb8-134">암호화 서비스</span><span class="sxs-lookup"><span data-stu-id="7ddb8-134">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="7ddb8-135">암호화 클래스 구성</span><span class="sxs-lookup"><span data-stu-id="7ddb8-135">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
