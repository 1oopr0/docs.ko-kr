---
title: BindingNavigator 컨트롤에 로드, 저장 및 취소 단추 추가
description: Windows Forms BindingNavigator 컨트롤에 로드, 저장 및 취소 단추를 추가 하는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: d4db91b8cfaf2df253d0c4cf5d8a66e9157d4986
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173421"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>방법: Windows Forms BindingNavigator 컨트롤에 로드, 저장 및 취소 단추 추가

<xref:System.Windows.Forms.BindingNavigator>컨트롤은 <xref:System.Windows.Forms.ToolStrip> 데이터에 바인딩되는 폼에서 컨트롤을 탐색 하 고 조작 하기 위한 특수 한 용도의 컨트롤입니다.

컨트롤 이기 때문에 <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.BindingNavigator> 구성 요소를 쉽게 수정 하 여 사용자에 대 한 추가 또는 대체 명령을 포함할 수 있습니다.

다음 절차에서 <xref:System.Windows.Forms.TextBox> 컨트롤은 데이터에 바인딩되고 <xref:System.Windows.Forms.ToolStrip> 폼에 추가 된 컨트롤은 로드, 저장 및 취소 단추를 포함 하도록 수정 됩니다.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>BindingNavigator 구성 요소에 로드, 저장 및 취소 단추 추가

1. Visual Studio에서 <xref:System.Windows.Forms.TextBox> 폼에 컨트롤을 추가 합니다.

2. <xref:System.Windows.Forms.BindingSource>데이터 소스에 바인딩된에 바인딩합니다. 이 예의 경우는 <xref:System.Windows.Forms.BindingSource> 데이터베이스에 바인딩됩니다.

3. 데이터 집합 및 테이블 어댑터를 생성 한 후 컨트롤을 <xref:System.Windows.Forms.BindingNavigator> 폼으로 끌어 옵니다.

4. 컨트롤 <xref:System.Windows.Forms.BindingNavigator> <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> 에 바인딩된 폼의 컨트롤에 대 한 속성을로 설정 합니다 <xref:System.Windows.Forms.BindingSource> .

5. <xref:System.Windows.Forms.BindingNavigator> 컨트롤을 선택합니다.

6. 디자이너 작업 문자 모양 ( ![ 작은 검은색 화살표)을 클릭 ](./media/designer-actions-glyph.gif) 하 여 **BindingNavigator 작업** 대화 상자를 표시 하 고 **항목 편집**을 선택 합니다.

     **항목 컬렉션 편집기** 가 나타납니다.

7. **항목 컬렉션 편집기**에서 다음을 완료 합니다.

    1. 적절 한 <xref:System.Windows.Forms.ToolStripSeparator> <xref:System.Windows.Forms.ToolStripButton> 형식을 선택 하 <xref:System.Windows.Forms.ToolStripItem> 고 **추가** 단추를 클릭 하 여 세 개의 항목을 추가 합니다.

    2. <xref:System.Windows.Forms.ToolStripItem.Name%2A>단추의 속성을 **loadbutton**, **Savebutton**및 **cancelbutton**으로 각각 설정 합니다.

    3. <xref:System.Windows.Forms.ToolStripItem.Text%2A>단추의 속성을 **로드**, **저장**및 **취소**로 설정 합니다.

    4. <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>각 단추에 대 한 속성을 **텍스트**로 설정 합니다. 또는이 속성을 **image** 또는 **imageandtext**로 설정 하 고 속성에 표시 될 이미지를 설정할 수 있습니다 <xref:System.Windows.Forms.ToolStripItem.Image%2A> .

    5. **확인** 을 클릭하여 대화 상자를 닫습니다. 단추는에 추가 됩니다 <xref:System.Windows.Forms.ToolStrip> .

8. 폼을 마우스 오른쪽 단추로 클릭 하 고 **코드 보기**를 선택 합니다.

9. 코드 편집기에서 테이블 어댑터에 데이터를 로드 하는 코드 줄을 찾습니다. 이 코드는 2 단계에서 데이터 바인딩을 설정할 때 생성 되었습니다. 코드는 다음과 유사 합니다. `TableAdapterName.Fill(DataSetName.TableName)` . 이는 대부분 양식의 이벤트에 있을 수 있습니다 <xref:System.Windows.Forms.Form.Load> .

10. 이전에 만든 부하의 이벤트에 대 한 이벤트 처리기를 만들고 <xref:System.Windows.Forms.ToolStripItem.Click> **Load** <xref:System.Windows.Forms.ToolStripButton> 데이터를 로드 하는 코드를 여기로 이동 합니다.

     이제 코드는 다음과 같이 표시 됩니다.

    ```vb
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click
        TableAdapterName.Fill(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void LoadButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Fill(DataSetName.TableName);
    }
    ```

11. 이전에 만든 저장 이벤트에 대 한 이벤트 처리기를 만들고 <xref:System.Windows.Forms.ToolStripItem.Click> **Save** <xref:System.Windows.Forms.ToolStripButton> 컨트롤이 바인딩된 테이블 내의 데이터를 업데이트 하는 코드를 작성 합니다.

    ```vb
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click
        TableAdapterName.Update(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void SaveButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Update(DataSetName.TableName);
    }
    ```

    > [!NOTE]
    > 일부 경우에는 <xref:System.Windows.Forms.BindingNavigator> 구성 요소에 이미 **저장** 단추가 있지만 Windows Forms 디자이너에 의해 코드가 생성 되지 않았습니다. 이 경우 <xref:System.Windows.Forms.ToolStripItem.Click> 에서 완전히 새로 만들기 단추를 만들지 않고 해당 단추에 대 한 이벤트 처리기에 위의 코드를 추가할 수 있습니다 <xref:System.Windows.Forms.ToolStrip> . 그러나 단추는 기본적으로 사용 하지 않도록 설정 되어 있으므로 단추가 <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> 제대로 작동 하도록 단추의 속성을로 설정 해야 합니다 `true` .

12. 앞에서 만든 취소의 이벤트에 대 한 이벤트 처리기를 만들고 <xref:System.Windows.Forms.ToolStripItem.Click> **Cancel** <xref:System.Windows.Forms.ToolStripButton> 표시 되는 데이터 레코드의 모든 변경 내용을 취소 하는 코드를 작성 합니다.

    ```vb
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click
        BindingSourceName.CancelEdit()
    End Sub
    ```

    ```csharp
    private void CancelButton_Click(System.Object sender, System.EventArgs e)
    {
        BindingSourceName.CancelEdit();
    }
    ```

    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>메서드는 데이터의 행으로 범위가 한정 됩니다. 다음 레코드로 이동 하기 전에 해당 개별 레코드를 보는 동안 변경한 내용을 저장 합니다.

## <a name="see-also"></a>참고 항목

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator 컨트롤](bindingnavigator-control-windows-forms.md)
- [BindingSource 구성 요소 개요](bindingsource-component-overview.md)
