---
title: Cláusula Join (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: 2186954ab6536988271629c4feba0a40563bfc3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603906"
---
# <a name="join-clause-visual-basic"></a>Cláusula Join (Visual Basic)
Combina duas coleções em uma única coleção. A operação de junção é baseada em chaves correspondentes e usa o `Equals` operador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a>Partes  
 `element`  
 Necessário. A variável de controle para a coleção sendo unida.  
  
 `collection`  
 Necessário. A coleção a combinar com a coleção identificada no lado esquerdo do `Join` operador. Um `Join` cláusula pode ser aninhada em outro `Join` cláusula, ou em um `Group Join` cláusula.  
  
 `joinClause`  
 Opcional. Um ou mais adicionais `Join` mais cláusulas refinar a consulta.  
  
 `groupJoinClause`  
 Opcional. Um ou mais adicionais `Group Join` mais cláusulas refinar a consulta.  
  
 `key1``Equals``key2`  
 Necessário. Identifica chaves para as coleções que estão sendo combinadas. Você deve usar o `Equals` operador para comparar chaves das coleções que estão sendo combinadas. Você pode combinar condições de junção usando o `And` operador para identificar várias chaves. `key1` deve ser da coleção no lado esquerdo do `Join` operador. `key2` deve ser da coleção no lado direito do `Join` operador.  
  
 As chaves usadas na condição de junção podem ser expressões que incluem mais de um item da coleção. No entanto, cada expressão de chave pode conter apenas os itens da sua respectiva coleção.  
  
## <a name="remarks"></a>Comentários  
 O `Join` cláusula combina duas coleções com base na correspondência de valores de chave das coleções que estão sendo combinadas. A coleção resultante pode conter qualquer combinação de valores da coleção no lado esquerdo do `Join` operador e na coleção identificada no `Join` cláusula. A consulta retornará apenas os resultados para o qual a condição especificada pelo `Equals` operador for atendido. Isso é equivalente a um `INNER JOIN` em SQL.  
  
 Você pode usar várias `Join` cláusulas em uma consulta para unir duas ou mais coleções em uma única coleção.  
  
 Você pode executar uma junção implícita para combinar coleções sem a `Join` cláusula. Para fazer isso, inclua várias `In` cláusulas em seu `From` cláusula e especifique um `Where` cláusula que identifica as chaves que você deseja usar para a junção.  
  
 Você pode usar o `Group Join` cláusula para combinar coleções em uma única coleção hierárquica. Isso é como uma `LEFT OUTER JOIN` em SQL.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir executa uma junção implícita para combinar uma lista de clientes com seus pedidos.  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir une duas coleções usando o `Join` cláusula.  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 Este exemplo produzirá uma saída semelhante à seguinte:  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir une duas coleções usando o `Join` cláusula com duas colunas de chave.  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 O exemplo produzirá uma saída semelhante à seguinte:  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
