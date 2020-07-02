---
title: TableLayoutPanel를 사용 하 여 컨트롤 정렬
description: FlowLayoutPanel 컨트롤 및 TableLayoutPanel 컨트롤을 사용 하 여 Windows Forms에서 컨트롤을 정렬 하는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 6dfc6dbdef38d635dc94877f79a8e3659295bd98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622798"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>연습: TableLayoutPanel을 사용하여 Windows Forms에서 컨트롤 정렬

일부 애플리케이션에는 폼 크기가 조정되거나 내용의 크기가 변경될 때 적절하게 정렬되는 레이아웃을 가진 폼이 필요합니다. 동적 레이아웃이 필요하며 코드에서 명시적으로 <xref:System.Windows.Forms.Control.Layout> 이벤트를 처리하지 않으려는 경우 레이아웃 패널을 사용하는 것이 좋습니다.

<xref:System.Windows.Forms.FlowLayoutPanel> 컨트롤 및 <xref:System.Windows.Forms.TableLayoutPanel> 컨트롤은 폼에서 컨트롤을 정렬하는 직관적인 방법을 제공합니다. 둘 다 포함된 자식 컨트롤의 상대 위치를 제어하는 구성 가능한 자동 기능을 제공하며, 둘 다 런타임에 동적 레이아웃 기능을 제공하므로 부모 폼의 크기가 변경될 때 자식 컨트롤의 크기를 조정하고 위치를 변경할 수 있습니다. 레이아웃 패널을 레이아웃 패널 내에 중첩하여 정교한 사용자 인터페이스를 구현할 수 있습니다.

<xref:System.Windows.Forms.FlowLayoutPanel> 은 특정 흐름 방향(수평 또는 수직)으로 내용을 정렬합니다. 컨트롤 내용을 한 행에서 다음 행으로 또는 한 열에서 다음 열로 줄 바꿈할 수 있습니다. 또는 컨트롤 내용이 줄 바꿈되는 대신 잘릴 수 있습니다. 자세한 내용은 [연습: FlowLayoutPanel를 사용 하 여 Windows Forms에서 컨트롤 정렬](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)을 참조 하세요.

는 <xref:System.Windows.Forms.TableLayoutPanel> HTML 요소와 유사한 기능을 제공 하 여 해당 내용을 표로 정렬 합니다 \<table> . <xref:System.Windows.Forms.TableLayoutPanel>컨트롤을 사용 하면 각 개별 컨트롤의 위치를 정확 하 게 지정 하지 않고도 모눈 레이아웃에 컨트롤을 배치할 수 있습니다. 해당 셀은 행과 열로 정렬되며 크기가 서로 다를 수 있습니다. 행과 열 간에 셀을 병합할 수 있습니다. 셀은 양식이 포함 하 고 대부분의 다른 측면에서 컨테이너와 함께 동작 하는 모든 항목을 포함할 수 있습니다.

<xref:System.Windows.Forms.TableLayoutPanel>또한 컨트롤은 런타임에 비례 크기 조정 기능을 제공 하므로 폼 크기를 조정할 때 레이아웃이 원활 하 게 변경 될 수 있습니다. 이렇게 하면 <xref:System.Windows.Forms.TableLayoutPanel> 데이터 입력 폼 및 지역화 된 응용 프로그램 등의 용도로 컨트롤이 잘 적합 합니다. 자세한 내용은 [연습: 데이터를 입력할 수 있는 크기 조정 가능한 Windows Form 만들기](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) 및 [연습: 지역화 가능한 windows form 만들기](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))를 참조 하세요.

일반적으로 <xref:System.Windows.Forms.TableLayoutPanel> 컨트롤을 전체 레이아웃에 대 한 컨테이너로 사용 하면 안 됩니다. <xref:System.Windows.Forms.TableLayoutPanel>컨트롤을 사용 하 여 레이아웃의 일부에 비례 크기 조정 기능을 제공 합니다.

이 연습에서 설명하는 작업은 다음과 같습니다.

- Windows Forms 프로젝트 만들기

- 행 및 열에 컨트롤 정렬

- 행 및 열 속성 설정

- 컨트롤과 함께 행 및 열 확장

- 오버플로 자동 처리

- 도구 상자에서 두 번 클릭하여 컨트롤 삽입

