---
title: 그래픽 렌더링 레지스트리 설정
description: Windows Presentation Foundation (WPF)에서 문제 해결, 디버깅 및 제품 지원을 위해 레지스트리 설정을 사용 하는 방법을 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
ms.openlocfilehash: a2c6cfa5a207ae89c053f6ee81597f01458b5933
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853761"
---
# <a name="graphics-rendering-registry-settings"></a>그래픽 렌더링 레지스트리 설정
이 항목에서는 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 애플리케이션에 영향을 미치는 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 그래픽 렌더링 레지스트리 설정에 대해 간략하게 설명합니다.  

<a name="overview"></a>
## <a name="when-to-use-graphics-rendering-registry-settings"></a>그래픽 렌더링 레지스트리 설정을 사용하는 경우  
 이러한 레지스트리 설정은 문제 해결, 디버깅 및 제품 지원 목적으로 제공됩니다. 레지스트리를 변경하면 모든 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 애플리케이션에 영향을 주기 때문에 애플리케이션은 자동으로 또는 설치 중에 이러한 레지스트리 키를 변경하면 안 됩니다.  
  
<a name="xpdmandwddm"></a>
## <a name="what-are-xpdm-and-wddm"></a>XPDM 및 WDDM이란?  
 일부 그래픽 렌더링 레지스트리 설정은 비디오 카드가 XPDM 드라이버를 사용하는지 또는 WDDM 드라이버를 사용하는지에 따라 기본값이 다릅니다. XPDM은 Microsoft Windows XP 디스플레이 드라이버 모델 이며, WDDM은 Windows 디스플레이 드라이버 모델입니다. WDDM은 Windows Vista 및 Windows 7을 실행 하는 컴퓨터에서 사용할 수 있습니다. XPDM은 Windows Vista, Microsoft Windows XP 및 Microsoft Windows Server 2003를 실행 하는 컴퓨터에서 사용할 수 있습니다. WDDM에 대 한 자세한 내용은 [wddm (Windows Display Driver Model) 디자인 가이드](/windows-hardware/drivers/display/windows-vista-display-driver-model-design-guide)를 참조 하세요.  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>레지스트리 설정  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]에서는 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 렌더링을 제어하는 다음 네 개의 레지스트리 설정을 제공합니다.  
  
|설정|설명|  
|-------------|-----------------|  
|**하드웨어 가속 옵션 사용 안 함**|하드웨어 가속을 사용해야 하는지 지정합니다.|  
|**최대 다중 샘플 값**|앤티 앨리어싱 3D 콘텐츠에 대 한 다중 샘플링 수준을 지정 합니다.|  
|**필수 비디오 드라이버 날짜 설정**|시스템에서 2004년 11월 이전에 릴리스된 드라이버의 하드웨어 가속을 사용하지 않게 설정할지 지정합니다.|  
|**참조 래스터라이저 옵션 사용**|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]에서 참조 래스터라이저를 사용해야 하는지 지정합니다.|  
  
 이러한 설정은 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 레지스트리 설정을 참조하는 방법을 아는 외부 구성 유틸리티에서 액세스할 수 있습니다. 이러한 설정은 Windows 레지스트리 편집기를 사용 하 여 값에 직접 액세스 하 여 만들거나 수정할 수도 있습니다.  
  
<a name="disablehardwareacceleration"></a>
## <a name="disable-hardware-acceleration-option"></a>하드웨어 가속 옵션 사용 안 함  
  
|레지스트리 키|값 형식|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **하드웨어 가속 옵션 사용 안 함**을 사용하여 디버깅 및 테스트 목적으로 하드웨어 가속을 해제할 수 있습니다. 애플리케이션에서 렌더링 아티팩트를 표시되면 하드웨어 가속을 해제하세요. 아티팩트가 사라지면 비디오 드라이버에 문제가 있는 것일 수 있습니다.  
  
 **하드웨어 가속 옵션 사용 안 함**은 0 또는 1의 DWORD 값입니다. 이 값이 1이면 하드웨어 가속이 사용되지 않습니다. 이 값이 0이면 시스템이 하드웨어 가속 요구를 충족할 경우 하드웨어 가속이 사용됩니다. 자세한 내용은 [그래픽 렌더링 계층](../advanced/graphics-rendering-tiers.md)을 참조하세요.  
  
