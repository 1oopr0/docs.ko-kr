---
title: ICLRStrongName::StrongNameSignatureGeneration 메서드
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: a8c9eab719f6a4f233490e544f67cf779ea10b20
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763042"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a>ICLRStrongName::StrongNameSignatureGeneration 메서드
지정된 어셈블리에 대한 강력한 이름 서명을 생성합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 `wszFilePath`  
 진행 강력한 이름 서명이 생성 될 어셈블리의 매니페스트가 포함 된 파일의 경로입니다.  
  
 `wszKeyContainer`  
 진행 공개/개인 키 쌍을 포함 하는 키 컨테이너의 이름입니다.  
  
 가 null 인 경우는 `pbKeyBlob` `wszKeyContainer` CSP (암호화 서비스 공급자) 내에 올바른 컨테이너를 지정 해야 합니다. 이 경우 컨테이너에 저장 된 키 쌍을 사용 하 여 파일에 서명 합니다.  
  
 `pbKeyBlob`가 null이 아닌 경우 키 쌍은 키 BLOB (binary large object)에 포함 된 것으로 간주 됩니다.  
  
 키는 1024 비트 RSA (Rivest Rivest-shamir-adleman Rivest-shamir-adleman) 서명 키 여야 합니다. 지금은 다른 유형의 키를 지원 하지 않습니다.  
  
 `pbKeyBlob`  
 진행 공개/개인 키 쌍에 대 한 포인터입니다. 이 쌍은 Win32 함수에서 만든 형식입니다 `CryptExportKey` . 가 null 인 경우에 `pbKeyBlob` 지정 된 키 컨테이너는 `wszKeyContainer` 키 쌍을 포함 하는 것으로 간주 됩니다.  
  
 `cbKeyBlob`  
 진행 의 크기 (바이트)입니다 `pbKeyBlob` .  
  
 `ppbSignatureBlob`  
 제한이 공용 언어 런타임에서 서명을 반환 하는 위치에 대 한 포인터입니다. `ppbSignatureBlob`가 null 이면 런타임에서는에 지정 된 파일에 서명을 저장 합니다 `wszFilePath` .  
  
 `ppbSignatureBlob`가 null이 아닌 경우 공용 언어 런타임은 서명을 반환할 공간을 할당 합니다. 호출자는 [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 메서드를 사용 하 여이 공간을 확보 해야 합니다.  
  
 `pcbSignatureBlob`  
 제한이 반환 된 시그니처의 크기 (바이트)입니다.  
  
## <a name="return-value"></a>Return Value  
 `S_OK`메서드가 성공적으로 완료 되었으면이 고, 그렇지 않으면입니다. 그렇지 않으면 오류를 나타내는 HRESULT 값입니다 (목록의 [일반적인 Hresult 값](/windows/win32/seccrypto/common-hresult-values) 참조).  
  
## <a name="remarks"></a>설명  
 에 대해 null `wszFilePath` 을 지정 하 여 서명을 만들지 않고 서명의 크기를 계산 합니다.  
  
 시그니처는 파일에 직접 저장 되거나 호출자에 게 반환 될 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** MetaHost  
  
 **라이브러리:** Mscoree.dll에 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>참조

- [StrongNameSignatureGenerationEx 메서드](iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName 인터페이스](iclrstrongname-interface.md)
