---
title: "Representação matricial de transformações"
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
- composite transformations
- transformations [Windows Forms], linear
- matrices
- translations in matrix representation
- transformations [Windows Forms], composite
- vectors
- linear transformations
- transformations [Windows Forms], matrix representation of
- transformations [Windows Forms], translation
- affine transformations
ms.assetid: 0659fe00-9e0c-41c4-9118-016f2404c905
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10babac22fd94bd00b14b7f861fe99469d3ecbda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="matrix-representation-of-transformations"></a><span data-ttu-id="e34c8-102">Representação matricial de transformações</span><span class="sxs-lookup"><span data-stu-id="e34c8-102">Matrix Representation of Transformations</span></span>
<span data-ttu-id="e34c8-103">Uma matriz m×n é um conjunto de números organizados em m linhas e n colunas.</span><span class="sxs-lookup"><span data-stu-id="e34c8-103">An m×n matrix is a set of numbers arranged in m rows and n columns.</span></span> <span data-ttu-id="e34c8-104">A ilustração a seguir mostra diversas matrizes.</span><span class="sxs-lookup"><span data-stu-id="e34c8-104">The following illustration shows several matrices.</span></span>  
  
 <span data-ttu-id="e34c8-105">![Transformações](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art04.gif "AboutGdip05_art04")</span><span class="sxs-lookup"><span data-stu-id="e34c8-105">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art04.gif "AboutGdip05_art04")</span></span>  
  
 <span data-ttu-id="e34c8-106">Você pode adicionar duas matrizes do mesmo tamanho ao adicionar elementos individuais.</span><span class="sxs-lookup"><span data-stu-id="e34c8-106">You can add two matrices of the same size by adding individual elements.</span></span> <span data-ttu-id="e34c8-107">A ilustração a seguir mostra dois exemplos de adição de matriz.</span><span class="sxs-lookup"><span data-stu-id="e34c8-107">The following illustration shows two examples of matrix addition.</span></span>  
  
 <span data-ttu-id="e34c8-108">![Transformações](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art05.gif "AboutGdip05_art05")</span><span class="sxs-lookup"><span data-stu-id="e34c8-108">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art05.gif "AboutGdip05_art05")</span></span>  
  
 <span data-ttu-id="e34c8-109">Uma matriz m×n pode ser multiplicada por uma matriz n×p e o resultado é uma matriz m×p.</span><span class="sxs-lookup"><span data-stu-id="e34c8-109">An m×n matrix can be multiplied by an n×p matrix, and the result is an m×p matrix.</span></span> <span data-ttu-id="e34c8-110">O número de colunas da primeira matriz deve ser igual ao número de linhas da segunda.</span><span class="sxs-lookup"><span data-stu-id="e34c8-110">The number of columns in the first matrix must be the same as the number of rows in the second matrix.</span></span> <span data-ttu-id="e34c8-111">Por exemplo, uma matriz 4x2 pode ser multiplicada por uma matriz 2×3 para produzir uma matriz 4×3.</span><span class="sxs-lookup"><span data-stu-id="e34c8-111">For example, a 4×2 matrix can be multiplied by a 2×3 matrix to produce a 4×3 matrix.</span></span>  
  
 <span data-ttu-id="e34c8-112">Os pontos no plano e as linhas e as colunas de uma matriz podem ser pensados como vetores.</span><span class="sxs-lookup"><span data-stu-id="e34c8-112">Points in the plane and rows and columns of a matrix can be thought of as vectors.</span></span> <span data-ttu-id="e34c8-113">Por exemplo, (2, 5) é um vetor com dois componentes e (3, 7, 1) é um vetor com três componentes.</span><span class="sxs-lookup"><span data-stu-id="e34c8-113">For example, (2, 5) is a vector with two components, and (3, 7, 1) is a vector with three components.</span></span> <span data-ttu-id="e34c8-114">O produto escalar de dois vetores é definido da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e34c8-114">The dot product of two vectors is defined as follows:</span></span>  
  
 <span data-ttu-id="e34c8-115">(a, b) • (c, d) = ac + bd</span><span class="sxs-lookup"><span data-stu-id="e34c8-115">(a, b) • (c, d) = ac + bd</span></span>  
  
 <span data-ttu-id="e34c8-116">(a, b, c) • (d, e, f) = ad + be + cf</span><span class="sxs-lookup"><span data-stu-id="e34c8-116">(a, b, c) • (d, e, f) = ad + be + cf</span></span>  
  
 <span data-ttu-id="e34c8-117">Por exemplo, o produto escalar (2, 3) e (5, 4) é (2)(5) + (3)(4) = 22.</span><span class="sxs-lookup"><span data-stu-id="e34c8-117">For example, the dot product of (2, 3) and (5, 4) is (2)(5) + (3)(4) = 22.</span></span> <span data-ttu-id="e34c8-118">O produto escalar (2, 5, 1) e (4, 3, 1) é (2)(4) + (5)(3) + (1)(1) = 24.</span><span class="sxs-lookup"><span data-stu-id="e34c8-118">The dot product of (2, 5, 1) and (4, 3, 1) is (2)(4) + (5)(3) + (1)(1) = 24.</span></span> <span data-ttu-id="e34c8-119">Observe que o produto escalar de dois vetores é um número e não outro vetor.</span><span class="sxs-lookup"><span data-stu-id="e34c8-119">Note that the dot product of two vectors is a number, not another vector.</span></span> <span data-ttu-id="e34c8-120">Observe também que você pode calcular o produto escalar somente se os dois vetores tiverem o mesmo número de componentes.</span><span class="sxs-lookup"><span data-stu-id="e34c8-120">Also note that you can calculate the dot product only if the two vectors have the same number of components.</span></span>  
  
 <span data-ttu-id="e34c8-121">Permita que A(i, j) seja a entrada na matriz A na iª linha e na jª coluna.</span><span class="sxs-lookup"><span data-stu-id="e34c8-121">Let A(i, j) be the entry in matrix A in the ith row and the jth column.</span></span> <span data-ttu-id="e34c8-122">Por exemplo, A(3, 2) é a entrada na matriz A na 3ª linha e na 2ª coluna.</span><span class="sxs-lookup"><span data-stu-id="e34c8-122">For example A(3, 2) is the entry in matrix A in the 3rd row and the 2nd column.</span></span> <span data-ttu-id="e34c8-123">Suponha que A, B e C são matrizes e AB = C. As entradas de C são calculadas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e34c8-123">Suppose A, B, and C are matrices, and AB = C. The entries of C are calculated as follows:</span></span>  
  
 <span data-ttu-id="e34c8-124">C(i, j) = (linha i de A) • (coluna j de B)</span><span class="sxs-lookup"><span data-stu-id="e34c8-124">C(i, j) = (row i of A) • (column j of B)</span></span>  
  
 <span data-ttu-id="e34c8-125">A ilustração a seguir mostra dois exemplos de multiplicação de matriz.</span><span class="sxs-lookup"><span data-stu-id="e34c8-125">The following illustration shows several examples of matrix multiplication.</span></span>  
  
 <span data-ttu-id="e34c8-126">![Transformações](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art06.gif "AboutGdip05_art06")</span><span class="sxs-lookup"><span data-stu-id="e34c8-126">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art06.gif "AboutGdip05_art06")</span></span>  
  
 <span data-ttu-id="e34c8-127">Se pensar em um ponto em um plano como uma matriz 1 × 2, você poderá transformar esse ponto multiplicando-o por uma matriz 2 x 2.</span><span class="sxs-lookup"><span data-stu-id="e34c8-127">If you think of a point in a plane as a 1×2 matrix, you can transform that point by multiplying it by a 2×2 matrix.</span></span> <span data-ttu-id="e34c8-128">A ilustração a seguir mostra várias transformações aplicadas ao ponto (2, 1).</span><span class="sxs-lookup"><span data-stu-id="e34c8-128">The following illustration shows several transformations applied to the point (2, 1).</span></span>  
  
 <span data-ttu-id="e34c8-129">![Transformações](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art07.gif "AboutGdip05_art07")</span><span class="sxs-lookup"><span data-stu-id="e34c8-129">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art07.gif "AboutGdip05_art07")</span></span>  
  
 <span data-ttu-id="e34c8-130">Todas as transformações mostradas na figura anterior são transformações lineares.</span><span class="sxs-lookup"><span data-stu-id="e34c8-130">All of the transformations shown in the preceding figure are linear transformations.</span></span> <span data-ttu-id="e34c8-131">Outras transformações, como conversão, não são lineares e não podem ser expressas como multiplicação por uma matriz 2 x 2.</span><span class="sxs-lookup"><span data-stu-id="e34c8-131">Certain other transformations, such as translation, are not linear, and cannot be expressed as multiplication by a 2×2 matrix.</span></span> <span data-ttu-id="e34c8-132">Suponha que você deseja começar com o ponto (2, 1), girá-lo 90 graus, movê-lo em 3 unidades na direção x e 4 unidades na direção y.</span><span class="sxs-lookup"><span data-stu-id="e34c8-132">Suppose you want to start with the point (2, 1), rotate it 90 degrees, translate it 3 units in the x direction, and translate it 4 units in the y direction.</span></span> <span data-ttu-id="e34c8-133">Você pode fazer isso usando uma multiplicação de matriz seguida por uma adição de matriz.</span><span class="sxs-lookup"><span data-stu-id="e34c8-133">You can accomplish this by using a matrix multiplication followed by a matrix addition.</span></span>  
  
 <span data-ttu-id="e34c8-134">![Transformações](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art08.gif "AboutGdip05_art08")</span><span class="sxs-lookup"><span data-stu-id="e34c8-134">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art08.gif "AboutGdip05_art08")</span></span>  
  
 <span data-ttu-id="e34c8-135">Uma transformação linear (multiplicação por uma matriz 2 x 2) seguida por uma tradução (além de uma matriz 1 × 2) é chamada de uma transformação afim.</span><span class="sxs-lookup"><span data-stu-id="e34c8-135">A linear transformation (multiplication by a 2×2 matrix) followed by a translation (addition of a 1×2 matrix) is called an affine transformation.</span></span> <span data-ttu-id="e34c8-136">Uma alternativa ao armazenamento uma transformação afim em um par de matrizes (um para a parte linear e outro para a conversão) é armazenar a transformação toda em uma matriz 3 × 3.</span><span class="sxs-lookup"><span data-stu-id="e34c8-136">An alternative to storing an affine transformation in a pair of matrices (one for the linear part and one for the translation) is to store the entire transformation in a 3×3 matrix.</span></span> <span data-ttu-id="e34c8-137">Para fazer esse trabalho, um ponto no plano deve ser armazenado em uma matriz 1 × 3 com uma 3ª coordenada fictícia.</span><span class="sxs-lookup"><span data-stu-id="e34c8-137">To make this work, a point in the plane must be stored in a 1×3 matrix with a dummy 3rd coordinate.</span></span> <span data-ttu-id="e34c8-138">A técnica comum é fazer todas as terceiras coordenadas iguais a 1.</span><span class="sxs-lookup"><span data-stu-id="e34c8-138">The usual technique is to make all 3rd coordinates equal to 1.</span></span> <span data-ttu-id="e34c8-139">Por exemplo, o ponto (2, 1) é representado pela matriz [2 1 1].</span><span class="sxs-lookup"><span data-stu-id="e34c8-139">For example, the point (2, 1) is represented by the matrix [2 1 1].</span></span> <span data-ttu-id="e34c8-140">A ilustração a seguir mostra uma transformação afim (girar 90 graus; mover 3 unidades na direção x, 4 unidades na direção y) expressa como uma multiplicação por uma matriz única 3 × 3.</span><span class="sxs-lookup"><span data-stu-id="e34c8-140">The following illustration shows an affine transformation (rotate 90 degrees; translate 3 units in the x direction, 4 units in the y direction) expressed as multiplication by a single 3×3 matrix.</span></span>  
  
 <span data-ttu-id="e34c8-141">![Transformações](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art09.gif "AboutGdip05_art09")</span><span class="sxs-lookup"><span data-stu-id="e34c8-141">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art09.gif "AboutGdip05_art09")</span></span>  
  
 <span data-ttu-id="e34c8-142">No exemplo anterior, o ponto (2, 1) é mapeado para o ponto (2, 6).</span><span class="sxs-lookup"><span data-stu-id="e34c8-142">In the preceding example, the point (2, 1) is mapped to the point (2, 6).</span></span> <span data-ttu-id="e34c8-143">Observe que a terceira coluna da matriz 3 × 3 contém os números 0, 0, 1.</span><span class="sxs-lookup"><span data-stu-id="e34c8-143">Note that the third column of the 3×3 matrix contains the numbers 0, 0, 1.</span></span> <span data-ttu-id="e34c8-144">Isso será sempre o caso para a matriz 3 × 3 de uma transformação afim.</span><span class="sxs-lookup"><span data-stu-id="e34c8-144">This will always be the case for the 3×3 matrix of an affine transformation.</span></span> <span data-ttu-id="e34c8-145">Os números importantes são os seis números nas colunas 1 e 2.</span><span class="sxs-lookup"><span data-stu-id="e34c8-145">The important numbers are the six numbers in columns 1 and 2.</span></span> <span data-ttu-id="e34c8-146">A parte 2 × 2 esquerda superior da matriz representa a parte linear da transformação e as duas primeiras entradas na 3ª linha representam a conversão.</span><span class="sxs-lookup"><span data-stu-id="e34c8-146">The upper-left 2×2 portion of the matrix represents the linear part of the transformation, and the first two entries in the 3rd row represent the translation.</span></span>  
  
 <span data-ttu-id="e34c8-147">![Transformações](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art10.gif "AboutGdip05_art10")</span><span class="sxs-lookup"><span data-stu-id="e34c8-147">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art10.gif "AboutGdip05_art10")</span></span>  
  
 <span data-ttu-id="e34c8-148">Em [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] , você pode armazenar uma transformação afim de um <xref:System.Drawing.Drawing2D.Matrix> objeto.</span><span class="sxs-lookup"><span data-stu-id="e34c8-148">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you can store an affine transformation in a <xref:System.Drawing.Drawing2D.Matrix> object.</span></span> <span data-ttu-id="e34c8-149">Como a terceira coluna de uma matriz que representa uma transformação afim sempre é (0, 0, 1), você especificar apenas os seis números nas duas primeiras colunas quando você construir um <xref:System.Drawing.Drawing2D.Matrix> objeto.</span><span class="sxs-lookup"><span data-stu-id="e34c8-149">Because the third column of a matrix that represents an affine transformation is always (0, 0, 1), you specify only the six numbers in the first two columns when you construct a <xref:System.Drawing.Drawing2D.Matrix> object.</span></span> <span data-ttu-id="e34c8-150">A instrução `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` constrói a matriz mostrada na figura anterior.</span><span class="sxs-lookup"><span data-stu-id="e34c8-150">The statement `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` constructs the matrix shown in the preceding figure.</span></span>  
  
