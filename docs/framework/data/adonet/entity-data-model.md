---
title: 엔터티 데이터 모델
description: 엔터티 데이터 모델는 저장 된 폼에 관계 없이 데이터의 구조를 설명 합니다. 그러면 데이터를 여러 형식으로 저장 하 여 발생 하는 문제를 해결할 수 있습니다.
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: 9323f652d1cfa27d442d45bd01e546f3b81d7e80
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200773"
---
# <a name="entity-data-model"></a>엔터티 데이터 모델

EDM(엔터티 데이터 모델)은 저장된 폼에 관계없이 데이터 구조를 설명하는 개념 집합입니다. EDM은 Peter Chen이 1976년에 설명한 엔터티-관계 모델에서 차용하지만 엔터티-관계 모델을 기반으로 하여 기존의 사용을 확장합니다.  
  
 EDM은 데이터가 여러 폼에 저장되어 있을 경우 발생하는 문제를 다룹니다. 예를 들어, 관계형 데이터베이스, 텍스트 파일, XML 파일, 스프레드시트 및 보고서에 데이터를 저장하는 비즈니스를 고려해 보세요. 이 경우 데이터 모델링, 애플리케이션 디자인 및 데이터 액세스가 상당히 어려워집니다. 데이터 지향 애플리케이션을 디자인하는 경우 효율적인 데이터 액세스, 스토리지 및 확장성의 손실 없이 효율적이고 유지 관리 가능한 코드를 작성하는 것이 어려워집니다. 데이터가 관계형 구조이면 데이터 액세스, 스토리지 및 확장성이 매우 효율적이지만 효율적이고 유지 관리 가능한 코드를 작성하기가 더 어려워집니다. 데이터가 개체 구조이면 이러한 상쇄는 반대가 됩니다. 효율적인 데이터 액세스, 스토리지 및 확장성이 저하되면 효율적이고 유지 관리 가능한 코드를 작성하기가 더 쉽습니다. 이러한 상쇄 간에 적절한 균형을 찾을 수 있다고 해도 한 폼에서 다른 폼으로 데이터를 이동하는 경우 새로운 문제가 발생합니다. 엔터티 데이터 모델은 스토리지 스키마에 독립적인 엔터티 및 관계를 기준으로 데이터 구조를 설명하여 이러한 문제를 다룹니다. 이렇게 하면 저장된 데이터 폼이 애플리케이션 디자인 및 개발과 관련이 없어집니다. 그리고 저장된 폼이 아니라 엔터티와 관계가 애플리케이션에서 사용되는 데이터 구조를 설명하기 때문에 애플리케이션 개발에 따라 엔터티와 관계도 개발될 수 있습니다.  
  
 `conceptual model`은 엔터티 및 관계로서의 특정 데이터 구조 표현이며, 일반적으로 EDM의 개념을 구현하는 DSL(Domain-Specific Language)에서 정의됩니다. [CSDL (개념 스키마 정의 언어)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) 은 이러한 도메인별 언어의 한 예입니다. 개념적 모델에서 설명되는 엔터티와 관계를 애플리케이션의 개체 및 연결 추상화로 간주할 수 있습니다. 이렇게 하면 개발자가 스토리지 스키마에 대해 염려하지 않고 개념적 모델에 집중할 수 있으며 효율성과 유지 관리 기능을 고려하여 코드를 작성할 수 있습니다. 한편, 스토리지 스키마 디자이너는 효율적인 데이터 액세스, 저장 및 확장성에 집중할 수 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  

 이 단원의 항목에서는 엔터티 데이터 모델의 개념에 대해 설명합니다. EDM을 구현하는 모든 DSL에는 여기에 설명된 개념이 포함되어야 합니다. [ADO.NET Entity Framework](./ef/index.md) 는 CSDL을 사용 하 여 개념적 모델을 정의 합니다. 자세한 내용은 [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)을 참조하십시오.  
  
 [엔터티 데이터 모델의 주요 개념](entity-data-model-key-concepts.md)  
  
 [엔터티 데이터 모델: 네임스페이스](entity-data-model-namespaces.md)  
  
 [엔터티 데이터 모델: 기본 데이터 형식](entity-data-model-primitive-data-types.md)  
  
 [엔터티 데이터 모델: 상속](entity-data-model-inheritance.md)  
  
 [연결 End](association-end.md)  
  
 [연결 End 복합성](association-end-multiplicity.md)  
  
 [연결 집합(association set)](association-set.md)  
  
 [연결 집합 End](association-set-end.md)  
  
 [연결 형식](association-type.md)  
  
 [복합 형식](complex-type.md)  
  
 [엔터티 컨테이너(entity container)](entity-container.md)  
  
 [엔터티 키](entity-key.md)  
  
 [엔터티 집합](entity-set.md)  
  
 [엔터티 형식](entity-type.md)  
  
 [패싯에](facet.md)  
  
 [외래 키 속성](foreign-key-property.md)  
  
 [모델 선언 함수](model-declared-function.md)  
  
 [모델 정의 함수](model-defined-function.md)  
  
 [탐색 속성(navigation property)](navigation-property.md)  
  
 [property](property.md)  
  
 [참조 무결성 제약 조건](referential-integrity-constraint.md)  
  
## <a name="see-also"></a>참고 항목

- [ADO.NET 엔터티 데이터 모델 도구](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [.edmx 파일 개요](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [CSDL 사양](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
