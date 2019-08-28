---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Audit et création de rapports sur JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017790"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="0d697-103">Audit et création de rapports sur JEA</span><span class="sxs-lookup"><span data-stu-id="0d697-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="0d697-104">Une fois que vous avez déployé JEA, vous devez auditer régulièrement la configuration JEA.</span><span class="sxs-lookup"><span data-stu-id="0d697-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="0d697-105">L’audit vous aide à évaluer si les personnes adéquates ont accès au point de terminaison JEA et si leurs rôles sont toujours appropriés.</span><span class="sxs-lookup"><span data-stu-id="0d697-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="0d697-106">Rechercher des sessions JEA inscrites sur une machine</span><span class="sxs-lookup"><span data-stu-id="0d697-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="0d697-107">Pour vérifier les sessions JEA inscrites sur une machine, utilisez l’applet de commande [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="0d697-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="0d697-108">Les droits effectifs pour le point de terminaison sont listés dans la propriété **Permission**.</span><span class="sxs-lookup"><span data-stu-id="0d697-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="0d697-109">Ces utilisateurs ont le droit de se connecter au point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="0d697-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="0d697-110">Cependant, les rôles et les commandes auxquels ils ont accès sont déterminés par la propriété **RoleDefinitions** dans le [fichier de configuration de session](session-configurations.md) qui a été utilisé pour inscrire le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0d697-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="0d697-111">Développez la propriété **RoleDefinitions** pour évaluer les correspondances de rôles dans un point de terminaison JEA inscrit.</span><span class="sxs-lookup"><span data-stu-id="0d697-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="0d697-112">Trouver des fonctionnalités de rôle disponibles sur la machine</span><span class="sxs-lookup"><span data-stu-id="0d697-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="0d697-113">JEA obtient les capacités de rôle auprès des fichiers `.psrc` stockés dans le dossier **RoleCapabilities** au sein d’un module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d697-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="0d697-114">La fonction suivante recherche toutes les capacités de rôle disponibles sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0d697-114">The following function finds all role capabilities available on a computer.</span></span>

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="0d697-115">L’ordre des résultats de cette fonction n’est pas nécessairement l’ordre dans lequel les fonctionnalités de rôle sont sélectionnées si plusieurs fonctionnalités des rôles partagent le même nom.</span><span class="sxs-lookup"><span data-stu-id="0d697-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="0d697-116">Vérifiez les droits effectifs pour un utilisateur spécifique</span><span class="sxs-lookup"><span data-stu-id="0d697-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="0d697-117">L’applet de commande [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) énumère toutes les commandes disponibles sur un point de terminaison JEA en fonction des appartenances aux groupes d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0d697-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="0d697-118">La sortie de `Get-PSSessionCapability` est identique à celle de l’utilisateur spécifié exécutant `Get-Command -CommandType All` dans une session JEA.</span><span class="sxs-lookup"><span data-stu-id="0d697-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="0d697-119">Si vos utilisateurs ne sont pas des membres permanents de groupes qui leur accordent des droits JEA supplémentaires, cette applet de commande peut ne pas refléter ces autres autorisations.</span><span class="sxs-lookup"><span data-stu-id="0d697-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="0d697-120">Ceci se produit lors de l’utilisation de systèmes de gestion à accès privilégié de type juste-à-temps pour permettre aux utilisateurs d’appartenir temporairement à un groupe de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0d697-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="0d697-121">Évaluez soigneusement la mise en correspondance des utilisateurs aux rôles et aux capacités pour garantir que les utilisateurs obtiennent seulement le niveau d’accès nécessaire pour faire leur travail.</span><span class="sxs-lookup"><span data-stu-id="0d697-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="0d697-122">Journaux des événements PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d697-122">PowerShell event logs</span></span>

<span data-ttu-id="0d697-123">Si vous avez activé la journalisation de module ou de bloc de script sur le système, vous pouvez voir des événements dans les journaux des événements Windows pour chaque commande exécutée par un utilisateur dans une session JEA.</span><span class="sxs-lookup"><span data-stu-id="0d697-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="0d697-124">Pour trouver ces événements, ouvrez le journal des événements **Microsoft-Windows-PowerShell/Operational** et recherchez des événements avec l’ID **4104**.</span><span class="sxs-lookup"><span data-stu-id="0d697-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="0d697-125">Chaque entrée du journal des événements comprend des informations sur la session dans laquelle la commande a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="0d697-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="0d697-126">Pour les sessions JEA, l’événement contient des informations sur **ConnectedUser** et **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="0d697-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="0d697-127">**ConnectedUser** est l’utilisateur réel qui a créé la session JEA.</span><span class="sxs-lookup"><span data-stu-id="0d697-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="0d697-128">**RunAsUser** est le compte JEA utilisé pour exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="0d697-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="0d697-129">Les journaux des événements d’applications montrent les changements effectués par **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="0d697-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="0d697-130">L’activation de la journalisation des modules et des scripts est donc nécessaire pour retracer l’appel d’une commande spécifique jusqu’à **ConnectedUser**.</span><span class="sxs-lookup"><span data-stu-id="0d697-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="0d697-131">Journaux des événements de l’application</span><span class="sxs-lookup"><span data-stu-id="0d697-131">Application event logs</span></span>

