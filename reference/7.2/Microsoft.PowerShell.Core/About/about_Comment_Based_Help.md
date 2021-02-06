---
description: Décrit comment écrire des rubriques d’aide basées sur des commentaires pour des fonctions et des scripts.
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comment_based_help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comment_Based_Help
ms.openlocfilehash: 055f2358a8e9d3868c9fd1024be1f6adf5520356
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599147"
---
# <a name="about-comment-based-help"></a>À propos de l’aide basée sur les commentaires

## <a name="short-description"></a>Description courte
Décrit comment écrire des rubriques d’aide basées sur des commentaires pour des fonctions et des scripts.

## <a name="long-description"></a>Description longue

Vous pouvez écrire des rubriques d’aide basées sur des commentaires pour les fonctions et les scripts en utilisant des mots clés de commentaires d’aide spéciaux.

L’applet de commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) affiche une aide basée sur des commentaires dans le même format que celui dans lequel elle affiche les rubriques d’aide sur les applets de commande générées à partir de fichiers XML. Les utilisateurs peuvent utiliser tous les paramètres de `Get-Help` , tels que **detailed**, **Full**, **examples** et **Online**, pour afficher le contenu de l’aide basée sur les commentaires.

Vous pouvez également écrire des fichiers d’aide XML pour des fonctions et des scripts. Pour permettre `Get-Help` à l’applet de commande de trouver le fichier d’aide XML pour une fonction ou un script, utilisez le `.ExternalHelp` mot clé. Sans ce mot clé, `Get-Help` les rubriques d’aide XML pour les fonctions ou les scripts ne sont pas disponibles.

Cette rubrique explique comment écrire des rubriques d’aide pour les fonctions et les scripts. Pour plus d’informations sur l’affichage des rubriques d’aide relatives aux fonctions et aux scripts, consultez [obtenir-aide](xref:Microsoft.PowerShell.Core.Get-Help).

Les applets de commande [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help) et [Save-Help](xref:Microsoft.PowerShell.Core.Save-Help) fonctionnent uniquement sur les fichiers XML. L’aide actualisable ne prend pas en charge les rubriques d’aide basées sur les commentaires.

## <a name="syntax-for-comment-based-help"></a>Syntaxe pour l’aide basée sur des commentaires

La syntaxe de l’aide basée sur les commentaires est la suivante :

```
# .<help keyword>
# <help content>
```

ou

```
<#
.<help keyword>
<help content>
#>
```

L’aide basée sur les commentaires est écrite sous la forme d’une série de commentaires. Vous pouvez taper un symbole de commentaire `#` avant chaque ligne de commentaires, ou vous pouvez utiliser `<#` les `#>` symboles et pour créer un bloc de commentaires. Toutes les lignes dans le bloc de commentaires sont interprétées comme des commentaires.

Toutes les lignes d’une rubrique d’aide basée sur des commentaires doivent être contiguës. Si une rubrique d’aide basée sur des commentaires suit un commentaire qui ne fait pas partie de la rubrique d’aide, il doit y avoir au moins une ligne vide entre la dernière ligne de commentaire non-aide et le début de l’aide basée sur les commentaires.

Les mots clés définissent chaque section de l’aide basée sur des commentaires. Chaque mot clé d’aide basé sur des commentaires est précédé d’un point `.` . Les mots clés peuvent apparaître dans n’importe quel ordre. Les noms de mots clés ne respectent pas la casse.

Par exemple, le `.Description` mot clé précède une description d’une fonction ou d’un script.

```
<#
.Description
Get-Function displays the name and syntax of all functions in the session.
#>
```

Le bloc de commentaires doit contenir au moins un mot clé. Certains mots clés, tels que `.EXAMPLE` , peuvent apparaître plusieurs fois dans le même bloc de commentaires. Le contenu de l’aide pour chaque mot clé commence sur la ligne qui suit le mot clé et peut s’étendre sur plusieurs lignes.

## <a name="syntax-for-comment-based-help-in-functions"></a>Syntaxe pour l’aide basée sur les commentaires dans les fonctions

L’aide basée sur les commentaires pour une fonction peut apparaître dans l’un des trois emplacements suivants :

- Au début du corps de la fonction.
- À la fin du corps de la fonction.
- Avant le `function` mot clé. Il ne peut pas y avoir plus d’une ligne vide entre la dernière ligne de l’aide de la fonction et le `function` mot clé.

Par exemple :

```powershell
function Get-Function
{
<#
.<help keyword>
<help content>
#>

  # function logic
}
```

