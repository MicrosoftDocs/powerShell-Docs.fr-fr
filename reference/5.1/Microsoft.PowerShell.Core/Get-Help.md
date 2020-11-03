---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: a9a7aa7730d920bb78e0ae64daa50e5a28921163
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "93205789"
---
# Get-Help

## SYNOPSIS
Affiche des informations sur les commandes et les concepts PowerShell.

## SYNTAX

### AllUsersView (par défaut)

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [-Full] [<CommonParameters>]
```

### DetailedView

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Detailed [<CommonParameters>]
```

### Exemples

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Examples [<CommonParameters>]
```

### Paramètres

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Parameter <String> [<CommonParameters>]
```

### En ligne

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Online [<CommonParameters>]
```

### ShowWindow

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -ShowWindow [<CommonParameters>]
```

## Description

L' `Get-Help` applet de commande affiche des informations sur les concepts et les commandes PowerShell, y compris les applets de commande, les fonctions, les commandes Common Information Model (CIM), les flux de travail, les fournisseurs, les alias et les scripts.

Pour obtenir de l’aide pour une applet de commande PowerShell, tapez `Get-Help` suivi du nom de l’applet de commande, par exemple : `Get-Help Get-Process` .

Les articles d’aide conceptuelle dans PowerShell commencent par **about_** , comme **about_Comparison_Operators** . Pour afficher tous les articles **about_** , tapez `Get-Help about_*` . Pour afficher un article particulier, tapez `Get-Help about_<article-name>` , par exemple `Get-Help about_Comparison_Operators` .

Pour obtenir de l’aide pour un fournisseur PowerShell, tapez `Get-Help` suivi du nom du fournisseur. Par exemple, pour obtenir de l’aide pour le fournisseur de certificats, tapez `Get-Help Certificate` .

Vous pouvez également taper `help` ou `man` , qui affiche un écran de texte à la fois. Ou, `<cmdlet-name> -?` , qui est identique à `Get-Help` , mais fonctionne uniquement pour les applets de commande.

`Get-Help` Obtient le contenu de l’aide qu’il affiche à partir des fichiers d’aide sur votre ordinateur. Sans les fichiers d’aide, `Get-Help` affiche uniquement les informations de base sur les applets de commande. Certains modules PowerShell incluent des fichiers d’aide. À compter de PowerShell 3,0, les modules fournis avec le système d’exploitation Windows n’incluent pas les fichiers d’aide. Pour télécharger ou mettre à jour les fichiers d’aide d’un module dans PowerShell 3,0, utilisez l’applet de commande `Update-Help` .

Vous pouvez également consulter les documents d’aide PowerShell en ligne dans le Microsoft Docs. Pour obtenir la version en ligne d’un fichier d’aide, utilisez le paramètre **Online** , tel que : `Get-Help Get-Process -Online` . Pour lire toute la documentation PowerShell, consultez la [documentation Microsoft docs PowerShell](/powershell).

Si vous tapez `Get-Help` suivi du nom exact d’un article d’aide, ou d’un mot unique à un article d’aide, `Get-Help` affiche le contenu de l’article. Si vous spécifiez le nom exact d’un alias de commande, `Get-Help` affiche l’aide de la commande d’origine. Si vous entrez un mot ou un modèle de mot qui apparaît dans plusieurs titres d’articles d’aide, `Get-Help` affiche une liste des titres correspondants. Si vous entrez du texte qui n’apparaît pas dans les titres des articles d’aide, `Get-Help` affiche une liste d’articles qui contiennent ce texte dans leur contenu.

`Get-Help` peut obtenir des articles d’aide pour toutes les langues et paramètres régionaux pris en charge. `Get-Help` recherche d’abord les fichiers d’aide dans les paramètres régionaux définis pour Windows, puis dans les paramètres régionaux parents, par exemple **PT** pour **pt-br** , puis dans des paramètres régionaux de secours. À compter de PowerShell 3,0, si `Get-Help` ne trouve pas l’aide dans les paramètres régionaux de secours, il recherche des articles d’aide en anglais, en **-US** , avant de renvoyer un message d’erreur ou d’afficher l’aide générée automatiquement.

Pour plus d’informations sur les symboles qui `Get-Help` s’affichent dans le diagramme de syntaxe de commande, consultez [about_Command_Syntax](./About/about_Command_Syntax.md).
Pour plus d’informations sur les attributs de paramètres, tels que **Required** et **Position** , consultez [about_Parameters](./About/about_Parameters.md).

