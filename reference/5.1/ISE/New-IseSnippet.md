---
external help file: ISE-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/new-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-IseSnippet
ms.openlocfilehash: 0ed1c2913fc7531574bfbdd435a002d60931d24a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202477"
---
# New-IseSnippet

## SYNOPSIS
Crée un extrait de code Windows PowerShell ISE.

## SYNTAX

```
New-IseSnippet [-Title] <String> [-Description] <String> [-Text] <String> [-Author <String>]
 [-CaretOffset <Int32>] [-Force] [<CommonParameters>]
```

## Description

L' `New-ISESnippet` applet de commande crée un « extrait » de texte réutilisable pour Windows PowerShell ISE. Vous pouvez utiliser des extraits de code pour ajouter du texte au volet de script ou de commandes dans Windows PowerShell ISE. Cette applet de commande est disponible uniquement dans Windows PowerShell ISE.

À compter de Windows PowerShell 3.0, Windows PowerShell ISE inclut une collection d'extraits de code intégrés. L' `New-ISESnippet` applet de commande vous permet de créer vos propres extraits de code à ajouter à la collection intégrée. Vous pouvez afficher, modifier, ajouter, supprimer et partager les fichiers d'extraits de code et les inclure dans les modules Windows PowerShell. Pour afficher les extraits de code dans Windows PowerShell ISE, dans le menu **Edition** , sélectionnez **Démarrer les extraits** ou appuyez sur <kbd>CTRL</kbd> + <kbd>J</kbd>.

L' `New-ISESnippet` applet de commande crée un `<Title>.Snippets.ps1xml` fichier dans le `$home\Documents\WindowsPowerShell\Snippets` répertoire avec le titre que vous spécifiez. Pour inclure un fichier d'extraits de code dans un module que vous créez, ajoutez le fichier d'extraits à un sous-répertoire Snippets de votre répertoire de module.

Vous ne pouvez pas utiliser d’extraits de code créés par l’utilisateur dans une session dans laquelle la stratégie d’exécution est **restreinte** ou **AllSigned** .

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : créer un extrait de code d’aide Comment-Based

```
New-IseSnippet -Title Comment-BasedHelp -Description "A template for comment-based help." -Text "<#
    .SYNOPSIS

    .DESCRIPTION
    .PARAMETER  <Parameter-Name>
    .INPUTS
    .OUTPUTS
    .EXAMPLE
    .LINK
#>"
```

Cette commande crée un extrait de code Comment-BasedHelp pour Windows PowerShell ISE. Il crée un fichier nommé `Comment-BasedHelp.snippets.ps1xml` dans le répertoire des extraits de code de l’utilisateur `$home\Documents\WindowsPowerShell\Snippets` .

### Exemple 2 : créer un extrait de code obligatoire

```
$M = @'
Param
(
  [parameter(Mandatory=$true)]
  [String[]]
  $<ParameterName>
)
'@

New-ISESnippet -Text $M -Title Mandatory -Description "Adds a mandatory function parameter." -Author "Patti Fuller, Fabrikam Corp." -Force
```

Cet exemple crée un extrait de code nommé **obligatoire** pour Windows PowerShell ISE. La première commande enregistre le texte de l’extrait de code dans la `$M` variable. La deuxième commande utilise l' `New-ISESnippet` applet de commande pour créer l’extrait de code. La commande utilise le paramètre **Force** pour remplacer un extrait de code précédent avec le même nom.

### Exemple 3 : copier un extrait de code obligatoire d’un dossier vers un dossier de destination

```
Copy-Item "$Home\Documents\WindowsPowerShell\Snippets\Mandatory.Snippets.ps1xml" -Destination "\\Server\Share"
```

Cette commande utilise la `Copy-Item` cmdlet pour copier l’extrait de code **obligatoire** à partir du dossier où `New-ISESnippet` il est placé dans le partage de fichiers Server\Share.

## PARAMETERS

### -Auteur

Spécifie l’auteur de l’extrait de code. Le champ de l'auteur apparaît dans le fichier d'extraits de code, mais il n'apparaît pas quand vous cliquez sur le nom de l'extrait de code dans Windows PowerShell ISE.

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

### -CaretOffset

Spécifie le caractère du texte de l’extrait de code sur lequel cette applet de commande place le curseur. Entrez un entier qui représente la position du curseur, « 1 » représentant le premier caractère de texte. La valeur par défaut, 0 (zéro), place le curseur immédiatement avant le premier caractère de texte. Ce paramètre ne met pas en retrait le texte de l'extrait de code.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### Description

Spécifie une description de l’extrait de code. La valeur de description s'affiche quand vous cliquez sur le nom de l'extrait de code dans Windows PowerShell ISE. Ce paramètre est obligatoire.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Indique que cette applet de commande remplace les fichiers d’extrait de code portant le même nom au même emplacement. Par défaut, `New-ISESnippet` ne remplace pas les fichiers.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Texte

Spécifie la valeur de texte qui est ajoutée quand vous sélectionnez l'extrait de code. Le texte de l'extrait apparaît quand vous cliquez sur le nom de l'extrait de code dans Windows PowerShell ISE. Ce paramètre est obligatoire.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Title

Spécifie un titre ou un nom pour l'extrait de code. Le titre nomme également le fichier d'extraits de code. Ce paramètre est obligatoire.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Cette applet de commande n'accepte pas d'entrée provenant du pipeline.

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

`New-IseSnippet` stocke les nouveaux extraits de code créés par l’utilisateur dans les fichiers. ps1xml non signés. En conséquence, Windows PowerShell ne peut pas les ajouter à une session dans laquelle la stratégie d'exécution est **AllSigned** ou **Restricted** . Dans une session **Restricted** ou **AllSigned** , vous pouvez créer, obtenir et importer des extraits de code créés par l'utilisateur non signés, mais vous ne pouvez pas les utiliser dans la session.

Si vous utilisez l' `New-IseSnippet` applet de commande dans une session **Restricted** ou **AllSigned** , l’extrait de code est créé, mais un message d’erreur s’affiche lorsque Windows PowerShell tente d’ajouter l’extrait de code nouvellement créé à la session. Pour utiliser le nouvel extrait de code (et d'autres extraits créés par l'utilisateur non signés), modifiez la stratégie d'exécution, puis redémarrez Windows PowerShell ISE.

Pour plus d'informations sur les stratégies d'exécution Windows PowerShell, consultez about_Execution_Policies.

- Pour modifier un extrait de code, modifiez le fichier d’extrait de code. Vous pouvez modifier les fichiers d’extrait de code dans le volet script de Windows PowerShell ISE.
- Pour supprimer un extrait de code que vous avez ajouté, supprimez le fichier d’extrait de code.
- Vous ne pouvez pas supprimer un extrait de code intégré, mais vous pouvez masquer tous les extraits de code intégrés à l’aide de l' $psise. Commande Options. ShowDefaultSnippets = $false».
- Vous pouvez créer un extrait de code qui porte le même nom qu’un extrait de code intégré. Les deux extraits de code apparaissent dans le menu des extraits de Windows PowerShell ISE.

## LIENS CONNEXES

[Get-IseSnippet](Get-IseSnippet.md)

[Import-IseSnippet](Import-IseSnippet.md)