- 윤곽선을 그려 컨트롤 삽입

- 다른 부모에 기존 컨트롤 다시 할당

작업을 완료하면 이러한 중요한 레이아웃 기능이 수행하는 역할을 이해하게 됩니다.

## <a name="creating-the-project"></a>프로젝트 만들기

첫 번째 단계는 프로젝트를 만들고 폼을 설정하는 것입니다.

#### <a name="to-create-the-project"></a>프로젝트를 만들려면

1. "TableLayoutPanelExample" 라는 Windows 응용 프로그램 프로젝트를 만듭니다. 자세한 내용은 [방법: Windows Forms 응용 프로그램 프로젝트 만들기](/visualstudio/ide/step-1-create-a-windows-forms-application-project) 를 참조 하세요.

2. **Windows** **Forms 디자이너**에서 폼을 선택 합니다.

## <a name="arranging-controls-in-rows-and-columns"></a>행 및 열에 컨트롤 정렬

<xref:System.Windows.Forms.TableLayoutPanel>컨트롤을 사용 하면 컨트롤을 행 및 열로 쉽게 정렬할 수 있습니다.

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>TableLayoutPanel를 사용 하 여 행과 열에 컨트롤을 정렬 하려면

1. <xref:System.Windows.Forms.TableLayoutPanel> 도구 상자 **에서** 컨트롤을 폼으로 끌어다 놓습니다. 기본적으로 컨트롤에는 <xref:System.Windows.Forms.TableLayoutPanel> 네 개의 셀이 있습니다.

2. <xref:System.Windows.Forms.Button> **도구 상자** 에서 컨트롤을 <xref:System.Windows.Forms.TableLayoutPanel> 컨트롤로 끌어 셀 중 하나에 놓습니다. <xref:System.Windows.Forms.Button>선택한 셀 내에 컨트롤이 생성 됩니다.

3. <xref:System.Windows.Forms.Button>각 셀에 단추가 포함 되도록 **도구 상자** 에서 컨트롤을 세 개 이상 끌어 옵니다 <xref:System.Windows.Forms.TableLayoutPanel> .

4. 두 열 사이의 세로 크기 조정 핸들을 잡고 왼쪽으로 이동 합니다. <xref:System.Windows.Forms.Button>첫 번째 열의 컨트롤은 더 작은 너비로 크기가 조정 되 고 <xref:System.Windows.Forms.Button> 두 번째 열에 있는 컨트롤의 크기는 변경 되지 않습니다.

5. 두 열 사이의 세로 크기 조정 핸들을 잡고 오른쪽으로 이동 합니다. <xref:System.Windows.Forms.Button>첫 번째 열의 컨트롤이 원래 크기로 반환 되는 반면 <xref:System.Windows.Forms.Button> 두 번째 열의 컨트롤은 오른쪽으로 이동 합니다.

6. 패널의 컨트롤에 미치는 영향을 확인 하려면 가로 크기 조정 핸들을 위아래로 이동 합니다.

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>도킹 및 고정을 사용 하 여 셀 내에서 컨트롤 위치 지정

에서 자식 컨트롤의 고정 동작은 <xref:System.Windows.Forms.TableLayoutPanel> 다른 컨테이너 컨트롤의 동작과 다릅니다. 자식 컨트롤의 도킹 동작은 다른 컨테이너 컨트롤과 동일 합니다.

#### <a name="positioning-controls-within-cells"></a>셀 내에서 컨트롤 위치 지정

1. 첫 번째 컨트롤을 선택 <xref:System.Windows.Forms.Button> 합니다. <xref:System.Windows.Forms.Control.Dock%2A> 속성의 값을 <xref:System.Windows.Forms.DockStyle.Fill>로 변경합니다. <xref:System.Windows.Forms.Button>컨트롤이 확장 되어 셀을 채웁니다.

2. 다른 컨트롤 중 하나를 선택 <xref:System.Windows.Forms.Button> 합니다. <xref:System.Windows.Forms.Control.Anchor%2A> 속성의 값을 <xref:System.Windows.Forms.AnchorStyles.Right>로 변경합니다. 오른쪽 테두리가 셀의 오른쪽 테두리 근처에 오도록 이동 합니다. 테두리 사이의 거리는 <xref:System.Windows.Forms.Button> 컨트롤의 <xref:System.Windows.Forms.Control.Margin%2A> 속성과 패널 속성의 합입니다 <xref:System.Windows.Forms.Control.Padding%2A> .

