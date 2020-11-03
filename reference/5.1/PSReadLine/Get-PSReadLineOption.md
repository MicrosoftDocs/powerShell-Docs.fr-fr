---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSReadline
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlineoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineOption
ms.openlocfilehash: 7f731014e5a240e0c756640144ff7cae5e48f051
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208653"
---
# <span data-ttu-id="d3649-103">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="d3649-103">Get-PSReadLineOption</span></span>

## <span data-ttu-id="d3649-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d3649-104">SYNOPSIS</span></span>
<span data-ttu-id="d3649-105">Obtient des valeurs pour les options qui peuvent être configurées.</span><span class="sxs-lookup"><span data-stu-id="d3649-105">Gets values for the options that can be configured.</span></span>

## <span data-ttu-id="d3649-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d3649-106">SYNTAX</span></span>

```
Get-PSReadLineOption [<CommonParameters>]
```

## <span data-ttu-id="d3649-107">Description</span><span class="sxs-lookup"><span data-stu-id="d3649-107">DESCRIPTION</span></span>

<span data-ttu-id="d3649-108">L' `Get-PSReadLineOption` applet de commande retourne l’état actuel des paramètres qui peuvent être configurés à l’aide de l’applet de commande `Set-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="d3649-108">The `Get-PSReadLineOption` cmdlet returns the current state of the settings that can be configured by using the `Set-PSReadLineOption` cmdlet.</span></span> <span data-ttu-id="d3649-109">Vous pouvez utiliser l’objet retourné pour modifier les options de **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="d3649-109">You can use the returned object to change **PSReadLine** options.</span></span> <span data-ttu-id="d3649-110">Cela offre un moyen légèrement plus simple de définir des options de coloration de syntaxe pour plusieurs types de jetons.</span><span class="sxs-lookup"><span data-stu-id="d3649-110">This provides a slightly simpler way to set syntax coloring options for multiple kinds of tokens.</span></span>

## <span data-ttu-id="d3649-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d3649-111">EXAMPLES</span></span>

### <span data-ttu-id="d3649-112">Exemple 1 : afficher les options et leurs valeurs</span><span class="sxs-lookup"><span data-stu-id="d3649-112">Example 1: Get options and their values</span></span>

```powershell
Get-PSReadLineOption
```

```Output
EditMode                               : Windows
AddToHistoryHandler                    : System.Func`2[System.String,System.Object]
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
CommandColor                           : "$([char]0x1b)[93m"
CommentColor                           : "$([char]0x1b)[32m"
ContinuationPromptColor                : "$([char]0x1b)[37m"
DefaultTokenColor                      : "$([char]0x1b)[37m"
EmphasisColor                          : "$([char]0x1b)[96m"
ErrorColor                             : "$([char]0x1b)[91m"
KeywordColor                           : "$([char]0x1b)[92m"
MemberColor                            : "$([char]0x1b)[97m"
NumberColor                            : "$([char]0x1b)[97m"
OperatorColor                          : "$([char]0x1b)[90m"
ParameterColor                         : "$([char]0x1b)[90m"
SelectionColor                         : "$([char]0x1b)[30;47m"
StringColor                            : "$([char]0x1b)[36m"
TypeColor                              : "$([char]0x1b)[37m"
VariableColor                          : "$([char]0x1b)[92m"
```

<span data-ttu-id="d3649-113">Cette commande retourne la liste des options PSReadLine disponibles et leurs valeurs actuelles.</span><span class="sxs-lookup"><span data-stu-id="d3649-113">This command returns the list of available PSReadLine options and their current values.</span></span>

## <span data-ttu-id="d3649-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d3649-114">PARAMETERS</span></span>

### <span data-ttu-id="d3649-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d3649-115">CommonParameters</span></span>

<span data-ttu-id="d3649-116">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d3649-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d3649-117">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d3649-117">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d3649-118">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d3649-118">INPUTS</span></span>

### <span data-ttu-id="d3649-119">Aucun</span><span class="sxs-lookup"><span data-stu-id="d3649-119">None</span></span>

<span data-ttu-id="d3649-120">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d3649-120">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="d3649-121">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d3649-121">OUTPUTS</span></span>

### <span data-ttu-id="d3649-122">Microsoft. PowerShell. PSConsoleReadLineOptions</span><span class="sxs-lookup"><span data-stu-id="d3649-122">Microsoft.PowerShell.PSConsoleReadLineOptions</span></span>

<span data-ttu-id="d3649-123">Instance des options actuelles.</span><span class="sxs-lookup"><span data-stu-id="d3649-123">An instance of the current options.</span></span> <span data-ttu-id="d3649-124">La modification des valeurs de propriété de cet objet met directement à jour les paramètres dans PSReadLine sans appeler `Set-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="d3649-124">Changing the property values of this object updates the settings in PSReadLine directly without invoking `Set-PSReadLineOption`.</span></span>

## <span data-ttu-id="d3649-125">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d3649-125">NOTES</span></span>

## <span data-ttu-id="d3649-126">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d3649-126">RELATED LINKS</span></span>

[<span data-ttu-id="d3649-127">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="d3649-127">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="d3649-128">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="d3649-128">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="d3649-129">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="d3649-129">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="d3649-130">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="d3649-130">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
