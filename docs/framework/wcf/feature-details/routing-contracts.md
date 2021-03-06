---
title: Contratos de roteamento
ms.date: 03/30/2017
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
ms.openlocfilehash: 64ebb673b17159967bb4acd4e3a5e0a3f89142f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494248"
---
# <a name="routing-contracts"></a>Contratos de roteamento
Contratos de roteamento definem os padrões de mensagens que o serviço de roteamento pode processar.  Cada contrato está sem especificação de tipo e permite que o serviço receber uma mensagem sem o conhecimento do esquema de mensagem ou ação. Isso permite que o serviço de roteamento genericamente rotear mensagens sem configuração adicional para as especificações das mensagens subjacentes que está sendo encaminhada.  
  
## <a name="routing-contracts"></a>Contratos de roteamento  
 Como o serviço de roteamento aceita um objeto de mensagem WCF genérico, o aspecto mais importante ao selecionar um contrato é a forma do canal que será usado ao se comunicar com clientes e serviços. Durante o processamento de mensagens, o serviço de roteamento usa bombas de mensagens simétrico, geralmente que a forma do contrato de entrada deve corresponder à forma do contrato de saída. No entanto, há casos onde o dispatcher do modelo de serviço pode modificar as formas, como quando o dispatcher converte um canal duplex em um canal de solicitação-resposta ou remove o suporte de sessão de um canal quando não é necessário e não está sendo usado (ou seja Quando **SessionMode**, converter um **IInputSessionChannel** em uma **IInputChannel**).  
  
 Para dar suporte a esses bombas de mensagens, o serviço de roteamento fornece contratos no <xref:System.ServiceModel.Routing> namespace, que deve ser usada ao definir os pontos de extremidade de serviço usados pelo serviço de roteamento. Esses contratos são sem tipo, que permite que o recebimento de qualquer tipo de mensagem ou uma ação e permite que o serviço de roteamento tratar mensagens sem o conhecimento do esquema de mensagem específica. Para obter mais informações sobre os contratos usados pelo serviço de roteamento, consulte [contratos de roteamento](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Os contratos fornecidos pelo serviço de roteamento estão localizados no <xref:System.ServiceModel.Routing> namespace e são descritas na tabela a seguir.  
  
|Contrato|Forma|Forma de canal|  
|--------------|-----------|-------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode = SessionMode<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputChannel -> IOutputChannel|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|SessionMode = SessionMode<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputSessionChannel -> IOutputSessionChannel|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode = SessionMode<br /><br /> AsyncPattern = true|IReplyChannel -> IRequestChannel|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode=SessionMode.Required<br /><br /> CallbackContract=typeof(ISimplexSession)<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true<br /><br /> TransactionFlow(TransactionFlowOption.Allowed)|IDuplexSessionChannel -> IDuplexSessionChannel|  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de roteamento](http://msdn.microsoft.com/library/5ac8718c-bcef-456f-bfd5-1e60a30d6eaa)  
 [Introdução ao roteamento](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
