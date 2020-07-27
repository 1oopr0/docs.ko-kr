---
title: '방법: DataGrid 컨트롤에서 데이터 그룹화, 정렬 및 필터링'
description: 뷰에서 데이터 그룹화, 정렬 및 필터링을 지 원하는 CollectionView에 Windows Presentation Foundation DataGrid 컨트롤을 바인딩하는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 072e5a104a91faa40bb54f2a3fc4ed6188e1112e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167665"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="fc3de-103">방법: DataGrid 컨트롤에서 데이터 그룹화, 정렬 및 필터링</span><span class="sxs-lookup"><span data-stu-id="fc3de-103">How to: Group, sort, and filter data in the DataGrid control</span></span>

<span data-ttu-id="fc3de-104"><xref:System.Windows.Controls.DataGrid>데이터를 그룹화, 정렬 및 필터링 하 여 다양 한 방법으로의 데이터를 보는 것이 유용한 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-104">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="fc3de-105">에서 데이터를 그룹화, 정렬 및 필터링 하려면 <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.CollectionView> 이러한 함수를 지 원하는에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-105">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="fc3de-106">그런 다음 <xref:System.Windows.Data.CollectionView> 기본 원본 데이터에 영향을 주지 않고의 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-106">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="fc3de-107">컬렉션 뷰의 변경 내용은 <xref:System.Windows.Controls.DataGrid> UI (사용자 인터페이스)에 반영 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-107">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>

<span data-ttu-id="fc3de-108"><xref:System.Windows.Data.CollectionView>클래스는 인터페이스를 구현 하는 데이터 소스에 대 한 그룹화 및 정렬 기능을 제공 합니다 <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-108">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="fc3de-109"><xref:System.Windows.Data.CollectionViewSource>클래스를 사용 하면 XAML에서의 속성을 설정할 수 있습니다 <xref:System.Windows.Data.CollectionView> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-109">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>

<span data-ttu-id="fc3de-110">이 예제에서는 개체의 컬렉션을에 `Task` 바인딩합니다 <xref:System.Windows.Data.CollectionViewSource> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-110">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="fc3de-111">는의 <xref:System.Windows.Data.CollectionViewSource> 로 사용 됩니다 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-111">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="fc3de-112">그룹화, 정렬 및 필터링은에서 수행 되며 <xref:System.Windows.Data.CollectionViewSource> UI에 표시 됩니다 <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-112">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="fc3de-113">![DataGrid의 그룹화 된 데이터](././media/wpf-datagridgroups.png "WPF_DataGridGroups") DataGrid의 그룹화 된 데이터</span><span class="sxs-lookup"><span data-stu-id="fc3de-113">![Grouped data in a DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Grouped data in a DataGrid</span></span>

## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="fc3de-114">System.windows.controls.itemscontrol.itemssource로 CollectionViewSource 사용</span><span class="sxs-lookup"><span data-stu-id="fc3de-114">Using a CollectionViewSource as an ItemsSource</span></span>

<span data-ttu-id="fc3de-115">컨트롤에서 데이터를 그룹화, 정렬 및 필터링 하려면 <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.CollectionView> 이러한 함수를 지 원하는에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-115">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="fc3de-116">이 예제에서는 <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.CollectionViewSource> 개체의에 대해 이러한 함수를 제공 하는에 <xref:System.Collections.Generic.List%601> 바인딩됩니다 `Task` .</span><span class="sxs-lookup"><span data-stu-id="fc3de-116">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="fc3de-117">CollectionViewSource에 DataGrid를 바인딩하려면</span><span class="sxs-lookup"><span data-stu-id="fc3de-117">To bind a DataGrid to a CollectionViewSource</span></span>

1. <span data-ttu-id="fc3de-118">인터페이스를 구현 하는 데이터 컬렉션을 만듭니다 <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-118">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>

    <span data-ttu-id="fc3de-119"><xref:System.Collections.Generic.List%601>를 사용 하 여 컬렉션을 만드는 경우의 인스턴스를 인스턴스화하는 대신에서 상속 하는 새 클래스를 만들어야 합니다 <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-119">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="fc3de-120">이렇게 하면 XAML에서 컬렉션에 데이터 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-120">This enables you to data bind to the collection in XAML.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fc3de-121">컬렉션의 개체는 <xref:System.ComponentModel.INotifyPropertyChanged> <xref:System.ComponentModel.IEditableObject> 가 <xref:System.Windows.Controls.DataGrid> 속성 변경 및 편집에 올바르게 응답 하기 위해 변경 된 인터페이스와 인터페이스를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-121">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="fc3de-122">자세한 내용은 [속성 변경 알림 구현](../data/how-to-implement-property-change-notification.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc3de-122">For more information, see [Implement Property Change Notification](../data/how-to-implement-property-change-notification.md).</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. <span data-ttu-id="fc3de-123">XAML에서 컬렉션 클래스의 인스턴스를 만들고 [X:Key 지시어](../../../desktop-wpf/xaml-services/xkey-directive.md)를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-123">In XAML, create an instance of the collection class and set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md).</span></span>

