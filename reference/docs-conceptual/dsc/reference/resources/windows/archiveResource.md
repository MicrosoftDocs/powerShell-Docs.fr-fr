---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource Archive DSC
ms.openlocfilehash: 679de8b965304c149b10321e73e42b224f49ecc5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560370"
---
# <a name="dsc-archive-resource"></a>Ressource Archive DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource Archive de la configuration d’état souhaité (DSC) de Windows PowerShell fournit un mécanisme permettant de décompresser les fichiers d’archive (.zip) à un emplacement spécifique.

## <a name="syntax"></a>Syntaxe

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Destination |Spécifie l’emplacement où le contenu de l’archive doit être extrait. |
|Path |Spécifie le chemin source du fichier d’archive. |
|Somme de contrôle |Définit le type à utiliser pour déterminer si deux fichiers sont identiques. Si **Checksum** n’est pas spécifié, seul le nom du fichier ou du répertoire est utilisé pour la comparaison. Les valeurs valides sont les suivantes : **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**. Si vous spécifiez **Checksum** sans **Validate**, la configuration échoue. |
|Force |Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire non vide) entraînent une erreur. La propriété **Force** permet d’ignorer ces erreurs. La valeur par défaut est **False**. |
|Valider| Utilise la propriété **Checksum** pour déterminer si l’archive correspond à la signature. Si vous spécifiez **Checksum** sans **Validate**, la configuration échoue. Si vous spécifiez **Validate** sans **Checksum**, une **somme de contrôle** _SHA-256_ est utilisée par défaut. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Détermine s’il faut vérifier que le contenu de l’archive se trouve à la **Destination** donnée. Définissez cette propriété sur **Present** pour vous assurer que le contenu se trouve à l’emplacement donné. Définissez la propriété sur **Absent** pour vous assurer que le contenu ne se trouve pas à l’emplacement donné. La valeur par défaut est **Present**. |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la ressource Archive pour vérifier que le contenu d’un fichier d’archive appelé `Test.zip` existe et qu’il est extrait à une destination donnée.

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```
