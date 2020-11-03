---
description: FileSystem
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur FileSystem
ms.openlocfilehash: 3b37f6e4eb53ef7291c30cbc9820caf83641a9bb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208033"
---
# <a name="filesystem-provider"></a>Fournisseur FileSystem

## <a name="provider-name"></a>Nom du fournisseur

FileSystem

## <a name="drives"></a>Lecteurs

`C:`, `D:` ...

## <a name="capabilities"></a>Fonctionnalités

**Filtre** , **ShouldProcess**

## <a name="short-description"></a>Description courte

Fournit l'accès aux fichiers et aux répertoires.

## <a name="detailed-description"></a>Description détaillée

Le fournisseur **FileSystem** de PowerShell vous permet d’acquérir, d’ajouter, de modifier, d’effacer et de supprimer des fichiers et des répertoires dans PowerShell.

Les lecteurs de **système de fichiers** sont un espace de noms hiérarchique contenant les répertoires et les fichiers sur votre ordinateur. Un lecteur de **système de fichiers** peut être un lecteur logique ou physiques, un répertoire ou un partage réseau mappé.

Le fournisseur **FileSystem** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Get-Acl](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-Acl](xref:Microsoft.PowerShell.Security.Set-Acl)
- [Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a>Types exposés par ce fournisseur

Les fichiers sont des instances de la classe [System. IO. FileInfo](/dotnet/api/system.io.fileinfo) .  Les répertoires sont des instances de la classe [System. IO. DirectoryInfo](/dotnet/api/system.io.directoryinfo) .

## <a name="navigating-the-filesystem-drives"></a>Navigation dans les lecteurs de système de fichiers

Le fournisseur **FileSystem** expose ses magasins de données en mappant les lecteurs logiques de l’ordinateur en tant que lecteurs PowerShell. Pour utiliser un lecteur de **système de fichiers** , vous pouvez modifier votre emplacement sur un lecteur autorités le nom de lecteur suivi d’un signe deux-points ( `:` ).

```powershell
Set-Location C:
```

Vous pouvez également utiliser le fournisseur **FileSystem** à partir de n’importe quel autre lecteur PowerShell. Pour faire référence à un fichier ou à un répertoire à partir d’un autre emplacement, utilisez le nom du lecteur ( `C:` , `D:` ,...) dans le chemin d’accès.

> [!NOTE]
> PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs. Les commandes telles que `dir` et `ls` sont maintenant des alias pour l’expression [« obtenir-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location). et `pwd` est un alias pour la récupération de l' [emplacement](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="getting-files-and-directories"></a>Obtention de fichiers et de répertoires

L' `Get-ChildItem` applet de commande retourne tous les fichiers et répertoires à l’emplacement actuel. Vous pouvez spécifier un autre chemin d’accès pour rechercher et utiliser des paramètres intégrés pour filtrer et contrôler la profondeur de récursivité.

```powershell
Get-ChildItem
```

Pour en savoir plus sur l’utilisation des applets de commande, consultez la page [obtenir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).

## <a name="copying-files-and-directories"></a>Copie de fichiers et de répertoires

L' `Copy-Item` applet de commande copie les fichiers et les répertoires vers un emplacement que vous spécifiez.
Les paramètres sont disponibles pour filtrer et recurse, comme dans `Get-ChildItem` .

La commande suivante copie tous les fichiers et répertoires sous le chemin d’accès « C:\temp \" dans le dossier «C:\Windows\Temp ».

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

`Copy-Item` remplace les fichiers dans le répertoire de destination sans demander confirmation.

Cette commande copie le `a.txt` fichier du `C:\a` répertoire vers le `C:\a\bb` répertoire.

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

Copie tous les répertoires et fichiers du `C:\a` répertoire dans le `C:\c` répertoire. Si un ou plusieurs des répertoires à copier existent déjà dans le répertoire de destination, la commande échoue, sauf si vous spécifiez le paramètre Force.

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

Pour plus d’informations, consultez [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item).

## <a name="moving-files-and-directories"></a>Déplacement de fichiers et de répertoires

Cette commande déplace le `c.txt` fichier du `C:\a` répertoire vers le `C:\a\aa` répertoire :

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

La commande ne remplacera pas automatiquement un fichier existant qui porte le même nom. Pour forcer l'applet de commande à remplacer un fichier existant, spécifiez le paramètre Force.

Vous ne pouvez pas déplacer un répertoire quand ce répertoire est l'emplacement actif. Lorsque vous utilisez `Move-Item` pour déplacer le répertoire à l’emplacement actuel, vous voyez cette erreur.

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a>Gestion du contenu des fichiers

### <a name="get-the-content-of-a-file"></a>Obtenir le contenu d’un fichier

Cette commande obtient le contenu du fichier « Test.txt » et les affiche dans la console.

```powershell
Get-Content -Path Test.txt
```

Vous pouvez diriger le contenu du fichier vers une autre applet de commande. Par exemple, la commande suivante lit le contenu du `Test.txt` fichier, puis les fournit comme entrée à l’applet de commande [ConvertTo-HTML](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) :

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

Vous pouvez également récupérer le contenu d’un fichier en préfixant son chemin d’accès de fournisseur avec le signe dollar ( `$` ). Le chemin d’accès doit être placé entre accolades en raison de restrictions de nom de variable. Pour plus d’informations, consultez [about_Variables](about_Variables.md).

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a>Ajouter du contenu à un fichier

Cette commande ajoute la chaîne « test content » au `Test.txt` fichier :

```powershell
Add-Content -Path test.txt -Value "test content"
```

Le contenu existant dans le `Test.txt` fichier n’est pas supprimé.

### <a name="replace-the-content-of-a-file"></a>Remplacer le contenu d’un fichier

Cette commande remplace le contenu du `Test.txt` fichier par la chaîne « test content » :

```powershell
Set-Content -Path test.txt -Value "test content"
```

Elle remplace le contenu de `Test.txt` . Vous pouvez utiliser le paramètre **value** de l’applet de [commande New-Item](xref:Microsoft.PowerShell.Management.New-Item) pour ajouter du contenu à un fichier lorsque vous le créez.

### <a name="loop-through-the-contents-of-a-file"></a>Parcourir le contenu d’un fichier

Par défaut, l' `Get-Content` applet de commande utilise le caractère de fin de ligne comme délimiteur, de sorte qu’elle obtient un fichier sous la forme d’une collection de chaînes, chaque ligne étant une chaîne dans le fichier.

Vous pouvez utiliser le `-Delimiter` paramètre pour spécifier un autre délimiteur. Si vous choisissez pour ce paramètre les caractères qui indiquent la fin d'une section ou le début de la section suivante, vous pouvez fractionner le fichier en parties logiques.

La première commande obtient le `Employees.txt` fichier et le fractionne en sections, chacune d’elles se terminant par les mots « end of Employee record » et l’enregistre dans la `$e` variable.

La deuxième commande utilise la notation de tableau pour récupérer le premier élément de la collection dans `$e` . Elle utilise un index de 0, car les tableaux PowerShell sont de base zéro.

Pour plus d’informations sur `Get-Content` l’applet de commande, consultez la rubrique d’aide relative à la commande [obtenir-content](xref:Microsoft.PowerShell.Management.Get-Content).

Pour plus d’informations sur les tableaux, consultez [about_Arrays](../About/about_Arrays.md).

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a>Gestion des descripteurs de sécurité

### <a name="view-the-acl-for-a-file"></a>Afficher la liste de contrôle d’accès pour un fichier

Cette commande retourne un objet [System. Security. AccessControl. FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) :

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

Pour plus d’informations sur cet objet, dirigez la commande vers l’applet de commande d' [extraction de membre](xref:Microsoft.PowerShell.Utility.Get-Member) . Ou consultez « classe[FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) » dans la bibliothèque MSDN (Microsoft Developer Network).

### <a name="modify-the-acl-for-a-file"></a>Modifier la liste de contrôle d’accès d’un fichier

### <a name="create-and-set-an-acl-for-a-file"></a>Créer et définir une liste de contrôle d’accès pour un fichier

## <a name="creating-files-and-directories"></a>Création de fichiers et de répertoires

### <a name="create-a-directory"></a>Créer un répertoire

Cette commande crée le `logfiles` répertoire sur le `C` lecteur :

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

PowerShell comprend également une `mkdir` fonction (alias `md` ) qui utilise l’applet de [commande New-Item](xref:Microsoft.PowerShell.Management.New-Item) pour créer un nouveau répertoire.

### <a name="create-a-file"></a>Créer un fichier

Cette commande crée le `log2.txt` fichier dans le `C:\logfiles` répertoire, puis ajoute la chaîne « test log » au fichier :

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a>Créez un fichier avec du contenu

Crée un fichier appelé `log2.txt` dans le `C:\logfiles` répertoire et ajoute la chaîne « test log » au fichier.

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a>Attribution d’un nouveau nom aux fichiers et répertoires

### <a name="rename-a-file"></a>Renommer un fichier

Cette commande renomme le `a.txt` fichier dans le `C:\a` répertoire en `b.txt` :

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a>Renommer un répertoire

Cette commande renomme le `C:\a\cc` répertoire en `C:\a\dd` :

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a>Suppression de fichiers et de répertoires

### <a name="delete-a-file"></a>Supprimer un fichier

Cette commande supprime le `Test.txt` fichier dans le répertoire actif :

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a>Supprimer des fichiers à l’aide de caractères génériques

Cette commande supprime tous les fichiers du répertoire actif qui ont l’extension de `.xml` nom de fichier :

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a>Démarrage d’un programme en appelant un fichier associé

### <a name="invoke-a-file"></a>Appeler un fichier

La première commande utilise l’applet de commande [obtenir-service](xref:Microsoft.PowerShell.Management.Get-Service) pour obtenir des informations sur les services locaux.

Il dirige les informations vers l’applet de commande [Export-CSV](xref:Microsoft.PowerShell.Utility.Export-Csv) , puis stocke ces informations dans le `Services.csv` fichier.

La deuxième commande utilise [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item) pour ouvrir le `services.csv` fichier dans le programme associé à l' `.csv` extension :

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a>Obtention de fichiers et de dossiers avec des attributs spécifiés

### <a name="get-system-files"></a>Récupération des fichiers système

Cette commande obtient les fichiers système du répertoire actif et de ses sous-répertoires.

Elle utilise le `-File` paramètre pour récupérer uniquement des fichiers (et non des répertoires) et le `-System` paramètre pour récupérer uniquement les éléments avec l’attribut « System ».

Elle utilise le `-Recurse` paramètre pour récupérer les éléments dans le répertoire actif et tous les sous-répertoires.

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a>Récupérer les fichiers masqués

Cette commande obtient tous les fichiers du répertoire actif, y compris les fichiers cachés.

Elle utilise le paramètre **attributes** avec deux valeurs, `!Directory+Hidden` , qui obtient les fichiers masqués, et `!Directory` , qui obtient tous les autres fichiers.

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

`dir -att !d,!d+h` est l’équivalent de cette commande.

### <a name="get-compressed-and-encrypted-files"></a>Recevoir des fichiers compressés et chiffrés

Cette commande obtient les fichiers du répertoire actif qui sont compressés ou chiffrés.

Elle utilise le `-Attributes` paramètre avec deux valeurs, `Compressed` et `Encrypted` . Les valeurs sont séparées par une virgule `,` qui représente l’opérateur « or ».

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a>Paramètres dynamiques

Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés par un fournisseur PowerShell et sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur activé par le fournisseur.

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a>Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\>

Spécifie l'encodage du fichier. La valeur par défaut est ASCII.

- **ASCII** : utilise l’encodage pour le jeu de caractères ASCII (7 bits).
- **BigEndianUnicode** : encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).
- **String** : utilise le type d’encodage pour une chaîne.
- **Unicode** : encode au format UTF-16 à l’aide de l’ordre d’octet avec primauté des octets de poids faible (Little-endian).
- **UTF7** : encode au format UTF-7.
- **UTF8** : encode au format UTF-8.
- **UTF8BOM** : encode au format UTF-8 avec marque d’ordre d’octet (BOM)
- **UF8NOBOM** : encode au format UTF-8 sans marque d’ordre d’octet (BOM)
- **UTF32** : encode au format UTF-32.
- **Default** : encode dans la page de codes installée par défaut.
- **OEM** : utilise l’encodage par défaut pour les programmes MS-DOS et console.
- **Inconnu** : le type d’encodage est inconnu ou non valide. Les données peuvent être traitées sous forme binaire.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Add-Content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a>Delimiter \<System.String\>

