---
title: Exemple de StopProcessSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7bed607-369b-4507-87fa-f6011c2f1970
caps.latest.revision: 9
ms.openlocfilehash: 2ce146df05ef876d9c17f560628ebac2c39e57bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067261"
---
# <a name="stopprocesssample01-sample"></a><span data-ttu-id="79aee-102">Exemple StopProcessSample01</span><span class="sxs-lookup"><span data-stu-id="79aee-102">StopProcessSample01 Sample</span></span>

<span data-ttu-id="79aee-103">Cet exemple montre comment écrire une applet de commande qui demande des commentaires à l’utilisateur avant d’essayer d’arrêter un processus et comment implémenter un `PassThru` indiquant que l’utilisateur souhaite l’applet de commande pour retourner un objet de paramètre.</span><span class="sxs-lookup"><span data-stu-id="79aee-103">This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter indicating that the user wants the cmdlet to return an object.</span></span> <span data-ttu-id="79aee-104">Cette applet de commande est similaire à la `Stop-Process` applet de commande fournie par Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="79aee-104">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="79aee-105">Guide pratique pour générer l’exemple à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79aee-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="79aee-106">Avec le Windows SDK PowerShell 2.0 installé, accédez au dossier StopProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="79aee-106">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample01 folder.</span></span> <span data-ttu-id="79aee-107">L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="79aee-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample01.</span></span>

2. <span data-ttu-id="79aee-108">Double-cliquez sur l’icône pour le fichier solution (.sln).</span><span class="sxs-lookup"><span data-stu-id="79aee-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="79aee-109">L’exemple de projet s’ouvre dans Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79aee-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="79aee-110">Dans le **Build** menu, sélectionnez **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="79aee-110">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="79aee-111">La bibliothèque de l’exemple est générée dans les dossiers \bin ou \bin\debug par défaut.</span><span class="sxs-lookup"><span data-stu-id="79aee-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="79aee-112">Comment exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="79aee-112">How to run the sample</span></span>

1. <span data-ttu-id="79aee-113">Créez le dossier de module suivant :</span><span class="sxs-lookup"><span data-stu-id="79aee-113">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample01`

2. <span data-ttu-id="79aee-114">Copiez l’exemple d’assembly dans le dossier de module.</span><span class="sxs-lookup"><span data-stu-id="79aee-114">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="79aee-115">Démarrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="79aee-115">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="79aee-116">Exécutez la commande suivante pour charger l’assembly dans Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="79aee-116">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample01`

5. <span data-ttu-id="79aee-117">Exécutez la commande suivante pour exécuter l’applet de commande :</span><span class="sxs-lookup"><span data-stu-id="79aee-117">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="79aee-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="79aee-118">Requirements</span></span>

<span data-ttu-id="79aee-119">Cet exemple requiert Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="79aee-119">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="79aee-120">Montre</span><span class="sxs-lookup"><span data-stu-id="79aee-120">Demonstrates</span></span>

<span data-ttu-id="79aee-121">Cet exemple montre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="79aee-121">This sample demonstrates the following.</span></span>

- <span data-ttu-id="79aee-122">Déclarer une classe de l’applet de commande à l’aide de l’attribut de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="79aee-122">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="79aee-123">Déclarer une applet de commande des paramètres à l’aide de l’attribut de paramètre.</span><span class="sxs-lookup"><span data-stu-id="79aee-123">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="79aee-124">La méthode ShouldProcess pour demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="79aee-124">Calling the ShouldProcess method to request confirmation.</span></span>

- <span data-ttu-id="79aee-125">Implémentation d’un `PassThru` paramètre qui indique si l’utilisateur souhaite que l’applet de commande pour retourner un objet.</span><span class="sxs-lookup"><span data-stu-id="79aee-125">Implementing a `PassThru` parameter that indicates if the user wants the cmdlet to return an object.</span></span> <span data-ttu-id="79aee-126">Par défaut, cette applet de commande ne retourne pas d’un objet au pipeline.</span><span class="sxs-lookup"><span data-stu-id="79aee-126">By default, this cmdlet does not return an object to the pipeline.</span></span>

## <a name="example"></a><span data-ttu-id="79aee-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="79aee-127">Example</span></span>

<span data-ttu-id="79aee-128">Cet exemple montre comment implémenter un `PassThru` paramètre qui indique que l’utilisateur veut l’applet de commande pour retourner un objet, et comment demander des commentaires utilisateur en appels à la `ShouldProcess` et `ShouldContinue` méthodes.</span><span class="sxs-lookup"><span data-stu-id="79aee-128">This sample shows how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object, and how to request user feedback by calls to the `ShouldProcess` and `ShouldContinue` methods.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;    // Windows PowerShell namespace
using System.Globalization;

