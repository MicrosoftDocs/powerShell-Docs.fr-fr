---
title: Exemple de StopProcessSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31298f1b-8b76-4637-8406-863f5ad27e53
caps.latest.revision: 8
ms.openlocfilehash: 7ba1f11b9aa1e602d5f09d6ee0978095aec41837
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854425"
---
# <a name="stopprocesssample03-sample"></a><span data-ttu-id="400f6-102">Exemple StopProcessSample03</span><span class="sxs-lookup"><span data-stu-id="400f6-102">StopProcessSample03 Sample</span></span>

<span data-ttu-id="400f6-103">Cet exemple montre comment écrire une applet de commande dont les paramètres ont des alias et dont les paramètres prennent en charge les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="400f6-103">This sample shows how to write a cmdlet whose parameters have aliases and whose parameters support wildcard characters.</span></span> <span data-ttu-id="400f6-104">Cette applet de commande est similaire à la `Stop-Process` applet de commande fournie par Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="400f6-104">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="400f6-105">Guide pratique pour générer l’exemple à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="400f6-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="400f6-106">Avec le Windows SDK PowerShell 2.0 installé, accédez au dossier StopProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="400f6-106">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample03 folder.</span></span> <span data-ttu-id="400f6-107">L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="400f6-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample03.</span></span>

2. <span data-ttu-id="400f6-108">Double-cliquez sur l’icône pour le fichier solution (.sln).</span><span class="sxs-lookup"><span data-stu-id="400f6-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="400f6-109">L’exemple de projet s’ouvre dans Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="400f6-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="400f6-110">Dans le **Build** menu, sélectionnez **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="400f6-110">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="400f6-111">La bibliothèque de l’exemple est générée dans les dossiers \bin ou \bin\debug par défaut.</span><span class="sxs-lookup"><span data-stu-id="400f6-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="400f6-112">Comment exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="400f6-112">How to run the sample</span></span>

1. <span data-ttu-id="400f6-113">Créez le dossier de module suivant :</span><span class="sxs-lookup"><span data-stu-id="400f6-113">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample03`

2. <span data-ttu-id="400f6-114">Copiez l’exemple d’assembly dans le dossier de module.</span><span class="sxs-lookup"><span data-stu-id="400f6-114">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="400f6-115">Démarrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="400f6-115">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="400f6-116">Exécutez la commande suivante pour charger l’assembly dans Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="400f6-116">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample03`

5. <span data-ttu-id="400f6-117">Exécutez la commande suivante pour exécuter l’applet de commande :</span><span class="sxs-lookup"><span data-stu-id="400f6-117">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="400f6-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="400f6-118">Requirements</span></span>

<span data-ttu-id="400f6-119">Cet exemple requiert Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="400f6-119">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="400f6-120">Montre</span><span class="sxs-lookup"><span data-stu-id="400f6-120">Demonstrates</span></span>

<span data-ttu-id="400f6-121">Cet exemple montre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="400f6-121">This sample demonstrates the following.</span></span>

- <span data-ttu-id="400f6-122">Déclarer une classe de l’applet de commande à l’aide de l’attribut de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="400f6-122">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="400f6-123">Déclarer une applet de commande des paramètres à l’aide de l’attribut de paramètre.</span><span class="sxs-lookup"><span data-stu-id="400f6-123">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="400f6-124">Ajout d’alias aux déclarations de paramètre...</span><span class="sxs-lookup"><span data-stu-id="400f6-124">Adding aliases to parameter declarations..</span></span>

- <span data-ttu-id="400f6-125">Prise en charge de caractère générique ajout aux paramètres.</span><span class="sxs-lookup"><span data-stu-id="400f6-125">Adding wildcard support to parameters.</span></span>

## <a name="example"></a><span data-ttu-id="400f6-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="400f6-126">Example</span></span>

<span data-ttu-id="400f6-127">Cet exemple montre comment déclarer des alias de paramètre et de prendre en charge des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="400f6-127">This sample shows how to declare parameter aliases and support wildcards.</span></span>

