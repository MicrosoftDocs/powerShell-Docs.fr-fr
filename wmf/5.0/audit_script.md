---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 2627b9d02788bd31a5384587406df533faf2cfaf
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="00f73-102">Traçage et journalisation de script</span><span class="sxs-lookup"><span data-stu-id="00f73-102">Script Tracing and Logging</span></span>

<span data-ttu-id="00f73-103">Bien que Windows PowerShell propose déjà le paramètre de stratégie de groupe **LogPipelineExecutionDetails** pour journaliser l’appel des applets de commande, le langage de script PowerShell offre de nombreuses fonctionnalités que vous souhaiterez peut-être journaliser et/ou auditer.</span><span class="sxs-lookup"><span data-stu-id="00f73-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="00f73-104">La nouvelle fonctionnalité de traçage de script détaillé vous permet d’activer le suivi et l’analyse détaillés de l’utilisation des scripts Windows PowerShell sur un système.</span><span class="sxs-lookup"><span data-stu-id="00f73-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="00f73-105">Une fois que vous avez activé le traçage de script détaillé, Windows PowerShell enregistre tous les blocs de scripts dans le journal des événements ETW, **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="00f73-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="00f73-106">Si un bloc de script crée un autre bloc de script (par exemple, un script qui appelle l’applet de commande Invoke-Expression sur une chaîne), ce bloc de script résultant est également enregistré.</span><span class="sxs-lookup"><span data-stu-id="00f73-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="00f73-107">Vous pouvez activer la journalisation de ces événements par le biais du paramètre de stratégie de groupe **Activer la journalisation de blocs de scripts PowerShell** (dans Modèles d’administration -> Composants Windows -> Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="00f73-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="00f73-108">Les événements sont :</span><span class="sxs-lookup"><span data-stu-id="00f73-108">The events are:</span></span>

| <span data-ttu-id="00f73-109">Canal</span><span class="sxs-lookup"><span data-stu-id="00f73-109">Channel</span></span> | <span data-ttu-id="00f73-110">Opérationnel</span><span class="sxs-lookup"><span data-stu-id="00f73-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="00f73-111">Niveau</span><span class="sxs-lookup"><span data-stu-id="00f73-111">Level</span></span>   | <span data-ttu-id="00f73-112">Verbose</span><span class="sxs-lookup"><span data-stu-id="00f73-112">Verbose</span></span>                                     |
| <span data-ttu-id="00f73-113">Opcode</span><span class="sxs-lookup"><span data-stu-id="00f73-113">Opcode</span></span>  | <span data-ttu-id="00f73-114">Create</span><span class="sxs-lookup"><span data-stu-id="00f73-114">Create</span></span>                                      |
| <span data-ttu-id="00f73-115">Tâche</span><span class="sxs-lookup"><span data-stu-id="00f73-115">Task</span></span>    | <span data-ttu-id="00f73-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="00f73-116">CommandStart</span></span>                                |
| <span data-ttu-id="00f73-117">Mot clé</span><span class="sxs-lookup"><span data-stu-id="00f73-117">Keyword</span></span> | <span data-ttu-id="00f73-118">Instance d'exécution</span><span class="sxs-lookup"><span data-stu-id="00f73-118">Runspace</span></span>                                    |
| <span data-ttu-id="00f73-119">EventId</span><span class="sxs-lookup"><span data-stu-id="00f73-119">EventId</span></span> | <span data-ttu-id="00f73-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="00f73-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="00f73-121">Message</span><span class="sxs-lookup"><span data-stu-id="00f73-121">Message</span></span> | <span data-ttu-id="00f73-122">Création du texte Scriptblock (%1 sur %2) :</span><span class="sxs-lookup"><span data-stu-id="00f73-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="00f73-123">%3</span><span class="sxs-lookup"><span data-stu-id="00f73-123">%3</span></span> </br> <span data-ttu-id="00f73-124">ID Scriptblock : %4</span><span class="sxs-lookup"><span data-stu-id="00f73-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="00f73-125">Le texte incorporé dans le message est l’étendue du bloc de script compilé.</span><span class="sxs-lookup"><span data-stu-id="00f73-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="00f73-126">L’ID est un GUID qui est conservé pendant toute la durée de vie du bloc de script.</span><span class="sxs-lookup"><span data-stu-id="00f73-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="00f73-127">Quand vous activez la journalisation détaillée, la fonctionnalité écrit des marqueurs de début et de fin :</span><span class="sxs-lookup"><span data-stu-id="00f73-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="00f73-128">Canal</span><span class="sxs-lookup"><span data-stu-id="00f73-128">Channel</span></span> | <span data-ttu-id="00f73-129">Opérationnel</span><span class="sxs-lookup"><span data-stu-id="00f73-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="00f73-130">Niveau</span><span class="sxs-lookup"><span data-stu-id="00f73-130">Level</span></span>   | <span data-ttu-id="00f73-131">Verbose</span><span class="sxs-lookup"><span data-stu-id="00f73-131">Verbose</span></span>                                                |
| <span data-ttu-id="00f73-132">Opcode</span><span class="sxs-lookup"><span data-stu-id="00f73-132">Opcode</span></span>  | <span data-ttu-id="00f73-133">Open (/ Close)</span><span class="sxs-lookup"><span data-stu-id="00f73-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="00f73-134">Tâche</span><span class="sxs-lookup"><span data-stu-id="00f73-134">Task</span></span>    | <span data-ttu-id="00f73-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="00f73-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="00f73-136">Mot clé</span><span class="sxs-lookup"><span data-stu-id="00f73-136">Keyword</span></span> | <span data-ttu-id="00f73-137">Instance d'exécution</span><span class="sxs-lookup"><span data-stu-id="00f73-137">Runspace</span></span>                                               |
| <span data-ttu-id="00f73-138">EventId</span><span class="sxs-lookup"><span data-stu-id="00f73-138">EventId</span></span> | <span data-ttu-id="00f73-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="00f73-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="00f73-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="00f73-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="00f73-141">Message</span><span class="sxs-lookup"><span data-stu-id="00f73-141">Message</span></span> | <span data-ttu-id="00f73-142">Le système a lancé l’appel de l’ID de bloc de script : %1%</span><span class="sxs-lookup"><span data-stu-id="00f73-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="00f73-143">ID d’instance d’exécution : %2</span><span class="sxs-lookup"><span data-stu-id="00f73-143">Runspace ID: %2</span></span> |

<span data-ttu-id="00f73-144">L’ID est le GUID représentant le bloc de script (qui peut être mis en corrélation avec l’ID d’événement 0x1008), et l’ID d’instance d’exécution représente l’instance d’exécution dans laquelle ce bloc de script a été exécuté.</span><span class="sxs-lookup"><span data-stu-id="00f73-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="00f73-145">Les signes de pourcentage dans le message d’appel représentent des propriétés ETW structurées.</span><span class="sxs-lookup"><span data-stu-id="00f73-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="00f73-146">Bien qu’ils soient remplacés par les valeurs réelles dans le texte du message, une façon plus fiable d’y accéder consiste à récupérer le message avec l’applet de commande Get-WinEvent, puis à utiliser le tableau **Propriétés** du message.</span><span class="sxs-lookup"><span data-stu-id="00f73-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="00f73-147">Voici un exemple qui illustre comment cette fonctionnalité peut aider à contrer une tentative malveillante de chiffrement et de brouillage de script :</span><span class="sxs-lookup"><span data-stu-id="00f73-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR “encryption”
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

<span data-ttu-id="00f73-148">L’exécution de ce code génère les entrées de journal suivantes :</span><span class="sxs-lookup"><span data-stu-id="00f73-148">Running this generates the following log entries:</span></span>

```
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

Si la longueur du bloc de script dépasse ce que ETW est capable de contenir dans un seul événement, Windows PowerShell divise le script en plusieurs parties. <span data-ttu-id="00f73-150">Voici un exemple de code qui recombine un script à partir de ses messages de journal :</span><span class="sxs-lookup"><span data-stu-id="00f73-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="00f73-151">Comme avec tous les systèmes de journalisation qui ont une mémoire tampon de rétention limitée (tels que les journaux ETW), une attaque possible contre cette infrastructure consiste à submerger le journal de faux événements pour masquer les preuves antérieures.</span><span class="sxs-lookup"><span data-stu-id="00f73-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="00f73-152">Pour vous protéger contre ce genre d’attaque, veillez à configurer une forme de collecte de journal des événements (par exemple, transferts d’événements Windows, [Spotting the Adversary with Windows Event Log Monitoring](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) pour déplacer les journaux des événements hors de l’ordinateur dès que possible.</span><span class="sxs-lookup"><span data-stu-id="00f73-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) to move event logs off of the computer as soon as possible.</span></span>
