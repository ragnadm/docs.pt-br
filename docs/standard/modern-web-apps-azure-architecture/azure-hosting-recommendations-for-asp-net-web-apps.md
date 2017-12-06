---
title: "Recomendações para aplicativos web do ASP.NET Core de hospedagem do Azure"
description: "Projetar aplicativos Web modernos com ASP.NET Core e o Azure | Recomendações para os aplicativos web ASP.NET de hospedagem do Azure"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: c361a28321ec9dcbfee1db8036757632a5d81f7c
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2017
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a><span data-ttu-id="d19f5-103">Recomendações para aplicativos Web do ASP.NET Core de hospedagem do Azure</span><span class="sxs-lookup"><span data-stu-id="d19f5-103">Azure Hosting Recommendations for ASP.NET Core Web Apps</span></span>

> <span data-ttu-id="d19f5-104">"Líderes de linha de negócios everywhere estão ignorando os departamentos de TI para obter aplicativos da nuvem (também conhecido como SaaS) e pagar por eles como seriam em uma assinatura de revista.</span><span class="sxs-lookup"><span data-stu-id="d19f5-104">"Line-of-business leaders everywhere are bypassing IT departments to get applications from the cloud (aka SaaS) and paying for them like they would a magazine subscription.</span></span> <span data-ttu-id="d19f5-105">E quando o serviço não é mais necessário, pode cancelar a assinatura com nenhum equipamento deixado no canto."</span><span class="sxs-lookup"><span data-stu-id="d19f5-105">And when the service is no longer required, they can cancel the subscription with no equipment left unused in the corner."</span></span>  
> <span data-ttu-id="d19f5-106">_\-Daryl Plummer, analista da Gartner_</span><span class="sxs-lookup"><span data-stu-id="d19f5-106">_\- Daryl Plummer, Gartner analyst_</span></span>

## <a name="summary"></a><span data-ttu-id="d19f5-107">Resumo</span><span class="sxs-lookup"><span data-stu-id="d19f5-107">Summary</span></span>

<span data-ttu-id="d19f5-108">Tudo o que seu aplicativo necessidades e arquitetura, do Windows Azure pode dar suporte a ele.</span><span class="sxs-lookup"><span data-stu-id="d19f5-108">Whatever your application's needs and architecture, Windows Azure can support it.</span></span> <span data-ttu-id="d19f5-109">Suas necessidades de hospedagem podem ser tão simples quanto um site estático para um aplicativo sofisticado extremamente composto de dezenas de serviços.</span><span class="sxs-lookup"><span data-stu-id="d19f5-109">Your hosting needs can be as simple as a static web site to an extremely sophisticated application made up of dozens of services.</span></span> <span data-ttu-id="d19f5-110">Para aplicativos do ASP.NET Core monolítico web e serviços de suporte, há várias configurações bem conhecidas que são recomendadas.</span><span class="sxs-lookup"><span data-stu-id="d19f5-110">For ASP.NET Core monolithic web applications and supporting services, there are several well-known configurations that are recommended.</span></span> <span data-ttu-id="d19f5-111">As recomendações a seguir são agrupadas de acordo com o tipo de recurso a ser hospedado completo se os dados, aplicativos ou processos individuais.</span><span class="sxs-lookup"><span data-stu-id="d19f5-111">The recommendations below are grouped according to the kind of resource to be hosted, whether full applications, individual processes, or data.</span></span>

## <a name="web-applications"></a><span data-ttu-id="d19f5-112">Aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="d19f5-112">Web Applications</span></span>

<span data-ttu-id="d19f5-113">Aplicativos da Web podem ser hospedados com:</span><span class="sxs-lookup"><span data-stu-id="d19f5-113">Web applications can be hosted with:</span></span>

-   <span data-ttu-id="d19f5-114">Aplicativos do serviço de aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="d19f5-114">App Service Web Apps</span></span>

-   <span data-ttu-id="d19f5-115">Contêineres</span><span class="sxs-lookup"><span data-stu-id="d19f5-115">Containers</span></span>

