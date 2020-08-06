---
title: Exemple Events01 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c7b0f759ca6f3c078649a462eac1713e8214a237
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774455"
---
# <a name="events01-sample"></a>Exemple Events01

Cet exemple montre comment créer une applet de commande qui permet à l’utilisateur de s’inscrire aux événements déclenchés par [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).
Avec cette applet de commande, les utilisateurs peuvent inscrire une action à exécuter lorsqu’un fichier est créé dans un répertoire spécifique.
Cet exemple dérive de la classe de base [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Comment générer l’exemple à l’aide de Visual Studio.

1. Une fois le kit de développement logiciel (SDK) 2,0 Windows PowerShell installé, accédez au dossier Events01.
   L’emplacement par défaut est `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.

2. Double-cliquez sur l’icône du fichier solution (. sln).
   L’exemple de projet s’ouvre dans Microsoft Visual Studio.

3. Dans le menu **Générer**, sélectionnez **Générer la solution**.
   La bibliothèque de l’exemple sera générée dans les `\bin` dossiers ou par défaut `\bin\debug` .

### <a name="how-to-run-the-sample"></a>Comment exécuter l’exemple

1. Créez le dossier de module suivant :

    `[user]/documents/windowspowershell/modules/events01`

2. Copiez le fichier de bibliothèque de l’exemple dans le dossier du module.

3. Démarrez Windows PowerShell.

4. Exécutez la commande suivante pour charger l’applet de commande dans Windows PowerShell :

    ```powershell
    import-module events01
    ```

5. Utilisez l’applet de commande Register-FileSystemEvent pour inscrire une action qui écrira un message quand un fichier est créé sous le répertoire TEMP.

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. Créez un fichier sous le répertoire temporaire et notez que l’action est exécutée (le message est affiché).

Voici un exemple de sortie résultant de cette procédure.

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

Cet exemple requiert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Illustre le

Cet exemple illustre ce qui suit.

### <a name="how-to-write-a-cmdlet-for-event-registration"></a>Comment écrire une applet de commande pour l’inscription des événements

L’applet de commande dérive de la classe [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) , qui fournit la prise en charge des paramètres communs aux `Register-*Event` cmdlets.
Les applets de commande dérivées de [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) ont uniquement besoin de définir leurs paramètres particuliers et de substituer les `GetSourceObject` `GetSourceObjectEventName` méthodes abstraites et.

## <a name="example"></a>Exemple

Cet exemple montre comment inscrire pour les événements déclenchés par [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).

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

[Écriture d’une applet de commande Windows PowerShell](writing-a-windows-powershell-cmdlet.md)
