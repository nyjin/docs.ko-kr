---
title: '방법: 관찰자 구현'
description: .NET에서 관찰자를 구현합니다. 관찰자 디자인 패턴에서는 알림에 등록하는 관찰자와 공급자 간에 구분이 필요합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET], observer design pattern
- observer design pattern [.NET], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
ms.openlocfilehash: bfd595cec8e499b760f75f614bd0a61b031eb207
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828337"
---
# <a name="how-to-implement-an-observer"></a>방법: 관찰자 구현
관찰자 디자인 패턴은 알림에 등록하는 관찰자와 데이터를 모니터링하고 하나 이상의 관찰자에게 알림을 보내는 공급자 간에 구분이 필요합니다. 이 항목에서는 관찰자를 만드는 방법을 설명합니다. 관련 항목인 [방법: 공급자 구현](how-to-implement-a-provider.md)에서는 공급자를 만드는 방법을 설명합니다.  
  
### <a name="to-create-an-observer"></a>관찰자를 만들려면  
  
1. <xref:System.IObserver%601?displayProperty=nameWithType> 인터페이스를 구현하는 형식인 관찰자를 정의합니다. 예를 들어 다음 코드에서는 `Temperature`의 제네릭 형식 인수를 사용하여 구성된 <xref:System.IObserver%601?displayProperty=nameWithType> 구현인 `TemperatureReporter`라는 형식을 정의합니다.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. 공급자가 해당 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> 구현을 호출하기 전에 관찰자가 알림 수신을 중지할 수 있는 경우 공급자의 <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> 메서드에서 반환한 <xref:System.IDisposable> 구현을 유지할 private 변수를 정의합니다. 또한 공급자의 <xref:System.IObservable%601.Subscribe%2A> 메서드를 호출하고 반환된 <xref:System.IDisposable> 개체를 저장하는 구독 메서드도 정의해야 합니다. 예를 들어 다음 코드는 `unsubscriber`라는 private 변수를 정의하고, 공급자의 <xref:System.IObservable%601.Subscribe%2A> 메서드를 호출하고 반환된 개체를 `unsubscriber` 변수에 할당하는 `Subscribe` 메서드를 정의합니다.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. 이 기능이 필수인 경우 공급자가 해당 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> 구현을 호출하기 전에 관찰자가 알림 수신을 중지할 수 있게 하는 메서드를 정의합니다. 다음 예제에서는 `Unsubscribe` 메서드를 정의합니다.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. <xref:System.IObserver%601> 인터페이스로 정의된 세 가지 메서드 즉, <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> 및 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>의 구현을 지정합니다. 공급자 및 애플리케이션의 필요에 따라 <xref:System.IObserver%601.OnError%2A> 및 <xref:System.IObserver%601.OnCompleted%2A> 메서드가 스텁 구현일 수 있습니다. <xref:System.IObserver%601.OnError%2A> 메서드는 전달된 <xref:System.Exception> 개체를 예외로 처리해서는 안 되며, <xref:System.IObserver%601.OnCompleted%2A> 메서드는 공급자의 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 구현을 자유롭게 호출할 수 있어야 합니다. 다음 예제에서는 `TemperatureReporter` 클래스의 <xref:System.IObserver%601> 구현을 보여줍니다.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>예제  
 다음 예제에는 온도 모니터링 애플리케이션에 대한 <xref:System.IObserver%601> 구현을 제공하는 `TemperatureReporter` 클래스의 전체 소스 코드가 포함되어 있습니다.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>참조

- <xref:System.IObserver%601>
- [관찰자 디자인 패턴](observer-design-pattern.md)
- [방법: 공급자 구현](how-to-implement-a-provider.md)
- [관찰자 디자인 패턴 유용한 정보](observer-design-pattern-best-practices.md)
