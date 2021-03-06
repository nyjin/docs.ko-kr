---
title: 문자열 마샬링
description: 문자열을 마샬링하는 방법을 살펴봅니다. 값별 또는 참조별 구조체 또는 클래스에서 결과로 값별 또는 참조별 문자열을 마샬링하는 옵션 등에 대해 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
ms.openlocfilehash: 11925e3e126620788bb09e90e4d2528dbaf56581
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547768"
---
# <a name="marshaling-strings"></a>문자열 마샬링
플랫폼 호출은 문자열 매개 변수를 복사하고 필요한 경우 .NET Framework 형식(유니코드)을 관리되지 않는 형식(ANSI)으로 변환합니다. 관리되는 문자열은 변경할 수 없으므로 함수가 반환할 때 플랫폼 호출을 통해 해당 문자열을 관리되지 않는 메모리에서 관리되는 메모리로 다시 복사하지 않습니다.  
  
 다음 표에서는 문자열에 대한 마샬링 옵션을 나열하고 용도를 설명하며 해당하는 .NET Framework 샘플에 대한 링크를 제공합니다.  
  
|String|설명|예제|  
|------------|-----------------|------------|  
|값.|문자열을 In 매개 변수로 전달합니다.|[MsgBox](msgbox-sample.md)|  
|결과.|비관리 코드에서 문자열을 반환합니다.|[문자열](/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|참조.|<xref:System.Text.StringBuilder>를 사용하여 In/Out 매개 변수로 문자열을 전달합니다.|[버퍼](/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))|  
|값 방식 구조체.|In 매개 변수에 있는 구조체에 문자열을 전달합니다.|[구조체](/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100))|  
|참조 방식 구조체 **(char\*)** .|In/Out 매개 변수에 있는 구조체에 문자열을 전달합니다. 관리되지 않는 함수에는 문자 버퍼에 대한 포인터가 필요하며 버퍼 크기는 구조체의 멤버입니다.|[문자열](/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|참조 방식 구조체 **(char[])** .|In/Out 매개 변수에 있는 구조체에 문자열을 전달합니다. 관리되지 않는 함수에는 포함된 문자 버퍼가 있어야 합니다.|[OSInfo](/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|값 방식 클래스 **(char\*)** .|클래스에 문자열을 전달합니다(클래스는 In/Out 매개 변수임). 관리되지 않는 함수에는 문자 버퍼에 대한 포인터가 있어야 합니다.|[OpenFileDlg](/previous-versions/dotnet/netframework-4.0/w5tyztk9(v=vs.100))|  
|값 방식 클래스 **(char[])** .|클래스에 문자열을 전달합니다(클래스는 In/Out 매개 변수임). 관리되지 않는 함수에는 포함된 문자 버퍼가 있어야 합니다.|[OSInfo](/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|값 형식 문자열 배열.|값으로 전달되는 문자열의 배열을 만듭니다.|[배열](marshaling-different-types-of-arrays.md)|  
|값 형식 문자열을 포함하는 구조체의 배열.|문자열을 포함하는 구조체의 배열을 만들고 배열을 값으로 전달합니다.|[배열](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>참조

- [문자열에 대한 기본 마샬링](default-marshaling-for-strings.md)
- [플랫폼 호출을 사용하여 데이터 마샬링](marshaling-data-with-platform-invoke.md)
- [클래스, 구조체 및 공용 구조체 마샬링](marshaling-classes-structures-and-unions.md)
- [여러 형식의 배열 마샬링](marshaling-different-types-of-arrays.md)
- [기타 마샬링 샘플](/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
