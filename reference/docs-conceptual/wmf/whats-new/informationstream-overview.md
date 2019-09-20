---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Flux d’informations
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147609"
---
# <a name="information-stream"></a><span data-ttu-id="78786-103">Flux d’informations</span><span class="sxs-lookup"><span data-stu-id="78786-103">Information Stream</span></span>

<span data-ttu-id="78786-104">PowerShell 5.0 ajoute un nouveau flux **d’informations** structuré pour transmettre des données structurées entre un script et son hôte.</span><span class="sxs-lookup"><span data-stu-id="78786-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="78786-105">`Write-Host` a également été mis à jour pour envoyer sa sortie vers le flux **d’informations**, où elle peut être capturée ou passée sous silence.</span><span class="sxs-lookup"><span data-stu-id="78786-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="78786-106">Utilisée avec les paramètres communs **InformationVariable** et **InformationAction**, la nouvelle cmdlet `Write-Information` offre davantage de souplesse et de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="78786-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="78786-107">La fonction suivante utilise des cmdlets qui exploitent le nouveau flux **d’informations**.</span><span class="sxs-lookup"><span data-stu-id="78786-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

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

<span data-ttu-id="78786-108">Les exemples suivants montrent les résultats de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="78786-108">The following examples show the results of running this function.</span></span>

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

<span data-ttu-id="78786-109">La variable `$r` a capturé les informations de processus dans la variable de script `$p`.</span><span class="sxs-lookup"><span data-stu-id="78786-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="78786-110">Contrairement à la cmdlet `Write-Host`, le paramètre **InformationVariable** `Write-Information` permet de capturer la sortie dans une variable.</span><span class="sxs-lookup"><span data-stu-id="78786-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="78786-111">Avec **Tags**, vous pouvez créer des canaux distincts pour le message envoyé au flux **d’informations**.</span><span class="sxs-lookup"><span data-stu-id="78786-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

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

<span data-ttu-id="78786-112">Lorsque vous envoyez un message au flux **d’informations** avec un tag, ce message ne s’affiche pas dans l’application hôte, mais reste récupérable avec le nom du tag.</span><span class="sxs-lookup"><span data-stu-id="78786-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="78786-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="78786-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```