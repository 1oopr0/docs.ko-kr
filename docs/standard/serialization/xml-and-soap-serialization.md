---
title: XML 및 SOAP Serialization
description: 이 개요에서는 SOAP 사양을 준수하는 XML 스트림으로 개체를 직렬화하는 데 사용할 수 있는 XML serialization에 대해 설명합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: 6b7d6f59694a28207758fa7772781eed073917e4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379539"
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="ac8b6-103">XML 및 SOAP serialization</span><span class="sxs-lookup"><span data-stu-id="ac8b6-103">XML and SOAP serialization</span></span>

<span data-ttu-id="ac8b6-104">XML serialization은 개체의 공용 필드와 속성, 메서드의 매개 변수와 반환 값을 특정 XSD(XML 스키마 정의 언어) 문서와 일치하는 XML 스트림으로 변환(serialize)합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8b6-104">XML serialization converts (serializes) the public fields and properties of an object, and the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="ac8b6-105">XML serialization을 사용하면 스토리지이나 전송을 위해 직렬 형식(이 경우 XML)으로 변환되는 public 속성 및 필드가 있는 강력한 형식의 클래스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ac8b6-105">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="ac8b6-106">XML은 공개 표준이기 때문에 XML 스트림은 플랫폼에 관계없이 필요에 따라 모든 애플리케이션에서 처리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8b6-106">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="ac8b6-107">예를 들어 ASP.NET을 사용하여 만들어진 XML Web services는 <xref:System.Xml.Serialization.XmlSerializer> 클래스를 사용하여 데이터를 인터넷이나 인트라넷을 통해 XML Web services 애플리케이션 간에 전달하는 XML 스트림을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac8b6-107">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="ac8b6-108">이와 반대로 deserialization에서는 이러한 XML 스트림을 받아서 개체를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac8b6-108">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="ac8b6-109">XML serialization은 SOAP 사양과 일치하는 XML 스트림으로 개체를 serialize하는 데 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8b6-109">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="ac8b6-110">SOAP는 특히 XML을 사용하여 프로시저 호출을 전송하기 위해 디자인된 XML 기반 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="ac8b6-110">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="ac8b6-111">개체를 직렬화하거나 역직렬화하려면 <xref:System.Xml.Serialization.XmlSerializer> 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8b6-111">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="ac8b6-112">클래스가 serialize되도록 하려면 XML 스키마 정의 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8b6-112">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac8b6-113">참조</span><span class="sxs-lookup"><span data-stu-id="ac8b6-113">See also</span></span>

- [<span data-ttu-id="ac8b6-114">이진 serialization</span><span class="sxs-lookup"><span data-stu-id="ac8b6-114">Binary Serialization</span></span>](binary-serialization.md)
- <span data-ttu-id="ac8b6-115">[ASP.NET 및 XML Web Service 클라이언트를 사용하여 만든 XML Web Services](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ac8b6-115">[XML Web Services created using ASP.NET and XML Web Service clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>
