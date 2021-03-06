---
title: Función PutInstanceWmi (referencia de API no administrada)
description: La función PutInstanceWmi crea o actualiza una instancia de una clase existente.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0db08ef4938a88ee657e2d65dda70edac09df8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi (función)
Crea o actualiza una instancia de una clase existente. La instancia se escribe en el repositorio de WMI. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a>Parámetros

`pInst`    
[in] Un puntero a la instancia sea escritos.

`lFlags`   
[in] Una combinación de indicadores que afectan al comportamiento de esta función. Los valores siguientes se definen en el *WbemCli.h* archivo de encabezado, o bien puede definirlas como constantes en el código: 

|Constante  |Valor  |Descripción  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0 x 20000 | Si se establece, WMI no almacena los calificadores con el **modificado** flavor. </br> Si no conjunto, se supone que no se localiza este objeto y todos los calificadores son storedwith esta instancia. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Crear la instancia si no existe, o sobrescribirlo si ya existe. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Actualizar la instancia. Debe existir la instancia de la llamada se realice correctamente. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Crear la instancia. Se produce un error en la llamada si la instancia ya existe. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0 x 10 | La marca hace una llamada semisincrónica. |

`pCtx`  
[in] Normalmente, este valor es `null`. En caso contrario, es un puntero a un [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instancia que se puede usar el proveedor que proporciona las clases solicitadas. 

`ppCallResult`  
[out] Si `null`, este parámetro no se utiliza. Si `lFlags` contiene `WBEM_FLAG_RETURN_IMMEDIATELY`, la función devuelve inmediatamente con `WBEM_S_NO_ERROR`. El `ppCallResult` parámetro recibe un puntero a una nueva [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) objeto.

## <a name="return-value"></a>Valor devuelto

Los siguientes valores devueltos por esta función se definen en el *WbemCli.h* archivo de encabezado, o bien puede definirlas como constantes en el código:

|Constante  |Valor  |Descripción  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | El usuario no tiene permiso para actualizar una instancia de la clase especificada. |
| `WBEM_E_FAILED` | 0 x 80041001 | Se ha producido un error no especificado. |
| `WBEM_E_INVALID_CLASS` | 0 x 80041010 | La clase compatible con esta instancia no es válida. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | un `null` no se especificó para una propiedad que no puede ser `null`, como uno que esté marcada con un **indexado** o **Not_Null** calificador. |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | La instancia especificada no es válida. (Por ejemplo, al llamar a `PutInstanceWmi` con una clase devuelve este valor.) |
| `WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un parámetro no es válido. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | El `WBEM_FLAG_CREATE_ONLY` se especificó la marca, pero la instancia ya existe. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` no se especificó en `lFlags`, pero la instancia no existe. |
| `WBEM_E_OUT_OF_MEMORY` | 0 x 80041006 | No hay suficiente memoria disponible para completar la operación. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI se ha detenido probablemente y reiniciar. Llame a [ConnectServerWmi](connectserverwmi.md) nuevo. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Error en el vínculo de procedimiento remoto (RPC) de la llamada entre el proceso actual y WMI. |
| `WBEM_S_NO_ERROR` | 0 | La llamada de función tuvo éxito. |
  
## <a name="remarks"></a>Comentarios

Esta función contiene una llamada a la [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) método.

El `PutInstanceWmi` función admite la creación de instancias y la actualización de instancias de clases existentes solo.  Función de la configuración `pCtx` parámetro se establece, se actualizan algunas o todas las propiedades de la instancia. 

Cuando la instancia que señala `pInst` pertenece a una subclase, administración de Windows llama todos los proveedores responsables de las clases de la que deriva la subclase. Todos estos proveedores deben ejecutarse correctamente para la versión original `PutInstanceWmi` solicitud se realice correctamente. El proveedor de compatibilidad de la clase de nivel superior en la jerarquía se llama en primer lugar. El orden de llamada continúa con la subclase de la clase de nivel superior y continúa de arriba a abajo hasta que alcance de administración de Windows del proveedor para la clase propietaria de la instancia que señala `pInst`.
Administración de Windows no llama a los proveedores para cualquiera de las clases secundarias de una instancia. 

Cuando una aplicación debe actualizar una instancia que pertenece a una jerarquía de clases, el `pInst` parámetro debe apuntar a la instancia que contiene las propiedades que se pueden modificar. Es decir, considere la posibilidad de una instancia de destino pertenece a **ClassB**. El **ClassB** deriva instancia **ClassA**, y **ClassA** define la propiedad **PropA**. Si una aplicación desea volver a realizar un cambio en el valor de **PropA** en el **ClassB** instancia, se debe establecer `pInst` a esa instancia en lugar de una instancia de **ClassA** .

Al llamar a `PutInstanceWmi` no se permite en una instancia de una clase abstracta.

Si se produce un error en la llamada de función, puede obtener información de error adicional mediante una llamada a la [GetErrorInfo](geterrorinfo.md) función.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** WMINet_Utils.idl  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Vea también  
[WMI y contadores de rendimiento (referencia de API no administrada)](index.md)
