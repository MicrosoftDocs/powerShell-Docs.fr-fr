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
# <a name="nonewline-parameter"></a><span data-ttu-id="57fed-102">Paramètre NoNewLine</span><span class="sxs-lookup"><span data-stu-id="57fed-102">NoNewLine parameter</span></span>
<span data-ttu-id="57fed-103">Les applets de commande **Out-File**, **Add-Content** et **Set-Content** ont maintenant un nouveau commutateur **–NoNewline** qui omet tout simplement une nouvelle ligne après la sortie.</span><span class="sxs-lookup"><span data-stu-id="57fed-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="57fed-104">Si vous ne spécifiez pas **–NoNewline**, chaque fragment est sur une ligne distincte :</span><span class="sxs-lookup"><span data-stu-id="57fed-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
