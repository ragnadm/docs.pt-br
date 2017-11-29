---
title: 'Codificador personalizado de mensagem: codificador personalizado de texto'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: def37608321923017e17a0296a4351cb951d6726
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="c2856-102">Codificador personalizado de mensagem: codificador personalizado de texto</span><span class="sxs-lookup"><span data-stu-id="c2856-102">Custom Message Encoder: Custom Text Encoder</span></span>
<span data-ttu-id="c2856-103">Este exemplo demonstra como implementar um codificador de mensagem de texto personalizado usando [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c2856-103">This sample demonstrates how to implement a custom text message encoder using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c2856-104">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c2856-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c2856-105">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c2856-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c2856-106">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="c2856-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c2856-107">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c2856-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 <span data-ttu-id="c2856-108">O <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte a apenas as codificações UTF-8, UTF-16 e Unicode de Endean grande.</span><span class="sxs-lookup"><span data-stu-id="c2856-108">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports only the UTF-8, UTF-16 and Big Endean Unicode encodings.</span></span> <span data-ttu-id="c2856-109">O codificador de mensagem de texto personalizado neste exemplo oferece suporte a todos os suporte de plataforma de codificação de caracteres que podem ser necessários para fins de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="c2856-109">The custom text message encoder in this sample supports all platform-supported character encoding that may be required for interoperability.</span></span> <span data-ttu-id="c2856-110">O exemplo consiste em um programa de console de cliente (.exe), uma biblioteca de serviço (. dll) hospedada pelo Internet Information Services (IIS) e uma biblioteca de codificador de mensagem de texto (. dll).</span><span class="sxs-lookup"><span data-stu-id="c2856-110">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS) and a text message encoder library (.dll).</span></span> <span data-ttu-id="c2856-111">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="c2856-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="c2856-112">O contrato é definido pelo `ICalculator` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir).</span><span class="sxs-lookup"><span data-stu-id="c2856-112">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="c2856-113">O cliente faz solicitações síncronas para uma operação matemática determinado e as respostas do serviço com o resultado.</span><span class="sxs-lookup"><span data-stu-id="c2856-113">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="c2856-114">Cliente e o serviço usa o `CustomTextMessageEncoder` em vez do padrão <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="c2856-114">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>  
  
 <span data-ttu-id="c2856-115">A implementação de codificador personalizado consiste em uma fábrica de codificador de mensagem, um codificador de mensagem, uma elemento de associação e um manipulador de configuração de codificação de mensagem e demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c2856-115">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>  
  
-   <span data-ttu-id="c2856-116">Criando um codificador personalizado e a fábrica do codificador.</span><span class="sxs-lookup"><span data-stu-id="c2856-116">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="c2856-117">Criar um elemento de associação para um codificador personalizado.</span><span class="sxs-lookup"><span data-stu-id="c2856-117">Creating a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="c2856-118">Usando a configuração de associação personalizada para a integração de elementos de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c2856-118">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="c2856-119">Desenvolvendo um manipulador de configuração personalizada para permitir a configuração de arquivo de um elemento de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c2856-119">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c2856-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="c2856-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c2856-121">Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="c2856-121">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="c2856-122">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2856-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="c2856-123">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2856-123">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="c2856-124">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2856-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="c2856-125">Fábrica de codificador de mensagem e o codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="c2856-125">Message Encoder Factory and the Message Encoder</span></span>  
 <span data-ttu-id="c2856-126">Quando o <xref:System.ServiceModel.ServiceHost> ou o cliente de canal é aberto, o componente de tempo de design `CustomTextMessageBindingElement` cria o `CustomTextMessageEncoderFactory`.</span><span class="sxs-lookup"><span data-stu-id="c2856-126">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="c2856-127">A fábrica cria o `CustomTextMessageEncoder`.</span><span class="sxs-lookup"><span data-stu-id="c2856-127">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="c2856-128">O codificador de mensagem opera no modo de transmissão e o modo de buffer.</span><span class="sxs-lookup"><span data-stu-id="c2856-128">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="c2856-129">Ele usa o <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter> para ler e gravar as mensagens respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c2856-129">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="c2856-130">Em vez do otimizado leitores XML e autores de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que dão suporte apenas UTF-8, UTF-16 e Unicode Big-Endean esses leitores e gravadores oferecem suporte a codificação de todas as plataformas com suporte.</span><span class="sxs-lookup"><span data-stu-id="c2856-130">As opposed to the optimized XML readers and writers of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that support only UTF-8, UTF-16 and Big-Endean Unicode these readers and writers support all platform supported encoding.</span></span>  
  
 <span data-ttu-id="c2856-131">O exemplo de código a seguir mostra o CustomTextMessageEncoder.</span><span class="sxs-lookup"><span data-stu-id="c2856-131">The following code example shows the CustomTextMessageEncoder.</span></span>  
  
