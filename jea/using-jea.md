---
ms.date: 06/12/2017
keywords: jea,powershell,sécurité
title: Utilisation de JEA
ms.openlocfilehash: fa3d3a3c8bc0090ec9ad788585ec5df933134173
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054677"
---
# <a name="using-jea"></a><span data-ttu-id="71f0e-103">Utilisation de JEA</span><span class="sxs-lookup"><span data-stu-id="71f0e-103">Using JEA</span></span>

> <span data-ttu-id="71f0e-104">S'applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="71f0e-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="71f0e-105">Cette rubrique décrit les différentes manières de se connecter à et d’utiliser un point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="71f0e-105">This topic describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="71f0e-106">Utiliser JEA de façon interactive</span><span class="sxs-lookup"><span data-stu-id="71f0e-106">Using JEA interactively</span></span>

<span data-ttu-id="71f0e-107">Si vous testez votre configuration JEA ou que vous souhaitez donner aux utilisateurs des tâches simples à effectuer, vous pouvez utiliser JEA de la même façon qu’une session de communication à distance PowerShell standard.</span><span class="sxs-lookup"><span data-stu-id="71f0e-107">If you are testing your JEA configuration or have simple tasks for users to perform, you can use JEA the same way you would a regular PowerShell remoting session.</span></span>
<span data-ttu-id="71f0e-108">Pour les tâches complexes de communication à distance, il est recommandé d’utiliser plutôt la [communication à distance implicite](#using-jea-with-implicit-remoting) afin de faciliter la tâche à vos utilisateurs en leur permettant de travailler localement avec les objets de données.</span><span class="sxs-lookup"><span data-stu-id="71f0e-108">For complex remoting tasks, it is recommended to use [implicit remoting](#using-jea-with-implicit-remoting) instead to make it easier for your users by allowing users to operate with the data objects locally.</span></span>

<span data-ttu-id="71f0e-109">Pour utiliser JEA de manière interactive, vous aurez besoin des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="71f0e-109">To use JEA interactively, you will need:</span></span>
- <span data-ttu-id="71f0e-110">le nom de l’ordinateur auquel vous vous connectez (potentiellement l’ordinateur local) ;</span><span class="sxs-lookup"><span data-stu-id="71f0e-110">The name of the computer you are connecting to (can be the local machine)</span></span>
- <span data-ttu-id="71f0e-111">le nom du point de terminaison JEA enregistré sur l’ordinateur ;</span><span class="sxs-lookup"><span data-stu-id="71f0e-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="71f0e-112">les informations d’identification de l’ordinateur ayant accès au point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="71f0e-112">Credentials for the computer that have access to the JEA endpoint</span></span>

<span data-ttu-id="71f0e-113">Une fois que vous disposez de ces informations, vous pouvez lancer une session JEA avec [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) ou [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="71f0e-113">With that information in hand, you can start a JEA session using [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="71f0e-114">Si le compte auquel vous êtes actuellement connecté a accès au point de terminaison JEA, vous pouvez omettre le paramètre `-Credential`.</span><span class="sxs-lookup"><span data-stu-id="71f0e-114">If the account you're currently logged in as has access to the JEA endpoint, you can omit the `-Credential` parameter.</span></span>

<span data-ttu-id="71f0e-115">Lorsque l’invite PowerShell passe à `[localhost]: PS>`, cela indique que interagissez maintenant avec la session JEA à distance.</span><span class="sxs-lookup"><span data-stu-id="71f0e-115">When the PowerShell prompt changes to `[localhost]: PS>` you will know that you are now interacting with the remote JEA session.</span></span>
<span data-ttu-id="71f0e-116">Vous pouvez exécuter `Get-Command` pour connaître les commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="71f0e-116">You can run `Get-Command` to check which commands are available.</span></span>
<span data-ttu-id="71f0e-117">Vous devez consulter votre administrateur pour savoir s’il existe des restrictions sur les paramètres disponibles ou des valeurs admissibles pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="71f0e-117">You will need to consult with your administrator to learn if there are any restrictions on the available parameters or allowable parameter values.</span></span>

<span data-ttu-id="71f0e-118">Pour rappel, les sessions JEA fonctionnent en mode NoLanguage ; il est donc possible que certains modes d’utilisation de PowerShell ne soient pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="71f0e-118">As a reminder, JEA sessions operate in NoLanguage mode, so some of the ways you typically use PowerShell may not be available.</span></span>
<span data-ttu-id="71f0e-119">Par exemple, vous ne pouvez pas utiliser des variables pour stocker des données ou inspecter les propriétés sur des objets retournés par des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="71f0e-119">For instance, you cannot use variables to store data or inspect the properties on objects returned from cmdlets.</span></span>
<span data-ttu-id="71f0e-120">L’exemple ci-dessous illustre une utilisation possible de PowerShell en l’état actuel des choses, et deux approches permettant de faire fonctionner la même commande en mode NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="71f0e-120">The below example shows an example of how you may be using PowerShell today, and two approaches to get the same command working in NoLanguage mode.</span></span>

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

<span data-ttu-id="71f0e-121">Pour les appels de commandes plus complexes qui rendent cette approche plus difficile, envisagez d’utiliser la [communication à distance implicite](#using-jea-with-implicit-remoting) ou de [créer des fonctions personnalisées](role-capabilities.md#creating-custom-functions) qui incluent la fonctionnalité souhaitée dans un wrapper.</span><span class="sxs-lookup"><span data-stu-id="71f0e-121">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you desire.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="71f0e-122">Utiliser JEA avec la communication à distance implicite</span><span class="sxs-lookup"><span data-stu-id="71f0e-122">Using JEA with implicit remoting</span></span>

<span data-ttu-id="71f0e-123">PowerShell prend en charge un autre modèle de communication à distance : vous pouvez importer les applets de commande de proxy à partir d’une machine distante sur votre ordinateur local et interagir avec elles comme s’il s’agissait de commandes locales.</span><span class="sxs-lookup"><span data-stu-id="71f0e-123">PowerShell supports an alternative remoting model where you can import proxy cmdlets from a remote machine on your local computer and interact with them as if they were local commands.</span></span>
<span data-ttu-id="71f0e-124">Ce modèle, appelé communication à distance implicite, est expliqué dans [cet article de blog *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="71f0e-124">This is called implicit remoting, and is explained well in [this *Hey, Scripting Guy!* blog post](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="71f0e-125">La communication à distance implicite est particulièrement utile lorsque vous travaillez avec JEA, car elle permet de travailler avec des applets de commande JEA en mode langage complet.</span><span class="sxs-lookup"><span data-stu-id="71f0e-125">Implicit remoting is particularly useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span>
<span data-ttu-id="71f0e-126">Cela signifie que vous pouvez utiliser la saisie semi-automatique par tabulation et les variables, manipuler des objets et même utiliser des scripts locaux afin de faciliter l’automatisation sur un point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="71f0e-126">This means you can use tab completion, variables, manipulate objects, and even use local scripts to more easily automate against a JEA endpoint.</span></span>
<span data-ttu-id="71f0e-127">Chaque fois que vous appelez une commande de proxy, les données sont envoyées au point de terminaison JEA et exécutées sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="71f0e-127">Anytime you invoke a proxy command, the data will be sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="71f0e-128">La communication à distance implicite fonctionne en important des applets de commande à partir d’une session PowerShell existante.</span><span class="sxs-lookup"><span data-stu-id="71f0e-128">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span>
<span data-ttu-id="71f0e-129">Vous pouvez éventuellement choisir de faire précéder le nom de chaque applet de commande du proxy par une chaîne de votre choix pour distinguer les commandes destinées au système distant.</span><span class="sxs-lookup"><span data-stu-id="71f0e-129">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing to distinguish which commands are for the remote system.</span></span>
<span data-ttu-id="71f0e-130">Un module de script temporaire contenant toutes les commandes de proxy est créé et peut être utilisé pour toute la durée de votre session PowerShell locale.</span><span class="sxs-lookup"><span data-stu-id="71f0e-130">A temporary script module containing all of the proxy commands will be created and can be used for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="71f0e-131">Tous les systèmes ne peuvent pas importer la totalité d’une session JEA en raison de contraintes pesant sur les applets de commande JEA par défaut.</span><span class="sxs-lookup"><span data-stu-id="71f0e-131">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span>
> <span data-ttu-id="71f0e-132">Pour contourner ce problème, importez uniquement les commandes dont vous avez besoin à partir de la session JEA en fournissant explicitement leur nom au paramètre `-CommandName`.</span><span class="sxs-lookup"><span data-stu-id="71f0e-132">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span>
> <span data-ttu-id="71f0e-133">Une mise à jour ultérieure résoudra le problème d’importation de la totalité d’une session JEA sur les systèmes concernés.</span><span class="sxs-lookup"><span data-stu-id="71f0e-133">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="71f0e-134">Si vous ne pouvez pas importer une session JEA en raison de contraintes pesant sur les paramètres JEA par défaut, vous pouvez suivre les étapes ci-dessous pour éliminer les commandes par défaut de l’ensemble importé.</span><span class="sxs-lookup"><span data-stu-id="71f0e-134">If you are unable to import a JEA session due to constraints on the default JEA parameters, you can follow the steps below to filter out the default commands from the imported set.</span></span>
<span data-ttu-id="71f0e-135">Vous pourrez toujours utiliser des commandes comme `Select-Object` : vous utiliserez seulement la version locale installée sur votre ordinateur plutôt que la version distante dans la session JEA.</span><span class="sxs-lookup"><span data-stu-id="71f0e-135">You will still be able to use commands like `Select-Object` -- you'll just use the local version installed on your computer instead of the remote one in the JEA session.</span></span>

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

<span data-ttu-id="71f0e-136">Vous pouvez également conserver les applets de commande en proxy de la communication à distance implicite avec [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="71f0e-136">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="71f0e-137">Pour plus d’informations sur la communication à distance implicite, consultez la documentation d’aide de [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) et [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="71f0e-137">For more information about implicit remoting, check out the help documentation for [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) and [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="71f0e-138">Utiliser JEA par programmation</span><span class="sxs-lookup"><span data-stu-id="71f0e-138">Using JEA programmatically</span></span>

<span data-ttu-id="71f0e-139">JEA peut également être utilisé dans les systèmes d’automatisation et dans les applications utilisateurs, comme les sites web et les applications de support technique internes.</span><span class="sxs-lookup"><span data-stu-id="71f0e-139">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and web sites.</span></span>
<span data-ttu-id="71f0e-140">L’approche est la même que pour créer des applications qui communiquent avec des points de terminaison PowerShell sans contraintes, mais il est à noter que JEA limite les commandes qui peuvent être exécutées dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="71f0e-140">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints, with the caveat that the program should be aware that JEA is limiting the commands that can be run in the remote session.</span></span>

<span data-ttu-id="71f0e-141">Pour les tâches simples et ponctuelles, vous pouvez utiliser [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) afin d’exécuter un ensemble de commandes avec JEA.</span><span class="sxs-lookup"><span data-stu-id="71f0e-141">For simple, one-off tasks, you can use [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) to run a set of commands using JEA.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="71f0e-142">Pour connaître les commandes disponibles lorsque vous vous connectez à une session JEA, exécutez `Get-Command` et effectuer une itération dans les résultats pour vérifier les paramètres autorisés.</span><span class="sxs-lookup"><span data-stu-id="71f0e-142">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="71f0e-143">Si vous créez une application C#, vous pouvez créer une instance d’exécution PowerShell qui se connecte à une session JEA en spécifiant le nom de la configuration dans un objet [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="71f0e-143">If you are building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span></span>

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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="71f0e-144">Utiliser JEA avec PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="71f0e-144">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="71f0e-145">Hyper-V dans Windows 10 et Windows Server 2016 propose [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), une fonctionnalité qui permet aux administrateurs Hyper-V de gérer des machines virtuelles avec PowerShell, indépendamment de la configuration du réseau ou des paramètres de gestion à distance sur la machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="71f0e-145">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), a feature which allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="71f0e-146">Vous pouvez utiliser PowerShell Direct avec JEA pour donner à un administrateur Hyper-V un accès limité à votre machine virtuelle, ce qui peut être utile si vous perdez la connectivité réseau à votre machine virtuelle et que vous avez besoin qu’un administrateur de centre de données corrige les paramètres réseau.</span><span class="sxs-lookup"><span data-stu-id="71f0e-146">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM, which can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="71f0e-147">Aucune configuration supplémentaire n’est requise pour utiliser JEA par PowerShell Direct ; cependant, le système d’exploitation de la machine virtuelle doit être Windows 10 ou Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="71f0e-147">No additional configuration is required to use JEA over PowerShell Direct, however the operating system running inside the virtual machine must be Windows 10 or Windows Server 2016.</span></span>
<span data-ttu-id="71f0e-148">L’administrateur Hyper-V peut se connecter au point de terminaison JEA en utilisant le paramètre `-VMName` ou `-VMId` sur les applets de commande PSRemoting :</span><span class="sxs-lookup"><span data-stu-id="71f0e-148">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="71f0e-149">Il est fortement recommandé de créer un utilisateur local dédié sans aucun autre droit de gestion du système, que les administrateurs Hyper-V pourront utiliser.</span><span class="sxs-lookup"><span data-stu-id="71f0e-149">It is strongly recommended that you create a dedicated local user with no other rights to manage the system for your Hyper-V administrators to use.</span></span>
<span data-ttu-id="71f0e-150">N’oubliez pas que même un utilisateur sans privilèges peut toujours se connecter à un ordinateur Windows par défaut, notamment à l’aide de PowerShell sans contraintes.</span><span class="sxs-lookup"><span data-stu-id="71f0e-150">Remember that even an unprivileged user can still log into a Windows machine by default, including using unconstrained PowerShell.</span></span>
<span data-ttu-id="71f0e-151">Cela lui permet de parcourir tout ou partie du système de fichiers et d’en savoir plus sur votre environnement de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="71f0e-151">That will allow them to browse (some of) the file system and learn more about your OS environment.</span></span>
<span data-ttu-id="71f0e-152">Pour verrouiller un administrateur Hyper-V afin qu’il n’accède à une machine virtuelle que par le biais de PowerShell Direct avec JEA, vous devez refuser les droits d’ouverture de session locale au compte JEA de l’administrateur Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="71f0e-152">To lock down a Hyper-V administrator to only access a VM using PowerShell Direct with JEA, you will need to deny local logon rights to the Hyper-V admin's JEA account.</span></span>