>[!NOTE]
> Dans PowerShell 3,0 et PowerShell 4,0, `Get-Help` les articles **About** ne peuvent pas être détectés dans les modules, sauf si le module est importé dans la session active. Il s'agit d'un problème connu. Pour obtenir des **informations sur** les articles d’un module, importez le module à l’aide de l’applet de commande `Import-Module` ou en exécutant une applet de commande incluse dans le module.

## EXEMPLES

### Exemple 1 : afficher les informations d’aide de base sur une applet de commande

Ces exemples affichent des informations d’aide de base sur l’applet de commande `Format-Table` .

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

`Get-Help <cmdlet-name>` est la syntaxe la plus simple et la syntaxe par défaut de l’applet de commande `Get-Help` . Vous pouvez omettre le paramètre **Name** .

La syntaxe `<cmdlet-name> -?` fonctionne uniquement pour les applets de commande.

### Exemple 2 : afficher les informations de base une page à la fois

Ces exemples affichent des informations d’aide de base sur l’applet de commande `Format-Table` , une page à la fois.

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

`help` est une fonction qui exécute `Get-Help` l’applet de commande en interne et affiche le résultat une page à la fois.

`man` alias de la `help` fonction.

`Get-Help Format-Table` envoie l’objet dans le pipeline. `Out-Host -Paging` reçoit la sortie du pipeline et l’affiche une page à la fois. Pour plus d’informations, consultez [Out-Host](Out-Host.md).

### Exemple 3 : afficher plus d’informations pour une applet de commande

Ces exemples affichent des informations d’aide plus détaillées sur l’applet de commande `Format-Table` .

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

Le paramètre **detailed** affiche la vue détaillée de l’article d’aide qui comprend des descriptions de paramètres et des exemples.

Le paramètre **Full** affiche la vue complète de l’article d’aide qui comprend des descriptions de paramètres, des exemples, des types d’objet d’entrée et de sortie, ainsi que des remarques supplémentaires.

Les paramètres **détaillés** et **complets** sont effectifs uniquement pour les commandes qui ont des fichiers d’aide installés sur l’ordinateur. Les paramètres ne sont pas efficaces pour les articles d’aide conceptuel ( **about_** ).

### Exemple 4 : afficher les parties sélectionnées d’une applet de commande à l’aide de paramètres

Ces exemples affichent les parties sélectionnées de l’aide de l’applet de commande `Format-Table` .

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

Le paramètre **exemples** affiche le **nom** et les sections **Synopsis** du fichier d’aide, ainsi que tous les exemples. Vous ne pouvez pas spécifier un exemple de nombre, car le paramètre d' **exemples** est un paramètre de commutateur.

Le **paramètre parameter affiche** uniquement les descriptions des paramètres spécifiés. Si vous spécifiez uniquement le `*` caractère générique astérisque (), il affiche les descriptions de tous les paramètres.
Quand le **paramètre** spécifie un nom de paramètre tel que **GroupBy** , les informations sur ce paramètre sont affichées.

Ces paramètres ne sont pas efficaces pour les articles d’aide conceptuel ( **about_** ).

### Exemple 5 : afficher la version en ligne de l’aide

Cet exemple affiche la version en ligne de l’article d’aide pour l’applet de commande `Format-Table` dans votre navigateur Web par défaut.

```powershell
Get-Help Format-Table -Online
```

### Exemple 6 : afficher de l’aide sur le système d’aide

L' `Get-Help` applet de commande sans paramètres affiche des informations sur le système d’aide PowerShell.

```powershell
Get-Help
```

### Exemple 7 : afficher les articles d’aide disponibles

Cet exemple affiche une liste de tous les articles d’aide disponibles sur votre ordinateur.

```powershell
Get-Help *
```

### Exemple 8 : afficher une liste d’articles conceptuels

Cet exemple affiche une liste des articles conceptuels inclus dans l’aide de PowerShell. Tous ces articles commencent par les caractères **about_** . Pour afficher un fichier d’aide particulier, tapez `Get-Help \<about_article-name\>` , par exemple, `Get-Help about_Signing` .

Seuls les articles conceptuels sur lesquels sont installés des fichiers d’aide sur votre ordinateur sont affichés. Pour plus d’informations sur le téléchargement et l’installation des fichiers d’aide dans PowerShell 3,0, consultez [Update-Help](Update-Help.md).

