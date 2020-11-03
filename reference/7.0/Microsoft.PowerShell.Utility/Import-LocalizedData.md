---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-localizeddata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-LocalizedData
ms.openlocfilehash: 06c267b75739b5a9ec318adf12159332c0fd23df
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201989"
---
# Import-LocalizedData

## SYNOPSIS
Importe les données propres au langage dans les scripts et les fonctions basés sur la culture d'interface utilisateur sélectionnée pour le système d'exploitation.

## SYNTAX

```
Import-LocalizedData [[-BindingVariable] <String>] [[-UICulture] <String>] [-BaseDirectory <String>]
 [-FileName <String>] [-SupportedCommand <String[]>] [<CommonParameters>]
```

## Description

L'applet de commande **Import-LocalizedData** récupère dynamiquement les chaînes d'un sous-répertoire dont le nom correspond à la langue de l'interface utilisateur définie pour l'utilisateur actuel du système d'exploitation.
Il est conçu pour permettre aux scripts d'afficher les messages de l'utilisateur dans la langue de l'interface utilisateur sélectionnée par l'utilisateur actuel.

**Import-LocalizedData** importe des données à partir de fichiers. psd1 dans des sous-répertoires spécifiques au langage du répertoire de script et les enregistre dans une variable locale spécifiée dans la commande.
L'applet de commande sélectionne le sous-répertoire et le fichier selon la valeur de la variable automatique $PSUICulture.
Lorsque vous utilisez la variable locale du script pour afficher un message de l'utilisateur, le message s'affiche dans la langue d'interface utilisateur de l'utilisateur.

Vous pouvez utiliser les paramètres de **Import-LocalizedData** pour spécifier une culture d'interface utilisateur, un chemin d'accès et un nom de fichier différents, pour ajouter des commandes prises en charge et pour supprimer le message d'erreur qui s'affiche si les fichiers .psd1 sont introuvables.

L'applet de commande **Import-LocalizedData** prend en charge l'initiative d'internationalisation de script introduite dans Windows PowerShell 2.0.
Cette initiative vise à mieux servir les utilisateurs dans le monde entier en permettant aux scripts d'afficher facilement les messages de l'utilisateur dans la langue de l'interface utilisateur de l'utilisateur actuel.
Pour plus d’informations sur ce sujet et sur le format des fichiers. psd1, consultez about_Script_Internationalization.

## EXEMPLES

### Exemple 1 : importer des chaînes de texte

```
PS C:\> Import-LocalizedData -BindingVariable "Messages"
```

Cette commande importe les chaînes de texte dans la variable $Messages.
Elle utilise les valeurs par défaut de tous les autres paramètres de l'applet de commande.

Si la commande est incluse dans le script Archives.ps1 du répertoire C:\Test, et que la valeur de la variable automatique $PsUICulture est zh-CN, **Import-LocalizedData** importe le fichier Archives.psd1 du répertoire C:\test\zh-CN dans la variable $Messages.

### Exemple 2 : importer des chaînes de données localisées

```
PS C:\> Import-LocalizedData -FileName "Test.psd1" -UICulture "en-US"

Name                           Value
----                           -----
Msg3                           "Use $_ to represent the object that is being processed."
Msg2                           "This command requires the credentials of a member of the Administrators group on the...
Msg1                           "The Name parameter is missing from the command."
```

Cette commande est exécutée au niveau de la ligne de commande, pas dans un script.
Elle obtient les chaînes de données localisées du fichier Test.psd1 et les affiche au niveau de la ligne de commande.
Étant donné que la commande n'est pas utilisée dans un script, le paramètre *FileName* est obligatoire.
La commande utilise le paramètre *UICulture* pour spécifier la culture en-US.

**Import-LocalizedData** retourne une table de hachage qui contient les chaînes de données localisées.

### Exemple 3 : importer des chaînes de culture d’interface utilisateur

