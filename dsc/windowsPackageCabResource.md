---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WindowsPackageCab
ms.openlocfilehash: 8c4de193c8ea787dd125436f86aa0b5eafdb1509
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190347"
---
# <a name="dsc-windowspackagecab-resource"></a>Ressource DSC WindowsPackageCab

> S’applique à : Windows PowerShell 5.1 et ultérieur

La ressource **WindowsPackageCab** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’installer ou de désinstaller des packages de cabinet Windows (.cab) sur un nœud cible.

Le nœud cible doit disposer du module DISM PowerShell installé. Pour plus d’informations, consultez [Utilisation de DISM Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).


## <a name="syntax"></a>Syntaxe

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   |
|---|---|
| Name| Indique le nom du package pour lequel vous souhaitez garantir un état spécifique.|
| Ensure| Indique si le package est installé. Définissez cette propriété sur « Absent » pour vous assurer que le package n’est pas installé (ou désinstallé, si le package n’est pas installé). Définissez cette propriété sur « Present » (valeur par défaut) pour vous assurer que le package est installé.|
| Path| Indique le chemin où se trouve le package.|
| LogPath| Indique le chemin complet où vous souhaitez que le fournisseur enregistre un fichier journal pour installer ou désinstaller le package.|
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : DependsOn = "[ResourceType]ResourceName"|

## <a name="example"></a>Exemple

L’exemple de configuration suivant accepte des paramètres d’entrée et garantit que le fichier spécifié par le paramètre `$Name` est installé.

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```