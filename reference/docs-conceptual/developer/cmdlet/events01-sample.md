---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple Events01
description: Exemple Events01
ms.openlocfilehash: ed8b7903537504609602e27693351847d322f904
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "94390403"
---
# <a name="events01-sample"></a><span data-ttu-id="3376d-103">Exemple Events01</span><span class="sxs-lookup"><span data-stu-id="3376d-103">Events01 Sample</span></span>

<span data-ttu-id="3376d-104">Cet exemple montre comment créer une applet de commande qui permet à l’utilisateur de s’inscrire aux événements déclenchés par [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="3376d-104">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="3376d-105">Avec cette applet de commande, les utilisateurs peuvent inscrire une action à exécuter lorsqu’un fichier est créé dans un répertoire spécifique.</span><span class="sxs-lookup"><span data-stu-id="3376d-105">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="3376d-106">Cet exemple dérive de la classe de base [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .</span><span class="sxs-lookup"><span data-stu-id="3376d-106">This sample derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="3376d-107">Comment générer l’exemple à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3376d-107">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="3376d-108">Une fois le kit de développement logiciel (SDK) 2,0 Windows PowerShell installé, accédez au dossier Events01.</span><span class="sxs-lookup"><span data-stu-id="3376d-108">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span> <span data-ttu-id="3376d-109">L’emplacement par défaut est `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span><span class="sxs-lookup"><span data-stu-id="3376d-109">The default location is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span></span>

2. <span data-ttu-id="3376d-110">Double-cliquez sur l’icône du fichier solution (. sln).</span><span class="sxs-lookup"><span data-stu-id="3376d-110">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="3376d-111">L’exemple de projet s’ouvre dans Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3376d-111">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="3376d-112">Dans le menu **Générer**, sélectionnez **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="3376d-112">In the **Build** menu, select **Build Solution**.</span></span> <span data-ttu-id="3376d-113">La bibliothèque de l’exemple sera générée dans les `\bin` dossiers ou par défaut `\bin\debug` .</span><span class="sxs-lookup"><span data-stu-id="3376d-113">The library for the sample will be built in the default `\bin` or `\bin\debug` folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="3376d-114">Comment exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="3376d-114">How to run the sample</span></span>

1. <span data-ttu-id="3376d-115">Créez le dossier de module suivant :</span><span class="sxs-lookup"><span data-stu-id="3376d-115">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="3376d-116">Copiez le fichier de bibliothèque de l’exemple dans le dossier du module.</span><span class="sxs-lookup"><span data-stu-id="3376d-116">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="3376d-117">Démarrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3376d-117">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="3376d-118">Exécutez la commande suivante pour charger l’applet de commande dans Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="3376d-118">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="3376d-119">Utilisez l’applet de commande Register-FileSystemEvent pour inscrire une action qui écrira un message lorsqu’un fichier est créé sous le répertoire TEMP.</span><span class="sxs-lookup"><span data-stu-id="3376d-119">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="3376d-120">Créez un fichier sous le répertoire temporaire et notez que l’action est exécutée (le message est affiché).</span><span class="sxs-lookup"><span data-stu-id="3376d-120">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="3376d-121">Voici un exemple de sortie résultant de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="3376d-121">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="3376d-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3376d-122">Requirements</span></span>

<span data-ttu-id="3376d-123">Cet exemple requiert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="3376d-123">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3376d-124">Illustre le</span><span class="sxs-lookup"><span data-stu-id="3376d-124">Demonstrates</span></span>

<span data-ttu-id="3376d-125">Cet exemple illustre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="3376d-125">This sample demonstrates the following.</span></span>

### <a name="how-to-write-a-cmdlet-for-event-registration"></a><span data-ttu-id="3376d-126">Comment écrire une applet de commande pour l’inscription des événements</span><span class="sxs-lookup"><span data-stu-id="3376d-126">How to write a cmdlet for event registration</span></span>

<span data-ttu-id="3376d-127">L’applet de commande dérive de la classe [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) , qui fournit la prise en charge des paramètres communs aux `Register-*Event` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3376d-127">The cmdlet derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the `Register-*Event` cmdlets.</span></span> <span data-ttu-id="3376d-128">Les applets de commande dérivées de [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) ont uniquement besoin de définir leurs paramètres particuliers et de substituer les `GetSourceObject` `GetSourceObjectEventName` méthodes abstraites et.</span><span class="sxs-lookup"><span data-stu-id="3376d-128">Cmdlets that are derived from [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="3376d-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="3376d-129">Example</span></span>

<span data-ttu-id="3376d-130">Cet exemple montre comment inscrire pour les événements déclenchés par [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="3376d-130">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>

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
        /// Deleted, Disposed, Error, and Renamed. Check the documentation of
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

## <a name="see-also"></a><span data-ttu-id="3376d-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3376d-131">See Also</span></span>

[<span data-ttu-id="3376d-132">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3376d-132">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
