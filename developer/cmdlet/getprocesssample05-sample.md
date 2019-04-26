---
title: Exemple de GetProcessSample05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6aebd53f-0610-4959-88b2-42339588c859
caps.latest.revision: 6
ms.openlocfilehash: ad4300937c10652b677346a62c42fa4f6e8513cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068009"
---
# <a name="getprocesssample05-sample"></a><span data-ttu-id="af7b6-102">Exemple GetProcessSample05</span><span class="sxs-lookup"><span data-stu-id="af7b6-102">GetProcessSample05 Sample</span></span>

<span data-ttu-id="af7b6-103">Cet exemple montre une version complète de l’applet de commande Get-Process.</span><span class="sxs-lookup"><span data-stu-id="af7b6-103">This sample shows a complete version of the Get-Proc cmdlet.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="af7b6-104">Guide pratique pour générer l’exemple à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="af7b6-104">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="af7b6-105">Ouvrez l’Explorateur Windows et accédez au répertoire GetProcessSample05 sous le répertoire d’exemples.</span><span class="sxs-lookup"><span data-stu-id="af7b6-105">Open Windows Explorer and navigate to the GetProcessSample05 directory under the Samples directory.</span></span>

   <span data-ttu-id="af7b6-106">Avec le Windows SDK PowerShell 2.0 installé, accédez au dossier GetProcessSample05.</span><span class="sxs-lookup"><span data-stu-id="af7b6-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample05 folder.</span></span> <span data-ttu-id="af7b6-107">L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample05.</span><span class="sxs-lookup"><span data-stu-id="af7b6-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample05.</span></span>

2. <span data-ttu-id="af7b6-108">Double-cliquez sur l’icône pour le fichier solution (.sln).</span><span class="sxs-lookup"><span data-stu-id="af7b6-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="af7b6-109">L’exemple de projet s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="af7b6-109">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="af7b6-110">Dans le **Build** menu, sélectionnez **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="af7b6-110">In the **Build** menu, select **Build Solution**.</span></span>

   <span data-ttu-id="af7b6-111">La bibliothèque de l’exemple est générée dans les répertoires de \bin ou \bin\debug par défaut.</span><span class="sxs-lookup"><span data-stu-id="af7b6-111">The library for the sample will be built in the default \bin or \bin\debug directories.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="af7b6-112">Comment exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="af7b6-112">How to run the sample</span></span>

1. <span data-ttu-id="af7b6-113">Créez le dossier de module suivant :</span><span class="sxs-lookup"><span data-stu-id="af7b6-113">Create the following module folder:</span></span>

   `[user]/documents/windowspowershell/modules/GetProcessSample05`

2. <span data-ttu-id="af7b6-114">Copiez l’exemple d’assembly dans le dossier de module.</span><span class="sxs-lookup"><span data-stu-id="af7b6-114">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="af7b6-115">Démarrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af7b6-115">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="af7b6-116">Exécutez la commande suivante pour charger l’assembly dans Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="af7b6-116">Run the following command to load the assembly into Windows PowerShell:</span></span>

   `Import-module getprossessample05`

5. <span data-ttu-id="af7b6-117">Exécutez la commande suivante pour exécuter l’applet de commande :</span><span class="sxs-lookup"><span data-stu-id="af7b6-117">Run the following command to run the cmdlet:</span></span>

   `get-proc`

## <a name="requirements"></a><span data-ttu-id="af7b6-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="af7b6-118">Requirements</span></span>

<span data-ttu-id="af7b6-119">Cet exemple requiert Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="af7b6-119">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="af7b6-120">Montre</span><span class="sxs-lookup"><span data-stu-id="af7b6-120">Demonstrates</span></span>

<span data-ttu-id="af7b6-121">Cet exemple montre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="af7b6-121">This sample demonstrates the following.</span></span>

- <span data-ttu-id="af7b6-122">Déclaration de la classe d’applet de commande à l’aide de l’attribut de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="af7b6-122">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="af7b6-123">Déclaration d’un paramètre de l’applet de commande à l’aide de l’attribut de paramètre.</span><span class="sxs-lookup"><span data-stu-id="af7b6-123">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="af7b6-124">Déterminant les positions des paramètres.</span><span class="sxs-lookup"><span data-stu-id="af7b6-124">Specifying positions for parameters.</span></span>

- <span data-ttu-id="af7b6-125">En spécifiant que les paramètres peuvent prendre d’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="af7b6-125">Specifying that parameters can take input from the pipeline.</span></span> <span data-ttu-id="af7b6-126">L’entrée peut provenir d’un objet ou une valeur d’une propriété d’un objet dont le nom propriété est le même que le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="af7b6-126">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="af7b6-127">Déclaration d’un attribut de validation pour le paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="af7b6-127">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="af7b6-128">Gestion des erreurs et exceptions.</span><span class="sxs-lookup"><span data-stu-id="af7b6-128">Handling errors and exceptions.</span></span>