```csharp  
public class CustomTextMessageEncoder : MessageEncoder  
{  
    private CustomTextMessageEncoderFactory factory;  
    private XmlWriterSettings writerSettings;  
    private string contentType;  
  
    public CustomTextMessageEncoder(CustomTextMessageEncoderFactory factory)  
    {  
        this.factory = factory;  
  
        this.writerSettings = new XmlWriterSettings();  
        this.writerSettings.Encoding = Encoding.GetEncoding(factory.CharSet);  
        this.contentType = string.Format("{0}; charset={1}",   
            this.factory.MediaType, this.writerSettings.Encoding.HeaderName);  
    }  
  
    public override string ContentType  
    {  
        get  
        {  
            return this.contentType;  
        }  
    }  
  
    public override string MediaType  
    {  
        get   
        {  
            return factory.MediaType;  
        }  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get   
        {  
            return this.factory.MessageVersion;  
        }  
    }  
  
    public override Message ReadMessage(ArraySegment<byte> buffer, BufferManager bufferManager, string contentType)  
    {     
        byte[] msgContents = new byte[buffer.Count];  
        Array.Copy(buffer.Array, buffer.Offset, msgContents, 0, msgContents.Length);  
        bufferManager.ReturnBuffer(buffer.Array);  
  
        MemoryStream stream = new MemoryStream(msgContents);  
        return ReadMessage(stream, int.MaxValue);  
    }  
  
    public override Message ReadMessage(Stream stream, int maxSizeOfHeaders, string contentType)  
    {  
        XmlReader reader = XmlReader.Create(stream);  
        return Message.CreateMessage(reader, maxSizeOfHeaders, this.MessageVersion);  
    }  
  
    public override ArraySegment<byte> WriteMessage(Message message, int maxMessageSize, BufferManager bufferManager, int messageOffset)  
    {  
        MemoryStream stream = new MemoryStream();  
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);  
        message.WriteMessage(writer);  
        writer.Close();  
  
        byte[] messageBytes = stream.GetBuffer();  
        int messageLength = (int)stream.Position;  
        stream.Close();  
  
        int totalLength = messageLength + messageOffset;  
        byte[] totalBytes = bufferManager.TakeBuffer(totalLength);  
        Array.Copy(messageBytes, 0, totalBytes, messageOffset, messageLength);  
  
        ArraySegment<byte> byteArray = new ArraySegment<byte>(totalBytes, messageOffset, messageLength);  
        return byteArray;  
    }  
  
    public override void WriteMessage(Message message, Stream stream)  
    {  
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);  
        message.WriteMessage(writer);  
        writer.Close();  
    }  
}  
```  
  
 <span data-ttu-id="c2856-132">O exemplo de código a seguir mostra como criar a fábrica do codificador de mensagem.</span><span class="sxs-lookup"><span data-stu-id="c2856-132">The following code example shows how to build the message encoder factory.</span></span>  
  
```csharp  
public class CustomTextMessageEncoderFactory : MessageEncoderFactory  
{  
    private MessageEncoder encoder;  
    private MessageVersion version;  
    private string mediaType;  
    private string charSet;  
  
    internal CustomTextMessageEncoderFactory(string mediaType, string charSet,  
        MessageVersion version)  
    {  
        this.version = version;  
        this.mediaType = mediaType;  
        this.charSet = charSet;  
        this.encoder = new CustomTextMessageEncoder(this);  
    }  
  
    public override MessageEncoder Encoder  
    {  
        get   
        {   
            return this.encoder;  
        }  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get   
        {   
            return this.version;  
        }  
    }  
  
    internal string MediaType  
    {  
        get  
        {  
            return this.mediaType;  
        }  
    }  
  
    internal string CharSet  
    {  
        get  
        {  
            return this.charSet;  
        }  
    }  
}  
```  
  