-   <span data-ttu-id="d19f5-116">Malha do serviço do Azure</span><span class="sxs-lookup"><span data-stu-id="d19f5-116">Azure Service Fabric</span></span>

-   <span data-ttu-id="d19f5-117">Máquinas virtuais (VMs)</span><span class="sxs-lookup"><span data-stu-id="d19f5-117">Virtual Machines (VMs)</span></span>

<span data-ttu-id="d19f5-118">Desses, o serviço de aplicativo Web de aplicativos são a abordagem recomendada para a maioria dos cenários.</span><span class="sxs-lookup"><span data-stu-id="d19f5-118">Of these, App Service Web Apps are the recommended approach for most scenarios.</span></span> <span data-ttu-id="d19f5-119">Para arquiteturas de microsserviço, considere uma abordagem baseada no contêiner ou do service fabric.</span><span class="sxs-lookup"><span data-stu-id="d19f5-119">For microservice architectures, consider a container-based approach, or service fabric.</span></span> <span data-ttu-id="d19f5-120">Se você precisar de mais controle sobre os computadores executando o aplicativo, considere a possibilidade de máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="d19f5-120">If you need more control over the machines running your application, consider Azure Virtual Machines.</span></span>

### <a name="app-service-web-apps"></a><span data-ttu-id="d19f5-121">Aplicativos do serviço de aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="d19f5-121">App Service Web Apps</span></span>

<span data-ttu-id="d19f5-122">Os aplicativos do serviço de aplicativo Web oferece uma plataforma de totalmente gerenciada otimizada para aplicativos web de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="d19f5-122">App Service Web Apps offers a fully managed platform optimized for hosting web applications.</span></span> <span data-ttu-id="d19f5-123">É um platform-as-a-service(PaaS) oferta que permite que você se concentre em sua lógica de negócios, enquanto o Azure se encarrega da infraestrutura necessária para executar e dimensionar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d19f5-123">It is a platform-as-a-service(PaaS) offering that lets you focus on your business logic, while Azure takes care of the infrastructure needed to run and scale the app.</span></span> <span data-ttu-id="d19f5-124">Alguns dos principais recursos do serviço de aplicativo Web de aplicativos:</span><span class="sxs-lookup"><span data-stu-id="d19f5-124">Some key features of App Service Web Apps:</span></span>

-   <span data-ttu-id="d19f5-125">Otimização de DevOps (integração contínua e entrega, vários ambientes, A / B testes, suporte a script)</span><span class="sxs-lookup"><span data-stu-id="d19f5-125">DevOps optimization (continuous integration and delivery, multiple environments, A/B testing, scripting support)</span></span>

-   <span data-ttu-id="d19f5-126">Escala global e alta disponibilidade</span><span class="sxs-lookup"><span data-stu-id="d19f5-126">Global scale and high availability</span></span>

-   <span data-ttu-id="d19f5-127">Conexões com plataformas de SaaS e seus dados no local</span><span class="sxs-lookup"><span data-stu-id="d19f5-127">Connections to SaaS platforms and your on-premises data</span></span>

-   <span data-ttu-id="d19f5-128">Segurança e conformidade</span><span class="sxs-lookup"><span data-stu-id="d19f5-128">Security and compliance</span></span>

-   <span data-ttu-id="d19f5-129">integração com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d19f5-129">Visual Studio integration</span></span>

<span data-ttu-id="d19f5-130">Serviço de aplicativo do Azure é a melhor opção para a maioria dos aplicativos web.</span><span class="sxs-lookup"><span data-stu-id="d19f5-130">Azure App Service is the best choice for most web apps.</span></span> <span data-ttu-id="d19f5-131">Gerenciamento e implantação são integradas à plataforma, sites podem ser dimensionados rapidamente para lidar com cargas de tráfego intenso e o Gerenciador de tráfego e balanceamento de carga interna fornecer alta disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="d19f5-131">Deployment and management are integrated into the platform, sites can scale quickly to handle high traffic loads, and the built-in load balancing and traffic manager provide high availability.</span></span> <span data-ttu-id="d19f5-132">Você pode mover os sites existentes para o serviço de aplicativo do Azure com facilidade usando uma ferramenta de migração on-line, usar um aplicativo de código-fonte aberto da Galeria de aplicativos da Web, ou criar um novo site usando a estrutura e as ferramentas de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="d19f5-132">You can move existing sites to Azure App Service easily with an online migration tool, use an open-source app from the Web Application Gallery, or create a new site using the framework and tools of your choice.</span></span> <span data-ttu-id="d19f5-133">O recurso WebJobs facilita a adicionar um trabalho em segundo plano para seu aplicativo da web do serviço de aplicativo de processamento.</span><span class="sxs-lookup"><span data-stu-id="d19f5-133">The WebJobs feature makes it easy to add background job processing to your App Service web app.</span></span>

