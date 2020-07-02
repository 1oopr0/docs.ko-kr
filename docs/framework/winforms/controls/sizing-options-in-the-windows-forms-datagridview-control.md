---
title: DataGridView 컨트롤의 크기 조정 옵션
description: Windows Forms DataGridView 컨트롤의 크기 조정 옵션에 대해 알아봅니다. DataGridView 행, 열 및 헤더는 다른 발생의 결과로 크기를 변경 합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sizing
- data grids [Windows Forms], column sizing
- DataGridView control [Windows Forms], column sizing
- DataGridView control [Windows Forms], sizing options
- data grids [Windows Forms], row sizing
- data grids [Windows Forms], sizing options
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
ms.openlocfilehash: 8ddf72c412db74df35bc3f035ff05d1e7e9738d1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613724"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView 컨트롤의 크기 조정 옵션
<xref:System.Windows.Forms.DataGridView>행, 열 및 헤더는 다양 한 발생의 결과로 크기를 변경할 수 있습니다. 다음 표에서는 이러한 항목을 보여 줍니다.  
  
|발생 빈도|설명|  
|----------------|-----------------|  
|사용자 크기 조정|사용자는 행, 열 또는 머리글 구분선을 끌거나 두 번 클릭 하 여 크기 조정을 수행할 수 있습니다.|  
|컨트롤 크기 조정|열 채우기 모드에서는 컨트롤 너비가 변경 될 때 열 너비가 변경 됩니다. 예를 들어 컨트롤을 부모 폼에 도킹 하 고 사용자가 폼의 크기를 조정 하는 경우입니다.|  
|셀 값 변경|내용 기반 자동 크기 조정 모드에서 크기는 새 표시 값에 맞게 변경 됩니다.|  
|메서드 호출|프로그래밍 방식의 내용 기반 크기 조정을 사용 하면 메서드 호출 시 셀 값에 따라 적절 한 크기 조정을 수행할 수 있습니다.|  
|속성 설정|특정 높이 및 너비 값을 설정할 수도 있습니다.|  
  
 기본적으로 사용자 크기 조정을 사용 하도록 설정 되 고 자동 크기 조정을 사용 하지 않도록 설정 되며 열 보다 더 넓은 셀 값이 잘립니다.  
  
 다음 표에서는 기본 동작을 조정 하거나 특정 크기 조정 옵션을 사용 하 여 특정 효과를 얻기 위해 사용할 수 있는 시나리오를 보여 줍니다.  
  