3. 컨트롤의 속성 값을 <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> 및로 변경 합니다 <xref:System.Windows.Forms.AnchorStyles.Right> <xref:System.Windows.Forms.AnchorStyles.Left> . 컨트롤의 크기는 및 값을 고려 하 여 셀의 너비를 지정 <xref:System.Windows.Forms.Control.Margin%2A> 합니다 <xref:System.Windows.Forms.Control.Padding%2A> .

4. 및 스타일을 사용 하 여 2 단계와 3 단계를 반복 <xref:System.Windows.Forms.AnchorStyles.Top> <xref:System.Windows.Forms.AnchorStyles.Bottom> 합니다.

## <a name="setting-row-and-column-properties"></a>행 및 열 속성 설정

및 컬렉션을 사용 하 여 행과 열의 개별 속성을 설정할 수 있습니다 <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> .

#### <a name="to-set-row-and-column-properties"></a>행 및 열 속성을 설정 하려면

1. <xref:System.Windows.Forms.TableLayoutPanel> **Windows Forms 디자이너**에서 컨트롤을 선택 합니다.

2. **속성** 창에서 <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> ![ ](./media/visual-studio-ellipsis-button.png) **열** 항목 옆의 줄임표 (Visual Studio의 속성 창) 단추를 클릭 하 여 컬렉션을 엽니다.

3. 첫 번째 열을 선택 하 고 속성의 값을 <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> 로 변경 <xref:System.Windows.Forms.SizeType.AutoSize> 합니다. **확인**을 클릭하여 변경 내용을 적용합니다. 컨트롤에 맞게 첫 번째 열의 너비가 줄어듭니다 <xref:System.Windows.Forms.Button> . 또한 열의 너비는 크기를 조정할 수 없습니다.

4. **속성** 창에서 컬렉션을 열고 <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> 첫 번째 열을 선택 합니다. <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> 속성의 값을 <xref:System.Windows.Forms.SizeType.Percent>로 변경합니다. **확인**을 클릭하여 변경 내용을 적용합니다. 컨트롤을 <xref:System.Windows.Forms.TableLayoutPanel> 더 큰 너비로 크기를 조정 하 고 첫 번째 열의 너비가 확장 됨을 확인 합니다. 컨트롤을 <xref:System.Windows.Forms.TableLayoutPanel> 더 작은 너비로 크기를 조정 하 고 첫 번째 열의 단추 크기가 셀에 맞게 조정 되는지 확인 합니다. 또한 열의 너비는 크기를 조정할 수 있습니다.

5. **속성** 창에서 컬렉션을 열고 <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> 나열 된 모든 열을 선택 합니다. 모든 속성의 값 <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> 을로 설정 <xref:System.Windows.Forms.SizeType.Percent> 합니다. **확인**을 클릭하여 변경 내용을 적용합니다. 컬렉션을 반복 <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> 합니다.

6. 모퉁이 크기 조정 핸들 중 하나를 잡고 컨트롤의 너비와 높이를 모두 조정 <xref:System.Windows.Forms.TableLayoutPanel> 합니다. 컨트롤의 크기가 변경 되 면 행과 열의 크기가 조정 됩니다 <xref:System.Windows.Forms.TableLayoutPanel> . 또한 행과 열은 가로 및 세로 크기 조정 핸들을 사용 하 여 크기를 조정할 수 있습니다.

## <a name="spanning-rows-and-columns-with-a-control"></a>컨트롤과 함께 행 및 열 확장

<xref:System.Windows.Forms.TableLayoutPanel>컨트롤은 디자인 타임에 컨트롤에 몇 가지 새 속성을 추가 합니다. 이러한 속성 중 두 가지는 `RowSpan` 및 `ColumnSpan` 입니다. 이러한 속성을 사용 하 여 컨트롤 범위를 두 개 이상의 행 또는 열로 설정할 수 있습니다.

#### <a name="to-span-rows-and-columns-with-a-control"></a>컨트롤과 함께 행과 열을 확장 하려면

1. <xref:System.Windows.Forms.Button>첫 번째 행과 첫 번째 열에서 컨트롤을 선택 합니다.

