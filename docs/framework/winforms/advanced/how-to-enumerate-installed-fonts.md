---
title: Como enumerar as fontes instaladas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
ms.openlocfilehash: 9f31880cbfb42c03122fc7d2730b9ca89db49226
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524433"
---
# <a name="how-to-enumerate-installed-fonts"></a>Como enumerar as fontes instaladas
O <xref:System.Drawing.Text.InstalledFontCollection> classe herda o <xref:System.Drawing.Text.FontCollection> classe base abstrata. Você pode usar um <xref:System.Drawing.Text.InstalledFontCollection> objeto para enumerar as fontes instaladas no computador. O <xref:System.Drawing.Text.FontCollection.Families%2A> propriedade de um <xref:System.Drawing.Text.InstalledFontCollection> objeto é uma matriz de <xref:System.Drawing.FontFamily> objetos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lista os nomes de todas as famílias de fontes instaladas no computador. O código recupera o <xref:System.Drawing.FontFamily.Name%2A> propriedade de cada <xref:System.Drawing.FontFamily> objeto na matriz retornada pelo <xref:System.Drawing.Text.FontCollection.Families%2A> propriedade. Como os nomes de família são recuperados, eles são concatenados à lista de formulário um separados por vírgulas. Em seguida, o <xref:System.Drawing.Graphics.DrawString%2A> método o <xref:System.Drawing.Graphics> classe desenha a lista separada por vírgulas em um retângulo.  
  
 Se você executar o código de exemplo, a saída será semelhante ao mostrado na ilustração a seguir.  
  
 ![Fontes instaladas](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")  
  
 [!code-csharp[System.Drawing.FontsAndText#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>. Além disso, você deve importar o <xref:System.Drawing.Text> namespace.  
  
## <a name="see-also"></a>Consulte também  
 [Usando fontes e texto](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
