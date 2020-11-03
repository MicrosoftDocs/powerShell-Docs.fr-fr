---
external help file: ISE-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/get-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-IseSnippet
ms.openlocfilehash: c43dae3f178ae778d78fe3718fa85fd2635eba86
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205338"
---
# Get-IseSnippet

## SYNOPSIS
Obtient les extraits de code créés par l'utilisateur.

## SYNTAX

```
Get-IseSnippet [<CommonParameters>]
```

## Description

L' `Get-IseSnippet` applet de commande obtient les fichiers ps1xml qui contiennent des extraits de texte réutilisables que l’utilisateur a créés. Elle fonctionne uniquement dans Environnement d’écriture de scripts intégré de Windows PowerShell (ISE).

Lorsque vous utilisez l' `New-IseSnippet` applet de commande pour créer un extrait de code, `New-IseSnippet` crée un `<SnippetTitle>.Snippets.ps1xml` fichier dans le `$home\Documents\WindowsPowerShell\Snippets` répertoire.
`Get-IseSnippet` Obtient les fichiers d’extraits de code dans le répertoire des extraits de code.

Cette applet de commande n’obtient pas les extraits de code intégrés ni les extraits de code importés à partir des modules via l’applet de commande `Import-IseSnippet` .

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : récupération de tous les extraits de code définis par l’utilisateur

Cet exemple obtient tous les extraits de code définis par l’utilisateur dans le répertoire snippets.

```powershell
Get-IseSnippet
```

### Exemple 2 : copier tous les extraits de code définis par l’utilisateur à partir d’ordinateurs distants dans un répertoire partagé

Cet exemple copie tous les extraits de code créés par l’utilisateur à partir d’un groupe d’ordinateurs distants dans un répertoire d’extraits de code partagé.

```powershell
Invoke-Command -Computer (Get-Content Servers.txt) {Get-IseSnippet | Copy-Item -Destination \\Server01\Share01\Snippets}
```

`Invoke-Command` s’exécute `Get-IseSnippet` sur les ordinateurs du `Servers.txt` fichier. Un opérateur de pipeline ( `|` ) envoie les fichiers d’extraits de code à l’applet de commande `Copy-Item` , qui les copie dans le répertoire spécifié par le paramètre de **destination** .

### Exemple 3 : afficher le titre et le texte de chaque extrait de code sur un ordinateur local

Cet exemple utilise les `Get-IseSnippet` applets de commande et `Select-Xml` pour afficher le titre et le texte de chaque extrait de code sur l’ordinateur local.

```powershell
#Parse-Snippet Function
function Parse-Snippet {
  $SnippetFiles = Get-IseSnippet
  $SnippetNamespace = @{x="http://schemas.microsoft.com/PowerShell/Snippets"}
  foreach ($SnippetFile in $SnippetFiles) {
     Write-Host ""
     $Title = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Title" |
       ForEach-Object {$_.Node.InnerXML}
     $Text = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Script" |
       ForEach-Object {$_.Node.InnerText}
     Write-Host "Title: $Title"
     Write-Host "Text: $Text"
   }
}
```

```Output
Title: Mandatory
Text:
Param
(
  [parameter(Mandatory=True)]
  [String[]]
  $<ParameterName>
)

Title: Copyright
Text:  (c) Fabrikam, Inc. 2012
```

### Exemple 4 : afficher le titre et la description de tous les extraits de code dans la session

Cet exemple affiche le titre et la description de tous les extraits de code dans la session, y compris les extraits de code intégrés, les extraits de code définis par l’utilisateur et les extraits importés.

```powershell
$PSISE.CurrentPowerShellTab.Snippets | Format-Table DisplayTitle, Description
```

La `$PSISE` variable représente le programme hôte Windows PowerShell ISE. La propriété **CurrentPowerShellTab** de la `$PSISE` variable représente la session active. La propriété **Snippets** représente les extraits de code dans la session active.

La `$PSISE.CurrentPowerShellTab.Snippets` commande retourne un objet **Microsoft. PowerShell. Host. ISE. ISESnippet** qui représente un extrait de code, contrairement à l’applet de commande `Get-IseSnippet` . `Get-IseSnippet` retourne un objet de fichier (System. IO. FileInfo) qui représente un fichier d’extrait de code.

L' `Format-Table` applet de commande affiche les propriétés **DisplayTitle** et **Description** des extraits de code dans une table.

## PARAMETERS

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

### System. IO. FileInfo

Cette applet de commande retourne un objet de fichier qui représente le fichier d’extrait de code.

## REMARQUES

* L' `New-IseSnippet` applet de commande stocke les nouveaux extraits de code créés par l’utilisateur dans les fichiers. ps1xml non signés. En conséquence, Windows PowerShell ne peut pas les ajouter à une session dans laquelle la stratégie d'exécution est **AllSigned** ou **Restricted** . Dans une session **Restricted** ou **AllSigned** , vous pouvez créer, obtenir et importer des extraits de code créés par l'utilisateur non signés, mais vous ne pouvez pas les utiliser dans la session.

  Pour utiliser des extraits de code créés par l’utilisateur non signés que l’applet de commande `Get-IseSnippet` retourne, modifiez la stratégie d’exécution, puis redémarrez Windows PowerShell ISE.

  Pour plus d'informations sur les stratégies d'exécution Windows PowerShell, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).

## LIENS CONNEXES

[New-IseSnippet](New-IseSnippet.md)

[Import-IseSnippet](Import-IseSnippet.md)
