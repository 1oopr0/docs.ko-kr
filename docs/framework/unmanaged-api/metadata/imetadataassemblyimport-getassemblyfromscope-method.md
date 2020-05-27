---
title: IMetaDataAssemblyImport::GetAssemblyFromScope 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type:
- apiref
ms.openlocfilehash: adcaac02526c7d72ffb75ba6c7552632173032cf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009043"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="53695-102">IMetaDataAssemblyImport::GetAssemblyFromScope 메서드</span><span class="sxs-lookup"><span data-stu-id="53695-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="53695-103">현재 범위에 있는 어셈블리에 대 한 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="53695-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53695-104">구문</span><span class="sxs-lookup"><span data-stu-id="53695-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53695-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="53695-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="53695-106">제한이 어셈블리를 식별 하는 검색 된 토큰에 대 한 포인터입니다 `mdAssembly` .</span><span class="sxs-lookup"><span data-stu-id="53695-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53695-107">요구 사항</span><span class="sxs-lookup"><span data-stu-id="53695-107">Requirements</span></span>  
 <span data-ttu-id="53695-108">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53695-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53695-109">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="53695-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53695-110">**라이브러리:** Mscoree.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53695-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53695-111">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53695-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53695-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="53695-112">See also</span></span>

- [<span data-ttu-id="53695-113">IMetaDataAssemblyImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="53695-113">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
