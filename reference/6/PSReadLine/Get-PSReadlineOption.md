---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSReadLine
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlineoption?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineOption
ms.openlocfilehash: 624978c94c9ed24c07c6dad384236c852b8a7fde
ms.sourcegitcommit: 105c69ecedfe5180d8c12e8015d667c5f1a71579
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "93201118"
---
# <span data-ttu-id="1b725-103">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="1b725-103">Get-PSReadLineOption</span></span>

## <span data-ttu-id="1b725-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1b725-104">SYNOPSIS</span></span>
<span data-ttu-id="1b725-105">Obtient des valeurs pour les options qui peuvent être configurées.</span><span class="sxs-lookup"><span data-stu-id="1b725-105">Gets values for the options that can be configured.</span></span>

## <span data-ttu-id="1b725-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1b725-106">SYNTAX</span></span>

```
Get-PSReadLineOption [<CommonParameters>]
```

## <span data-ttu-id="1b725-107">Description</span><span class="sxs-lookup"><span data-stu-id="1b725-107">DESCRIPTION</span></span>

<span data-ttu-id="1b725-108">L' `Get-PSReadLineOption` applet de commande retourne l’état actuel des paramètres qui peuvent être configurés à l’aide de l’applet de commande `Set-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="1b725-108">The `Get-PSReadLineOption` cmdlet returns the current state of the settings that can be configured by using the `Set-PSReadLineOption` cmdlet.</span></span> <span data-ttu-id="1b725-109">Vous pouvez utiliser l’objet retourné pour modifier les options de **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="1b725-109">You can use the returned object to change **PSReadLine** options.</span></span> <span data-ttu-id="1b725-110">Cela offre un moyen légèrement plus simple de définir des options de coloration de syntaxe pour plusieurs types de jetons.</span><span class="sxs-lookup"><span data-stu-id="1b725-110">This provides a slightly simpler way to set syntax coloring options for multiple kinds of tokens.</span></span>

## <span data-ttu-id="1b725-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1b725-111">EXAMPLES</span></span>

### <span data-ttu-id="1b725-112">Exemple 1 : afficher les options et leurs valeurs</span><span class="sxs-lookup"><span data-stu-id="1b725-112">Example 1: Get options and their values</span></span>

```powershell
Get-PSReadLineOption
```

```Output
EditMode                               : Windows
AddToHistoryHandler                    :
HistoryNoDuplicates                    : True
HistorySavePath                        : C:\Users\username\AppData\Roaming\Microsoft\Windows\
                                         PowerShell\PSReadLine\ConsoleHost_history.txt
HistorySaveStyle                       : SaveIncrementally
HistorySearchCaseSensitive             : False
HistorySearchCursorMovesToEnd          : False
MaximumHistoryCount                    : 4096
ContinuationPrompt                     : >>
ExtraPromptLineCount                   : 0
PromptText                             : {> }
BellStyle                              : Audible
DingDuration                           : 50
DingTone                               : 1221
CommandsToValidateScriptBlockArguments : {ForEach-Object, %, Invoke-Command, icm...}
CommandValidationHandler               :
CompletionQueryItems                   : 100
MaximumKillRingCount                   : 10
ShowToolTips                           : True
ViModeIndicator                        : None
WordDelimiters                         : ;:,.[]{}()/\|^&*-=+'"---
AnsiEscapeTimeout                      : 100
CommandColor                           : "`e[93m"
CommentColor                           : "`e[32m"
ContinuationPromptColor                : "`e[97m"
DefaultTokenColor                      : "`e[97m"
EmphasisColor                          : "`e[96m"
ErrorColor                             : "`e[91m"
KeywordColor                           : "`e[92m"
MemberColor                            : "`e[97m"
NumberColor                            : "`e[97m"
OperatorColor                          : "`e[90m"
ParameterColor                         : "`e[90m"
SelectionColor                         : "`e[30;107m"
StringColor                            : "`e[36m"
TypeColor                              : "`e[37m"
VariableColor                          : "`e[92m"
```

<span data-ttu-id="1b725-113">Cette commande retourne la liste des options PSReadLine disponibles et leurs valeurs actuelles.</span><span class="sxs-lookup"><span data-stu-id="1b725-113">This command returns the list of available PSReadLine options and their current values.</span></span>

## <span data-ttu-id="1b725-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1b725-114">PARAMETERS</span></span>

### <span data-ttu-id="1b725-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1b725-115">CommonParameters</span></span>

<span data-ttu-id="1b725-116">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1b725-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1b725-117">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1b725-117">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1b725-118">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1b725-118">INPUTS</span></span>

### <span data-ttu-id="1b725-119">Aucun</span><span class="sxs-lookup"><span data-stu-id="1b725-119">None</span></span>

<span data-ttu-id="1b725-120">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1b725-120">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="1b725-121">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1b725-121">OUTPUTS</span></span>

### <span data-ttu-id="1b725-122">Microsoft. PowerShell. PSConsoleReadLineOptions</span><span class="sxs-lookup"><span data-stu-id="1b725-122">Microsoft.PowerShell.PSConsoleReadLineOptions</span></span>

<span data-ttu-id="1b725-123">Instance des options actuelles.</span><span class="sxs-lookup"><span data-stu-id="1b725-123">An instance of the current options.</span></span> <span data-ttu-id="1b725-124">La modification des valeurs de propriété de cet objet met directement à jour les paramètres dans PSReadLine sans appeler `Set-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="1b725-124">Changing the property values of this object updates the settings in PSReadLine directly without invoking `Set-PSReadLineOption`.</span></span>

## <span data-ttu-id="1b725-125">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1b725-125">NOTES</span></span>

## <span data-ttu-id="1b725-126">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1b725-126">RELATED LINKS</span></span>

[<span data-ttu-id="1b725-127">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="1b725-127">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="1b725-128">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="1b725-128">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="1b725-129">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="1b725-129">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="1b725-130">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="1b725-130">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