or

```powershell
function Get-Function
{
   # function logic

<#
.<help keyword>
<help content>
#>
}
```

or

```powershell
<#
.<help keyword>
<help content>
#>
function Get-Function { }
```

## <a name="syntax-for-comment-based-help-in-scripts"></a>Syntaxe pour l’aide basée sur les commentaires dans les scripts

L’aide sur les commentaires d’un script peut apparaître dans l’un des deux emplacements suivants du script.

- Au début du fichier de script. L’aide sur les scripts peut être précédée du script uniquement par des commentaires et des lignes vides.

  Si le premier élément du corps du script (après l’aide) est une déclaration de fonction, il doit y avoir au moins deux lignes vides entre la fin de l’aide du script et la déclaration de la fonction. Dans le cas contraire, l’aide est interprétée comme une aide pour la fonction, et non pour l’aide du script.

- À la fin du fichier de script. Toutefois, si le script est signé, placez l’aide basée sur les commentaires au début du fichier de script. La fin du script est occupée par le bloc de signature.

Par exemple :

```powershell
<#
.<help keyword>
<help content>
#>


function Get-Function { }
```

or

```powershell
function Get-Function { }

<#
.<help keyword>
<help content>
#>
```

## <a name="syntax-for-comment-based-help-in-script-modules"></a>Syntaxe pour l’aide basée sur les commentaires dans les modules de script

Dans un module de script `.psm1` , l’aide basée sur les commentaires utilise la syntaxe pour les fonctions, et non la syntaxe pour les scripts. Vous ne pouvez pas utiliser la syntaxe de script pour fournir de l’aide pour toutes les fonctions définies dans un module de script.

Par exemple, si vous utilisez le `.ExternalHelp` mot clé pour identifier les fichiers d’aide XML pour les fonctions dans un module de script, vous devez ajouter un `.ExternalHelp` Commentaire à chaque fonction.

```powershell
# .ExternalHelp <XML-file-name>
function <function-name>
{
  ...
}
```

## <a name="comment-based-help-keywords"></a>Mots clés d’aide basés sur des commentaires

Les éléments suivants sont des mots clés d’aide basés sur des commentaires valides. Ils sont répertoriés dans l’ordre dans lequel ils apparaissent généralement dans une rubrique d’aide, ainsi que l’utilisation prévue. Ces mots clés peuvent apparaître dans n’importe quel ordre dans l’aide basée sur les commentaires, et ils ne respectent pas la casse.

### <a name="synopsis"></a>. SYNOPSIS

Brève description de la fonction ou du script. Ce mot clé ne peut être utilisé qu’une seule fois dans chaque rubrique.

### <a name="description"></a>. DESCRIPTIVE

Description détaillée de la fonction ou du script. Ce mot clé ne peut être utilisé qu’une seule fois dans chaque rubrique.

### <a name="parameter"></a>. PARAMÈTRE

Description d’un paramètre. Ajoutez un `.PARAMETER` mot clé pour chaque paramètre dans la syntaxe de la fonction ou du script.

Tapez le nom du paramètre sur la même ligne que le `.PARAMETER` mot clé. Tapez la description du paramètre sur les lignes qui suivent le `.PARAMETER` mot clé. Windows PowerShell interprète tout le texte entre la `.PARAMETER` ligne et le mot clé suivant ou la fin du bloc de commentaires dans le cadre de la description du paramètre.
La description peut inclure des sauts de paragraphe.

```
.PARAMETER  <Parameter-Name>
```

Les mots clés des paramètres peuvent apparaître dans n’importe quel ordre dans le bloc de commentaires, mais la syntaxe de la fonction ou du script détermine l’ordre dans lequel les paramètres (et leurs descriptions) s’affichent dans la rubrique d’aide. Pour modifier l’ordre, modifiez la syntaxe.

Vous pouvez également spécifier une description de paramètre en plaçant un commentaire dans la syntaxe de la fonction ou du script juste avant le nom de la variable de paramètre. Pour que cela fonctionne, vous devez également disposer d’un bloc de commentaires avec au moins un mot clé.

Si vous utilisez à la fois un commentaire de syntaxe et un `.PARAMETER` mot clé, la description associée au `.PARAMETER` mot clé est utilisée et le commentaire de syntaxe est ignoré.

```powershell
<#
.SYNOPSIS
    Short description here
#>
function Verb-Noun {
    [CmdletBinding()]
    param (
        # This is the same as .Parameter
        [string]$Computername
    )
    # Verb the Noun on the computer
}
```

