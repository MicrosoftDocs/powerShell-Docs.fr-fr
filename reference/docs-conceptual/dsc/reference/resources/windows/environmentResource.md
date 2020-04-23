---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource Environment DSC
ms.openlocfilehash: d6d3b4a2086be28fbfa2bf200acef9b13b7b7825
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954716"
---
# <a name="dsc-environment-resource"></a>Ressource Environment DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource **Environment** dans DSC Windows PowerShell fournit un mécanisme permettant de gérer les variables d’environnement système.

## <a name="syntax"></a>Syntaxe

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Name |Spécifie le nom de la variable d’environnement pour laquelle vous voulez garantir un état spécifique. |
|Path |Définit la variable d’environnement actuellement configurée. Définissez cette propriété sur `$true` si la variable est une variable **Path** ; sinon, affectez-lui la valeur `$false`. Par défaut, il s’agit de `$false`. Si la variable actuellement configurée est une variable **Path**, la valeur fournie par la propriété **Value** est adjointe à la valeur existante. |
|Valeur |Valeur à attribuer à la variable d’environnement. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indique si une variable existe. Définissez cette propriété sur **Present** pour créer la variable d’environnement s’il n’en existe pas ou pour vérifier que sa valeur correspond à celle fournie par la propriété **Value** si la variable existe déjà. Affectez-lui la valeur **Absent** pour supprimer la variable, si elle existe. |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Exemple

L’exemple suivant vérifie que TestEnvironmentVariable est présent et que sa valeur est _TestValue_. S’il n’est pas présent, il le crée.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```