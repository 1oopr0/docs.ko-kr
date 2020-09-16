---
title: 워크플로 솔루션에 서비스 참조 추가
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 1b4cc16d3bd85c28ac7267e88ae0a714620c9861
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557060"
---
# <a name="add-a-service-reference-in-a-workflow-solution"></a>워크플로 솔루션에 서비스 참조 추가

워크플로 애플리케이션에서 서비스 참조를 추가하는 작업은 일반적인 WCF 애플리케이션과 약간 다르게 작동합니다. **Add**  >  **서비스 참조** 추가를 선택 하 고 서비스에 대 한 URL을 지정 하면 메타 데이터가 다운로드 되 고 해당 wcf 서비스 또는 wcf 워크플로 서비스를 호출할 수 있는 사용자 지정 작업이 생성 됩니다. 서비스 참조를 추가한 후 생성된 활동이 빌드되도록 솔루션을 다시 빌드합니다. 솔루션을 다시 빌드한 후 생성된 활동이 워크플로 디자이너 도구 상자에 나타납니다. 이는 워크플로 솔루션 내에서 서비스 참조를 추가 하는 경우에만 작동 합니다. 다음 웹 캐스트는 다른 형식의 프로젝트에서 서비스 참조를 추가 하는 방법을 보여 줍니다. [웹 프로젝트의 워크플로에서 WCF 서비스를 호출](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)합니다.

동일한 작업 이름이 포함된 서비스에 대한 서비스 참조를 둘 이상 추가하면 문제가 발생합니다. 생성된 활동이 첫 번째 서비스 작업만 호출합니다. 이 문제를 해결 하려면 서비스 작업 이름을 다르게 변경 하거나 생성 된 각 작업 내에서 끝점 구성 이름을 변경 합니다.

## <a name="see-also"></a>참조

- [워크플로 서비스](workflow-services.md)
- [웹 프로젝트의 워크플로에서 WCF 서비스 호출](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
