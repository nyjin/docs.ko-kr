---
title: 디버깅 전역 정적 함수
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: 04906322e311b580abddeca7744cf3e75d471e05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722988"
---
# <a name="debugging-global-static-functions"></a>디버깅 전역 정적 함수

이 섹션에서는 디버깅 API에서 사용하는 관리되지 않는 전역 정적 함수에 대해 설명합니다.  
  
## <a name="in-this-section"></a>섹션 내용  

 [_EFN_GetManagedExcepStack 함수](efn-getmanagedexcepstack-function.md)  
 관리되는 예외 개체 주소를 제공하면 내부에 포함된 스택 추적의 문자열 버전을 반환합니다.  
  
 [_EFN_GetManagedObjectFieldInfo 함수](efn-getmanagedobjectfieldinfo-function.md)  
 제공된 개체 포인터와 필드 이름을 사용하여 개체 시작부터 필드 및 필드 값까지의 오프셋을 가져옵니다.  
  
 [_EFN_GetManagedObjectName 함수](efn-getmanagedobjectname-function.md)  
 제공된 관리되는 개체 포인터를 사용하여 형식 이름을 가져옵니다.  
  
 [_EFN_StackTrace 함수](efn-stacktrace-function.md)  
 비관리 코드와 관리 코드 간 각 전환에 대해 하나씩, `CONTEXT` 레코드 배열 및 관리되는 스택 추적의 텍스트 표시를 제공합니다.  
  
 [CLRDataCreateInstance 함수](clrdatacreateinstance-function.md)  
 지정된 대상 프로세스에 대한 지정된 인터페이스 개체를 만들려고 CLR(공용 언어 런타임) 데이터 액세스 서비스에 의해 호출됩니다.  
  
 [PFN_CLRDataCreateInstance 함수 포인터](pfn-clrdatacreateinstance-function-pointer.md)  
 지정된 대상 프로세스에 대한 지정된 인터페이스 개체를 만들려고 CLR 데이터 액세스 서비스에 의해 호출되는 함수를 가리킵니다.  
  
## <a name="related-sections"></a>관련 단원  

 [디버깅 Coclass](debugging-coclasses.md)  
  
 [디버깅 인터페이스](debugging-interfaces.md)  
  
 [디버깅 열거형](debugging-enumerations.md)  
  
 [디버깅 구조체](debugging-structures.md)
