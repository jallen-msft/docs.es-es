---
title: 'Cómo: Aplicar propiedades de expansión al contenido de un Viewbox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StretchDirection properties [WPF]
- Stretch properties [WPF]
- controls [WPF], Viewbox
- Viewbox control [WPF]
ms.assetid: b9c22ef4-bce4-4300-9e0c-8260b7db83cc
ms.openlocfilehash: 3e81ec9fd045bb3fcf359943e455d2cce94aec55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-stretch-properties-to-the-contents-of-a-viewbox"></a>Cómo: Aplicar propiedades de expansión al contenido de un Viewbox
## <a name="example"></a>Ejemplo  
 Este ejemplo muestra cómo cambiar el valor de la <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> y <xref:System.Windows.Controls.Viewbox.Stretch%2A> propiedades de un <xref:System.Windows.Controls.Viewbox>.  
  
 El primer ejemplo utiliza [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para definir un <xref:System.Windows.Controls.Viewbox> elemento. Asigna un <xref:System.Windows.FrameworkElement.MaxWidth%2A> y <xref:System.Windows.FrameworkElement.MaxHeight%2A> de 400. El ejemplo anida una <xref:System.Windows.Controls.Image> elemento dentro de la <xref:System.Windows.Controls.Viewbox>. <xref:System.Windows.Controls.Button> elementos que corresponden a los valores de propiedad para el <xref:System.Windows.Controls.Viewbox.Stretch%2A> y <xref:System.Windows.Controls.StretchDirection> enumeraciones manipulan el comportamiento de ajuste de las anidadas <xref:System.Windows.Controls.Image>.  
  
 [!code-xaml[viewboxStretchLayoutSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml#1)]  
  
 Los siguientes identificadores de archivo de código subyacente del <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos que el anterior [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] en el ejemplo se define.  
  
 [!code-csharp[viewboxStretchLayoutSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[viewboxStretchLayoutSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/viewboxStretchLayoutSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Controls.Viewbox>  
 <xref:System.Windows.Media.Stretch>  
 <xref:System.Windows.Controls.StretchDirection>
