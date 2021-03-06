---
title: Null 값 처리
description: SQL Server에 대 한 .NET Framework Data Provider에서 null을 처리 하는 방법과 null 및 SqlBoolean, 3 값 논리 및 null 값 할당에 대해 읽어 보십시오.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 2ed2a88b91f06bb02c72d3e310ae09d58637205f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197471"
---
# <a name="handling-null-values"></a>Null 값 처리

관계형 데이터베이스에서 null 값은 열 값을 알 수 없거나 값이 누락된 경우에 사용됩니다. Null은 빈 문자열(문자 또는 날짜/시간 데이터 형식의 경우)도 아니고 0 값(숫자 데이터 형식의 경우)도 아닙니다. ANSI SQL-92 사양에서는 모든 null이 일관되게 처리되도록 null이 모든 데이터 형식에 대해 동일해야 함을 명시합니다. <xref:System.Data.SqlTypes> 네임스페이스는 <xref:System.Data.SqlTypes.INullable> 인터페이스를 구현하여 null 의미 체계를 제공합니다. <xref:System.Data.SqlTypes>의 각 데이터 형식에는 해당 데이터 형식의 인스턴스에 할당할 수 있는 고유한 `IsNull` 속성과 `Null` 값이 있습니다.  
  
> [!NOTE]
> .NET Framework 버전 2.0에서는 프로그래머가 값 형식을 확장 하 여 기본 형식의 모든 값을 나타내도록 허용 하는 nullable 값 형식에 대 한 지원이 도입 되었습니다. 이러한 CLR nullable 값 형식은 구조체의 인스턴스를 나타냅니다 <xref:System.Nullable> . 이 기능은 값 형식이 boxed 및 unboxed인 경우에 특히 유용하며 개체 유형과의 호환성을 향상시킵니다. ANSI SQL null은 `null` 참조 (또는 Visual Basic)와 동일한 방식으로 동작 하지 않으므로 CLR nullable 값 형식은 데이터베이스 null의 저장에 적합 하지 않습니다 `Nothing` . 데이터베이스 ANSI SQL null 값에 대한 작업을 수행하려면 <xref:System.Data.SqlTypes> 대신 <xref:System.Nullable> null을 사용합니다. Visual Basic에서 CLR 값 nullable 형식을 사용 하는 방법에 대 한 자세한 내용은 [Nullable 값 형식](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)및 c #의 경우 [nullable 값 형식](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)을 참조 하세요.  
  
## <a name="nulls-and-three-valued-logic"></a>Null과 3중값 논리  

 열 정의에 null 값을 허용하면 애플리케이션에 값이 3치 논리가 도입됩니다. 비교는 다음 세 가지 조건 중 하나로 평가될 수 있습니다.  
  
- True  
  
- False  
  
- 알 수 없음  
  
 Null은 unknown으로 간주되기 때문에 서로 비교되는 두 null 값은 동일한 것으로 간주되지 않습니다. 산술 연산자를 사용하는 식에서 피연산자 중 하나라도 null이면 결과도 null입니다.  
  
