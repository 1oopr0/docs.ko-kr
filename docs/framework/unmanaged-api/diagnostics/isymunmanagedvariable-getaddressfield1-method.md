---
title: ISymUnmanagedVariable::GetAddressField1 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
ms.openlocfilehash: 253fd17178c03bc0c4d8ea031888a404ad56f876
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615282"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a>ISymUnmanagedVariable::GetAddressField1 메서드
이 변수의 첫 번째 주소 필드를 가져옵니다. 이는 주소 유형에 따라 달라 집니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>매개 변수  
 `pRetVal`  
 제한이 `ULONG32`첫 번째 주소 필드를 수신 하는에 대 한 포인터입니다.  
  
## <a name="return-value"></a>Return Value  
 메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** CorSym, CorSym  
  
## <a name="see-also"></a>참고 항목

- [ISymUnmanagedVariable 인터페이스](isymunmanagedvariable-interface.md)
- [GetAddressField2 메서드](isymunmanagedvariable-getaddressfield2-method.md)
- [GetAddressField3 메서드](isymunmanagedvariable-getaddressfield3-method.md)
- [GetAddressKind 메서드](isymunmanagedvariable-getaddresskind-method.md)
