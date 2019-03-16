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
ms.openlocfilehash: c9963819f1842d1245735dabc487babaa566c160
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057159"
---
# <a name="events01-sample"></a>Exemple Events01

Cet exemple montre comment créer une applet de commande qui permet à l’utilisateur enregistrer les événements qui sont déclenchés par [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Avec cette applet de commande, les utilisateurs peuvent inscrire une action à exécuter quand un fichier est créé dans un répertoire spécifique. Cet exemple dérive le [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe de base.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Guide pratique pour générer l’exemple à l’aide de Visual Studio.

1. Avec le Windows SDK PowerShell 2.0 installé, accédez au dossier Events01. L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.

2. Double-cliquez sur l’icône pour le fichier solution (.sln). L’exemple de projet s’ouvre dans Microsoft Visual Studio.

3. Dans le **Build** menu, sélectionnez **générer la Solution**.

    La bibliothèque de l’exemple est générée dans les dossiers \bin ou \bin\debug par défaut.

### <a name="how-to-run-the-sample"></a>Comment exécuter l’exemple

1. Créez le dossier de module suivant :

    `[user]/documents/windowspowershell/modules/events01`

2. Copiez le fichier de bibliothèque pour l’exemple dans le dossier de module.

3. Démarrez Windows PowerShell.

4. Exécutez la commande suivante pour charger l’applet de commande dans Windows PowerShell :

    ```powershell
    import-module events01
    ```

5. Utilisez l’applet de commande Register-FileSystemEvent pour inscrire une action qui écrit un message quand un fichier est créé sous le répertoire TEMP.

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. Créez un fichier sous le répertoire TEMP et notez que l’action est exécutée (le message est affiché).

Il s’agit d’un exemple de sortie qui résulte en suivant ces étapes.

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

## <a name="requirements"></a>Spécifications

Cet exemple requiert Windows PowerShell 2.0.

## <a name="demonstrates"></a>Montre

Cet exemple montre ce qui suit.

- Comment écrire une applet de commande d’inscription d’événement. Dérive de l’applet de commande le [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe, qui fournit la prise en charge pour les paramètres communs à Register-* événement applets de commande. Applets de commande qui sont dérivés de [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) suffit de définir leurs paramètres particuliers et d’ignorer le `GetSourceObject` et `GetSourceObjectEventName` méthodes abstraites.

## <a name="example"></a>Exemple

Cet exemple montre comment s’inscrire aux événements déclenchés par [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).

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

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)