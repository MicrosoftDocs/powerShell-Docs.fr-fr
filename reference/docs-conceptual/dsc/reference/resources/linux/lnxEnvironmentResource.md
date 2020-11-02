---
ms.date: 07/17/2020
ms.topic: reference
title: Ressource nxEnvironment dans DSC pour Linux
description: Ressource nxEnvironment dans DSC pour Linux
ms.openlocfilehash: 86ed538732254967cb4a3bb55af4f6b179947e52
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644678"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>Ressource nxEnvironment dans DSC pour Linux

La ressource **nxEnvironment** de DSC (Desired State Configuration) PowerShell offre un mécanisme permettant de gérer les variables d’environnement système sur un nœud Linux.

## <a name="syntax"></a>Syntaxe

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Name |Spécifie le nom de la variable d’environnement pour laquelle vous voulez garantir un état spécifique. |
|Valeur |Valeur à attribuer à la variable d’environnement. |
|Path |Définit la variable d’environnement actuellement configurée. Définissez cette propriété sur `$true` si la variable est une variable **Path**  ; sinon, affectez-lui la valeur `$false`. Par défaut, il s’agit de `$false`. Si la variable actuellement configurée est une variable **Path** , la valeur fournie par la propriété **Value** est adjointe à la valeur existante. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Détermine si l’existence de la variable doit être vérifiée. Définissez cette propriété sur **Present** pour vous assurer que la variable existe. Définissez la propriété sur **Absent** pour vous assurer que la variable n’existe pas. La valeur par défaut est **Present** . |

## <a name="additional-information"></a>Informations supplémentaires

- Si **Path** est absent ou a la valeur `$false`, les variables d’environnement sont gérées dans `/etc/environment`.
  Vos programmes ou vos scripts peuvent nécessiter que la configuration « source » le fichier `/etc/environment` pour accéder aux variables d’environnement gérées.
- Si **Path** est défini sur `$true`, la variable d’environnement est gérée dans le fichier `/etc/profile.d/DSCenvironment.sh`. Ce fichier est créé s’il n’existe pas. Si **Ensure** est défini sur **Absent** et **Path** sur `$true`, une variable d’environnement existante est supprimée de `/etc/profile.d/DSCenvironment.sh`, mais pas des autres fichiers.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la ressource **nxEnvironment** pour s’assurer que **TestEnvironmentVariable** est présent et a la valeur Test-Value. Si **TestEnvironmentVariable** est absent, il est créé.

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
