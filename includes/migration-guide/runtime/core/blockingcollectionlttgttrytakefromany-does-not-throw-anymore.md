---
ms.openlocfilehash: 277a91fbfbf0c6aaaa0dc044ef0c079ad8607699
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497855"
---
### <a name="blockingcollectionlttgttrytakefromany-does-not-throw-anymore"></a>BlockingCollection&lt;T&gt;.TryTakeFromAny는 더 이상 throw하지 않습니다.

#### <a name="details"></a>설명

입력 컬렉션 중 하나가 완료됨으로 표시될 경우 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)>은 더이상 -1을 반환하지 않고 <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)>는 더 이상 예외를 throw하지 않습니다. 이러한 변경을 통해 컬렉션 중 하나가 비어 있거나 완료되었더라도 나머지 컬렉션에는 검색할 수 있는 항목이 아직 있는 경우 컬렉션을 사용할 수 있습니다.

#### <a name="suggestion"></a>제안 해결 방법

차단 컬렉션 완료 시 제어 흐름 목적으로 -1을 반환하는 TryTakeFromAny 또는 throw하는 TakeFromAny가 사용된 경우, 이러한 코드는 <code>.Any(b =&gt; b.IsCompleted)</code>를 사용하도록 변경되어 해당 조건을 검색하도록 해야 합니다.

| 이름    | 값       |
|:--------|:------------|
| Scope   |부|
|버전|4.5|
|형식|런타임|

#### <a name="affected-apis"></a>영향을 받는 API

- <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Int32)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Concurrent.BlockingCollection`1.TakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.Threading.CancellationToken)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.Int32)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.TimeSpan)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.TimeSpan)``

-->
