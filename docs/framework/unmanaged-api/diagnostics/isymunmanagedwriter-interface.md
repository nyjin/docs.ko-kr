---
title: ISymUnmanagedWriter 인터페이스
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
ms.openlocfilehash: fddfd2a163f6e6513b648ee0b724c0b5bd54c81a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722936"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter 인터페이스

기호 작성기를 나타내며 문서, 시퀀스 포인트, 어휘 범위 및 변수를 정의하는 메서드를 제공합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[Abort 메서드](isymunmanagedwriter-abort-method.md)|기호를 기호 저장소에 커밋하지 않고 기호 작성기를 닫습니다.|  
|[Close 메서드](isymunmanagedwriter-close-method.md)|기호를 기호 저장소에 커밋한 후 기호 작성기를 닫습니다.|  
|[CloseMethod 메서드](isymunmanagedwriter-closemethod-method.md)|현재 메서드를 닫습니다. 메서드를 닫은 후에는 더 이상 기호를 정의할 수 없습니다.|  
|[CloseNamespace 메서드](isymunmanagedwriter-closenamespace-method.md)|가장 최근에 열린 네임 스페이스를 닫습니다.|  
|[CloseScope 메서드](isymunmanagedwriter-closescope-method.md)|현재 어휘 범위를 닫습니다.|  
|[DefineConstant 메서드](isymunmanagedwriter-defineconstant-method.md)|상수 값의 이름을 정의 합니다.|  
|[DefineDocument 메서드](isymunmanagedwriter-definedocument-method.md)|소스 문서를 정의합니다.|  
|[DefineField 메서드](isymunmanagedwriter-definefield-method.md)|메서드 내에 없는 단일 변수를 정의 합니다.|  
|[DefineGlobalVariable 메서드](isymunmanagedwriter-defineglobalvariable-method.md)|단일 전역 변수를 정의합니다.|  
|[DefineLocalVariable 메서드](isymunmanagedwriter-definelocalvariable-method.md)|현재 어휘 범위에 단일 변수를 정의합니다.|  
|[DefineParameter 메서드](isymunmanagedwriter-defineparameter-method.md)|현재 메서드의 단일 매개 변수를 정의합니다.|  
|[DefineSequencePoints 메서드](isymunmanagedwriter-definesequencepoints-method.md)|현재 메서드 내에서 시퀀스 위치 그룹을 정의합니다.|  
|[GetDebugInfo 메서드](isymunmanagedwriter-getdebuginfo-method.md)|컴파일러가 PE (이식 가능한 실행) 파일 헤더에 디버그 디렉터리 항목을 쓰는 데 필요한 정보를 반환 합니다.|  
|[Initialize 메서드](isymunmanagedwriter-initialize-method.md)|이 작성기를 연결할 메타 데이터 내보내기 인터페이스를 설정 하 고 디버깅 기호를 쓸 출력 파일 이름을 설정 합니다.|  
|[Initialize2 메서드](isymunmanagedwriter-initialize2-method.md)|이 작성기를 연결할 메타 데이터 내보내기 인터페이스를 설정 하 고, 디버깅 기호가 쓰여질 출력 파일 이름을 설정 하 고, PDB (프로그램 데이터베이스) 파일의 최종 위치를 설정 합니다.|  
|[OpenMethod 메서드](isymunmanagedwriter-openmethod-method.md)|기호 정보를 내보내는 메서드를 엽니다.|  
|[OpenNamespace 메서드](isymunmanagedwriter-opennamespace-method.md)|새 네임스페이스를 엽니다.|  
|[OpenScope 메서드](isymunmanagedwriter-openscope-method.md)|현재 메서드에서 새 어휘 범위를 엽니다.|  
|[RemapToken 메서드](isymunmanagedwriter-remaptoken-method.md)|메타 데이터를 내보낼 때 메타 데이터 토큰이 다시 매핑되고 있음을 기호 작성기에 알립니다.|  
|[SetMethodSourceRange 메서드](isymunmanagedwriter-setmethodsourcerange-method.md)|소스 파일 내에서 메서드의 실제 시작과 끝을 지정합니다.|  
|[SetScopeRange 메서드](isymunmanagedwriter-setscoperange-method.md)|지정된 어휘 범위에 대한 오프셋 범위를 정의합니다.|  
|[SetSymAttribute 메서드](isymunmanagedwriter-setsymattribute-method.md)|이름에 따라 사용자 지정 특성을 정의 합니다.|  
|[SetUserEntryPoint 메서드](isymunmanagedwriter-setuserentrypoint-method.md)|이 모듈의 진입점인 사용자 정의 메서드를 지정 합니다.|  
|[UsingNamespace 메서드](isymunmanagedwriter-usingnamespace-method.md)|지정 된 정규화 된 네임 스페이스 이름이 현재 열려 있는 어휘 범위 내에서 사용 되 고 있음을 지정 합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **헤더:** CorSym, CorSym  
  
## <a name="see-also"></a>참조

- [진단 기호 저장소 인터페이스](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 인터페이스](isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 인터페이스](isymunmanagedwriter3-interface.md)