|시나리오|구현|  
|--------------|--------------------|  
|열 채우기 모드를 사용 하 여 가로 스크롤 막대를 표시 하지 않고 컨트롤의 전체 너비를 차지 하는 비교적 적은 수의 열에 비슷한 크기의 데이터를 표시 합니다.|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 속성을 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>으로 설정합니다.|  
|다양 한 크기의 표시 값으로 열 채우기 모드를 사용 합니다.|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 속성을 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>으로 설정합니다. 열 속성을 설정 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 하거나 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> 컨트롤을 데이터로 채운 후 control 메서드를 호출 하 여 상대 열 너비를 초기화 합니다.|  
|다양 한 중요도의 값으로 열 채우기 모드를 사용 합니다.|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 속성을 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>으로 설정합니다. <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>특정 열에 대해 항상 데이터의 일부를 표시 하거나 채우기 모드 이외의 크기 조정 옵션을 사용 해야 하는 열의 값을 크게 설정 합니다.|  
|열 채우기 모드를 사용 하 여 컨트롤 배경을 표시 하지 않습니다.|<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>마지막 열의 속성을로 설정 하 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> 고 다른 열에 다른 크기 조정 옵션을 사용 합니다. 다른 열에서 사용 가능한 공간을 너무 많이 사용 하는 경우 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 마지막 열의 속성을 설정 합니다.|  
|아이콘 또는 ID 열과 같은 고정 너비 열을 표시 합니다.|열에 대해를로 설정 하 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> 고를로 설정 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> <xref:System.Windows.Forms.DataGridViewTriState.False> 합니다. <xref:System.Windows.Forms.DataGridViewColumn.Width%2A>컨트롤을 데이터로 채운 후 컨트롤 메서드를 호출 하거나 속성을 설정 하 여 너비를 초기화 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> 합니다.|  
|자르기를 방지 하 고 공간 사용을 최적화 하기 위해 셀 내용이 변경 될 때마다 크기를 자동으로 조정 합니다.|자동 크기 조정 속성을 내용 기반 크기 조정 모드를 나타내는 값으로 설정 합니다. 많은 양의 데이터로 작업할 때 성능 저하를 방지 하려면 표시 된 행만 계산 하는 크기 조정 모드를 사용 합니다.|  
|많은 행으로 작업할 때 성능 저하를 방지 하기 위해 표시 되는 행의 값에 맞게 크기를 조정 합니다.|자동 또는 프로그래밍 방식으로 크기를 조정 하 여 적절 한 크기 조정 모드 열거 값을 사용 합니다. 스크롤할 때 새로 표시 된 행의 값에 맞게 크기를 조정 하려면 이벤트 처리기에서 크기 조정 메서드를 호출 <xref:System.Windows.Forms.DataGridView.Scroll> 합니다. 표시 된 행의 값만 새 크기를 결정 하도록 사용자를 두 번 클릭 하 여 크기 조정을 사용자 지정 하려면 또는 이벤트 처리기에서 크기 조정 메서드를 호출 <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> 합니다.|  
|특정 시간에만 셀 내용에 맞게 크기를 조정 하 여 성능 저하를 방지 하거나 사용자 크기 조정을 사용 하도록 설정 합니다.|이벤트 처리기에서 내용 기반 크기 조정 메서드를 호출 합니다. 예를 들어, 이벤트를 사용 하 여 <xref:System.Windows.Forms.DataGridView.DataBindingComplete> 바인딩 후 크기를 초기화 하 고 또는 이벤트를 처리 하 여 크기를 조정 하 여 <xref:System.Windows.Forms.DataGridView.CellValidated> <xref:System.Windows.Forms.DataGridView.CellValueChanged> 바인딩된 데이터 소스의 사용자 편집 또는 변경 사항을 보정 합니다.|  
|여러 줄 셀 내용의 행 높이를 조정 합니다.|텍스트 단락을 표시 하는 데 열 너비가 적절 한지 확인 하 고 자동 또는 프로그래밍 내용 기반 행 크기 조정을 사용 하 여 높이를 조정 합니다. 또한 셀 스타일 값을 사용 하 여 여러 줄로 된 내용이 있는 셀이 표시 되도록 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> <xref:System.Windows.Forms.DataGridViewTriState.True> 합니다.<br /><br /> 일반적으로 자동 열 크기 조정 모드를 사용 하 여 열 너비를 유지 하거나 행 높이를 조정 하기 전에 특정 너비로 설정 합니다.|  
  
## <a name="resizing-with-the-mouse"></a>마우스로 크기 조정  
 기본적으로 사용자는 셀 값을 기반으로 자동 크기 조정 모드를 사용 하지 않는 행, 열 및 헤더의 크기를 조정할 수 있습니다. 열 채우기 모드와 같은 다른 모드를 사용 하 여 사용자가 크기를 조정 하지 못하게 하려면 다음 속성 중 하나 이상을 설정 합니다 <xref:System.Windows.Forms.DataGridView> .  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 사용자가 속성을 설정 하 여 개별 행 이나 열의 크기를 조정 하지 못하도록 할 수도 있습니다 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> . 기본적으로 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 속성 값은 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> 열에 대 한 속성 값 및 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> 행에 대 한 속성 값을 기반으로 합니다. 그러나를 또는로 명시적으로 설정 하는 경우 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> <xref:System.Windows.Forms.DataGridViewTriState.True> 지정 된 값은 <xref:System.Windows.Forms.DataGridViewTriState.False> 해당 행 또는 열에 대 한 컨트롤 값을 재정의 합니다. <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>상속을 <xref:System.Windows.Forms.DataGridViewTriState.NotSet> 복원 하려면로 설정 합니다.  
  
 는 <xref:System.Windows.Forms.DataGridViewTriState.NotSet> 값 상속을 복원 하므로 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> <xref:System.Windows.Forms.DataGridViewTriState.NotSet> 행 또는 열이 컨트롤에 추가 되지 않은 경우에는 속성에서 값을 반환 하지 않습니다 <xref:System.Windows.Forms.DataGridView> . 행 또는 열의 속성 값이 상속 되는지 여부를 확인 해야 하는 경우 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 해당 속성을 검사 <xref:System.Windows.Forms.DataGridViewElement.State%2A> 합니다. 값에 <xref:System.Windows.Forms.DataGridViewElement.State%2A> 플래그가 포함 된 경우 <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet> <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 속성 값이 상속 되지 않습니다.  
  