Spécifie le délimiteur utilisé par [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) pour diviser le fichier en objets lors de la lecture.

La valeur par défaut est `\n` , le caractère de fin de ligne.

Lors de la lecture d’un fichier texte, la méthode [obten-content](xref:Microsoft.PowerShell.Management.Get-Content) retourne une collection d’objets String, dont chacun se termine par le caractère délimiteur.

Si vous entrez un délimiteur qui n’existe pas dans le fichier, la fonctionnalité [obtenir-content](xref:Microsoft.PowerShell.Management.Get-Content) retourne l’intégralité du fichier sous la forme d’un objet unique, non délimité.

Vous pouvez utiliser ce paramètre pour fractionner un fichier volumineux en fichiers plus petits, en spécifiant un séparateur de fichier comme « Fin de l'exemple » comme délimiteur. Le délimiteur est conservé (il n'est pas supprimé) et devient le dernier élément de chaque section du fichier.

> [!NOTE]
> Actuellement, lorsque la valeur du `-Delimiter` paramètre est une chaîne vide, la valeur de l’opération [obtenir-content](xref:Microsoft.PowerShell.Management.Get-Content) ne retourne rien.
> Il s'agit d'un problème connu. Pour forcer [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) à retourner la totalité du fichier sous la forme d'une seule chaîne non délimitée, entrez une valeur qui n'existe pas dans le fichier.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a>Wait \<System.Management.Automation.SwitchParameter\>