## <a name="message-encoding-binding-element"></a><span data-ttu-id="c2856-133">Elemento de associação de codificação de mensagem</span><span class="sxs-lookup"><span data-stu-id="c2856-133">Message Encoding Binding Element</span></span>  
 <span data-ttu-id="c2856-134">Os elementos de associação permitem a configuração do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pilha de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c2856-134">The binding elements allow the configuration of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] run-time stack.</span></span> <span data-ttu-id="c2856-135">Para usar o codificador de mensagem personalizada em um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, um elemento de associação é necessário que cria a fábrica de codificador de mensagem com as configurações apropriadas no nível apropriado na pilha de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c2856-135">To use the custom message encoder in a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>  
  
 <span data-ttu-id="c2856-136">O `CustomTextMessageBindingElement` deriva o <xref:System.ServiceModel.Channels.BindingElement> classe base e herde o <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> classe.</span><span class="sxs-lookup"><span data-stu-id="c2856-136">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="c2856-137">Isso permite que outros [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componentes para reconhecer esse elemento de associação como uma elemento de associação de codificação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="c2856-137">This allows other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="c2856-138">A implementação de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> retorna uma instância da fábrica de codificador de mensagem correspondente com as configurações apropriadas.</span><span class="sxs-lookup"><span data-stu-id="c2856-138">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>  
  
 <span data-ttu-id="c2856-139">O `CustomTextMessageBindingElement` expõe as configurações de `MessageVersion`, `ContentType`, e `Encoding` por meio de propriedades.</span><span class="sxs-lookup"><span data-stu-id="c2856-139">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="c2856-140">O codificador dá suporte a versões Soap11Addressing e Soap12Addressing1.</span><span class="sxs-lookup"><span data-stu-id="c2856-140">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="c2856-141">O padrão é Soap11Addressing1.</span><span class="sxs-lookup"><span data-stu-id="c2856-141">The default is Soap11Addressing1.</span></span> <span data-ttu-id="c2856-142">O valor padrão de `ContentType` é "text/xml".</span><span class="sxs-lookup"><span data-stu-id="c2856-142">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="c2856-143">O `Encoding` propriedade permite que você defina o valor de codificação de caractere desejado.</span><span class="sxs-lookup"><span data-stu-id="c2856-143">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="c2856-144">O exemplo de cliente e o serviço usa a codificação de caracteres de ISO 8859-1 (Latim1), que não é compatível com o <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c2856-144">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="c2856-145">O código a seguir mostra como criar programaticamente a associação usando o codificador de mensagem de texto personalizado.</span><span class="sxs-lookup"><span data-stu-id="c2856-145">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="c2856-146">Adicionando suporte a metadados para a elemento de associação de codificação de mensagem</span><span class="sxs-lookup"><span data-stu-id="c2856-146">Adding Metadata Support to the Message Encoding Binding Element</span></span>  
 <span data-ttu-id="c2856-147">Qualquer tipo que deriva de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> é responsável por atualizar a versão da associação SOAP no documento WSDL gerado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="c2856-147">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="c2856-148">Isso é feito através da implementação de `ExportEndpoint` método o <xref:System.ServiceModel.Description.IWsdlExportExtension> interface e, em seguida, modificando o WSDL gerado.</span><span class="sxs-lookup"><span data-stu-id="c2856-148">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="c2856-149">Neste exemplo, o `CustomTextMessageBindingElement` usa a lógica de exportação WSDL do `TextMessageEncodingBinidngElement`.</span><span class="sxs-lookup"><span data-stu-id="c2856-149">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBinidngElement`.</span></span>  
  
 <span data-ttu-id="c2856-150">Para este exemplo, a configuração do cliente é configurado de mão.</span><span class="sxs-lookup"><span data-stu-id="c2856-150">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="c2856-151">Você não pode usar o Svcutil.exe para gerar a configuração do cliente porque o `CustomTextMessageBindingElement` não exporta uma declaração de política para descrever seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="c2856-151">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="c2856-152">Em geral, você deve implementar o <xref:System.ServiceModel.Description.IPolicyExportExtension> interface em um elemento de associação personalizada para exportar uma declaração de política personalizada que descreve o comportamento ou um recurso implementado para o elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="c2856-152">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="c2856-153">Para obter um exemplo de como exportar uma declaração de política para um elemento de associação personalizada, consulte o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="c2856-153">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="c2856-154">Manipulador de configuração de associação de codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="c2856-154">Message Encoding Binding Configuration Handler</span></span>  
 <span data-ttu-id="c2856-155">A seção anterior mostra como usar o codificador de mensagem de texto personalizado programaticamente.</span><span class="sxs-lookup"><span data-stu-id="c2856-155">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="c2856-156">O `CustomTextMessageEncodingBindingSection` implementa um manipulador de configuração que permite que você especifique o uso de um codificador de mensagem de texto personalizado em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c2856-156">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="c2856-157">O `CustomTextMessageEncodingBindingSection` classe deriva de <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> classe.</span><span class="sxs-lookup"><span data-stu-id="c2856-157">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="c2856-158">O `BindingElementType` propriedade informa o sistema de configuração do tipo de elemento de associação para criar para essa seção.</span><span class="sxs-lookup"><span data-stu-id="c2856-158">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>  
  
 <span data-ttu-id="c2856-159">Todas as configurações definidas por `CustomTextMessageBindingElement` são expostos como propriedades no `CustomTextMessageEncodingBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="c2856-159">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="c2856-160">O <xref:System.Configuration.ConfigurationPropertyAttribute> ajuda a mapear os atributos do elemento de configuração para as propriedades e configuração de valores padrão se o atributo não está definido.</span><span class="sxs-lookup"><span data-stu-id="c2856-160">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="c2856-161">Depois que os valores de configuração são carregados e aplicados às propriedades do tipo, o <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> método é chamado, que converte as propriedades em uma instância concreta de um elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="c2856-161">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>  
  
 <span data-ttu-id="c2856-162">Este manipulador de configuração é mapeado para a representação seguinte no App. config ou Web. config para o serviço ou cliente.</span><span class="sxs-lookup"><span data-stu-id="c2856-162">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 <span data-ttu-id="c2856-163">O exemplo usa a codificação ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="c2856-163">The sample uses the ISO-8859-1 encoding.</span></span>  
  
 <span data-ttu-id="c2856-164">Para usar este manipulador de configuração que devem ser registrado usando o seguinte elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="c2856-164">To use this configuration handler it must be registered using the following configuration element.</span></span>  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
        <add name="customTextMessageEncoding" type="   
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,   
                  CustomTextMessageEncoder" />  
    </bindingElementExtensions>  
</extensions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2856-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2856-165">See Also</span></span>