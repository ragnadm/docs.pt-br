---
title: "Método IHostTaskManager::BeginThreadAffinity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.BeginThreadAffinity
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6e382809d705e022e1e5431dfec6ace06d449b48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="b3b70-102">Método IHostTaskManager::BeginThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="b3b70-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="b3b70-103">Notifica o host que o código gerenciado está inserindo um período no qual a tarefa atual não deve ser movida para outro thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="b3b70-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3b70-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3b70-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b3b70-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b3b70-105">Return Value</span></span>  
  
|<span data-ttu-id="b3b70-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3b70-106">HRESULT</span></span>|<span data-ttu-id="b3b70-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3b70-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3b70-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3b70-108">S_OK</span></span>|<span data-ttu-id="b3b70-109">`BeginThreadAffinity`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="b3b70-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="b3b70-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b3b70-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b3b70-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b3b70-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b3b70-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b3b70-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b3b70-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="b3b70-113">The call timed out.</span></span>|  
|<span data-ttu-id="b3b70-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3b70-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b3b70-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b3b70-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b3b70-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b3b70-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b3b70-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="b3b70-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b3b70-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b3b70-118">E_FAIL</span></span>|<span data-ttu-id="b3b70-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b3b70-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b3b70-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b3b70-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b3b70-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b3b70-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3b70-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3b70-122">Remarks</span></span>  
 <span data-ttu-id="b3b70-123">O CLR chama normalmente `IHostTaskManager::BeginThreadAffinity` no contexto de uma chamada para <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b3b70-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b3b70-124">A tarefa atual não deve ser reagendada até que é feita uma chamada correspondente para [EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="b3b70-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="b3b70-125">Tarefas podem ser alternadas, mas quando eles são alternados novamente, eles devem ser atribuídos a mesmo thread do sistema operacional do qual eles foram alternados. Aninhadas chamadas para `BeginThreadAffinity` não têm nenhum efeito, porque se refere a chamada para a tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="b3b70-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3b70-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3b70-126">Requirements</span></span>  
 <span data-ttu-id="b3b70-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3b70-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3b70-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b3b70-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3b70-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b3b70-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3b70-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3b70-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b70-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3b70-131">See Also</span></span>  
 [<span data-ttu-id="b3b70-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="b3b70-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="b3b70-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="b3b70-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="b3b70-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="b3b70-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="b3b70-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="b3b70-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)