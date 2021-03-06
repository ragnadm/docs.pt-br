---
title: '- (Negativo) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 5d1726be6a4a59891646d05b344f59962d548c75
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765146"
---
# <a name="--negative-entity-sql"></a>- (Negativo) (Entity SQL)
Retorna o negativo o valor de uma expressão numérica.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
- expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão válida de qualquer dos tipos de dados numéricos.  
  
## <a name="result-types"></a>Tipos de resultado  
 O tipo de dados de `expression`.  
  
## <a name="remarks"></a>Comentários  
 Se `expression` é um tipo sem sinal, o tipo do resultado será o tipo com sinal que relaciona o melhor para o tipo de `expression`. Por exemplo, se `expression` é de bytes de tipo, um valor do tipo Int16 será retornado.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa o operador - aritmético para retornar o negativo o valor de uma expressão numérica. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
