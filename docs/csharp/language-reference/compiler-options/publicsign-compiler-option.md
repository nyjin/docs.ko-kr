---
description: -publicsign(C# 컴파일러 옵션)
title: -publicsign(C# 컴파일러 옵션)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 525912c7f50aa6b51e602be7b9258f1f5907daac
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124814"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign(C# 컴파일러 옵션)

이 옵션을 사용하면 컴파일러는 공개 키를 적용하지만 실제로 어셈블리에 서명하지 않습니다. 또한 **-publicsign** 옵션은 파일이 실제로 서명되었음을 런타임에 알리는 비트를 어셈블리에 설정합니다.

## <a name="syntax"></a>구문

```console
-publicsign
```

## <a name="arguments"></a>인수

없음

## <a name="remarks"></a>설명

**-publicsign** 옵션에는 [-keyfile](keyfile-compiler-option.md) 또는 [-keycontainer](keycontainer-compiler-option.md)를 사용해야 합니다. **keyfile** 또는 **keycontainer** 옵션은 공개 키를 지정합니다.

**-publicsign** 및 **-delaysign** 옵션은 함께 사용할 수 없습니다.

“모조 서명” 또는 “OSS 서명”이라고도 하는 퍼블릭 서명은 출력 어셈블리에 퍼블릭 키를 포함하고 “서명된” 플래그를 설정하지만 프라이빗 키를 사용하여 어셈블리에 실제로 서명하지는 않습니다. 이 서명은 릴리스된 “완전히 서명된” 어셈블리와 호환되지만 어셈블리 서명에 사용된 프라이빗 키에는 액세스할 수 없는 어셈블리를 빌드하려는 오픈 소스 프로젝트에 유용합니다. 어셈블리가 완전히 서명되었는지 실제로 확인해야 하는 소비자는 거의 없으므로 완전히 서명된 어셈블리가 사용되는 거의 모든 시나리오에서 이러한 공개적으로 빌드된 어셈블리를 사용할 수 있습니다.

### <a name="to-set-this-compiler-option-in-a-csproj-file"></a>csproj 파일에서 이 컴파일러 옵션을 설정하는 방법

프로젝트에 대한 .csproj 파일을 열고 다음 요소를 추가합니다.

```xml
<PublicSign>true</PublicSign>
```

## <a name="see-also"></a>참고 항목

- [C# 컴파일러 -delaysign 옵션](delaysign-compiler-option.md)
- [C# 컴파일러 -keyfile 옵션](keyfile-compiler-option.md)
- [C# 컴파일러 -keycontainer 옵션](keycontainer-compiler-option.md)
- [C# 컴파일러 옵션](index.md)
- [프로젝트 및 솔루션 속성 관리](/visualstudio/ide/managing-project-and-solution-properties)
