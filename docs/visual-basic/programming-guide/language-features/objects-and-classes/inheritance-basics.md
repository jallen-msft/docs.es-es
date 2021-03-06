---
title: Fundamentos de la herencia (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: 9225e5fd9fa35ae06414018a109f66515f99363f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="inheritance-basics-visual-basic"></a>Fundamentos de la herencia (Visual Basic)
El `Inherits` instrucción se utiliza para declarar una nueva clase, denominada una *clase derivada*, en función de una clase existente, conocida como un *clase base*. Las clases derivadas heredan y pueden extender, las propiedades, métodos, eventos, campos y constantes definidas en la clase base. En la siguiente sección se describe algunas de las reglas de herencia, y los modificadores que puede utilizar para cambiar las clases de manera heredan o son heredados:  
  
-   De forma predeterminada, todas las clases son heredables a menos que se marca con el `NotInheritable` palabra clave. Las clases pueden heredar de otras clases en el proyecto o de clases en otros ensamblados a los que hace referencia el proyecto.  
  
-   A diferencia de los lenguajes que permiten la herencia múltiple, Visual Basic permite la herencia única sólo en las clases; es decir, las clases derivadas pueden tener sólo una clase base. Aunque no se permite la herencia múltiple de clases, las clases pueden implementar varias interfaces, que se pueden lograr de manera eficaz los mismos fines.  
  
-   Para evitar la exposición de elementos restringidos en una clase base, el tipo de acceso de una clase derivada debe ser igual o más restrictivo que su clase base. Por ejemplo, un `Public` clase no puede heredar una `Friend` o un `Private` (clase) y un `Friend` clase no puede heredar un `Private` clase.  
  
## <a name="inheritance-modifiers"></a>Modificadores de herencia  
 Visual Basic presenta las siguientes instrucciones de nivel de clase y los modificadores para admitir la herencia:  
  
-   `Inherits` instrucción: especifica la clase base.  
  
-   `NotInheritable` modificador: impide que los programadores utilicen la clase como una clase base.  
  
-   `MustInherit` modificador: Especifica que la clase está diseñada para su uso como clase base. Instancias de `MustInherit` clases no se pueden crear directamente; solo se pueden crear instancias de clases como base de una clase derivada. (Otros lenguajes de programación, como C++ y C#, usan el término *clase abstracta* para describir esta clase.)  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>Reemplazar propiedades y métodos en clases derivadas  
 De forma predeterminada, una clase derivada hereda las propiedades y métodos de la clase base. Si una propiedad o método heredado debe comportarse de manera diferente en la clase derivada puede ser *se reemplaza*. Es decir, puede definir una nueva implementación del método en la clase derivada. Los siguientes modificadores se utilizan para controlar cómo se reemplazan propiedades y métodos:  
  
-   `Overridable` Permite un método o propiedad en una clase para que se invalide en una clase derivada.  
  
-   `Overrides` : Invalida un `Overridable` propiedad o un método definido en la clase base.  
  
-   `NotOverridable` : Impide que una propiedad o método se invalide en una clase heredera. De forma predeterminada, `Public` métodos son `NotOverridable`.  
  
-   `MustOverride` : Requiere que una clase derivada invalide la propiedad o método. Cuando el `MustOverride` se utiliza la palabra clave, formada por la definición de método simplemente el `Sub`, `Function`, o `Property` instrucción. Se permite ninguna otra instrucción y, específicamente no hay ningún `End Sub` o `End Function` instrucción. `MustOverride` los métodos se deben declarar en `MustInherit` clases.  
  
 Suponga que desea definir clases para controlar la nómina. Puede definir un tipo genérico `Payroll` clase que contiene un `RunPayroll` método calcular la nómina de una semana típica. A continuación, podría utilizar `Payroll` como una clase base para una más especializado `BonusPayroll` (clase), que se pueda usar durante la distribución de bonificaciones de empleado.  
  
 El `BonusPayroll` clase puede heredar y reemplazar, el `PayEmployee` método definido en la base de `Payroll` clase.  
  
 En el ejemplo siguiente se define una clase base, `Payroll,` y una clase derivada, `BonusPayroll`, que reemplaza un método heredado, `PayEmployee`. Un procedimiento, `RunPayroll`, crea y, a continuación, pasa una `Payroll` objeto y un `BonusPayroll` objeto a una función, `Pay`, que se ejecuta el `PayEmployee` método de ambos objetos.  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a>La palabra clave MyBase  
 El `MyBase` palabra clave se comporta como una variable de objeto que hace referencia a la clase base de la instancia actual de una clase. `MyBase` se suele utilizar para tener acceso a miembros de clase base que se reemplazan o se sombrean en una clase derivada. En concreto, `MyBase.New` se utiliza para llamar explícitamente a un constructor de clase base desde un constructor de clase derivada.  
  
 Por ejemplo, suponga que está diseñando una clase derivada que reemplaza un método heredado de la clase base. El método invalidado puede llamar al método en la clase base y modificar el valor devuelto como se muestra en el siguiente fragmento de código:  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 La siguiente lista describe las restricciones sobre el uso de `MyBase`:  
  
-   `MyBase` hace referencia a la clase base inmediata y a sus miembros heredados. No se puede usar para tener acceso a `Private` los miembros de la clase.  
  
-   `MyBase` es una palabra clave, no un objeto real. `MyBase` no se asigna a una variable, pasar a los procedimientos o utilizar en una `Is` comparación.  
  
-   El método que `MyBase` se consideran no tienen que definirse en la clase base inmediata; en su lugar puede definirse en una clase base heredada indirectamente. En orden para una referencia calificada mediante `MyBase` para compilar correctamente, alguna clase base debe contener un método correspondiente al nombre y los tipos de parámetros que aparecen en la llamada.  
  
-   No se puede utilizar `MyBase` para llamar a `MustOverride` métodos de la clase de base.  
  
-   `MyBase` no se puede utilizar para calificarse a sí misma. Por lo tanto, el código siguiente no es válido:  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase` no se puede utilizar en módulos.  
  
-   `MyBase` no se puede usar para tener acceso a los miembros de clase base que están marcados como `Friend` si la clase base está en un ensamblado diferente.  
  
 Para obtener más información y otro ejemplo, vea [Cómo: obtener acceso a una Variable oculta una clase derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
## <a name="the-myclass-keyword"></a>La palabra clave MyClass  
 El `MyClass` palabra clave se comporta como una variable de objeto que hace referencia a la instancia actual de una clase como se implementaron originalmente. `MyClass` es similar a `Me`, pero llama cada método y propiedad en `MyClass` se trata como si fuera el método o propiedad [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). Por lo tanto, el método o propiedad no se ve afectado por el reemplazo de una clase derivada.  
  
-   `MyClass` es una palabra clave, no un objeto real. `MyClass` no se asigna a una variable, pasar a los procedimientos o utilizar en una `Is` comparación.  
  
-   `MyClass` hace referencia a la clase contenedora y a sus miembros heredados.  
  
-   `MyClass` se pueden usar como un calificador para `Shared` miembros.  
  
-   `MyClass` no se puede usar dentro de un `Shared` (método), pero se puede usar dentro de un método de instancia para tener acceso a un miembro compartido de una clase.  
  
-   `MyClass` no se puede utilizar en módulos estándares.  
  
-   `MyClass` puede utilizarse para calificar un método que se define en una clase base y que no tiene ninguna implementación del método proporcionado en esa clase. Este tipo de referencia tiene el mismo significado que `MyBase.` *método*.  
  
 En el ejemplo siguiente se comparan `Me` y `MyClass`.  
  
```vb
Class baseClass  
    Public Overridable Sub testMethod()  
        MsgBox("Base class string")  
    End Sub  
    Public Sub useMe()  
        ' The following call uses the calling class's method, even if   
        ' that method is an override.  
        Me.testMethod()  
    End Sub  
    Public Sub useMyClass()  
        ' The following call uses this instance's method and not any  
        ' override.  
        MyClass.testMethod()  
    End Sub  
End Class  
Class derivedClass : Inherits baseClass  
    Public Overrides Sub testMethod()  
        MsgBox("Derived class string")  
    End Sub  
End Class  
Class testClasses  
    Sub startHere()  
        Dim testObj As derivedClass = New derivedClass()  
        ' The following call displays "Derived class string".  
        testObj.useMe()  
        ' The following call displays "Base class string".  
        testObj.useMyClass()  
    End Sub  
End Class  
```  
  
 Aunque `derivedClass` invalida `testMethod`, `MyClass` palabra clave en `useMyClass` anula el efecto del reemplazo y el compilador resuelve la llamada a la versión de la clase base de `testMethod`.  
  
## <a name="see-also"></a>Vea también  
 [Inherits (instrucción)](../../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Me, My, MyBase y MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
