---
ms.date: 06/12/2017
title: Flux d’informations
description: PowerShell 5.0 ajoute un nouveau flux **d’informations** structuré pour transmettre des données structurées entre un script et son hôte.
ms.openlocfilehash: 818c99ce281f5ada596ff92cd7bafb8b7cacf709
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646713"
---
# <a name="information-stream"></a>Flux d’informations

PowerShell 5.0 ajoute un nouveau flux **d’informations** structuré pour transmettre des données structurées entre un script et son hôte. `Write-Host` a également été mis à jour pour envoyer sa sortie vers le flux **d’informations** , où elle peut être capturée ou passée sous silence. Utilisée avec les paramètres communs `Write-Information`InformationVariable **et** InformationAction **, la nouvelle cmdlet**  offre davantage de souplesse et de fonctionnalités.

La fonction suivante utilise des cmdlets qui exploitent le nouveau flux **d’informations** .

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

Les exemples suivants montrent les résultats de cette fonction.

```powershell
$r = OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

La variable `$r` a capturé les informations de processus dans la variable de script `$p`.

```powershell
$r.Id
4008
```

Contrairement à la cmdlet `Write-Host`, le paramètre **InformationVariable**`Write-Information` permet de capturer la sortie dans une variable. Avec **Tags** , vous pouvez créer des canaux distincts pour le message envoyé au flux **d’informations** .

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

Lorsque vous envoyez un message au flux **d’informations** avec un tag, ce message ne s’affiche pas dans l’application hôte, mais reste récupérable avec le nom du tag. Par exemple :

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```
