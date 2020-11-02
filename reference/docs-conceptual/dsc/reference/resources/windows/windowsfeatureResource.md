---
ms.date: 07/16/2020
ms.topic: reference
title: Ressource WindowsFeature dans DSC
description: Ressource WindowsFeature dans DSC
ms.openlocfilehash: 0089e1d2a045e9398aa53a3cedc3f64285c7cd58
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142988"
---
# <a name="dsc-windowsfeature-resource"></a>Ressource WindowsFeature dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource **WindowsFeature** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des rôles et des fonctionnalités sont ajoutés ou supprimés sur un nœud cible.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntaxe

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Name |Indique le nom du rôle ou de la fonctionnalité dont vous voulez garantir l’ajout ou la suppression. Il s’agit du même nom que celui de la propriété **Name** de l’applet de commande [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) et non du nom d’affichage du rôle ou de la fonctionnalité. |
|Informations d'identification |Indique les informations d’identification à utiliser pour ajouter ou supprimer le rôle ou la fonctionnalité. |
|IncludeAllSubFeature |Définissez cette propriété sur `$true` pour faire en sorte que l’état de toutes les sous-fonctionnalités nécessaires soit l’état de la fonctionnalité que vous spécifiez avec la propriété **Name** . |
|LogPath |Indique le chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indique si le rôle ou la fonctionnalité sont ajoutés. Pour faire en sorte que le rôle ou la fonctionnalité soient ajoutés, définissez cette propriété sur **Present** . Pour faire en sorte que le rôle ou la fonctionnalité soient supprimés, définissez cette propriété sur **Absent** . La valeur par défaut est **Present** . |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Exemple

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```
