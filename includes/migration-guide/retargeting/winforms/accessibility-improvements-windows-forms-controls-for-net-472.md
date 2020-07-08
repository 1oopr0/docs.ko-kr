---
ms.openlocfilehash: cc3c2c2be179842f87be8892d057a6c4138086cb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614876"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-472"></a>.NET 4.7.2에 대한 Windows Forms 콘트롤의 접근성 개선 사항

#### <a name="details"></a>설명

Windows Forms Framework는 Windows Forms 고객을 더욱 효과적으로 지원하도록 접근성 기술로 작업하는 방법을 개선합니다. 여기에는 다음과 같은 변경이 포함됩니다.

- 고대비 모드 중에 표시를 개선하기 위한 변경 내용
- DataGridView 및 MenuStrip 컨트롤에서 키보드 탐색을 개선하기 위한 변경 내용입니다.
- 내레이터와 상호 작용의 변경 내용입니다.

#### <a name="suggestion"></a>제안 해결 방법

**이러한 변경을 옵트인 또는 옵트아웃하는 방법**: 애플리케이션이 이러한 변경의 이점을 활용하도록 하기 위해 .NET Framework 4.7.2 이상에서 실행해야 합니다. 애플리케이션은 다음과 같은 방법으로 이러한 변경의 이점을 활용할 수 있습니다.

- 컴파일되어 .NET Framework 4.7.2를 대상으로 지정합니다. 이러한 접근성 변경 내용은 .NET Framework 4.7.2 이상을 대상으로 하는 Windows Forms 애플리케이션에서 기본적으로 활성화됩니다.
- .NET Framework 4.7.1 이전 버전을 대상으로 하며 다음 예제와 같이 app.config 파일의 `<runtime>` 섹션에 [AppContext 스위치](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)를 추가하고 이를 `false`로 설정하여 레거시 접근성 동작을 옵트아웃합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
  </runtime>
</configuration>
```

.NET Framework 4.7.2에 추가된 접근성 기능을 옵트인하려면 .NET Framework 4.7.1의 접근성 기능도 옵트인해야 합니다. .NET Framework 4.7.2 이상을 대상으로 하고 레거시 접근성 동작을 유지하려는 애플리케이션은 이 AppContext 스위치를 `true`로 명확하게 설정하여 레거시 접근성 기능 사용을 옵트인할 수 있습니다.

**고대비 테마에서 OS 정의 색 사용**

- <xref:System.Windows.Forms.ToolStripDropDownButton>의 드롭다운 화살표는 이제 고대비 테마에서 OS 정의 색을 사용합니다.
- <xref:System.Windows.Forms.ButtonBase.FlatStyle>를 <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> 또는 <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>으로 설정한 <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> 및 <xref:System.Windows.Forms.CheckBox> 컨트롤은 선택된 경우 고대비 테마에서 OS 정의 색을 사용합니다. 이전에 텍스트 및 배경색이 대비되지 않았고 읽기가 어려웠습니다.
- <xref:System.Windows.Forms.Control.Enabled> 속성을 `false`으로 설정한 <xref:System.Windows.Forms.GroupBox>에 포함된 컨트롤은 이제 고대비 테마에서 OS 정의 색을 사용하게 됩니다.
- <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox> 및 <xref:System.Windows.Forms.ToolStripDropDownButton> 컨트롤이 고대비 모드에서 명도 대비를 증가시켰습니다.
- <xref:System.Windows.Forms.DataGridViewLinkCell>은 기본적으로 <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor?displayProperty=nameWithType> 속성에 대한 고대비 모드에서 OS 정의 색을 사용합니다.
참고:  Windows 10은 일부 고대비 시스템 색에 대한 값을 변경했습니다. Windows Forms Framework는 Win32 프레임워크를 기반으로 합니다. 환경을 최적화하기 위해 테스트 애플리케이션에 app.manifest 파일을 추가하고 다음과 같은 코드의 주석을 제거하여 최신 버전의 Windows에서 실행하고 최신 OS 변경 사항을 옵트인합니다.

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

**향상된 내레이터 지원**

- <xref:System.Windows.Forms.ToolStripMenuItem>의 텍스트를 발표할 경우 내레이터는 <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> 속성 값도 발표합니다.
- 내레이터는 <xref:System.Windows.Forms.ToolStripMenuItem>이 해당 <xref:System.Windows.Forms.Control.Enabled> 속성을 `false`으로 설정할 때를 지정합니다.
- 내레이터는 <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> 속성이 `true`로 설정될 경우 확인란의 상태에 대한 피드백을 제공합니다.
- 내레이터 스캔 모드 포커스 순서는 ClickOnce 다운로드 대화 상자 창에서 컨트롤의 시각적 개체 순서와 일치합니다.

**개선된 DataGridView 접근성 지원**

- <xref:System.Windows.Forms.DataGridView>의 행은 키보드를 사용하여 정렬할 수 있습니다. 현재 열로 정렬하려면 사용자는 F3 키를 사용할 수 있습니다.
- <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType>이 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>로 설정된 경우 열 헤더는 색을 변경하여 현재 행의 셀을 통해 현재 열을 사용자 탭으로 나타내게 됩니다.
- <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Parent?displayProperty=nameWithType> 속성은 이제 올바른 부모 컨트롤을 반환합니다.

**개선된 시각적 표시**

- <xref:System.Windows.Forms.ButtonBase.Text> 속성이 빈 <xref:System.Windows.Forms.RadioButton> 및 <xref:System.Windows.Forms.CheckBox> 컨트롤은 포커스를 받을 때 포커스 표시기를 표시합니다.

**개선된 속성 표 지원**

- <xref:System.Windows.Forms.PropertyGrid> 컨트롤 자식 요소는 PropertyGrid 요소를 사용하도록 설정한 경우에만 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> 속성에 대한 `true`를 반환합니다.
- <xref:System.Windows.Forms.PropertyGrid> 컨트롤 자식 요소는 PropertyGrid 요소를 사용자가 변경할 수 있는 경우에만 <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> 속성에 대한 `false`를 반환합니다.
UI 자동화 개요는 [UI Automation 개요](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview)를 참조하세요.</p>**바로 가기 탐색 개선**

- <xref:System.Windows.Forms.ToolStripButton>은 <xref:System.Windows.Forms.ToolStripPanel.TabStop> 속성이 `true`로 설정된 <xref:System.Windows.Forms.ToolStripPanel>에 포함된 경우 포커스를 허용합니다.

| 이름    | 값       |
|:--------|:------------|
| Scope   | 주요함       |
| 버전 | 4.7.2       |
| 형식    | 대상 변경 |
