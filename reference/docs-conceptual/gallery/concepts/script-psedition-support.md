---
ms.date: 06/12/2017
title: Écrire des scripts avec des éditions de PowerShell compatibles
description: Cet article explique comment les applets de commande PowerShellGet prennent en charge les éditions Desktop et Core des scripts PowerShell.
ms.openlocfilehash: c9d8af24be8138283027263c62140b3fd04d6b24
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656054"
---
# <a name="script-with-compatible-powershell-editions"></a>Écrire des scripts avec des éditions de PowerShell compatibles

À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent la compatibilité de la plateforme et les différents ensembles de fonctionnalités.

- **Édition Desktop :** repose sur .NET Framework et offre une compatibilité avec les scripts et les modules ciblant les versions de PowerShell exécutées sur les éditions complètes de Windows, telles que Server Core et le Bureau Windows.

- **Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.

La version de PowerShell en cours d’exécution figure dans la propriété PSEdition de $PSVersionTable.

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

Les auteurs de scripts peuvent empêcher l’exécution d’un script, sauf s’il est exécuté dans une édition compatible de PowerShell avec le paramètre PSEdition sur une instruction `#requires`.

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

Les utilisateurs de PowerShell Gallery peuvent trouver la liste des scripts pris en charge sur une édition spécifique de PowerShell.
Les scripts sans les étiquettes PSEdition_Desktop et PSEdition_Core sont considérés comme fonctionnant correctement sur l’édition de PowerShell Desktop.

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a>Détails supplémentaires

- [Modules avec des éditions PS](module-psedition-support.md)
- [Prise en charge des éditions PS sur PowerShellGallery](../how-to/finding-packages/searching-by-compatibility.md)
