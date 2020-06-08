---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: d1307603ebc06b4eb4c3786f1cd2fb432c0cf636
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360464"
---
# <a name="-nologo-visual-basic"></a>-nologo(Visual Basic)
컴파일하는 동안 저작권 배너 및 정보 메시지를 표시하지 않습니다.  
  
## <a name="syntax"></a>구문  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a>설명  
 `-nologo`를 지정하면 컴파일러에 저작권 배너가 표시되지 않습니다. 기본적으로 `-nologo`은 적용되지 않습니다.  
  
> [!NOTE]
> Visual Studio 개발 환경 내에서는 `-nologo` 옵션을 사용할 수 없습니다. 명령줄에서 컴파일하는 경우에만 사용할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 코드는 `T2.vb`를 컴파일하고 저작권 배너를 표시하지 않습니다.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>참조

- [Visual Basic 명령줄 컴파일러](index.md)
- [샘플 컴파일 명령줄](sample-compilation-command-lines.md)
