---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Utilisation de JEA
description: Cet article décrit les différentes façons de se connecter et d’utiliser un point de terminaison JEA.
ms.openlocfilehash: b3d81cc0aa76549c81136e5a1a5af28df9c6fa7a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501539"
---
# <a name="using-jea"></a>Utilisation de JEA

Cet article décrit les différentes façons de se connecter et d’utiliser un point de terminaison JEA.

## <a name="using-jea-interactively"></a>Utiliser JEA de façon interactive

Si vous testez votre configuration JEA ou que vous avez des tâches simples pour les utilisateurs, vous pouvez utiliser JEA de la même façon qu’une session de communication à distance PowerShell standard. Pour les tâches complexes de communication à distance, il est recommandé d’utiliser la [communication à distance implicite](#using-jea-with-implicit-remoting). La communication à distance implicite permet aux utilisateurs de manipuler les objets de données localement.

Pour utiliser JEA de façon interactive, vous avez besoin des éléments suivants :

- Le nom de l’ordinateur auquel vous vous connectez (ce peut être la machine locale)
- le nom du point de terminaison JEA enregistré sur l’ordinateur ;
- Les informations d’identification ayant accès au point de terminaison JEA sur cet ordinateur

Avec ces informations, vous pouvez démarrer une session JEA avec les applets de commande [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) ou [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Si le compte d’utilisateur actuel a accès au point de terminaison JEA, vous pouvez omettre le paramètre **Credential**.

Quand l’invite PowerShell se change en `[localhost]: PS>`, vous savez que vous interagissez maintenant avec la session JEA à distance. Vous pouvez exécuter `Get-Command` pour connaître les commandes disponibles. Consultez votre administrateur pour savoir s’il existe des restrictions sur les paramètres disponibles ou des valeurs autorisées pour les paramètres.

Rappelez-vous que les sessions JEA fonctionnent en mode NoLanguage. Certains éléments de PowerShell que vous utilisez généralement peuvent ne pas être disponibles. Par exemple, vous ne pouvez pas utiliser des variables pour stocker des données ou inspecter les propriétés sur des objets retournés par des applets de commande. L’exemple suivant montre deux approches pour obtenir que les mêmes commandes fonctionnent en mode NoLanguage.

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

Pour les appels de commandes plus complexes qui rendent cette approche difficile, envisagez d’utiliser la [communication à distance implicite](#using-jea-with-implicit-remoting) ou de [créer des fonctions personnalisées](role-capabilities.md#creating-custom-functions) qui wrappent la fonctionnalité souhaitée.

## <a name="using-jea-with-implicit-remoting"></a>Utiliser JEA avec la communication à distance implicite

PowerShell a un modèle de communication à distance implicite qui vous permet d’importer les applets de commande de proxy à partir d’une machine distante et d’interagir avec elles comme s’il s’agissait de commandes locales. La communication à distance implicite est expliquée dans **Hey, Scripting Guy!** (un [billet de blog](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/)).
La communication à distance implicite est pratique quand vous travaillez avec JEA, car elle permet de travailler avec des applets de commande JEA en mode langage complet. Vous pouvez utiliser la complétion par tabulation et des variables, manipuler des objets, et même utiliser des scripts locaux pour automatiser des tâches sur un point de terminaison JEA. Chaque fois que vous appelez une commande de proxy, les données sont envoyées au point de terminaison JEA et exécutées sur la machine distante.

La communication à distance implicite fonctionne en important des applets de commande à partir d’une session PowerShell existante. Vous pouvez aussi choisir de faire préfixer le nom de chaque applet de commande de proxy par une chaîne de votre choix. Le préfixe vous permet de distinguer les commandes qui sont destinées au système distant. Un module de script temporaire contenant toutes les commandes de proxy est créé et est importé pour toute la durée de votre session PowerShell locale.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Tous les systèmes ne peuvent pas importer la totalité d’une session JEA en raison de contraintes pesant sur les applets de commande JEA par défaut. Pour contourner ce problème, importez uniquement les commandes dont vous avez besoin à partir de la session JEA en fournissant explicitement leur nom au paramètre `-CommandName`. Une mise à jour ultérieure résoudra le problème d’importation de la totalité d’une session JEA sur les systèmes concernés.

Si vous ne pouvez pas importer une session JEA en raison de contraintes sur les paramètres JEA par défaut, suivez les étapes ci-dessous pour éliminer les commandes par défaut de l’ensemble importé. Vous pouvez continuer d’utiliser des commandes comme `Select-Object`, mais vous utiliserez seulement la version locale installée sur votre ordinateur au lieu de la version importée depuis la session JEA distante.

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

Vous pouvez également conserver les applets de commande en proxy de la communication à distance implicite avec [Export-PSSession](/powershell/module/microsoft.powershell.utility/Export-PSSession).
Pour plus d’informations sur la communication à distance implicite, consultez la documentation pour [Import-PSSession](/powershell/module/microsoft.powershell.utility/import-pssession) et [Import-Module](/powershell/module/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>Utiliser JEA par programmation

JEA peut également être utilisé dans les systèmes d’automatisation et dans les applications utilisateurs, comme les sites web et les applications de support technique internes. L’approche est la même que celle utilisée pour créer des applications qui communiquent avec des points de terminaison PowerShell sans contrainte. Vérifiez que le programme est conçu pour fonctionner avec la limitation imposée par JEA.

Pour les tâches simples et ponctuelles, vous pouvez utiliser [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) pour exécuter des commandes dans une session JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Pour connaître les commandes disponibles lorsque vous vous connectez à une session JEA, exécutez `Get-Command` et effectuer une itération dans les résultats pour vérifier les paramètres autorisés.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Si vous créez une application C#, vous pouvez créer une instance d’exécution PowerShell qui se connecte à une session JEA en spécifiant le nom de la configuration dans un objet [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo).

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),
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

Hyper-V dans Windows 10 et Windows Server 2016 offre [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), fonctionnalité qui permet aux administrateurs Hyper-V de gérer des machines virtuelles avec PowerShell, indépendamment de la configuration réseau ou des paramètres de gestion à distance sur la machine virtuelle.

Vous pouvez utiliser PowerShell Direct avec JEA pour donner à un administrateur Hyper-V un accès limité à votre machine virtuelle.
Ce peut être utile si vous perdez la connectivité réseau à votre machine virtuelle et que vous avez besoin qu’un administrateur du centre de données corrige les paramètres réseau.

Aucune configuration supplémentaire n’est nécessaire pour utiliser JEA sur PowerShell Direct. Cependant, le système d’exploitation invité s’exécutant dans la machine virtuelle doit être Windows 10, Windows Server 2016 ou une version ultérieure. L’administrateur Hyper-V peut se connecter au point de terminaison JEA en utilisant le paramètre `-VMName` ou `-VMId` sur les applets de commande PSRemoting :

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Il est recommandé de créer un compte d’utilisateur dédié avec les droits minimaux nécessaires pour gérer le système pour une utilisation par un administrateur Hyper-V. Rappelez-vous que même un utilisateur sans privilèges peut se connecter à une machine Windows par défaut, notamment avec PowerShell sans contraintes. Ceci lui permet de parcourir le système de fichiers et de découvrir plus d’informations sur l’environnement de votre système d’exploitation. Pour bloquer un administrateur Hyper-V et lui permettre d’accéder à une machine virtuelle seulement via PowerShell Direct avec JEA, vous devez refuser les droits d’ouverture de session locale au compte JEA de l’administrateur Hyper-V.