```
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;             //Windows PowerShell namespace
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
          ValueFromPipelineByPropertyName = true,
          HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
       )]
       [Alias("ProcessName")]
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
       [Parameter(
          ValueFromPipelineByPropertyName = true,
          HelpMessage = "If set, the process(es) will be passed to the pipeline after stopped."
       )]
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
           Process[] processes = null;

           try
           {
               processes = Process.GetProcesses();
           }
           catch (InvalidOperationException ioe)
           {
               base.ThrowTerminatingError(new ErrorRecord(ioe,
                         "UnableToAcessProcessList",
                             ErrorCategory.InvalidOperation,
                                 null));
           }

           // For every process name passed to the cmdlet, get the associated
           // processes.
           // Write a nonterminating error for failure to retrieve
           // a process.
           foreach (string name in processNames)
           {
               // Write a user-friendly verbose message to the pipeline. These
               // messages are intended to give the user detailed information
               // on the operations performed by the cmdlet. These messages will
               // appear with the -Verbose option.
               string message = String.Format(CultureInfo.CurrentCulture,
                                    "Attempting to stop process \"{0}\".", name);
               WriteVerbose(message);

               // Validate the process name against a wildcard pattern.
               // If the name does not contain any wildcard patterns, it
               // will be treated as an exact match.
               WildcardOptions options = WildcardOptions.IgnoreCase |
                                         WildcardOptions.Compiled;
               WildcardPattern wildcard = new WildcardPattern(name,options);

               foreach (Process process in processes)
               {
                   string processName;

                   try
                   {
                       processName = process.ProcessName;
                   }
                   catch (Win32Exception e)
                   {
                       WriteError(new ErrorRecord(
                                              e, "ProcessNameNotFound",
                                                ErrorCategory.ObjectNotFound,
                                                  process)
                                 );
                       continue;
                   }

                   // Write a debug message to the host that can be used when
                   // troubleshooting a problem. All debug messages will appear
                   // with the -Debug option.
                   message = String.Format(CultureInfo.CurrentCulture,
                                "Acquired name for pid {0} : \"{1}\"",
                                      process.Id, processName);
                   WriteDebug(message);

                   // Check to see if this process matches the current process
                   // name pattern. Skip this process if it does not.
                   if (!wildcard.IsMatch(processName))
                   {
                       continue;
                   }

                   // Stop the process.
                   SafeStopProcess(process);
               } // foreach (Process...
           } // foreach (string...
       } // ProcessRecord

       #endregion Cmdlet Overrides

       #region Helper Methods

       /// <summary>
       /// Safely stops a named process.  Used as standalone function
       /// to declutter the ProcessRecord method.
       /// </summary>
       /// <param name="process">The process to stop.</param>
       private void SafeStopProcess(Process process)
       {
           string processName = null;
           try
           {
               processName = process.ProcessName;
           }
           catch (Win32Exception e)
           {
               WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                                 ErrorCategory.ObjectNotFound, process));
               return;
           }

           string message = null;

           // Confirm the operation first.
           // This is always false if the WhatIf parametr is specified.
           if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,
                    "{0} ({1})", processName, process.Id)))
           {
               return;
           }

           // Make sure that the user really wants to stop a critical
           // process that could possibly stop the computer.
           bool criticalProcess = criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

           if (criticalProcess && !force)
           {
               message = String.Format(CultureInfo.CurrentCulture,
                            "The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                                processName);

               // It is possible that ProcessRecord is called multiple
               // when objects are recieved as inputs from a pipeline.
               // So, to retain YesToAll and NoToAll input that the
               // user may enter across mutilple calls to this
               // function, they are stored as private members of the
               // Cmdlet.
               if (!ShouldContinue(message, "Warning!",
                            ref yesToAll, ref noToAll))
               {
                   return;
               }
           } // if (criticalProcess...

           // Display a warning message if stopping a critical
           // process.
           if (criticalProcess)
           {
               message = String.Format(CultureInfo.CurrentCulture,
                            "Stopping the critical process \"{0}\".",
                                processName);
               WriteWarning(message);
           } // if (criticalProcess...

           try
           {
               // Stop the process.
               process.Kill();
           }
           catch (Exception e)
           {
               if ((e is Win32Exception) || (e is SystemException) ||
                   (e is InvalidOperationException))
               {
                   // This process could not be stopped so write
                   // a non-terminating error.
                   WriteError(new ErrorRecord(e, "CouldNotStopProcess",
                                    ErrorCategory.CloseError,
                                    process)
                              );
                   return;
               } // if ((e is...
               else throw;
           } // catch

           message = String.Format(CultureInfo.CurrentCulture,
                        "Stopped process \"{0}\", pid {1}.",
                              processName, process.Id);

           WriteVerbose(message);

           // If the PassThru parameter is specified,
           // return the terminated process to the pipeline.
           if (passThru)
           {
               message = String.Format(CultureInfo.CurrentCulture,
                            "Writing process \"{0}\" to pipeline",
                                processName);
               WriteDebug(message);
               WriteObject(process);
           } // if (passThru...
       } // SafeStopProcess

       #endregion Helper Methods

       #region Private Data

       private bool yesToAll, noToAll;

       /// <summary>
       /// Partial list of the critical processes that should not be
       /// stopped.  Lower case is used for case insensitive matching.
       /// </summary>
       private ArrayList criticalProcessNames = new ArrayList(
          new string[] { "system", "winlogon", "spoolsv" }
       );

       #endregion Private Data

   } // StopProcCommand

   #endregion StopProcCommand
} // namespace Microsoft.Samples.PowerShell.Commands
```

## <a name="see-also"></a><span data-ttu-id="400f6-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="400f6-128">See Also</span></span>

[<span data-ttu-id="400f6-129">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="400f6-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
