---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource Archive DSC
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047313"
---
# <a name="dsc-archive-resource"></a>Ressource Archive DSC

> S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource Archive de la configuration d’état souhaité (DSC) de Windows PowerShell fournit un mécanisme permettant de décompresser les fichiers d’archive (.zip) à un emplacement spécifique.

## <a name="syntax"></a>Syntaxe
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   |
|---|---|
| Destination| Spécifie l’emplacement où le contenu de l’archive doit être extrait.|
| Path| Spécifie le chemin source du fichier d’archive.|
| __Checksum__| Définit le type à utiliser pour déterminer si deux fichiers sont identiques. Si __Checksum__ n’est pas spécifié, seul le nom du fichier ou du répertoire est utilisé pour la comparaison. Les valeurs valides sont les suivantes : SHA-1, SHA-256, SHA-512, createdDate, modifiedDate et none (valeur par défaut). Si vous spécifiez __Checksum__ sans __Validate__, la configuration échoue.|
| Ensure| Détermine s’il faut vérifier que le contenu de l’archive se trouve à la __Destination__ donnée. Définissez cette propriété sur __Present__ pour vous assurer que le contenu se trouve à l’emplacement donné. Définissez la propriété sur __Absent__ pour vous assurer que le contenu ne se trouve pas à l’emplacement donné. La valeur par défaut est __Present__.|
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si l’ID du bloc de script de configuration de ressource que vous voulez exécuter en premier est ResourceName et son type est __ResourceType__, la syntaxe de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.|
| Validate| Utilise la propriété Checksum pour déterminer si l’archive correspond à la signature. Si vous spécifiez Checksum sans Validate, la configuration échoue. Si vous spécifiez Validate sans Checksum, une somme de contrôle SHA-256 est utilisée par défaut.|
| Force| Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire non vide) entraînent une erreur. La propriété Force permet d’ignorer ces erreurs. La valeur par défaut est False.|

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la ressource Archive pour vous assurer que le contenu d’un fichier d’archive appelé Test.zip existe et qu’il est extrait à une destination donnée.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```