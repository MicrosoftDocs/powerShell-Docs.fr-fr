---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/set-logproperties?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LogProperties
ms.openlocfilehash: d6ad6f8cc299351cc85d4ed7e7b9682a1d90307b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204826"
---
# <span data-ttu-id="de659-102">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="de659-102">Set-LogProperties</span></span>

## <span data-ttu-id="de659-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="de659-103">SYNOPSIS</span></span>
<span data-ttu-id="de659-104">Modifie les propriétés d’un journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="de659-104">Changes the properties of a Windows event log.</span></span>

## <span data-ttu-id="de659-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="de659-105">SYNTAX</span></span>

```
Set-LogProperties [-LogDetails] <LogDetails> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="de659-106">Description</span><span class="sxs-lookup"><span data-stu-id="de659-106">DESCRIPTION</span></span>

<span data-ttu-id="de659-107">Cette applet de commande modifie les paramètres de configuration d’un journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="de659-107">This cmdlet changes the configuration settings of a Windows event log.</span></span> <span data-ttu-id="de659-108">Cette applet de commande est utilisée par les `Enable-PSTrace` applets de commande et `Disable-PSTrace` .</span><span class="sxs-lookup"><span data-stu-id="de659-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

<span data-ttu-id="de659-109">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="de659-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="de659-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="de659-110">EXAMPLES</span></span>

### <span data-ttu-id="de659-111">Exemple 1 : modifier le paramètre de rétention du journal des événements Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="de659-111">Example 1: Change the retention setting of the Windows PowerShell event log</span></span>

```powershell
$logDetails = Get-LogProperties 'Windows PowerShell'
$logDetails.Retention = $True
Set-LogProperties -LogDetails $logDetails
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : True
AutoBackup : False
MaxLogSize : 15728640
```

## <span data-ttu-id="de659-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="de659-112">PARAMETERS</span></span>

### <span data-ttu-id="de659-113">-Force</span><span class="sxs-lookup"><span data-stu-id="de659-113">-Force</span></span>

<span data-ttu-id="de659-114">Utilisé pour forcer la modification sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="de659-114">Used to force the change without prompting.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="de659-115">-LogDetails</span><span class="sxs-lookup"><span data-stu-id="de659-115">-LogDetails</span></span>

<span data-ttu-id="de659-116">Paramètres de configuration mis à jour à assigner au journal des événements.</span><span class="sxs-lookup"><span data-stu-id="de659-116">The updated configuration settings to be assigned to the event log.</span></span>

```yaml
Type: Microsoft.PowerShell.Diagnostics.LogDetails
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="de659-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="de659-117">CommonParameters</span></span>

<span data-ttu-id="de659-118">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="de659-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="de659-119">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="de659-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="de659-120">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="de659-120">INPUTS</span></span>

### <span data-ttu-id="de659-121">Microsoft. PowerShell. Diagnostics. LogDetails</span><span class="sxs-lookup"><span data-stu-id="de659-121">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="de659-122">Vous devez transmettre un objet **LogDetails** entièrement configuré à l' `Set-LogProperties` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="de659-122">You must pass a fully configured **LogDetails** object to the `Set-LogProperties` cmdlet.</span></span>
<span data-ttu-id="de659-123">Par conséquent, pour modifier un paramètre, vous devez utiliser `Get-LogProperties` pour récupérer la configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="de659-123">Therefore, to change one setting, you should use `Get-LogProperties` to retrieve the current configuration.</span></span>

## <span data-ttu-id="de659-124">SORTIES</span><span class="sxs-lookup"><span data-stu-id="de659-124">OUTPUTS</span></span>

### <span data-ttu-id="de659-125">Aucun</span><span class="sxs-lookup"><span data-stu-id="de659-125">None</span></span>

## <span data-ttu-id="de659-126">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="de659-126">NOTES</span></span>

<span data-ttu-id="de659-127">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="de659-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="de659-128">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="de659-128">RELATED LINKS</span></span>

[<span data-ttu-id="de659-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="de659-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="de659-130">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="de659-130">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="de659-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="de659-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)
