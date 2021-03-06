---
title: ISymUnmanagedDocument::GetCheckSum 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
ms.openlocfilehash: 4030da31400b7075952d146e5d6740306863e9ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721090"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a>ISymUnmanagedDocument::GetCheckSum 메서드

체크섬을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>매개 변수  

 `cData`  
 진행 매개 변수에서 제공 하는 버퍼의 길이입니다. `data`  
  
 `pcData`  
 제한이 체크섬의 크기 및 길이 (바이트)입니다.  
  
 `data`  
 제한이 체크섬을 수신 하는 버퍼입니다.  
  
## <a name="return-value"></a>반환 값  

 메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 오류 코드입니다.  
  
## <a name="see-also"></a>참조

- [ISymUnmanagedDocument 인터페이스](isymunmanageddocument-interface.md)
