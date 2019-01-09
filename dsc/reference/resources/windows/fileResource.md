---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource File DSC
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047402"
---
# <a name="dsc-file-resource"></a>Ressource File DSC

> S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource File dans DSC Windows PowerShell fournit un mécanisme permettant de gérer les fichiers et les dossiers sur un nœud cible.

>**Remarque :** Si la propriété **MatchSource** est définie sur **$false** (qui est la valeur par défaut), le contenu à copier est mis en cache la première fois que la configuration est appliquée.
>Les applications suivantes de la configuration ne recherchent pas les fichiers et/ou dossiers mis à jour dans le chemin spécifié par **SourcePath**. Si vous voulez rechercher les mises à jour des fichiers et/ou dossiers dans **SourcePath** chaque fois que la configuration est appliquée, affectez à **MatchSource** la valeur **$true**.

## <a name="syntax"></a>Syntaxe
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   |
|---|---|
| DestinationPath| Spécifie l’emplacement d’un fichier ou d’un répertoire dont vous voulez garantir l’état.|
| Attributes| Spécifie l’état souhaité des attributs du fichier ou du répertoire cible.|
| Checksum| Spécifie le type de somme de contrôle à utiliser pour déterminer si deux fichiers sont identiques. Si __Checksum__ n’est pas spécifié, seul le nom du fichier ou du répertoire est utilisé pour la comparaison. Les valeurs valides sont les suivantes : SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.|
| Contenu| Spécifie le contenu d’un fichier, tel qu’une chaîne spécifique.|
| Credential| Indique les informations d’identification qui sont nécessaires pour accéder aux ressources, telles que des fichiers sources, si ce type d’accès est nécessaire.|
| Ensure| Indique si le fichier ou le répertoire existe. Définissez cette propriété sur Absent pour vous assurer que le fichier ou le répertoire n’existe pas. Définissez cette propriété sur Present pour vous assurer que le fichier ou le répertoire existe. La valeur par défaut est Present.|
| Force| Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire non vide) entraînent une erreur. La propriété Force permet d’ignorer ces erreurs. La valeur par défaut est __$false__.|
| Recurse| Indique si des sous-répertoires sont inclus. Définissez cette propriété sur __$true__ pour indiquer que vous voulez inclure des sous-répertoires. La valeur par défaut est __$false__. **Remarque** : Cette propriété est valide uniquement lorsque la propriété de Type est définie sur Directory.|
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.|
| SourcePath| Indique le chemin à partir duquel copier la ressource de fichier ou de dossier.|
| Type| Indique si la ressource actuellement configurée est un répertoire ou un fichier. Définissez cette propriété sur Directory pour indiquer que la ressource est un répertoire. Affectez-lui la valeur File pour indiquer que la ressource est un fichier. La valeur par défaut est File.|
| MatchSource| Si la valeur par défaut __$false__ est définie, tous les fichiers de la source (par exemple, les fichiers A, B et C) sont ajoutés à la destination quand la configuration est appliquée pour la première fois. Si un nouveau fichier (D) est ajouté à la source, il n’est pas ajouté à la destination, même si la configuration est de nouveau appliquée plus tard. Si la valeur est __$true__, chaque fois que la configuration est appliquée, les nouveaux fichiers détectés par la suite sur la source (comme le fichier D de cet exemple) seront ajoutés à la destination. La valeur par défaut est **$false**.|

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la ressource File pour vérifier qu’un répertoire à l’emplacement `C:\Users\Public\Documents\DSCDemo\DemoSource` sur un ordinateur source (tel que le serveur collecteur) est également présent (ainsi que tous ses sous-répertoires) sur le nœud cible. Il écrit également un message de confirmation dans le journal une fois terminé, et ajoute une instruction pour garantir que l’opération de vérification des fichiers sera exécutée avant l’opération de journalisation.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```