Attend que le contenu soit ajouté au fichier. Si le contenu est ajouté, il retourne le contenu ajouté. Si le contenu a changé, il retourne la totalité du fichier.

Lors de l'attente, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) vérifie le fichier une fois par seconde jusqu'à ce que vous interrompiez l'attente, par exemple en appuyant sur Ctrl+C.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a>Attributes \<FlagsExpression\>

Obtient les fichiers et les dossiers avec les attributs spécifiés. Ce paramètre prend en charge tous les attributs et vous permet de spécifier des combinaisons complexes d'attributs.

Le `-Attributes` paramètre a été introduit dans Windows PowerShell 3,0.

Le `-Attributes` paramètre prend en charge les attributs suivants :

- **Archive**
- **Compressed**
- **Appareil**
- **Directory**
- **Chiffré**
- **Hidden**
- **Normal**
- **NotContentIndexed**
- **Hors connexion**
- **Lecture seule**
- **ReparsePoint**
- **SparseFile**
- **Système**
- **Temporaire**

Pour obtenir une description de ces attributs, consultez l’énumération [FileAttributes](/dotnet/api/system.io.fileattributes) .

Utilisez les opérateurs suivants pour combiner des attributs.

- `!` -NON
- `+` -ET
- `,` -OU

Les espaces ne sont pas autorisés entre un opérateur et son attribut. Les espaces sont cependant autorisés devant les virgules.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a>Directory \<System.Management.Automation.SwitchParameter\>

