---
title: return (Referencia de C#)
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 29d2b8e28ae6240b9d06b82695efe1736404c5cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="return-c-reference"></a>return (Referencia de C#)
La instrucción `return` termina la ejecución del método en el que aparece y devuelve el control al método de llamada. También puede devolver un valor opcional. Si el método es del tipo `void`, la instrucción `return` se puede omitir.  
  
 Si la instrucción return está incluida en un bloque `try`, el bloque `finally`, si existe, se ejecutará antes de que el control se devuelva al método de llamada.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, el método `CalculateArea()` devuelve la variable local `area` como un valor de tipo [double](../../../csharp/language-reference/keywords/double.md).  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a>Especificación del lenguaje C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Referencia de C#](../../../csharp/language-reference/index.md)  
 [Guía de programación de C#](../../../csharp/programming-guide/index.md)  
 [Palabras clave de C#](../../../csharp/language-reference/keywords/index.md)  
 [return (instrucción)](/cpp/cpp/return-statement-cpp)  
 [Instrucciones de salto](../../../csharp/language-reference/keywords/jump-statements.md)
