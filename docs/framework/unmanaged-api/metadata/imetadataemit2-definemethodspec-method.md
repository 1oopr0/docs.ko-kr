---
title: IMetaDataEmit2::DefineMethodSpec 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
ms.openlocfilehash: 8e067dc4943e6847177c13a683703e3a649a49e4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503824"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="bf8fd-102">IMetaDataEmit2::DefineMethodSpec 메서드</span><span class="sxs-lookup"><span data-stu-id="bf8fd-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="bf8fd-103">메서드의 제네릭 인스턴스를 만들고 해당 정의에 대 한 토큰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf8fd-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf8fd-104">구문</span><span class="sxs-lookup"><span data-stu-id="bf8fd-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf8fd-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="bf8fd-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="bf8fd-106">진행 제네릭 인스턴스를 만들 메서드의 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="bf8fd-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="bf8fd-107">토큰은 또는 형식 이어야 합니다 `mdMethodDef` `mdMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="bf8fd-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="bf8fd-108">진행 메서드의 이진 COM + 시그니처에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="bf8fd-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="bf8fd-109">진행 의 크기 (바이트)입니다 `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="bf8fd-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="bf8fd-110">제한이 메서드의 메타 데이터 서명 정의에 대 한 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="bf8fd-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf8fd-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="bf8fd-111">Requirements</span></span>  
 <span data-ttu-id="bf8fd-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf8fd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf8fd-113">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="bf8fd-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf8fd-114">**라이브러리:** Mscoree.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf8fd-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bf8fd-115">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf8fd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf8fd-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf8fd-116">See also</span></span>

- [<span data-ttu-id="bf8fd-117">IMetaDataEmit2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="bf8fd-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="bf8fd-118">IMetaDataEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="bf8fd-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
