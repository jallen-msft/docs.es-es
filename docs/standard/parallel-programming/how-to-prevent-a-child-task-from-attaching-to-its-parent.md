---
title: 'Cómo: Evitar que una tarea secundaria se adjunte a su elemento primario'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ea0254add0592c0c79c03f4e94f02526f9fe689
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Cómo: Evitar que una tarea secundaria se adjunte a su elemento primario
En este documento se explica cómo evitar que una tarea secundaria se adjunte a la tarea principal. Impedir que una tarea secundaria se adjunte a su elemento principal es útil cuando se llama a un componente que está escrito por un tercero y que también usa las tareas. Por ejemplo, un componente de terceros que utiliza la opción <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> para crear un objeto <xref:System.Threading.Tasks.Task> o <xref:System.Threading.Tasks.Task%601> puede causar problemas en el código si es de larga duración o produce una excepción no controlada.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se comparan los efectos del uso de las opciones predeterminadas con los efectos de impedir que una tarea secundaria se adjunte al elemento principal. En el ejemplo se crea un objeto <xref:System.Threading.Tasks.Task> que llama a una biblioteca de terceros que también usa un objeto <xref:System.Threading.Tasks.Task>. La biblioteca de otro fabricante utiliza la opción <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> para crear el objeto <xref:System.Threading.Tasks.Task>. La aplicación utiliza la opción <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> para crear la tarea principal. Esta opción indica el tiempo de ejecución para quitar la especificación <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> de las tareas secundarias.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Dado que una tarea primaria no finaliza hasta que finalizan todas las tareas secundarias, una tarea secundaria que se ejecute durante mucho tiempo puede provocar que el rendimiento general de la aplicación sea bajo. En este ejemplo, cuando la aplicación usa las opciones predeterminadas para crear la tarea principal, la tarea secundaria debe finalizar antes de que finalice la principal. Cuando la aplicación utiliza la opción <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, el elemento secundario no está asociado al principal. Por lo tanto, la aplicación puede realizar un trabajo adicional después de que finalice la tarea principal y antes debe esperar a que finalice la tarea secundaria.  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `DenyChildAttach.cs` (`DenyChildAttach.vb` para Visual Basic) y, luego, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 Visual C#  
  
 **csc.exe DenyChildAttach.cs**  
  
 Visual Basic  
  
 **vbc.exe DenyChildAttach.vb**  
  
## <a name="robust-programming"></a>Programación sólida  
  
## <a name="see-also"></a>Vea también  
 [Programación asincrónica basada en tareas](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
