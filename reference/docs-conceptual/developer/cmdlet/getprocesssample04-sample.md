---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple GetProcessSample04
description: Exemple GetProcessSample04
ms.openlocfilehash: 4b2b7f7ed5fd87711d0d7872caaf75d453de4832
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652739"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="35dd6-103">Exemple GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="35dd6-103">GetProcessSample04 Sample</span></span>

<span data-ttu-id="35dd6-104">Cet exemple montre comment implémenter une applet de commande qui récupère les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="35dd6-104">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="35dd6-105">Il génère une erreur sans fin si une erreur se produit lors de la récupération d’un processus.</span><span class="sxs-lookup"><span data-stu-id="35dd6-105">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="35dd6-106">Cette applet de commande est une version simplifiée de l’applet de commande `Get-Process` fournie par Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="35dd6-106">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="35dd6-107">Comment générer l’exemple à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="35dd6-107">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="35dd6-108">Une fois le kit de développement logiciel (SDK) 2,0 Windows PowerShell installé, accédez au dossier GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="35dd6-108">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="35dd6-109">L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="35dd6-109">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="35dd6-110">Double-cliquez sur l’icône du fichier solution (. sln).</span><span class="sxs-lookup"><span data-stu-id="35dd6-110">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="35dd6-111">L’exemple de projet s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="35dd6-111">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="35dd6-112">Dans le menu **Générer**, sélectionnez **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="35dd6-112">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="35dd6-113">La bibliothèque de l’exemple sera générée dans les dossiers \bin ou \bin\debug par défaut.</span><span class="sxs-lookup"><span data-stu-id="35dd6-113">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="35dd6-114">Comment exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="35dd6-114">How to run the sample</span></span>

1. <span data-ttu-id="35dd6-115">Créez le dossier de module suivant :</span><span class="sxs-lookup"><span data-stu-id="35dd6-115">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="35dd6-116">Copiez l’exemple d’assembly dans le dossier du module.</span><span class="sxs-lookup"><span data-stu-id="35dd6-116">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="35dd6-117">Démarrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35dd6-117">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="35dd6-118">Exécutez la commande suivante pour charger l’assembly dans Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="35dd6-118">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="35dd6-119">Exécutez la commande suivante pour exécuter l’applet de commande :</span><span class="sxs-lookup"><span data-stu-id="35dd6-119">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="35dd6-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="35dd6-120">Requirements</span></span>

<span data-ttu-id="35dd6-121">Cet exemple requiert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="35dd6-121">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="35dd6-122">Illustre le</span><span class="sxs-lookup"><span data-stu-id="35dd6-122">Demonstrates</span></span>

<span data-ttu-id="35dd6-123">Cet exemple illustre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="35dd6-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="35dd6-124">Déclaration d’une classe d’applet de commande à l’aide de l’attribut d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35dd6-124">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="35dd6-125">Déclaration d’un paramètre d’applet de commande à l’aide de l’attribut Parameter.</span><span class="sxs-lookup"><span data-stu-id="35dd6-125">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="35dd6-126">Spécification de la position du paramètre.</span><span class="sxs-lookup"><span data-stu-id="35dd6-126">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="35dd6-127">Spécifie que le paramètre prend l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="35dd6-127">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="35dd6-128">L’entrée peut être extraite à partir d’un objet ou d’une valeur d’une propriété d’un objet dont le nom de la propriété est le même que le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="35dd6-128">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="35dd6-129">Déclaration d’un attribut de validation pour l’entrée de paramètre.</span><span class="sxs-lookup"><span data-stu-id="35dd6-129">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="35dd6-130">Intercepter une erreur ne se terminant pas et en écrivant un message d’erreur dans le flux d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="35dd6-130">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="35dd6-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="35dd6-131">Example</span></span>

<span data-ttu-id="35dd6-132">Cet exemple montre comment créer une applet de commande qui gère les erreurs qui ne se terminent pas et qui écrit des messages d’erreur dans le flux d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="35dd6-132">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
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
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="35dd6-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35dd6-133">See Also</span></span>

[<span data-ttu-id="35dd6-134">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="35dd6-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
