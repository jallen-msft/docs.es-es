---
title: 'Cómo: Voltear un control UIElement horizontal o verticalmente'
ms.date: 03/30/2017
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
ms.openlocfilehash: 89dcf668f1fe361480dabdab227a35ea40c344a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a>Cómo: Voltear un control UIElement horizontal o verticalmente
Este ejemplo muestra cómo utilizar un <xref:System.Windows.Media.ScaleTransform> debe voltear un <xref:System.Windows.UIElement> horizontal o verticalmente. En este ejemplo, un <xref:System.Windows.Controls.Button> control (un tipo de <xref:System.Windows.UIElement>) se voltea aplicando un <xref:System.Windows.Media.ScaleTransform> a su <xref:System.Windows.UIElement.RenderTransform%2A> propiedad.  
  
## <a name="example"></a>Ejemplo  
 En la siguiente ilustración muestra el botón Examinar.  
  
 ![Un botón sin transformación](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")  
El elemento de IU para voltear  
  
 A continuación muestra el código que crea el botón.  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a>Ejemplo  
 Para voltear horizontalmente el botón, cree una <xref:System.Windows.Media.ScaleTransform> y establecer su <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> propiedad en -1. Aplicar el <xref:System.Windows.Media.ScaleTransform> en el botón <xref:System.Windows.UIElement.RenderTransform%2A> propiedad.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 ![Botón volteado horizontalmente alrededor de &#40;0,0&#41;](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")  
El botón después de aplicar ScaleTransform  
  
## <a name="example"></a>Ejemplo  
 Como puede ver en la ilustración anterior, el botón se ha volteado, pero también se ha movido. Eso es porque se voltea el botón de la esquina superior izquierda. Para voltear el botón en su lugar, desea aplicar el <xref:System.Windows.Media.ScaleTransform> a su centro, no a su esquina. Una forma sencilla de aplicar el <xref:System.Windows.Media.ScaleTransform> a los botones es establecer el botón Centro <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propiedad en 0,5, 0,5.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 ![Botón volteado horizontalmente alrededor de su centro](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")  
El botón con un valor de RenderTransformOrigin de 0,5, 0,5  
  
## <a name="example"></a>Ejemplo  
 Para voltear verticalmente el botón, establezca la <xref:System.Windows.Media.ScaleTransform> del objeto <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propiedad en lugar de su <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> propiedad.  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 ![Botón volteado verticalmente alrededor de su centro](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")  
El botón volteado verticalmente  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre transformaciones](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