### <a name="containers-and-azure-container-service"></a><span data-ttu-id="d19f5-134">Contêineres e serviço de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="d19f5-134">Containers and Azure Container Service</span></span>

<span data-ttu-id="d19f5-135">Serviço de contêiner do Azure simplifica a criar, configurar e gerenciar um cluster de máquinas virtuais que são pré-configurados para executar aplicativos em contêineres.</span><span class="sxs-lookup"><span data-stu-id="d19f5-135">Azure Container Service makes it simpler for you to create, configure, and manage a cluster of virtual machines that are preconfigured to run containerized applications.</span></span> <span data-ttu-id="d19f5-136">Ele usa uma configuração otimizada de ferramentas populares de agendamento e a coordenação de código-fonte aberto.</span><span class="sxs-lookup"><span data-stu-id="d19f5-136">It uses an optimized configuration of popular open-source scheduling and orchestration tools.</span></span> <span data-ttu-id="d19f5-137">Isso permite que você use suas habilidades existentes ou exploram um corpo grande e crescente de experiência da comunidade, para implantar e gerenciar aplicativos de contêiner no Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="d19f5-137">This enables you to use your existing skills, or draw upon a large and growing body of community expertise, to deploy and manage container-based applications on Microsoft Azure.</span></span>

<span data-ttu-id="d19f5-138">Serviço de contêiner do Azure simplifica a criar, configurar e gerenciar um cluster de máquinas virtuais que são pré-configurados para executar aplicativos em contêineres.</span><span class="sxs-lookup"><span data-stu-id="d19f5-138">Azure Container Service makes it simpler for you to create, configure, and manage a cluster of virtual machines that are preconfigured to run containerized applications.</span></span> <span data-ttu-id="d19f5-139">Ele usa uma configuração otimizada de ferramentas populares de agendamento e a coordenação de código-fonte aberto.</span><span class="sxs-lookup"><span data-stu-id="d19f5-139">It uses an optimized configuration of popular open-source scheduling and orchestration tools.</span></span> <span data-ttu-id="d19f5-140">Isso permite que você use suas habilidades existentes ou exploram um corpo grande e crescente de experiência da comunidade, para implantar e gerenciar aplicativos de contêiner no Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="d19f5-140">This enables you to use your existing skills, or draw upon a large and growing body of community expertise, to deploy and manage container-based applications on Microsoft Azure.</span></span>

