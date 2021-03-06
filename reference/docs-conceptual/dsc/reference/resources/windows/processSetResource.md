---
ms.date: 07/16/2020
ms.topic: reference
title: Ressources ProcessSet dans DSC
description: Ressources ProcessSet dans DSC
ms.openlocfilehash: 3e09c8c7b4ca7d8e95b36f9d4c20c2a85abad9dd
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142563"
---
# <a name="dsc-processset-resource"></a>Ressources ProcessSet dans DSC

> S’applique à : Windows PowerShell 5.x

La ressource **ProcessSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour configurer des processus sur un nœud cible.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntaxe

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Path |Chemin de l’exécutable du processus. S’il s’agit des noms des fichiers exécutables (et non des chemins d’accès complets), la ressource DSC recherche la variable d’environnement `$env:Path` pour rechercher les fichiers. Si les valeurs de cette propriété sont des chemins d’accès complets, DSC n’utilise pas la variable d’environnement `$env:Path` pour rechercher les fichiers et lève une erreur si l’un des chemins n’existe pas. Les chemins relatifs ne sont pas autorisés. |
|Informations d'identification |Indique les informations d’identification pour démarrer le processus. |
|StandardErrorPath |Chemin où les processus écrivent l’erreur standard. Tout fichier existant est remplacé. |
|StandardInputPath |Flux à partir duquel le processus reçoit l’entrée standard. |
|StandardOutputPath |Chemin du fichier où les processus écrivent la sortie standard. Tout fichier existant est remplacé. |
|WorkingDirectory |Emplacement utilisé comme répertoire de travail actuel pour les processus. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Spécifie si les processus existent. Définissez cette propriété sur **Present** pour faire en sorte que le processus existe. Sinon, donnez-lui la valeur **Absent** . La valeur par défaut est **Present** . |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).
