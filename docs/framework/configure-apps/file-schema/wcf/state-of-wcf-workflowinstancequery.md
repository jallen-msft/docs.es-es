---
title: '&lt;state&gt; de WCF, &lt;workflowInstanceQuery&gt;'
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 69ebedec40243d3e6580b8350c1253fca83e0802
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a>&lt;state&gt; de WCF, &lt;workflowInstanceQuery&gt;
Representa una colección de estados suscritos de la instancia de flujo de trabajo de la que se ha realizado el seguimiento cuando se crean los registros del seguimiento.  
  
 Para obtener más información sobre las consultas de perfil de seguimiento, vea [perfiles de seguimiento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
 \<system.serviceModel>  
\<seguimiento >  
\<trackingProfile >  
\<flujo de trabajo >  
\<workflowInstanceQueries >  
\<workflowInstanceQuery >  
\<Estados >  
\<estado >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|name|Una cadena que especifica un estado suscrito de la instancia de flujo de trabajo de la que se ha realizado el seguimiento cuando se crea el registro del seguimiento.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<Estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|Una colección de estados subscritos de la instancia de flujo de trabajo de la que se ha realizado el seguimiento cuando se crean los registros del seguimiento.|  
  
## <a name="remarks"></a>Comentarios  
 Los registros devueltos se filtran por los estados de esta colección.  
  
 En la siguiente tabla se describen los valores de estado posibles.  
  
|Estado|Descripción|  
|-----------|-----------------|  
|Anulado|Se ha anulado la instancia de flujo de trabajo.|  
|Completado|Se ha completado la instancia de flujo de trabajo.|  
|Deleted|Se ha eliminado la instancia de flujo de trabajo.|  
|Inactivo|La instancia de flujo de trabajo está inactiva.|  
|Conservado|Se ha guardado la instancia de flujo de trabajo.|  
|Reanudado|Se ha reanudado la instancia de flujo de trabajo.|  
|Comenzado|Se ha iniciado la instancia de flujo de trabajo.|  
|UnhandledException|La instancia de flujo de trabajo ha detectado una excepción no controlada.|  
|Unloaded|Se ha descargado la instancia de flujo de trabajo.|  
|Cancelado|Se ha cancelado la instancia de flujo de trabajo.|  
|Suspendido|Se suspende la instancia de flujo de trabajo.|  
|Terminado|Se ha terminado la instancia de flujo de trabajo.|  
|No suspendido|No se suspende la instancia de flujo de trabajo.|  
  
## <a name="example"></a>Ejemplo  
 La siguiente configuración se suscribe a los registros de seguimiento de nivel de instancia de flujo de trabajo del estado de instancia `Started` mediante esta consulta.  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [Seguimiento y traza de flujos de trabajo](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Perfiles de seguimiento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