3. <span data-ttu-id="fc3de-124">XAML에서 클래스의 인스턴스를 만들고, <xref:System.Windows.Data.CollectionViewSource> [x:Key 지시문](../../../desktop-wpf/xaml-services/xkey-directive.md)을 설정 하 고, 컬렉션 클래스의 인스턴스를로 설정 <xref:System.Windows.Data.CollectionViewSource.Source%2A> 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-124">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. <span data-ttu-id="fc3de-125">클래스의 인스턴스를 만들고 <xref:System.Windows.Controls.DataGrid> 속성을로 설정 합니다 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Data.CollectionViewSource> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-125">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. <span data-ttu-id="fc3de-126">코드에서에 액세스 하려면 메서드를 사용 하 여에 대 한 <xref:System.Windows.Data.CollectionViewSource> <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> 참조를 가져옵니다 <xref:System.Windows.Data.CollectionViewSource> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-126">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="fc3de-127">DataGrid에서 항목 그룹화</span><span class="sxs-lookup"><span data-stu-id="fc3de-127">Grouping items in a DataGrid</span></span>

<span data-ttu-id="fc3de-128">에서 항목을 그룹화 하는 방법을 지정 하려면 <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.PropertyGroupDescription> 형식을 사용 하 여 원본 뷰의 항목을 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-128">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>

### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="fc3de-129">XAML을 사용 하 여 DataGrid에서 항목을 그룹화 하려면</span><span class="sxs-lookup"><span data-stu-id="fc3de-129">To group items in a DataGrid using XAML</span></span>

1. <span data-ttu-id="fc3de-130"><xref:System.Windows.Data.PropertyGroupDescription>그룹화 할 속성을 지정 하는을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-130">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="fc3de-131">XAML 또는 코드에서 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-131">You can specify the property in XAML or in code.</span></span>

   1. <span data-ttu-id="fc3de-132">XAML에서을 <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> 그룹화 할 속성의 이름으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-132">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>

   2. <span data-ttu-id="fc3de-133">코드에서 그룹화 할 속성의 이름을 생성자에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-133">In code, pass the name of the property to group by to the constructor.</span></span>

2. <span data-ttu-id="fc3de-134">를 <xref:System.Windows.Data.PropertyGroupDescription> 컬렉션에 추가 합니다 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-134">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="fc3de-135">컬렉션에의 추가 인스턴스 <xref:System.Windows.Data.PropertyGroupDescription> <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 를 추가 하 여 그룹화 수준을 더 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-135">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. <span data-ttu-id="fc3de-136">그룹을 제거 하려면 <xref:System.Windows.Data.PropertyGroupDescription> 컬렉션에서을 제거 합니다 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-136">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

5. <span data-ttu-id="fc3de-137">모든 그룹을 제거 하려면 <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> 컬렉션의 메서드를 호출 합니다 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-137">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

<span data-ttu-id="fc3de-138">에서 항목이 그룹화 되 면 <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.GroupStyle> 각 그룹의 모양을 지정 하는를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-138">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="fc3de-139">를 <xref:System.Windows.Controls.GroupStyle> DataGrid의 컬렉션에 추가 하 여 적용 합니다 <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-139">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="fc3de-140">그룹화 수준이 여러 개인 경우 각 그룹 수준에 다른 스타일을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-140">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="fc3de-141">스타일은 정의 된 순서 대로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-141">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="fc3de-142">예를 들어 두 스타일을 정의 하는 경우 첫 번째이 최상위 행 그룹에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-142">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="fc3de-143">두 번째 스타일은 두 번째 수준 이하의 모든 행 그룹에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-143">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="fc3de-144"><xref:System.Windows.FrameworkElement.DataContext%2A>의는 <xref:System.Windows.Controls.GroupStyle> <xref:System.Windows.Data.CollectionViewGroup> 그룹이 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-144">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>

### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="fc3de-145">행 그룹 머리글의 모양을 변경 하려면</span><span class="sxs-lookup"><span data-stu-id="fc3de-145">To change the appearance of row group headers</span></span>

1. <span data-ttu-id="fc3de-146"><xref:System.Windows.Controls.GroupStyle>행 그룹의 모양을 정의 하는을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-146">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>

2. <span data-ttu-id="fc3de-147">태그 안에를 추가 합니다 <xref:System.Windows.Controls.GroupStyle> `<DataGrid.GroupStyle>` .</span><span class="sxs-lookup"><span data-stu-id="fc3de-147">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="fc3de-148">DataGrid에서 항목 정렬</span><span class="sxs-lookup"><span data-stu-id="fc3de-148">Sorting items in a DataGrid</span></span>

