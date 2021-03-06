---
title: ISymUnmanagedENCUpdate::UpdateMethodLines 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
ms.openlocfilehash: 99499b8717f219616b6b368e6393b4b7ca0a79d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699588"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a>ISymUnmanagedENCUpdate::UpdateMethodLines 메서드

다시 컴파일되지 않았지만 해당 줄이 독립적으로 이동 된 메서드에 대 한 줄 정보를 업데이트할 수 있습니다. 각 문에 대 한 델타를 사용할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a>매개 변수  

 `mdMethodToken`  
 진행 메서드 토큰의 메타 데이터입니다.  
  
 `pDeltas`  
 진행 `INT32` 메서드의 각 시퀀스 위치에 대 한 델타를 나타내는 값의 배열입니다.  
  
 `cDeltas`  
 진행 `ULONG` 매개 변수의 크기를 포함 하는 `pDeltas` 입니다.  
  
## <a name="return-value"></a>반환 값  

 메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.  
  
## <a name="requirements"></a>요구 사항  

 **헤더:** CorSym, CorSym  
  
## <a name="see-also"></a>참조

- [ISymUnmanagedENCUpdate 인터페이스](isymunmanagedencupdate-interface.md)
