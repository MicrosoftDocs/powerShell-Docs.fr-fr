---
ms.date: 07/17/2020
keywords: dsc,powershell,configuration,installation
title: Ressource nxFile dans DSC pour Linux
ms.openlocfilehash: 37de70fedce77161c97084d5ca7eaf8e1bce45d8
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463922"
---
# <a name="dsc-for-linux-nxfile-resource"></a>Ressource nxFile dans DSC pour Linux

La ressource **nxFile** dans DSC PowerShell fournit un mécanisme permettant de gérer les fichiers et les répertoires sur un nœud Linux.

## <a name="syntax"></a>Syntaxe

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|DestinationPath |Spécifie l’emplacement d’un fichier ou d’un répertoire dont vous voulez garantir l’état. |
|SourcePath |Spécifie le chemin à partir duquel copier la ressource de fichier ou de dossier. Ce chemin peut être un chemin local ou une URL `http/https/ftp`. Les URL `http/https/ftp` distantes sont uniquement prises en charge quand la valeur de la propriété **Type** est **file**. |
|Type |Spécifie si la ressource actuellement configurée est un répertoire ou un fichier. Définissez cette propriété sur **directory** pour indiquer que la ressource est un répertoire. Affectez-lui la valeur **file** pour indiquer que la ressource est un fichier. La valeur par défaut est **file**. |
|Contents |Spécifie le contenu d’un fichier, tel qu’une chaîne spécifique. |
|Somme de contrôle |Définit le type à utiliser pour déterminer si deux fichiers sont identiques. Si **Checksum** n’est pas spécifié, seul le nom du fichier ou du répertoire est utilisé pour la comparaison. Les valeurs sont **ctime**, **mtime** ou **md5**. |
|Recurse |Indique si des sous-répertoires sont inclus. Définissez cette propriété sur `$true` pour indiquer que vous voulez inclure des sous-répertoires. Par défaut, il s’agit de `$false`. Cette propriété est valide uniquement quand la propriété **Type** est définie sur **directory**. |
|Force |Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire non vide) entraînent une erreur. La propriété **Force** permet d’ignorer ces erreurs. La valeur par défaut est `$false`. |
|Liens |Spécifie le comportement souhaité pour les liens symboliques. Définissez cette propriété sur **follow** pour suivre les liens symboliques et agir sur la cible des liens. Par exemple, copiez le fichier au lieu du lien. Définissez cette propriété sur **manage** pour agir sur le lien. Par exemple, copiez le lien lui-même. Définissez cette propriété sur **ignore** pour ignorer les liens symboliques. |
|Groupe |Nom du **groupe** qui doit avoir les autorisations sur le fichier ou le répertoire. |
|Mode |Spécifie les autorisations souhaitées pour la ressource, en notation octale ou symbolique Par exemple, **777** ou **rwxrwxrwx**. Si vous utilisez la notation symbolique, n’entrez pas le premier caractère qui indique le répertoire ou le fichier. |
|Propriétaire |Nom du groupe qui possède le fichier ou le répertoire. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Détermine si l’existence du fichier doit être vérifiée. Définissez cette propriété sur **Present** pour garantir l’existence du fichier. Définissez la propriété sur **Absent** pour vous assurer que le fichier n’existe pas. La valeur par défaut est **Present**. |

## <a name="additional-information"></a>Informations supplémentaires

Linux et Windows utilisent des caractères de saut de ligne différents dans les fichiers texte par défaut, ce qui peut entraîner des résultats inattendus quand vous configurez des fichiers sur un ordinateur Linux avec **nxFile**. Il existe plusieurs manières de gérer le contenu d’un fichier Linux tout en évitant les problèmes provoqués par les caractères de saut de ligne inattendus :

1. Copier le fichier à partir d’une source distante (HTTP, HTTPS ou FTP)

   Créez un fichier sur Linux avec le contenu de votre choix et effectuez une copie intermédiaire vers un serveur web ou FTP accessible aux nœuds que vous allez configurer. Définissez la propriété **SourcePath** de la ressource **nxFile** sur l’URL web ou FTP du fichier.

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      nxFile resolvConf
      {
         SourcePath = "http://10.185.85.11/conf/resolv.conf"
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
      }
   }
   ```

1. Lire le contenu du fichier de script PowerShell avec [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) après avoir défini la propriété **$OFS** pour utiliser le caractère de saut de ligne Linux.

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      $OFS = "`n"
      $Contents = Get-Content C:\temp\resolv.conf

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = "$Contents"
      }
   }
   ```

1. utiliser une fonction PowerShell pour remplacer les sauts de ligne Windows par des caractères de saut de ligne Linux.

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
      Return $outputStr
   }

   Import-DSCResource -Module nx

   Node $Node
   {
      $Contents = @'
   search contoso.com
   domain contoso.com
   nameserver 10.185.85.11
   '@
       $Contents = LinuxString $Contents

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = $Contents
      }
   }
   ```

## <a name="example"></a>Exemple

L’exemple suivant vérifie que le répertoire `/opt/mydir` existe et qu’un fichier avec le contenu spécifié se trouve dans ce répertoire.

```powershell
Import-DSCResource -Module nx

Node $node {
    nxFile DirectoryExample
    {
        Ensure = "Present"
        DestinationPath = "/opt/mydir"
        Type = "Directory"
    }

    nxFile FileExample
    {
        Ensure = "Present"
        Destinationpath = "/opt/mydir/myfile"
        Contents=@"
#!/bin/bash`necho "hello world"`n
"@
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```
