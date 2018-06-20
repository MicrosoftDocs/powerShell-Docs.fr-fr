---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource WindowsOptionalFeatureSet dans DSC
ms.openlocfilehash: 7c5eb553b396776f54a36bec8971f71ec61f9354
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187655"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>Ressource WindowsOptionalFeatureSet dans DSC

> S’applique à : Windows PowerShell 5.0

La ressource **WindowsOptionalFeatureSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des fonctionnalités facultatives sont activées sur un nœud cible.
Cette ressource est une [ressource composite](authoringResourceComposite.md) qui appelle la ressource [WindowsOptionalFeature](windowsOptionalFeatureResource.md) pour chaque fonctionnalité spécifiée dans la propriété `Name`.

Utilisez cette ressource quand vous voulez configurer certaines fonctionnalités facultatives de Windows au même état.

## <a name="syntax"></a>Syntaxe

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   |
|---|---|
| Name| Indique le nom des fonctionnalités que vous souhaitez voir activées ou désactivées.|
| Ensure| Spécifie si les fonctionnalités sont activées. Pour vous assurer que les fonctionnalités sont activées, affectez la valeur « Enable » à cette propriété. Pour vous assurer que les fonctionnalités sont désactivées, affectez la valeur «Disable ».|
| Source| Non implémentée.|
| NoWindowsUpdateCheck| Indique si DISM contacte Windows Update (WU) lors de la recherche des fichiers sources pour activer les fonctionnalités. Si la valeur est $true, DISM ne contacte pas Windows Update.|
| RemoveFilesOnDisable| Affectez la valeur **$true** pour supprimer tous les fichiers associés aux fonctionnalités quand elles sont désactivées (autrement dit, quand **Ensure** a la valeur « Absent »).|
| LogLevel| Niveau de sortie maximal affiché dans les journaux. Les valeurs acceptées sont les suivantes : « ErrorsOnly » (seules les erreurs sont enregistrées), « ErrorsAndWarning » (les erreurs et les avertissements sont enregistrés) et « ErrorsAndWarningAndInformation » (les erreurs, les avertissements et les informations de débogage sont enregistrés).|
| LogPath| Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.|
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.|