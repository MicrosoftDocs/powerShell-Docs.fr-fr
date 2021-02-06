---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: 7e4f4adf60a4f6386c646d92ada0003f239f05f4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603666"
---
# <span data-ttu-id="0a9a4-102">Get-Error</span><span class="sxs-lookup"><span data-stu-id="0a9a4-102">Get-Error</span></span>

## <span data-ttu-id="0a9a4-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0a9a4-103">SYNOPSIS</span></span>

<span data-ttu-id="0a9a4-104">Obtient et affiche les messages d’erreur les plus récents de la session active.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-104">Gets and displays the most recent error messages from the current session.</span></span>

## <span data-ttu-id="0a9a4-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="0a9a4-105">SYNTAX</span></span>

### <span data-ttu-id="0a9a4-106">La plus récente (par défaut)</span><span class="sxs-lookup"><span data-stu-id="0a9a4-106">Newest (Default)</span></span>

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="0a9a4-107">Error</span><span class="sxs-lookup"><span data-stu-id="0a9a4-107">Error</span></span>

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="0a9a4-108">Description</span><span class="sxs-lookup"><span data-stu-id="0a9a4-108">DESCRIPTION</span></span>

<span data-ttu-id="0a9a4-109">L' `Get-Error` applet de commande obtient un objet **PSExtendedError** qui représente les détails de l’erreur actuelle de la dernière erreur qui s’est produite dans la session.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-109">The `Get-Error` cmdlet gets a **PSExtendedError** object that represents the current error details from the last error that occurred in the session.</span></span>

<span data-ttu-id="0a9a4-110">Vous pouvez utiliser `Get-Error` pour afficher un nombre spécifié d’erreurs qui se sont produites dans la session active à l’aide du paramètre le plus **récent** .</span><span class="sxs-lookup"><span data-stu-id="0a9a4-110">You can use `Get-Error` to display a specified number of errors that have occurred in the current session using the **Newest** parameter.</span></span>

<span data-ttu-id="0a9a4-111">L' `Get-Error` applet de commande reçoit également des objets d’erreur d’une collection, tels que `$Error` , pour afficher plusieurs erreurs à partir de la session active.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-111">The `Get-Error` cmdlet also receives error objects from a collection, such as `$Error`, to display multiple errors from the current session.</span></span>

## <span data-ttu-id="0a9a4-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0a9a4-112">EXAMPLES</span></span>

### <span data-ttu-id="0a9a4-113">Exemple 1 : récupérer les détails de l’erreur la plus récente</span><span class="sxs-lookup"><span data-stu-id="0a9a4-113">Example 1: Get the most recent error details</span></span>

<span data-ttu-id="0a9a4-114">Dans cet exemple, `Get-Error` affiche les détails de l’erreur la plus récente qui s’est produite dans la session active.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-114">In this example, `Get-Error` displays the details of the most recent error that occurred in the current session.</span></span>

```powershell
Get-Childitem -path /NoRealDirectory
Get-Error
```

```
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.

Exception             :
    ErrorRecord          :
        Exception             :
            Message : Cannot find path 'C:\NoRealDirectory' because it does not exist.
            HResult : -2146233087
        TargetObject          : C:\NoRealDirectory
        CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [], ParentContainsErrorRecordException
        FullyQualifiedErrorId : PathNotFound
    ItemName             : C:\NoRealDirectory
    SessionStateCategory : Drive
    TargetSite           :
        Name          : GetChildItems
        DeclaringType : System.Management.Automation.SessionStateInternal
        MemberType    : Method
        Module        : System.Management.Automation.dll
    StackTrace           :
   at System.Management.Automation.SessionStateInternal.GetChildItems(String path, Boolean recurse, UInt32 depth,
CmdletProviderContext context)
   at System.Management.Automation.ChildItemCmdletProviderIntrinsics.Get(String path, Boolean recurse, UInt32
depth, CmdletProviderContext context)
   at Microsoft.PowerShell.Commands.GetChildItemCommand.ProcessRecord()
    Message              : Cannot find path 'C:\NoRealDirectory' because it does not exist.
    Source               : System.Management.Automation
    HResult              : -2146233087
TargetObject          : C:\NoRealDirectory
CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [Get-ChildItem], ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
InvocationInfo        :
    MyCommand        : Get-ChildItem
    ScriptLineNumber : 1
    OffsetInLine     : 1
    HistoryId        : 57
    Line             : Get-Childitem -path c:\NoRealDirectory
    PositionMessage  : At line:1 char:1
                       + Get-Childitem -path c:\NoRealDirectory
                       + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    InvocationName   : Get-Childitem
    CommandOrigin    : Internal
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo :
```

