---
title: 'ICorDebugVariableHome:: GetOffset 메서드'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
ms.openlocfilehash: c5d491b66e4ec64dffa4e19dabff876c9c473036
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711795"
---
# <a name="icordebugvariablehomegetoffset-method"></a>ICorDebugVariableHome:: GetOffset 메서드

변수에 대 한 기본 레지스터에서 오프셋을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pOffset`  
 제한이 기본 레지스터의 오프셋입니다.  
  
## <a name="return-value"></a>반환 값  

 메서드는 다음 값을 반환 합니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|변수가 등록 관련 메모리 위치에 있습니다.|  
|`E_FAIL`|변수가 등록 관련 메모리 위치에 없습니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICorDebugVariableHome 인터페이스](icordebugvariablehome-interface.md)
