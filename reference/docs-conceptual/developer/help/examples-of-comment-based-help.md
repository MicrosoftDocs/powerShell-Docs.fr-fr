---
ms.date: 01/11/2021
ms.topic: reference
title: Exemples d’aide basée sur les commentaires
description: Exemples d’aide basée sur les commentaires
ms.openlocfilehash: 237e65c59cc3b35f48b6d667c8fb297994b03638
ms.sourcegitcommit: 4879b9cdfa3f03b04a07b84442dc1ca9ae0f6b46
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2021
ms.locfileid: "98105160"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="c1bb1-103">Exemples d’aide basée sur les commentaires</span><span class="sxs-lookup"><span data-stu-id="c1bb1-103">Examples of Comment-Based Help</span></span>

<span data-ttu-id="c1bb1-104">Cette rubrique contient des exemples qui montrent comment utiliser l’aide basée sur des commentaires pour les scripts et les fonctions.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-104">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="c1bb1-105">Exemple 1 : Comment-Based de l’aide pour une fonction</span><span class="sxs-lookup"><span data-stu-id="c1bb1-105">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="c1bb1-106">L’exemple de fonction suivant comprend une aide basée sur des commentaires.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-106">The following sample function includes comment-based Help.</span></span>

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
        PS> extension -name "File"
        File.txt

        .EXAMPLE
        PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

<span data-ttu-id="c1bb1-107">La sortie suivante montre les résultats d’une `Get-Help` commande qui affiche l’aide de la `Add-Extension` fonction.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-107">The following output shows the results of a `Get-Help` command that displays the help for the `Add-Extension` function.</span></span>

```powershell
PS> Get-Help Add-Extension -full
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

            PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="c1bb1-108">Exemple 2 : Comment-Based de l’aide pour un script</span><span class="sxs-lookup"><span data-stu-id="c1bb1-108">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="c1bb1-109">L’exemple de fonction suivant comprend une aide basée sur des commentaires.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-109">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="c1bb1-110">Notez les lignes vides entre la fermeture **#>** et l' `Param` instruction.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-110">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="c1bb1-111">Dans un script qui n’a pas d' `Param` instruction, il doit y avoir au moins deux lignes vides entre le commentaire final de la rubrique d’aide et la première déclaration de fonction.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-111">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="c1bb1-112">Sans ces lignes vides, `Get-Help` associe la rubrique d’aide à la fonction, au lieu du script.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-112">Without these blank lines, `Get-Help` associates the Help topic with the function, instead of the script.</span></span>

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
  PS> .\Update-Month.ps1

  .EXAMPLE
  PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

<span data-ttu-id="c1bb1-113">La commande suivante obtient l’aide du script.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-113">The following command gets the script Help.</span></span> <span data-ttu-id="c1bb1-114">Étant donné que le script n’est pas dans un répertoire qui est listé dans la variable d’environnement PATH, la `Get-Help` commande qui obtient l’aide du script doit spécifier le chemin d’accès du script.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-114">Because the script is not in a directory that is listed in the Path environment variable, the `Get-Help` command that gets the script Help must specify the script path.</span></span>

```powershell
PS> Get-Help c:\ps-test\update-month.ps1 -full
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

            PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="c1bb1-115">Exemple 3 : descriptions des paramètres dans une instruction param</span><span class="sxs-lookup"><span data-stu-id="c1bb1-115">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="c1bb1-116">Cet exemple montre comment insérer des descriptions de paramètres dans l' `Param` instruction d’une fonction ou d’un script.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-116">This example shows how to insert parameter descriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="c1bb1-117">Ce format est particulièrement utile lorsque les descriptions des paramètres sont courtes.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-117">This format is most useful when the parameter descriptions are brief.</span></span>

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

<span data-ttu-id="c1bb1-118">Les résultats sont les mêmes que ceux de l’exemple 1.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-118">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="c1bb1-119">`Get-Help` interprète les descriptions des paramètres comme s’ils étaient accompagnés du `.Parameter` mot clé.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-119">`Get-Help` interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="c1bb1-120">Exemple 4 : redirection vers un fichier XML</span><span class="sxs-lookup"><span data-stu-id="c1bb1-120">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="c1bb1-121">Vous pouvez écrire des rubriques d’aide basées sur XML pour des fonctions et des scripts.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-121">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="c1bb1-122">Bien que l’aide basée sur les commentaires soit plus facile à implémenter, une aide XML est nécessaire si vous souhaitez contrôler plus précisément le contenu de l’aide ou si vous traduisez des rubriques d’aide en plusieurs langues. L’exemple suivant montre les premières lignes du `Update-Month.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-122">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the `Update-Month.ps1` script.</span></span> <span data-ttu-id="c1bb1-123">Le script utilise le `.ExternalHelp` mot clé pour spécifier le chemin d’accès à une rubrique d’aide XML pour le script.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-123">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="c1bb1-124">L’exemple suivant illustre l’utilisation du `.ExternalHelp` mot clé dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-124">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="c1bb1-125">Exemple 5 : redirection vers une autre rubrique d’aide</span><span class="sxs-lookup"><span data-stu-id="c1bb1-125">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="c1bb1-126">Le code suivant est un extrait du début de la `Help` fonction intégrée dans PowerShell, qui affiche un écran de texte d’aide à la fois.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-126">The following code is an excerpt from the beginning of the built-in `Help` function in PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="c1bb1-127">Étant donné que la rubrique d’aide de l’applet de commande Get-Help décrit la fonction Help, la fonction Help utilise les `.ForwardHelpTargetName` `.ForwardHelpCategory` Mots clés et pour rediriger l’utilisateur vers la rubrique d’aide de l’applet de commande Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-127">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

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

<span data-ttu-id="c1bb1-128">La commande suivante utilise cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="c1bb1-128">The following command uses this feature.</span></span> <span data-ttu-id="c1bb1-129">Quand un utilisateur tape une `Get-Help` commande pour la `Help` fonction, `Get-Help` affiche la rubrique d’aide de l’applet de commande `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="c1bb1-129">When a user types a `Get-Help` command for the `Help` function, `Get-Help` displays the Help topic for the `Get-Help` cmdlet.</span></span>

```powershell
PS> get-help help
```

```Output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```
