---
title: ICorProfilerInfo2::GetAppDomainStaticAddress 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
ms.openlocfilehash: 271f9f4fd0d85407aedf088ffb524fa6e0398e37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727213"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a>ICorProfilerInfo2::GetAppDomainStaticAddress 메서드

지정 된 응용 프로그램 도메인의 범위에 있는 지정 된 응용 프로그램 도메인 정적 필드의 주소를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>매개 변수  

 `classId`  
 진행 요청 된 응용 프로그램 도메인 정적 필드를 포함 하는 클래스의 클래스 ID입니다.  
  
 `fieldToken`  
 진행 요청 된 응용 프로그램 도메인 정적 필드에 대 한 메타 데이터 토큰입니다.  
  
 `appDomainId`  
 진행 요청 된 정적 필드의 범위에 해당 하는 응용 프로그램 도메인의 ID입니다.  
  
 `ppAddress`  
 제한이 지정 된 응용 프로그램 도메인 내에 있는 정적 필드의 주소에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  

 `GetAppDomainStaticAddress`메서드는 다음 중 하나를 반환할 수 있습니다.  
  
- 지정 된 컨텍스트에서 지정 된 정적 필드에 주소가 할당 되지 않은 경우 HRESULT CORPROF_E_DATAINCOMPLETE입니다.  
  
- 가비지 컬렉션 힙에 있을 수 있는 개체의 주소입니다. 이러한 주소는 가비지 수집 후에 무효화 될 수 있으므로 가비지 수집 후 프로파일러는 이러한 주소를 유효한 것으로 가정 하지 않아야 합니다.  
  
 클래스의 클래스 생성자가 완료 되기 전에는 `GetAppDomainStaticAddress` 모든 정적 필드에 대 한 CORPROF_E_DATAINCOMPLETE를 반환 하지만, 일부 정적 필드는 이미 초기화 되 고 가비지 수집 개체를 루 팅 하 고 있을 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICorProfilerInfo 인터페이스](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 인터페이스](icorprofilerinfo2-interface.md)
