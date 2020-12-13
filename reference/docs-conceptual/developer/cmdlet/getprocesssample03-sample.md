---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple GetProcessSample03
description: Exemple GetProcessSample03
ms.openlocfilehash: 7827247238f3dad2018b55e396b73d1fa434eb97
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660725"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="6958f-103">Exemple GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="6958f-103">GetProcessSample03 Sample</span></span>

<span data-ttu-id="6958f-104">Cet exemple montre comment implémenter une applet de commande qui récupère les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6958f-104">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="6958f-105">Il fournit un `Name` paramètre qui peut accepter un objet du pipeline ou une valeur d’une propriété d’un objet dont le nom de la propriété est le même que le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="6958f-105">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="6958f-106">Cette applet de commande est une version simplifiée de l’applet de commande `Get-Process` fournie par Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="6958f-106">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="6958f-107">Comment générer l’exemple à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6958f-107">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="6958f-108">Une fois le kit de développement logiciel (SDK) 2,0 Windows PowerShell installé, accédez au dossier GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="6958f-108">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="6958f-109">L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="6958f-109">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="6958f-110">Double-cliquez sur l’icône du fichier solution (. sln).</span><span class="sxs-lookup"><span data-stu-id="6958f-110">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="6958f-111">L’exemple de projet s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6958f-111">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="6958f-112">Dans le menu **Générer**, sélectionnez **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="6958f-112">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="6958f-113">La bibliothèque de l’exemple sera générée dans les dossiers \bin ou \bin\debug par défaut.</span><span class="sxs-lookup"><span data-stu-id="6958f-113">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="6958f-114">Comment exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="6958f-114">How to run the sample</span></span>

1. <span data-ttu-id="6958f-115">Créez le dossier de module suivant :</span><span class="sxs-lookup"><span data-stu-id="6958f-115">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="6958f-116">Copiez l’exemple d’assembly dans le dossier du module.</span><span class="sxs-lookup"><span data-stu-id="6958f-116">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="6958f-117">Démarrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6958f-117">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="6958f-118">Exécutez la commande suivante pour charger l’assembly dans Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="6958f-118">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="6958f-119">Exécutez la commande suivante pour exécuter l’applet de commande :</span><span class="sxs-lookup"><span data-stu-id="6958f-119">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="6958f-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6958f-120">Requirements</span></span>

<span data-ttu-id="6958f-121">Cet exemple requiert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="6958f-121">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="6958f-122">Illustre le</span><span class="sxs-lookup"><span data-stu-id="6958f-122">Demonstrates</span></span>

<span data-ttu-id="6958f-123">Cet exemple illustre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="6958f-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="6958f-124">Déclaration d’une classe d’applet de commande à l’aide de l’attribut d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6958f-124">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="6958f-125">Déclaration d’un paramètre d’applet de commande à l’aide de l’attribut Parameter.</span><span class="sxs-lookup"><span data-stu-id="6958f-125">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="6958f-126">Spécification de la position du paramètre.</span><span class="sxs-lookup"><span data-stu-id="6958f-126">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="6958f-127">Spécifie que le paramètre prend l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="6958f-127">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="6958f-128">L’entrée peut être extraite à partir d’un objet ou d’une valeur d’une propriété d’un objet dont le nom de la propriété est le même que le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="6958f-128">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="6958f-129">Déclaration d’un attribut de validation pour l’entrée de paramètre.</span><span class="sxs-lookup"><span data-stu-id="6958f-129">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="6958f-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="6958f-130">Example</span></span>

<span data-ttu-id="6958f-131">Cet exemple illustre une implémentation de l’applet de commande Get-Proc qui comprend un `Name` paramètre acceptant l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="6958f-131">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
    /// </summary>
    [Parameter(
               Position = 0,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated processes to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="6958f-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6958f-132">See Also</span></span>

[<span data-ttu-id="6958f-133">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6958f-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
