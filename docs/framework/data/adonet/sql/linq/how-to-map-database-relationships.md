---
title: '방법: 데이터베이스 관계 매핑'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: 2f612877f5e7da6442c242aa0d56d811c0aa7cf8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166458"
---
# <a name="how-to-map-database-relationships"></a><span data-ttu-id="2e9e8-102">방법: 데이터베이스 관계 매핑</span><span class="sxs-lookup"><span data-stu-id="2e9e8-102">How to: Map Database Relationships</span></span>

<span data-ttu-id="2e9e8-103">항상 동일하게 유지되는 모든 데이터 관계를 엔터티 클래스에서 속성 참조로 인코딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-103">You can encode as property references in your entity class any data relationships that will always be the same.</span></span> <span data-ttu-id="2e9e8-104">예를 들어 Northwind 샘플 데이터베이스에서는 일반적으로 고객이 주문을 하기 때문에 고객과 고객 주문 간의 관계가 항상 모델에 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-104">In the Northwind sample database, for example, because customers typically place orders, there is always a relationship in the model between customers and their orders.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="2e9e8-105">은 이러한 관계를 나타내는 데 도움이 되도록 <xref:System.Data.Linq.Mapping.AssociationAttribute> 특성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-105">defines an <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute to help represent such relationships.</span></span> <span data-ttu-id="2e9e8-106">이 특성은 데이터베이스에서의 외래 키 관계가 무엇인지 나타내기 위해 <xref:System.Data.Linq.EntitySet%601> 및 <xref:System.Data.Linq.EntityRef%601> 형식과 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-106">This attribute is used together with the <xref:System.Data.Linq.EntitySet%601> and <xref:System.Data.Linq.EntityRef%601> types to represent what would be a foreign key relationship in a database.</span></span> <span data-ttu-id="2e9e8-107">자세한 내용은 [특성 기반 매핑의](attribute-based-mapping.md)Association 특성 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-107">For more information, see the Association Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e9e8-108">AssociationAttribute 및 ColumnAttribute Storage 속성 값은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-108">AssociationAttribute and ColumnAttribute Storage property values are case sensitive.</span></span> <span data-ttu-id="2e9e8-109">예를 들어 AssociationAttribute.Storage 속성의 특성에 사용하는 값은 코드의 다른 곳에서 사용하는 해당 속성 이름과 대/소문자가 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-109">For example, ensure that values used in the attribute for the AssociationAttribute.Storage property match the case for the corresponding property names used elsewhere in the code.</span></span> <span data-ttu-id="2e9e8-110">이 일반적으로 대/소문자 구분, Visual Basic을 포함 하지 않는 이더라도 모든.NET 프로그래밍 언어에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-110">This applies to all .NET programming languages, even those which are not typically case sensitive, including Visual Basic.</span></span> <span data-ttu-id="2e9e8-111">Storage 속성에 대한 자세한 내용은 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-111">For more information about the Storage property, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="2e9e8-112">이 항목의 뒷부분에 나오는 예제처럼 대부분의 관계는 일대다입니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-112">Most relationships are one-to-many, as in the example later in this topic.</span></span> <span data-ttu-id="2e9e8-113">다음과 같이 일대일 및 다대다 관계를 나타낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-113">You can also represent one-to-one and many-to-many relationships as follows:</span></span>  
  
- <span data-ttu-id="2e9e8-114">일대일: 양쪽 모두에 <xref:System.Data.Linq.EntitySet%601>을 포함하여 이 종류의 관계를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-114">One-to-one: Represent this kind of relationship by including <xref:System.Data.Linq.EntitySet%601> on both sides.</span></span>  
  
     <span data-ttu-id="2e9e8-115">예를 들어, `Customer` - `SecurityCode` 고객의 보안 코드를 테이블에서 찾을 수 없으며 권한 있는 사용자 `Customer` 만 액세스할 수 있도록 만든 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-115">For example, consider a `Customer`-`SecurityCode` relationship, created so that the customer's security code will not be found in the `Customer` table and can be accessed only by authorized persons.</span></span>  
  
