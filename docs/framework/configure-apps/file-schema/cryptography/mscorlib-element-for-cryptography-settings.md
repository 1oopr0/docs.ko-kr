---
title: 암호화 설정에 대한 <mscorlib> 요소
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: 1788205997d0dc49df172c9dfe48faceb8fc3290
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201787"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="fe90a-102">암호화 설정에 대한 \<mscorlib> 요소</span><span class="sxs-lookup"><span data-stu-id="fe90a-102">\<mscorlib> Element for Cryptography Settings</span></span>

<span data-ttu-id="fe90a-103">[ \<cryptographySettings> 요소](cryptographysettings-element.md)를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe90a-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<mscorlib>**  
  
## <a name="syntax"></a><span data-ttu-id="fe90a-104">구문</span><span class="sxs-lookup"><span data-stu-id="fe90a-104">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe90a-105">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="fe90a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="fe90a-106">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fe90a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe90a-107">특성</span><span class="sxs-lookup"><span data-stu-id="fe90a-107">Attributes</span></span>  

 <span data-ttu-id="fe90a-108">없음</span><span class="sxs-lookup"><span data-stu-id="fe90a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fe90a-109">자식 요소</span><span class="sxs-lookup"><span data-stu-id="fe90a-109">Child Elements</span></span>  
  
|<span data-ttu-id="fe90a-110">요소</span><span class="sxs-lookup"><span data-stu-id="fe90a-110">Element</span></span>|<span data-ttu-id="fe90a-111">설명</span><span class="sxs-lookup"><span data-stu-id="fe90a-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="fe90a-112">암호화 설정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe90a-112">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe90a-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="fe90a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="fe90a-114">요소</span><span class="sxs-lookup"><span data-stu-id="fe90a-114">Element</span></span>|<span data-ttu-id="fe90a-115">설명</span><span class="sxs-lookup"><span data-stu-id="fe90a-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fe90a-116">공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fe90a-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fe90a-117">예제</span><span class="sxs-lookup"><span data-stu-id="fe90a-117">Example</span></span>  

 <span data-ttu-id="fe90a-118">다음 예제에서는 요소를 사용 하 여 **\<mscorlib>** 암호화 클래스를 참조 하 고 런타임을 구성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe90a-118">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="fe90a-119">그런 다음 "RSA" 문자열을 메서드에 전달 하 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 고 메서드를 사용 하 여 개체를 반환할 수 있습니다 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> `MyCryptoRSAClass` .</span><span class="sxs-lookup"><span data-stu-id="fe90a-119">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe90a-120">참조</span><span class="sxs-lookup"><span data-stu-id="fe90a-120">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="fe90a-121">구성 파일 스키마</span><span class="sxs-lookup"><span data-stu-id="fe90a-121">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fe90a-122">암호화 설정 스키마</span><span class="sxs-lookup"><span data-stu-id="fe90a-122">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fe90a-123">암호화 서비스</span><span class="sxs-lookup"><span data-stu-id="fe90a-123">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="fe90a-124">암호화 클래스 구성</span><span class="sxs-lookup"><span data-stu-id="fe90a-124">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
