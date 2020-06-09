---
title: '방법: 디지털 서명으로 XML 문서 서명'
description: 디지털 서명으로 XML 문서에 서명 하는 방법에 대해 알아봅니다. .NET의 System.xml 네임 스페이스에서 클래스를 사용 합니다.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSACryptoServiceProvider class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
ms.openlocfilehash: 97bd23182ed54b899b76dbf43e179fe0c94b011d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598569"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="68e95-104">방법: 디지털 서명으로 XML 문서 서명</span><span class="sxs-lookup"><span data-stu-id="68e95-104">How to: Sign XML Documents with Digital Signatures</span></span>
<span data-ttu-id="68e95-105"><xref:System.Security.Cryptography.Xml> 네임스페이스의 클래스를 사용하여 XML 문서 또는 XML 문서의 일부를 디지털 서명으로 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-105">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="68e95-106">XML 디지털 서명(XMLDSIG)을 사용하면 서명된 후 데이터가 변경되지 않았음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-106">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="68e95-107">XMLDSIG 표준에 대 한 자세한 내용은 W3C (World Wide Web 컨소시엄) 권장 사항 [XML 서명 구문 및 처리](https://www.w3.org/TR/xmldsig-core/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="68e95-107">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="68e95-108">이 절차의 코드 예제에서는 전체 XML 문서를 디지털 서명 하 고 <> 요소의 문서에 서명을 첨부 하는 방법을 보여 줍니다 `Signature` .</span><span class="sxs-lookup"><span data-stu-id="68e95-108">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="68e95-109">이 예제에서는 RSA 서명 키를 만들고, 보안 키 컨테이너에 키를 추가한 다음 키를 사용하여 XML 문서에 디지털 서명합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-109">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="68e95-110">그런 다음 키를 검색하여 XML 디지털 서명을 확인하거나 다른 XML 문서에 서명하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-110">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
 <span data-ttu-id="68e95-111">이 절차를 사용 하 여 만든 XML 디지털 서명을 확인 하는 방법에 대 한 자세한 내용은 [방법: Xml 문서의 디지털 서명 확인](how-to-verify-the-digital-signatures-of-xml-documents.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="68e95-111">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="68e95-112">XML 문서에 디지털 서명하려면</span><span class="sxs-lookup"><span data-stu-id="68e95-112">To digitally sign an XML document</span></span>  
  
1. <span data-ttu-id="68e95-113"><xref:System.Security.Cryptography.CspParameters> 개체를 만들고 키 컨테이너의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-113">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="68e95-114"><xref:System.Security.Cryptography.RSACryptoServiceProvider> 클래스를 사용하여 비대칭 키를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-114">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="68e95-115"><xref:System.Security.Cryptography.RSACryptoServiceProvider> 클래스의 생성자에 <xref:System.Security.Cryptography.CspParameters> 개체를 전달하면 키가 자동으로 키 컨테이너에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-115">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="68e95-116">이 키는 XML 문서에 서명하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-116">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="68e95-117">디스크에서 XML 파일을 로드하여 <xref:System.Xml.XmlDocument> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-117">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="68e95-118"><xref:System.Xml.XmlDocument> 개체는 암호화할 XML 요소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-118">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="68e95-119">새 <xref:System.Security.Cryptography.Xml.SignedXml> 개체를 만들고 <xref:System.Xml.XmlDocument> 개체를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-119">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="68e95-120"><xref:System.Security.Cryptography.Xml.SignedXml> 개체에 서명 RSA 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-120">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="68e95-121">서명할 항목을 설명하는 <xref:System.Security.Cryptography.Xml.Reference> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-121">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="68e95-122">전체 문서에 서명하려면 <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> 속성을 `""`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-122">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="68e95-123"><xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> 개체를 <xref:System.Security.Cryptography.Xml.Reference> 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-123">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="68e95-124">변환을 통해 검증 도구는 서명자가 사용한 것과 동일한 방식으로 XML 데이터를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-124">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="68e95-125">XML 데이터는 다양한 방식으로 표시될 수 있으므로 이 단계는 검증에 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-125">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. <span data-ttu-id="68e95-126"><xref:System.Security.Cryptography.Xml.Reference> 개체를 <xref:System.Security.Cryptography.Xml.SignedXml> 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-126">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="68e95-127"><xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> 메서드를 호출하여 서명을 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-127">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="68e95-128">시그니처의 XML 표시 (<`Signature`> 요소)를 검색 하 여 새 개체에 저장 <xref:System.Xml.XmlElement> 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-128">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="68e95-129"><xref:System.Xml.XmlDocument> 개체에 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-129">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="68e95-130">문서를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-130">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="68e95-131">예제</span><span class="sxs-lookup"><span data-stu-id="68e95-131">Example</span></span>  
 <span data-ttu-id="68e95-132">이 예제에서는 `test.xml`이라는 파일이 컴파일된 프로그램과 동일한 디렉터리에 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-132">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="68e95-133">`test.xml`이라는 파일에 다음 XML을 배치하고 이 예제에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-133">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="68e95-134">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="68e95-134">Compiling the Code</span></span>  
  
- <span data-ttu-id="68e95-135">이 예제를 컴파일하려면 `System.Security.dll`에 대한 참조를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-135">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="68e95-136"><xref:System.Xml>, <xref:System.Security.Cryptography> 및 <xref:System.Security.Cryptography.Xml> 네임스페이스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-136">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="68e95-137">.NET Framework 보안</span><span class="sxs-lookup"><span data-stu-id="68e95-137">.NET Framework Security</span></span>  
 <span data-ttu-id="68e95-138">비대칭 키 쌍의 프라이빗 키를 일반 텍스트로 저장하거나 전송하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="68e95-138">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="68e95-139">대칭 및 비대칭 암호화 키에 대 한 자세한 내용은 [암호화 및 암호 해독을 위한 키 생성](generating-keys-for-encryption-and-decryption.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="68e95-139">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="68e95-140">소스 코드에 직접 프라이빗 키를 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="68e95-140">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="68e95-141">[Ildasm.exe (IL 디스어셈블러)](../../framework/tools/ildasm-exe-il-disassembler.md) 를 사용 하거나 메모장과 같은 텍스트 편집기에서 어셈블리를 열어 어셈블리에서 포함 된 키를 쉽게 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e95-141">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e95-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68e95-142">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="68e95-143">방법: XML 문서의 디지털 서명 확인</span><span class="sxs-lookup"><span data-stu-id="68e95-143">How to: Verify the Digital Signatures of XML Documents</span></span>](how-to-verify-the-digital-signatures-of-xml-documents.md)
