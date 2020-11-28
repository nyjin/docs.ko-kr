---
title: 트랜잭션
ms.date: 09/08/2020
description: 트랜잭션을 사용하는 방법을 알아봅니다.
ms.openlocfilehash: 50c4cd1023eac892cafc3ae4395e9168bd8e9f36
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678864"
---
# <a name="transactions"></a>의

트랜잭션을 사용하면 여러 SQL 문을 하나의 원자 단위로 데이터베이스에 커밋된 단일 작업 단위로 그룹화할 수 있습니다. 트랜잭션의 명령문이 실패하면 이전 명령문에서 변경한 내용을 롤백할 수 있습니다. 트랜잭션이 시작될 때 데이터베이스의 초기 상태는 유지됩니다. 트랜잭션을 사용하면 데이터베이스를 동시에 여러 번 변경할 때 SQLite의 성능을 개선할 수도 있습니다.

## <a name="concurrency"></a>동시성

SQLite에서는 한 번에 하나의 트랜잭션만 데이터베이스에 보류 중인 변경 내용을 포함할 수 있습니다. 이로 인해 다른 트랜잭션을 완료하는 데 시간이 너무 오래 걸리면 <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> 및 <xref:Microsoft.Data.Sqlite.SqliteCommand>의 `Execute` 메서드에 대한 호출이 시간 초과될 수 있습니다.

잠금, 다시 시도 및 시간 제한에 대한 자세한 내용은 [데이터 베이스 오류](database-errors.md)를 참조하세요.

## <a name="isolation-levels"></a>격리 수준

트랜잭션은 기본적으로 SQLite에서 **직렬화 가능**입니다. 이 격리 수준은 트랜잭션 내에서 수행된 모든 변경 내용이 완전히 격리되도록 보장합니다. 트랜잭션 외부에서 실행된 다른 명령문은 트랜잭션의 변경 내용에 의해 영향을 받지 않습니다.

SQLite는 공유 캐시를 사용할 때 **커밋되지 않은 읽기**도 지원합니다. 이 수준은 커밋되지 않은 데이터 읽기, 반복되지 않는 읽기 및 팬텀을 허용합니다.

- 한 트랜잭션에서 보류 중인 변경 내용이 트랜잭션 외부의 쿼리에 의해 반환될 때 *커밋되지 않은 데이터 읽기*가 발생하지만 트랜잭션의 변경 내용은 롤백됩니다. 결과에는 실제로 데이터베이스에 커밋되지 않은 데이터가 포함됩니다.

- *반복되지 않는 읽기*는 트랜잭션이 동일한 행을 두 번 쿼리할 때 발생하지만 다른 트랜잭션에 의해 두 쿼리 간에 변경되었기 때문에 결과가 다릅니다.

- *팬텀*은 트랜잭션 중에 쿼리의 where 절을 충족하기 위해 변경되거나 추가되는 행입니다. 허용되는 경우 동일한 트랜잭션에서 두 번 실행될 때 동일한 쿼리가 다른 행을 반환할 수 있습니다.

Microsoft.Data.Sqlite는 <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A>에 전달된 IsolationLevel을 최소 수준으로 취급합니다. 실제 격리 수준은 커밋되지 않은 읽기 또는 직렬화 가능 수준으로 승격됩니다.

다음 코드는 커밋되지 않은 데이터 읽기를 시뮬레이션합니다. 참고: 연결 문자열에는 `Cache=Shared`가 포함되어야 합니다.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DirtyReadSample/Program.cs?name=snippet_DirtyRead)]

## <a name="deferred-transactions"></a>지연된 트랜잭션

Microsoft.Data.Sqlite 버전 5.0부터는 트랜잭션이 지연될 수 있습니다. 이렇게 되면 첫 번째 명령이 실행될 때까지 데이터베이스에서 실제 트랜잭션 생성이 지연됩니다. 또한 해당 명령에서 필요한 경우 트랜잭션이 점진적으로 읽기 트랜잭선에서 쓰기 트랜잭션으로 업그레이드됩니다. 트랜잭션 도중에 데이터베이스에 대한 동시 액세스를 사용하도록 설정하는 데 유용할 수 있습니다.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DeferredTransactionSample/Program.cs?name=snippet_DeferredTransaction)]

> [!WARNING]
> 데이터베이스가 잠겨 있는 동안 트랜잭션이 읽기 트랜잭션에서 쓰기 트랜잭션으로 업그레이드되는 경우 지연된 트랜잭션 내의 명령이 실패할 수 있습니다. 이 경우 애플리케이션은 전체 트랜잭션을 다시 시도해야 합니다.
