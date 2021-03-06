---
title: '&lt;add&gt; de &lt;issuerChannelBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 75531e8ed50ae89f379db23d228804612f4bfccb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a>&lt;add&gt; de &lt;issuerChannelBehaviors&gt;
Agrega un comportamiento del punto de conexión que se va a usar al comunicar con STS.  
  
> [!NOTE]
>  Si cualquier comportamiento de punto de conexión contiene un [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento, se producirá una excepción.  
  
 \<system.ServiceModel>  
\<comportamientos >  
sección endpointBehaviors  
\<comportamiento >  
\<clientCredentials >  
\<issuedToken >  
\<issuerChannelBehaviors > elemento  
\<add>  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|issuerAddress|El URI del emisor del token seguridad con el que se va a comunicar.|  
|behaviorConfiguration|El nombre de un comportamiento del punto de conexión definido en el mismo archivo de configuración.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Contiene una colección de comportamientos de extremo de cliente de Windows Communication Foundation (WCF) que se usará al comunicarse con los servicios de Token de servicio especificado.|  
  
## <a name="remarks"></a>Comentarios  
 `issuerAddress` contiene el URI del Servicio de token de seguridad con el que el cliente desea comunicarse. `behaviorConfiguration` apunta a un comportamiento de punto de conexión que utiliza la aplicación en los canales creados por Windows Communication Foundation (WCF) para obtener los tokens emitidos desde los servicios de Token de seguridad.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [Identidad del servicio y autenticación](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Comportamientos de seguridad](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Federación y tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Protección de servicios y clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Protección de clientes](../../../../../docs/framework/wcf/securing-clients.md)  
 [Creación de un cliente federado](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Configuración de un emisor local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Federación y tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
