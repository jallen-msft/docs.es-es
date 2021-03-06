---
title: 'Cómo: Personalizar la ordenación en el control DataGridView de formularios Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: d781da54a8db8a0af01690f08e9cfd8958adec74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Cómo: Personalizar la ordenación en el control DataGridView de formularios Windows Forms
El control <xref:System.Windows.Forms.DataGridView> proporciona ordenación automática pero, dependiendo de sus necesidades, puede que necesite personalizar las operaciones de ordenación. Por ejemplo, puede usar la ordenación mediante programación para crear una interfaz de usuario alternativa. También puede controlar el evento <xref:System.Windows.Forms.DataGridView.SortCompare> o llamar a la sobrecarga `Sort(IComparer)` del método <xref:System.Windows.Forms.DataGridView.Sort%2A> para disfrutar de más opciones de ordenación, como la ordenación de varias columnas.  
  
 Los ejemplos de código siguientes muestran estos tres enfoques de la ordenación personalizada. Para más información, consulte [Modos de ordenación de columnas del control DataGridView de Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="programmatic-sorting"></a>Ordenación mediante programación  
 En el ejemplo de código siguiente se muestra una ordenación mediante programación usando las propiedades <xref:System.Windows.Forms.DataGridView.SortOrder%2A> y <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> para determinar la dirección de la ordenación, y la propiedad <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> para establecer manualmente el glifo de ordenación. La sobrecarga `Sort(DataGridViewColumn,ListSortDirection)` del método <xref:System.Windows.Forms.DataGridView.Sort%2A> se usa para ordenar los datos de una sola columna.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>Ordenación personalizada mediante el evento SortCompare  
 En el ejemplo de código siguiente se muestra la ordenación personalizada mediante un controlador de eventos <xref:System.Windows.Forms.DataGridView.SortCompare>. Se ordena la <xref:System.Windows.Forms.DataGridViewColumn> seleccionada y, si hay valores duplicados en la columna, se usa el identificador de columna para determinar el orden final.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>Ordenación personalizada mediante la interfaz IComparer  
 En el ejemplo de código siguiente se muestra la ordenación personalizada mediante la sobrecarga `Sort(IComparer)` del método <xref:System.Windows.Forms.DataGridView.Sort%2A>, que toma una implementación de la interfaz <xref:System.Collections.IComparer> para realizar una ordenación de varias columnas.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para estos ejemplos se necesita:  
  
-   Referencias a los ensamblados System, System.Drawing y System.Windows.Forms.  
  
 Para obtener información acerca de cómo compilar estos ejemplos desde la línea de comandos de Visual Basic o Visual C#, vea [compilar desde la línea de comandos](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) o [Command-Line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). También puede compilar este ejemplo en Visual Studio pegando el código en un nuevo proyecto.  Consulte también [Cómo: Compilar y ejecutar un ejemplo de código completo de Windows Forms en Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Forms.DataGridView>  
 [Ordenar datos en el control DataGridView de Windows Forms](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [Modos de ordenación de columnas del control DataGridView de Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Cómo: Establecer modos de ordenación de columnas en el control DataGridView de Windows Forms](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)