## <a name="nulls-and-sqlboolean"></a>Null 및 SqlBoolean  

 <xref:System.Data.SqlTypes> 간 비교는 <xref:System.Data.SqlTypes.SqlBoolean>을 반환합니다. 각 `IsNull`에 대한 `SqlType` 함수는 <xref:System.Data.SqlTypes.SqlBoolean>을 반환하며 null 값을 확인하는 데 사용할 수 있습니다. 다음 진리표에서는 null 값이 있는 경우 AND, OR 및 NOT 연산자가 작동하는 방식을 보여 줍니다. (T=true, F=false, U=unknown 또는 null)  
  
 ![진리표](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>ANSI_NULLS 옵션 이해  

 <xref:System.Data.SqlTypes>는 SQL Server에서 ANSI_NULLS 옵션이 on으로 설정된 경우와 동일한 의미 체계를 제공합니다. 모든 산술 연산자 (+,-, \* ,/,%), 비트 연산자 (~, &, \| ) 및 대부분의 함수는 속성을 제외 하 고 피연산자 또는 인수가 null 인 경우 null을 반환 `IsNull` 합니다.  
  
 ANSI SQL-92 표준에서는 WHERE 절에서 *columnName* = NULL을 지원하지 않습니다. SQL Server에서 ANSI_NULLS 옵션은 데이터베이스의 기본 null 허용 여부와 null 값에 대한 비교 평가를 모두 제어합니다. ANSI_NULLS이 설정된 경우(기본값) null 값을 테스트할 때 식에서 IS NULL 연산자를 사용해야 합니다. 예를 들어 ANSI_NULLS가 on이면 다음 비교 결과는 항상 unknown이 됩니다.  
  
```sql
colname > NULL  
```  
  
 Null 값을 포함하는 변수와 비교하면 unknown도 생성됩니다.  
  
```sql
colname > @MyVariable  
```  
  
 IS NULL 또는 IS NOT NULL 조건자를 사용하여 null 값을 테스트하세요. 그렇게 하면 WHERE 절이 복잡해질 수 있습니다. 예를 들어 AdventureWorks Customer 테이블의 TerritoryID 열은 null 값을 허용합니다. SELECT 문이 다른 값 이외에 Null 값을 테스트하는 경우 IS NULL 조건자가 포함되어야 합니다.  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 SQL Server에서 ANSI_NULLS를 off로 설정한 경우 같음 연산자를 사용하여 null과 비교하는 식을 만들 수 있습니다. 그러나 다른 연결이 해당 연결에 null 옵션을 설정하는 것을 방지할 수 없습니다. 연결에 대한 ANSI_NULLS 설정에 관계없이 null 값을 테스트하기 위해 IS NULL을 사용하는 것은 항상 작동합니다.  
  
 `DataSet`에서 null 값을 처리하기 위해 항상 ANSI SQL-92 표준을 따르는 <xref:System.Data.SqlTypes>에서는 ANSI_NULLS를 off로 설정할 수 없습니다.  
  
## <a name="assigning-null-values"></a>Null 값 할당  

 Null 값은 특수하며, 저장 및 할당 의미 체계가 다양한 형식 시스템 및 스토리지 시스템에서 서로 다릅니다. `Dataset`는 다양한 형식 및 스토리지 시스템에서 사용하도록 설계되었습니다.  
  
 이 섹션에서는 다양한 형식 시스템에서 <xref:System.Data.DataColumn>의 <xref:System.Data.DataRow>에 null 값을 할당하기 위한 null 의미 체계에 대해 설명합니다.  
  
 `DBNull.Value`  
 이 할당은 모든 형식의 `DataColumn`에 유효합니다. 형식이 `INullable`를 구현하는 경우 `DBNull.Value`는 적절한 강력한 형식의 Null 값으로 강제 변환됩니다.  
  
 `SqlType.Null`  
 모든 <xref:System.Data.SqlTypes> 데이터 형식에서 `INullable`을 구현합니다. 암시적 캐스트 연산자를 사용하여 강력한 형식의 null 값을 열의 데이터 형식으로 변환할 수 있는 경우 할당이 통과합니다. 그렇지 않으면 잘못된 캐스트 예외가 throw됩니다.  
  
 `null`  
 'Null'이 지정된 `DataColumn` 데이터 형식에 올바른 값이면 `DbNull.Value` 형식(`Null`)과 연결된 적절한 `INullable` 또는 `SqlType.Null`으로 강제 변환됩니다.  
  
 `derivedUdt.Null`  
 UDT 열의 경우 null은 항상 `DataColumn`과 연결된 형식에 따라 저장됩니다. `DataColumn`과 연결된 UDT가 `INullable`를 구현하지 않지만 하위 클래스는 구현하는 경우를 생각해 보겠습니다. 이 경우 파생 클래스와 연결된 강력한 형식의 null 값이 할당되면 해당 값은 형식화되지 않은 `DbNull.Value`로 저장됩니다. Null 저장소는 항상 DataColumn의 데이터 형식과 일치하기 때문입니다.  
  
> [!NOTE]
> `Nullable<T>` 또는 <xref:System.Nullable> 구조체는 현재 `DataSet`에서 지원되지 않습니다.  
  
### <a name="multiple-column-row-assignment"></a>여러 열(행) 할당  

 `DataTable.Add`, `DataTable.LoadDataRow`또는 행에 매핑되는 <xref:System.Data.DataRow.ItemArray%2A>를 수락하는 다른 API는 'null'을 DataColumn의 기본값에 매핑합니다. 배열의 개체에 `DbNull.Value` 또는 강력한 형식의 상응하는 값이 포함된 경우 위에 설명한 것과 동일한 규칙이 적용됩니다.  
  
 또한 `DataRow.["columnName"]` null 할당 인스턴스에 다음 규칙이 적용됩니다.  
  
1. 강력한 형식의 null 값이 적절한 강력한 형식의 null 열을 제외한 모든 열에서 기본 *default* 값은 `DbNull.Value`입니다.  
  
2. "xsi:nil"에서처럼 XML 파일로 직렬화하는 동안에는 null 값이 작성되지 않습니다.  
  
3. 기본값을 포함하여 null이 아닌 모든 값은 항상 XML로 직렬화하는 동안 작성됩니다. 이는 null 값(xsi: nil)이 명시적이고 기본값이 암시적인(XML에 없는 경우 유효성 검사 파서가 연결된 XSD 스키마에서 가져올 수 있음) XSD/XML 의미 체계와는 다릅니다. `DataTable`에서는 그 반대입니다. Null 값은 암시적이고 기본값은 명시적입니다.  
  
4. XML 입력에서 읽은 행에 대해 누락된 모든 열 값에는 NULL이 할당됩니다. <xref:System.Data.DataTable.NewRow%2A> 또는 유사한 메서드를 사용하여 만든 행에는 DataColumn의 기본값이 할당됩니다.  
  
5. <xref:System.Data.DataRow.IsNull%2A> 메서드는 `true` 및 `DbNull.Value`에 대해 `INullable.Null`를 반환합니다.  
  
## <a name="assigning-null-values"></a>Null 값 할당  

 <xref:System.Data.SqlTypes> 인스턴스의 기본값은 null입니다.  
  
 <xref:System.Data.SqlTypes>의 null은 형식에 따라 달라지며 `DbNull`과 같은 단일 값으로 나타낼 수 없습니다. `IsNull` 속성을 사용하여 null을 확인합니다.  
  
 다음 코드 예제와 같이 <xref:System.Data.DataColumn>에 null 값을 할당할 수 있습니다. 예외를 트리거하지 않고 `SqlTypes` 변수에 null 값을 직접 할당할 수 있습니다.  
  
### <a name="example"></a>예제  

 다음 코드 예제에서는 <xref:System.Data.DataTable> 및 <xref:System.Data.SqlTypes.SqlInt32>으로 정의된 두 개의 열이 있는 <xref:System.Data.SqlTypes.SqlString>을 만듭니다. 이 코드는 알려진 값의 행과 null 값의 행을 하나씩 추가하고 <xref:System.Data.DataTable>을 반복하여 변수에 값을 할당하고 콘솔 창에 출력을 표시합니다.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 이 예제에서 표시되는 결과는 다음과 같습니다.  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>SqlTypes 및 CLR 형식을 사용하여 Null 값 비교  

 Null 값을 비교할 때 `Equals` 메서드가 CLR 형식에서 작동하는 방식과 비교하여 <xref:System.Data.SqlTypes>에서 null 값을 평가하는 방법 간의 차이점을 이해하는 것이 중요합니다. 모든 <xref:System.Data.SqlTypes>`Equals` 메서드는 null 값을 평가하는 데 데이터베이스 의미 체계를 사용합니다. 두 값 중 하나 또는 둘 다 null이면 비교가 null을 생성합니다. 반면에 두 `Equals`에서 CLR <xref:System.Data.SqlTypes> 메서드를 사용하면 둘 다 null인 경우 true가 생성됩니다. 이는 CLR `String.Equals` 메서드와 같은 인스턴스 메서드를 사용하는 경우와 정적/공유 메서드 `SqlString.Equals`를 사용하는 경우의 차이점을 반영합니다.  
  
 다음 예제에서는 각각에 null 값 쌍이 전달된 후 빈 문자열 쌍이 전달될 때 `SqlString.Equals` 메서드와 `String.Equals` 메서드 간의 결과 차이를 보여 줍니다.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 이 코드는 다음 출력을 생성합니다.  
  
```output
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True
```  
  
## <a name="see-also"></a>참고 항목

- [SQL Server 데이터 형식 및 ADO.NET](sql-server-data-types.md)
- [ADO.NET 개요](../ado-net-overview.md)
