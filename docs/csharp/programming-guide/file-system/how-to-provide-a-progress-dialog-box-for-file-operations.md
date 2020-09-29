---
title: 파일 작업에 대한 진행률 대화 상자를 제공하는 방법 - C# 프로그래밍 가이드
description: CopyFile(String, String, UIOption) 메서드를 사용하여 파일 작업에 대한 진행률 대화 상자를 제공하는 방법을 알아봅니다.
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 5d16aeb3a5394ca250e4a5e26074db797c54216d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185888"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>파일 작업에 대한 진행률 대화 상자를 제공하는 방법(C# 프로그래밍 가이드)

<xref:Microsoft.VisualBasic?displayProperty=nameWithType> 네임스페이스의 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> 메서드를 사용하는 경우 Windows에서 파일 작업 진행률을 보여 주는 표준 대화 상자를 제공할 수 있습니다.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Visual Studio에서 참조를 추가하려면  
  
1. 메뉴 모음에서 **프로젝트**, **참조 추가**를 선택합니다.  
  
     **참조 관리자** 대화 상자가 나타납니다.  
  
2. **어셈블리** 영역에서 **프레임워크**가 선택되지 않은 경우 선택합니다.  
  
3. 이름 목록에서 **Microsoft.VisualBasic** 확인란을 선택한 다음 **확인** 단추를 선택하여 대화 상자를 닫습니다.  
  
## <a name="example"></a>예제  

 다음 코드는 `sourcePath`로 지정된 디렉터리를 `destinationPath`로 지정된 디렉터리에 복사합니다. 또한 이 코드는 작업이 완료되기까지 남은 예상 시간을 보여 주는 표준 대화 상자를 제공합니다.  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a>참조

- [파일 시스템 및 레지스트리(C# 프로그래밍 가이드)](./index.md)
