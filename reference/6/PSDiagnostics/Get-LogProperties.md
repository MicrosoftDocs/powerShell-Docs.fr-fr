---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: 63f9f644a81886dab498e46fce90d4ff2f7be91b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204825"
---
# <span data-ttu-id="61992-102">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="61992-102">Get-LogProperties</span></span>

## <span data-ttu-id="61992-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="61992-103">SYNOPSIS</span></span>
<span data-ttu-id="61992-104">Récupère les propriétés d’un journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="61992-104">Retrieves the properties of a Windows event log.</span></span>

## <span data-ttu-id="61992-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="61992-105">SYNTAX</span></span>

```
Get-LogProperties [-Name] <Object> [<CommonParameters>]
```

## <span data-ttu-id="61992-106">Description</span><span class="sxs-lookup"><span data-stu-id="61992-106">DESCRIPTION</span></span>

<span data-ttu-id="61992-107">Cette applet de commande obtient les paramètres de configuration d’un journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="61992-107">This cmdlet gets the configuration settings of a Windows event log.</span></span> <span data-ttu-id="61992-108">Cette applet de commande est utilisée par les `Enable-PSTrace` applets de commande et `Disable-PSTrace` .</span><span class="sxs-lookup"><span data-stu-id="61992-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

## <span data-ttu-id="61992-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="61992-109">EXAMPLES</span></span>

### <span data-ttu-id="61992-110">Exemple 1 : récupérer les paramètres de configuration du journal des événements Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="61992-110">Example 1: Get the configuration settings of the Windows PowerShell event log</span></span>

```powershell
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : False
AutoBackup : False
MaxLogSize : 15728640
```

## <span data-ttu-id="61992-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="61992-111">PARAMETERS</span></span>

### <span data-ttu-id="61992-112">-Name</span><span class="sxs-lookup"><span data-stu-id="61992-112">-Name</span></span>

<span data-ttu-id="61992-113">Nom du fournisseur d’événements.</span><span class="sxs-lookup"><span data-stu-id="61992-113">The name of the event provider.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="61992-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="61992-114">CommonParameters</span></span>

<span data-ttu-id="61992-115">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="61992-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="61992-116">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="61992-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="61992-117">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="61992-117">INPUTS</span></span>

### <span data-ttu-id="61992-118">System.String</span><span class="sxs-lookup"><span data-stu-id="61992-118">System.String</span></span>

## <span data-ttu-id="61992-119">SORTIES</span><span class="sxs-lookup"><span data-stu-id="61992-119">OUTPUTS</span></span>

### <span data-ttu-id="61992-120">Microsoft. PowerShell. Diagnostics. LogDetails</span><span class="sxs-lookup"><span data-stu-id="61992-120">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="61992-121">Le module **PSDiagnostics** ajoute la classe **LogDetails** à l' `Microsoft.PowerShell.Diagnostics` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="61992-121">The **PSDiagnostics** module adds the **LogDetails** class to the `Microsoft.PowerShell.Diagnostics` namespace.</span></span>

## <span data-ttu-id="61992-122">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="61992-122">NOTES</span></span>

## <span data-ttu-id="61992-123">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="61992-123">RELATED LINKS</span></span>

[<span data-ttu-id="61992-124">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="61992-124">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="61992-125">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="61992-125">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="61992-126">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="61992-126">Disable-PSTrace</span></span>](Disable-PSTrace.md)