<span data-ttu-id="d19f5-141">Um objetivo do serviço de contêiner do Azure é fornecer um ambiente de hospedagem de contêiner usando ferramentas de código-fonte aberto e tecnologias que são comuns entre os clientes da Microsoft hoje.</span><span class="sxs-lookup"><span data-stu-id="d19f5-141">One goal of Azure Container Service is to provide a container hosting environment using open-source tools and technologies that are popular among Microsoft's customers today.</span></span> <span data-ttu-id="d19f5-142">Para esse fim, o serviço de contêiner do Azure expõe os pontos de extremidade de API padrão para o orchestrator escolhido (controlador de domínio/OS, Docker Swarm ou Kubernetes).</span><span class="sxs-lookup"><span data-stu-id="d19f5-142">To this end, Azure Container Service exposes the standard API endpoints for your chosen orchestrator (DC/OS, Docker Swarm, or Kubernetes).</span></span> <span data-ttu-id="d19f5-143">Ao usar esses pontos de extremidade, você pode utilizar qualquer software que é capaz de se comunicando com esses pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d19f5-143">By using these endpoints, you can leverage any software that is capable of talking to those endpoints.</span></span> <span data-ttu-id="d19f5-144">Por exemplo, no caso do ponto de extremidade Docker Swarm, você pode optar por usar a interface de linha de comando do Docker (CLI).</span><span class="sxs-lookup"><span data-stu-id="d19f5-144">For example, in the case of the Docker Swarm endpoint, you might choose to use the Docker command-line interface (CLI).</span></span> <span data-ttu-id="d19f5-145">Para o SO/controlador de domínio, você pode escolher DCOS CLI.</span><span class="sxs-lookup"><span data-stu-id="d19f5-145">For DC/OS, you might choose the DCOS CLI.</span></span> <span data-ttu-id="d19f5-146">Para Kubernetes, você pode escolher kubectl.</span><span class="sxs-lookup"><span data-stu-id="d19f5-146">For Kubernetes, you might choose kubectl.</span></span> <span data-ttu-id="d19f5-147">Figura 11-1 mostra como você usaria esses pontos de extremidade para gerenciar os clusters do contêiner.</span><span class="sxs-lookup"><span data-stu-id="d19f5-147">Figure 11-1 shows how you would use these endpoints to manage your container clusters.</span></span>

![](./media/image11-1.png)

<span data-ttu-id="d19f5-148">**Figura 11-1.**</span><span class="sxs-lookup"><span data-stu-id="d19f5-148">**Figure 11-1.**</span></span> <span data-ttu-id="d19f5-149">Gerenciamento do Azure do serviço de contêiner com Docker, Kubernetes ou DC/OS pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d19f5-149">Azure Container Service management with Docker, Kubernetes, or DC/OS endpoints.</span></span>

### <a name="azure-service-fabric"></a><span data-ttu-id="d19f5-150">Malha do serviço do Azure</span><span class="sxs-lookup"><span data-stu-id="d19f5-150">Azure Service Fabric</span></span>

<span data-ttu-id="d19f5-151">Service Fabric é uma boa opção se você estiver criando um novo aplicativo ou reescrever em um aplicativo existente para usar uma arquitetura de microsserviço.</span><span class="sxs-lookup"><span data-stu-id="d19f5-151">Service Fabric is a good choice if you're creating a new app or re-writing an existing app to use a microservice architecture.</span></span> <span data-ttu-id="d19f5-152">Aplicativos, que são executados em um pool compartilhado de computadores, podem começar pequenos e crescer em grande escala com centenas ou milhares de computadores, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="d19f5-152">Apps, which run on a shared pool of machines, can start small and grow to massive scale with hundreds or thousands of machines as needed.</span></span> <span data-ttu-id="d19f5-153">Serviços com monitoração de estado mais fácil de maneira consistente e confiável armazenar o estado do aplicativo e do Service Fabric gerencia automaticamente o particionamento de serviço, dimensionamento e disponibilidade para você.</span><span class="sxs-lookup"><span data-stu-id="d19f5-153">Stateful services make it easy to consistently and reliably store app state, and Service Fabric automatically manages service partitioning, scaling, and availability for you.</span></span> <span data-ttu-id="d19f5-154">Serviço de malha também oferece suporte a WebAPI com Interface Web aberta para .NET (OWIN) e o ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d19f5-154">Service Fabric also supports WebAPI with Open Web Interface for .NET (OWIN) and ASP.NET Core.</span></span> <span data-ttu-id="d19f5-155">Em comparação com o serviço de aplicativo, Service Fabric que também esteja fornece mais controle sobre ou acesso direto à infraestrutura subjacente.</span><span class="sxs-lookup"><span data-stu-id="d19f5-155">Compared to App Service, Service Fabric also provides more control over, or direct access to, the underlying infrastructure.</span></span> <span data-ttu-id="d19f5-156">Você pode remoto em servidores ou configurar tarefas de inicialização do servidor.</span><span class="sxs-lookup"><span data-stu-id="d19f5-156">You can remote into your servers or configure server startup tasks.</span></span>

