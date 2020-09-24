---
title: = (같음) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 31299670d9f47ed7672b980a3415b8d214463b8e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148089"
---
# <a name="-equals-entity-sql"></a>= (같음) (Entity SQL)

두 식이 같은지 비교합니다.  
  
## <a name="syntax"></a>구문  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a>인수  

 `expression`  
 모든 유효한 식입니다. 두 식은 모두 암시적으로 변환 가능한 데이터 형식이어야 합니다.  
  
## <a name="result-types"></a>결과 형식  

 왼쪽 식의 값이 오른쪽 식의 값과 같으면`true` 이고, 그렇지 않으면 `false`입니다.  
  
## <a name="remarks"></a>설명  

 == 연산자는 = 연산자와 동일합니다.  
  
## <a name="example"></a>예제  

 다음 Entity SQL 쿼리에서는 = 비교 연산자를 사용하여 두 식이 같은지 비교합니다. 쿼리는 AdventureWorks Sales 모델을 기반으로 합니다. 이 쿼리를 컴파일하고 실행하려면 다음 단계를 수행하세요.  
  
1. [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)의 절차를 따릅니다.  
  
2. 다음 쿼리를 `ExecuteStructuralTypeQuery` 메서드에 인수로 전달합니다.  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a>참고 항목

- [엔터티 SQL 참조](entity-sql-reference.md)
