---
title: Comment écrire une applet de commande simple | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365468"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="5fd0f-102">Comment écrire une applet de commande</span><span class="sxs-lookup"><span data-stu-id="5fd0f-102">How to write a cmdlet</span></span>

<span data-ttu-id="5fd0f-103">Cet article explique comment écrire une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5fd0f-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="5fd0f-104">L’applet de commande `Send-Greeting` accepte un nom d’utilisateur unique comme entrée, puis écrit un message d’accueil à cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5fd0f-104">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="5fd0f-105">Bien que l’applet de commande n’effectue pas de nombreuses tâches, cet exemple illustre les principales sections d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5fd0f-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="5fd0f-106">Étapes d’écriture d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="5fd0f-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="5fd0f-107">Pour déclarer la classe en tant qu’applet de commande, utilisez l’attribut d' **applet** de commande.</span><span class="sxs-lookup"><span data-stu-id="5fd0f-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="5fd0f-108">L’attribut d' **applet** de commande spécifie le verbe et le nom du nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5fd0f-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="5fd0f-109">Pour plus d’informations sur l’attribut d' **applet** de commande, consultez [déclaration CmdletAttribute](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5fd0f-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="5fd0f-110">Spécifiez le nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="5fd0f-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="5fd0f-111">Spécifiez que l’applet de commande dérive de l’une des classes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5fd0f-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="5fd0f-112">System. Management. Automation. applet de commande</span><span class="sxs-lookup"><span data-stu-id="5fd0f-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="5fd0f-113">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="5fd0f-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="5fd0f-114">Pour définir les paramètres de l’applet de commande, utilisez l’attribut **Parameter** .</span><span class="sxs-lookup"><span data-stu-id="5fd0f-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="5fd0f-115">Dans ce cas, un seul paramètre obligatoire est spécifié.</span><span class="sxs-lookup"><span data-stu-id="5fd0f-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="5fd0f-116">Pour plus d’informations sur l’attribut de **paramètre** , consultez [déclaration ParameterAttribute](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5fd0f-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="5fd0f-117">Substituez la méthode de traitement d’entrée qui traite l’entrée.</span><span class="sxs-lookup"><span data-stu-id="5fd0f-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="5fd0f-118">Dans ce cas, la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) est remplacée.</span><span class="sxs-lookup"><span data-stu-id="5fd0f-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="5fd0f-119">Pour écrire le message d’accueil, utilisez la méthode [System. Management. Automation. applet de commande. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="5fd0f-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="5fd0f-120">Le message d’accueil s’affiche au format suivant :</span><span class="sxs-lookup"><span data-stu-id="5fd0f-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="5fd0f-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="5fd0f-121">Example</span></span>

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="5fd0f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fd0f-122">See also</span></span>

[<span data-ttu-id="5fd0f-123">System. Management. Automation. applet de commande</span><span class="sxs-lookup"><span data-stu-id="5fd0f-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="5fd0f-124">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="5fd0f-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="5fd0f-125">System. Management. Automation. applet de commande. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="5fd0f-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="5fd0f-126">System. Management. Automation. applet de commande. WriteObject</span><span class="sxs-lookup"><span data-stu-id="5fd0f-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="5fd0f-127">Déclaration CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="5fd0f-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="5fd0f-128">Déclaration ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="5fd0f-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="5fd0f-129">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fd0f-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)