---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource Environment DSC
ms.openlocfilehash: 023ecf4cc2e3f553770d9c49a94b6e903e560b01
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-environment-resource"></a>Ressource Environment DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource __Environment__ dans DSC Windows PowerShell fournit un mécanisme permettant de gérer les variables d’environnement système.

## <a name="syntax"></a>Syntaxe
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   |
|---|---|
| Name| Spécifie le nom de la variable d’environnement pour laquelle vous voulez garantir un état spécifique.|
| Ensure| Indique si une variable existe. Définissez cette propriété sur __Present__ pour créer la variable d’environnement s’il n’en existe pas ou pour vérifier que sa valeur correspond à celle fournie par la propriété __Value__ si la variable existe déjà. Affectez-lui la valeur __Absent__ pour supprimer la variable, si elle existe.|
| Path| Définit la variable d’environnement actuellement configurée. Définissez cette propriété sur __$true__ si la variable est une variable __Path__ ; sinon, affectez-lui la valeur __$false__. La valeur par défaut est __$false__. Si la variable actuellement configurée est une variable __Path__, la valeur fournie par la propriété __Value__ est adjointe à la valeur existante.|
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID __ResourceName__ et le type __ResourceType__, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.|
| Valeur| Valeur à attribuer à la variable d’environnement.|

## <a name="example"></a>Exemple

L’exemple suivant vérifie que __TestEnvironmentVariable__ est présent et que sa valeur est __TestValue__. S’il n’est pas présent, il le crée.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```