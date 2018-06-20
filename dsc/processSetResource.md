---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressources ProcessSet dans DSC
ms.openlocfilehash: 412cf1076996126f0d9b7a9a8ebbc9bdb7ecf377
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189922"
---
# <a name="dsc-windowsprocess-resource"></a>Ressource WindowsProcess dans DSC

> S’applique à : Windows PowerShell 5.0

La ressource **ProcessSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour configurer des processus sur un nœud cible. Cette ressource est une [ressource composite](authoringResourceComposite.md) qui appelle la ressource [WindowsProcess](windowsProcessResource.md) pour chaque groupe spécifié dans le paramètre `GroupName`.

## <a name="syntax"></a>Syntaxe

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propriétés
|  Propriété  |  Description   |
|---|---|
| Arguments| Chaîne qui contient les arguments à passer au processus en l’état. Si vous devez passer plusieurs arguments, placez-les dans cette chaîne.|
| Path| Chemins vers les exécutables du processus. S’il s’agit des noms des fichiers exécutables (et non des chemins qualifiés complets), la ressource DSC recherche la variable d’environnement **Path** (`$env:Path`) pour rechercher les fichiers. Si les valeurs de cette propriété sont des chemins qualifiés complets, DSC n’utilise pas la variable d’environnement **Path** pour rechercher les fichiers et génère une erreur si l’un des chemins n’existe pas. Les chemins relatifs ne sont pas autorisés.|
| Credential| Indique les informations d’identification pour démarrer le processus.|
| Ensure| Spécifie si les processus existent. Définissez cette propriété sur « Present » pour vous assurer que le package existe. Sinon, donnez-lui la valeur « Absent ». La valeur par défaut est Present.|
| StandardErrorPath| Chemin où les processus écrivent l’erreur standard. Tout fichier existant est remplacé.|
| StandardInputPath| Flux à partir duquel le processus reçoit l’entrée standard.|
| StandardOutputPath| Chemin du fichier où les processus écrivent la sortie standard. Tout fichier existant est remplacé.|
| WorkingDirectory| Emplacement utilisé comme répertoire de travail actuel pour les processus.|
| DependsOn | Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID **ResourceName** et le type **_ResourceType**, utilisez la syntaxe suivante pour cette propriété : DependsOn = "[ResourceType]ResourceName"|