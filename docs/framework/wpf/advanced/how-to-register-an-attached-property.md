---
title: 'Cómo: Registrar una propiedad asociada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
ms.openlocfilehash: e6b0b461552811c5b3fca46a11f087f710e3b2e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-register-an-attached-property"></a>Cómo: Registrar una propiedad asociada
En este ejemplo se muestra cómo registrar una propiedad adjunta y se proporcionan descriptores de acceso públicos para que pueda usar la propiedad en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] y en el código. Las propiedades adjuntas son un concepto de sintaxis que define [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. La mayoría de propiedades adjuntas para los tipos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] también se implementan como propiedades de dependencia. Puede usar las propiedades de dependencia en cualquier <xref:System.Windows.DependencyObject> tipos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo registrar una propiedad adjunta como una propiedad de dependencia, utilizando el <xref:System.Windows.DependencyProperty.RegisterAttached%2A> método. La clase de proveedor tiene la opción de proporcionar metadatos predeterminados para la propiedad que se aplica cuando la propiedad se usa en otra clase, a menos que esa clase invalide los metadatos. En este ejemplo, el valor predeterminado de la propiedad `IsBubbleSource` está establecida en `false`.  
  
 La clase de proveedor para una propiedad adjunta (incluso si no está registrada como una propiedad de dependencia) debe proporcionar descriptores de acceso get y set estáticos que siguen la convención de nomenclatura `Set`*[AttachedPropertyName]* y `Get`*[AttachedPropertyName]*. Estos descriptores de acceso son necesarios para que el lector [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pueda reconocer la propiedad como un atributo en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] y resolver los tipos pertinentes.  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.DependencyProperty>  
 [Información general sobre las propiedades de dependencia](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Propiedades de dependencia personalizadas](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Temas "Cómo..."](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