### <a name="azure-virtual-machines"></a><span data-ttu-id="d19f5-157">Máquinas Virtuais do Azure</span><span class="sxs-lookup"><span data-stu-id="d19f5-157">Azure Virtual Machines</span></span>

<span data-ttu-id="d19f5-158">Se você tiver um aplicativo existente que exige modificações significativas para ser executado no serviço de aplicativo ou serviço de malha, você pode escolher as máquinas virtuais para simplificar a migração para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="d19f5-158">If you have an existing application that would require substantial modifications to run in App Service or Service Fabric, you could choose Virtual Machines in order to simplify migrating to the cloud.</span></span> <span data-ttu-id="d19f5-159">No entanto, corretamente configurar, proteger e VMs mantendo requer muito mais tempo e conhecimento de TI em comparação com o serviço de aplicativo do Azure e do Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="d19f5-159">However, correctly configuring, securing, and maintaining VMs requires much more time and IT expertise compared to Azure App Service and Service Fabric.</span></span> <span data-ttu-id="d19f5-160">Se você estiver pensando em máquinas virtuais do Azure, certifique-se de que levar em conta o esforço de manutenção contínua necessário para o patch, atualizar e gerenciar seu ambiente de VM.</span><span class="sxs-lookup"><span data-stu-id="d19f5-160">If you are considering Azure Virtual Machines, make sure you take into account the ongoing maintenance effort required to patch, update, and manage your VM environment.</span></span> <span data-ttu-id="d19f5-161">Máquinas virtuais do Azure é a infraestrutura-como-um-serviço (IaaS), enquanto o serviço de aplicativo e serviço de malha são plataforma-como-um-serviço (Paas).</span><span class="sxs-lookup"><span data-stu-id="d19f5-161">Azure Virtual Machines is Infrastructure-as-a-Service (IaaS), while App Service and Service Fabric are Platform-as-a-Service (Paas).</span></span>

#### <a name="feature-comparison"></a><span data-ttu-id="d19f5-162">Comparação de recursos</span><span class="sxs-lookup"><span data-stu-id="d19f5-162">Feature Comparison</span></span>

