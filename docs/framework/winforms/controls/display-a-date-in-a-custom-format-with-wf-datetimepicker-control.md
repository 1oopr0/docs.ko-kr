---
title: DateTimePicker 컨트롤을 사용 하 여 날짜를 사용자 지정 형식으로 표시
description: Windows Forms DateTimePicker 컨트롤을 사용 하 여 컨트롤의 날짜 및 시간 표시 형식을 지정 하는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
ms.openlocfilehash: 773070136e4fd43ab1bf510ebcaf6b0aa6a7ba8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325826"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="27e8b-103">방법: Windows Forms DateTimePicker 컨트롤을 사용하여 날짜를 사용자 지정 형식으로 표시</span><span class="sxs-lookup"><span data-stu-id="27e8b-103">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="27e8b-104">Windows Forms <xref:System.Windows.Forms.DateTimePicker> 컨트롤을 사용 하면 컨트롤의 날짜 및 시간 표시를 유연 하 게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27e8b-104">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="27e8b-105"><xref:System.Windows.Forms.DateTimePicker.Format%2A>속성을 사용 하면에 나열 된 미리 정의 된 형식에서 선택할 수 있습니다 <xref:System.Windows.Forms.DateTimePickerFormat> .</span><span class="sxs-lookup"><span data-stu-id="27e8b-105">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="27e8b-106">이러한 항목이 용도에 적합 하지 않은 경우에 나열 된 형식 문자를 사용 하 여 고유한 형식 스타일을 만들 수 있습니다 <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> .</span><span class="sxs-lookup"><span data-stu-id="27e8b-106">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="27e8b-107">사용자 지정 형식을 표시 하려면</span><span class="sxs-lookup"><span data-stu-id="27e8b-107">To display a custom format</span></span>  
  
1. <span data-ttu-id="27e8b-108"><xref:System.Windows.Forms.DateTimePicker.Format%2A> 속성을 `DateTimePickerFormat.Custom`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="27e8b-108">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2. <span data-ttu-id="27e8b-109">속성을 <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> 형식 문자열로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="27e8b-109">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="27e8b-110">서식이 지정 된 값에 텍스트를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="27e8b-110">To add text to the formatted value</span></span>  
  
1. <span data-ttu-id="27e8b-111">작은따옴표를 사용 하 여 "M"과 같은 서식 문자가 아닌 문자 또는 ":"와 같은 구분 기호를 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="27e8b-111">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="27e8b-112">예를 들어 아래 서식 문자열은 영어 (미국) 문화권의 "오늘: 05:30:31 년 3 월 02 2012 일 금요일" 형식으로 현재 날짜를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="27e8b-112">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     <span data-ttu-id="27e8b-113">문화권 설정에 따라 작은따옴표로 묶이지 않은 문자는 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27e8b-113">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="27e8b-114">예를 들어 위의 형식 문자열은 영어 (미국) 문화권의 "오늘: 05:30:31 년 3 월 02 2012 일 금요일" 형식으로 현재 날짜를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="27e8b-114">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="27e8b-115">첫 번째 콜론은 "hh: mm: ss"에 있는 구분 문자로 사용할 수 없으므로 작은따옴표로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27e8b-115">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="27e8b-116">다른 문화권에서 형식은 "오늘: 05.30.31 금요일 3 월 02 2012"로 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27e8b-116">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e8b-117">참조</span><span class="sxs-lookup"><span data-stu-id="27e8b-117">See also</span></span>

- [<span data-ttu-id="27e8b-118">DateTimePicker 컨트롤</span><span class="sxs-lookup"><span data-stu-id="27e8b-118">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="27e8b-119">방법: Windows Forms DateTimePicker 컨트롤을 사용하여 날짜 설정 및 반환</span><span class="sxs-lookup"><span data-stu-id="27e8b-119">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
