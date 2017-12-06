---
title: "Quando escolher o .NET Framework para contêineres do Docker"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Quando escolher o .NET Framework para contêineres do Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1bf1f055f040e7f3dc575b7a04140ebf0c599f98
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a><span data-ttu-id="ef1bd-104">Quando escolher o .NET Framework para contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="ef1bd-104">When to choose .NET Framework for Docker containers</span></span>

<span data-ttu-id="ef1bd-105">Enquanto o .NET Core oferece benefícios significativos para novos aplicativos e padrões de aplicativo, do .NET Framework continuará a ser uma boa opção para muitos cenários existentes.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-105">While .NET Core offers significant benefits for new applications and application patterns, .NET Framework will continue to be a good choice for many existing scenarios.</span></span>

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a><span data-ttu-id="ef1bd-106">Migrar aplicativos existentes diretamente para um contêiner do Windows Server</span><span class="sxs-lookup"><span data-stu-id="ef1bd-106">Migrating existing applications directly to a Windows Server container</span></span>

<span data-ttu-id="ef1bd-107">Você talvez queira usar contêineres do Docker apenas para simplificar a implantação, mesmo se você não estiver criando microservices.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-107">You might want to use Docker containers just to simplify deployment, even if you are not creating microservices.</span></span> <span data-ttu-id="ef1bd-108">Por exemplo, talvez você queira aumentar seu fluxo de trabalho de DevOps com o Docker, contêineres pode fornecer melhor teste isolada ambientes e também pode eliminar problemas de implantação causados por dependências ausentes, quando você move para um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-108">For example, perhaps you want to improve your DevOps workflow with Docker—containers can give you better isolated test environments and can also eliminate deployment issues caused by missing dependencies when you move to a production environment.</span></span> <span data-ttu-id="ef1bd-109">Em casos assim, mesmo se você estiver implantando um aplicativo monolítico, faz sentido usar Docker e contêineres do Windows para seus aplicativos do .NET Framework atuais.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-109">In cases like these, even if you are deploying a monolithic application, it makes sense to use Docker and Windows Containers for your current .NET Framework applications.</span></span>

<span data-ttu-id="ef1bd-110">Na maioria dos casos para esse cenário, você não precisará migrar seus aplicativos existentes para o núcleo do .NET; Você pode usar contêineres do Docker que incluem o tradicional do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-110">In most cases for this scenario, you will not need to migrate your existing applications to .NET Core; you can use Docker containers that include the traditional .NET Framework.</span></span> <span data-ttu-id="ef1bd-111">No entanto, uma abordagem recomendada é usar o .NET Core como estender um aplicativo existente, como gravar um novo serviço no núcleo do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-111">However, a recommended approach is to use .NET Core as you extend an existing application, such as writing a new service in ASP.NET Core.</span></span>

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a><span data-ttu-id="ef1bd-112">Usando bibliotecas .NET de terceiros ou pacotes do NuGet não está disponíveis para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef1bd-112">Using third-party .NET libraries or NuGet packages not available for .NET Core</span></span>