### <a name="example"></a>. TELS

Exemple de commande qui utilise la fonction ou le script, éventuellement suivi d’un exemple de sortie et d’une description. Répétez ce mot clé pour chaque exemple.

### <a name="inputs"></a>. PORT

Types .NET d’objets qui peuvent être dirigés vers la fonction ou le script. Vous pouvez également inclure une description des objets d’entrée.

### <a name="outputs"></a>. ENVERRA

Type .NET des objets que l’applet de commande retourne. Vous pouvez également inclure une description des objets retournés.

### <a name="notes"></a>. NOTES

Informations supplémentaires sur la fonction ou le script.

### <a name="link"></a>. LIEN

Nom d’une rubrique associée. La valeur apparaît sur la ligne sous le «. LINK» et doit être précédé d’un symbole de commentaire `#` ou inclus dans le bloc de commentaires.

Répétez le `.LINK` mot clé pour chaque rubrique associée.

Ce contenu apparaît dans la section Liens connexes de la rubrique d’aide.

Le `.Link` contenu du mot clé peut également inclure une Uniform Resource Identifier (Uri) à une version en ligne de la même rubrique d’aide. La version en ligne s’ouvre lorsque vous utilisez le paramètre **Online** de `Get-Help` . L’URI doit commencer par « http » ou « HTTPS ».

### <a name="component"></a>. -

Nom de la technologie ou de la fonctionnalité utilisée par la fonction ou le script, ou à laquelle elle est associée. Le paramètre **Component** de `Get-Help` utilise cette valeur pour filtrer les résultats de recherche retournés par `Get-Help` .

### <a name="role"></a>. ACTIF

Nom du rôle d’utilisateur pour la rubrique d’aide. Le paramètre **role** de `Get-Help` utilise cette valeur pour filtrer les résultats de recherche retournés par `Get-Help` .

### <a name="functionality"></a>. SES

Mots clés qui décrivent l’utilisation prévue de la fonction. Le paramètre de **fonctionnalité** de `Get-Help` utilise cette valeur pour filtrer les résultats de recherche retournés par `Get-Help` .

### <a name="forwardhelptargetname"></a>. FORWARDHELPTARGETNAME

Redirige vers la rubrique d’aide pour la commande spécifiée. Vous pouvez rediriger les utilisateurs vers n’importe quelle rubrique d’aide, y compris les rubriques d’aide d’une fonction, d’un script, d’une applet de commande ou d’un fournisseur.

```powershell
# .FORWARDHELPTARGETNAME <Command-Name>
```

### <a name="forwardhelpcategory"></a>. FORWARDHELPCATEGORY

Spécifie la catégorie d’aide de l’élément dans `.ForwardHelpTargetName` . Les valeurs valides sont `Alias` , `Cmdlet` , `HelpFile` , `Function` , `Provider` , `General` , `FAQ` , `Glossary` , `ScriptCommand` , `ExternalScript` , `Filter` ou `All` . Utilisez ce mot clé pour éviter les conflits lorsqu’il existe des commandes portant le même nom.

```powershell
# .FORWARDHELPCATEGORY <Category>
```

### <a name="remotehelprunspace"></a>. REMOTEHELPRUNSPACE

Spécifie une session qui contient la rubrique d’aide. Entrez une variable qui contient un objet **PSSession** . Ce mot clé est utilisé par l’applet de commande [Export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) pour rechercher les rubriques d’aide pour les commandes exportées.

```powershell
# .REMOTEHELPRUNSPACE <PSSession-variable>
```

### <a name="externalhelp"></a>. Commentaire ExternalHelp

Spécifie un fichier d’aide XML pour le script ou la fonction.

```powershell
# .EXTERNALHELP <XML Help File>
```

Le `.ExternalHelp` mot clé est requis lorsqu’une fonction ou un script est documenté dans des fichiers XML. Sans ce mot clé, `Get-Help` le fichier d’aide XML pour la fonction ou le script est introuvable.

Le `.ExternalHelp` mot clé est prioritaire sur les autres mots clés d’aide basés sur des commentaires. Si `.ExternalHelp` est présent, `Get-Help` n’affiche pas l’aide basée sur les commentaires, même s’il ne trouve pas de rubrique d’aide qui correspond à la valeur du `.ExternalHelp` mot clé.

