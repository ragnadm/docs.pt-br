---
title: "Elementos de tipo em uma sequência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2f4f89c1391b6582d77acccb8b256bef617ecff3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="8823f-102">Elementos de tipo em uma sequência</span><span class="sxs-lookup"><span data-stu-id="8823f-102">Sort Elements in a Sequence</span></span>
<span data-ttu-id="8823f-103">Use o operador de <xref:System.Linq.Enumerable.OrderBy%2A> para classificar uma sequência de acordo com um ou mais chaves.</span><span class="sxs-lookup"><span data-stu-id="8823f-103">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8823f-104">foi projetado para oferecer suporte a ordenação por tipos primitivos simples, como `string`, `int`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="8823f-104"> is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="8823f-105">Não suporta classificação para várias classes avaliadas complexo, como tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="8823f-105">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="8823f-106">Também não suporta tipos de dados de `byte` .</span><span class="sxs-lookup"><span data-stu-id="8823f-106">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8823f-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8823f-107">Example</span></span>  
 <span data-ttu-id="8823f-108">O exemplo a seguir classe `Employees` a data de aluguer.</span><span class="sxs-lookup"><span data-stu-id="8823f-108">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="8823f-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8823f-109">Example</span></span>  
 <span data-ttu-id="8823f-110">O exemplo a seguir usa `where` para classificar `Orders` enviado a `London` por frete.</span><span class="sxs-lookup"><span data-stu-id="8823f-110">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="8823f-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8823f-111">Example</span></span>  
 <span data-ttu-id="8823f-112">O exemplo a seguir classe `Products` pelo preço unitário de mais alto para o menor.</span><span class="sxs-lookup"><span data-stu-id="8823f-112">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="8823f-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8823f-113">Example</span></span>  
 <span data-ttu-id="8823f-114">O exemplo a seguir usa um composto `OrderBy` para classificar por `Customers` cidade e em seguida pelo nome de contato.</span><span class="sxs-lookup"><span data-stu-id="8823f-114">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="8823f-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8823f-115">Example</span></span>  
 <span data-ttu-id="8823f-116">O exemplo a seguir classe pedidos de `EmployeeID 1` por navio- ao país, e mais alto em transmitir pelo menor.</span><span class="sxs-lookup"><span data-stu-id="8823f-116">The following example sorts Orders from `EmployeeID 1` by ship-to country, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="8823f-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8823f-117">Example</span></span>  
 <span data-ttu-id="8823f-118">O exemplo a seguir combina <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, e os operadores de <xref:System.Linq.Enumerable.GroupBy%2A> para localizar `Products` que têm o preço unitário o maior em cada categoria, e classes no grupo pela ID da categoria</span><span class="sxs-lookup"><span data-stu-id="8823f-118">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="8823f-119">Se você executa a consulta anterior com o base de dados de exemplo Northwind, os resultados assemelhar-se-ão o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8823f-119">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="8823f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8823f-120">See Also</span></span>  
 [<span data-ttu-id="8823f-121">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="8823f-121">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="8823f-122">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="8823f-122">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)</span></span>