### <span data-ttu-id="0a9a4-115">Exemple 2 : récupérer le nombre spécifié de messages d’erreur qui se sont produits dans la session active</span><span class="sxs-lookup"><span data-stu-id="0a9a4-115">Example 2: Get the specified number of error messages that occurred in the current session</span></span>

<span data-ttu-id="0a9a4-116">Cet exemple montre comment utiliser `Get-Error` avec le paramètre le plus **récent** .</span><span class="sxs-lookup"><span data-stu-id="0a9a4-116">This example shows how to use `Get-Error` with the **Newest** parameter.</span></span> <span data-ttu-id="0a9a4-117">Dans cet exemple, le plus **récent** retourne les détails des 3 erreurs les plus récentes qui se sont produites dans cette session.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-117">In this example, **Newest** returns the details of the 3 newest errors that occurred in this session.</span></span>

```powershell
Get-Error -Newest 3
```

### <span data-ttu-id="0a9a4-118">Exemple 3 : envoyer une collection d’erreurs pour recevoir des messages détaillés</span><span class="sxs-lookup"><span data-stu-id="0a9a4-118">Example 3: Send a collection of errors to receive detailed messages</span></span>

<span data-ttu-id="0a9a4-119">La `$Error` variable automatique contient un tableau d’objets d’erreur dans la session active.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-119">The `$Error` automatic variable contains an array of error objects in the current session.</span></span> <span data-ttu-id="0a9a4-120">Le tableau d’objets peut être redirigé vers `Get-Error` pour recevoir des messages d’erreur détaillés.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-120">The array of objects can be piped to `Get-Error` to receive detailed error messages.</span></span>

<span data-ttu-id="0a9a4-121">Dans cet exemple, `$Error` est dirigé vers l' `Get-Error` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-121">In this example, `$Error` is piped to the `Get-Error` cmdlet.</span></span> <span data-ttu-id="0a9a4-122">le résultat est la liste des messages d’erreur détaillés, comme le résultat de l’exemple 1.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-122">the result is list of detailed error messages, similar to the result of Example 1.</span></span>

```powershell
$Error | Get-Error
```

## <span data-ttu-id="0a9a4-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0a9a4-123">PARAMETERS</span></span>

### <span data-ttu-id="0a9a4-124">-Plus récent</span><span class="sxs-lookup"><span data-stu-id="0a9a4-124">-Newest</span></span>

<span data-ttu-id="0a9a4-125">Spécifie le nombre d’erreurs à afficher qui se sont produites dans la session active.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-125">Specifies the number of errors to display that have occurred in the current session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Newest
Aliases: Last

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0a9a4-126">-InputObject</span><span class="sxs-lookup"><span data-stu-id="0a9a4-126">-InputObject</span></span>

<span data-ttu-id="0a9a4-127">Ce paramètre est utilisé pour l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-127">This parameter is used for pipeline input.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Error
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0a9a4-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0a9a4-128">CommonParameters</span></span>

<span data-ttu-id="0a9a4-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0a9a4-130">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0a9a4-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0a9a4-131">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0a9a4-131">INPUTS</span></span>

### <span data-ttu-id="0a9a4-132">PSObject</span><span class="sxs-lookup"><span data-stu-id="0a9a4-132">PSObject</span></span>

<span data-ttu-id="0a9a4-133">Prend en charge l’entrée de n’importe quel **PSObject**, mais les résultats varient à moins qu’un objet **ErrorRecord** ou **exception** ne soit fourni.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-133">Supports input from any **PSObject**, but results vary unless either an **ErrorRecord** or **Exception** object are supplied.</span></span>

## <span data-ttu-id="0a9a4-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0a9a4-134">OUTPUTS</span></span>

### <span data-ttu-id="0a9a4-135">System. Management. Automation. ErrorRecord # PSExtendedError</span><span class="sxs-lookup"><span data-stu-id="0a9a4-135">System.Management.Automation.ErrorRecord#PSExtendedError</span></span>

<span data-ttu-id="0a9a4-136">Sortie dans un objet **PSExtendedError** .</span><span class="sxs-lookup"><span data-stu-id="0a9a4-136">Output in a **PSExtendedError** object.</span></span>

## <span data-ttu-id="0a9a4-137">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0a9a4-137">NOTES</span></span>

<span data-ttu-id="0a9a4-138">`Get-Error` accepte l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-138">`Get-Error` accepts pipeline input.</span></span> <span data-ttu-id="0a9a4-139">Par exemple, `$Error | Get-Error`.</span><span class="sxs-lookup"><span data-stu-id="0a9a4-139">For example, `$Error | Get-Error`.</span></span>

## <span data-ttu-id="0a9a4-140">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0a9a4-140">RELATED LINKS</span></span>

[<span data-ttu-id="0a9a4-141">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="0a9a4-141">about_Try_Catch_Finally</span></span>](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
