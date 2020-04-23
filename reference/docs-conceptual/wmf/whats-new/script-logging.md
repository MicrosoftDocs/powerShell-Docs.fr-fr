---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Traçage et journalisation de script
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147799"
---
# <a name="script-tracing-and-logging"></a>Traçage et journalisation de script

Bien que PowerShell propose déjà le paramètre de stratégie de groupe **LogPipelineExecutionDetails** pour consigner l’appel des cmdlets, le langage de script PowerShell offre plusieurs fonctionnalités intéressantes dans une optique de journalisation et d’audit. La nouvelle fonctionnalité de traçage de script détaillé assure un suivi et une analyse détaillés de l’activité des scripts PowerShell sur un système. Lorsqu’elle est activée, PowerShell consigne tous les blocs de scripts dans le journal des événements ETW, **Microsoft-Windows-PowerShell/Operational**. Si un bloc de script crée un autre bloc de script, par exemple en appelant `Invoke-Expression`, le bloc de script appelé est également enregistré.

La journalisation s’active par le biais du paramètre de stratégie de groupe **Activer la journalisation des blocs de scripts PowerShell** dans **Modèles d’administration** -> **Composants Windows** -> **Windows PowerShell**.

Les événements sont :

| Channel |                               En fonctionnement                               |
| ------- | ----------------------------------------------------------------------- |
| Level   | Commentaires                                                                 |
| Opcode  | Créer                                                                  |
| Tâche    | CommandStart                                                            |
| Mot clé | Instance d'exécution                                                                |
| EventId | Engine_ScriptBlockCompiled (0x1008 = 4104)                              |
| Message | Création du texte Scriptblock (%1 sur %2) : </br> %3 </br> ID Scriptblock : %4 |


Le texte incorporé dans le message est l’étendue du bloc de script compilé. L’ID est un GUID qui est conservé pendant toute la durée de vie du bloc de script.

Quand vous activez la journalisation détaillée, la fonctionnalité écrit des marqueurs de début et de fin :

| Channel |                                 En fonctionnement                                |
| ------- | -------------------------------------------------------------------------- |
| Level   | Commentaires                                                                    |
| Opcode  | Open / Close                                                               |
| Tâche    | CommandStart / CommandStop                                                 |
| Mot clé | Instance d'exécution                                                                   |
| EventId | ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) / </br> ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106) |
| Message | Started / Completed invocation of ScriptBlock ID: %1 </br> ID d’instance d’exécution : %2 |

L’ID est le GUID représentant le bloc de script (qui peut être mis en corrélation avec l’ID d’événement 0x1008), et l’ID d’instance d’exécution représente l’instance d’exécution dans laquelle ce bloc de script a été exécuté.

Les signes de pourcentage dans le message d’appel représentent des propriétés ETW structurées. Bien qu’ils soient remplacés par les valeurs réelles dans le texte du message, une façon plus fiable d’y accéder consiste à récupérer le message avec l’applet de commande Get-WinEvent, puis à utiliser le tableau **Propriétés** du message.

Voici un exemple qui illustre comment cette fonctionnalité peut aider à contrer une tentative malveillante de chiffrement et de brouillage de script :

```powershell
## Malware
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

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

L’exécution de ce code génère les entrées de journal suivantes :

```Output
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

Si la longueur du bloc de script dépasse la capacité d’un seul événement, PowerShell divise le script en plusieurs parties. Voici un exemple de code qui recombine un script à partir de ses messages de journal :

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Comme pour tous les systèmes de journalisation dont la mémoire tampon de rétention est limitée, une attaque possible contre cette infrastructure consiste à saturer le journal de faux événements pour masquer les preuves antérieures. Pour vous en protéger, configurez, sous une forme ou une autre, la collecte de journaux des événements dans le transfert d’événements Windows. Pour plus d’informations, voir [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).