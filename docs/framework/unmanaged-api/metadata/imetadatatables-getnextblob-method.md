---
title: IMetaDataTables::GetNextBlob 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
ms.openlocfilehash: 086448248364403b718408ad8bd32e48447742d0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490383"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="a90a4-102">IMetaDataTables::GetNextBlob 메서드</span><span class="sxs-lookup"><span data-stu-id="a90a4-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="a90a4-103">테이블에서 다음 BLOB (binary large object)의 인덱스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a90a4-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a90a4-104">구문</span><span class="sxs-lookup"><span data-stu-id="a90a4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a90a4-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a90a4-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="a90a4-106">진행 Blob의 열에서 반환 된 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="a90a4-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="a90a4-107">제한이 다음 BLOB의 인덱스에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a90a4-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a90a4-108">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a90a4-108">Requirements</span></span>  
 <span data-ttu-id="a90a4-109">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a90a4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a90a4-110">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="a90a4-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a90a4-111">**라이브러리:** Mscoree.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a90a4-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a90a4-112">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a90a4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a90a4-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a90a4-113">See also</span></span>

- [<span data-ttu-id="a90a4-114">IMetaDataTables 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a90a4-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="a90a4-115">IMetaDataTables2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a90a4-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
