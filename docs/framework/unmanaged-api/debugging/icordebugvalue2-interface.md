---
title: ICorDebugValue2 (Interfaz)
ms.date: 03/30/2017
api_name:
- ICorDebugValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2
helpviewer_keywords:
- ICorDebugValue2 interface [.NET Framework debugging]
ms.assetid: 3ff2ad2a-da5a-461b-8627-1a8eba49df9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2462d1de9f1b5f94f2581c1a06ca2987712fd7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvalue2-interface"></a>ICorDebugValue2 (Interfaz)
Extiende la interfaz "ICorDebugValue" para proporcionar compatibilidad para objetos de "ICorDebugType".  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetExactType (método)](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|Obtiene un puntero de interfaz a una `ICorDebugType` objeto que representa el <xref:System.Type> de este valor.|  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Esta interfaz no admite que se la llame de forma remota, ya sea entre procesos o entre equipos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de depuración](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
    
 [ICorDebugValue3 (interfaz)](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
