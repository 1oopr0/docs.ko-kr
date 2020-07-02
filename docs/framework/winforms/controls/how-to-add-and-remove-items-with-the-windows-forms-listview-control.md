---
title: ListView 컨트롤을 사용 하 여 항목 추가 및 제거
description: 항목을 지정 하 고 속성을 할당 하 여 Windows Forms ListView 컨트롤을 사용 하 여 항목을 추가 하 고 제거 하는 방법을 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: db374ded69bcbd93527381d75a8ff751a1c9abe6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618092"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>방법: Windows Forms ListView 컨트롤을 사용하여 항목 추가 및 제거
Windows Forms 컨트롤에 항목을 추가 하는 프로세스는 <xref:System.Windows.Forms.ListView> 주로 항목을 지정 하 고 여기에 속성을 할당 하는 것으로 구성 됩니다. 언제 든 지 목록 항목 추가 또는 제거 작업을 수행할 수 있습니다.  
  
### <a name="to-add-items-programmatically"></a>프로그래밍 방식으로 항목을 추가 하려면  
  
1. <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A>속성의 메서드를 사용 합니다 <xref:System.Windows.Forms.ListView.Items%2A> .  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>프로그래밍 방식으로 항목을 제거 하려면  
  
1. <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>속성의 또는 메서드를 사용 합니다 <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> <xref:System.Windows.Forms.ListView.Items%2A> . <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>메서드는 단일 항목을 제거 합니다. <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> 메서드는 목록에서 모든 항목을 제거 합니다.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Windows.Forms.ListView>
- [ListView 컨트롤](listview-control-windows-forms.md)
- [ListView 컨트롤 개요](listview-control-overview-windows-forms.md)
