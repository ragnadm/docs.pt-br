---
title: Enumeração CorSetENC
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e09bf424a41445f7e36397775d1578cdf4e7e75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442781"
---
# <a name="corsetenc-enumeration"></a>Enumeração CorSetENC
Contém valores usados para influenciar o comportamento durante a geração de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`MDSetENCOn`|Obsoleto.|  
|`MDSetENCOff`|Obsoleto.|  
|`MDUpdateENC`|Indica que, enquanto os metadados podem ser atualizados, tokens não podem ser movidos.|  
|`MDUpdateFull`|Indica que os tokens podem ser movidos durante as atualizações.|  
|`MDUpdateExtension`|Indica que as atualizações podem consistir apenas de adições. Tokens não podem ser movidos.|  
|`MDUpdateIncremental`|Indica que a compilação é incremental.|  
|`MDUpdateDelta`|Indica que apenas os metadados alterados devem ser salvo.|  
|`MDUpdateMask`|Inclui `MDUpdateENC`, `MDUpdateFull` e `MDUpdateIncremental`.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