<a name="maxmultisample"></a>
## <a name="maximum-multisample-value"></a>최대 다중 샘플 값  
  
|레지스트리 키|값 형식|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **Maximum 다중 샘플 값** 을 사용 하면 3d 콘텐츠의 최대 앤티 앨리어싱 크기를 조정할 수 있습니다. Windows Vista에서 3D 앤티 앨리어싱을 사용 하지 않도록 설정 하려면이 수준을 사용 합니다.  
  
 **최대 다중 샘플 값**은 0~16 사이의 DWORD 값입니다. 값이 0 이면 3D 콘텐츠의 다중 샘플 앤티엘리어싱을 사용 하지 않도록 설정 하 고, 값 16은 비디오 카드에서 지 원하는 경우 최대 16x 다중 샘플 앤티엘리어싱을 사용 하려고 합니다. XPDM 드라이버를 사용 하는 컴퓨터에서이 레지스트리 키 값을 설정 하면 응용 프로그램에서 많은 양의 추가 비디오 메모리를 사용 하 고, 3D 렌더링의 성능을 저하 시키고, 렌더링 오류 및 안정성 문제를 일으킬 수 있습니다.  
  
 이 레지스트리 키가 설정되지 않았으면 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 기본값은 XPDM 드라이버의 경우 0, WDDM 드라이버의 경우 4입니다.  
  
<a name="requiredvideodriverdatesetting"></a>
## <a name="required-video-driver-date-setting"></a>필수 비디오 드라이버 날짜 설정  
  
|레지스트리 키|값 형식|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|String|  
  
 2004 년 11 월에 Microsoft는 새 버전의 드라이버 테스트 지침을 출시 했습니다. 이 날짜 이후에 작성 된 드라이버는 더 나은 안정성을 제공 합니다. 기본적으로 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]는 이러한 드라이버에 대해 하드웨어 가속 파이프라인을 사용하며, 이 날짜 이전에 게시된 XPDM 드라이버용 소프트웨어 렌더링으로 대체됩니다.  
  
 **필수 비디오 드라이버 날짜 설정**을 통해 XPDM 드라이버에 대한 대체 최소 날짜를 지정할 수 있습니다. 비디오 드라이버가 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]를 지원하기에 충분히 안정적인 경우에만 2004년 11월 이전 날짜를 지정하는 것이 좋습니다.  
  
 필수 비디오 드라이버 설정은 다음 형식의 문자열을 사용합니다.  
  
| |  
|-|  
|*YYYY* `/` *MM* `/` *DD*|  
  
 여기서 *YYYY*는 4자리 연도이고, *MM*은 2자리 월이고, *DD*는 2자리 일입니다. 이 값을 설정하지 않으면 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]는 필수 비디오 드라이버 날짜로 2004년 11월을 사용합니다.  
  
<a name="usereferencerasterizeroption"></a>
## <a name="use-reference-rasterizer-option"></a>참조 래스터라이저 옵션 사용  
  
|레지스트리 키|값 형식|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **참조 래스터 라이저 사용 옵션** 을 사용 하면 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 디버깅을 위해 시뮬레이션 된 하드웨어 렌더링 모드를 강제 적용할 수 있습니다 .는 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 하드웨어 모드로 전환 되지만 실제 하드웨어 장치 대신 Microsoft Direct3D 참조 소프트웨어 래스터 라이저 (d3dref9.dll)를 사용 합니다.  
  
 참조 래스터라이저는 매우 느리지만 비디오 드라이버를 우회하여 드라이버 문제로 인한 렌더링 문제를 방지합니다. 이러한 이유로 참조 래스터라이저를 사용하여 렌더링 문제가 비디오 드라이버로 인한 것인지 확인할 수 있습니다. d3dref9.dll 파일은 시스템 경로의 위치나 애플리케이션의 로컬 디렉터리 같이 애플리케이션이 액세스할 수 있는 위치에 있어야 합니다.  
  
 **참조 래스터라이저 옵션 사용**은 DWORD 값을 사용합니다. 값이 0이면 참조 래스터라이저가 사용되지 않는 것입니다. 0이 아닌 값을 지정하면 강제로 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]가 참조 래스터라이저를 사용하게 됩니다.  
  
## <a name="see-also"></a>참조

- [그래픽 렌더링 계층](../advanced/graphics-rendering-tiers.md)
- [WPF 그래픽 렌더링 개요](wpf-graphics-rendering-overview.md)
