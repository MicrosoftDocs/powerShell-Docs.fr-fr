---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource nxFile dans DSC pour Linux
ms.openlocfilehash: e4916414e4de29ab15d9c82c492671ebc16d5412
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxfile-resource"></a>Ressource nxFile dans DSC pour Linux

La ressource **nxFile** dans DSC PowerShell fournit un mécanisme permettant de gérer les fichiers et les répertoires sur un nœud Linux.

## <a name="syntax"></a>Syntaxe

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriétés

|  Propriété |  Description | 
|---|---|
| DestinationPath| Spécifie l’emplacement d’un fichier ou d’un répertoire dont vous voulez garantir l’état.| 
| SourcePath| Spécifie le chemin à partir duquel copier la ressource de fichier ou de dossier. Ce chemin peut être un chemin local ou une URL `http/https/ftp`. Les URL `http/https/ftp` distantes sont uniquement prises en charge quand la valeur de la propriété **Type** est File.| 
| Ensure| Détermine si l’existence du fichier doit être vérifiée. Définissez cette propriété sur « Present » pour vous assurer que le fichier existe. Définissez la propriété sur « Absent » pour vous assurer que le fichier n’existe pas. La valeur par défaut est « Present ».| 
| Type| Spécifie si la ressource actuellement configurée est un répertoire ou un fichier. Définissez cette propriété sur Directory pour indiquer que la ressource est un répertoire. Affectez-lui la valeur File pour indiquer que la ressource est un fichier. La valeur par défaut est File.| 
| Contents| Spécifie le contenu d’un fichier, tel qu’une chaîne spécifique.| 
| Checksum| Définit le type à utiliser pour déterminer si deux fichiers sont identiques. Si **Checksum** n’est pas spécifié, seul le nom du fichier ou du répertoire est utilisé pour la comparaison. Les valeurs sont « ctime », « mtime » et « md5 ».| 
| Recurse| Indique si des sous-répertoires sont inclus. Définissez cette propriété sur **$true** pour indiquer que vous voulez inclure des sous-répertoires. La valeur par défaut est **$false**. **Remarque** : Cette propriété est valide uniquement quand la propriété **Type** est définie sur Directory.| 
| Force| Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire non vide) entraînent une erreur. La propriété **Force** permet d’ignorer ces erreurs. La valeur par défaut est **$false**.| 
| Links| Spécifie le comportement souhaité pour les liens symboliques. Définissez cette propriété sur Follow pour suivre les liens symboliques et agir sur la cible des liens (par exemple, pour copier le fichier au lieu du lien). Définissez cette propriété sur Manage pour agir sur le lien (par exemple, pour copier le lien). Définissez cette propriété sur Ignore pour ignorer les liens symboliques.| 
| Group| Nom du **groupe** qui possède le fichier ou le répertoire.| 
| Mode| Spécifie les autorisations souhaitées pour la ressource, en notation octale ou symbolique (par exemple, 777 ou rwxrwxrwx). Si vous utilisez la notation symbolique, n’entrez pas le premier caractère qui indique le répertoire ou le fichier.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="additional-information"></a>Informations supplémentaires


Linux et Windows utilisent des caractères de saut de ligne différents dans les fichiers texte par défaut, ce qui peut entraîner des résultats inattendus quand vous configurez des fichiers sur un ordinateur Linux avec __nxFile__. Il existe plusieurs manières de gérer le contenu d’un fichier Linux tout en évitant les problèmes provoqués par les caractères de saut de ligne inattendus :

Étape 1 - Copier le fichier à partir d’une source distante (http, https ou ftp) : créez un fichier sur Linux avec le contenu de votre choix et effectuez une copie intermédiaire vers un serveur web ou FTP accessible aux nœuds que vous allez configurer. Définissez la propriété __SourcePath__ de la ressource __nxFile__ sur l’URL web ou FTP du fichier.

```
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


Étape 2 : Lire le contenu du fichier de script PowerShell avec [Get-Content](https://technet.microsoft.com/en-us/library/hh849787.aspx) après avoir défini la propriété __$OFS__ pour utiliser le caractère de saut de ligne Linux.


```
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


Étape 3 : Utiliser une fonction PowerShell pour remplacer les sauts de ligne Windows par des caractères de saut de ligne Linux.

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
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

```
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
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
} 
}
```