<span data-ttu-id="fc3de-149">에서 항목을 정렬 하는 방법을 지정 하려면 <xref:System.Windows.Controls.DataGrid> 형식을 사용 하 여 <xref:System.ComponentModel.SortDescription> 소스 뷰의 항목을 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-149">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>

### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="fc3de-150">DataGrid에서 항목을 정렬 하려면</span><span class="sxs-lookup"><span data-stu-id="fc3de-150">To sort items in a DataGrid</span></span>

1. <span data-ttu-id="fc3de-151"><xref:System.ComponentModel.SortDescription>정렬할 속성을 지정 하는을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-151">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="fc3de-152">XAML 또는 코드에서 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-152">You can specify the property in XAML or in code.</span></span>

    1. <span data-ttu-id="fc3de-153">XAML에서을 <xref:System.ComponentModel.SortDescription.PropertyName%2A> 정렬할 속성의 이름으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-153">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>

    2. <span data-ttu-id="fc3de-154">코드에서 정렬할 속성의 이름을 및 <xref:System.ComponentModel.ListSortDirection> 생성자에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-154">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>

2. <span data-ttu-id="fc3de-155">를 <xref:System.ComponentModel.SortDescription> 컬렉션에 추가 합니다 <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-155">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="fc3de-156">추가 속성을 기준으로 정렬 하려면의 인스턴스를 <xref:System.ComponentModel.SortDescription> 컬렉션에 추가 <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-156">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="fc3de-157">DataGrid에서 항목 필터링</span><span class="sxs-lookup"><span data-stu-id="fc3de-157">Filtering items in a DataGrid</span></span>

<span data-ttu-id="fc3de-158">을 사용 하 여에서 항목을 필터링 하려면 <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.CollectionViewSource> 이벤트에 대 한 처리기에서 필터링 논리를 제공 합니다 <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-158">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="fc3de-159">DataGrid에서 항목을 필터링 하려면</span><span class="sxs-lookup"><span data-stu-id="fc3de-159">To filter items in a DataGrid</span></span>

1. <span data-ttu-id="fc3de-160">이벤트에 대 한 처리기를 추가 <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-160">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

2. <span data-ttu-id="fc3de-161"><xref:System.Windows.Data.CollectionViewSource.Filter>이벤트 처리기에서 필터링 논리를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-161">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>

    <span data-ttu-id="fc3de-162">뷰를 새로 고칠 때마다 필터가 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-162">The filter will be applied every time the view is refreshed.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

<span data-ttu-id="fc3de-163">또는 <xref:System.Windows.Controls.DataGrid> 필터링 논리를 제공 하는 메서드를 만들고 <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> 필터를 적용 하도록 속성을 설정 하 여에서 항목을 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-163">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="fc3de-164">이 메서드의 예를 보려면 [뷰에서 데이터 필터링](../data/how-to-filter-data-in-a-view.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fc3de-164">To see an example of this method, see [Filter Data in a View](../data/how-to-filter-data-in-a-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fc3de-165">예제</span><span class="sxs-lookup"><span data-stu-id="fc3de-165">Example</span></span>

<span data-ttu-id="fc3de-166">다음 예에서는에서 데이터를 그룹화, 정렬 및 필터링 `Task` <xref:System.Windows.Data.CollectionViewSource> 하 고에서 그룹화, 정렬 및 필터링 된 데이터를 표시 하는 방법을 보여 줍니다 `Task` <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-166">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="fc3de-167">는의 <xref:System.Windows.Data.CollectionViewSource> 로 사용 됩니다 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-167">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="fc3de-168">그룹화, 정렬 및 필터링은에서 수행 되며 <xref:System.Windows.Data.CollectionViewSource> UI에 표시 됩니다 <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="fc3de-168">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="fc3de-169">이 예를 테스트 하려면 프로젝트 이름과 일치 하도록 DGGroupSortFilterExample 이름을 조정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-169">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="fc3de-170">Visual Basic를 사용 하는 경우 클래스 이름을 다음과 같이 변경 해야 <xref:System.Windows.Window> 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc3de-170">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a><span data-ttu-id="fc3de-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc3de-171">See also</span></span>

- [<span data-ttu-id="fc3de-172">데이터 바인딩 개요</span><span class="sxs-lookup"><span data-stu-id="fc3de-172">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="fc3de-173">System.collections.objectmodel.observablecollection 만들기 및 바인딩</span><span class="sxs-lookup"><span data-stu-id="fc3de-173">Create and Bind to an ObservableCollection</span></span>](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [<span data-ttu-id="fc3de-174">뷰에서 데이터 필터링</span><span class="sxs-lookup"><span data-stu-id="fc3de-174">Filter Data in a View</span></span>](../data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="fc3de-175">뷰의 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="fc3de-175">Sort Data in a View</span></span>](../data/how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="fc3de-176">XAML에서 뷰를 사용 하 여 데이터 정렬 및 그룹화</span><span class="sxs-lookup"><span data-stu-id="fc3de-176">Sort and Group Data Using a View in XAML</span></span>](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
