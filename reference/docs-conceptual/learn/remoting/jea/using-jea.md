---
ms.date: 07/10/2019
keywords: jea,powershell,sécurité
title: Utilisation de JEA
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017750"
---
# <a name="using-jea"></a><span data-ttu-id="9660c-103">Utilisation de JEA</span><span class="sxs-lookup"><span data-stu-id="9660c-103">Using JEA</span></span>

<span data-ttu-id="9660c-104">Cet article décrit les différentes façons de se connecter et d’utiliser un point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="9660c-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="9660c-105">Utiliser JEA de façon interactive</span><span class="sxs-lookup"><span data-stu-id="9660c-105">Using JEA interactively</span></span>

<span data-ttu-id="9660c-106">Si vous testez votre configuration JEA ou que vous avez des tâches simples pour les utilisateurs, vous pouvez utiliser JEA de la même façon qu’une session de communication à distance PowerShell standard.</span><span class="sxs-lookup"><span data-stu-id="9660c-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="9660c-107">Pour les tâches complexes de communication à distance, il est recommandé d’utiliser la [communication à distance implicite](#using-jea-with-implicit-remoting).</span><span class="sxs-lookup"><span data-stu-id="9660c-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="9660c-108">La communication à distance implicite permet aux utilisateurs de manipuler les objets de données localement.</span><span class="sxs-lookup"><span data-stu-id="9660c-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="9660c-109">Pour utiliser JEA de façon interactive, vous avez besoin des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9660c-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="9660c-110">Le nom de l’ordinateur auquel vous vous connectez (ce peut être la machine locale)</span><span class="sxs-lookup"><span data-stu-id="9660c-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="9660c-111">le nom du point de terminaison JEA enregistré sur l’ordinateur ;</span><span class="sxs-lookup"><span data-stu-id="9660c-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="9660c-112">Les informations d’identification ayant accès au point de terminaison JEA sur cet ordinateur</span><span class="sxs-lookup"><span data-stu-id="9660c-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="9660c-113">Avec ces informations, vous pouvez démarrer une session JEA avec les applets de commande [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) ou [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="9660c-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="9660c-114">Si le compte d’utilisateur actuel a accès au point de terminaison JEA, vous pouvez omettre le paramètre **Credential**.</span><span class="sxs-lookup"><span data-stu-id="9660c-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="9660c-115">Quand l’invite PowerShell se change en `[localhost]: PS>`, vous savez que vous interagissez maintenant avec la session JEA à distance.</span><span class="sxs-lookup"><span data-stu-id="9660c-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="9660c-116">Vous pouvez exécuter `Get-Command` pour connaître les commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="9660c-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="9660c-117">Consultez votre administrateur pour savoir s’il existe des restrictions sur les paramètres disponibles ou des valeurs autorisées pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="9660c-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="9660c-118">Rappelez-vous que les sessions JEA fonctionnent en mode NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="9660c-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="9660c-119">Certains éléments de PowerShell que vous utilisez généralement peuvent ne pas être disponibles.</span><span class="sxs-lookup"><span data-stu-id="9660c-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="9660c-120">Par exemple, vous ne pouvez pas utiliser des variables pour stocker des données ou inspecter les propriétés sur des objets retournés par des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="9660c-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="9660c-121">L’exemple suivant montre deux approches pour obtenir que les mêmes commandes fonctionnent en mode NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="9660c-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

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

<span data-ttu-id="9660c-122">Pour les appels de commandes plus complexes qui rendent cette approche difficile, envisagez d’utiliser la [communication à distance implicite](#using-jea-with-implicit-remoting) ou de [créer des fonctions personnalisées](role-capabilities.md#creating-custom-functions) qui wrappent la fonctionnalité souhaitée.</span><span class="sxs-lookup"><span data-stu-id="9660c-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="9660c-123">Utiliser JEA avec la communication à distance implicite</span><span class="sxs-lookup"><span data-stu-id="9660c-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="9660c-124">PowerShell a un modèle de communication à distance implicite qui vous permet d’importer les applets de commande de proxy à partir d’une machine distante et d’interagir avec elles comme s’il s’agissait de commandes locales.</span><span class="sxs-lookup"><span data-stu-id="9660c-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="9660c-125">La communication à distance implicite est expliquée dans **Hey, Scripting Guy!**</span><span class="sxs-lookup"><span data-stu-id="9660c-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="9660c-126">(un [billet de blog](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/)).</span><span class="sxs-lookup"><span data-stu-id="9660c-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="9660c-127">La communication à distance implicite est pratique quand vous travaillez avec JEA, car elle permet de travailler avec des applets de commande JEA en mode langage complet.</span><span class="sxs-lookup"><span data-stu-id="9660c-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="9660c-128">Vous pouvez utiliser la complétion par tabulation et des variables, manipuler des objets, et même utiliser des scripts locaux pour automatiser des tâches sur un point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="9660c-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="9660c-129">Chaque fois que vous appelez une commande de proxy, les données sont envoyées au point de terminaison JEA et exécutées sur la machine distante.</span><span class="sxs-lookup"><span data-stu-id="9660c-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="9660c-130">La communication à distance implicite fonctionne en important des applets de commande à partir d’une session PowerShell existante.</span><span class="sxs-lookup"><span data-stu-id="9660c-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="9660c-131">Vous pouvez aussi choisir de faire préfixer le nom de chaque applet de commande de proxy par une chaîne de votre choix.</span><span class="sxs-lookup"><span data-stu-id="9660c-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="9660c-132">Le préfixe vous permet de distinguer les commandes qui sont destinées au système distant.</span><span class="sxs-lookup"><span data-stu-id="9660c-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="9660c-133">Un module de script temporaire contenant toutes les commandes de proxy est créé et est importé pour toute la durée de votre session PowerShell locale.</span><span class="sxs-lookup"><span data-stu-id="9660c-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="9660c-134">Tous les systèmes ne peuvent pas importer la totalité d’une session JEA en raison de contraintes pesant sur les applets de commande JEA par défaut.</span><span class="sxs-lookup"><span data-stu-id="9660c-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="9660c-135">Pour contourner ce problème, importez uniquement les commandes dont vous avez besoin à partir de la session JEA en fournissant explicitement leur nom au paramètre `-CommandName`.</span><span class="sxs-lookup"><span data-stu-id="9660c-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="9660c-136">Une mise à jour ultérieure résoudra le problème d’importation de la totalité d’une session JEA sur les systèmes concernés.</span><span class="sxs-lookup"><span data-stu-id="9660c-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="9660c-137">Si vous ne pouvez pas importer une session JEA en raison de contraintes sur les paramètres JEA par défaut, suivez les étapes ci-dessous pour éliminer les commandes par défaut de l’ensemble importé.</span><span class="sxs-lookup"><span data-stu-id="9660c-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="9660c-138">Vous pouvez continuer d’utiliser des commandes comme `Select-Object`, mais vous utiliserez seulement la version locale installée sur votre ordinateur au lieu de la version importée depuis la session JEA distante.</span><span class="sxs-lookup"><span data-stu-id="9660c-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

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

<span data-ttu-id="9660c-139">Vous pouvez également conserver les applets de commande en proxy de la communication à distance implicite avec [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="9660c-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="9660c-140">Pour plus d’informations sur la communication à distance implicite, consultez la documentation pour [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) et [Import-Module](/powershell/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="9660c-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="9660c-141">Utiliser JEA par programmation</span><span class="sxs-lookup"><span data-stu-id="9660c-141">Using JEA programmatically</span></span>

<span data-ttu-id="9660c-142">JEA peut également être utilisé dans les systèmes d’automatisation et dans les applications utilisateurs, comme les sites web et les applications de support technique internes.</span><span class="sxs-lookup"><span data-stu-id="9660c-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="9660c-143">L’approche est la même que celle utilisée pour créer des applications qui communiquent avec des points de terminaison PowerShell sans contrainte.</span><span class="sxs-lookup"><span data-stu-id="9660c-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="9660c-144">Vérifiez que le programme est conçu pour fonctionner avec la limitation imposée par JEA.</span><span class="sxs-lookup"><span data-stu-id="9660c-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="9660c-145">Pour les tâches simples et ponctuelles, vous pouvez utiliser [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) pour exécuter des commandes dans une session JEA.</span><span class="sxs-lookup"><span data-stu-id="9660c-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="9660c-146">Pour connaître les commandes disponibles lorsque vous vous connectez à une session JEA, exécutez `Get-Command` et effectuer une itération dans les résultats pour vérifier les paramètres autorisés.</span><span class="sxs-lookup"><span data-stu-id="9660c-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="9660c-147">Si vous créez une application C#, vous pouvez créer une instance d’exécution PowerShell qui se connecte à une session JEA en spécifiant le nom de la configuration dans un objet [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo).</span><span class="sxs-lookup"><span data-stu-id="9660c-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="9660c-148">Utiliser JEA avec PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="9660c-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="9660c-149">Hyper-V dans Windows 10 et Windows Server 2016 offre [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), fonctionnalité qui permet aux administrateurs Hyper-V de gérer des machines virtuelles avec PowerShell, indépendamment de la configuration réseau ou des paramètres de gestion à distance sur la machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="9660c-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="9660c-150">Vous pouvez utiliser PowerShell Direct avec JEA pour donner à un administrateur Hyper-V un accès limité à votre machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="9660c-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="9660c-151">Ce peut être utile si vous perdez la connectivité réseau à votre machine virtuelle et que vous avez besoin qu’un administrateur du centre de données corrige les paramètres réseau.</span><span class="sxs-lookup"><span data-stu-id="9660c-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="9660c-152">Aucune configuration supplémentaire n’est nécessaire pour utiliser JEA sur PowerShell Direct.</span><span class="sxs-lookup"><span data-stu-id="9660c-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="9660c-153">Cependant, le système d’exploitation invité s’exécutant dans la machine virtuelle doit être Windows 10, Windows Server 2016 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9660c-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="9660c-154">L’administrateur Hyper-V peut se connecter au point de terminaison JEA en utilisant le paramètre `-VMName` ou `-VMId` sur les applets de commande PSRemoting :</span><span class="sxs-lookup"><span data-stu-id="9660c-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="9660c-155">Il est recommandé de créer un compte d’utilisateur dédié avec les droits minimaux nécessaires pour gérer le système pour une utilisation par un administrateur Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="9660c-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="9660c-156">Rappelez-vous que même un utilisateur sans privilèges peut se connecter à une machine Windows par défaut, notamment avec PowerShell sans contraintes.</span><span class="sxs-lookup"><span data-stu-id="9660c-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="9660c-157">Ceci lui permet de parcourir le système de fichiers et de découvrir plus d’informations sur l’environnement de votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="9660c-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="9660c-158">Pour bloquer un administrateur Hyper-V et lui permettre d’accéder à une machine virtuelle seulement via PowerShell Direct avec JEA, vous devez refuser les droits d’ouverture de session locale au compte JEA de l’administrateur Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="9660c-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
