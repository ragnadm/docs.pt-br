---
title: 'Como: abrir uma caixa de mensagem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: dd79d69c9b1b54c5158b58ee2f1675e7d11a386a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545630"
---
# <a name="how-to-open-a-message-box"></a>Como: abrir uma caixa de mensagem
Este exemplo mostra como abrir uma caixa de mensagem.  
  
## <a name="example"></a>Exemplo  
 Uma caixa de mensagem é uma caixa de diálogo modal pré-fabricada para exibir informações aos usuários. Uma caixa de mensagem é aberta chamando estático <xref:System.Windows.MessageBox.Show%2A> método o <xref:System.Windows.MessageBox> classe. Quando <xref:System.Windows.MessageBox.Show%2A> é chamado, a mensagem será passada usando um parâmetro de cadeia de caracteres. Várias sobrecargas de <xref:System.Windows.MessageBox.Show%2A> permitem que você configure como uma caixa de mensagem será exibida (consulte <xref:System.Windows.MessageBox>).  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de MessageBox](http://go.microsoft.com/fwlink/?LinkID=160023)
