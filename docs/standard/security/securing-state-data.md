---
title: 상태 데이터 보안
description: 상태 데이터를 private 또는 internal 변수로 선언 하 여 액세스를 제한 합니다. 이러한 데이터는 리플렉션, serialization 및 디버깅을 통해 여전히 액세스할 수 있습니다.
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: 849ed993befaceda1b04becbb7fb2530c5c62a77
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824163"
---
# <a name="securing-state-data"></a>상태 데이터 보안

중요한 데이터를 처리하거나 보안 관련 사항을 결정해야 하는 애플리케이션에서는 데이터를 자체적으로 제어해야 하며 악성 코드가 데이터에 직접 액세스하지 못하게 해야 합니다. 데이터를 메모리에서 보호하는 최상의 방법은 데이터를 동일한 어셈블리로 제한된 범위 사용하여 private 또는 internal 변수로 선언하는 것입니다. 그러나 이 데이터도 다음과 같이 액세스할 수 있습니다.  
  
- 리플렉션 메커니즘을 사용하면 개체를 참조할 수 있는 매우 신뢰되는 코드가 전용 멤버를 얻고 설정할 수 있습니다.  
  
- serialization을 사용하면 매우 신뢰되는 코드가 serialize된 형식의 개체에서 해당 데이터에 액세스할 수 있을 경우 효과적으로 전용 멤버를 얻고 설정할 수 있습니다.  
  
- 디버깅할 때 이 데이터를 읽을 수 있습니다.  
  
 따라서 메서드나 속성이 실수로 해당 값을 노출하지 않도록 해야 합니다.  
  
## <a name="see-also"></a>참고 항목

- [보안 코딩 지침](secure-coding-guidelines.md)
- [ASP.NET Core 보안](/aspnet/core/security/)
