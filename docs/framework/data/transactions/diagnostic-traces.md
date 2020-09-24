---
title: 진단 추적
description: .NET의 진단 추적에 대해 알아봅니다. 추적은 애플리케이션 실행 중에 생성된 특정 메시지의 게시입니다.
ms.date: 03/30/2017
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
ms.openlocfilehash: 1999cd922b9e7299cbf3c10a702eb4d2dc6c3fbb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177243"
---
# <a name="diagnostic-traces"></a>진단 추적

추적은 애플리케이션 실행 중에 생성된 특정 메시지의 게시입니다. 추적을 사용하는 경우 전송된 메시지를 수집 및 기록하는 메커니즘이 있어야 합니다. 수신기가 추적 메시지를 수신합니다. 수신기의 목적은 추적 메시지를 수집, 저장 및 라우팅하는 것입니다. 수신기는 추적 출력을 로그, 창 또는 텍스트 파일과 같은 적절한 대상에 보냅니다.  
  
 추적을 사용하면 이러한 수신기 중 하나인 <xref:System.Diagnostics.DefaultTraceListener>가 자동으로 만들어지고 초기화됩니다. 추적 출력을 추가 소스에 보내려면 추가 추적 수신기를 만들고 초기화해야 합니다. 수신기를 만들 때는 개인이 필요로 하는 내용을 반영해야 합니다. 예를 들어, 모든 추적 출력의 텍스트 레코드를 필요로 할 수도 있습니다. 이 경우에는 활성화되면 모든 출력을 새 텍스트 파일에 쓰는 수신기를 만듭니다. 반면에 애플리케이션이 실행되는 동안 출력을 보기만 할 수도 있습니다. 이 경우에는 모든 출력을 콘솔 창으로 보내는 수신기를 만들면 됩니다. <xref:System.Diagnostics.EventLogTraceListener>는 추적 출력을 이벤트 로그로 보낼 수 있고 <xref:System.Diagnostics.TextWriterTraceListener>는 추적 출력을 스트림에 쓸 수 있습니다.  
  
## <a name="enabling-tracing"></a>추적 사용  

 트랜잭션 처리 중에 추적을 사용하려면 애플리케이션의 구성 파일을 편집해야 합니다. 다음은 이에 대한 예입니다.  
  
```xml  
<configuration>  
<system.diagnostics>  
     <sources>  
          <source name="System.Transactions" switchValue="Warning">  
               <listeners>  
                    <add name="tx"
                     type="System.Diagnostics.XmlWriterTraceListener"
                     initializeData= "tx.log" />  
               </listeners>  
          </source>  
     </sources>  
</system.diagnostics>  
</configuration>  
```  
  
 <xref:System.Transactions> 추적은 "System.Transactions"라는 소스에 기록됩니다. `add`를 사용하여 사용할 추적 수신기의 이름과 형식을 지정할 수 있습니다. 예제 구성에서는 수신기 이름을 "tx"로 지정하고 표준 .NET Framework 추적 수신기(<xref:System.Diagnostics.XmlWriterTraceListener>)를 사용할 형식으로 추가했습니다. `initializeData`를 사용하여 해당 수신기의 로그 파일 이름을 설정합니다. 또한 단순한 파일 이름 대신 정규화된 경로를 사용할 수 있습니다.  
  
 각 추적 메시지 형식에 수준이 할당되어 중요도를 나타냅니다. app-domain의 추적 수준이 이벤트 형식의 수준보다 낮거나 같으면 해당 메시지가 생성됩니다. 추적 수준은 구성 파일의 `switchValue` 설정에 의해 제어됩니다. 진단 추적 메시지와 연결된 수준은 다음 표에 정의되어 있습니다.  
  
|추적 수준|설명|  
|-----------------|-----------------|  
|위험|다음과 같은 심각한 오류가 발생했습니다.<br /><br /> -사용자 기능이 즉시 손실 될 수 있는 오류입니다.<br />-기능 손실을 방지 하기 위해 관리자가 작업을 수행 해야 하는 이벤트입니다.<br />-코드가 중단 됩니다.<br />-이 추적 수준은 다른 중요 한 추적을 해석 하는 데 충분 한 컨텍스트를 제공할 수도 있습니다. 이를 통해 심각한 오류를 발생시키는 작업 시퀀스를 식별할 수 있습니다.|  
|오류|사용자 기능이 손실될 수 있는 오류(예: 잘못된 구성 또는 네트워크 동작)가 발생했습니다.|  
|경고|이후에 오류 또는 치명적인 오류를 발생시킬 수 있는 조건이 있습니다(예: 할당 실패 또는 한도 접근). 사용자 코드 오류(예: 트랜잭션 중단, 시간 초과, 인증 실패)의 정상적인 처리 중에 경고가 생성될 수도 있습니다.|  
|정보|시스템 상태 모니터링 및 진단, 성능 측정 또는 프로파일링에 유용한 메시지가 생성됩니다. 여기에는 만들어지거나 커밋되는 트랜잭션, 중요한 경계 초과 또는 중요한 리소스 할당 같은 트랜잭션 및 인리스트먼트 수명 이벤트가 포함될 수 있습니다. 개발자는 용량 계획 및 성능 관리에 이러한 정보를 활용할 수 있습니다.|  
  
