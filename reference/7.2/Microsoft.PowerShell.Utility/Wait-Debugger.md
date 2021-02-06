---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-debugger?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Debugger
ms.openlocfilehash: a2ef114a43a63b18f5dc2d28acf7cbc0de8392bd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603663"
---
# <span data-ttu-id="cee30-102">Wait-Debugger</span><span class="sxs-lookup"><span data-stu-id="cee30-102">Wait-Debugger</span></span>

## <span data-ttu-id="cee30-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="cee30-103">SYNOPSIS</span></span>
<span data-ttu-id="cee30-104">Arrête un script dans le débogueur avant d’exécuter l’instruction suivante dans le script.</span><span class="sxs-lookup"><span data-stu-id="cee30-104">Stops a script in the debugger before running the next statement in the script.</span></span>

## <span data-ttu-id="cee30-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="cee30-105">SYNTAX</span></span>

```
Wait-Debugger [<CommonParameters>]
```

## <span data-ttu-id="cee30-106">Description</span><span class="sxs-lookup"><span data-stu-id="cee30-106">DESCRIPTION</span></span>

<span data-ttu-id="cee30-107">Arrête le moteur d’exécution de script PowerShell à l’emplacement immédiatement après l' `Wait-Debugger` applet de commande et attend qu’un débogueur soit attaché.</span><span class="sxs-lookup"><span data-stu-id="cee30-107">Stops the PowerShell script execution engine at the point immediately after the `Wait-Debugger` cmdlet and waits for a debugger to be attached.</span></span> <span data-ttu-id="cee30-108">Cela est similaire à l’utilisation `Enable-RunspaceDebug -BreakAll` de dans une ressource DSC, mais s’arrête à un point spécifique du script.</span><span class="sxs-lookup"><span data-stu-id="cee30-108">This is similar to using `Enable-RunspaceDebug -BreakAll` in a DSC resource but breaks at a specific point in the script.</span></span>

> [!CAUTION]
> <span data-ttu-id="cee30-109">Veillez à supprimer les `Wait-Debugger` lignes une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="cee30-109">Make sure you remove the `Wait-Debugger` lines after you are done.</span></span> <span data-ttu-id="cee30-110">Un script en cours d’exécution semble être suspendu lorsqu’il est arrêté à un `Wait-Debugger` .</span><span class="sxs-lookup"><span data-stu-id="cee30-110">A running script appears to be hung when it is stopped at a `Wait-Debugger`.</span></span>

## <span data-ttu-id="cee30-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="cee30-111">EXAMPLES</span></span>

### <span data-ttu-id="cee30-112">Exemple 1 : insérer un point d’arrêt pour le débogage</span><span class="sxs-lookup"><span data-stu-id="cee30-112">Example 1: Insert breakpoint for debugging</span></span>

```
[DscResource()]
class FileResource
{
    [DscProperty(Key)]
    [string] $Path

    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    [DscProperty(Mandatory)]
    [string] $SourcePath

    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime


    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (! $fileExists)
            {
               $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    [bool] Test()
    {
        $present = Test-Path -LiteralPath $this.Path

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return (! $present)
        }
    }

    [FileResource] Get()
    {
        $present = Test-Path -Path $this.Path

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    [void] CopyFile()
    {
        # Testing only - Remove before deployment!
        Wait-Debugger

        if (! (Test-Path -LiteralPath $this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose "Copying $($this.SourcePath) to $($this.Path)"

        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <span data-ttu-id="cee30-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cee30-113">PARAMETERS</span></span>

### <span data-ttu-id="cee30-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cee30-114">CommonParameters</span></span>

<span data-ttu-id="cee30-115">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cee30-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cee30-116">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="cee30-116">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="cee30-117">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="cee30-117">INPUTS</span></span>

### <span data-ttu-id="cee30-118">None</span><span class="sxs-lookup"><span data-stu-id="cee30-118">None</span></span>

## <span data-ttu-id="cee30-119">SORTIES</span><span class="sxs-lookup"><span data-stu-id="cee30-119">OUTPUTS</span></span>

### <span data-ttu-id="cee30-120">None</span><span class="sxs-lookup"><span data-stu-id="cee30-120">None</span></span>

## <span data-ttu-id="cee30-121">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="cee30-121">NOTES</span></span>

## <span data-ttu-id="cee30-122">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="cee30-122">RELATED LINKS</span></span>

[<span data-ttu-id="cee30-123">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="cee30-123">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)

