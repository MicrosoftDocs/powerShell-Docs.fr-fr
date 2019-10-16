---
title: Exemple GetProcessSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364568"
---
# <a name="getprocesssample02-sample"></a><span data-ttu-id="b88b6-102">Exemple GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="b88b6-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="b88b6-103">Cet exemple montre comment écrire une applet de commande qui récupère les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b88b6-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="b88b6-104">Il fournit un paramètre `Name` qui peut être utilisé pour spécifier les processus à récupérer.</span><span class="sxs-lookup"><span data-stu-id="b88b6-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="b88b6-105">Cette applet de commande est une version simplifiée de l’applet de commande `Get-Process` fournie par Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="b88b6-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="b88b6-106">Comment générer l’exemple à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b88b6-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="b88b6-107">Une fois le kit de développement logiciel (SDK) 2,0 Windows PowerShell installé, accédez au dossier GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="b88b6-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="b88b6-108">L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="b88b6-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="b88b6-109">Double-cliquez sur l’icône du fichier solution (. sln).</span><span class="sxs-lookup"><span data-stu-id="b88b6-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="b88b6-110">L’exemple de projet s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b88b6-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="b88b6-111">Dans le menu **générer** , sélectionnez **générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="b88b6-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="b88b6-112">La bibliothèque de l’exemple sera générée dans les dossiers \bin ou \bin\debug par défaut.</span><span class="sxs-lookup"><span data-stu-id="b88b6-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="b88b6-113">Comment exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="b88b6-113">How to run the sample</span></span>

1. <span data-ttu-id="b88b6-114">Créez le dossier de module suivant :</span><span class="sxs-lookup"><span data-stu-id="b88b6-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="b88b6-115">Copiez l’exemple d’assembly dans le dossier du module.</span><span class="sxs-lookup"><span data-stu-id="b88b6-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="b88b6-116">Démarrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b88b6-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="b88b6-117">Exécutez la commande suivante pour charger l’assembly dans Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="b88b6-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="b88b6-118">Exécutez la commande suivante pour exécuter l’applet de commande :</span><span class="sxs-lookup"><span data-stu-id="b88b6-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="b88b6-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b88b6-119">Requirements</span></span>

<span data-ttu-id="b88b6-120">Cet exemple requiert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="b88b6-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b88b6-121">Illustré</span><span class="sxs-lookup"><span data-stu-id="b88b6-121">Demonstrates</span></span>

<span data-ttu-id="b88b6-122">Cet exemple illustre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="b88b6-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="b88b6-123">Déclaration d’une classe d’applet de commande à l’aide de l’attribut d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b88b6-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="b88b6-124">Déclaration d’un paramètre d’applet de commande à l’aide de l’attribut Parameter.</span><span class="sxs-lookup"><span data-stu-id="b88b6-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="b88b6-125">Spécification de la position du paramètre.</span><span class="sxs-lookup"><span data-stu-id="b88b6-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="b88b6-126">Déclaration d’un attribut de validation pour l’entrée de paramètre.</span><span class="sxs-lookup"><span data-stu-id="b88b6-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="b88b6-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="b88b6-127">Example</span></span>

<span data-ttu-id="b88b6-128">Cet exemple illustre une implémentation de l’applet de commande « obtenir-proc » qui comprend un paramètre `Name`.</span><span class="sxs-lookup"><span data-stu-id="b88b6-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

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
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
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
    /// associated process objects to the pipeline.
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
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="b88b6-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b88b6-129">See Also</span></span>

[<span data-ttu-id="b88b6-130">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b88b6-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
