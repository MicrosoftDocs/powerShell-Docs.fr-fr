---
title: Exemple GetProcessSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 27f1c346863458920b310c6c4ce1403b3aab69ba
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563799"
---
# <a name="getprocesssample01-sample"></a><span data-ttu-id="98cb4-102">Exemple GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="98cb4-102">GetProcessSample01 Sample</span></span>

<span data-ttu-id="98cb4-103">Cet exemple montre comment implémenter une applet de commande qui récupère les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="98cb4-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="98cb4-104">Cette applet de commande est une version simplifiée de l’applet de commande `Get-Process` fournie par Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="98cb4-104">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="98cb4-105">Comment générer l’exemple à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98cb4-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="98cb4-106">Une fois le kit de développement logiciel (SDK) 2,0 Windows PowerShell installé, accédez au dossier GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="98cb4-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="98cb4-107">L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="98cb4-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="98cb4-108">Double-cliquez sur l’icône du fichier solution (. sln).</span><span class="sxs-lookup"><span data-stu-id="98cb4-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="98cb4-109">L’exemple de projet s’ouvre dans Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98cb4-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="98cb4-110">Dans le menu **Générer**, sélectionnez **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="98cb4-110">In the **Build** menu, select **Build Solution**.</span></span>

  <span data-ttu-id="98cb4-111">La bibliothèque de l’exemple sera générée dans les dossiers \bin ou \bin\debug par défaut.</span><span class="sxs-lookup"><span data-stu-id="98cb4-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="98cb4-112">Comment exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="98cb4-112">How to run the sample</span></span>

1. <span data-ttu-id="98cb4-113">Ouvrez une fenêtre d’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="98cb4-113">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="98cb4-114">Accédez au répertoire contenant le fichier Sample. dll.</span><span class="sxs-lookup"><span data-stu-id="98cb4-114">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="98cb4-115">Exécutez installutil « GetProcessSample01. dll ».</span><span class="sxs-lookup"><span data-stu-id="98cb4-115">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="98cb4-116">Démarrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98cb4-116">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="98cb4-117">Exécutez la commande suivante pour ajouter le composant logiciel enfichable à l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="98cb4-117">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="98cb4-118">Entrez la commande suivante pour exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="98cb4-118">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="98cb4-119">Voici un exemple de sortie résultant de la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="98cb4-119">This is a sample output that results from following these steps.</span></span>

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a><span data-ttu-id="98cb4-120">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="98cb4-120">Requirements</span></span>

<span data-ttu-id="98cb4-121">Cet exemple requiert Windows PowerShell 1,0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="98cb4-121">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="98cb4-122">Illustre le</span><span class="sxs-lookup"><span data-stu-id="98cb4-122">Demonstrates</span></span>

<span data-ttu-id="98cb4-123">Cet exemple illustre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="98cb4-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="98cb4-124">Création d’un exemple d’applet de commande de base.</span><span class="sxs-lookup"><span data-stu-id="98cb4-124">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="98cb4-125">Définition d’une classe d’applet de commande à l’aide de l’attribut d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="98cb4-125">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="98cb4-126">Création d’un composant logiciel enfichable qui fonctionne avec Windows PowerShell 1,0 et Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="98cb4-126">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="98cb4-127">Les exemples suivants utilisent des modules à la place des composants logiciels enfichables afin qu’ils requièrent Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="98cb4-127">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="98cb4-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="98cb4-128">Example</span></span>

<span data-ttu-id="98cb4-129">Cet exemple montre comment créer une applet de commande simple et son composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="98cb4-129">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a><span data-ttu-id="98cb4-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98cb4-130">See Also</span></span>

[<span data-ttu-id="98cb4-131">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="98cb4-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
