---
title: Esquema de la configuración de inicio
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 59f0441b79244eb529be338495c32af886a5f2b3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="startup-settings-schema"></a>Esquema de la configuración de inicio
La configuración de inicio especifica la versión de Common Language Runtime que debe ejecutar la aplicación.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<requiredRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Especifica que la aplicación solo admite la versión 1.0 de Common Language Runtime. Las aplicaciones compiladas con la versión 1.1 en tiempo de ejecución deberían usar el elemento **\<supportedRuntime>**.|  
|[\<supportedRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Especifica qué versiones de Common Language Runtime admite la aplicación.|  
|[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|Contiene los elementos **\<requiredRuntime>** y **\<supportedRuntime>**.|  
  
## <a name="see-also"></a>Vea también  
 [Esquema de los archivos de configuración](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> Especificar la versión en tiempo de ejecución que se va a usar](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
