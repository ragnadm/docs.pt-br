---
title: "Como preencher uma forma com uma cor sólida"
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
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb3e160392a903083386d9942f8e2cfe31ee89a4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a><span data-ttu-id="7ad52-102">Como preencher uma forma com uma cor sólida</span><span class="sxs-lookup"><span data-stu-id="7ad52-102">How to: Fill a Shape with a Solid Color</span></span>
<span data-ttu-id="7ad52-103">Para preencher uma forma com uma cor sólida, criar um <xref:System.Drawing.SolidBrush> do objeto e, em seguida, passar que <xref:System.Drawing.SolidBrush> objeto como um argumento para um dos métodos de preenchimento de <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="7ad52-103">To fill a shape with a solid color, create a <xref:System.Drawing.SolidBrush> object, and then pass that <xref:System.Drawing.SolidBrush> object as an argument to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="7ad52-104">O exemplo a seguir mostra como preencher uma elipse com a cor vermelha.</span><span class="sxs-lookup"><span data-stu-id="7ad52-104">The following example shows how to fill an ellipse with the color red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ad52-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7ad52-105">Example</span></span>  
 <span data-ttu-id="7ad52-106">No código a seguir, o <xref:System.Drawing.SolidBrush.%23ctor%2A> construtor usa uma <xref:System.Drawing.Color> objeto como seu único argumento.</span><span class="sxs-lookup"><span data-stu-id="7ad52-106">In the following code, the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor takes a <xref:System.Drawing.Color> object as its only argument.</span></span> <span data-ttu-id="7ad52-107">Os valores usados pelo <xref:System.Drawing.Color.FromArgb%2A> método representam os componentes alfa, vermelhos, verdes e azuis da cor.</span><span class="sxs-lookup"><span data-stu-id="7ad52-107">The values used by the <xref:System.Drawing.Color.FromArgb%2A> method represent the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="7ad52-108">Cada um desses valores deve estar no intervalo de 0 a 255.</span><span class="sxs-lookup"><span data-stu-id="7ad52-108">Each of these values must be in the range 0 through 255.</span></span> <span data-ttu-id="7ad52-109">O primeiro 255 indica que a cor é totalmente opaca e o segundo 255 indica que o componente vermelho é de intensidade total.</span><span class="sxs-lookup"><span data-stu-id="7ad52-109">The first 255 indicates that the color is fully opaque, and the second 255 indicates that the red component is at full intensity.</span></span> <span data-ttu-id="7ad52-110">Os dois zeros indicam que os componentes verde e azul têm uma intensidade igual a 0.</span><span class="sxs-lookup"><span data-stu-id="7ad52-110">The two zeros indicate that the green and blue components both have an intensity of 0.</span></span>  
  
 <span data-ttu-id="7ad52-111">Os quatro números (0, 0, 100, 60) passado para o <xref:System.Drawing.Graphics.FillEllipse%2A> método especificar o local e o tamanho do retângulo delimitador para a elipse.</span><span class="sxs-lookup"><span data-stu-id="7ad52-111">The four numbers (0, 0, 100, 60) passed to the <xref:System.Drawing.Graphics.FillEllipse%2A> method specify the location and size of the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="7ad52-112">O retângulo tem um canto superior esquerdo de (0, 0), uma largura de 100 e uma altura de 60.</span><span class="sxs-lookup"><span data-stu-id="7ad52-112">The rectangle has an upper-left corner of (0, 0), a width of 100, and a height of 60.</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7ad52-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="7ad52-113">Compiling the Code</span></span>  
 <span data-ttu-id="7ad52-114">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="7ad52-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ad52-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ad52-115">See Also</span></span>  
 [<span data-ttu-id="7ad52-116">Usando um pincel para preencher formas</span><span class="sxs-lookup"><span data-stu-id="7ad52-116">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)