Obtient les répertoires (dossiers).

Le `-Directory` paramètre a été introduit dans Windows PowerShell 3,0.

Pour accéder uniquement aux répertoires, utilisez le `-Directory` paramètre et omettez le `-File` paramètre. Pour exclure des répertoires, utilisez le `-File` paramètre et omettez le `-Directory` paramètre, ou utilisez le `-Attributes` paramètre.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a>File \<System.Management.Automation.SwitchParameter\>

Obtient les fichiers.

Le `-File` paramètre a été introduit dans Windows PowerShell 3,0.

Pour récupérer uniquement des fichiers, utilisez le `-File` paramètre et omettez le `-Directory` paramètre. Pour exclure des fichiers, utilisez le `-Directory` paramètre et omettez le paramètre `-File` , ou utilisez le `-Attributes` paramètre.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a>Hidden \<System.Management.Automation.SwitchParameter\>

Obtient uniquement les fichiers et les répertoires (dossiers) cachés. Par défaut, l’option [obtenir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) obtient uniquement les éléments non masqués.

Le `-Hidden` paramètre a été introduit dans Windows PowerShell 3,0.

Pour récupérer uniquement les éléments masqués, utilisez le `-Hidden` paramètre, ses `h` `ah` alias ou, ou la valeur **masquée** du `-Attributes` paramètre. Pour exclure les éléments masqués, omettez le `-Hidden` paramètre ou utilisez le `-Attributes` paramètre.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a>ReadOnly \<System.Management.Automation.SwitchParameter\>

