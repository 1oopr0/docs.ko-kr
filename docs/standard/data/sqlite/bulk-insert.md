---
title: 대량 삽입
ms.date: 12/13/2019
description: 데이터베이스에 대해 여러 변경 작업을 수행할 때 사용할 수 있는 성능 팁입니다.
ms.openlocfilehash: 9d87d5c8d70f8e70479f9aa02b7802f73b88de9e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75450299"
---
# <a name="bulk-insert"></a>대량 삽입

SQLite에는 데이터를 대량 삽입하는 특별한 방법이 없습니다. 데이터를 삽입하거나 업데이트할 때 최적의 성능을 얻으려면 다음을 수행해야 합니다.

- 트랜잭션을 사용하세요.
- 동일한 매개 변수화된 명령을 다시 사용하세요. 이후 실행은 첫 번째 실행의 컴파일을 다시 사용합니다.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BulkInsertSample/Program.cs?name=snippet_BulkInsert)]
