---
title: Elemento &lt;MethodInstantiation&gt; (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d741e8df8f2b8c6d90a1d867c73495a2ffd1304
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397787"
---
# <a name="ltmethodinstantiationgt-element-net-native"></a>Elemento &lt;MethodInstantiation&gt; (.NET Nativo)
Aplica a política de reflexão de tempo de execução a um método genérico construído.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Tipo de atributo|Descrição|  
|---------------|--------------------|-----------------|  
|`Name`|Geral|Atributo obrigatório. Especifica o nome do método.|  
|`Signature`|Geral|Atributo opcional. Especifica os parâmetros nomeados do método. Vários parâmetros nomeados são separados por vírgulas. O atributo `Signature` é usado para diferenciar métodos sobrecarregados.|  
|`Arguments`|Geral|Atributo obrigatório. Especifica os argumentos de tipo genérico. Se houver vários parâmetros, eles são separados por vírgulas.|  
|`Browse`|Reflexão|Atributo opcional. Controla consultas para obter informações sobre o método ou para enumerá-lo, mas não permite qualquer invocação dinâmica no tempo de execução.|  
|`Dynamic`|Reflexão|Atributo opcional. Controla o acesso do tempo de execução a um construtor ou método para habilitar a programação dinâmica. Essa política garante que um membro pode ser invocado dinamicamente no tempo de execução.|  
  
## <a name="name-attribute"></a>Atributo de nome  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*method_name*|O nome do método. O tipo do método é definido pelo elemento pai [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).|  
  
## <a name="signature-attribute"></a>Atributo de assinatura  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*method_signature*|Especifica os parâmetros nomeados do método. Se vários parâmetros estiverem presentes, eles são separados por vírgulas.|  
  
## <a name="arguments-attribute"></a>Atributo de argumentos  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*method_arguments*|Especifica os argumentos de tipo genérico. Se houver vários parâmetros, eles são separados por vírgulas. Cada argumento deve conter o nome do tipo totalmente qualificado.|  
  
## <a name="all-other-attributes"></a>Todos os outros atributos  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*policy_setting*|A configuração a ser aplicada a este tipo de política para o método. Os valores possíveis são `Auto`, `Excluded`, `Included` e `Required`. Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Aplica a política de reflexão a um tipo e todos os seus membros.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `<MethodInstantiation>` substitui a política de reflexão de tempo de execução do seu método genérico aberto correspondente.  
  
## <a name="see-also"></a>Consulte também  
 [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [Elemento \<Method>](../../../docs/framework/net-native/method-element-net-native.md)
