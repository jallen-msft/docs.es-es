---
title: Utilizar interoperabilidad con intercambio de datos externos
ms.date: 03/30/2017
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
ms.openlocfilehash: 9571a571137ff0a493be67ee9c607cd46dd47889
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="using-interop-with-external-data-exchange"></a>Utilizar interoperabilidad con intercambio de datos externos
El <xref:System.Activities.Statements.Interop> actividad puede utilizarse para ejecutar las actividades de Windows Workflow Foundation (WF) en [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] y [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) y los flujos de trabajo en Windows Workflow Foundation en [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4). En este ejemplo se muestra cómo configurar y ejecutar un flujo de trabajo WF3 que utiliza <xref:System.Workflow.Activities.ExternalDataExchangeService> (y las actividades personalizadas correspondientes para llamar a los métodos y administrar los eventos) utilizando la actividad <xref:System.Activities.Statements.Interop> en un servicio de flujo de trabajo WF4.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si este directorio no existe, vaya a [Windows Communication Foundation (WCF) y ejemplos de Windows Workflow Foundation (WF) para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a>Para utilizar este ejemplo  
  
1.  Abra el archivo ExternalDataExchange.sln de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Para generar el ejemplo, presione Ctrl+Mayús+B.  
  
3.  Para ejecutar el ejemplo, presione F5.
