---
title: Consultas em tabelas cruzadas (LINQ to DataSet)
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
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d0b829840257dc2b3b4bbf0b8c3a294a77060e2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="cross-table-queries-linq-to-dataset"></a><span data-ttu-id="ded81-102">Consultas em tabelas cruzadas (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="ded81-102">Cross-Table Queries (LINQ to DataSet)</span></span>
<span data-ttu-id="ded81-103">Além de consultar uma única tabela, você também pode executar consultas de tabela cruzada em [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ded81-103">In addition to querying a single table, you can also perform cross-table queries in [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="ded81-104">Isso é feito usando um *junção*.</span><span class="sxs-lookup"><span data-stu-id="ded81-104">This is done by using a *join*.</span></span> <span data-ttu-id="ded81-105">Uma junção é a associação de objetos em uma fonte de dados com objetos que compartilham um atributo comum em outra fonte de dados, como um produto ou entre em contato com a ID.</span><span class="sxs-lookup"><span data-stu-id="ded81-105">A join is the association of objects in one data source with objects that share a common attribute in another data source, such as a product or contact ID.</span></span> <span data-ttu-id="ded81-106">Em programação orientada a objeto, relações entre objetos são relativamente fáceis de navegar porque cada objeto tem um membro que faz referência a outro objeto.</span><span class="sxs-lookup"><span data-stu-id="ded81-106">In object-oriented programming, relationships between objects are relatively easy to navigate because each object has a member that references another object.</span></span> <span data-ttu-id="ded81-107">Nas tabelas de banco de dados externo, no entanto, à navegação por relações não é tão simples.</span><span class="sxs-lookup"><span data-stu-id="ded81-107">In external database tables, however, navigating relationships is not as straightforward.</span></span> <span data-ttu-id="ded81-108">Tabelas de banco de dados não contêm relacionamentos internos.</span><span class="sxs-lookup"><span data-stu-id="ded81-108">Database tables do not contain built-in relationships.</span></span> <span data-ttu-id="ded81-109">Nesses casos, a operação de junção pode ser usada para fazer a correspondência de elementos em cada origem.</span><span class="sxs-lookup"><span data-stu-id="ded81-109">In these cases, the join operation can be used to match elements from each source.</span></span> <span data-ttu-id="ded81-110">Por exemplo, considerando duas tabelas que contêm informações de produto e de vendas, você pode usar uma operação de união para corresponder as informações de vendas e produtos para a mesma ordem de venda.</span><span class="sxs-lookup"><span data-stu-id="ded81-110">For example, given two tables that contain product information and sales information, you could use a join operation to match sales information and products for the same sales order.</span></span>  
  
 <span data-ttu-id="ded81-111">O [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] framework fornece dois operadores de junção, <xref:System.Linq.Enumerable.Join%2A> e <xref:System.Linq.Enumerable.GroupJoin%2A>.</span><span class="sxs-lookup"><span data-stu-id="ded81-111">The [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] framework provides two join operators, <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="ded81-112">Esses operadores fazem *equi joins*: ou seja, junções que correspondem a dados de duas fontes somente quando as chaves são iguais.</span><span class="sxs-lookup"><span data-stu-id="ded81-112">These operators perform *equi-joins*: that is, joins that match two data sources only when their keys are equal.</span></span> <span data-ttu-id="ded81-113">(Por outro lado, o [!INCLUDE[tsql](../../../../includes/tsql-md.md)] dá suporte a operadores de junção além do `equals`, como o operador `less than`.)</span><span class="sxs-lookup"><span data-stu-id="ded81-113">(By contrast, [!INCLUDE[tsql](../../../../includes/tsql-md.md)] supports join operators other than `equals`, such as the `less than` operator.)</span></span>  
  
 <span data-ttu-id="ded81-114">Em termos de banco de dados relacional, o <xref:System.Linq.Enumerable.Join%2A> implementa uma junção interna.</span><span class="sxs-lookup"><span data-stu-id="ded81-114">In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join.</span></span> <span data-ttu-id="ded81-115">Uma junção interna é um tipo de junção na qual apenas os objetos que têm uma correspondência no conjunto de dados oposto são retornados.</span><span class="sxs-lookup"><span data-stu-id="ded81-115">An inner join is a type of join in which only those objects that have a match in the opposite data set are returned.</span></span>  
  
 <span data-ttu-id="ded81-116">O <xref:System.Linq.Enumerable.GroupJoin%2A> operadores não têm equivalente direto em termos de banco de dados relacional; elas implementam um superconjunto de junções internas e externas esquerdas.</span><span class="sxs-lookup"><span data-stu-id="ded81-116">The <xref:System.Linq.Enumerable.GroupJoin%2A> operators have no direct equivalent in relational database terms; they implement a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="ded81-117">Uma junção externa esquerda é uma associação que retorna cada elemento da coleção primeira (à esquerda), mesmo se ele não tem nenhum elemento correlacionado a segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="ded81-117">A left outer join is a join that returns each element of the first (left) collection, even if it has no correlated elements in the second collection.</span></span>  
  
 <span data-ttu-id="ded81-118">Para obter mais informações sobre junções, consulte [operações Join](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).</span><span class="sxs-lookup"><span data-stu-id="ded81-118">For more information about joins, see [Join Operations](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ded81-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ded81-119">Example</span></span>  
 <span data-ttu-id="ded81-120">O exemplo a seguir executa um junção tradicional de tabelas `SalesOrderHeader` e `SalesOrderDetail` do banco de dados de exemplo AdventureWorks para obter pedidos online do mês de agosto.</span><span class="sxs-lookup"><span data-stu-id="ded81-120">The following example performs a traditional join of the `SalesOrderHeader` and `SalesOrderDetail` tables from the AdventureWorks sample database to obtain online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="ded81-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ded81-121">See Also</span></span>  
 [<span data-ttu-id="ded81-122">Consultando DataSets</span><span class="sxs-lookup"><span data-stu-id="ded81-122">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="ded81-123">Consultas de tabela única</span><span class="sxs-lookup"><span data-stu-id="ded81-123">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 [<span data-ttu-id="ded81-124">Consultando DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="ded81-124">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [<span data-ttu-id="ded81-125">Operações join</span><span class="sxs-lookup"><span data-stu-id="ded81-125">Join Operations</span></span>](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)  
 [<span data-ttu-id="ded81-126">LINQ para exemplos de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="ded81-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)