<span data-ttu-id="0d697-132">Les commandes exécutées dans une session JEA qui interagissent avec des applications ou des services externes peuvent consigner des événements dans leurs propres journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="0d697-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="0d697-133">Contrairement aux journaux et aux transcriptions PowerShell, les autres mécanismes de journalisation ne capturent pas l’utilisateur connecté de la session JEA.</span><span class="sxs-lookup"><span data-stu-id="0d697-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="0d697-134">Au lieu de cela, ces applications consignent seulement l’utilisateur d’identification virtuel.</span><span class="sxs-lookup"><span data-stu-id="0d697-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="0d697-135">Pour déterminer qui a exécuté la commande, vous devez consulter une [transcription de session](#session-transcripts), ou mettre en corrélation des journaux des événements de PowerShell avec le moment et l’utilisateur indiqués dans le journal des événements d’une application.</span><span class="sxs-lookup"><span data-stu-id="0d697-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="0d697-136">Le journal WinRM peut également vous aider à mettre en corrélation les utilisateurs d’identification avec l’utilisateur qui se connecte dans un journal des événements d’une application.</span><span class="sxs-lookup"><span data-stu-id="0d697-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="0d697-137">L’ID d’événement **193** dans le journal **Microsoft-Windows-Windows Remote Management/Operational** enregistre l’identificateur de sécurité (SID) et le nom du compte de l’utilisateur d’identification et de l’utilisateur qui se connecte pour chaque nouvelle session JEA.</span><span class="sxs-lookup"><span data-stu-id="0d697-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="0d697-138">Transcription de sessions</span><span class="sxs-lookup"><span data-stu-id="0d697-138">Session transcripts</span></span>

<span data-ttu-id="0d697-139">Si vous avez configuré JEA pour créer une transcription pour chaque session utilisateur, une copie texte des actions de chaque utilisateur est stockée dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="0d697-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="0d697-140">La commande suivante (exécutée en tant qu’administrateur) trouve tous les répertoires de transcription.</span><span class="sxs-lookup"><span data-stu-id="0d697-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="0d697-141">Chaque transcription démarre avec des informations sur l’heure de début de la session, l’heure de la connexion de l’utilisateur à la session, et l’identité JEA qui lui a été attribuée.</span><span class="sxs-lookup"><span data-stu-id="0d697-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="0d697-142">Le corps de la transcription contient des informations sur chaque commande que l’utilisateur a appelée.</span><span class="sxs-lookup"><span data-stu-id="0d697-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="0d697-143">La syntaxe exacte de la commande utilisée n’est pas disponible dans les sessions JEA en raison de la façon dont les commandes sont transformées pour la communication à distance de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d697-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="0d697-144">Cependant, vous pouvez toujours déterminer la commande effective qui a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="0d697-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="0d697-145">Voici un exemple d’extrait de code de transcription d’un utilisateur exécutant `Get-Service Dns` dans une session JEA :</span><span class="sxs-lookup"><span data-stu-id="0d697-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="0d697-146">Une ligne **CommandInvocation** est écrite pour chaque commande exécutée par un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0d697-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="0d697-147">**ParameterBindings** enregistre chaque paramètre et chaque valeur fournis avec la commande.</span><span class="sxs-lookup"><span data-stu-id="0d697-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="0d697-148">Dans l’exemple précédent, vous pouvez voir que le paramètre **Name** a été fourni avec la valeur **Dns** pour l’applet de commande `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="0d697-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="0d697-149">Le résultat de chaque commande déclenche également une **CommandInvocation**, généralement pour `Out-Default`.</span><span class="sxs-lookup"><span data-stu-id="0d697-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="0d697-150">Le **InputObject** de `Out-Default` est l’objet PowerShell retourné par la commande.</span><span class="sxs-lookup"><span data-stu-id="0d697-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="0d697-151">Les détails de cet objet sont indiqués ci-dessous. Ils imitent étroitement ce que l’utilisateur a pu observer.</span><span class="sxs-lookup"><span data-stu-id="0d697-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d697-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d697-152">See also</span></span>

[<span data-ttu-id="0d697-153">*PowerShell ♥ the Blue Team*, billet de blog sur la sécurité</span><span class="sxs-lookup"><span data-stu-id="0d697-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
