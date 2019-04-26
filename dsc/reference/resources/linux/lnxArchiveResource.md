---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource nxArchive dans DSC pour Linux
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078042"
---
# <a name="dsc-for-linux-nxarchive-resource"></a>Ressource nxArchive dans DSC pour Linux

La ressource **nxArchive** de la configuration d’état souhaité (DSC) de Windows PowerShell fournit un mécanisme permettant de décompresser les fichiers d’archive (.zip) à un emplacement spécifique d’un nœud Linux.

## <a name="syntax"></a>Syntaxe

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Propriétés

|  Propriété |  Description |
|---|---|
| SourcePath| Spécifie le chemin source du fichier d’archive. Ce fichier doit être au format .tar, .zip ou .tar.gz. |
| DestinationPath| Spécifie l’emplacement où le contenu de l’archive doit être extrait.|
| Somme de contrôle| Définit le type à utiliser pour déterminer si l’archive source a été mise à jour. Les valeurs sont « ctime », « mtime » et « md5 ». La valeur par défaut est « md5 ».|
| Force| Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire non vide) entraînent une erreur. La propriété **Force** permet d’ignorer ces erreurs. La valeur par défaut est **$false**.|
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.|
| Ensure| Détermine s’il faut vérifier que le contenu de l’archive se trouve à la **Destination** donnée. Définissez cette propriété sur Present pour vous assurer que le contenu se trouve à l’emplacement donné. Définissez la propriété sur Absent pour vous assurer que le contenu ne se trouve pas à l’emplacement donné. La valeur par défaut est « Present ».|

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la ressource **nxArchive** pour vous assurer que le contenu d’un fichier d’archive appelé `website.tar` existe et qu’il est extrait à une destination donnée.

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```