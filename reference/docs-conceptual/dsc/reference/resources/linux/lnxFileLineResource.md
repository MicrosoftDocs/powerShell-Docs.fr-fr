---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource nxFileLine dans DSC pour Linux
ms.openlocfilehash: 2e94bab318b5db65df88d268a88585079bab89bf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953216"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>Ressource nxFileLine dans DSC pour Linux

La ressource **nxFileLine** de DSC (Desired State Configuration) PowerShell offre un mécanisme permettant de gérer les lignes d’un fichier de configuration sur un nœud Linux.

## <a name="syntax"></a>Syntaxe

```Syntax
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|FilePath |Le chemin complet du fichier dans lequel gérer les lignes se trouve sur le nœud cible. |
|ContainsLine |Une ligne à vérifier se trouve dans le fichier. Cette ligne est ajoutée au fichier si elle ne s’y trouve pas. **ContainsLine** est obligatoire, mais peut être défini sur une chaîne vide (`ContainsLine = ""`) s’il n’est pas nécessaire. |
|DoesNotContainPattern |Modèle d’expression régulière pour les lignes qui ne doivent pas se trouver dans le fichier. Les lignes du fichier qui correspondent à cette expression régulière seront supprimées du fichier. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |

## <a name="example"></a>Exemple

Cet exemple montre comment utiliser la ressource **nxFileLine** pour configurer le fichier `/etc/sudoers`, en s’assurant que l’utilisateur :monuser est configuré sur DoNotRequireTTY.

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = "/etc/sudoers"
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```