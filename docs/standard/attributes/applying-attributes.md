---
title: 특성 적용
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET], attributes
- attributes [.NET], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 83cfb1d5b5aa3ebc8651406850a758146fd329d4
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829104"
---
# <a name="apply-attributes"></a>특성 적용

다음 프로세스를 사용하여 코드 요소에 특성을 적용합니다.

1. 새 특성을 정의하거나 기존 .NET 특성을 사용합니다.

2. 코드 요소 바로 앞에 특성을 배치하여 이 요소에 해당 특성을 적용합니다.

     각 언어마다 고유한 특성 구문이 있습니다. C++ 및 C#의 경우 특성은 대괄호로 묶고, 공백으로 요소와 구분되며, 줄 바꿈 문자를 사용할 수 있습니다. Visual Basic의 경우 특성은 꺾쇠 괄호로 묶고, 같은 논리 줄에 있어야 합니다. 줄 바꿈이 필요하면 줄 연속 문자를 사용할 수 있습니다.

3. 특성에 대한 위치 매개 변수와 명명된 매개 변수를 지정합니다.

     *위치* 매개 변수는 필수 요소로서 명명된 매개 변수 앞에 와야 하며, 특성의 생성자 중 하나의 매개 변수에 해당합니다. *명명된* 매개 변수는 선택적 요소이며, 특성의 읽기/쓰기 속성에 해당합니다. C++ 및 C#의 경우 각 선택적 매개 변수에 `name=value`를 지정합니다. 여기서 `name`은 속성의 이름입니다. Visual Basic의 경우 `name:=value`를 지정합니다.

 특성은 코드를 컴파일할 때 메타데이터로 내보내지며, 공용 언어 런타임과 사용자 지정 도구 또는 애플리케이션에서 런타임 리플렉션 서비스를 통해 사용할 수 있습니다.

 모든 특성 이름은 규칙에 따라 "Attribute"로 끝납니다. 하지만 런타임을 목적으로 하는 일부 언어(예: Visual Basic 및 C#)에서는 특성의 전체 이름을 지정할 필요가 없습니다. 예를 들어 <xref:System.ObsoleteAttribute?displayProperty=nameWithType>를 초기화하려는 경우 **Obsolete** 로만 참조해야 합니다.

## <a name="apply-an-attribute-to-a-method"></a>메서드에 특성 적용

 다음 코드 예제에서는 코드를 오래된 것으로 표시하는 **System.ObsoleteAttribute** 를 사용하는 방법을 보여줍니다. `"Will be removed in next version"` 문자열이 특성에 전달됩니다. 이 특성이 설명하는 코드가 호출되면 이 특성으로 인해 전달된 문자열을 표시하는 컴파일러 경고가 발생합니다.

 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]

## <a name="apply-attributes-at-the-assembly-level"></a>어셈블리 수준에서 특성 적용

 어셈블리 수준에서 특성을 적용하려면 `assembly`(Visual Basic에서는 `Assembly`) 키워드를 사용합니다. 다음 코드에서는 어셈블리 수준에서 적용된 **AssemblyTitleAttribute** 를 보여 줍니다.

 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]

 이 특성을 적용하면 `"My Assembly"` 문자열이 해당 파일의 메타데이터 부분에 있는 어셈블리 매니페스트에 배치됩니다. [Ildasm.exe(MSIL 디스어셈블러)](../../framework/tools/ildasm-exe-il-disassembler.md)를 사용하거나 특성을 검색하는 사용자 지정 프로그램을 만들어 이 특성을 볼 수 있습니다.

## <a name="see-also"></a>참고 항목

- [특성](index.md)
- [특성에 저장된 정보 검색](retrieving-information-stored-in-attributes.md)
- [개념](/cpp/windows/attributed-programming-concepts)
- [특성(C#)](../../csharp/programming-guide/concepts/attributes/index.md)
- [특성 개요(Visual Basic)](../../visual-basic/programming-guide/concepts/attributes/index.md)