- <span data-ttu-id="2e9e8-116">다대다: 다 대 다 관계에서 링크 테이블의 기본 키 ( *접합* 테이블)는 다른 두 테이블의 복합 외래 키로 구성 되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-116">Many-to-many: In many-to-many relationships, the primary key of the link table (also named the *junction* table) is often formed by a composite of the foreign keys from the other two tables.</span></span>  
  
     <span data-ttu-id="2e9e8-117">예를 들어 `Employee` - `Project` 링크 테이블을 사용 하 여 형성 된 다 대 다 관계를 생각해 보겠습니다 `EmployeeProject` .</span><span class="sxs-lookup"><span data-stu-id="2e9e8-117">For example, consider an `Employee`-`Project` many-to-many relationship formed by using link table `EmployeeProject`.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="2e9e8-118">에서는 `Employee`, `Project` 및 `EmployeeProject`라는 세 개의 클래스를 사용하여 이러한 관계를 모델링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-118">requires that such a relationship be modeled by using three classes: `Employee`, `Project`, and `EmployeeProject`.</span></span> <span data-ttu-id="2e9e8-119">이 경우 `Employee` 및 `Project` 간의 관계를 변경하려면 기본 키 `EmployeeProject`의 업데이트가 필요한 것처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-119">In this case, changing the relationship between an `Employee` and a `Project` can appear to require an update of the primary key `EmployeeProject`.</span></span> <span data-ttu-id="2e9e8-120">그러나 이 상황을 모델링하는 최선의 방법은 기존 `EmployeeProject`를 삭제하고 새 `EmployeeProject`를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-120">However, this situation is best modeled as deleting an existing `EmployeeProject` and the creating a new `EmployeeProject`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2e9e8-121">관계형 데이터베이스에서 관계는 일반적으로 다른 테이블의 기본 키를 참조하는 외래 키 값으로 모델링됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-121">Relationships in relational databases are typically modeled as foreign key values that refer to primary keys in other tables.</span></span> <span data-ttu-id="2e9e8-122">두 테이블 간에 이동 하려면 관계형 *조인* 작업을 사용 하 여 두 테이블을 명시적으로 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-122">To navigate between them you explicitly associate the two tables by using a relational *join* operation.</span></span>  
    >
    >  <span data-ttu-id="2e9e8-123">반면의 개체는 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *점* 표기법을 사용 하 여 탐색 하는 참조의 컬렉션 또는 속성 참조를 사용 하 여 서로를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-123">Objects in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], on the other hand, refer to each other by using property references or collections of references that you navigate by using *dot* notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e9e8-124">예제</span><span class="sxs-lookup"><span data-stu-id="2e9e8-124">Example</span></span>  

 <span data-ttu-id="2e9e8-125">다음 일대다 예제에서 `Customer` 클래스는 고객과 고객의 주문 사이의 관계를 선언하는 속성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-125">In the following one-to-many example, the `Customer` class has a property that declares the relationship between customers and their orders.</span></span>  <span data-ttu-id="2e9e8-126">`Orders` 속성은 <xref:System.Data.Linq.EntitySet%601> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-126">The `Orders` property is of type <xref:System.Data.Linq.EntitySet%601>.</span></span> <span data-ttu-id="2e9e8-127">이 형식은 이 관계가 일대다(한 명의 고객과 여러 개의 주문)라는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-127">This type signifies that this relationship is one-to-many (one customer to many orders).</span></span> <span data-ttu-id="2e9e8-128"><xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> 속성은 이 속성과 비교할 관련 클래스의 속성 이름을 지정함으로써 이 연결이 이루어지는 방법을 설명하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-128">The <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> property is used to describe how this association is accomplished, namely, by specifying the name of the property in the related class to be compared with this one.</span></span> <span data-ttu-id="2e9e8-129">이 예에서는 `CustomerID` 데이터베이스 *조인이* 해당 열 값을 비교 하는 것 처럼 속성을 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-129">In this example, the `CustomerID` property is compared, just as a database *join* would compare that column value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e9e8-130">Visual Studio를 사용 하는 경우 개체 관계형 디자이너를 사용 하 여 클래스 간의 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-130">If you are using Visual Studio, you can use the Object Relational Designer to create an association between classes.</span></span>  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="2e9e8-131">예제</span><span class="sxs-lookup"><span data-stu-id="2e9e8-131">Example</span></span>  

 <span data-ttu-id="2e9e8-132">또한 이 상황을 반대로 적용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-132">You can also reverse the situation.</span></span> <span data-ttu-id="2e9e8-133">`Customer` 클래스를 사용하여 고객과 주문 간의 연결을 설명하는 대신에 `Order` 클래스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-133">Instead of using the `Customer` class to describe the association between customers and orders, you can use the `Order` class.</span></span> <span data-ttu-id="2e9e8-134">다음 코드 예제와 같이 `Order` 클래스는 <xref:System.Data.Linq.EntityRef%601> 형식을 사용하여 고객에 대한 관계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-134">The `Order` class uses the <xref:System.Data.Linq.EntityRef%601> type to describe the relationship back to the customer, as in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e9e8-135"><xref:System.Data.Linq.EntityRef%601>클래스는 *지연 된 로드*를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e9e8-135">The <xref:System.Data.Linq.EntityRef%601> class supports *deferred loading*.</span></span> <span data-ttu-id="2e9e8-136">자세한 내용은 [지연 된 로드 및 즉시 로드](deferred-versus-immediate-loading.md)를 *참조 하세요* .</span><span class="sxs-lookup"><span data-stu-id="2e9e8-136">For more information, *see* [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="2e9e8-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e9e8-137">See also</span></span>

- [<span data-ttu-id="2e9e8-138">방법: 코드 편집기를 사용하여 엔터티 클래스 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="2e9e8-138">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="2e9e8-139">LINQ to SQL 개체 모델</span><span class="sxs-lookup"><span data-stu-id="2e9e8-139">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
