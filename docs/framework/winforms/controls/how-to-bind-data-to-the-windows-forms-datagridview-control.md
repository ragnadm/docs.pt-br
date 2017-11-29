---
title: Como associar dados ao controle DataGridView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63194d01d5de1eab9d71376e472a70613f83d1ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="e99ae-102">Como associar dados ao controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e99ae-102">How to: Bind Data to the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e99ae-103">O <xref:System.Windows.Forms.DataGridView> controle oferece suporte para o modelo de associação de dados formulários do Windows padrão, portanto ele associará a uma variedade de fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="e99ae-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to a variety of data sources.</span></span> <span data-ttu-id="e99ae-104">Na maioria das circunstâncias, no entanto, você associará a uma <xref:System.Windows.Forms.BindingSource> componente que gerenciará os detalhes de interagir com a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e99ae-104">In most circumstances, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component which will manage the details of interacting with the data source.</span></span> <span data-ttu-id="e99ae-105">O <xref:System.Windows.Forms.BindingSource> componente pode representar qualquer fonte de dados do Windows Forms e oferece excelente flexibilidade ao escolher ou modificar o local de seus dados.</span><span class="sxs-lookup"><span data-stu-id="e99ae-105">The <xref:System.Windows.Forms.BindingSource> component can represent any Windows Forms data source and gives you great flexibility when choosing or modifying the location of your data.</span></span> <span data-ttu-id="e99ae-106">Para obter mais informações sobre as fontes de dados com suporte a <xref:System.Windows.Forms.DataGridView> , consulte [visão geral do controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e99ae-106">For more information about the data sources supported by the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="e99ae-107">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e99ae-107">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="e99ae-108">Veja também [Como associar dados ao controle DataGridView dos Windows Forms usando o designer](http://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e99ae-108">Also see [How to: Bind Data to the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="e99ae-109">Procedimento</span><span class="sxs-lookup"><span data-stu-id="e99ae-109">Procedure</span></span>  
  
#### <a name="to-connect-a-datagridview-control-to-data"></a><span data-ttu-id="e99ae-110">Para conectar um controle DataGridView aos dados</span><span class="sxs-lookup"><span data-stu-id="e99ae-110">To connect a DataGridView control to data</span></span>  
  
1.  <span data-ttu-id="e99ae-111">Implementar um método para manipular os detalhes de recuperar dados de um base de dados.</span><span class="sxs-lookup"><span data-stu-id="e99ae-111">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="e99ae-112">O seguinte código exemplo implementa um `GetData` método inicializa um <xref:System.Data.SqlClient.SqlDataAdapter> componente e o utiliza para preencher um <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="e99ae-112">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="e99ae-113">O <xref:System.Data.DataTable> é então associado para o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="e99ae-113">The <xref:System.Data.DataTable> is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="e99ae-114">Certifique-se de definir a variável de `connectionString` como um valor que seja apropriada para o base de dados.</span><span class="sxs-lookup"><span data-stu-id="e99ae-114">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="e99ae-115">Você precisa ter acesso a um servidor com o banco de dados de exemplo Northwind do SQL Server instalado.</span><span class="sxs-lookup"><span data-stu-id="e99ae-115">You will need access to a server with the Northwind SQL Server sample database installed.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#20)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#20)]  
  
2.  <span data-ttu-id="e99ae-116">Em sua forma <xref:System.Windows.Forms.Form.Load> manipulador de eventos, a associação a <xref:System.Windows.Forms.DataGridView> controlar para a <xref:System.Windows.Forms.BindingSource> componente e chama o `GetData` método para recuperar os dados do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e99ae-116">In your form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#10)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="e99ae-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e99ae-117">Example</span></span>  
 <span data-ttu-id="e99ae-118">O exemplo de código completo a seguir fornece botões para recarregar os dados do banco de dados e enviar alterações para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e99ae-118">The following complete code example provides buttons for reloading data from the database and submitting changes to the database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#00)]
 [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e99ae-119">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e99ae-119">Compiling the Code</span></span>  
 <span data-ttu-id="e99ae-120">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="e99ae-120">This example requires:</span></span>  
  
-   <span data-ttu-id="e99ae-121">Referências aos assemblies System, System.Windows.Forms, System.Data e System.XML.</span><span class="sxs-lookup"><span data-stu-id="e99ae-121">References to the System, System.Windows.Forms, System.Data, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="e99ae-122">Para obter informações sobre como criar este exemplo da linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) (Compilação da linha de comando) ou [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) (Compilação da linha de comando com csc.exe).</span><span class="sxs-lookup"><span data-stu-id="e99ae-122">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e99ae-123">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="e99ae-123">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="e99ae-124">Consulte também [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) (Como compilar e executar um exemplo completo de código dos Windows Forms usando o Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="e99ae-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e99ae-125">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e99ae-125">.NET Framework Security</span></span>  
 <span data-ttu-id="e99ae-126">O armazenamento das informações confidenciais, como uma senha, dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e99ae-126">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="e99ae-127">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e99ae-127">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="e99ae-128">Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="e99ae-128">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e99ae-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e99ae-129">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="e99ae-130">Exibindo dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e99ae-130">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="e99ae-131">Protegendo informações de conexão</span><span class="sxs-lookup"><span data-stu-id="e99ae-131">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)