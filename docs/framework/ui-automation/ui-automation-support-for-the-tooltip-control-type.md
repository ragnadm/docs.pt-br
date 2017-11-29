---
title: "Suporte de automação de interface de usuário para o tipo de controle ToolTip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, ToolTip control type
- ToolTip control type
- control types, ToolTip
ms.assetid: c3779d78-3164-43ae-8dae-bfaeafffdd65
caps.latest.revision: "22"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 2040020ba32aed97c613260948f0772355c1287f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-support-for-the-tooltip-control-type"></a><span data-ttu-id="f85d0-102">Suporte de automação de interface de usuário para o tipo de controle ToolTip</span><span class="sxs-lookup"><span data-stu-id="f85d0-102">UI Automation Support for the ToolTip Control Type</span></span>
> [!NOTE]
>  <span data-ttu-id="f85d0-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="f85d0-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f85d0-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="f85d0-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f85d0-105">Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporte para o tipo de controle de dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="f85d0-105">This topic provides information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] support for the ToolTip control type.</span></span> <span data-ttu-id="f85d0-106">Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle precisa atender para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> propriedade.</span><span class="sxs-lookup"><span data-stu-id="f85d0-106">In [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], a control type is a set of conditions that a control must meet in order to use the <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> property.</span></span> <span data-ttu-id="f85d0-107">As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade e padrões de controle.</span><span class="sxs-lookup"><span data-stu-id="f85d0-107">The conditions include specific guidelines for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] property values and control patterns.</span></span>  
  
 <span data-ttu-id="f85d0-108">Controles de dica de ferramenta são janelas pop-up que contêm texto.</span><span class="sxs-lookup"><span data-stu-id="f85d0-108">Tool tip controls are pop-up windows that contain text.</span></span>  
  
 <span data-ttu-id="f85d0-109">As seções a seguir definem as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos para o tipo de controle de dica de ferramenta, propriedades, padrões de controle e estrutura de árvore.</span><span class="sxs-lookup"><span data-stu-id="f85d0-109">The following sections define the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure, properties, control patterns, and events for the ToolTip control type.</span></span> <span data-ttu-id="f85d0-110">O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos os controles de dica de ferramenta se [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f85d0-110">The [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requirements apply to all tool tip controls, whether [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], or [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a><span data-ttu-id="f85d0-111">Estrutura de árvore de automação da interface do usuário necessário</span><span class="sxs-lookup"><span data-stu-id="f85d0-111">Required UI Automation Tree Structure</span></span>  
 <span data-ttu-id="f85d0-112">A tabela a seguir descreve o modo de exibição de controle e exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] controles de árvore referente a dica de ferramenta e descreve o que pode ser contido em cada modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="f85d0-112">The following table depicts the control view and the content view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree that pertains to tool tip controls and describes what can be contained in each view.</span></span> <span data-ttu-id="f85d0-113">Para obter mais informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f85d0-113">For more information on the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree, see [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).</span></span>  
  
