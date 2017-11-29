---
title: Como determinar qual painel no controle StatusBar dos Windows Forms foi clicado
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
- status bars [Windows Forms], determining panel clicked
- panels [Windows Forms], determining clicked
- StatusBar control [Windows Forms], coding panel click events
- StatusBar control [Windows Forms], determining panel clicked
- PanelClick event [Windows Forms], determining panel clicked
- Panel control [Windows Forms], determining click
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27cf31d7e5944f206bca880adad1407ab124ad6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="5e9ef-102">Como determinar qual painel no controle StatusBar dos Windows Forms foi clicado</span><span class="sxs-lookup"><span data-stu-id="5e9ef-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="5e9ef-103">O <xref:System.Windows.Forms.StatusStrip> e <xref:System.Windows.Forms.ToolStripStatusLabel> controles substituir e adiciona a funcionalidade para o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controla; no entanto, o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controles são mantidos para compatibilidade com versões anteriores e o uso futuro, se você Escolha.</span><span class="sxs-lookup"><span data-stu-id="5e9ef-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="5e9ef-104">Programa a [controle StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) controle para responder a cliques do usuário, use uma instrução case dentro de <xref:System.Windows.Forms.StatusBar.PanelClick> eventos.</span><span class="sxs-lookup"><span data-stu-id="5e9ef-104">To program the [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="5e9ef-105">O evento contém um argumento (o argumento do painel), que contém uma referência para o clicado <xref:System.Windows.Forms.StatusBarPanel>.</span><span class="sxs-lookup"><span data-stu-id="5e9ef-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="5e9ef-106">Usando essa referência, determine o índice do painel clicado e programe adequadamente.</span><span class="sxs-lookup"><span data-stu-id="5e9ef-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e9ef-107">Certifique-se de que o <xref:System.Windows.Forms.StatusBar> do controle <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> está definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="5e9ef-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="5e9ef-108">Para determinar qual painel foi clicado</span><span class="sxs-lookup"><span data-stu-id="5e9ef-108">To determine which panel was clicked</span></span>  
  
1.  <span data-ttu-id="5e9ef-109">No <xref:System.Windows.Forms.StatusBar.PanelClick> manipulador de eventos, use um `Select Case` (em [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) ou `switch case` ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ou [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) instrução para determinar qual painel foi clicado examinando o índice do painel clicado nos argumentos de evento.</span><span class="sxs-lookup"><span data-stu-id="5e9ef-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) or `switch case` ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] or [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="5e9ef-110">O exemplo de código a seguir requer a presença, o formulário de um <xref:System.Windows.Forms.StatusBar> controle, `StatusBar1`e dois <xref:System.Windows.Forms.StatusBarPanel> objetos, `StatusBarPanel1` e `StatusBarPanel2`.</span><span class="sxs-lookup"><span data-stu-id="5e9ef-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,   
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     <span data-ttu-id="5e9ef-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Coloque o seguinte código no construtor de formulários para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="5e9ef-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.statusBar1.PanelClick += new   
       System.Windows.Forms.StatusBarPanelClickEventHandler   
       (this.statusBar1_PanelClick);  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5e9ef-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e9ef-112">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="5e9ef-113">Como definir o tamanho de painéis da barra de status</span><span class="sxs-lookup"><span data-stu-id="5e9ef-113">How to: Set the Size of Status-Bar Panels</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 [<span data-ttu-id="5e9ef-114">Passo a passo: atualizando informações da barra de status em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5e9ef-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [<span data-ttu-id="5e9ef-115">Visão geral do controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="5e9ef-115">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)