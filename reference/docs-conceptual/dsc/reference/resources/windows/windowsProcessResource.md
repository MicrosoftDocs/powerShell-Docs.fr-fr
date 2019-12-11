---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource WindowsProcess dans DSC
ms.openlocfilehash: e168cdebb04f7ec83b73a537a5f188299f40d8b7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952836"
---
# <a name="dsc-windowsprocess-resource"></a>Ressource WindowsProcess dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource **WindowsProcess** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour configurer des processus sur un nœud cible.

## <a name="syntax"></a>Syntaxe

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Arguments |Indique une chaîne d’arguments à passer au processus en l’état. Si vous devez passer plusieurs arguments, placez-les dans cette chaîne. |
|Path |Chemin de l’exécutable du processus. S’il s’agit du nom de fichier de l’exécutable (et non du chemin d’accès complet), la ressource DSC recherche la variable d’environnement `$env:Path` pour rechercher le fichier exécutable. Si la valeur de cette propriété est un chemin d’accès complet, DSC n’utilise pas la variable `$env:Path` pour rechercher le fichier et lève une erreur si le chemin n’existe pas. Les chemins relatifs ne sont pas autorisés. |
|Credential |Indique les informations d’identification pour démarrer le processus. |
|StandardErrorPath |Indique le chemin du répertoire dans lequel écrire l’erreur standard. Tout fichier existant est remplacé. |
|StandardInputPath |Indique l’emplacement d’entrée standard. |
|StandardOutputPath |Indique l’emplacement où écrire la sortie standard. Tout fichier existant est remplacé. |
|WorkingDirectory |Indique l’emplacement à utiliser comme répertoire de travail actuel pour le processus. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indique si le processus existe. Définissez cette propriété sur **Present** pour faire en sorte que le processus existe. Sinon, donnez-lui la valeur **Absent**. La valeur par défaut est **Present**. |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |