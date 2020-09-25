---
title: 중첩된 스키마 요소 사이에 암시적 관계 매핑
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 32f8bf67242143098717b47c3b7aa175317ba274
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201319"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="f65e8-102">중첩된 스키마 요소 사이에 암시적 관계 매핑</span><span class="sxs-lookup"><span data-stu-id="f65e8-102">Map Implicit Relations Between Nested Schema Elements</span></span>

<span data-ttu-id="f65e8-103">XSD(XML 스키마 정의 언어) 스키마에는 다른 형식 내부에 중첩된 복합 형식이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="f65e8-104">이 경우 매핑 프로세스에서는 기본 매핑을 적용하며 <xref:System.Data.DataSet>에 다음 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="f65e8-105">각 복합 형식(부모 및 자식)에 대해 하나의 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="f65e8-106">부모에 unique 제약 조건이 없는 경우 *tablename*이라는 테이블 정의 당 추가 기본 키 열이 하나 있습니다. 여기서 *tablename* 은 부모 테이블의 이름 _Id 합니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="f65e8-107">**IsPrimaryKey** 속성을 **True**로 설정 하 여 추가 열을 기본 키로 식별 하는 부모 테이블의 primary key 제약 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="f65e8-108">제약 조건은 Constraint\#으로 명명되며, 여기서 \#은 1, 2, 3 등을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="f65e8-109">예를 들어, 첫 번째 제약 조건의 기본 이름은 Constraint1입니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="f65e8-110">추가 열을 부모 테이블의 기본 키를 참조하는 외래 키로 식별하는 외래 키 제약 조건을 자식 테이블에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="f65e8-111">제약 조건의 이름은 *ParentTable_ChildTable* 여기서 *parenttable* 은 부모 테이블의 이름이 고 *childtable* 은 자식 테이블의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="f65e8-112">부모와 자식 테이블 간의 데이터 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="f65e8-113">다음 예제에서는 **Orderdetail** 이 **Order**의 자식 요소인 스키마를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
   <xs:complexType>  
     <xs:choice maxOccurs="unbounded">  
       <xs:element name="Order">  
         <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="f65e8-114">XML 스키마 매핑 프로세스는 **데이터 집합**에 다음을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="f65e8-115">**Order** 및 **orderdetail** 테이블</span><span class="sxs-lookup"><span data-stu-id="f65e8-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="f65e8-116">**Order** 테이블에 대 한 unique 제약 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="f65e8-117">**IsPrimaryKey** 속성은 **True**로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="f65e8-118">**Orderdetail** 테이블의 foreign key 제약 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- <span data-ttu-id="f65e8-119">**Order** 및 **orderdetail** 테이블 간의 관계입니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="f65e8-120">**Order** 및 **orderdetail** 요소가 스키마에 중첩 되어 있으므로이 관계의 **Nested** 속성은 **True** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f65e8-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: Order_Id
    ChildTable: OrderDetail  
    ChildColumns: Order_Id
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f65e8-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f65e8-121">See also</span></span>

- [<span data-ttu-id="f65e8-122">XSD(XML 스키마)에서 데이터 세트 관계 생성</span><span class="sxs-lookup"><span data-stu-id="f65e8-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="f65e8-123">데이터 세트 제약 조건에 XSD(XML 스키마) 제약 조건 매핑</span><span class="sxs-lookup"><span data-stu-id="f65e8-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="f65e8-124">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="f65e8-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