| <span data-ttu-id="d19f5-163">Serviço de aplicativo de recurso</span><span class="sxs-lookup"><span data-stu-id="d19f5-163">Feature App Service</span></span> | <span data-ttu-id="d19f5-164">Malha do serviço</span><span class="sxs-lookup"><span data-stu-id="d19f5-164">Service Fabric</span></span> | <span data-ttu-id="d19f5-165">Máquina virtual</span><span class="sxs-lookup"><span data-stu-id="d19f5-165">Virtual Machine</span></span> |
|---------|----------|----------|
| <span data-ttu-id="d19f5-166">Implantação quase instantânea</span><span class="sxs-lookup"><span data-stu-id="d19f5-166">Near-Instant Deployment</span></span> | <span data-ttu-id="d19f5-167">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-167">X</span></span> | <span data-ttu-id="d19f5-168">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-168">X</span></span> | |
| <span data-ttu-id="d19f5-169">Expansão vertical para máquinas maiores sem reimplantação</span><span class="sxs-lookup"><span data-stu-id="d19f5-169">Scale up to larger machines without redeploy</span></span> | <span data-ttu-id="d19f5-170">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-170">X</span></span> | <span data-ttu-id="d19f5-171">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-171">X</span></span> | |
| <span data-ttu-id="d19f5-172">Instâncias compartilham conteúdo e configuração; não é necessário reimplantar ou reconfigure ao dimensionar</span><span class="sxs-lookup"><span data-stu-id="d19f5-172">Instances share content and configuration; no need to redeploy or reconfigure when scaling</span></span> | <span data-ttu-id="d19f5-173">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-173">X</span></span> | <span data-ttu-id="d19f5-174">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-174">X</span></span> | |
| <span data-ttu-id="d19f5-175">Vários ambientes de implantação (produção, preparo)</span><span class="sxs-lookup"><span data-stu-id="d19f5-175">Multiple deployment environments (production, staging)</span></span> | <span data-ttu-id="d19f5-176">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-176">X</span></span> | <span data-ttu-id="d19f5-177">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-177">X</span></span> | |
| <span data-ttu-id="d19f5-178">Gerenciamento automático de atualização do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="d19f5-178">Automatic OS update management</span></span> | <span data-ttu-id="d19f5-179">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-179">X</span></span> | | |
| <span data-ttu-id="d19f5-180">Perfeita para alternar entre as plataformas de 32/64 bits</span><span class="sxs-lookup"><span data-stu-id="d19f5-180">Seamless switching between 32/64 bit platforms</span></span> | <span data-ttu-id="d19f5-181">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-181">X</span></span> | | |
| <span data-ttu-id="d19f5-182">Código de implantação com Git, FTP</span><span class="sxs-lookup"><span data-stu-id="d19f5-182">Deploy code with Git, FTP</span></span> | <span data-ttu-id="d19f5-183">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-183">X</span></span> | | <span data-ttu-id="d19f5-184">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-184">X</span></span> |
| <span data-ttu-id="d19f5-185">Código de implantação com WebDeploy</span><span class="sxs-lookup"><span data-stu-id="d19f5-185">Deploy code with WebDeploy</span></span> | <span data-ttu-id="d19f5-186">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-186">X</span></span> | | <span data-ttu-id="d19f5-187">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-187">X</span></span> |
| <span data-ttu-id="d19f5-188">Implantar o código com o TFS</span><span class="sxs-lookup"><span data-stu-id="d19f5-188">Deploy code with TFS</span></span> | <span data-ttu-id="d19f5-189">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-189">X</span></span> | <span data-ttu-id="d19f5-190">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-190">X</span></span> | <span data-ttu-id="d19f5-191">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-191">X</span></span> |
| <span data-ttu-id="d19f5-192">Host da web ou camada de serviço da web da arquitetura de várias camada</span><span class="sxs-lookup"><span data-stu-id="d19f5-192">Host web or web service tier of multi-tier architecture</span></span> | <span data-ttu-id="d19f5-193">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-193">X</span></span> | <span data-ttu-id="d19f5-194">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-194">X</span></span> | <span data-ttu-id="d19f5-195">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-195">X</span></span> |
| <span data-ttu-id="d19f5-196">Acessar os serviços do Azure, como o barramento de serviço, armazenamento, banco de dados SQL</span><span class="sxs-lookup"><span data-stu-id="d19f5-196">Access Azure services like Service Bus, Storage, SQL Database</span></span> | <span data-ttu-id="d19f5-197">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-197">X</span></span> | <span data-ttu-id="d19f5-198">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-198">X</span></span> | <span data-ttu-id="d19f5-199">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-199">X</span></span> |
| <span data-ttu-id="d19f5-200">Instalar qualquer MSI personalizado</span><span class="sxs-lookup"><span data-stu-id="d19f5-200">Install any custom MSI</span></span> | | <span data-ttu-id="d19f5-201">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-201">X</span></span> | <span data-ttu-id="d19f5-202">X</span><span class="sxs-lookup"><span data-stu-id="d19f5-202">X</span></span> |

## <a name="logical-processes"></a><span data-ttu-id="d19f5-203">Processos lógicos</span><span class="sxs-lookup"><span data-stu-id="d19f5-203">Logical Processes</span></span>

<span data-ttu-id="d19f5-204">Processos individuais de lógicos que podem ser separados do restante do aplicativo podem ser implantados independentemente para funções do Azure de modo "sem servidor".</span><span class="sxs-lookup"><span data-stu-id="d19f5-204">Individual logical processes that can be decoupled from the rest of the application may be deployed independently to Azure Functions in a "serverless" manner.</span></span> <span data-ttu-id="d19f5-205">As funções do Azure permite que você simplesmente escrever o código necessário para um problema específico, sem se preocupar com o aplicativo ou a infraestrutura para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="d19f5-205">Azure Functions lets you just write the code you need for a given problem, without worrying about the application or infrastructure to run it.</span></span> <span data-ttu-id="d19f5-206">Você pode escolher entre uma variedade de linguagens de programação, incluindo C\#, F\#, Node.js, Python e PHP, permitindo que você escolha a linguagem mais produtiva para a tarefa em questão.</span><span class="sxs-lookup"><span data-stu-id="d19f5-206">You can choose from a variety of programming languages, including C\#, F\#, Node.js, Python, and PHP, allowing you to pick the most productive language for the task at hand.</span></span> <span data-ttu-id="d19f5-207">Como a maioria das soluções com base em nuvem, você paga apenas pelo período de tempo que seu uso e você pode confiar em funções do Azure para expandir conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="d19f5-207">Like most cloud-based solutions, you pay only for the amount of time your use, and you can trust Azure Functions to scale up as needed.</span></span>