```
PS C:\> Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

Cette commande importe les chaînes de texte dans la variable $MsgTbl d’un script.

Elle utilise le paramètre *UICulture* pour demander à l'applet de commande d'importer les données à partir du fichier Simple.psd1 dans le sous-répertoire ar-SA de C:\Data\Localized.

### Exemple 4 : importer des données localisées dans un script

```
PS C:\> # In C:\Test\en-US\Test.psd1:

ConvertFrom-StringData @'

# English strings

Msg1 = "The Name parameter is missing from the command."
Msg2 = "This command requires the credentials of a member of the Administrators group on the computer."
Msg3 = "Use $_ to represent the object that is being processed."
'@

# In C:\Test\Test.ps1

Import-LocalizedData -BindingVariable "Messages"
Write-Host $Messages.Msg2

# In PowerShell

PS C:\> .\Test.ps1

This command requires the credentials of a member of the Administrators group on the computer.
```

Cet exemple montre comment utiliser les données localisées dans un script simple.

La première partie de l'exemple illustre le contenu du fichier Test.psd1.
Elle contient une commande ConvertFrom-StringData qui convertit une série de chaînes de texte nommées en une table de hachage.
Le fichier Test.psd1 se trouve dans le sous-répertoire en-US du répertoire C:\Test qui contient le script.

La deuxième partie de l'exemple illustre le contenu du script Test.ps1.
Elle contient une commande **Import-LocalizedData** qui importe les données du fichier. psd1 correspondant dans la variable $messages et une commande Write-Host qui écrit l’un des messages de la variable $messages dans le programme hôte.

La dernière partie de l'exemple exécute le script.
La sortie montre qu'il affiche le message correct de l'utilisateur dans la langue de l'interface utilisateur définie pour l'utilisateur actuel du système d'exploitation.

### Exemple 5 : remplacer les chaînes de texte par défaut dans un script

```
PS C:\> # In TestScript.ps1
$UserMessages = DATA

