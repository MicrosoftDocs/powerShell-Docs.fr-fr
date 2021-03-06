---
ms.date: 08/28/2020
ms.topic: reference
title: Ressource WindowsOptionalFeature dans DSC
description: Ressource WindowsOptionalFeature dans DSC
ms.openlocfilehash: 1c7e888ea49b0d1710cc22c975cb618999238f67
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143056"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>Ressource WindowsOptionalFeature dans DSC

> S’applique à : Windows PowerShell 5.x

La ressource **WindowsOptionalFeature** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des fonctionnalités facultatives sont activées sur un nœud cible.

> [!NOTE]
> **WindowsOptionalFeature** fonctionne uniquement sur les ordinateurs clients Windows, comme Windows 10.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntaxe

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Name |Indique le nom de la fonctionnalité que vous souhaitez voir activée ou désactivée. |
|NoWindowsUpdateCheck |Indique si DISM contacte Windows Update (WU) lors de la recherche des fichiers sources pour activer une fonctionnalité. Si la valeur est `$true`, DISM ne contacte pas Windows Update. |
|RemoveFilesOnDisable |Affectez la valeur `$true` pour supprimer tous les fichiers associés à la fonctionnalité quand **Ensure** est défini sur **Absent** . |
|LogLevel |Niveau de sortie maximal affiché dans les journaux. Les valeurs acceptées sont les suivantes : **ErrorsOnly** , **ErrorsAndWarning** et **ErrorsAndWarningAndInformation** . |
|LogPath |Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indique si la fonctionnalité est activée. Pour faire en sorte que la fonctionnalité soit activée, affectez à cette propriété la valeur _Enable_ . Pour faire en sorte que la fonctionnalité soit désactivée, affectez à cette propriété la valeur _Disable_ . La valeur par défaut est _Enable_ . |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).