## <a name="data"></a><span data-ttu-id="d19f5-208">Dados</span><span class="sxs-lookup"><span data-stu-id="d19f5-208">Data</span></span>

<span data-ttu-id="d19f5-209">O Azure oferece uma ampla variedade de opções de armazenamento de dados, para que seu aplicativo pode usar o provedor de dados apropriado para os dados em questão.</span><span class="sxs-lookup"><span data-stu-id="d19f5-209">Azure offers a wide variety of data storage options, so that your application can use the appropriate data provider for the data in question.</span></span>

<span data-ttu-id="d19f5-210">Para dados transacionais e relacionais, bancos de dados do SQL Azure são a melhor opção.</span><span class="sxs-lookup"><span data-stu-id="d19f5-210">For transactional, relational data, Azure SQL Databases are the best option.</span></span> <span data-ttu-id="d19f5-211">Para ler mais dados de alto desempenho, um cache Redis com o apoio de um banco de dados do SQL Azure é uma boa solução.</span><span class="sxs-lookup"><span data-stu-id="d19f5-211">For high performance read-mostly data, a Redis cache backed by an Azure SQL Database is a good solution.</span></span>

<span data-ttu-id="d19f5-212">Dados JSON não estruturados podem ser armazenados em uma variedade de maneiras, colunas de banco de dados SQL para Blobs ou tabelas no armazenamento do Azure, de documentos.</span><span class="sxs-lookup"><span data-stu-id="d19f5-212">Unstructured JSON data can be stored in a variety of ways, from SQL Database columns to Blobs or Tables in Azure Storage, to DocumentDB.</span></span> <span data-ttu-id="d19f5-213">Desses, DocumentDB oferece o melhor consultar a funcionalidade e é a opção recomendada para um grande número de documentos com base em JSON que devem dar suporte à consulta.</span><span class="sxs-lookup"><span data-stu-id="d19f5-213">Of these, DocumentDB offers the best querying functionality, and is the recommended option for large numbers of JSON-based documents that must support querying.</span></span>

<span data-ttu-id="d19f5-214">Dados transitório ou evento-baseado em comandos usados para orquestrar o comportamento do aplicativo podem usar o barramento de serviço do Azure ou filas do armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="d19f5-214">Transient command- or event-based data used to orchestrate application behavior can use Azure Service Bus or Azure Storage Queues.</span></span> <span data-ttu-id="d19f5-215">Barramento de armazenamento do Azure oferece mais flexibilidade e é o serviço recomendado para mensagens não trivial dentro e entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d19f5-215">Azure Storage Bus offers more flexibility and is the recommended service for non-trivial messaging within and between applications.</span></span>

## <a name="architecture-recommendations"></a><span data-ttu-id="d19f5-216">Recomendações de arquitetura</span><span class="sxs-lookup"><span data-stu-id="d19f5-216">Architecture Recommendations</span></span>

<span data-ttu-id="d19f5-217">Requisitos do seu aplicativo devem determinar sua arquitetura.</span><span class="sxs-lookup"><span data-stu-id="d19f5-217">Your application's requirements should dictate its architecture.</span></span> <span data-ttu-id="d19f5-218">Há muitos serviços do Azure diferentes disponíveis, escolhendo que certo é uma decisão importante.</span><span class="sxs-lookup"><span data-stu-id="d19f5-218">There are many different Azure services available, choosing the right one is an important decision.</span></span> <span data-ttu-id="d19f5-219">A Microsoft oferece uma galeria de arquiteturas de referência para ajudar a identificar típicas arquiteturas otimizadas para cenários comuns.</span><span class="sxs-lookup"><span data-stu-id="d19f5-219">Microsoft offers a gallery of reference architectures to help identify typical architectures optimized for common scenarios.</span></span> <span data-ttu-id="d19f5-220">Você pode associar uma arquitetura de referência que mapas estreitamente às necessidades do seu aplicativo ou em menos oferece um ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="d19f5-220">You may bind a reference architecture that maps closely to your application's requirements, or at least offers a starting point.</span></span>

