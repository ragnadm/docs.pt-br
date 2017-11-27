---
title: "Como criar um modo de exibição personalizado para um ListView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c62bcb14f444490991b36dc21eb7676a67007906
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="cac7a-102">Como criar um modo de exibição personalizado para um ListView</span><span class="sxs-lookup"><span data-stu-id="cac7a-102">How to: Create a Custom View Mode for a ListView</span></span>
<span data-ttu-id="cac7a-103">Este exemplo mostra como criar um personalizado <xref:System.Windows.Controls.ListView.View%2A> modo para um <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="cac7a-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cac7a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cac7a-104">Example</span></span>  
 <span data-ttu-id="cac7a-105">Você deve usar o <xref:System.Windows.Controls.ViewBase> classe quando você criar uma exibição personalizada para o <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="cac7a-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="cac7a-106">O exemplo a seguir mostra um modo de exibição que é chamado `PlainView`, que é derivado de <xref:System.Windows.Controls.ViewBase> classe.</span><span class="sxs-lookup"><span data-stu-id="cac7a-106">The following example shows a view mode that is called `PlainView`, which is derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="cac7a-107">Para aplicar um estilo para o modo de exibição personalizado, use o <xref:System.Windows.Style> classe.</span><span class="sxs-lookup"><span data-stu-id="cac7a-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="cac7a-108">O exemplo a seguir define uma <xref:System.Windows.Style> para o `PlainView` modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="cac7a-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="cac7a-109">No exemplo anterior, esse estilo é definido como o valor de <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> propriedade que é definida para `PlainView`.</span><span class="sxs-lookup"><span data-stu-id="cac7a-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that is defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="cac7a-110">Para definir o layout dos dados em um modo de exibição personalizado, defina um <xref:System.Windows.DataTemplate> objeto.</span><span class="sxs-lookup"><span data-stu-id="cac7a-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="cac7a-111">O exemplo a seguir define uma <xref:System.Windows.DataTemplate> que pode ser usado para exibir dados de `PlainView` o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="cac7a-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="cac7a-112">O exemplo a seguir mostra como definir um <xref:System.Windows.ResourceKey> para o `PlainView` modo de exibição que usa o <xref:System.Windows.DataTemplate> que é definida no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="cac7a-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="cac7a-113">Um <xref:System.Windows.Controls.ListView> controle pode usar um modo de exibição personalizado se você definir o <xref:System.Windows.Controls.ListView.View%2A> propriedade para a chave de recurso.</span><span class="sxs-lookup"><span data-stu-id="cac7a-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="cac7a-114">O exemplo a seguir mostra como especificar `PlainView` como o modo de exibição para um <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="cac7a-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="cac7a-115">Para obter um exemplo completo, consulte [ListView com várias exibições de exemplo](http://go.microsoft.com/fwlink/?LinkID=160013).</span><span class="sxs-lookup"><span data-stu-id="cac7a-115">For the complete sample, see [ListView with Multiple Views Sample](http://go.microsoft.com/fwlink/?LinkID=160013).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac7a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cac7a-116">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="cac7a-117">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="cac7a-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="cac7a-118">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="cac7a-118">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="cac7a-119">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="cac7a-119">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)