{    ConvertFrom-StringData @'

    # English strings

        Msg1 = "Enter a name."
        Msg2 = "Enter your employee ID."
        Msg3 = "Enter your building number."
'@ }
Import-LocalizedData -BindingVariable "UserMessages"
$UserMessages.Msg1...
```

Cet exemple montre comment utiliser **Import-LocalizedData** pour remplacer les chaînes de texte par défaut définies dans la section DATA d'un script.

Dans cet exemple, la section de données du script TestScript.ps1 contient une commande ConvertFrom-StringData qui convertit le contenu de la section de données en une table de hachage et stocke dans la valeur de la variable $UserMessages.

Le script inclut également une commande **Import-LocalizedData** , qui importe une table de hachage des chaînes de texte traduites du fichier TestScript.psd1 du sous-répertoire spécifié par la valeur de la variable $PsUICulture.
Si la commande trouve le fichier .psd1, elle enregistre les chaînes traduites du fichier de la valeur de la même variable $UserMessages, remplaçant ainsi la table de hachage enregistrée par la logique de la section DATA.

La troisième commande affiche le premier message de la variable $UserMessages.

Si la commande **Import-LocalizedData** trouve un fichier .psd1 pour la langue $PsUICulture, la valeur de la variable $UserMessages contient les chaînes de texte traduites.
Si la commande échoue pour une raison quelconque, la commande affiche les chaînes de texte par défaut définies dans la section DATA du script.

### Exemple 6 : supprimer les messages d’erreur si la culture de l’interface utilisateur est introuvable

```
PS C:\> # In Day1.ps1

Import-LocalizedData -BindingVariable "Day"

# In Day2.ps1

Import-LocalizedData -BindingVariable "Day" -ErrorAction:SilentlyContinue

PS C:\> .\Day1.ps1
Import-LocalizedData : Cannot find PowerShell data file 'Day1.psd1' in directory 'C:\ps-test\fr-BE\' or any parent culture directories.
At C:\ps-test\Day1.ps1:17 char:21+ Import-LocalizedData <<<<  Day
Today is Tuesday PS C:\> .\Day2.ps1
Today is Tuesday
```

Cet exemple montre comment supprimer les messages d'erreur qui s'affichent quand **Import-LocalizedData** ne peut pas trouver les répertoires qui correspondent à la culture d'interface utilisateur de l'utilisateur ou ne peut pas trouver un fichier .psd1 pour le script dans ces répertoires.

Vous pouvez utiliser le paramètre commun *ErrorAction* avec la valeur SilentlyContinue pour supprimer le message d'erreur.
Cela s’avère particulièrement utile lorsque vous avez fourni des messages utilisateur dans une langue par défaut ou de secours, et qu’aucun message d’erreur n’est nécessaire.

Cet exemple compare deux scripts, Day1.ps1 et Day2.ps1, qui incluent une commande **Import-LocalizedData** .
Les scripts sont identiques, sauf que Day2 utilise le paramètre commun *ErrorAction* avec la valeur SilentlyContinue.

L'exemple de sortie montre les résultats de l'exécution des scripts lorsque la culture d'interface utilisateur est définie sur fr-BE et qu'il n'existe aucun fichier ou répertoire correspondant pour cette culture d'interface utilisateur.
Day1.ps1 affiche un message d'erreur et la sortie en anglais.
Day2.ps1 affiche simplement le résultat en anglais.

## PARAMETERS

### -BaseDirectory

Spécifie le répertoire de base où se trouvent les fichiers .psd1.
La valeur par défaut est le répertoire où se trouve le script.
**Import-LocalizedData** recherche le fichier .psd1 du script dans un sous-répertoire propre au langage du répertoire de base.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BindingVariable

Spécifie la variable dans laquelle les chaînes de texte sont importées.
Entrez un nom de variable sans le symbole dollar ($).

Dans Windows PowerShell 2.0, ce paramètre est obligatoire.
Dans Windows PowerShell 3.0, ce paramètre est facultatif.
Si vous omettez ce paramètre, **Import-LocalizedData** retourne une table de hachage des chaînes de texte.
La table de hachage est passée dans le pipeline ou affichée sur la ligne de commande.

Lorsque vous utilisez **Import-LocalizedData** pour remplacer les chaînes de texte par défaut spécifiées dans la section DATA d'un script, affectez la section DATA à une variable et entrez le nom de la variable de la section DATA dans la valeur du paramètre *BindingVariable* .
Ensuite, lorsque **Import-LocalizedData** enregistre le contenu importé dans *BindingVariable* , les données importées remplacent les chaînes de texte par défaut.
Si vous ne spécifiez pas de chaînes de texte par défaut, vous pouvez sélectionner n'importe quel nom de variable.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Variable

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### Nom de fichier

Spécifie le nom du fichier de données (.psd1) à importer.
Entrez un nom de fichier.
Vous pouvez spécifier un nom de fichier qui n'inclut pas son extension de nom de fichier .psd1 ou vous pouvez spécifier le nom du fichier y compris l'extension de nom de fichier .psd1.

Le *FileName* paramètre est requis quand **Import-LocalizedData** n'est pas utilisé dans un script.
Sinon, le paramètre est facultatif et la valeur par défaut est le nom de base du script.
Vous pouvez utiliser ce paramètre pour diriger **Import-LocalizedData** et rechercher un autre fichier .psd1.

Par exemple, si le nom de *fichier* est omis et que le nom du script est FindFiles.ps1, **Import-LocalizedData** recherche le fichier de données FindFiles.psd1.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportedCommand

Spécifie les applets de commande et les fonctions qui génèrent uniquement des données.

Utilisez ce paramètre pour inclure les applets de commande et les fonctions que vous avez écrites ou testées.
Pour plus d’informations, consultez about_Script_Internationalization.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UICulture

Spécifie une autre culture d'interface utilisateur.
La valeur par défaut est la valeur de la variable automatique $PsUICulture.
Entrez une culture d’interface utilisateur au \<language\> - \<region\> format, par exemple fr-fr, de-de ou ar-sa.

La valeur du paramètre *UICulture* détermine le sous-répertoire propre au langage (dans le répertoire de base) à partir duquel **Import-LocalizedData** obtient le fichier .psd1 pour le script.

L’applet de commande recherche un sous-répertoire portant le même nom que la valeur du paramètre *UICulture* ou la variable automatique $PsUICulture, par exemple DE-de ou ar-sa.
S’il ne trouve pas le répertoire ou si le répertoire ne contient pas de fichier. psd1 pour le script, il recherche un sous-répertoire avec le nom du code de langue, tel que de ou ar.
Si elle ne peut pas trouver le sous-répertoire ou le fichier .psd1, la commande échoue et les données sont affichées dans la langue par défaut spécifiée dans le script.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System.Collections.Hashtable

**Import-LocalizedData** enregistre la table de hachage dans la variable spécifiée par la valeur du paramètre **BindingVariable** .

## REMARQUES

* Avant d'utiliser **Import-LocalizedData** , localisez vos messages utilisateur. Mettez en forme les messages de chacun des paramètres régionaux (culture d'interface utilisateur) dans une table de hachage de paires clé/valeur et enregistrez la table de hachage dans un fichier portant le même nom que le script et une extension de nom de fichier .psd1. Créez un répertoire sous le répertoire de scripts pour chaque culture d'interface utilisateur prise en charge, puis enregistrez le fichier .psd1 pour chaque culture d'interface utilisateur dans le répertoire avec le nom de la culture d'interface utilisateur.

  Par exemple, localisez vos messages utilisateur pour les paramètres régionaux fr-FR et mettez-les en forme dans une table de hachage.
Enregistrez la table de hachage dans un fichier \<ScriptName\>.psd1.
Puis, créez un sous-répertoire fr-FR sous le répertoire de scripts, puis enregistrez le fichier fr-FR \<ScriptName\>.psd1 dans le sous-répertoire fr-FR.
Répétez l'opération pour chacun des paramètres régionaux pris en charge.

* **Import-LocalizedData** effectue une recherche structurée des messages utilisateur localisés pour un script.

  **Import-LocalizedData** commence la recherche dans le répertoire où se trouve le fichier de script (ou la valeur du paramètre *baseDirectory* ).
Il recherche ensuite dans le répertoire de base un sous-répertoire portant le même nom que la valeur de la variable $PsUICulture (ou la valeur du paramètre *UICulture* ), par exemple DE-fr ou ar-sa.
Il recherche ensuite dans ce sous-répertoire un fichier .psd1 de même nom que le script (ou que la valeur du paramètre *FileName* ).

  Si **Import-LocalizedData** ne trouve pas de sous-répertoire avec le nom de la culture d’interface utilisateur, ou si le sous-répertoire ne contient pas de fichier. psd1 pour le script, il recherche un fichier. psd1 pour le script dans un sous-répertoire avec le nom du code de langue, par exemple de ou ar.
Si l'applet de commande ne peut pas trouver le sous-répertoire ou le fichier .psd1, la commande échoue, les données sont affichées dans la langue par défaut dans le script et un message d'erreur apparaît, expliquant que les données ne peuvent pas être importées.
Pour supprimer le message et échouer correctement, utilisez le paramètre commun *ErrorAction* avec la valeur SilentlyContinue.

  Si **Import-LocalizedData** trouve le sous-répertoire et le fichier .psd1, il importe la table de hachage des messages utilisateur dans la valeur du paramètre *BindingVariable* de la commande.
Ensuite, lorsque vous affichez un message à partir de la table de hachage de la variable, le message localisé apparaît.

  Pour plus d’informations, consultez [about_Script_Internationalization](../Microsoft.PowerShell.Core/about/about_Script_Internationalization.md).

## LIENS CONNEXES

[Write-Host](Write-Host.md)

[Import-PowerShellDataFile](Import-PowerShellDataFile.md)
