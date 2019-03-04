---
title: Exemples de l’aide basée sur le commentaire | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 868194a2-17e9-4184-bc36-c04a33f26494
caps.latest.revision: 4
ms.openlocfilehash: dbccaf5b8e48a1c4d924bc0ec4ea09b25e10adf0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857965"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="a3a59-102">Exemples d’aide basée sur les commentaires</span><span class="sxs-lookup"><span data-stu-id="a3a59-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="a3a59-103">Cette rubrique inclut un exemple qui montrent comment utiliser l’aide basée sur un commentaire pour les scripts et fonctions.</span><span class="sxs-lookup"><span data-stu-id="a3a59-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="a3a59-104">Exemple 1 : Aide relative à une fonction en fonction du commentaire</span><span class="sxs-lookup"><span data-stu-id="a3a59-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="a3a59-105">L’exemple de fonction suivant inclut l’aide basée sur le commentaire.</span><span class="sxs-lookup"><span data-stu-id="a3a59-105">The following sample function includes comment-based Help.</span></span>

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

<span data-ttu-id="a3a59-106">La sortie suivante montre les résultats d’une commande Get-Help qui affiche l’aide de la fonction Ajouter l’Extension.</span><span class="sxs-lookup"><span data-stu-id="a3a59-106">The following output shows the results of a Get-Help command that displays the help for the Add-Extension function.</span></span>

```powershell
C:\PS> get-help add-extension -full
```

```output
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

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="a3a59-107">Exemple 2 : Aide basée sur un Script</span><span class="sxs-lookup"><span data-stu-id="a3a59-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="a3a59-108">L’exemple de fonction suivant inclut l’aide basée sur le commentaire.</span><span class="sxs-lookup"><span data-stu-id="a3a59-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="a3a59-109">Notez que les lignes vides entre la fermeture **#>** et `Param` instruction.</span><span class="sxs-lookup"><span data-stu-id="a3a59-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="a3a59-110">Dans un script qui n’a pas un `Param` instruction, il doit être d’au moins deux lignes vides entre le commentaire final dans la rubrique d’aide et de la première déclaration de fonction.</span><span class="sxs-lookup"><span data-stu-id="a3a59-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="a3a59-111">Sans ces lignes vides, Get-Help associe la rubrique d’aide à la fonction, plutôt que le script.</span><span class="sxs-lookup"><span data-stu-id="a3a59-111">Without these blank lines, Get-Help associates the Help topic with the function, instead of the script.</span></span>

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

<span data-ttu-id="a3a59-112">La commande suivante obtient le script Help.</span><span class="sxs-lookup"><span data-stu-id="a3a59-112">The following command gets the script Help.</span></span> <span data-ttu-id="a3a59-113">Étant donné que le script n’est pas n un répertoire qui est répertorié dans la variable d’environnement Path, la commande Get-Help qui obtient le script Help doit spécifier le chemin d’accès du script.</span><span class="sxs-lookup"><span data-stu-id="a3a59-113">Because the script is not n a directory that is listed in the Path environment variable, the Get-Help command that gets the script Help must specify the script path.</span></span>

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```output
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

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="a3a59-114">Exemple 3 : Descriptions de paramètre dans une instruction Param</span><span class="sxs-lookup"><span data-stu-id="a3a59-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="a3a59-115">Cet exemple montre comment insérer parameterdescriptions dans la `Param` instruction d’une fonction ou un script.</span><span class="sxs-lookup"><span data-stu-id="a3a59-115">This example show how to insert parameterdescriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="a3a59-116">Ce format est particulièrement utile lorsque les descriptions de paramètre sont brèves.</span><span class="sxs-lookup"><span data-stu-id="a3a59-116">This format is most useful when the parameter descriptions are brief.</span></span>

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

<span data-ttu-id="a3a59-117">Les résultats sont les mêmes que les résultats par exemple 1.</span><span class="sxs-lookup"><span data-stu-id="a3a59-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="a3a59-118">Get-Help interprète les descriptions de paramètre comme s’ils étaient accompagnés le `.Parameter` mot clé.</span><span class="sxs-lookup"><span data-stu-id="a3a59-118">Get-Help interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="a3a59-119">Exemple 4 :  Redirection vers un fichier XML</span><span class="sxs-lookup"><span data-stu-id="a3a59-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="a3a59-120">Vous pouvez écrire des rubriques d’aide basé sur XML pour les fonctions et les scripts.</span><span class="sxs-lookup"><span data-stu-id="a3a59-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="a3a59-121">Bien que l’aide basée sur le commentaire est plus facile à implémenter, basé sur XML Help est nécessaire si vous souhaitez un contrôle plus précis sur le contenu d’aide ou si vous traduisez des rubriques d’aide en plusieurs langues. L’exemple suivant montre les premières lignes du script Month.ps1 de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="a3a59-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the Update-Month.ps1 script.</span></span> <span data-ttu-id="a3a59-122">Le script utilise le `.ExternalHelp` mot clé pour spécifier le chemin d’accès à une rubrique d’aide basé sur XML pour le script.</span><span class="sxs-lookup"><span data-stu-id="a3a59-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="a3a59-123">L’exemple suivant illustre l’utilisation de la `.ExternalHelp` mot clé dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="a3a59-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="a3a59-124">Exemple 5 :  Redirection vers une autre rubrique d’aide</span><span class="sxs-lookup"><span data-stu-id="a3a59-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="a3a59-125">Le code suivant est un extrait à partir du début des prédéfinis `Help` (fonction) dans Windows PowerShell, qui affiche un écran de texte d’aide à la fois.</span><span class="sxs-lookup"><span data-stu-id="a3a59-125">The following code is an excerpt from the beginning of the built-in `Help` function in Windows PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="a3a59-126">Étant donné que la rubrique d’aide pour l’applet de commande Get-Help décrit la fonction d’aide, la fonction Help utilise le `.ForwardHelpTargetName` et `.ForwardHelpCategory` mots clés pour rediriger l’utilisateur vers la rubrique d’aide applet de commande Get-Help.</span><span class="sxs-lookup"><span data-stu-id="a3a59-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

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

<span data-ttu-id="a3a59-127">La commande suivante utilise cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="a3a59-127">The following command uses this feature.</span></span> <span data-ttu-id="a3a59-128">Lorsqu’un utilisateur tape une commande Get-Help pour la fonction Help, Get-Help affiche la rubrique d’aide pour l’applet de commande Get-Help.</span><span class="sxs-lookup"><span data-stu-id="a3a59-128">When a user types a Get-Help command for the Help function, Get-Help displays the Help topic for the Get-Help cmdlet.</span></span>

```powershell
C:\PS> get-help help
```

```output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```