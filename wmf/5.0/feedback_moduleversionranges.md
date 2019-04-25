---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: e2c9233734a6ede04e8ec2bbad05950cbb31cbba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057501"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Prise en charge des modules pour la déclaration des plages de versions (1.*, etc.)
Combiné avec **-MinimumVersion**, **-MaximumVersion** permet désormais à l’utilisateur d’obtenir/importer un module dans une plage spécifique. Le paramètre prend également en charge **.**\*. L’exemple suivant illustre son fonctionnement :

Maintenant, vous pouvez combiner **- MinimumVersion** et **- MaximumVersion** pour importer le module dans une plage spécifique :

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