2. **속성** 창에서 속성의 값을 `ColumnSpan` **2**로 변경 합니다. <xref:System.Windows.Forms.Button>컨트롤은 첫 번째 열과 두 번째 열을 채웁니다. 또한이 변경 내용을 수용 하기 위해 추가 행이 추가 되었습니다.

3. 속성에 대해 2 단계를 반복 `RowSpan` 합니다.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>도구 상자에서 두 번 클릭하여 컨트롤 삽입

<xref:System.Windows.Forms.TableLayoutPanel> 도구 상자 **에서 컨트롤을 두 번 클릭하여**컨트롤을 채울 수 있습니다.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>도구 상자에서 두 번 클릭하여 컨트롤을 삽입하려면

1. <xref:System.Windows.Forms.TableLayoutPanel> 도구 상자 **에서** 컨트롤을 폼으로 끌어다 놓습니다.

2. <xref:System.Windows.Forms.Button> 도구 상자 **에서**컨트롤 아이콘을 두 번 클릭합니다. 새 단추 컨트롤이 <xref:System.Windows.Forms.TableLayoutPanel> 컨트롤의 첫 번째 셀에 나타납니다.

3. **도구 상자**에서 컨트롤을 몇 개 더 두 번 클릭합니다. 새 컨트롤이 컨트롤의 빈 셀에 연속 해 서 표시 <xref:System.Windows.Forms.TableLayoutPanel> 됩니다. 또한 <xref:System.Windows.Forms.TableLayoutPanel> 열려 있는 셀을 사용할 수 없는 경우 새 컨트롤에 맞게 컨트롤이 확장 됩니다.

## <a name="automatic-handling-of-overflows"></a>오버플로 자동 처리

컨트롤에 컨트롤을 삽입 하는 경우 <xref:System.Windows.Forms.TableLayoutPanel> 새 컨트롤에 대 한 빈 셀이 없을 수 있습니다. <xref:System.Windows.Forms.TableLayoutPanel>컨트롤은 셀 수를 늘려서 이러한 상황을 자동으로 처리 합니다.

#### <a name="to-observe-automatic-handling-of-overflows"></a>오버플로 자동 처리를 관찰 하려면

1. 컨트롤에 빈 셀이 있으면 <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.Button> 컨트롤이 가득 찼을 때까지 새 컨트롤을 계속 삽입 합니다 <xref:System.Windows.Forms.TableLayoutPanel> .

2. <xref:System.Windows.Forms.TableLayoutPanel>컨트롤이 꽉 차면 <xref:System.Windows.Forms.Button> **도구 상자** 에서 아이콘을 두 번 클릭 하 여 다른 컨트롤을 삽입 <xref:System.Windows.Forms.Button> 합니다. 컨트롤은 새 <xref:System.Windows.Forms.TableLayoutPanel> 컨트롤을 수용할 새 셀을 만듭니다. 몇 가지 컨트롤을 추가로 삽입 하 고 크기 조정 동작을 관찰 합니다.

3. <xref:System.Windows.Forms.TableLayoutPanel> 컨트롤의 <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> 속성 값을 <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>로 변경합니다. <xref:System.Windows.Forms.Button> **도구 상자** 의 아이콘을 두 번 클릭 하 여 <xref:System.Windows.Forms.Button> 컨트롤이 가득 찼을 때까지 컨트롤을 삽입 <xref:System.Windows.Forms.TableLayoutPanel> 합니다. <xref:System.Windows.Forms.Button> **도구 상자** 에서 아이콘을 다시 두 번 클릭 합니다. 추가 행과 열을 만들 수 없다는 오류 메시지가 표시 **Windows Forms 디자이너** .

## <a name="inserting-a-control-by-drawing-its-outline"></a>윤곽선을 그려 컨트롤 삽입

<xref:System.Windows.Forms.TableLayoutPanel> 컨트롤에 컨트롤을 삽입하고 셀에서 해당 윤곽선을 그려 크기를 지정합니다.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>윤곽선을 그려 컨트롤을 삽입하려면

1. <xref:System.Windows.Forms.TableLayoutPanel> 도구 상자 **에서** 컨트롤을 폼으로 끌어다 놓습니다.

