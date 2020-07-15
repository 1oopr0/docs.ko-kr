---
title: ARM(애플리케이션 도메인 리소스 모니터링) ETW 이벤트
description: '.NET의 ARM (응용 프로그램 도메인 리소스 모니터링) ETW 이벤트 (예: ThreadCreated, AppDomainMemAllocated, AppDomainMemSurvived 등)에 대해 읽어 보십시오.'
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: d118b3196b019a804df5399464cb86f7492c61b0
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309783"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>ARM(애플리케이션 도메인 리소스 모니터링) ETW 이벤트

이들 이벤트는 응용 프로그램 도메인 상태에 대한 자세한 진단 정보를 제공합니다. 이들 이벤트를 사용하거나 애플리케이션 도메인 리소스 모니터링(ARM) 기능을 사용하여 같은 정보를 얻을 수 있습니다.

## <a name="threadcreated-event"></a>ThreadCreated 이벤트

이 이벤트는 런다운 공급자에서만 `ThreadDC` 로서 발생합니다( `AppDomainResourceManagementRundownKeyword` 키워드에서). 이 이벤트는 이 범주의 런다운 공급자에서 발생하는 유일한 이벤트입니다.

다음 표에서는 키워드와 수준을 보여 줍니다. 자세한 내용은 [CLR ETW 키워드 및 수준](clr-etw-keywords-and-levels.md)을 참조 하세요.

|이벤트를 발생시키기 위한 키워드|수준|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|정보 제공(4)|
|`ThreadingKeyword` (0x10000)|정보 제공(4)|

다음 표에서는 이벤트 정보를 보여 줍니다.

|Event|이벤트 ID|발생 시기|
|-----------|--------------|-----------------|
|`ThreadCreated`|85|애플리케이션 도메인에 대한 스레드가 만들어졌습니다.|

다음 표에서는 이벤트 데이터를 보여 줍니다.

|필드 이름|데이터 형식|Description|
|----------------|---------------|-----------------|
|ThreadID|win:UInt64|만들어진 스레드의 ID입니다.|
|AppDomainID|win:UInt64|스레드 활동이 보고되는 애플리케이션 도메인의 식별자입니다.|
|플래그|win:UInt32|스레드 만들기 플래그입니다.|
|ManagedThreadIndex|win:UInt32|만들어진 스레드의 관리되는 인덱스입니다.|
|OSThreadID|win:UInt32|만들어진 스레드의 운영 체제 ID입니다.|
|ClrInstanceID|win:UInt16|CLR 또는 CoreCLR 인스턴스에 대한 고유 ID입니다.|

## <a name="appdomainmemallocated-event"></a>AppDomainMemAllocated 이벤트

다음 표에서는 키워드와 수준을 보여 줍니다.

|이벤트를 발생시키기 위한 키워드|수준|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|정보 제공(4)|

다음 표에서는 이벤트 정보를 보여 줍니다.

|Event|이벤트 ID|발생 시기|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|83|약 4MB의 모든 메모리가 애플리케이션 도메인에서 할당됩니다.|

다음 표에서는 이벤트 데이터를 보여 줍니다.

|필드 이름|데이터 형식|Description|
|----------------|---------------|-----------------|
|AppDomainID|win:UInt64|리소스 사용량이 보고되는 애플리케이션 도메인의 식별자입니다.|
|Allocated|win:UInt64|애플리케이션 도메인이 만들어진 후 이 애플리케이션 도메인에서 할당된 총 바이트 수입니다(해제된 메모리 양을 빼지 않음).|
|ClrInstanceID|win:UInt16|CLR 또는 CoreCLR 인스턴스에 대한 고유 ID입니다.|

## <a name="appdomainmemsurvived-event"></a>AppDomainMemSurvived 이벤트

다음 표에서는 키워드와 수준을 보여 줍니다.

|이벤트를 발생시키기 위한 키워드|수준|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|정보 제공(4)|

다음 표에서는 이벤트 정보를 보여 줍니다.

|Event|이벤트 ID|발생 시기|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|84|각 가비지 수집이 종료되었습니다.|

다음 표에서는 이벤트 데이터를 보여 줍니다.

|필드 이름|데이터 형식|Description|
|----------------|---------------|-----------------|
|AppDomainID|win:UInt64|리소스 사용량이 보고되는 도메인의 식별자입니다.|
|Survived|win:UInt64|마지막 수집 후에도 유지되고 이 애플리케이션 도메인에 저장되는 것으로 알려진 바이트 수입니다. 이 수는 전체 수집 후에 정확하고 완전하지만 임시 수집 후에는 불완전할 수 있습니다.|
|ProcessSurvived|win:UInt64|마지막 수집에서 유지된 총 바이트 수입니다. 전체 수집 후에 이 수는 관리되는 힙에 실시간으로 저장되는 바이트 수를 나타냅니다. 임시 수집 후에 이 수는 임시 생성에 실시간으로 저장되는 바이트 수를 나타냅니다.|
|ClrInstanceID|win:UInt16|CLR 또는 CoreCLR 인스턴스에 대한 고유 ID입니다.|

## <a name="threadappdomainenter-event"></a>ThreadAppDomainEnter 이벤트

다음 표에서는 키워드와 수준을 보여 줍니다.

|이벤트를 발생시키기 위한 키워드|수준|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|정보 제공(4)|
|`ThreadingKeyword` (0x10000)|정보 제공(4)|

다음 표에서는 이벤트 정보를 보여 줍니다.

|Event|이벤트 ID|발생 시기|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|87|스레드가 애플리케이션 도메인에 들어갑니다.|

다음 표에서는 이벤트 데이터를 보여 줍니다.

|필드 이름|데이터 형식|Description|
|----------------|---------------|-----------------|
|ThreadID|win:UInt64|스레드 식별자입니다.|
|AppDomainID|win:UInt64|애플리케이션 도메인 식별자입니다.|
|ClrInstanceID|win:UInt16|CLR 또는 CoreCLR 인스턴스에 대한 고유 ID입니다.|

## <a name="threadterminated-event"></a>ThreadTerminated 이벤트

다음 표에서는 키워드와 수준을 보여 줍니다.

|이벤트를 발생시키기 위한 키워드|수준|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|정보 제공(4)|
|`ThreadingKeyword` (0x10000)|정보 제공(4)|

다음 표에서는 이벤트 정보를 보여 줍니다.

|Event|이벤트 ID|발생 시기|
|-----------|--------------|-----------------|
|`ThreadTerminated`|86|스레드가 종료됩니다.|

다음 표에서는 이벤트 데이터를 보여 줍니다.

|필드 이름|데이터 형식|Description|
|----------------|---------------|-----------------|
|ThreadID|win:UInt64|스레드 식별자입니다.|
|AppDomainID|win:UInt64|애플리케이션 도메인 식별자입니다.|
|ClrInstanceID|win:UInt16|CLR 또는 CoreCLR 인스턴스에 대한 고유 ID입니다.|

## <a name="see-also"></a>참고 항목

- [CLR ETW 이벤트](clr-etw-events.md)
