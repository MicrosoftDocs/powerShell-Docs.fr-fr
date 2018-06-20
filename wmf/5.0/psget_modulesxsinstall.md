---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: d4168640f67cb1dd44e91d1867e87fd7a6b7f549
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218347"
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a>Prise en charge des versions côte à côte sur PowerShell 5.0 ou version ultérieure

Les applets de commande Install-module, Update-Module et Publish-Module qui s’exécutent dans Windows PowerShell 5.0 ou version ultérieure offrent désormais une prise en charge des versions de modules côte à côte (SxS).
Nous avons aussi ajouté un paramètre -RequiredVersion à l’applet de commande Publish-Module pour spécifier la version à publier. Le paramètre Path prend désormais en charge le chemin de base de module avec le dossier de version.

**Exemples Install-Module :**
```powershell
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Get-InstalledModule -Name PSScriptAnalyzer -AllVersions

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```
