---
title: Expresiones constantes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 616f297c261c4309dc0db7a4efe2fcad8cc00966
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="constant-expressions"></a>Expresiones constantes
Una expresión constante consta de un valor constante. Los valores constantes se convierten directamente en expresiones constantes de árbol de comandos, sin sufrir ninguna traducción en el cliente. Esto incluye a las expresiones que producen un valor constante. Por consiguiente, debe esperarse el comportamiento del origen de datos para todas las expresiones que impliquen constantes. Esto puede producir un comportamiento que difiera del comportamiento de CLR.  
  
 En el ejemplo siguiente se muestra una expresión constante que se evalúa en el servidor.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] no permite utilizar una clase de usuario como constante. Sin embargo, una referencia de propiedad en una clase de usuario se considera una constante, se convertirá en una expresión constante de árbol de comandos y se ejecutará en el origen de datos.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones en consultas de LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