## <a name="trace-codes"></a>추적 코드  

 다음 표에서는 <xref:System.Transactions> 인프라에서 생성되는 추적 코드를 보여 줍니다. 이 표에는 추적 코드 식별자, 추적 <xref:System.Diagnostics.EventTypeFilter.EventType%2A> 의 열거 수준 및 추적에 대 한 **TraceRecord** 에 포함 된 추가 데이터가 포함 되어 있습니다. 또한 추적의 해당 추적 수준도 **TraceRecord**에 저장 됩니다.  
  
|TraceCode|EventType|TraceRecord의 추가 데이터|  
|---------------|---------------|-------------------------------|  
|TransactionCreated|정보|TransactionTraceId|  
|TransactionPromoted|정보|로컬 TransactionTraceId, 분산 TransactionTraceId|  
|EnlistmentCreated|정보|TransactionTraceId, EnlistmentTraceId, EnlistmentType(durable/volatile), EnlistmentOptions|  
|EnlistmentCallbackNegative|경고|TransactionTraceId, EnlistmentTraceId,<br /><br /> Callback(forcerollback/aborted/indoubt)|  
|TransactionRollbackCalled|경고|TransactionTraceId|  
|TransactionAborted|경고|TransactionTraceId|  
|TransactionInDoubt|경고|TransactionTraceId|  
|TransactionScopeCreated|정보|TransactionScopeResult. 다음 중 하나일 수 있습니다.<br /><br /> -새 트랜잭션.<br />-트랜잭션이 전달 되었습니다.<br />-종속 트랜잭션이 전달 되었습니다.<br />-현재 트랜잭션을 사용 합니다.<br />-트랜잭션이 없습니다.<br /><br /> 새 현재 TransactionTraceId|  
|TransactionScopeDisposed|정보|범위 "예상" 현재 트랜잭션의 TransactionTraceId입니다.|  
|TransactionScopeIncomplete|경고|범위 "예상" 현재 트랜잭션의 TransactionTraceId입니다.|  
|TransactionScopeNestedIncorrectly|경고|범위 "예상" 현재 트랜잭션의 TransactionTraceId입니다.|  
|TransactionScopeCurrentTransactionChanged|경고|이전의 현재 TransactionTraceId, 기타 TransactionTraceId|  
|TransactionScopeTimeout|경고|범위 "예상" 현재 트랜잭션의 TransactionTraceId입니다.|  
|DependentCloneCreated|정보|TransactionTraceId, 만들어지는 종속 트랜잭션의 형식(RollbackIfNotComplete/BlockCommitUntilComplete)|  
|DependentCloneComplete|정보|TransactionTraceId|  
|RecoveryComplete|정보|리소스 관리자 GUID(기본 클래스로부터)|  
|Reenlist|정보|리소스 관리자 GUID(기본 클래스로부터)|  
|TransactionSerialized|정보|TransactionTraceId|  
|TransactionException|오류|예외 메시지|  
|InvalidOperationException|오류|예외 메시지|  
|InternalError|위험|예외 메시지|  
|TransferEvent||트랜잭션을 역직렬화하거나 <xref:System.Transactions> 트랜잭션에서 분산 트랜잭션으로 승격하는 경우 ExecutionContext의 현재 ActivityID 및 분산 트랜잭션 ID가 기록됩니다.<br /><br /> DTC가 관리되는 코드로 콜백되는 경우 분산 트랜잭션 ID는 콜백 기간 동안 ExecutionContext에 ActivityID로 설정됩니다.|  
|ConfiguredDefaultTimeoutAdjusted|경고|추가 데이터가 없습니다.|  
|TransactionTimeout|경고|시간 초과되는 트랜잭션의 TransactionTraceId입니다.|  
  
 앞의 각 추가 데이터 항목에 대한 XML 스키마에는 다음 형식이 있습니다.  
  
### <a name="transactiontraceidentifier"></a>TransactionTraceIdentifier  

 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `< CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `</TransactionTraceIdentifier>`  
  
### <a name="enlistmenttraceidentifier"></a>EnlistmentTraceIdentifier  

 `<EnlistmentTraceIdentifier>`  
  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `<CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<EnlistmentIdentifier>`  
  
 `the enlistment id number`  
  
 `</EnlistmentIdentifier>`  
  
 `</EnlistmentTraceIdentifier>`  
  
### <a name="resource-manager-identifier"></a>리소스 관리자 식별자  

 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
## <a name="security-issues-for-tracing"></a>추적과 관련된 보안 문제  

 관리자가 추적을 설정하면 기본적으로 공개적으로 볼 수 있는 추적 로그에 중요한 정보가 기록될 수 있습니다. 가능한 보안 위협을 줄이려면 공유 및 파일 시스템 액세스 권한에 의해 제어되는 안전한 위치에 추적 로그를 저장해야 합니다.
