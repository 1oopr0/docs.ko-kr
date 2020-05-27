---
title: CorValidatorModuleType 열거형
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
ms.openlocfilehash: 038e2ec20e5fd01edf9835080e0f7a15ec862fd9
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008939"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="7af1c-102">CorValidatorModuleType 열거형</span><span class="sxs-lookup"><span data-stu-id="7af1c-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="7af1c-103">모듈의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7af1c-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7af1c-104">구문</span><span class="sxs-lookup"><span data-stu-id="7af1c-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a><span data-ttu-id="7af1c-105">멤버</span><span class="sxs-lookup"><span data-stu-id="7af1c-105">Members</span></span>  
  
|<span data-ttu-id="7af1c-106">멤버</span><span class="sxs-lookup"><span data-stu-id="7af1c-106">Member</span></span>|<span data-ttu-id="7af1c-107">설명</span><span class="sxs-lookup"><span data-stu-id="7af1c-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="7af1c-108">모듈의 형식이 잘못 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7af1c-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="7af1c-109">열거형의 최소값 `CorValidatorModuleType` 입니다.</span><span class="sxs-lookup"><span data-stu-id="7af1c-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="7af1c-110">모듈은 PE (이식 가능한 실행) 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="7af1c-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="7af1c-111">모듈은 .obj 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="7af1c-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="7af1c-112">이 모듈은 편집 하며 계속 하기 디버거 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="7af1c-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="7af1c-113">모듈은 증분 방식으로 작성 된 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="7af1c-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="7af1c-114">열거형의 최대값 `CorValidatorModuleType` 입니다.</span><span class="sxs-lookup"><span data-stu-id="7af1c-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7af1c-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7af1c-115">Requirements</span></span>  
 <span data-ttu-id="7af1c-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7af1c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7af1c-117">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="7af1c-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7af1c-118">**라이브러리:** Mscoree.dll에 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7af1c-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7af1c-119">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7af1c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7af1c-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7af1c-120">See also</span></span>

- [<span data-ttu-id="7af1c-121">메타데이터 열거형</span><span class="sxs-lookup"><span data-stu-id="7af1c-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
