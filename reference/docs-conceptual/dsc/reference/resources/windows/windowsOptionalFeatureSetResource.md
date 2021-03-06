---
ms.date: 07/16/2020
ms.topic: reference
title: Ressource WindowsOptionalFeatureSet dans DSC
description: Ressource WindowsOptionalFeatureSet dans DSC
ms.openlocfilehash: f72cc27bfc8847d2c87cfb289f3e2c729a21d1f4
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143039"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>Ressource WindowsOptionalFeatureSet dans DSC

> S’applique à : Windows PowerShell 5.x

La ressource **WindowsOptionalFeatureSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des fonctionnalités facultatives sont activées sur un nœud cible. Cette ressource est une [ressource composite](../../../resources/authoringResourceComposite.md) qui appelle la [ressource WindowsOptionalFeature](windowsOptionalFeatureResource.md) pour chaque fonctionnalité spécifiée dans la propriété **Name** .

Utilisez cette ressource quand vous voulez configurer certaines fonctionnalités facultatives de Windows au même état.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntaxe

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Nom |Indique le nom des fonctionnalités que vous souhaitez voir activées ou désactivées. |
|NoWindowsUpdateCheck |Indique si DISM contacte Windows Update (WU) lors de la recherche des fichiers sources pour activer les fonctionnalités. Si la valeur est `$true`, DISM ne contacte pas Windows Update. |
|RemoveFilesOnDisable |Affectez la valeur `$true` pour supprimer tous les fichiers associés aux fonctionnalités quand **Ensure** est défini sur **Absent** . |
|LogLevel |Niveau de sortie maximal affiché dans les journaux. Les valeurs acceptées sont les suivantes : **ErrorsOnly** , **ErrorsAndWarning** et **ErrorsAndWarningAndInformation** . |
|LogPath |Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Spécifie si les fonctionnalités sont activées. Pour faire en sorte que les fonctionnalités soient activées, affectez à cette propriété la valeur **Enable** . Pour faire en sorte que les fonctionnalités soient désactivées, affectez à cette propriété la valeur **Disable** . La valeur par défaut est **Enable** . |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).
