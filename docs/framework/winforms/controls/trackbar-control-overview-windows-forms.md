---
title: Información general del control TrackBar (formularios Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: d0a0cbbcc618e2fa52b3719bcc8f0135a1e0752e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="trackbar-control-overview-windows-forms"></a>Información general del control TrackBar (formularios Windows Forms)
Los formularios Windows Forms <xref:System.Windows.Forms.TrackBar> control (a veces denominado control "deslizante") se utiliza para navegar por una gran cantidad de información o para ajustar visualmente una configuración numérica. El <xref:System.Windows.Forms.TrackBar> control tiene dos partes: el control de posición, también conocido como control deslizante y las marcas de graduación. El cuadro de desplazamiento es la parte que se puede ajustar. Su posición corresponde a la <xref:System.Windows.Forms.TrackBar.Value%2A> propiedad. Las marcas de graduación son indicadores visuales que se llevan a intervalos regulares. La barra de seguimiento se mueve en incrementos que se especifiquen y puede alinearse horizontal o verticalmente. Por ejemplo, puede usar la barra de seguimiento para controlar la velocidad de velocidad o el mouse de parpadeo de cursor para un sistema.  
  
## <a name="key-properties"></a>Propiedades clave  
 Las propiedades de clave de la <xref:System.Windows.Forms.TrackBar> control son <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, y <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> es el espaciado de las marcas de paso. <xref:System.Windows.Forms.TrackBar.Minimum%2A> y <xref:System.Windows.Forms.TrackBar.Maximum%2A> son los valores mínimo y máximo que se pueden representar en la barra de seguimiento.  
  
 Otras dos propiedades importantes son <xref:System.Windows.Forms.TrackBar.SmallChange%2A> y <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. El valor de la <xref:System.Windows.Forms.TrackBar.SmallChange%2A> propiedad es el número de posiciones que se desplaza el control de posición en respuesta a la presionar la tecla flecha izquierda o derecha. El valor de la <xref:System.Windows.Forms.TrackBar.LargeChange%2A> propiedad es el número de posiciones en el cuadro de desplazamiento mueve como respuesta a la presionar la tecla RE PÁG o AV PÁG, o en respuesta a mouse (ratón) haga clic en la barra de seguimiento a ambos lados del control.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Forms.TrackBar>  
 [TrackBar (control)](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
