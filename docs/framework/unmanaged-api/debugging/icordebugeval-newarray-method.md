---
title: ICorDebugEval::NewArray (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38b00d903fdd7301415a8df7642e12366178fd10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray (Método)
Asigna una nueva matriz del tipo de elemento especificado y dimensiones.  
  
 Este método está obsoleto en la versión 2.0 de .NET Framework. Use [ICorDebugEval2:: NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) en su lugar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `elementType`  
 [in] Un valor de la enumeración CorElementType que especifica el tipo de elemento de la matriz.  
  
 `pElementClass`  
 [in] Un puntero a un objeto ICorDebugClass que especifica la clase del elemento. Este valor puede ser null si el tipo de elemento es un tipo primitivo.  
  
 `rank`  
 [in] El número de dimensiones de la matriz. En la versión 2.0 de .NET Framework, este valor debe ser 1.  
  
 `dims`  
 [in] El tamaño, en bytes, de cada dimensión de la matriz.  
  
 `lowBounds`  
 [in] Opcional. El límite inferior de cada dimensión de la matriz. Si este valor se omite, se supone que un límite inferior de cero para cada dimensión.  
  
## <a name="remarks"></a>Comentarios  
 La matriz siempre se crea en el dominio de aplicación en el que se está ejecutando el subproceso.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** 1.1, 1.0
