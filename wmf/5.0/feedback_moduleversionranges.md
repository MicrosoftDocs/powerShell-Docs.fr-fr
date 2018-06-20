---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: f491e30859cbe6cbaa58f94389382ff231c52956
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225689"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="76355-102">Prise en charge des modules pour la déclaration des plages de versions (1.\*, etc.)</span><span class="sxs-lookup"><span data-stu-id="76355-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="76355-103">Combiné avec **-MinimumVersion**, **-MaximumVersion** permet désormais à l’utilisateur d’obtenir/importer un module dans une plage spécifique.</span><span class="sxs-lookup"><span data-stu-id="76355-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="76355-104">Le paramètre prend également en charge **.**\*.</span><span class="sxs-lookup"><span data-stu-id="76355-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="76355-105">L’exemple suivant illustre son fonctionnement :</span><span class="sxs-lookup"><span data-stu-id="76355-105">The following example shows how it works:</span></span>

<span data-ttu-id="76355-106">Maintenant, vous pouvez combiner **- MinimumVersion** et **- MaximumVersion** pour importer le module dans une plage spécifique :</span><span class="sxs-lookup"><span data-stu-id="76355-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
