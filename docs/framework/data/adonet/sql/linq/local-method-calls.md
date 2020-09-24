---
title: 로컬 메서드 호출
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: 25aded1aa961e182e8d2d472fca4c5a84b501af1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166172"
---
# <a name="local-method-calls"></a>로컬 메서드 호출

로컬 메서드 호출은 개체 모델 내에서 실행되는 작업입니다. 원격 메서드 호출은 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서 SQL로 변환하고 실행을 위해 데이터베이스 엔진으로 전송하는 작업입니다. 로컬 메서드 호출은 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서 호출을 SQL로 변환할 수 없는 경우 필요합니다. 그렇지 않으면 <xref:System.InvalidOperationException>이 throw됩니다.  
  
## <a name="example-1"></a>예 1  

 다음 예제에서는 `Order` 클래스를 Northwind 샘플 데이터베이스의 Orders 테이블에 매핑합니다. 로컬 인스턴스 메서드가 해당 클래스에 추가됩니다.  
  
 쿼리 1에서 `Order` 클래스의 생성자는 로컬로 실행됩니다. 쿼리 2에서 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]이 `LocalInstanceMethod()`를 SQL로 변환을 시도하면 해당 시도는 실패하고 <xref:System.InvalidOperationException> 예외가 throw됩니다. 그러나 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서 로컬 메서드 호출을 지원하기 때문에 쿼리 2에서는 예외를 throw하지 않습니다.  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>참고 항목

- [배경 정보](background-information.md)