<span data-ttu-id="ef1bd-113">Bibliotecas de terceiros estão adotando rapidamente o [.NET padrão](https://docs.microsoft.com/dotnet/standard/net-standard), que permite que o código de compartilhamento em todos os tipos do .NET, incluindo o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-113">Third-party libraries are quickly embracing the [.NET Standard](https://docs.microsoft.com/dotnet/standard/net-standard), which enables code sharing across all .NET flavors, including .NET Core.</span></span> <span data-ttu-id="ef1bd-114">Com o .NET padrão biblioteca 2.0 e além da superfície da API compatibilidade nas estruturas diferentes se tornou significativamente maior e no .NET Core 2.0 aplicativos podem também fazer referência direta bibliotecas existentes do .NET Framework (consulte [compatível shim](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work)).</span><span class="sxs-lookup"><span data-stu-id="ef1bd-114">With the .NET Standard Library 2.0 and beyond the API surface compatibility across different frameworks has become significantly larger and in .NET Core 2.0 applications can also directly reference existing .NET Framework libraries (see [compat shim](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work)).</span></span>

<span data-ttu-id="ef1bd-115">No entanto, mesmo com esse progressão excepcional desde padrão do .NET 2.0 e o núcleo do .NET 2.0, pode haver casos em que determinados pacotes do NuGet precisam a execução do Windows e podem não oferecer suporte a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-115">However, even with that exceptional progression since .NET Standard 2.0 and .NET Core 2.0, there might be cases where certain NuGet packages need Windows to run and might not support .NET Core.</span></span> <span data-ttu-id="ef1bd-116">Se esses pacotes são essenciais para o seu aplicativo, você precisará usar o .NET Framework em contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-116">If those packages are critical for your application, then you will need to use .NET Framework on Windows Containers.</span></span>

## <a name="usingnet-technologies-not-available-for-net-core"></a><span data-ttu-id="ef1bd-117">Tecnologias de Using.NET não está disponíveis para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef1bd-117">Using.NET technologies not available for .NET Core</span></span> 

<span data-ttu-id="ef1bd-118">Algumas tecnologias do .NET Framework não estão disponíveis na versão atual do núcleo do .NET (versão 2.0 redação deste artigo).</span><span class="sxs-lookup"><span data-stu-id="ef1bd-118">Some .NET Framework technologies are not available in the current version of .NET Core (version 2.0 as of this writing).</span></span> <span data-ttu-id="ef1bd-119">Algumas delas estarão disponíveis em versões posteriores do .NET Core (.NET Core 2. x), mas outras não se aplicam para o novo aplicativo padrões direcionados ao .NET Core e nunca podem estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-119">Some of them will be available in later .NET Core releases (.NET Core 2.x), but others do not apply to the new application patterns targeted by .NET Core and might never be available.</span></span>

<span data-ttu-id="ef1bd-120">A lista a seguir mostra a maioria das tecnologias que não estão disponíveis no núcleo do .NET 2.0:</span><span class="sxs-lookup"><span data-stu-id="ef1bd-120">The following list shows most of the technologies that are not available in .NET Core 2.0:</span></span>

-   <span data-ttu-id="ef1bd-121">Web Forms do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-121">ASP.NET Web Forms.</span></span> <span data-ttu-id="ef1bd-122">Essa tecnologia só está disponível no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-122">This technology is only available on .NET Framework.</span></span> <span data-ttu-id="ef1bd-123">Atualmente, não há planos para trazer os Web Forms do ASP.NET para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-123">Currently there are no plans to bring ASP.NET Web Forms to .NET Core.</span></span>

-   <span data-ttu-id="ef1bd-124">Serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-124">WCF services.</span></span> <span data-ttu-id="ef1bd-125">Mesmo quando um [biblioteca de cliente WCF](https://github.com/dotnet/wcf) está disponível para consumir os serviços WCF do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-125">Even when a [WCF-Client library](https://github.com/dotnet/wcf) is available to consume WCF services from .NET Core.</span></span> <span data-ttu-id="ef1bd-126">Desde meados de 2017, a implementação do servidor WCF só está disponível no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-126">as of mid-2017, the WCF server implementation is only available on .NET Framework.</span></span> <span data-ttu-id="ef1bd-127">Esse cenário pode ser considerado para futuras versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-127">This scenario might be considered for future releases of .NET Core.</span></span>

-   <span data-ttu-id="ef1bd-128">Serviços relacionados ao fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-128">Workflow-related services.</span></span> <span data-ttu-id="ef1bd-129">(Anteriormente conhecido como ADO.NET Data Services) do WCF Data Services, serviços de fluxo de trabalho (WCF + WF em um único serviço) e Windows Workflow Foundation (WF) só estão disponíveis no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-129">Windows Workflow Foundation (WF), Workflow Services (WCF + WF in a single service), and WCF Data Services (formerly known as ADO.NET Data Services) are only available on .NET Framework.</span></span> <span data-ttu-id="ef1bd-130">Atualmente, não há nenhum plano para colocá-los em .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-130">There are currently no plans to bring them to .NET Core.</span></span>

<span data-ttu-id="ef1bd-131">Além das tecnologias listadas no oficial [roteiro .NET Core](https://github.com/aspnet/Home/wiki/Roadmap), outros recursos podem ser movidos para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-131">In addition to the technologies listed in the official [.NET Core roadmap](https://github.com/aspnet/Home/wiki/Roadmap), other features might be ported to .NET Core.</span></span> <span data-ttu-id="ef1bd-132">Para obter uma lista completa, examine os itens marcados como [porta núcleo](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) no site do CoreFX GitHub.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-132">For a full list, look at the items tagged as [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) on the CoreFX GitHub site.</span></span> <span data-ttu-id="ef1bd-133">Observe que essa lista não representa um compromisso da Microsoft para trazer esses componentes para .NET Core — os itens simplesmente capturar solicitações da comunidade.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-133">Note that this list does not represent a commitment from Microsoft to bring those components to .NET Core—the items simply capture requests from the community.</span></span> <span data-ttu-id="ef1bd-134">Se você gosta qualquer um dos componentes listados acima, considere participar de discussões no GitHub para que sua voz pode ser ouvido.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-134">If you care about any of the components listed above, consider participating in the discussions on GitHub so that your voice can be heard.</span></span> <span data-ttu-id="ef1bd-135">E se você achar que algo está faltando, [envie uma nova questão no repositório do CoreFX](https://github.com/dotnet/corefx/issues/new).</span><span class="sxs-lookup"><span data-stu-id="ef1bd-135">And if you think something is missing, please [file a new issue in the CoreFX repository](https://github.com/dotnet/corefx/issues/new).</span></span>

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a><span data-ttu-id="ef1bd-136">Usando uma plataforma ou uma API que não oferece suporte a .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef1bd-136">Using a platform or API that does not support .NET Core</span></span>

<span data-ttu-id="ef1bd-137">Algumas plataformas de terceiros ou Microsoft não dão suporte a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-137">Some Microsoft or third-party platforms do not support .NET Core.</span></span> <span data-ttu-id="ef1bd-138">Por exemplo, alguns serviços do Azure fornecem um SDK que ainda não está disponível para consumo no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-138">For example, some Azure services provide an SDK that is not yet available for consumption on .NET Core.</span></span> <span data-ttu-id="ef1bd-139">Isso é temporário, porque todos os serviços do Azure ainda usará .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-139">This is temporary, because all Azure services will eventually use .NET Core.</span></span> <span data-ttu-id="ef1bd-140">Por exemplo, o [SDK do DocumentDB do Azure para .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) foi lançado como uma visualização em 16 de novembro de 2016, mas agora está disponível (GA) como uma versão estável.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-140">For example, the [Azure DocumentDB SDK for .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) was released as a preview on November 16, 2016, but it is now generally available (GA) as a stable version.</span></span>

<span data-ttu-id="ef1bd-141">Enquanto isso, se qualquer plataforma ou o serviço no Azure ainda não dá suporte .NET Core com seu cliente de API, você pode usar a API REST equivalente do SDK de cliente ou o serviço do Azure no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-141">In the meantime, if any platform or service in Azure still doesn’t support .NET Core with its client API, you can use the equivalent REST API from the Azure service or the client SDK on .NET Framework.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ef1bd-142">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="ef1bd-142">Additional resources</span></span>

-   <span data-ttu-id="ef1bd-143">**Guia de núcleo do .NET**
    [*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)</span><span class="sxs-lookup"><span data-stu-id="ef1bd-143">**.NET Core Guide**
[*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)</span></span>

-   <span data-ttu-id="ef1bd-144">**Movimentando do .NET Framework para .NET Core**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)</span><span class="sxs-lookup"><span data-stu-id="ef1bd-144">**Porting from .NET Framework to .NET Core**
[*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)</span></span>

-   <span data-ttu-id="ef1bd-145">**.NET framework no guia de Docker**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)</span><span class="sxs-lookup"><span data-stu-id="ef1bd-145">**.NET Framework on Docker Guide**
[*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)</span></span>

-   <span data-ttu-id="ef1bd-146">**Visão geral dos componentes do .NET**
    [*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)</span><span class="sxs-lookup"><span data-stu-id="ef1bd-146">**.NET Components Overview**
[*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="ef1bd-147">[Anterior] (net-core-contêiner-scenarios.md) [Avançar] (contêiner-estrutura-escolha-factors.md)</span><span class="sxs-lookup"><span data-stu-id="ef1bd-147">[Previous] (net-core-container-scenarios.md) [Next] (container-framework-choice-factors.md)</span></span>