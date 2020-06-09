---
title: '방법: 인증서 지문 검색'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: f59fad86287e89b0a573a6e3ee8420f384b0bc3b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601207"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a><span data-ttu-id="177ac-102">방법: 인증서 지문 검색</span><span class="sxs-lookup"><span data-stu-id="177ac-102">How to: Retrieve the Thumbprint of a Certificate</span></span>
<span data-ttu-id="177ac-103">인증에 x.509 인증서를 사용 하는 WCF (Windows Communication Foundation) 응용 프로그램을 작성 하는 경우 인증서에 있는 클레임을 지정 해야 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-103">When writing a Windows Communication Foundation (WCF) application that uses an X.509 certificate for authentication, it is often necessary to specify claims found in the certificate.</span></span> <span data-ttu-id="177ac-104">예를 들어 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> 메서드에 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 열거를 사용하는 경우 지문 클레임을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-104">For example, you must supply a thumbprint claim when using the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> enumeration in the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="177ac-105">클레임 값을 찾는 과정은 두 단계로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-105">Finding the claim value requires two steps.</span></span> <span data-ttu-id="177ac-106">첫째, 인증서에 대한 MMC(Microsoft Management Console) 스냅인을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-106">First, open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="177ac-107">[방법: MMC 스냅인을 사용 하 여 인증서 보기](how-to-view-certificates-with-the-mmc-snap-in.md)를 참조 하세요. 두 번째는 여기에 설명 된 대로 적절 한 인증서를 찾고 해당 지문 (또는 기타 클레임 값)을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-107">(See [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).) Second, as described here, find an appropriate certificate and copy its thumbprint (or other claim values).</span></span>  
  
 <span data-ttu-id="177ac-108">서비스 인증에 인증서를 사용하는 경우 **발급 대상** 열(콘솔의 첫 번째 열)의 값을 확인하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-108">If you are using a certificate for service authentication, it is important to note the value of the **Issued To** column (the first column in the console).</span></span> <span data-ttu-id="177ac-109">SSL(Secure Sockets Layer)을 전송 보안으로 사용하는 경우 수행되는 첫 번째 확인 작업 중 하나는 서비스의 기본 주소 URI(Uniform Resource Identifier)를 **발급 대상** 값과 비교하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-109">When using Secure Sockets Layer (SSL) as a transport security, one of the first checks done is to compare the base address Uniform Resource Identifier (URI) of a service to the **Issued To** value.</span></span> <span data-ttu-id="177ac-110">값이 일치해야 하며, 그렇지 않으면 인증 프로세스가 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-110">The values must match or the authentication process is halted.</span></span>  
  
 <span data-ttu-id="177ac-111">Powershell New-selfsignedcertificate cmdlet을 사용 하 여 개발 중에만 사용할 임시 인증서를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-111">You can also use the Powershell New-SelfSignedCertificate cmdlet to create temporary certificates for use only during development.</span></span> <span data-ttu-id="177ac-112">그러나 이러한 인증서는 기본적으로 인증 기관에서 발급 되지 않으며 프로덕션 용도로는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-112">By default, however, such a certificate is not issued by a certification authority and is unusable for production purposes.</span></span> <span data-ttu-id="177ac-113">자세한 내용은 [방법: 개발 하는 동안 사용할 임시 인증서 만들기](how-to-create-temporary-certificates-for-use-during-development.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="177ac-113">For more information, see [How to: Create Temporary Certificates for Use During Development](how-to-create-temporary-certificates-for-use-during-development.md).</span></span>  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a><span data-ttu-id="177ac-114">인증서의 지문을 검색하려면</span><span class="sxs-lookup"><span data-stu-id="177ac-114">To retrieve a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="177ac-115">인증서에 대한 MMC(Microsoft Management Console) 스냅인을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-115">Open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="177ac-116">[How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="177ac-116">(See [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).)</span></span>  
  
2. <span data-ttu-id="177ac-117">**콘솔 루트** 창의 왼쪽 창에서 **인증서(로컬 컴퓨터)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-117">In the **Console Root** window's left pane, click **Certificates (Local Computer)**.</span></span>  
  
3. <span data-ttu-id="177ac-118">**개인** 폴더를 클릭하여 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-118">Click the **Personal** folder to expand it.</span></span>  
  
4. <span data-ttu-id="177ac-119">**인증서** 폴더를 클릭하여 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-119">Click the **Certificates** folder to expand it.</span></span>  
  
5. <span data-ttu-id="177ac-120">인증서 목록에서 **용도** 제목을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-120">In the list of certificates, note the **Intended Purposes** heading.</span></span> <span data-ttu-id="177ac-121">**클라이언트 인증** 을 용도로 표시하는 인증서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-121">Find a certificate that lists **Client Authentication** as an intended purpose.</span></span>  
  
6. <span data-ttu-id="177ac-122">인증서를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-122">Double-click the certificate.</span></span>  
  
7. <span data-ttu-id="177ac-123">**인증서** 대화 상자에서 **자세히** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-123">In the **Certificate** dialog box, click the **Details** tab.</span></span>  
  
8. <span data-ttu-id="177ac-124">필드 목록을 스크롤하여 **지문**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-124">Scroll through the list of fields and click **Thumbprint**.</span></span>  
  
9. <span data-ttu-id="177ac-125">상자에서 16진수 문자를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-125">Copy the hexadecimal characters from the box.</span></span> <span data-ttu-id="177ac-126">`X509FindType`에 대한 코드에서 이 지문을 사용하는 경우 16진수 사이의 공백을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-126">If this thumbprint is used in code for the `X509FindType`, remove the spaces between the hexadecimal numbers.</span></span> <span data-ttu-id="177ac-127">예를 들어 지문 "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b"는 코드에서 "a909502dd82ae41433e6f83886b00d4277a32a7b"로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="177ac-127">For example, the thumbprint "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" should be specified as "a909502dd82ae41433e6f83886b00d4277a32a7b" in code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="177ac-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="177ac-128">See also</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>
- [<span data-ttu-id="177ac-129">방법: SSL 인증서를 사용하여 포트 구성</span><span class="sxs-lookup"><span data-stu-id="177ac-129">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="177ac-130">방법: MMC 스냅인을 사용하여 인증서 보기</span><span class="sxs-lookup"><span data-stu-id="177ac-130">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="177ac-131">방법: 개발 중에 사용할 임시 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="177ac-131">How to: Create Temporary Certificates for Use During Development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
