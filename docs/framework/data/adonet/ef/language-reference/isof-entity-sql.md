---
title: ISOF(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 3cbbc9b6feda1bde104ed2c95d4dca274b090028
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202281"
---
# <a name="isof-entity-sql"></a>ISOF(Entity SQL)

식의 형식이 지정된 형식 또는 그 하위 형식인지 여부를 확인합니다.  
  
## <a name="syntax"></a>구문  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>인수  

 `expression`  
 형식을 결정할 수 있는 모든 유효한 쿼리 식입니다.  
  
 NOT  
 IS OF의 EDM.Boolean 결과를 부정합니다.  
  
 ONLY  
 `true`이 `expression` 형식이며 그 하위 형식이 아닌 경우에만 IS OF가 `type`를 반환하도록 지정합니다.  
  
 `type`  
 `expression`을 테스트할 형식입니다. 형식은 네임스페이스로 한정되어야 합니다.  
  
## <a name="return-value"></a>반환 값  

 `true`이 T 형식이며 T가 기본 형식이거나 `expression`의 파생 형식인 경우 `type`이고, `expression`이 런타임에 null인 경우 null이며, 그 이외의 경우 `false`입니다.  
  
## <a name="remarks"></a>설명  

 식 `expression IS NOT OF (type)` 과는 `expression IS NOT OF (ONLY type)` 각각 및에 구문적으로 동일 `NOT (expression IS OF (type))` `NOT (expression IS OF (ONLY type))` 합니다.  
  
 다음 표에서는 일반 패턴 및 비교적 특수한 패턴에 대한 `IS OF` 연산자의 동작을 보여 줍니다. 공급자 호출 이전에 모든 예외가 클라이언트 측에서 throw됩니다.  
  
|무늬|동작|  
|-------------|--------------|  
|null IS OF(EntityType)|되거나|  
|null IS OF(ComplexType)|되거나|  
|null IS OF(RowType)|되거나|  
|TREAT(null AS EntityType) IS OF(EntityType)|DBNull 반환|  
|TREAT(null AS ComplexType) IS OF(ComplexType)|되거나|  
|TREAT(null AS RowType) IS OF(RowType)|되거나|  
|EntityType IS OF(EntityType)|true/false 반환|  
|ComplexType IS OF(ComplexType)|되거나|  
|RowType IS OF(RowType)|되거나|  
  
## <a name="example"></a>예제  

 다음 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 쿼리에서는 IS OF 연산자를 사용하여 쿼리 식의 형식을 결정한 다음 TREAT 연산자를 사용하여 Course 형식의 개체를 OnsiteCourse 형식의 개체 컬렉션으로 변환합니다. 쿼리는 [School 모델](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))을 기반으로 합니다.  
  
 [! 코드-sql [DP EntityServices 개념 # TREAT_ISOF] ~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices 개념/tsql/entityservices .sql # treat_isof)]  
  
## <a name="see-also"></a>참고 항목

- [엔터티 SQL 참조](entity-sql-reference.md)
