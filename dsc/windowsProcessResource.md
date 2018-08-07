---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource WindowsProcess dans DSC
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267955"
---
# <a name="dsc-windowsprocess-resource"></a>Ressource WindowsProcess dans DSC

_S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0_

La ressource **WindowsProcess** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour configurer des processus sur un nœud cible.

## <a name="syntax"></a>Syntaxe

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a>Propriétés

| Propriété | Description |
| --- | --- |
| Arguments| Indique une chaîne d’arguments à passer au processus en l’état. Si vous devez passer plusieurs arguments, placez-les dans cette chaîne.|
| Path| Chemin de l’exécutable du processus. S’il s’agit du nom de fichier de l’exécutable (et non du chemin qualifié complet), la ressource DSC recherche la variable d’environnement **Path** (`$env:Path`) pour rechercher le fichier exécutable. Si la valeur de cette propriété est un chemin qualifié complet, DSC n’utilise pas la variable d’environnement **Path** pour rechercher le fichier et génère une erreur si le chemin n’existe pas. Les chemins relatifs ne sont pas autorisés.|
| Credential| Indique les informations d’identification pour démarrer le processus.|
| Ensure| Indique si le processus existe. Définissez cette propriété sur « Present » pour vous assurer que le package existe. Sinon, donnez-lui la valeur « Absent ». La valeur par défaut est « Present ».|
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous souhaitez exécuter en premier le bloc de script de configuration de ressource ayant l’ID **ResourceName** et le type **ResourceType**, la syntaxe à utiliser pour cette propriété est la suivante : `DependsOn = "[ResourceType]ResourceName"`.|
| StandardErrorPath| Indique le chemin du répertoire dans lequel écrire l’erreur standard. Tout fichier existant est remplacé.|
| StandardInputPath| Indique l’emplacement d’entrée standard.|
| StandardOutputPath| Indique l’emplacement où écrire la sortie standard. Tout fichier existant est remplacé.|
| WorkingDirectory| Indique l’emplacement à utiliser comme répertoire de travail actuel pour le processus.|