---
title: ICorDebugAppDomain3 (Interfaz)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3
helpviewer_keywords: ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 08f125d7fc388a9b2d31c9cc1cebf2605ffa7e23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 (Interfaz)
Proporciona métodos para recuperar información acerca de las representaciones administradas de [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos cargados actualmente en un dominio de aplicación. Esta interfaz es una extensión de las interfaces ICorDebugAppDomain y ICorDebugAppDomain2.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[Icordebugappdomain3:: Getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|Obtiene un enumerador para todos los almacena en caché [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos.|  
|[Icordebugappdomain3:: Getcachedwinrttypesforiids](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|Obtiene un enumerador para almacenado en memoria caché [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos en un dominio de aplicación en función de sus identificadores de interfaz.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz está pensada para usarse con un depurador junto con una llamada a evaluación de función `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`. Cuando el método recupera los identificadores de interfaz admitidos por un [!INCLUDE[wrt](../../../../includes/wrt-md.md)] objeto de servidor, el depurador puede usar los métodos definidos en esta interfaz para asignarlas a los tipos administrados que se corresponden con esas interfaces.  
  
 Para recuperar una instancia de esta interfaz, ejecute `QueryInterface` en una instancia de la interfaz ICorDebugAppDomain o ICorDebugAppDomain2.  
  
> [!NOTE]
>  Esta interfaz no admite que se la llame de forma remota, ya sea entre procesos o entre equipos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de depuración](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)