## <a name="composite-transformations"></a><span data-ttu-id="e34c8-151">Transformações de composição</span><span class="sxs-lookup"><span data-stu-id="e34c8-151">Composite Transformations</span></span>  
 <span data-ttu-id="e34c8-152">Uma transformação de composição é uma sequência de transformações, uma seguida da outra.</span><span class="sxs-lookup"><span data-stu-id="e34c8-152">A composite transformation is a sequence of transformations, one followed by the other.</span></span> <span data-ttu-id="e34c8-153">Considere as matrizes e transformações na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="e34c8-153">Consider the matrices and transformations in the following list:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e34c8-154">Matriz A</span><span class="sxs-lookup"><span data-stu-id="e34c8-154">Matrix A</span></span>|<span data-ttu-id="e34c8-155">Girar 90 graus</span><span class="sxs-lookup"><span data-stu-id="e34c8-155">Rotate 90 degrees</span></span>|  
|<span data-ttu-id="e34c8-156">Matriz B</span><span class="sxs-lookup"><span data-stu-id="e34c8-156">Matrix B</span></span>|<span data-ttu-id="e34c8-157">Dimensionar por um fator de 2 na direção x</span><span class="sxs-lookup"><span data-stu-id="e34c8-157">Scale by a factor of 2 in the x direction</span></span>|  
|<span data-ttu-id="e34c8-158">Matriz C</span><span class="sxs-lookup"><span data-stu-id="e34c8-158">Matrix C</span></span>|<span data-ttu-id="e34c8-159">Mover 3 unidades na direção y</span><span class="sxs-lookup"><span data-stu-id="e34c8-159">Translate 3 units in the y direction</span></span>|  
  
 <span data-ttu-id="e34c8-160">Se começar com o ponto (2, 1) — representado pela matriz [2 1 1] — e multiplicar por A, em seguida, B e C, o ponto (2, 1) passará as três transformações na ordem listada.</span><span class="sxs-lookup"><span data-stu-id="e34c8-160">If we start with the point (2, 1) — represented by the matrix [2 1 1] — and multiply by A, then B, then C, the point (2, 1) will undergo the three transformations in the order listed.</span></span>  
  
 <span data-ttu-id="e34c8-161">[2 1 1]ABC = [-2 5 1]</span><span class="sxs-lookup"><span data-stu-id="e34c8-161">[2 1 1]ABC = [-2 5 1]</span></span>  
  
 <span data-ttu-id="e34c8-162">Em vez de armazenar as três partes da transformação de composição em três matrizes separadas, você pode multiplicar A, B e C juntos para obter uma única matriz 3 × 3 que armazena a transformação de composição inteira.</span><span class="sxs-lookup"><span data-stu-id="e34c8-162">Rather than store the three parts of the composite transformation in three separate matrices, you can multiply A, B, and C together to get a single 3×3 matrix that stores the entire composite transformation.</span></span> <span data-ttu-id="e34c8-163">Suponha que a ABC = D. Em seguida, um ponto multiplicado por D fornece o mesmo resultado que um ponto multiplicado por A, B e, em seguida, C.</span><span class="sxs-lookup"><span data-stu-id="e34c8-163">Suppose ABC = D. Then a point multiplied by D gives the same result as a point multiplied by A, then B, then C.</span></span>  
  
 <span data-ttu-id="e34c8-164">[2 1 1]D = [-2 5 1]</span><span class="sxs-lookup"><span data-stu-id="e34c8-164">[2 1 1]D = [-2 5 1]</span></span>  
  
 <span data-ttu-id="e34c8-165">A ilustração a seguir mostra as matrizes A, B, C e D.</span><span class="sxs-lookup"><span data-stu-id="e34c8-165">The following illustration shows the matrices A, B, C, and D.</span></span>  
  
 <span data-ttu-id="e34c8-166">![Transformações](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art12.gif "AboutGdip05_art12")</span><span class="sxs-lookup"><span data-stu-id="e34c8-166">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art12.gif "AboutGdip05_art12")</span></span>  
  
 <span data-ttu-id="e34c8-167">O fato de que a matriz de uma transformação composta pode ser formada pela multiplicação de matrizes de transformação individuais significa que qualquer sequência de transformações afins pode ser armazenada em uma única <xref:System.Drawing.Drawing2D.Matrix> objeto.</span><span class="sxs-lookup"><span data-stu-id="e34c8-167">The fact that the matrix of a composite transformation can be formed by multiplying the individual transformation matrices means that any sequence of affine transformations can be stored in a single <xref:System.Drawing.Drawing2D.Matrix> object.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e34c8-168">A ordem de uma transformação de composição é importante.</span><span class="sxs-lookup"><span data-stu-id="e34c8-168">The order of a composite transformation is important.</span></span> <span data-ttu-id="e34c8-169">Em geral, girar, dimensionar e converter não é o mesmo que dimensionar, girar e converter.</span><span class="sxs-lookup"><span data-stu-id="e34c8-169">In general, rotate, then scale, then translate is not the same as scale, then rotate, then translate.</span></span> <span data-ttu-id="e34c8-170">Da mesma forma, a ordem de multiplicação de matriz é importante.</span><span class="sxs-lookup"><span data-stu-id="e34c8-170">Similarly, the order of matrix multiplication is important.</span></span> <span data-ttu-id="e34c8-171">Em geral, ABC não é o mesmo que BAC.</span><span class="sxs-lookup"><span data-stu-id="e34c8-171">In general, ABC is not the same as BAC.</span></span>  
  
 <span data-ttu-id="e34c8-172">O <xref:System.Drawing.Drawing2D.Matrix> classe fornece vários métodos para criar uma transformação composta: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, e <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>.</span><span class="sxs-lookup"><span data-stu-id="e34c8-172">The <xref:System.Drawing.Drawing2D.Matrix> class provides several methods for building a composite transformation: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, and <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>.</span></span> <span data-ttu-id="e34c8-173">O exemplo a seguir cria a matriz de uma transformação de composição que primeiro gira 30 graus e, então, é dimensionada por um fator de 2 na direção y e movida em 5 unidades na direção x:</span><span class="sxs-lookup"><span data-stu-id="e34c8-173">The following example creates the matrix of a composite transformation that first rotates 30 degrees, then scales by a factor of 2 in the y direction, and then translates 5 units in the x direction:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 <span data-ttu-id="e34c8-174">A ilustração a seguir mostra a matriz.</span><span class="sxs-lookup"><span data-stu-id="e34c8-174">The following illustration shows the matrix.</span></span>  
  
 <span data-ttu-id="e34c8-175">![Transformações](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art13.gif "AboutGdip05_art13")</span><span class="sxs-lookup"><span data-stu-id="e34c8-175">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art13.gif "AboutGdip05_art13")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e34c8-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e34c8-176">See Also</span></span>  
 [<span data-ttu-id="e34c8-177">Sistemas de Coordenadas e Transformações</span><span class="sxs-lookup"><span data-stu-id="e34c8-177">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="e34c8-178">Usando Transformações no GDI+ Gerenciado</span><span class="sxs-lookup"><span data-stu-id="e34c8-178">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)