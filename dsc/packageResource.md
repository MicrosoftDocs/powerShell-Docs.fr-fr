---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource Package dans DSC
ms.openlocfilehash: 16f7f1b8fa7b84bcfdeb09fdc46db9c93113e70c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188528"
---
# <a name="dsc-package-resource"></a>Ressource Package dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource **Package** dans DSC Windows PowerShell fournit un mécanisme permettant d’installer ou de désinstaller des packages, tels que les packages Windows Installer et setup.exe, sur un nœud cible.

## <a name="syntax"></a>Syntaxe

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a>Propriétés
|  Propriété  |  Description   |
|---|---|
| Name| Indique le nom du package pour lequel vous souhaitez garantir un état spécifique.|
| Path| Indique le chemin où se trouve le package.|
| ProductId| Indique l’ID de produit qui identifie le package de manière unique.|
| Arguments| Chaîne d’arguments transmise telle quelle au package.|
| Credential| Informations d’identification permettant l’accès au package sur une source distante. Cette propriété n’est pas utilisée pour installer le package. Le package est toujours installé sur le système local.|
| Ensure| Indique si le package est installé. Définissez cette propriété sur « Absent » pour vous assurer que le package n’est pas installé (ou désinstallé, si le package n’est pas installé). Définissez cette propriété sur « Present » (valeur par défaut) pour vous assurer que le package est installé.|
| LogPath| Indique le chemin complet où vous souhaitez que le fournisseur enregistre un fichier journal pour installer ou désinstaller le package.|
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : DependsOn = "[ResourceType]ResourceName"|
| ReturnCode| Indique le code de retour attendu. Si le code de retour réel ne correspond pas à la valeur attendue indiquée ici, la configuration retourne une erreur.|

## <a name="example"></a>Exemple

Cet exemple exécute le programme d’installation .msi qui se trouve dans le chemin spécifié et qui possède l’ID de produit spécifié.

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```