2. **도구 상자**에서 <xref:System.Windows.Forms.Button> 컨트롤 아이콘을 클릭합니다. 폼으로 끌어다 놓지 마세요.

3. 마우스 포인터를 <xref:System.Windows.Forms.TableLayoutPanel> 컨트롤 위로 이동합니다. 포인터가 <xref:System.Windows.Forms.Button> 컨트롤 아이콘이 연결된 십자형으로 바뀝니다.

4. 마우스 단추를 길게 클릭합니다.

5. 마우스 포인터를 끌어 <xref:System.Windows.Forms.Button> 컨트롤의 윤곽선을 그립니다. 원하는 크기가 되면 마우스 단추를 놓습니다. 컨트롤은 <xref:System.Windows.Forms.Button> 컨트롤의 윤곽선을 그린 셀에 생성 됩니다.

## <a name="multiple-controls-within-cells-are-not-permitted"></a>셀 내의 여러 컨트롤이 허용 되지 않습니다.

<xref:System.Windows.Forms.TableLayoutPanel>컨트롤은 셀 마다 자식 컨트롤을 하나만 포함할 수 있습니다.

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>셀 내의 여러 컨트롤이 허용 되지 않음을 보여 주기 위해

- <xref:System.Windows.Forms.Button> **도구 상자** 에서 컨트롤을 컨트롤로 끌어다 놓고 <xref:System.Windows.Forms.TableLayoutPanel> 이 컨트롤을 차지 하는 셀 중 하나에 놓습니다. 컨트롤에서 사용 하는 <xref:System.Windows.Forms.TableLayoutPanel> 셀에 컨트롤을 놓을 수 <xref:System.Windows.Forms.Button> 없습니다.

## <a name="swapping-controls"></a>컨트롤 맞바꾸기

<xref:System.Windows.Forms.TableLayoutPanel>컨트롤을 사용 하면 두 개의 다른 셀을 차지 하는 컨트롤을 교환할 수 있습니다.

#### <a name="to-swap-controls"></a>컨트롤을 교환 하려면

- 점유 된 셀에서 컨트롤 중 하나를 끌고 <xref:System.Windows.Forms.Button> 다른의 다른 셀에 놓습니다. 두 컨트롤은 한 셀에서 다른 셀로 이동 됩니다.

## <a name="next-steps"></a>다음 단계

레이아웃 패널 및 컨트롤의 조합을 사용하여 복잡한 레이아웃을 얻을 수 있습니다. 다음을 추가로 살펴볼 수 있습니다.

- 컨트롤 중 하나의 <xref:System.Windows.Forms.Button> 크기를 더 크게 조정 하 고 레이아웃에 미치는 영향을 확인 하세요.

- 여러 컨트롤의 선택 항목을 컨트롤에 붙여넣고 <xref:System.Windows.Forms.TableLayoutPanel> 컨트롤이 삽입 되는 방식을 확인 합니다.

- 레이아웃 패널에 다른 레이아웃 패널을 포함할 수 있습니다. <xref:System.Windows.Forms.TableLayoutPanel> 컨트롤을 기존 컨트롤에 끌어다 놓습니다.

- <xref:System.Windows.Forms.TableLayoutPanel> 컨트롤을 부모 폼에 도킹합니다. 폼의 크기를 조정하고 레이아웃에 미치는 영향을 확인합니다.

## <a name="see-also"></a>참고 항목

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [연습: FlowLayoutPanel을 사용하여 Windows Forms에서 컨트롤 정렬](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [연습: 맞춤선을 사용하여 Windows Forms에서 컨트롤 정렬](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [연습: 데이터를 입력할 수 있는 크기 조정 가능한 Windows Form 만들기](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [연습: 지역화 가능한 Windows Form 만들기](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [TableLayoutPanel 컨트롤에 대한 모범 사례](best-practices-for-the-tablelayoutpanel-control.md)
- [AutoSize 속성 개요](autosize-property-overview.md)
- [방법: Windows Forms에 컨트롤 도킹](how-to-dock-controls-on-windows-forms.md)
- [방법: Windows Forms에서 컨트롤 고정](how-to-anchor-controls-on-windows-forms.md)
- [연습: Padding, Margin 및 AutoSize 속성을 사용하여 Windows Forms 컨트롤 레이아웃](windows-forms-controls-padding-autosize.md)