Obtient uniquement les fichiers et les répertoires (dossiers) en lecture seule.

Le `-ReadOnly` paramètre a été introduit dans Windows PowerShell 3,0.

Pour obtenir uniquement les éléments en lecture seule, utilisez le `-ReadOnly` paramètre, son `ar` alias ou la valeur **ReadOnly** du `-Attributes` paramètre. Pour exclure les éléments en lecture seule, utilisez le `-Attributes` paramètre.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a>System \<System.Management.Automation.SwitchParameter\>

Obtient uniquement les fichiers et les répertoires (dossiers) système.

Le `-System` paramètre a été introduit dans Windows PowerShell 3,0.

Pour récupérer uniquement les fichiers et dossiers système, utilisez le `-System` paramètre, son `as` alias ou la valeur **système** du `-Attributes` paramètre. Pour exclure des fichiers et des dossiers système, utilisez le `-Attributes` paramètre.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a>NewerThan \<System.DateTime\>

Retourne `$True` lorsque la `LastWriteTime` valeur d’un fichier est supérieure à la date spécifiée. Sinon, il retourne `$False`.

Entrez un objet [DateTime](/dotnet/api/system.datetime) , tel que celui retourné par l’applet de commande [obtenir-date](xref:Microsoft.PowerShell.Utility.Get-Date) , ou une chaîne qui peut être convertie en un objet [DateTime](/dotnet/api/system.datetime) , tel que `"August 10, 2011 2:00 PM"` .

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Test-Path](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a>OlderThan \<System.DateTime\>

Retourne `$True` lorsque la `LastWriteTime` valeur d’un fichier est inférieure à la date spécifiée. Sinon, il retourne `$False`.

Entrez un objet [DateTime](/dotnet/api/system.datetime) , tel que celui retourné par l’applet de commande [obtenir-date](xref:Microsoft.PowerShell.Utility.Get-Date) , ou une chaîne qui peut être convertie en un objet [DateTime](/dotnet/api/system.datetime) , tel que `"August 10, 2011 2:00 PM"` .

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Test-Path](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a>Stream \<System.String\>

Gère les flux de données alternatifs. Entrez le nom du flux. Les caractères génériques sont autorisés uniquement dans les commandes [obtenir un élément](xref:Microsoft.PowerShell.Management.Get-Item) pour et [supprimer un élément](xref:Microsoft.PowerShell.Management.Remove-Item) dans un lecteur du système de fichiers.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Add-Content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Clear-Content](xref:Microsoft.PowerShell.Management.Clear-Content)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a>Raw \<SwitchParameter\>

Ignore les caractères de nouvelle ligne. Retourne le contenu sous la forme d'un seul élément.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a>ItemType \<String\>

Ce paramètre vous permet de spécifier le Tye d’élément à créer avec `New-Item`

Les valeurs disponibles de ce paramètre dépendent du fournisseur actuel que vous utilisez.

Dans un `FileSystem` lecteur, les valeurs suivantes sont autorisées :

- Fichier
- Répertoire
- SymbolicLink
- jonction
- HardLink

### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a>Utilisation du pipeline

Les applets de commande du fournisseur acceptent l’entrée du pipeline. Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur.
Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.

## <a name="getting-help"></a>Obtenir de l’aide

Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.

Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) dans un lecteur du système de fichiers ou utilisez le `-Path` paramètre de la commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) pour spécifier un lecteur du système de fichiers.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a>Voir aussi

[about_Providers](../About/about_Providers.md)
