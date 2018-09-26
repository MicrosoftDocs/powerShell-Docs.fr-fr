---
ms.date: 06/12/2017
keywords: jea,powershell,sécurité
title: Utilisation de JEA
ms.openlocfilehash: 539d280aff0b2656a5e9c710acfa468057753027
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522988"
---
# <a name="using-jea"></a>Utilisation de JEA

> S’applique à : Windows PowerShell 5.0

Cette rubrique décrit les différentes manières de se connecter à et d’utiliser un point de terminaison JEA.

## <a name="using-jea-interactively"></a>Utiliser JEA de façon interactive

Si vous testez votre configuration JEA ou que vous souhaitez donner aux utilisateurs des tâches simples à effectuer, vous pouvez utiliser JEA de la même façon qu’une session de communication à distance PowerShell standard.
Pour les tâches complexes de communication à distance, il est recommandé d’utiliser plutôt la [communication à distance implicite](#using-jea-with-implicit-remoting) afin de faciliter la tâche à vos utilisateurs en leur permettant de travailler localement avec les objets de données.

Pour utiliser JEA de manière interactive, vous aurez besoin des éléments suivants :
- le nom de l’ordinateur auquel vous vous connectez (potentiellement l’ordinateur local) ;
- le nom du point de terminaison JEA enregistré sur l’ordinateur ;
- les informations d’identification de l’ordinateur ayant accès au point de terminaison JEA.

Une fois que vous disposez de ces informations, vous pouvez lancer une session JEA avec [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) ou [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Si le compte auquel vous êtes actuellement connecté a accès au point de terminaison JEA, vous pouvez omettre le paramètre `-Credential`.

Lorsque l’invite PowerShell passe à `[localhost]: PS>`, cela indique que interagissez maintenant avec la session JEA à distance.
Vous pouvez exécuter `Get-Command` pour connaître les commandes disponibles.
Vous devez consulter votre administrateur pour savoir s’il existe des restrictions sur les paramètres disponibles ou des valeurs admissibles pour les paramètres.

Pour rappel, les sessions JEA fonctionnent en mode NoLanguage ; il est donc possible que certains modes d’utilisation de PowerShell ne soient pas disponibles.
Par exemple, vous ne pouvez pas utiliser des variables pour stocker des données ou inspecter les propriétés sur des objets retournés par des applets de commande.
L’exemple ci-dessous illustre une utilisation possible de PowerShell en l’état actuel des choses, et deux approches permettant de faire fonctionner la même commande en mode NoLanguage.

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

Pour les appels de commandes plus complexes qui rendent cette approche plus difficile, envisagez d’utiliser la [communication à distance implicite](#using-jea-with-implicit-remoting) ou de [créer des fonctions personnalisées](role-capabilities.md#creating-custom-functions) qui incluent la fonctionnalité souhaitée dans un wrapper.

## <a name="using-jea-with-implicit-remoting"></a>Utiliser JEA avec la communication à distance implicite

PowerShell prend en charge un autre modèle de communication à distance : vous pouvez importer les applets de commande de proxy à partir d’une machine distante sur votre ordinateur local et interagir avec elles comme s’il s’agissait de commandes locales.
Ce modèle, appelé communication à distance implicite, est expliqué dans [cet article de blog *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).
La communication à distance implicite est particulièrement utile lorsque vous travaillez avec JEA, car elle permet de travailler avec des applets de commande JEA en mode langage complet.
Cela signifie que vous pouvez utiliser la saisie semi-automatique par tabulation et les variables, manipuler des objets et même utiliser des scripts locaux afin de faciliter l’automatisation sur un point de terminaison JEA.
Chaque fois que vous appelez une commande de proxy, les données sont envoyées au point de terminaison JEA et exécutées sur l’ordinateur distant.

La communication à distance implicite fonctionne en important des applets de commande à partir d’une session PowerShell existante.
Vous pouvez éventuellement choisir de faire précéder le nom de chaque applet de commande du proxy par une chaîne de votre choix pour distinguer les commandes destinées au système distant.
Un module de script temporaire contenant toutes les commandes de proxy est créé et peut être utilisé pour toute la durée de votre session PowerShell locale.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Tous les systèmes ne peuvent pas importer la totalité d’une session JEA en raison de contraintes pesant sur les applets de commande JEA par défaut.
> Pour contourner ce problème, importez uniquement les commandes dont vous avez besoin à partir de la session JEA en fournissant explicitement leur nom au paramètre `-CommandName`.
> Une mise à jour ultérieure résoudra le problème d’importation de la totalité d’une session JEA sur les systèmes concernés.

Si vous ne pouvez pas importer une session JEA en raison de contraintes pesant sur les paramètres JEA par défaut, vous pouvez suivre les étapes ci-dessous pour éliminer les commandes par défaut de l’ensemble importé.
Vous pourrez toujours utiliser des commandes comme `Select-Object` : vous utiliserez seulement la version locale installée sur votre ordinateur plutôt que la version distante dans la session JEA.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

Vous pouvez également conserver les applets de commande en proxy de la communication à distance implicite avec [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Pour plus d’informations sur la communication à distance implicite, consultez la documentation d’aide de [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) et [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programatically"></a>Utiliser JEA par programmation

JEA peut également être utilisé dans les systèmes d’automatisation et dans les applications utilisateurs, comme les sites web et les applications de support technique internes.
L’approche est la même que pour créer des applications qui communiquent avec des points de terminaison PowerShell sans contraintes, mais il est à noter que JEA limite les commandes qui peuvent être exécutées dans la session à distance.

Pour les tâches simples et ponctuelles, vous pouvez utiliser [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) afin d’exécuter un ensemble de commandes avec JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Pour connaître les commandes disponibles lorsque vous vous connectez à une session JEA, exécutez `Get-Command` et effectuer une itération dans les résultats pour vérifier les paramètres autorisés.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Si vous créez une application C#, vous pouvez créer une instance d’exécution PowerShell qui se connecte à une session JEA en spécifiant le nom de la configuration dans un objet [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx).

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
                    creds);                // Credentials
// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a>Utiliser JEA avec PowerShell Direct

Hyper-V dans Windows 10 et Windows Server 2016 propose [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), une fonctionnalité qui permet aux administrateurs Hyper-V de gérer des machines virtuelles avec PowerShell, indépendamment de la configuration du réseau ou des paramètres de gestion à distance sur la machine virtuelle.

Vous pouvez utiliser PowerShell Direct avec JEA pour donner à un administrateur Hyper-V un accès limité à votre machine virtuelle, ce qui peut être utile si vous perdez la connectivité réseau à votre machine virtuelle et que vous avez besoin qu’un administrateur de centre de données corrige les paramètres réseau.

Aucune configuration supplémentaire n’est requise pour utiliser JEA par PowerShell Direct ; cependant, le système d’exploitation de la machine virtuelle doit être Windows 10 ou Windows Server 2016.
L’administrateur Hyper-V peut se connecter au point de terminaison JEA en utilisant le paramètre `-VMName` ou `-VMId` sur les applets de commande PSRemoting :

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Il est fortement recommandé de créer un utilisateur local dédié sans aucun autre droit de gestion du système, que les administrateurs Hyper-V pourront utiliser.
N’oubliez pas que même un utilisateur sans privilèges peut toujours se connecter à un ordinateur Windows par défaut, notamment à l’aide de PowerShell sans contraintes.
Cela lui permet de parcourir tout ou partie du système de fichiers et d’en savoir plus sur votre environnement de système d’exploitation.
Pour verrouiller un administrateur Hyper-V afin qu’il n’accède à une machine virtuelle que par le biais de PowerShell Direct avec JEA, vous devez refuser les droits d’ouverture de session locale au compte JEA de l’administrateur Hyper-V.