---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: b8f175cee0a1de501b64890fdc2798f4f6421a14
ms.sourcegitcommit: 2ffb9fa92129c2001379ca2c17646466721f7165
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251481"
---
# <a name="script-tracing-and-logging"></a>Traçage et journalisation de script

Bien que Windows PowerShell propose déjà le paramètre de stratégie de groupe **LogPipelineExecutionDetails** pour journaliser l’appel des applets de commande, le langage de script PowerShell offre de nombreuses fonctionnalités que vous souhaiterez peut-être journaliser et/ou auditer. La nouvelle fonctionnalité de traçage de script détaillé vous permet d’activer le suivi et l’analyse détaillés de l’utilisation des scripts Windows PowerShell sur un système. Une fois que vous avez activé le traçage de script détaillé, Windows PowerShell enregistre tous les blocs de scripts dans le journal des événements ETW, **Microsoft-Windows-PowerShell/Operational**. Si un bloc de script crée un autre bloc de script (par exemple, un script qui appelle l’applet de commande Invoke-Expression sur une chaîne), ce bloc de script résultant est également enregistré.

Vous pouvez activer la journalisation de ces événements par le biais du paramètre de stratégie de groupe **Activer la journalisation de blocs de scripts PowerShell** (dans Modèles d’administration -> Composants Windows -> Windows PowerShell).

Les événements sont :

| Canal | Opérationnel                                 |
|---------|---------------------------------------------|
| Niveau   | Verbose                                     |
| Opcode  | Create                                      |
| Tâche    | CommandStart                                |
| Mot clé | Instance d'exécution                                    |
| EventId | Engine_ScriptBlockCompiled (0x1008 = 4104)  |
| Message | Création du texte Scriptblock (%1 sur %2) : </br> %3 </br> ID Scriptblock : %4 |


Le texte incorporé dans le message est l’étendue du bloc de script compilé. L’ID est un GUID qui est conservé pendant toute la durée de vie du bloc de script.

Quand vous activez la journalisation détaillée, la fonctionnalité écrit des marqueurs de début et de fin :

| Canal | Opérationnel                                            |
|---------|--------------------------------------------------------|
| Niveau   | Verbose                                                |
| Opcode  | Open (/ Close)                                         |
| Tâche    | CommandStart (/ CommandStop)                           |
| Mot clé | Instance d'exécution                                               |
| EventId | ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) / </br> ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106) |
| Message | Le système a lancé l’appel de l’ID de bloc de script : %1% </br> ID d’instance d’exécution : %2 |

L’ID est le GUID représentant le bloc de script (qui peut être mis en corrélation avec l’ID d’événement 0x1008), et l’ID d’instance d’exécution représente l’instance d’exécution dans laquelle ce bloc de script a été exécuté.

Les signes de pourcentage dans le message d’appel représentent des propriétés ETW structurées. Bien qu’ils soient remplacés par les valeurs réelles dans le texte du message, une façon plus fiable d’y accéder consiste à récupérer le message avec l’applet de commande Get-WinEvent, puis à utiliser le tableau **Propriétés** du message.

Voici un exemple qui illustre comment cette fonctionnalité peut aider à contrer une tentative malveillante de chiffrement et de brouillage de script :

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

L’exécution de ce code génère les entrées de journal suivantes :

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

Si la longueur du bloc de script dépasse ce que ETW est capable de contenir dans un seul événement, Windows PowerShell divise le script en plusieurs parties. Voici un exemple de code qui recombine un script à partir de ses messages de journal :

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Comme avec tous les systèmes de journalisation qui ont une mémoire tampon de rétention limitée (tels que les journaux ETW), une attaque possible contre cette infrastructure consiste à submerger le journal de faux événements pour masquer les preuves antérieures. Pour vous protéger contre ce genre d’attaque, veillez à configurer une forme de collecte de journal des événements (par exemple, transferts d’événements Windows, [Spotting the Adversary with Windows Event Log Monitoring](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) pour déplacer les journaux des événements hors de l’ordinateur dès que possible.
