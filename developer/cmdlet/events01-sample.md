---
title: Exemple de Events01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: 8f745cc0e5ef6db7a6bbdf39d826103f3b8a98ce
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229288"
---
# <a name="events01-sample"></a><span data-ttu-id="b5a4c-102">Exemple Events01</span><span class="sxs-lookup"><span data-stu-id="b5a4c-102">Events01 Sample</span></span>

<span data-ttu-id="b5a4c-103">Cet exemple montre comment créer une applet de commande qui permet à l’utilisateur enregistrer les événements qui sont déclenchés par [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="b5a4c-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>
<span data-ttu-id="b5a4c-104">Avec cette applet de commande, les utilisateurs peuvent inscrire une action à exécuter quand un fichier est créé dans un répertoire spécifique.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span>
<span data-ttu-id="b5a4c-105">Cet exemple dérive le [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe de base.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-105">This sample derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="b5a4c-106">Guide pratique pour générer l’exemple à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="b5a4c-107">Avec le Windows SDK PowerShell 2.0 installé, accédez au dossier Events01.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span>
   <span data-ttu-id="b5a4c-108">L’emplacement par défaut est `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-108">The default location is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span></span>

2. <span data-ttu-id="b5a4c-109">Double-cliquez sur l’icône pour le fichier solution (.sln).</span><span class="sxs-lookup"><span data-stu-id="b5a4c-109">Double-click the icon for the solution (.sln) file.</span></span>
   <span data-ttu-id="b5a4c-110">L’exemple de projet s’ouvre dans Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="b5a4c-111">Dans le **Build** menu, sélectionnez **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-111">In the **Build** menu, select **Build Solution**.</span></span>
   <span data-ttu-id="b5a4c-112">La bibliothèque de l’exemple est générée dans la valeur par défaut `\bin` ou `\bin\debug` dossiers.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-112">The library for the sample will be built in the default `\bin` or `\bin\debug` folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="b5a4c-113">Comment exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="b5a4c-113">How to run the sample</span></span>

1. <span data-ttu-id="b5a4c-114">Créez le dossier de module suivant :</span><span class="sxs-lookup"><span data-stu-id="b5a4c-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="b5a4c-115">Copiez le fichier de bibliothèque pour l’exemple dans le dossier de module.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="b5a4c-116">Démarrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="b5a4c-117">Exécutez la commande suivante pour charger l’applet de commande dans Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="b5a4c-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="b5a4c-118">Utilisez l’applet de commande Register-FileSystemEvent pour inscrire une action qui écrit un message quand un fichier est créé sous le répertoire TEMP.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="b5a4c-119">Créez un fichier sous le répertoire TEMP et notez que l’action est exécutée (le message est affiché).</span><span class="sxs-lookup"><span data-stu-id="b5a4c-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="b5a4c-120">Il s’agit d’un exemple de sortie qui résulte en suivant ces étapes.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="b5a4c-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b5a4c-121">Requirements</span></span>

<span data-ttu-id="b5a4c-122">Cet exemple requiert Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b5a4c-123">Montre</span><span class="sxs-lookup"><span data-stu-id="b5a4c-123">Demonstrates</span></span>

<span data-ttu-id="b5a4c-124">Cet exemple montre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-124">This sample demonstrates the following.</span></span>

### <a name="how-to-write-a-cmdlet-for-event-registration"></a><span data-ttu-id="b5a4c-125">Comment écrire une applet de commande d’inscription d’événement</span><span class="sxs-lookup"><span data-stu-id="b5a4c-125">How to write a cmdlet for event registration</span></span>

<span data-ttu-id="b5a4c-126">L’applet de commande dérive le [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) (classe), qui fournit la prise en charge pour les paramètres communs à la `Register-*Event` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the `Register-*Event` cmdlets.</span></span>
<span data-ttu-id="b5a4c-127">Applets de commande qui sont dérivés de [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) suffit de définir leurs paramètres particuliers et d’ignorer le `GetSourceObject` et `GetSourceObjectEventName` méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="b5a4c-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="b5a4c-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5a4c-128">Example</span></span>

<span data-ttu-id="b5a4c-129">Cet exemple montre comment s’inscrire aux événements déclenchés par [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="b5a4c-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="b5a4c-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5a4c-130">See Also</span></span>

[<span data-ttu-id="b5a4c-131">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5a4c-131">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)