Si la fonction est exportée par un module, définissez la valeur du `.ExternalHelp` mot clé sur un nom de fichier sans chemin d’accès. `Get-Help` recherche le nom de fichier spécifié dans un sous-répertoire spécifique à la langue du répertoire du module. Il n’existe aucune condition requise pour le nom du fichier d’aide XML pour une fonction, mais il est recommandé d’utiliser le format suivant :

```
<ScriptModule.psm1>-help.xml
```

Si la fonction n’est pas incluse dans un module, incluez un chemin d’accès au fichier d’aide XML. Si la valeur inclut un chemin d’accès et que le chemin d’accès contient des sous-répertoires spécifiques à la culture de l’interface utilisateur, `Get-Help` recherche les sous-répertoires de manière récursive pour un fichier XML portant le nom du script ou de la fonction conformément aux normes de langue de secours établies pour Windows, tout comme dans un répertoire de module.

Pour plus d’informations sur le format de fichier d’aide XML de l’applet de commande, consultez [Comment écrire l’aide sur les applets de](/powershell/scripting/developer/help/writing-comment-based-help-topics)commande.

## <a name="autogenerated-content"></a>Contenu généré automatiquement

Le nom, la syntaxe, la liste de paramètres, la table d’attributs des paramètres, les paramètres communs et les notes sont générés automatiquement par l’applet de commande `Get-Help` .

### <a name="name"></a>Nom

La section **nom** d’une rubrique d’aide de la fonction est extraite du nom de la fonction dans la syntaxe de la fonction. Le **nom** d’une rubrique d’aide de script est extrait du nom de fichier du script. Pour modifier le nom ou la mise en majuscules, modifiez la syntaxe de la fonction ou le nom de fichier du script.

### <a name="syntax"></a>Syntaxe

La section **syntaxe** de la rubrique d’aide est générée à partir de la syntaxe de la fonction ou du script. Pour ajouter des détails à la syntaxe de la rubrique d’aide, comme le type .NET d’un paramètre, ajoutez les détails à la syntaxe. Si vous ne spécifiez pas de type de paramètre, le type d' **objet** est inséré en tant que valeur par défaut.

### <a name="parameter-list"></a>Liste de paramètres

La liste de paramètres de la rubrique d’aide est générée à partir de la syntaxe de la fonction ou du script et des descriptions que vous ajoutez à l’aide du `.Parameter` mot clé. Les paramètres de fonction s’affichent dans la section **paramètres** de la rubrique d’aide dans l’ordre dans lequel ils apparaissent dans la syntaxe de la fonction ou du script. L’orthographe et la mise en majuscules des noms de paramètres proviennent également de la syntaxe. Elle n’est pas affectée par le nom de paramètre spécifié par le `.Parameter` mot clé.

### <a name="common-parameters"></a>Paramètres communs

Les **paramètres communs** sont ajoutés à la liste de syntaxe et de paramètres de la rubrique d’aide, même s’ils n’ont aucun effet. Pour plus d’informations sur les paramètres communs, consultez [about_CommonParameters](about_CommonParameters.md).

### <a name="parameter-attribute-table"></a>Table d’attributs de paramètre

`Get-Help` génère la table d’attributs de paramètres qui apparaît lorsque vous utilisez le paramètre **complet** ou le paramètre de **paramètre** de `Get-Help` . La valeur des attributs **requis**, de **position** et de valeur **par défaut** est extraite de la syntaxe de la fonction ou du script.

Les valeurs par défaut et une valeur pour **accepter les caractères génériques** n’apparaissent pas dans la table attribut de paramètre, même lorsqu’elles sont définies dans la fonction ou le script. Pour aider les utilisateurs, fournissez ces informations dans la description du paramètre.

### <a name="remarks"></a>Remarques

La section **Notes** de la rubrique d’aide est générée automatiquement à partir du nom de la fonction ou du script. Vous ne pouvez pas modifier ou affecter son contenu.

## <a name="examples"></a>Exemples

### <a name="comment-based-help-for-a-function"></a>Aide sur les commentaires pour une fonction

L’exemple de fonction suivant comprend une aide basée sur des commentaires :

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

System.String. Add-Extension returns a string with the extension
or file name.

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

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

Les résultats sont les suivants :

```powershell
Get-Help -Name "Add-Extension" -Full
```

```Output
NAME

Add-Extension

SYNOPSIS

Adds a file name extension to a supplied name.

SYNTAX

Add-Extension [[-Name] <String>] [[-Extension] <String>]
[<CommonParameters>]

DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

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

System.String. Add-Extension returns a string with the extension or
file name.

Example 1

PS> extension -name "File"
File.txt

Example 2

PS> extension -name "File" -extension "doc"
File.doc

Example 3

PS> extension "File" "doc"
File.doc

RELATED LINKS

http://www.fabrikam.com/extension.html
Set-Item
```