```powershell
Get-Help about_*
```

### Exemple 9 : Rechercher un mot dans l’aide sur les applets de commande

Cet exemple montre comment rechercher un mot dans l’article d’aide d’une applet de commande.

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

`Get-Help` utilise le paramètre **Full** pour obtenir des informations d’aide pour `Add-Member` . L’objet **MamlCommandHelpInfo** est envoyé vers le pipeline. `Out-String` utilise le paramètre **Stream** pour convertir l’objet en une chaîne. `Select-String` utilise le paramètre **pattern** pour rechercher **Clixml** dans la chaîne.

### Exemple 10 : afficher une liste d’articles incluant un mot

Cet exemple affiche une liste d’articles qui incluent le mot **Remoting** .

Lorsque vous entrez un mot qui n’apparaît pas dans un titre d’article, `Get-Help` affiche la liste des articles qui contiennent ce mot.

```powershell
Get-Help -Name remoting
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Install-PowerShellRemoting.ps1    External                            Install-PowerShellRemoting.ps1
Disable-PSRemoting                Cmdlet    Microsoft.PowerShell.Core Prevents remote users...
Enable-PSRemoting                 Cmdlet    Microsoft.PowerShell.Core Configures the computer...
```

### Exemple 11 : afficher l’aide spécifique au fournisseur

Cet exemple montre deux façons d’obtenir l’aide spécifique au fournisseur pour `Get-Item` . Ces commandes obtiennent de l’aide qui explique comment utiliser l' `Get-Item` applet de commande dans le nœud **DataCollection** du fournisseur de SQL Server PowerShell.

Le premier exemple utilise le `Get-Help` paramètre **path** pour spécifier le chemin d’accès du fournisseur SQL Server.
Étant donné que le chemin d’accès du fournisseur est spécifié, vous pouvez exécuter la commande à partir de n’importe quel emplacement de chemin d’accès.

Le deuxième exemple utilise `Set-Location` pour naviguer jusqu’au chemin d’accès du fournisseur SQL Server. À partir de cet emplacement, le paramètre **path** n’est pas nécessaire pour `Get-Help` pour obtenir l’aide spécifique au fournisseur.

```powershell
Get-Help Get-Item -Path SQLSERVER:\DataCollection
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

```powershell
Set-Location SQLSERVER:\DataCollection
SQLSERVER:\DataCollection> Get-Help Get-Item
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

### Exemple 12 : afficher l’aide d’un script

