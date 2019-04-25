---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: e01f6ceea361f5a9b3de645346d0652986b6267d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057228"
---
# <a name="nonewline-parameter"></a>Paramètre NoNewLine
Les applets de commande **Out-File**, **Add-Content** et **Set-Content** ont maintenant un nouveau commutateur **–NoNewline** qui omet tout simplement une nouvelle ligne après la sortie.
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
Si vous ne spécifiez pas **–NoNewline**, chaque fragment est sur une ligne distincte :
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