- <span data-ttu-id="af7b6-129">Écriture de messages de débogage.</span><span class="sxs-lookup"><span data-stu-id="af7b6-129">Writing debug messages.</span></span>

## <a name="example"></a><span data-ttu-id="af7b6-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="af7b6-130">Example</span></span>

<span data-ttu-id="af7b6-131">Cet exemple montre comment créer une applet de commande qui affiche la liste des processus spécifiés.</span><span class="sxs-lookup"><span data-stu-id="af7b6-131">This sample shows how to create a cmdlet that displays a list of specified processes.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Collections.Generic;
    using System.Diagnostics;
    using System.Management.Automation;    // Windows PowerShell namespace.
    using System.Security.Permissions;
    using Win32Exception = System.ComponentModel.Win32Exception;
    #region GetProcCommand

    /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc",
      DefaultParameterSetName = "ProcessName")]
   public class GetProcCommand : PSCmdlet
   {
       #region Fields
       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

       /// <summary>
       /// The identifiers of the processes to act on.
       /// </summary>
       private int[] processIds;

       /// <summary>
       /// The process objects to act on.
       /// </summary>
       private Process[] inputObjects;

       #endregion Fields

       #region Parameters

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ParameterSetName = "ProcessName",
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      /// <summary>
      /// Gets or sets the list of process identifiers on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         ParameterSetName = "Id",
         Mandatory = true,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true,
         HelpMessage = "The unique id of the process to get.")]
      public int[] Id
      {
         get { return this.processIds; }
         set { this.processIds = value; }
      }

      /// <summary>
      /// Gets or sets Process objects directly. If the input is a
      /// stream of [collection of] Process objects, the cmdlet bypasses the
      /// ProcessName and Id parameters and reads the Process objects
      /// directly.  This allows the cmdlet to deal with processes that have
      /// wildcard characters in their name.
      /// <value>Process objects</value>
      /// </summary>
      [Parameter(
         ParameterSetName = "InputObject",
         Mandatory = true,
         ValueFromPipeline = true)]
      public Process[] Input
      {
         get { return this.inputObjects; }
         set { this.inputObjects = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes. Then, the WriteObject
      /// method writes the associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         List<Process> matchingProcesses;

         WriteDebug("Obtaining the list of matching process objects.");

         switch (ParameterSetName)
         {
            case "Id":
               matchingProcesses = this.GetMatchingProcessesById();
               break;
            case "ProcessName":
               matchingProcesses = this.GetMatchingProcessesByName();
               break;
            case "InputObject":
               matchingProcesses = this.GetProcessesByInput();
               break;
            default:
               ThrowTerminatingError(
                   new ErrorRecord(
                       new ArgumentException("Bad ParameterSetName"),
                       "UnableToAccessProcessList",
                       ErrorCategory.InvalidOperation,
                       null));
               return;
         } // switch (ParameterSetName)

         WriteDebug("Outputting the matching process objects.");

         matchingProcesses.Sort(ProcessComparison);

         foreach (Process process in matchingProcesses)
         {
            WriteObject(process);
         }
      } // ProcessRecord

      #endregion Overrides

      #region protected Methods and Data

      /// <summary>
      /// Retrieves the list of all processes matching the ProcessName
      /// parameter and generates a nonterminating error for each
      /// specified process name which is not found even though the name
      /// contains no wildcards.
      /// </summary>
      /// <returns>The matching processes.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetMatchingProcessesByName()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> allProcesses =
            new List<Process>(Process.GetProcesses());

         // The keys dictionary is used for rapid lookup of
         // processes that are already in the matchingProcesses list.
         Dictionary<int, byte> keys = new Dictionary<int, byte>();

         List<Process> matchingProcesses = new List<Process>();

         if (null == this.processNames)
         {
             matchingProcesses.AddRange(allProcesses);
         }
         else
         {
             foreach (string pattern in this.processNames)
             {
                 WriteVerbose("Finding matches for process name \""
                    + pattern + "\".");

                 // WildCard search on the available processes
                 WildcardPattern wildcard =
                    new WildcardPattern(
                        pattern,
                        WildcardOptions.IgnoreCase);

                 bool found = false;

                 foreach (Process process in allProcesses)
                 {
                     if (!keys.ContainsKey(process.Id))
                     {
                         string processName = SafeGetProcessName(process);

                         // Remove the process from the allProcesses list
                         // so that it is not tested again.
                         if (processName.Length == 0)
                         {
                             allProcesses.Remove(process);
                         }

                         // Perform a wildcard search on this particular
                         // process name and check whether it matches the
                         // pattern specified.
                         if (!wildcard.IsMatch(processName))
                         {
                             continue;
                         }

                         WriteDebug("Found matching process id "
                            + process.Id + ".");

                         // A match is found.
                         found = true;

                         // Store the process identifier so that the same process
                         // is not added twice.
                         keys.Add(process.Id, 0);

                         // Add the process to the processes list.
                         matchingProcesses.Add(process);
                     }
                 } // foreach (Process...

                 if (!found &&
                   !WildcardPattern.ContainsWildcardCharacters(pattern))
                 {
                     WriteError(new ErrorRecord(
                        new ArgumentException("Cannot find process name "
                           + "\"" + pattern + "\"."),
                        "ProcessNameNotFound",
                        ErrorCategory.ObjectNotFound,
                        pattern));
                 }
             } // foreach (string...
         } // if (null...

         return matchingProcesses;
      } // GetMatchingProcessesByName

      /// <summary>
      /// Returns the name of a process.  If an error occurs, a blank
      /// string is returned.
      /// </summary>
      /// <param name="process">The process whose name is
      /// returned.</param>
      /// <returns>The name of the process.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand, Unrestricted = true)]
      protected static string SafeGetProcessName(Process process)
      {
         new EnvironmentPermission(PermissionState.Unrestricted).Assert();
         string name = String.Empty;

         if (process != null)
         {
            try
            {
                return process.ProcessName;
            }
            catch (Win32Exception)
            {
            }
            catch (InvalidOperationException)
            {
            }
         }

         return name;
     } // SafeGetProcessName

      #endregion Cmdlet Overrides

      #region Private Methods

      /// <summary>
      /// Function to sort by process name first, and then by
      /// the process identifier.
      /// </summary>
      /// <param name="x">First process object.</param>
      /// <param name="y">Second process object.</param>
      /// <returns>
      /// Returns less than zero if x is less than y,
      /// greater than 0 if x is greater than y, and 0 if x == y.
      /// </returns>
      private static int ProcessComparison(Process x, Process y)
      {
         int diff = String.Compare(
            SafeGetProcessName(x),
            SafeGetProcessName(y),
            StringComparison.CurrentCultureIgnoreCase);

         if (0 != diff)
         {
             return diff;
         }
         else
         {
             return x.Id.CompareTo(y.Id);
         }
      }

      /// <summary>
      /// Retrieves the list of all processes matching the Id
      /// parameter and generates a nonterminating error for
      /// each specified process identifier which is not found.
      /// </summary>
      /// <returns>
      /// An array of processes that match the given identifier.
      /// </returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetMatchingProcessesById()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> matchingProcesses = new List<Process>();

         if (null != this.processIds)
         {
            // The keys dictionary is used for rapid lookup of the
            // processes already in the matchingProcesses list.
            Dictionary<int, byte> keys = new Dictionary<int, byte>();

            foreach (int processId in this.processIds)
            {
               WriteVerbose("Finding match for process id "
                  + processId + ".");

               if (!keys.ContainsKey(processId))
               {
                  Process process;
                  try
                  {
                      process = Process.GetProcessById(processId);
                  }
                  catch (ArgumentException ex)
                  {
                     WriteError(new ErrorRecord(
                        ex,
                        "ProcessIdNotFound",
                        ErrorCategory.ObjectNotFound,
                        processId));
                     continue;
                  }

                  WriteDebug("Found matching process.");

                  matchingProcesses.Add(process);
                  keys.Add(processId, 0);
               }
            }
         }

         return matchingProcesses;
      } // GetMatchingProcessesById

      /// <summary>
      /// Retrieves the list of all processes matching the InputObject
      /// parameter.
      /// </summary>
      /// <returns>The matching processes.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetProcessesByInput()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> matchingProcesses = new List<Process>();

         if (null != this.Input)
         {
            // The keys dictionary is used for rapid lookup of the
            // processes already in the matchingProcesses list.
            Dictionary<int, byte> keys = new Dictionary<int, byte>();

            foreach (Process process in this.Input)
            {
               WriteVerbose("Refreshing process object.");

               if (!keys.ContainsKey(process.Id))
               {
                  try
                  {
                      process.Refresh();
                  }
                  catch (Win32Exception)
                  {
                  }
                  catch (InvalidOperationException)
                  {
                  }

                  matchingProcesses.Add(process);
               }
            }
         }

         return matchingProcesses;
      } // GetProcessesByInput
      #endregion Private Methods
    } // End GetProcCommand class.

    #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="af7b6-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af7b6-132">See Also</span></span>

[<span data-ttu-id="af7b6-133">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="af7b6-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
