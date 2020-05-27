---
title: IMetaDataEmit::SetPropertyProps 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: b5af877c26c20bf64a27618bf24a7bce5b410419
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007782"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="780af-102">IMetaDataEmit::SetPropertyProps 메서드</span><span class="sxs-lookup"><span data-stu-id="780af-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="780af-103">[DefineProperty 메서드에](imetadataemit-defineproperty-method.md)대 한 이전 호출로 정의 된 속성에 대 한 메타 데이터에 저장 된 기능을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="780af-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="780af-104">구문</span><span class="sxs-lookup"><span data-stu-id="780af-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertyProps (
    [in]  mdProperty      pr,
    [in]  DWORD           dwPropFlags,
    [in]  DWORD           dwCPlusTypeFlag,
    [in]  void const      *pValue,
    [in]  ULONG           cchValue,
    [in]  mdMethodDef     mdSetter,
    [in]  mdMethodDef     mdGetter,
    [in]  mdMethodDef     rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="780af-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="780af-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="780af-106">진행 변경할 속성의 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="780af-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="780af-107">진행 속성 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="780af-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="780af-108">진행 속성의 기본값 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="780af-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="780af-109">진행 속성의 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="780af-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="780af-110">진행 의 (유니코드) 문자 수입니다 `pValue` .</span><span class="sxs-lookup"><span data-stu-id="780af-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="780af-111">진행 속성 값을 설정 하는 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="780af-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="780af-112">진행 속성 값을 가져오는 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="780af-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="780af-113">진행 속성과 연결 된 다른 메서드의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="780af-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="780af-114">토큰을 사용 하 여이 배열을 종료 `mdTokenNil` 합니다.</span><span class="sxs-lookup"><span data-stu-id="780af-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="780af-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="780af-115">Requirements</span></span>  
 <span data-ttu-id="780af-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="780af-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="780af-117">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="780af-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="780af-118">**라이브러리:** Mscoree.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="780af-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="780af-119">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="780af-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="780af-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="780af-120">See also</span></span>

- [<span data-ttu-id="780af-121">IMetaDataEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="780af-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="780af-122">IMetaDataEmit2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="780af-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
