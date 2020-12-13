---
ms.date: 09/12/2016
ms.topic: reference
title: Exemples d’aide basée sur les commentaires
description: Exemples d’aide basée sur les commentaires
ms.openlocfilehash: 35fe9103a261483c56af629f620dbd6b3c642e68
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667638"
---
# <a name="examples-of-comment-based-help"></a>Exemples d’aide basée sur les commentaires

Cette rubrique contient des exemples qui montrent comment utiliser l’aide basée sur des commentaires pour les scripts et les fonctions.

## <a name="example-1-comment-based-help-for-a-function"></a>Exemple 1 : Comment-Based de l’aide pour une fonction

 L’exemple de fonction suivant comprend une aide basée sur des commentaires.

```powershell
function Add-Extension
{
    param ([string]$Name,[string]$Extension = "txt")
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.

        .DESCRIPTION
        Adds a file name extension to a supplied name.
        Takes any strings for the file name or extension.

        .PARAMETER Name
        Specifies the file name.

        .PARAMETER Extension
        Specifies the extension. "Txt" is the default.

        .INPUTS
        None. You cannot pipe objects to Add-Extension.

        .OUTPUTS
        System.String. Add-Extension returns a string with the extension or file name.

        .EXAMPLE
        C:\PS> extension -name "File"
        File.txt

        .EXAMPLE
        C:\PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        C:\PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

La sortie suivante montre les résultats d’une `Get-Help` commande qui affiche l’aide de la `Add-Extension` fonction.

```powershell
C:\PS> get-help add-extension -full
```

```Output
        NAME
            Add-Extension

        SYNOPSIS
            Adds a file name extension to a supplied name.

        SYNTAX
            Add-Extension [[-Name] <String>] [[-Extension] <String>] [<CommonParameters>]

        DESCRIPTION
            Adds a file name extension to a supplied name. Takes any strings for the file name or extension.

        PARAMETERS
           -Name
               Specifies the file name.

               Required?                    false
               Position?                    0
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

           -Extension
               Specifies the extension. "Txt" is the default.

               Required?                    false
               Position?                    1
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

            <CommonParameters>
               This cmdlet supports the common parameters: -Verbose, -Debug,
               -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
               -OutBuffer and -OutVariable. For more information, type
               "get-help about_commonparameters".

        INPUTS
            None. You cannot pipe objects to Add-Extension.

        OUTPUTS
            System.String. Add-Extension returns a string with the extension or file name.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a>Exemple 2 : Comment-Based de l’aide pour un script

L’exemple de fonction suivant comprend une aide basée sur des commentaires.

Notez les lignes vides entre la fermeture **#>** et l' `Param` instruction. Dans un script qui n’a pas d' `Param` instruction, il doit y avoir au moins deux lignes vides entre le commentaire final de la rubrique d’aide et la première déclaration de fonction. Sans ces lignes vides, `Get-Help` associe la rubrique d’aide à la fonction, au lieu du script.

```powershell
<#
  .SYNOPSIS
  Performs monthly data updates.

  .DESCRIPTION
  The Update-Month.ps1 script updates the registry with new data generated
  during the past month and generates a report.

  .PARAMETER InputPath
  Specifies the path to the CSV-based input file.

  .PARAMETER OutputPath
  Specifies the name and path for the CSV-based output file. By default,
  MonthlyUpdates.ps1 generates a name from the date and time it runs, and
  saves the output in the local directory.

  .INPUTS
  None. You cannot pipe objects to Update-Month.ps1.

  .OUTPUTS
  None. Update-Month.ps1 does not generate any output.

  .EXAMPLE
  C:\PS> .\Update-Month.ps1

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

La commande suivante obtient l’aide du script. Étant donné que le script n’est pas dans un répertoire qui est listé dans la variable d’environnement PATH, la `Get-Help` commande qui obtient l’aide du script doit spécifier le chemin d’accès du script.

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```Output
            NAME
                C:\ps-test\Update-Month.ps1

            SYNOPSIS
                Performs monthly data updates.

            SYNTAX
                C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
                <String>] [<CommonParameters>]

            DESCRIPTION
                The Update-Month.ps1 script updates the registry with new data
                generated during the past month and generates a report.

            PARAMETERS
               -InputPath
                   Specifies the path to the CSV-based input file.

                   Required?                    true
                   Position?                    0
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               -OutputPath
                   Specifies the name and path for the CSV-based output file. By
                   default, MonthlyUpdates.ps1 generates a name from the date
                   and time it runs, and saves the output in the local directory.

                   Required?                    false
                   Position?                    1
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               <CommonParameters>
                   This cmdlet supports the common parameters: -Verbose, -Debug,
                   -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
                   -OutBuffer and -OutVariable. For more information, type,
                   "get-help about_commonparameters".

            INPUTS
                   None. You cannot pipe objects to Update-Month.ps1.

            OUTPUTS
                   None. Update-Month.ps1 does not generate any output.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a>Exemple 3 : descriptions des paramètres dans une instruction param

Cet exemple montre comment insérer des descriptions de paramètres dans l' `Param` instruction d’une fonction ou d’un script. Ce format est particulièrement utile lorsque les descriptions des paramètres sont courtes.

```powershell
function Add-Extension
{
    param
    (
        [string]
        # Specifies the file name.
        $name,

        [string]
        # Specifies the file name extension. "Txt" is the default.
        $extension = "txt"
    )
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.
...
    #>
```

Les résultats sont les mêmes que ceux de l’exemple 1. `Get-Help` interprète les descriptions des paramètres comme s’ils étaient accompagnés du `.Parameter` mot clé.

## <a name="example-4--redirecting-to-an-xml-file"></a>Exemple 4 : redirection vers un fichier XML

Vous pouvez écrire des rubriques d’aide basées sur XML pour des fonctions et des scripts. Bien que l’aide basée sur les commentaires soit plus facile à implémenter, une aide XML est nécessaire si vous souhaitez contrôler plus précisément le contenu de l’aide ou si vous traduisez des rubriques d’aide en plusieurs langues. L’exemple suivant montre les premières lignes du `Update-Month.ps1` script. Le script utilise le `.ExternalHelp` mot clé pour spécifier le chemin d’accès à une rubrique d’aide XML pour le script.

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

L’exemple suivant illustre l’utilisation du `.ExternalHelp` mot clé dans une fonction.

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a>Exemple 5 : redirection vers une autre rubrique d’aide

Le code suivant est un extrait du début de la `Help` fonction intégrée dans PowerShell, qui affiche un écran de texte d’aide à la fois. Étant donné que la rubrique d’aide de l’applet de commande Get-Help décrit la fonction Help, la fonction Help utilise les `.ForwardHelpTargetName` `.ForwardHelpCategory` Mots clés et pour rediriger l’utilisateur vers la rubrique d’aide de l’applet de commande Get-Help.

```powershell
function help
{

    <#
      .FORWARDHELPTARGETNAME Get-Help
      .FORWARDHELPCATEGORY Cmdlet
    #>
    [CmdletBinding(DefaultParameterSetName='AllUsersView')]
    param(
            [Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
            [System.String]
            ${Name},
    ...
```

La commande suivante utilise cette fonctionnalité. Quand un utilisateur tape une `Get-Help` commande pour la `Help` fonction, `Get-Help` affiche la rubrique d’aide de l’applet de commande `Get-Help` .

```powershell
C:\PS> get-help help
```

```Output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```
