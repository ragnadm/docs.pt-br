---
title: Como ocultar ToolStripMenuItems
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cb24fd36bdee76fa80a87d48f41b72f01c8f263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-toolstripmenuitems"></a><span data-ttu-id="27e88-102">Como ocultar ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="27e88-102">How to: Hide ToolStripMenuItems</span></span>
<span data-ttu-id="27e88-103">Ocultando itens de menu é uma maneira de controlar a interface do usuário do seu aplicativo e restringir os comandos do usuário.</span><span class="sxs-lookup"><span data-stu-id="27e88-103">Hiding menu items is a way to control the user interface of your application and restrict user commands.</span></span> <span data-ttu-id="27e88-104">Geralmente, é recomendável ocultar um menu inteiro quando todos os itens de menu estão indisponíveis.</span><span class="sxs-lookup"><span data-stu-id="27e88-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="27e88-105">Isso apresenta menos distrações para o usuário.</span><span class="sxs-lookup"><span data-stu-id="27e88-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="27e88-106">Além disso, pode ser útil ocultar e desabilitar o menu ou item de menu, visto que apenas ocultar não impede que o usuário acesse um comando de menu usando uma tecla de atalho.</span><span class="sxs-lookup"><span data-stu-id="27e88-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span>  
  
### <a name="to-hide-any-menu-item-programmatically"></a><span data-ttu-id="27e88-107">Para ocultar qualquer item de menu programaticamente</span><span class="sxs-lookup"><span data-stu-id="27e88-107">To hide any menu item programmatically</span></span>  
  
-   <span data-ttu-id="27e88-108">Dentro do método onde você define as propriedades do item de menu, adicione código para definir o <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade `false`.</span><span class="sxs-lookup"><span data-stu-id="27e88-108">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="27e88-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27e88-109">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 [<span data-ttu-id="27e88-110">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="27e88-110">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="27e88-111">Como desabilitar ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="27e88-111">How to: Disable ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)