## <a name="automatic-sizing"></a>자동 크기 조정  
 컨트롤에는 <xref:System.Windows.Forms.DataGridView> 열 채우기 모드와 내용 기반 자동 크기 조정 이라는 두 가지 종류의 자동 크기 조정 기능이 있습니다.  
  
 열 채우기 모드를 설정 하면 컨트롤의 표시 되는 열이 컨트롤의 표시 영역 너비를 채웁니다. 이 모드에 대 한 자세한 내용은 [Windows Forms DataGridView 컨트롤의 열 채우기 모드](column-fill-mode-in-the-windows-forms-datagridview-control.md)를 참조 하세요.  
  
 행, 열 및 머리글을 구성 하 여 셀 내용에 맞게 크기를 자동으로 조정할 수도 있습니다. 이 경우 셀 내용이 변경 될 때마다 크기 조정이 발생 합니다.  
  
> [!NOTE]
> 가상 모드를 사용 하 여 사용자 지정 데이터 캐시에서 셀 값을 유지 하는 경우 자동 크기 조정은 사용자가 셀 값을 편집할 때 발생 하지만 이벤트 처리기 외부에서 캐시 된 값을 변경할 경우에는 발생 하지 않습니다 <xref:System.Windows.Forms.DataGridView.CellValuePushed> . 이 경우 메서드를 호출 <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> 하 여 컨트롤이 셀 표시를 업데이트 하 고 현재 자동 크기 조정 모드를 적용 하도록 합니다.  
  
 한 차원에 대해서만 내용 기반 자동 크기 조정을 사용 하도록 설정 하는 경우, 즉 행은 제외 하 고 행은 제외 하 고 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> 도 사용 하도록 설정 된 경우 다른 차원이 변경 될 때마다 크기 조정도 발생 합니다. 예를 들어 열이 아닌 행이 자동 크기 조정으로 구성 되 고 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> 사용 하도록 설정 된 경우 사용자는 열 구분선을 끌어 열 너비를 변경할 수 있으며 행 높이가 자동으로 조정 되어 셀 내용이 완전 하 게 표시 됩니다.  
  
 내용 기반 자동 크기 조정에 대해 행과 열을 모두 구성 하 고 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> 사용 하도록 설정 된 경우, <xref:System.Windows.Forms.DataGridView> 컨트롤은 셀 내용이 변경 될 때마다 크기를 조정 하 고 새 크기를 계산할 때 이상적인 셀 높이-너비 비율을 사용 합니다.  
  
 헤더 및 행에 대 한 크기 조정 모드를 구성 하 고 컨트롤 값을 재정의 하지 않는 열에 대해 다음 속성 중 하나 이상을 설정 합니다 <xref:System.Windows.Forms.DataGridView> .  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 개별 열에 대 한 컨트롤의 열 크기 조정 모드를 재정의 하려면 해당 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 속성을 이외의 값으로 설정 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> 합니다. 열의 크기 조정 모드는 실제로 해당 속성에 따라 결정 됩니다 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> . 이 속성의 값은 해당 값이 인 경우를 제외 하 고는 열의 속성 값을 기반으로 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> 하며,이 경우 컨트롤의 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 값이 상속 됩니다.  
  
 많은 양의 데이터로 작업할 때 내용 기반 자동 크기 조정을 사용 합니다. 성능 저하를 방지 하려면 컨트롤의 모든 행을 분석 하는 대신 표시 된 행만을 기준으로 크기를 계산 하는 자동 크기 조정 모드를 사용 합니다. 최대 성능을 위해 새 데이터를 로드 한 직후와 같이 특정 시간에 크기를 조정할 수 있도록 프로그래밍 방식의 크기 조정을 대신 사용 합니다.  
  
 내용 기반 자동 크기 조정 모드는 행 이나 열 <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> 속성 또는 컨트롤 <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> 또는 속성을로 설정 하 여 숨긴 행, 열 또는 헤더에 영향을 주지 않습니다 <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> `false` . 예를 들어 큰 셀 값에 맞게 자동으로 크기를 조정 하 여 열을 숨긴 경우 큰 셀 값을 포함 하는 행이 삭제 되 면 숨겨진 열의 크기가 변경 되지 않습니다. 자동 크기 조정은 표시 유형이 변경 될 때 발생 하지 않으므로 열 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> 속성을 다시로 변경 하면 `true` 현재 내용에 따라 크기가 다시 계산 되지 않습니다.  
  
 프로그래밍 방식의 내용 기반 크기 조정은 표시 여부와 관계 없이 행, 열 및 헤더에 영향을 줍니다.  
  