namespace Microsoft.Samples.PowerShell.Commands
{
   #region StopProcCommand

    /// <summary>
   /// This class implements the stop-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsLifecycle.Stop, "Proc",
       SupportsShouldProcess = true)]
   public class StopProcCommand : Cmdlet
   {
       #region Parameters

      /// <summary>
      /// This parameter provides the list of process names on
      /// which the Stop-Proc cmdlet will work.
      /// </summary>
       [Parameter(
          Position = 0,
          Mandatory = true,
          ValueFromPipeline = true,
          ValueFromPipelineByPropertyName = true
       )]
       public string[] Name
       {
           get { return processNames; }
           set { processNames = value; }
       }
       private string[] processNames;

       /// <summary>
       /// This parameter overrides the ShouldContinue call to force
       /// the cmdlet to stop its operation. This parameter should always
       /// be used with caution.
       /// </summary>
       [Parameter]
       public SwitchParameter Force
       {
           get { return force; }
           set { force = value; }
       }
       private bool force;

       /// <summary>
       /// This parameter indicates that the cmdlet should return
       /// an object to the pipeline after the processing has been
       /// completed.
       /// </summary>
       [Parameter]
       public SwitchParameter PassThru
       {
           get { return passThru; }
           set { passThru = value; }
       }
       private bool passThru;

       #endregion Parameters

       #region Cmdlet Overrides

       /// <summary>
       /// The ProcessRecord method does the following for each of the
       /// requested process names:
       /// 1) Check that the process is not a critical process.
       /// 2) Attempt to stop that process.
       /// If no process is requested then nothing occurs.
       /// </summary>
       protected override void ProcessRecord()
       {
           foreach (string name in processNames)
           {
               // For every process name passed to the cmdlet, get the associated
               // processes.
               // Write a nonterminating error for failure to retrieve
               // a process.
               Process[] processes;

               try
               {
                   processes = Process.GetProcessesByName(name);
               }
               catch (InvalidOperationException ioe)
               {
                   WriteError(new ErrorRecord(ioe,"UnableToAccessProcessByName",
                       ErrorCategory.InvalidOperation, name));

                   continue;
               }

               // Try to stop the processes that have been retrieved.
               foreach (Process process in processes)
               {
                   string processName;

                   try
                   {
                       processName = process.ProcessName;
                   }
                   catch (Win32Exception e)
                   {
                      WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                                           ErrorCategory.ReadError, process));
                      continue;
                   }

                   // Confirm the operation with the user first.
                   // This is always false if the WhatIf parameter is set.
                   if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,"{0} ({1})", processName,
                               process.Id)))
                   {
                       continue;
                   }

                   // Make sure that the user really wants to stop a critical
                   // process that could possibly stop the computer.
                   bool criticalProcess =
                       criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

                   if (criticalProcess &&!force)
                   {
                       string message = String.Format
                           (CultureInfo.CurrentCulture,
                                "The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                                    processName);

                       // It is possible that the ProcessRecord method is called
                       // multiple times when objects are received as inputs from
                       // the pipeline. So to retain YesToAll and NoToAll input that
                       // the user may enter across multiple calls to this function,
                       // they are stored as private members of the cmdlet.
                       if (!ShouldContinue(message, "Warning!",
                                               ref yesToAll, ref noToAll))
                       {
                           continue;
                       }
                   } // if (criticalProcess...

                   // Stop the named process.
                   try
                   {
                       process.Kill();
                   }
                   catch (Exception e)
                   {
                       if ((e is Win32Exception) || (e is SystemException) ||
                          (e is InvalidOperationException))
                       {
                           // This process could not be stopped so write
                           // a nonterminating error.
                           WriteError(new ErrorRecord(e, "CouldNotStopProcess",
                                           ErrorCategory.CloseError, process));
                           continue;
                       } // if ((e is...
                       else throw;
                   } // catch

                   // If the PassThru parameter is
                   // specified, return the terminated process.
                   if (passThru)
                   {
                       WriteObject(process);
                   }
               } // foreach (Process...
           } // foreach (string...
       } // ProcessRecord

       #endregion Cmdlet Overrides

       #region Private Data

       private bool yesToAll, noToAll;

       /// <summary>
       /// Partial list of critical processes that should not be
       /// stopped.  Lower case is used for case insensitive matching.
       /// </summary>
       private ArrayList criticalProcessNames = new ArrayList(
          new string[] { "system", "winlogon", "spoolsv" }
       );

       #endregion Private Data

   } // StopProcCommand

   #endregion StopProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="79aee-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79aee-129">See Also</span></span>

[<span data-ttu-id="79aee-130">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="79aee-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