### <a name="parameter-descriptions-in-function-syntax"></a>Descriptions des paramètres dans la syntaxe de fonction

Cet exemple est identique au précédent, hormis le fait que les descriptions des paramètres sont insérées dans la syntaxe de la fonction. Ce format est particulièrement utile lorsque les descriptions sont courtes.

```powershell
function Add-Extension
{
param
(

[string]
#Specifies the file name.
$name,

[string]
#Specifies the file name extension. "Txt" is the default.
$extension = "txt"
)

$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

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

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

### <a name="comment-based-help-for-a-script"></a>Aide sur les commentaires pour un script

L’exemple de script suivant comprend une aide basée sur des commentaires. Notez les lignes vides entre la fermeture `#>` et l' `Param` instruction. Dans un script qui n’a pas d' `Param` instruction, il doit y avoir au moins deux lignes vides entre le commentaire final de la rubrique d’aide et la première déclaration de fonction. Sans ces lignes vides, `Get-Help` associe la rubrique d’aide à la fonction, et non pas au script.

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

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath `
C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
...
```

La commande suivante obtient l’aide du script. Étant donné que le script n’est pas dans un répertoire qui est listé dans la `$env:Path` variable d’environnement, la `Get-Help` commande qui obtient l’aide du script doit spécifier le chemin d’accès du script.

```powershell
Get-Help -Path .\update-month.ps1 -Full
```

```Output
# NAME

C:\ps-test\Update-Month.ps1

# SYNOPSIS

Performs monthly data updates.

# SYNTAX

C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
<String>] [<CommonParameters>]

# DESCRIPTION

The Update-Month.ps1 script updates the registry with new data
generated during the past month and generates a report.

# PARAMETERS

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

# INPUTS

None. You cannot pipe objects to Update-Month.ps1.

# OUTPUTS

None. Update-Month.ps1 does not generate any output.

Example 1

PS> .\Update-Month.ps1

Example 2

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

Example 3

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
C:\Reports\2009\January.csv

# RELATED LINKS
```

### <a name="redirecting-to-an-xml-file"></a>Redirection vers un fichier XML

Vous pouvez écrire des rubriques d’aide basées sur XML pour des fonctions et des scripts. Bien que l’aide basée sur les commentaires soit plus facile à implémenter, une aide XML est nécessaire pour obtenir de l’aide actualisable et pour fournir des rubriques d’aide dans plusieurs langues.

L’exemple suivant montre les premières lignes du script de Update-Month.ps1.
Le script utilise le `.ExternalHelp` mot clé pour spécifier le chemin d’accès à une rubrique d’aide XML pour le script.

Notez que la valeur du `.ExternalHelp` mot clé apparaît sur la même ligne que le mot clé. Tout autre placement est inefficace.

```powershell
# .ExternalHelp C:\MyScripts\Update-Month-Help.xml

param ([string]$InputPath, [string]$OutPutPath)
function Get-Data { }
...
```

Les exemples suivants illustrent trois emplacements valides du `.ExternalHelp` mot clé dans une fonction.

```powershell
function Add-Extension
{
# .ExternalHelp C:\ps-test\Add-Extension.xml

param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

```powershell
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name

# .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

```powershell
# .ExternalHelp C:\ps-test\Add-Extension.xml
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

### <a name="redirecting-to-a-different-help-topic"></a>Redirection vers une autre rubrique d’aide

Le code suivant est un extrait du début de la fonction d’aide intégrée dans PowerShell, qui affiche un écran de texte d’aide à la fois.
Étant donné que la rubrique d’aide de l’applet de commande `Get-Help` décrit la fonction d’aide, la fonction d’aide utilise les `.ForwardHelpTargetName` `.ForwardHelpCategory` Mots clés et pour rediriger l’utilisateur vers la `Get-Help` rubrique d’aide de l’applet de commande.

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

La commande suivante utilise cette fonctionnalité :

```powershell
Get-Help -Name help
```

```Output
NAME

Get-Help

SYNOPSIS

Displays information about PowerShell cmdlets and concepts.
...
```

## <a name="see-also"></a>Voir aussi

[about_Functions](about_Functions.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Scripts](about_Scripts.md)

[Comment écrire l’aide sur les applets de commande](https://go.microsoft.com/fwlink/?LinkID=123415)