## <a name="programmatic-resizing"></a>프로그래밍 방식 크기 조정  
 자동 크기 조정을 사용 하지 않도록 설정 된 경우 다음 속성을 통해 행, 열 또는 머리글의 정확한 너비나 높이를 프로그래밍 방식으로 설정할 수 있습니다.  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 다음 메서드를 사용 하 여 프로그래밍 방식으로 행, 열 및 머리글의 크기를 조정 하 여 해당 내용에 맞출 수도 있습니다.  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 이러한 메서드는 연속 크기 조정을 위해 행, 열 또는 헤더를 구성 하는 대신 한 번만 크기를 조정 합니다. 새 크기는 자동으로 계산 되어 클리핑 없이 모든 셀 내용을 표시 합니다. 그러나의 속성 값이 있는 열의 크기를 프로그래밍 방식으로 조정 하는 경우 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> 계산 된 내용 기반 너비가 열 속성 값을 비례적으로 조정 하는 데 사용 되며, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 실제로 열 너비는 모든 열이 컨트롤의 사용 가능한 표시 영역을 채우도록 이러한 새 비율에 따라 계산 됩니다.  
  
 연속 크기 조정은 연속 크기 조정으로 성능 저하를 방지 하는 데 유용 합니다. 사용자가 크기를 조정할 수 있는 행, 열 및 헤더와 열 채우기 모드의 초기 크기를 제공 하는 데도 유용 합니다.  
  
 일반적으로 특정 시간에 프로그래밍 방식의 크기 조정 메서드를 호출 합니다. 예를 들어 데이터를 로드 한 직후에 모든 열의 크기를 프로그래밍 방식으로 조정 하거나 특정 셀 값이 수정 된 후 프로그래밍 방식으로 특정 행의 크기를 조정할 수 있습니다.  
  
## <a name="customizing-content-based-sizing-behavior"></a>내용 기반 크기 조정 동작 사용자 지정  
 파생 된 <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType> 컨트롤에서, 또는 메서드를 재정의 <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> 하거나 protected 크기 조정 메서드 오버 로드를 호출 하 여 파생 셀, 행 및 열 형식으로 작업할 때 크기 조정 동작을 사용자 지정할 수 있습니다 <xref:System.Windows.Forms.DataGridView> . 보호 되는 크기 조정 메서드 오버 로드는 짝이 되는 셀의 높이와 너비를 조정 하 여 셀이 너무 길거나 긴 셀을 방지 하기 위해 쌍으로 작동 하도록 설계 되었습니다. 예를 들어 `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` 메서드의 오버 로드를 호출 하 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> 고 매개 변수에 대해 값을 전달 하 `false` 는 경우 <xref:System.Boolean> 오버 로드는 행의 셀에 대해 이상적인 높이와 너비를 계산 하지만 행 높이도 조정 됩니다. 그런 다음 메서드를 호출 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> 하 여 열 너비를 계산 된 이상적인로 조정 해야 합니다.  
  
## <a name="content-based-sizing-options"></a>내용 기반 크기 조정 옵션  
 크기 조정 속성 및 메서드에 사용 되는 열거형에는 내용 기반 크기 조정에 대해 유사한 값이 있습니다. 이러한 값을 사용 하 여 기본 크기를 계산 하는 데 사용 되는 셀을 제한할 수 있습니다. 모든 크기 조정 열거의 경우 표시 된 셀을 참조 하는 이름의 값은 표시 된 행의 셀에 대 한 계산을 제한 합니다. 행을 제외 하면 많은 양의 행으로 작업할 때 성능 저하를 방지 하는 데 유용 합니다. 머리글 또는 nonheader 셀의 셀 값에 대 한 계산을 제한할 수도 있습니다.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [Windows Forms DataGridView 컨트롤에서 열 및 행 크기 조정](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 컨트롤의 열 채우기 모드](column-fill-mode-in-the-windows-forms-datagridview-control.md)
- [방법: Windows Forms DataGridView 컨트롤의 크기 조정 모드 설정](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