|<span data-ttu-id="f85d0-114">Exibição de controle</span><span class="sxs-lookup"><span data-stu-id="f85d0-114">Control View</span></span>|<span data-ttu-id="f85d0-115">Exibição de conteúdo</span><span class="sxs-lookup"><span data-stu-id="f85d0-115">Content View</span></span>|  
|------------------|------------------|  
|<span data-ttu-id="f85d0-116">ToolTip</span><span class="sxs-lookup"><span data-stu-id="f85d0-116">ToolTip</span></span><br /><br /> <span data-ttu-id="f85d0-117">-Texto (0 ou mais)</span><span class="sxs-lookup"><span data-stu-id="f85d0-117">-   Text (0 or more)</span></span><br /><span data-ttu-id="f85d0-118">-Imagem (0 ou mais)</span><span class="sxs-lookup"><span data-stu-id="f85d0-118">-   Image (0 or more)</span></span>|<span data-ttu-id="f85d0-119">ToolTip</span><span class="sxs-lookup"><span data-stu-id="f85d0-119">ToolTip</span></span>|  
  
 <span data-ttu-id="f85d0-120">Controles de dica de ferramenta aparecem somente na exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore se eles podem receber o foco do teclado.</span><span class="sxs-lookup"><span data-stu-id="f85d0-120">Tool tip controls appear only in the Content View of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree if they can receive keyboard focus.</span></span> <span data-ttu-id="f85d0-121">Caso contrário, todas as informações da dica de ferramenta está disponível na `HelpTextProperty` no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a dica de ferramenta está fazendo referência ao elemento.</span><span class="sxs-lookup"><span data-stu-id="f85d0-121">Otherwise, all of the tool tip's information is available from the `HelpTextProperty` on the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element that the tool tip is referring to.</span></span>  
  
 <span data-ttu-id="f85d0-122">Dicas de ferramenta devem aparecer sob o controle que suas informações se refere a.</span><span class="sxs-lookup"><span data-stu-id="f85d0-122">Tool tips should appear beneath the control that their information is referring to.</span></span> <span data-ttu-id="f85d0-123">Os clientes devem escutar a `ToolTipOpenedEvent` para garantir que eles consistentemente obtenham informações contidas na dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="f85d0-123">Clients must listen for the `ToolTipOpenedEvent` to ensure that they consistently obtain information contained in tool tips.</span></span>  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a><span data-ttu-id="f85d0-124">Propriedades de automação de interface do usuário necessário</span><span class="sxs-lookup"><span data-stu-id="f85d0-124">Required UI Automation Properties</span></span>  
 <span data-ttu-id="f85d0-125">A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades cujos valores ou definição é especialmente relevante para controles de dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="f85d0-125">The following table lists the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties whose value or definition is especially relevant to tool tip controls.</span></span> <span data-ttu-id="f85d0-126">Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades, consulte [propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).</span><span class="sxs-lookup"><span data-stu-id="f85d0-126">For more information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).</span></span>  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="f85d0-127">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f85d0-127"> Property</span></span>|<span data-ttu-id="f85d0-128">Valor</span><span class="sxs-lookup"><span data-stu-id="f85d0-128">Value</span></span>|<span data-ttu-id="f85d0-129">Observações</span><span class="sxs-lookup"><span data-stu-id="f85d0-129">Notes</span></span>|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|<span data-ttu-id="f85d0-130">Consulte as observações.</span><span class="sxs-lookup"><span data-stu-id="f85d0-130">See notes.</span></span>|<span data-ttu-id="f85d0-131">O valor dessa propriedade deve ser exclusivo em todos os controles em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f85d0-131">The value of this property needs to be unique across all controls in an application.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|<span data-ttu-id="f85d0-132">Consulte as observações.</span><span class="sxs-lookup"><span data-stu-id="f85d0-132">See notes.</span></span>|<span data-ttu-id="f85d0-133">O retângulo mais externo que contém todo o controle.</span><span class="sxs-lookup"><span data-stu-id="f85d0-133">The outermost rectangle that contains the whole control.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|<span data-ttu-id="f85d0-134">Consulte as observações.</span><span class="sxs-lookup"><span data-stu-id="f85d0-134">See notes.</span></span>|<span data-ttu-id="f85d0-135">O ponto clicável deve ser parte da dica de ferramenta que irá ignorar o controle.</span><span class="sxs-lookup"><span data-stu-id="f85d0-135">The clickable point should be the part of the tool tip that will dismiss the control.</span></span> <span data-ttu-id="f85d0-136">Algumas dicas de ferramenta não têm essa capacidade e não terá um ponto clicável.</span><span class="sxs-lookup"><span data-stu-id="f85d0-136">Some tool tips do not have this ability and will not have a clickable point.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|<span data-ttu-id="f85d0-137">Consulte as observações.</span><span class="sxs-lookup"><span data-stu-id="f85d0-137">See notes.</span></span>|<span data-ttu-id="f85d0-138">Se o controle pode receber o foco do teclado, deve suportar essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="f85d0-138">If the control can receive keyboard focus, it must support this property.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|<span data-ttu-id="f85d0-139">Consulte as observações.</span><span class="sxs-lookup"><span data-stu-id="f85d0-139">See notes.</span></span>|<span data-ttu-id="f85d0-140">O nome do controle de dica de ferramenta é o texto que é exibido na dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="f85d0-140">The name of the tool tip control is the text that is displayed within the tool tip.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|<span data-ttu-id="f85d0-141">Controles de dica de ferramenta sempre são rotulados automaticamente pelo seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f85d0-141">Tool tip controls are always self-labeled by their contents.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|<span data-ttu-id="f85d0-142">ToolTip</span><span class="sxs-lookup"><span data-stu-id="f85d0-142">ToolTip</span></span>|<span data-ttu-id="f85d0-143">Esse valor é o mesmo para todas as estruturas de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="f85d0-143">This value is the same for all UI frameworks.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|<span data-ttu-id="f85d0-144">"dica de ferramenta"</span><span class="sxs-lookup"><span data-stu-id="f85d0-144">"tool tip"</span></span>|<span data-ttu-id="f85d0-145">Cadeia de caracteres localizada correspondente ao tipo de controle de dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="f85d0-145">Localized string corresponding to the ToolTip control type.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|<span data-ttu-id="f85d0-146">Depende</span><span class="sxs-lookup"><span data-stu-id="f85d0-146">Depends</span></span>|<span data-ttu-id="f85d0-147">Se o controle de dica de ferramenta pode receber o foco do teclado, ele deverá ser na exibição de conteúdo da árvore.</span><span class="sxs-lookup"><span data-stu-id="f85d0-147">If the tool tip control can receive keyboard focus, it must be in the Content View of the tree.</span></span> <span data-ttu-id="f85d0-148">Se ele é somente texto, está disponível como o HelpTextProperty do controle que o gerou.</span><span class="sxs-lookup"><span data-stu-id="f85d0-148">If it is text only, then it is available as the HelpTextProperty from the control that raised it.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|<span data-ttu-id="f85d0-149">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="f85d0-149">True</span></span>|<span data-ttu-id="f85d0-150">O controle de dica de ferramenta sempre deve ser um controle.</span><span class="sxs-lookup"><span data-stu-id="f85d0-150">The tool tip control must always be a control.</span></span>|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a><span data-ttu-id="f85d0-151">Padrões de controle de automação de interface do usuário necessário</span><span class="sxs-lookup"><span data-stu-id="f85d0-151">Required UI Automation Control Patterns</span></span>  
 <span data-ttu-id="f85d0-152">A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] devem ser suportados por controles de dica de ferramenta de padrões de controle.</span><span class="sxs-lookup"><span data-stu-id="f85d0-152">The following table lists the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] control patterns required to be supported by tool tip controls.</span></span> <span data-ttu-id="f85d0-153">Para obter mais informações sobre padrões de controle, consulte [visão geral de padrões de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f85d0-153">For more information on control patterns, see [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).</span></span>  
  
|<span data-ttu-id="f85d0-154">Padrão de controle</span><span class="sxs-lookup"><span data-stu-id="f85d0-154">Control Pattern</span></span>|<span data-ttu-id="f85d0-155">Suporte</span><span class="sxs-lookup"><span data-stu-id="f85d0-155">Support</span></span>|<span data-ttu-id="f85d0-156">Observações</span><span class="sxs-lookup"><span data-stu-id="f85d0-156">Notes</span></span>|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|<span data-ttu-id="f85d0-157">Depende</span><span class="sxs-lookup"><span data-stu-id="f85d0-157">Depends</span></span>|<span data-ttu-id="f85d0-158">Dicas de ferramenta que podem ser fechadas clicando em um item de interface do usuário devem oferecer suporte ao WindowPattern para que eles podem fechada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f85d0-158">Tool tips that can be closed by clicking a UI item must support WindowPattern so that they can closed automatically.</span></span>|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|<span data-ttu-id="f85d0-159">Depende</span><span class="sxs-lookup"><span data-stu-id="f85d0-159">Depends</span></span>|<span data-ttu-id="f85d0-160">Para melhor acessibilidade, um controle de dica de ferramenta pode dar suporte o padrão de controle de texto, embora não seja necessário.</span><span class="sxs-lookup"><span data-stu-id="f85d0-160">For better accessibility, a tool tip control can support the Text control pattern, although it is not required.</span></span> <span data-ttu-id="f85d0-161">O padrão de controle de texto é útil quando o texto com estilo avançado e os atributos (por exemplo, cor, negrito e itálico).</span><span class="sxs-lookup"><span data-stu-id="f85d0-161">The Text control pattern is useful when the text has rich style and attributes (for example, color, bold, and italics).</span></span>|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a><span data-ttu-id="f85d0-162">Eventos de automação de interface do usuário necessário</span><span class="sxs-lookup"><span data-stu-id="f85d0-162">Required UI Automation Events</span></span>  
 <span data-ttu-id="f85d0-163">Controles de dica de ferramenta devem gerar o `ToolTipOpenedEvent` quando eles aparecem na tela.</span><span class="sxs-lookup"><span data-stu-id="f85d0-163">Tool tip controls must raise the `ToolTipOpenedEvent` when they appear on the screen.</span></span> <span data-ttu-id="f85d0-164">O evento irá incluir uma referência para o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elemento da dica de ferramenta em si.</span><span class="sxs-lookup"><span data-stu-id="f85d0-164">The event will include a reference to the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element of the tool tip itself.</span></span>  
  
 <span data-ttu-id="f85d0-165">A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos que devem ser suportados por todos os controles de dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="f85d0-165">The following table lists the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] events required to be supported by all tool tip controls.</span></span> <span data-ttu-id="f85d0-166">Para obter mais informações sobre eventos, consulte [visão geral sobre eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f85d0-166">For more information about events, see [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).</span></span>  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="f85d0-167">Evento</span><span class="sxs-lookup"><span data-stu-id="f85d0-167"> Event</span></span>|<span data-ttu-id="f85d0-168">Suporte</span><span class="sxs-lookup"><span data-stu-id="f85d0-168">Support</span></span>|<span data-ttu-id="f85d0-169">Observações</span><span class="sxs-lookup"><span data-stu-id="f85d0-169">Notes</span></span>|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|<span data-ttu-id="f85d0-170">Depende</span><span class="sxs-lookup"><span data-stu-id="f85d0-170">Depends</span></span>|<span data-ttu-id="f85d0-171">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f85d0-171">None</span></span>|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|<span data-ttu-id="f85d0-172">Depende</span><span class="sxs-lookup"><span data-stu-id="f85d0-172">Depends</span></span>|<span data-ttu-id="f85d0-173">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f85d0-173">None</span></span>|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|<span data-ttu-id="f85d0-174">Depende</span><span class="sxs-lookup"><span data-stu-id="f85d0-174">Depends</span></span>|<span data-ttu-id="f85d0-175">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f85d0-175">None</span></span>|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|<span data-ttu-id="f85d0-176">Depende</span><span class="sxs-lookup"><span data-stu-id="f85d0-176">Depends</span></span>|<span data-ttu-id="f85d0-177">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f85d0-177">None</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent>|<span data-ttu-id="f85d0-178">Necessária</span><span class="sxs-lookup"><span data-stu-id="f85d0-178">Required</span></span>|<span data-ttu-id="f85d0-179">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f85d0-179">None</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent>|<span data-ttu-id="f85d0-180">Necessária</span><span class="sxs-lookup"><span data-stu-id="f85d0-180">Required</span></span>|<span data-ttu-id="f85d0-181">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f85d0-181">None</span></span>|  
|<span data-ttu-id="f85d0-182"><xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento de propriedade alterada.</span><span class="sxs-lookup"><span data-stu-id="f85d0-182"><xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> property-changed event.</span></span>|<span data-ttu-id="f85d0-183">Necessária</span><span class="sxs-lookup"><span data-stu-id="f85d0-183">Required</span></span>|<span data-ttu-id="f85d0-184">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f85d0-184">None</span></span>|  
|<span data-ttu-id="f85d0-185"><xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento de propriedade alterada.</span><span class="sxs-lookup"><span data-stu-id="f85d0-185"><xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> property-changed event.</span></span>|<span data-ttu-id="f85d0-186">Necessária</span><span class="sxs-lookup"><span data-stu-id="f85d0-186">Required</span></span>|<span data-ttu-id="f85d0-187">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f85d0-187">None</span></span>|  
|<span data-ttu-id="f85d0-188"><xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento de propriedade alterada.</span><span class="sxs-lookup"><span data-stu-id="f85d0-188"><xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> property-changed event.</span></span>|<span data-ttu-id="f85d0-189">Necessária</span><span class="sxs-lookup"><span data-stu-id="f85d0-189">Required</span></span>|<span data-ttu-id="f85d0-190">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f85d0-190">None</span></span>|  
|<span data-ttu-id="f85d0-191"><xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>evento de propriedade alterada.</span><span class="sxs-lookup"><span data-stu-id="f85d0-191"><xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> property-changed event.</span></span>|<span data-ttu-id="f85d0-192">Necessária</span><span class="sxs-lookup"><span data-stu-id="f85d0-192">Required</span></span>|<span data-ttu-id="f85d0-193">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f85d0-193">None</span></span>|  
|<span data-ttu-id="f85d0-194"><xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty>evento de propriedade alterada.</span><span class="sxs-lookup"><span data-stu-id="f85d0-194"><xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty> property-changed event.</span></span>|<span data-ttu-id="f85d0-195">Depende</span><span class="sxs-lookup"><span data-stu-id="f85d0-195">Depends</span></span>|<span data-ttu-id="f85d0-196">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f85d0-196">None</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|<span data-ttu-id="f85d0-197">Necessária</span><span class="sxs-lookup"><span data-stu-id="f85d0-197">Required</span></span>|<span data-ttu-id="f85d0-198">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f85d0-198">None</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|<span data-ttu-id="f85d0-199">Necessária</span><span class="sxs-lookup"><span data-stu-id="f85d0-199">Required</span></span>|<span data-ttu-id="f85d0-200">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f85d0-200">None</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f85d0-201">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f85d0-201">See Also</span></span>  
 <xref:System.Windows.Automation.ControlType.ToolTip>  
 [<span data-ttu-id="f85d0-202">Visão geral de tipos de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f85d0-202">UI Automation Control Types Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [<span data-ttu-id="f85d0-203">Visão geral de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f85d0-203">UI Automation Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-overview.md)