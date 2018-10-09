---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Audit et création de rapports sur JEA
ms.openlocfilehash: 2388c735840d8d3683aa8bc9869b9fb0371e5902
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851218"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="93351-103">Audit et création de rapports sur JEA</span><span class="sxs-lookup"><span data-stu-id="93351-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="93351-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="93351-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="93351-105">Une fois que vous avez déployé JEA, vous devez auditer régulièrement la configuration JEA.</span><span class="sxs-lookup"><span data-stu-id="93351-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="93351-106">Cela vous aide à évaluer si les personnes adéquates ont accès au point de terminaison JEA et si leurs rôles sont toujours appropriés.</span><span class="sxs-lookup"><span data-stu-id="93351-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="93351-107">Cette rubrique décrit les différentes manières d’auditer un point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="93351-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="93351-108">Rechercher des sessions JEA inscrites sur une machine</span><span class="sxs-lookup"><span data-stu-id="93351-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="93351-109">Pour vérifier les sessions JEA inscrites sur une machine, utilisez l’applet de commande [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="93351-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="93351-110">Les droits effectifs pour le point de terminaison sont répertoriés dans la propriété « Permission » (Autorisation).</span><span class="sxs-lookup"><span data-stu-id="93351-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="93351-111">Ces utilisateurs ont le droit de se connecter au point de terminaison JEA, mais les rôles (et, par extension, les commandes) auxquels ils ont accès sont déterminés par le champ « RoleDefinitions » dans le [fichier de configuration de session](session-configurations.md) qui a été utilisé pour inscrire le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="93351-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="93351-112">Vous pouvez évaluer les mappages de rôles dans un point de terminaison JEA inscrit en développant les données de la propriété « RoleDefinitions ».</span><span class="sxs-lookup"><span data-stu-id="93351-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="93351-113">Trouver des fonctionnalités de rôle disponibles sur la machine</span><span class="sxs-lookup"><span data-stu-id="93351-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="93351-114">Les fichiers de fonctionnalité de rôle sont uniquement utilisés par JEA s’ils sont stockés dans un dossier « RoleCapabilities » à l’intérieur d’un module PowerShell valide.</span><span class="sxs-lookup"><span data-stu-id="93351-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="93351-115">Vous pouvez trouver toutes les fonctionnalités de rôle disponibles sur un ordinateur en recherchant la liste des modules disponibles.</span><span class="sxs-lookup"><span data-stu-id="93351-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="93351-116">L’ordre des résultats de cette fonction n’est pas nécessairement l’ordre dans lequel les fonctionnalités de rôle sont sélectionnées si plusieurs fonctionnalités des rôles partagent le même nom.</span><span class="sxs-lookup"><span data-stu-id="93351-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="93351-117">Vérifiez les droits effectifs pour un utilisateur spécifique</span><span class="sxs-lookup"><span data-stu-id="93351-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="93351-118">Une fois que vous avez configuré un point de terminaison JEA, vous pourrez peut-être vérifier les commandes disponibles pour un utilisateur spécifique dans une session JEA.</span><span class="sxs-lookup"><span data-stu-id="93351-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="93351-119">Vous pouvez utiliser [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) pour énumérer toutes les commandes applicables à un utilisateur s’il s’agit de démarrer une session JEA avec leur appartenance à un groupe actuelle.</span><span class="sxs-lookup"><span data-stu-id="93351-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="93351-120">La sortie de `Get-PSSessionCapability` est identique à celle de l’utilisateur spécifié exécutant `Get-Command -CommandType All` dans une session JEA.</span><span class="sxs-lookup"><span data-stu-id="93351-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="93351-121">Si vos utilisateurs ne sont pas des membres permanents de groupes qui accorderaient des droits JEA supplémentaires, cette applet de commande ne reflète pas ces autorisations.</span><span class="sxs-lookup"><span data-stu-id="93351-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="93351-122">C’est généralement le cas lors de l’utilisation de systèmes de gestion à accès privilégié de type just-in-time pour permettre aux utilisateurs d’appartenir temporairement à un groupe de sécurité.</span><span class="sxs-lookup"><span data-stu-id="93351-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="93351-123">Évaluez toujours attentivement le mappage des utilisateurs sur les rôles et les contenus de chaque rôle pour vous assurer que les utilisateurs ont accès uniquement à la quantité de commandes nécessaires pour mener leurs tâches à bien.</span><span class="sxs-lookup"><span data-stu-id="93351-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="93351-124">Journaux des événements PowerShell</span><span class="sxs-lookup"><span data-stu-id="93351-124">PowerShell event logs</span></span>

<span data-ttu-id="93351-125">Si vous avez activé la journalisation de module et/ou de bloc de script sur le système, vous serez en mesure de rechercher des événements dans les journaux des événements Windows pour chaque commande exécutée par un utilisateur dans ses sessions JEA.</span><span class="sxs-lookup"><span data-stu-id="93351-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="93351-126">Pour rechercher ces événements, ouvrez l’Observateur d’événements Windows, accédez au journal des événements **Microsoft-Windows-PowerShell/Operational** et recherchez des événements avec l’ID **4104**.</span><span class="sxs-lookup"><span data-stu-id="93351-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="93351-127">Chaque entrée de journal des événements comprend des informations sur la session dans laquelle la commande a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="93351-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="93351-128">Pour les sessions JEA, il s’agit d’informations importantes sur le **ConnectedUser**, qui est l’utilisateur réel qui a créé la session JEA, ainsi que le **RunAsUser**, qui identifie le compte JEA utilisé pour exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="93351-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="93351-129">Les journaux des événements de l’application indiquent les modifications effectuées par le RunAsUser. Il est donc important de disposer de transcriptions ou d’activer la journalisation du module / des scripts pour pouvoir tracer un appel de commande spécifique jusqu’à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="93351-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="93351-130">Journaux des événements de l’application</span><span class="sxs-lookup"><span data-stu-id="93351-130">Application event logs</span></span>

<span data-ttu-id="93351-131">Lorsque vous exécutez une commande dans une session JEA qui interagit avec une application ou un service externe, ces applications peuvent éventuellement journaliser des événements dans leurs propres journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="93351-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="93351-132">Contrairement aux journaux PowerShell et aux transcriptions, d’autres mécanismes de journalisation ne capturent pas l’utilisateur connecté de la session JEA et journalisent uniquement le run-as user virtuel ou le compte de service administré de groupe.</span><span class="sxs-lookup"><span data-stu-id="93351-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="93351-133">Afin de déterminer qui a exécuté la commande, vous devez consulter un [transcript de session](#session-transcripts) ou mettre en corrélation des journaux des événements de PowerShell avec l’heure et l’utilisateur indiqués dans le journal des événements de l’application.</span><span class="sxs-lookup"><span data-stu-id="93351-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="93351-134">Le journal WinRM peut également vous aider à mettre en corrélation les run as users dans un journal des événements de l’application avec l’utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="93351-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="93351-135">L’ID d’événement **193** dans le journal **Microsoft-Windows-Windows Remote Management/Operational** enregistre l’identificateur de sécurité (SID) et le nom du compte de l’utilisateur qui se connecte et le run as user chaque fois qu’une session JEA est créée.</span><span class="sxs-lookup"><span data-stu-id="93351-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="93351-136">Transcriptions de session</span><span class="sxs-lookup"><span data-stu-id="93351-136">Session transcripts</span></span>

<span data-ttu-id="93351-137">Si vous avez configuré JEA afin de créer une transcription pour chaque session utilisateur, une copie de texte des actions de chaque utilisateur est stockée dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="93351-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="93351-138">Pour rechercher tous les répertoires de transcription, exécutez la commande suivante en tant qu’administrateur sur l’ordinateur configuré avec JEA :</span><span class="sxs-lookup"><span data-stu-id="93351-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="93351-139">Chaque transcription démarre avec des informations sur l’heure de début de la session, l’heure de la connexion de l’utilisateur à la session, et l’identité JEA qui lui a été attribuée.</span><span class="sxs-lookup"><span data-stu-id="93351-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="93351-140">Dans le texte de la transcription, les informations concernant chaque commande que l’utilisateur a appelée sont journalisées.</span><span class="sxs-lookup"><span data-stu-id="93351-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="93351-141">La syntaxe exacte de la commande exécutée par l’utilisateur n’est pas disponible dans les sessions JEA en raison de la manière dont les commandes sont transformées pour l’accès distant PowerShell. Cependant, vous pouvez toujours déterminer la commande effective qui a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="93351-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="93351-142">Voici un exemple d’extrait de code de transcription d’un utilisateur exécutant `Get-Service Dns` dans une session JEA :</span><span class="sxs-lookup"><span data-stu-id="93351-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="93351-143">Une ligne « CommandInvocation » est écrite pour chaque commande qu'un utilisateur exécute, qui décrit l’applet de commande ou la fonction appelée par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="93351-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="93351-144">Les liaisons de paramètres (ParameterBindings) suivent chaque appel de commande (CommandInvocation) pour vous donner des informations sur chaque paramètre et leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="93351-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="93351-145">Dans l’exemple ci-dessus, vous pouvez voir que le paramètre « Name » a reçu la valeur « Dns » pour l’applet de commande « Get-Service ».</span><span class="sxs-lookup"><span data-stu-id="93351-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="93351-146">Le résultat de chaque commande déclenche également une CommandInvocation, généralement pour Out-Default.</span><span class="sxs-lookup"><span data-stu-id="93351-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span>
<span data-ttu-id="93351-147">L’objet d’entrée (InputObject) d’Out-Default est l’objet PowerShell retourné par la commande.</span><span class="sxs-lookup"><span data-stu-id="93351-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="93351-148">Les détails de cet objet sont indiqués ci-dessous. Ils imitent étroitement ce que l’utilisateur a pu observer.</span><span class="sxs-lookup"><span data-stu-id="93351-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="93351-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93351-149">See also</span></span>

- [<span data-ttu-id="93351-150">*PowerShell ♥ the Blue Team*, billet de blog sur la sécurité</span><span class="sxs-lookup"><span data-stu-id="93351-150">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)
