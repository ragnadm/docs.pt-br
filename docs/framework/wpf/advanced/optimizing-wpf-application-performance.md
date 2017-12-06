---
title: Otimizando o desempenho do aplicativo WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9ea154bc7c7a20bcdd57e1f271a4010f50646de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="93645-102">Otimizando o desempenho do aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="93645-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="93645-103">Esta seção destina-se como uma referência para [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] os desenvolvedores de aplicativos que estão procurando maneiras de melhorar o desempenho de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="93645-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="93645-104">Se você for um desenvolvedor que há de novo para o [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você deve primeiro familiarizar com ambas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="93645-104">If you are a developer who is new to the [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="93645-105">Esta seção pressupõe conhecimento prático de ambos e é gravada para programadores que já conhecem o suficiente para obter seus aplicativos em execução.</span><span class="sxs-lookup"><span data-stu-id="93645-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93645-106">Os dados de desempenho fornecidos nesta seção são baseados em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos em execução em um PC 2.8 GHz com 512 RAM e um ATI Radeon 9700 placa gráfica.</span><span class="sxs-lookup"><span data-stu-id="93645-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="93645-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="93645-107">In This Section</span></span>  
 [<span data-ttu-id="93645-108">Planejando para desempenho do aplicativo</span><span class="sxs-lookup"><span data-stu-id="93645-108">Planning for Application Performance</span></span>](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
  
 [<span data-ttu-id="93645-109">Aproveitando o hardware</span><span class="sxs-lookup"><span data-stu-id="93645-109">Taking Advantage of Hardware</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="93645-110">Layout e design</span><span class="sxs-lookup"><span data-stu-id="93645-110">Layout and Design</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="93645-111">Elementos gráficos e geração de imagens 2D</span><span class="sxs-lookup"><span data-stu-id="93645-111">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="93645-112">Comportamento do objeto</span><span class="sxs-lookup"><span data-stu-id="93645-112">Object Behavior</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="93645-113">Recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="93645-113">Application Resources</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="93645-114">Texto</span><span class="sxs-lookup"><span data-stu-id="93645-114">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
  
 [<span data-ttu-id="93645-115">Associação de dados</span><span class="sxs-lookup"><span data-stu-id="93645-115">Data Binding</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="93645-116">Controles</span><span class="sxs-lookup"><span data-stu-id="93645-116">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)  
  
 [<span data-ttu-id="93645-117">Outras recomendações de desempenho</span><span class="sxs-lookup"><span data-stu-id="93645-117">Other Performance Recommendations</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="93645-118">Tempo de inicialização do aplicativo</span><span class="sxs-lookup"><span data-stu-id="93645-118">Application Startup Time</span></span>](../../../../docs/framework/wpf/advanced/application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="93645-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93645-119">See Also</span></span>  
 <xref:System.Windows.Media.RenderOptions>  
 <xref:System.Windows.Media.RenderCapability>  
 [<span data-ttu-id="93645-120">Camadas de renderização de gráficos</span><span class="sxs-lookup"><span data-stu-id="93645-120">Graphics Rendering Tiers</span></span>](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [<span data-ttu-id="93645-121">Visão geral de renderização de gráficos do WPF</span><span class="sxs-lookup"><span data-stu-id="93645-121">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [<span data-ttu-id="93645-122">Layout</span><span class="sxs-lookup"><span data-stu-id="93645-122">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
 [<span data-ttu-id="93645-123">Árvores no WPF</span><span class="sxs-lookup"><span data-stu-id="93645-123">Trees in WPF</span></span>](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [<span data-ttu-id="93645-124">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="93645-124">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="93645-125">Usando objetos DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="93645-125">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)  
 [<span data-ttu-id="93645-126">Visão geral das propriedades da dependência</span><span class="sxs-lookup"><span data-stu-id="93645-126">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="93645-127">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="93645-127">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="93645-128">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="93645-128">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="93645-129">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="93645-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="93645-130">Desenhando texto formatado</span><span class="sxs-lookup"><span data-stu-id="93645-130">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)  
 [<span data-ttu-id="93645-131">Tipografia no WPF</span><span class="sxs-lookup"><span data-stu-id="93645-131">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [<span data-ttu-id="93645-132">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="93645-132">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="93645-133">Visão geral de navegação</span><span class="sxs-lookup"><span data-stu-id="93645-133">Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [<span data-ttu-id="93645-134">Dicas e truques de animação</span><span class="sxs-lookup"><span data-stu-id="93645-134">Animation Tips and Tricks</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)  
 [<span data-ttu-id="93645-135">Passo a passo: armazenando dados de aplicativo em cache em um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="93645-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)