<span data-ttu-id="d19f5-221">Figura 11-2 mostra uma arquitetura de referência de exemplo.</span><span class="sxs-lookup"><span data-stu-id="d19f5-221">Figure 11-2 shows an example reference architecture.</span></span> <span data-ttu-id="d19f5-222">Este diagrama descreve uma abordagem de arquitetura recomendada para um site de sistema de gerenciamento de conteúdo Sitecore otimizado para marketing.</span><span class="sxs-lookup"><span data-stu-id="d19f5-222">This diagram describes a recommended architecture approach for a Sitecore content management system website optimized for marketing.</span></span>

![](./media/image11-2.png)

<span data-ttu-id="d19f5-223">**Figura 11-2.**</span><span class="sxs-lookup"><span data-stu-id="d19f5-223">**Figure 11-2.**</span></span> <span data-ttu-id="d19f5-224">Sitecore marketing arquitetura de referência do site.</span><span class="sxs-lookup"><span data-stu-id="d19f5-224">Sitecore marketing website reference architecture.</span></span>

<span data-ttu-id="d19f5-225">**Referências – recomendações de hospedagem do Azure**</span><span class="sxs-lookup"><span data-stu-id="d19f5-225">**References – Azure Hosting Recommendations**</span></span>

-   <span data-ttu-id="d19f5-226">Architectures\ de solução do Azure</span><span class="sxs-lookup"><span data-stu-id="d19f5-226">Azure Solution Architectures\\</span></span>
    <span data-ttu-id="d19f5-227"><https://Azure.microsoft.com/Solutions/Architecture/></span><span class="sxs-lookup"><span data-stu-id="d19f5-227"><https://azure.microsoft.com/solutions/architecture/></span></span>

-   <span data-ttu-id="d19f5-228">Guide\ de desenvolvedores do Azure</span><span class="sxs-lookup"><span data-stu-id="d19f5-228">Azure Developer Guide\\</span></span>
    <span data-ttu-id="d19f5-229"><https://Azure.microsoft.com/Campaigns/Developer-Guide/></span><span class="sxs-lookup"><span data-stu-id="d19f5-229"><https://azure.microsoft.com/campaigns/developer-guide/></span></span>

-   <span data-ttu-id="d19f5-230">O que é o serviço de aplicativo do Azure? \\</span><span class="sxs-lookup"><span data-stu-id="d19f5-230">What is Azure App Service?\\</span></span>
    <span data-ttu-id="d19f5-231"><https://docs.microsoft.com/Azure/App-Service/App-Service-Value-prop-What-is></span><span class="sxs-lookup"><span data-stu-id="d19f5-231"><https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is></span></span>

-   <span data-ttu-id="d19f5-232">Serviço de aplicativo do Azure, máquinas virtuais, serviço de malha e Comparison\ de serviços de nuvem</span><span class="sxs-lookup"><span data-stu-id="d19f5-232">Azure App Service, Virtual Machines, Service Fabric and Cloud Services Comparison\\</span></span>
    <span data-ttu-id="d19f5-233"><https://docs.microsoft.com/Azure/App-Service-Web/Choose-Web-site-Cloud-Service-VM></span><span class="sxs-lookup"><span data-stu-id="d19f5-233"><https://docs.microsoft.com/azure/app-service-web/choose-web-site-cloud-service-vm></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="d19f5-234">[Anterior] (desenvolvimento-processo-para-azure.md)</span><span class="sxs-lookup"><span data-stu-id="d19f5-234">[Previous] (development-process-for-azure.md)</span></span>