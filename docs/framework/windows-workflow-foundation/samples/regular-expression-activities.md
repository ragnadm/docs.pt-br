---
title: "Atividades de expressão regular"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: edeb55f25abf9e6f22ebfe1d0ea63eb07ba0f203
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-activities"></a><span data-ttu-id="47516-102">Atividades de expressão regular</span><span class="sxs-lookup"><span data-stu-id="47516-102">Regular Expression Activities</span></span>
<span data-ttu-id="47516-103">Este exemplo demonstra como criar um conjunto de atividades que expõe a funcionalidade de expressões regulares do <xref:System.Text.RegularExpressions> .</span><span class="sxs-lookup"><span data-stu-id="47516-103">This sample demonstrates how to create a set of activities that expose the regular expression functionality of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="47516-104">Essas atividades personalizados podem ser usadas em um aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="47516-104">These custom activities can be used within a workflow application.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="47516-105">expressões regulares, consulte [n: System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span><span class="sxs-lookup"><span data-stu-id="47516-105"> regular expressions, see [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span></span>  
  
 <span data-ttu-id="47516-106">A tabela a seguir detalha as atividades personalizados nesse exemplo.</span><span class="sxs-lookup"><span data-stu-id="47516-106">The following table details the custom activities in this sample.</span></span>  
  
|<span data-ttu-id="47516-107">Atividade</span><span class="sxs-lookup"><span data-stu-id="47516-107">Activity</span></span>|<span data-ttu-id="47516-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="47516-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="47516-109">IsMatch</span><span class="sxs-lookup"><span data-stu-id="47516-109">IsMatch</span></span>|<span data-ttu-id="47516-110">Especifica se a expressão regular encontrado uma correspondência na cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="47516-110">Specifies whether the regular expression found a match in the input string.</span></span>|  
|<span data-ttu-id="47516-111">Correspondências</span><span class="sxs-lookup"><span data-stu-id="47516-111">Matches</span></span>|<span data-ttu-id="47516-112">Procura uma cadeia de caracteres de entrada por todas as ocorrências de uma expressão regular e retorna todas as correspondências com êxito.</span><span class="sxs-lookup"><span data-stu-id="47516-112">Searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span>|  
|<span data-ttu-id="47516-113">Substituir</span><span class="sxs-lookup"><span data-stu-id="47516-113">Replace</span></span>|<span data-ttu-id="47516-114">Dentro de uma cadeia de caracteres especificada de entrada, substitui as cadeias de caracteres que correspondem um padrão de expressão regular com uma cadeia de caracteres especificada de substituição.</span><span class="sxs-lookup"><span data-stu-id="47516-114">Within a specified input string, replaces strings that match a regular expression pattern with a specified replacement string.</span></span>|  
  
## <a name="ismatch"></a><span data-ttu-id="47516-115">IsMatch</span><span class="sxs-lookup"><span data-stu-id="47516-115">IsMatch</span></span>  
 <span data-ttu-id="47516-116">A atividade personalizado de `IsMatch` retorna `true` se a propriedade de cadeia de caracteres de `Input` encontra uma correspondência na expressão regular especificada na propriedade de `Pattern` .</span><span class="sxs-lookup"><span data-stu-id="47516-116">The `IsMatch` custom activity returns `true` if the `Input` string property finds a match in the regular expression specified in the `Pattern` property.</span></span> <span data-ttu-id="47516-117">A atividade deriva de <xref:System.Activities.CodeActivity%601> e dentro de <xref:System.Activities.CodeActivity%601.Execute%2A> o método chama o método de <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> .</span><span class="sxs-lookup"><span data-stu-id="47516-117">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method.</span></span>  
  
 <span data-ttu-id="47516-118">A tabela a seguir descreve as propriedades e o valor de retorno para atividades personalizado de `IsMatch` .</span><span class="sxs-lookup"><span data-stu-id="47516-118">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="47516-119">Propriedade ou valor de retorno</span><span class="sxs-lookup"><span data-stu-id="47516-119">Property or Return Value</span></span>|<span data-ttu-id="47516-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="47516-120">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="47516-121">Padrão (necessário)</span><span class="sxs-lookup"><span data-stu-id="47516-121">Pattern (required)</span></span>|<span data-ttu-id="47516-122">A expressão regular com a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="47516-122">The regular expression to search with.</span></span>|  
|<span data-ttu-id="47516-123">Entrada (necessária)</span><span class="sxs-lookup"><span data-stu-id="47516-123">Input (required)</span></span>|<span data-ttu-id="47516-124">A cadeia de caracteres de entrada para procurar.</span><span class="sxs-lookup"><span data-stu-id="47516-124">The input string to search.</span></span>|  
|<span data-ttu-id="47516-125">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="47516-125">RegexOptions</span></span>|<span data-ttu-id="47516-126">Combinação de OR bit a bit de [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="47516-126">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="47516-127">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="47516-127">Return value</span></span>|<span data-ttu-id="47516-128">`true` se a entrada encontra uma correspondência no padrão fornecido; se não `false`.</span><span class="sxs-lookup"><span data-stu-id="47516-128">`true` if the input finds a match in the provided pattern; otherwise `false`.</span></span>|  
  
 <span data-ttu-id="47516-129">O exemplo de código demonstra como usar a atividade personalizado de `IsMatch` .</span><span class="sxs-lookup"><span data-stu-id="47516-129">The following code example demonstrates how to use the `IsMatch` custom activity.</span></span>  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a><span data-ttu-id="47516-130">Correspondências</span><span class="sxs-lookup"><span data-stu-id="47516-130">Matches</span></span>  
 <span data-ttu-id="47516-131">A atividade personalizado de `Matches` procura uma cadeia de caracteres de entrada por todas as ocorrências de uma expressão regular e retorna todas as correspondências com êxito.</span><span class="sxs-lookup"><span data-stu-id="47516-131">The `Matches` custom activity searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span> <span data-ttu-id="47516-132">A atividade deriva de <xref:System.Activities.CodeActivity%601> e dentro de <xref:System.Activities.CodeActivity%601.Execute%2A> o método chama o método de <xref:System.Text.RegularExpressions.Regex.Matches%2A> .</span><span class="sxs-lookup"><span data-stu-id="47516-132">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Matches%2A> method.</span></span>  
  
 <span data-ttu-id="47516-133">A tabela a seguir descreve as propriedades e o valor de retorno para atividades personalizado de `IsMatch` .</span><span class="sxs-lookup"><span data-stu-id="47516-133">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="47516-134">Propriedade ou valor de retorno</span><span class="sxs-lookup"><span data-stu-id="47516-134">Property or Return Value</span></span>|<span data-ttu-id="47516-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="47516-135">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="47516-136">Padrão (necessário)</span><span class="sxs-lookup"><span data-stu-id="47516-136">Pattern (required)</span></span>|<span data-ttu-id="47516-137">A expressão regular com a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="47516-137">The regular expression to search with.</span></span>|  
|<span data-ttu-id="47516-138">Entrada (necessária)</span><span class="sxs-lookup"><span data-stu-id="47516-138">Input (required)</span></span>|<span data-ttu-id="47516-139">A cadeia de caracteres de entrada para procurar.</span><span class="sxs-lookup"><span data-stu-id="47516-139">The input string to search.</span></span>|  
|<span data-ttu-id="47516-140">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="47516-140">RegexOptions</span></span>|<span data-ttu-id="47516-141">Combinação de OR bit a bit de [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="47516-141">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="47516-142">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="47516-142">Return Value</span></span>|<span data-ttu-id="47516-143"><xref:System.Text.RegularExpressions.MatchCollection> que contém a coleção de correspondências com êxito.</span><span class="sxs-lookup"><span data-stu-id="47516-143">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="47516-144">O exemplo de código demonstra como usar a atividade personalizado de `Matches` .</span><span class="sxs-lookup"><span data-stu-id="47516-144">The following code example demonstrates how to use the `Matches` custom activity.</span></span>  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a><span data-ttu-id="47516-145">Substituir</span><span class="sxs-lookup"><span data-stu-id="47516-145">Replace</span></span>  
 <span data-ttu-id="47516-146">A atividade personalizado de `Replace` procura uma cadeia de caracteres de entrada e substitui todas as cadeias de caracteres que correspondem a uma expressão regular especificada com uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="47516-146">The `Replace` custom activity searches an input string and replaces all strings that match a specified regular expression with a string.</span></span> <span data-ttu-id="47516-147">A atividade deriva de <xref:System.Activities.CodeActivity%601> e dentro de <xref:System.Activities.CodeActivity%601.Execute%2A> o método chama o método de <xref:System.Text.RegularExpressions.Regex.Replace%2A> .</span><span class="sxs-lookup"><span data-stu-id="47516-147">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method.</span></span>  
  
 <span data-ttu-id="47516-148">A tabela a seguir descreve as propriedades e o valor de retorno para atividades personalizado de `Replace` .</span><span class="sxs-lookup"><span data-stu-id="47516-148">The following table describes the properties and return value for the `Replace` custom activity.</span></span>  
  
|<span data-ttu-id="47516-149">Propriedade ou valor de retorno</span><span class="sxs-lookup"><span data-stu-id="47516-149">Property or Return Value</span></span>|<span data-ttu-id="47516-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="47516-150">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="47516-151">Padrão (necessário)</span><span class="sxs-lookup"><span data-stu-id="47516-151">Pattern (required)</span></span>|<span data-ttu-id="47516-152">A expressão regular com a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="47516-152">The regular expression to search with.</span></span>|  
|<span data-ttu-id="47516-153">Entrada (necessária)</span><span class="sxs-lookup"><span data-stu-id="47516-153">Input (required)</span></span>|<span data-ttu-id="47516-154">A cadeia de caracteres de entrada para procurar.</span><span class="sxs-lookup"><span data-stu-id="47516-154">The input string to search.</span></span>|  
|<span data-ttu-id="47516-155">Substituição</span><span class="sxs-lookup"><span data-stu-id="47516-155">Replacement</span></span>|<span data-ttu-id="47516-156">A cadeia de caracteres substituta.</span><span class="sxs-lookup"><span data-stu-id="47516-156">The replacement string.</span></span><br /><br /> <span data-ttu-id="47516-157">Se `Replacement` for especificado, então a propriedade de `MatchEvaluator` será ignorada.</span><span class="sxs-lookup"><span data-stu-id="47516-157">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="47516-158">`Replacement` ou propriedade de `MatchEvaluator` devem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="47516-158">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="47516-159">MatchEvaluator</span><span class="sxs-lookup"><span data-stu-id="47516-159">MatchEvaluator</span></span>|<span data-ttu-id="47516-160">Um método personalizado que examina cada correspondência e retorna a cadeia de caracteres correspondida original ou uma cadeia de caracteres de substituição.</span><span class="sxs-lookup"><span data-stu-id="47516-160">A custom method that examines each match and returns either the original matched string or a replacement string.</span></span><br /><br /> <span data-ttu-id="47516-161">Se `Replacement` for especificado, então a propriedade de `MatchEvaluator` será ignorada.</span><span class="sxs-lookup"><span data-stu-id="47516-161">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="47516-162">`Replacement` ou propriedade de `MatchEvaluator` devem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="47516-162">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="47516-163">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="47516-163">RegexOptions</span></span>|<span data-ttu-id="47516-164">Combinação de OR bit a bit de [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="47516-164">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="47516-165">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="47516-165">Return Value</span></span>|<span data-ttu-id="47516-166"><xref:System.Text.RegularExpressions.MatchCollection> que contém a coleção de correspondências com êxito.</span><span class="sxs-lookup"><span data-stu-id="47516-166">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="47516-167">O exemplo de código demonstra como usar a atividade personalizado de `Replace` .</span><span class="sxs-lookup"><span data-stu-id="47516-167">The following code example demonstrates how to use the `Replace` custom activity.</span></span>  
  
```  
// Using the replacement string.  
new Replace  
{  
    Pattern = @"\bWorld\b",  
    Input = "Hello World! This is a wonderful World",  
    Replacement = "Universe"  
};  
  
// Using a match evaluator.  
new Replace  
{  
    Pattern = new InArgument<string>(pattern),  
    Input = new InArgument<string>(input),  
    MatchEvaluator = new MatchEvaluator(CapText)                  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="47516-168">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="47516-168">To use this sample</span></span>  
  
1.  <span data-ttu-id="47516-169">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de RegexActivities.sln.</span><span class="sxs-lookup"><span data-stu-id="47516-169">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RegexActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="47516-170">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="47516-170">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="47516-171">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="47516-171">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="47516-172">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="47516-172">The samples may already be installed on your machine.</span></span> <span data-ttu-id="47516-173">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="47516-173">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="47516-174">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="47516-174">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="47516-175">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="47516-175">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`  
  
## <a name="see-also"></a><span data-ttu-id="47516-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47516-176">See Also</span></span>