Cet exemple obtient l’aide pour le `MyScript.ps1 script` . Pour plus d’informations sur la façon d’écrire de l’aide pour vos fonctions et scripts, consultez [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## PARAMETERS

### -Catégorie

Affiche l'aide uniquement des éléments de la catégorie spécifiée et de leurs alias. Les articles conceptuels se trouvent dans la catégorie **HelpFile** .

Les valeurs acceptables pour ce paramètre sont les suivantes :

- Alias
- Applet de commande
- Fournisseur
- Général
- Questions fréquentes (FAQ)
- Glossaire
- HelpFile
- ScriptCommand
- Fonction
- Filtrer
- ExternalScript
- Tous
- DefaultHelp
- Workflow
- DscResource
- Classe
- Configuration

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Alias, Cmdlet, Provider, General, FAQ, Glossary, HelpFile, ScriptCommand, Function, Filter, ExternalScript, All, DefaultHelp, Workflow, DscResource, Class, Configuration

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Composant

Affiche les commandes avec la valeur de composant spécifiée, par exemple **Exchange** . Entrez un nom de composant.
Les caractères génériques sont autorisés. Ce paramètre n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Detailed

Ajoute la description des paramètre et les exemples à l'affichage de l'aide de base. Ce paramètre est effectif uniquement lorsque les fichiers d’aide sont installés sur l’ordinateur. Elle n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetailedView
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Examples

Affiche uniquement le nom, le résumé et les exemples. Pour afficher uniquement les exemples, tapez `(Get-Help \<cmdlet-name\>).Examples` .

Ce paramètre est effectif uniquement lorsque les fichiers d’aide sont installés sur l’ordinateur. Elle n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Examples
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Full

Affiche la totalité de l’article d’aide pour une applet de commande. **Full** comprend des descriptions de paramètres et des attributs, des exemples, des types d’objet d’entrée et de sortie, ainsi que des remarques supplémentaires.

Ce paramètre est effectif uniquement lorsque les fichiers d’aide sont installés sur l’ordinateur. Elle n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllUsersView
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fonctionnalité

Affiche l'aide pour des éléments ayant la fonctionnalité spécifiée. Entrez la fonctionnalité. Les caractères génériques sont autorisés. Ce paramètre n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

Obtient de l'aide sur la commande ou le concept spécifié. Entrez le nom d’une applet de commande, d’une fonction, d’un fournisseur, d’un script ou d’un flux de travail, tel que `Get-Member` , un nom d’article conceptuel, tel que `about_Objects` , ou un alias, tel que `ls` . Les caractères génériques sont autorisés dans les noms d’applet de commande et de fournisseur, mais vous ne pouvez pas utiliser de caractères génériques pour rechercher les noms des articles d’aide de fonction et de script.

Pour obtenir de l’aide sur un script qui ne se trouve pas dans un chemin d’accès qui est listé dans la `$env:Path` variable d’environnement, tapez le chemin d’accès et le nom de fichier du script.

Si vous entrez le nom exact d’un article d’aide, `Get-Help` affiche le contenu de l’article.

Si vous entrez un mot ou un modèle de mot qui apparaît dans plusieurs titres d’articles d’aide, `Get-Help` affiche une liste des titres correspondants.

Si vous entrez du texte qui ne correspond à aucun titre d’article d’aide, `Get-Help` affiche une liste d’articles incluant ce texte dans leur contenu.

Les noms des articles conceptuels, tels que `about_Objects` , doivent être entrés en anglais, même dans les versions non anglaises de PowerShell.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -En ligne

Affiche la version en ligne d’un article d’aide dans le navigateur par défaut. Ce paramètre est valide uniquement pour les articles d’aide sur les applets de commande, les fonctions, les workflows et les scripts. Vous ne pouvez pas utiliser le paramètre **Online** avec `Get-Help` dans une session à distance.

Pour plus d’informations sur la prise en charge de cette fonctionnalité dans les articles d’aide que vous écrivez, consultez [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)et [prise en charge de l’aide en ligne](/powershell/scripting/developer/module/supporting-online-help)et [écriture d’aide pour les applets de commande PowerShell](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Online
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### Paramètres 

Affiche uniquement les descriptions détaillées des paramètres spécifiés. Les caractères génériques sont autorisés. Ce paramètre n’a aucun effet sur les affichages de l’aide conceptuelle ( **about_** ).

```yaml
Type: System.String
Parameter Sets: Parameters
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

Obtient l'aide qui explique le fonctionnement de l'applet de commande dans le chemin d'accès du fournisseur spécifié. Entrez un chemin d’accès au fournisseur PowerShell.

Ce paramètre obtient une version personnalisée d’un article d’aide sur les applets de commande qui explique le fonctionnement de l’applet de commande dans le chemin d’accès du fournisseur PowerShell spécifié. Ce paramètre est effectif uniquement pour l’aide relative à une applet de commande de fournisseur et uniquement lorsque le fournisseur comprend une version personnalisée de l’article d’aide sur l’applet de commande du fournisseur dans son fichier d’aide. Pour utiliser ce paramètre, installez le fichier d'aide du module qui inclut le fournisseur.

Pour afficher l’aide de l’applet de commande personnalisée pour un chemin d’accès de fournisseur, accédez à l’emplacement du chemin d’accès du fournisseur et entrez une `Get-Help` commande ou, à partir d’un emplacement de chemin d’accès, utilisez le paramètre **path** de `Get-Help` pour spécifier le chemin d’accès du fournisseur. Vous pouvez également trouver l’aide en ligne de l’applet de commande personnalisée dans la section d’aide du fournisseur des articles d’aide.

Pour plus d’informations sur les fournisseurs PowerShell, consultez [about_Providers](./About/about_Providers.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Rôle

Affiche l'aide personnalisée du rôle d'utilisateur spécifié. Entrez un rôle. Les caractères génériques sont autorisés.

Entrez le rôle joué par l'utilisateur dans une organisation. Certaines applets de commande affichent du texte différent dans leurs fichiers d'aide en fonction de la valeur de ce paramètre. Ce paramètre n'a aucun effet sur l'aide des applets de commande de base.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowWindow

Affiche la rubrique d'aide dans une fenêtre pour faciliter la lecture. La fenêtre inclut une fonctionnalité **de recherche de recherche et** une zone de **paramètres** qui vous permettent de définir des options pour l’affichage, y compris des options permettant d’afficher uniquement les sections sélectionnées d’une rubrique d’aide.

Le paramètre **ShowWindow** prend en charge les rubriques d’aide pour les commandes (applets de commande, fonctions, commandes CIM, workflows, scripts) et **les articles** conceptuels. Il ne gère pas l'aide du fournisseur.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShowWindow
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas envoyer d’objets dans le pipeline vers `Get-Help` .

## SORTIES

### ExtendedCmdletHelpInfo

Si vous exécutez `Get-Help` sur une commande qui n’a pas de fichier d’aide, `Get-Help` retourne un objet **ExtendedCmdletHelpInfo** qui représente l’aide générée automatiquement.

### System.String

Si vous recevez un article d’aide conceptuelle, `Get-Help` le retourne sous forme de chaîne.

### MamlCommandHelpInfo

Si vous recevez une commande qui contient un fichier d’aide, `Get-Help` retourne un objet **MamlCommandHelpInfo** .

## REMARQUES

PowerShell 3,0 n’inclut pas les fichiers d’aide. Pour télécharger et installer les fichiers d’aide que `Get-Help` lit, utilisez l’applet de commande `Update-Help` . Vous pouvez utiliser l' `Update-Help` applet de commande pour télécharger et installer les fichiers d’aide pour les commandes de base fournies avec PowerShell et pour tous les modules que vous installez. Vous pouvez également l'utiliser pour mettre à jour les fichiers d'aide afin que l'aide sur votre ordinateur ne soit jamais obsolète.

Vous pouvez également lire les articles d’aide sur les commandes fournies avec PowerShell Online à partir de [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

`Get-Help` affiche l’aide dans l’ensemble de paramètres régionaux pour le système d’exploitation Windows ou dans la langue de secours pour ces paramètres régionaux. Si vous n’avez pas de fichiers d’aide pour les paramètres régionaux principaux ou de secours, `Get-Help` se comporte comme s’il n’y avait pas de fichiers d’aide sur l’ordinateur. Pour obtenir de l’aide pour des paramètres régionaux différents, utilisez **région** et **langue** dans le panneau de configuration pour modifier les paramètres. Sur Windows 10, **paramètres** , **heure & langue** .

La vue complète de l’aide comprend une table d’informations sur les paramètres. La table inclut les champs suivants :

- **Requis** . indique si le paramètre est obligatoire (true) ou facultatif (false).

- **Position** . Indique si le paramètre est nommé ou positionnel (numérique). les paramètres positionnels doivent apparaître à un emplacement spécifié de la commande.

- **Nommé** indique que le nom du paramètre est obligatoire, mais que le paramètre peut apparaître n’importe où dans la commande.

- **Numeric** indique que le nom du paramètre est facultatif, mais lorsque le nom est omis, le paramètre doit se trouver à l’emplacement spécifié par le nombre. Par exemple, `2` indique que lorsque le nom du paramètre est omis, le paramètre doit être le deuxième ou le seul paramètre sans nom dans la commande. Quand le nom du paramètre est utilisé, le paramètre peut apparaître n'importe où dans la commande.

- **Valeur par défaut** . La valeur du paramètre ou le comportement par défaut que PowerShell utilise si vous n’incluez pas le paramètre dans la commande.

- Accepte l’entrée de pipeline. Indique si vous pouvez (true) ou ne pouvez pas (false) envoyer des objets au paramètre via un pipeline. **Par nom de propriété** signifie que l’objet en pipeline doit avoir une propriété qui porte le même nom que le nom du paramètre.

- **Accepte les caractères génériques** . Indique si la valeur d’un paramètre peut inclure des caractères génériques, tels qu’un astérisque () ou un point d' `*` interrogation ( `?` ).

## LIENS CONNEXES

[about_Command_Syntax](About/about_Command_Syntax.md)

[about_Comment_Based_Help](./About/about_Comment_Based_Help.md)

[Get-Command](Get-Command.md)

[Prise en charge de l’aide actualisable](/powershell/scripting/developer/module/supporting-updatable-help)

[Update-Help](Update-Help.md)

[Écriture de rubriques d’aide basée sur les commentaires](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[Écriture d’une aide pour les applets de commande PowerShell](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)
