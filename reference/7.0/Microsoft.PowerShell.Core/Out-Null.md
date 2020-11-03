---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: 501c0482270a5a4919ed33844beb838e231f8636
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201606"
---
# <span data-ttu-id="4b456-103">Out-Null</span><span class="sxs-lookup"><span data-stu-id="4b456-103">Out-Null</span></span>

## <span data-ttu-id="4b456-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4b456-104">SYNOPSIS</span></span>
<span data-ttu-id="4b456-105">Masque la sortie au lieu de l’envoyer dans le pipeline ou de l’afficher.</span><span class="sxs-lookup"><span data-stu-id="4b456-105">Hides the output instead of sending it down the pipeline or displaying it.</span></span>

## <span data-ttu-id="4b456-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4b456-106">SYNTAX</span></span>

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="4b456-107">Description</span><span class="sxs-lookup"><span data-stu-id="4b456-107">DESCRIPTION</span></span>

<span data-ttu-id="4b456-108">L’applet de commande **out-NULL** envoie sa sortie à null, en effet, en la supprimant du pipeline et en empêchant l’affichage de la sortie à l’écran.</span><span class="sxs-lookup"><span data-stu-id="4b456-108">The **Out-Null** cmdlet sends its output to NULL, in effect, removing it from the pipeline and preventing the output to be displayed at the screen.</span></span>

## <span data-ttu-id="4b456-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4b456-109">EXAMPLES</span></span>

### <span data-ttu-id="4b456-110">Exemple 1 : supprimer la sortie</span><span class="sxs-lookup"><span data-stu-id="4b456-110">Example 1: Delete output</span></span>

```powershell
Get-ChildItem | Out-Null
```

<span data-ttu-id="4b456-111">Cette commande obtient les éléments de l’emplacement/répertoire actuel, mais sa sortie n’est pas transmise via le pipeline ni affichée sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="4b456-111">This command gets items in the current location/directory, but its output is not passed through the pipeline nor displayed at the command line.</span></span>
<span data-ttu-id="4b456-112">Cela est utile pour masquer la sortie dont vous n’avez pas besoin.</span><span class="sxs-lookup"><span data-stu-id="4b456-112">This is useful for hiding output that you do not need.</span></span>

## <span data-ttu-id="4b456-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4b456-113">PARAMETERS</span></span>

### <span data-ttu-id="4b456-114">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4b456-114">-InputObject</span></span>

<span data-ttu-id="4b456-115">Spécifie l’objet à envoyer à NULL (supprimé du pipeline).</span><span class="sxs-lookup"><span data-stu-id="4b456-115">Specifies the object to be sent to NULL (removed from pipeline).</span></span>
<span data-ttu-id="4b456-116">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="4b456-116">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4b456-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4b456-117">CommonParameters</span></span>

<span data-ttu-id="4b456-118">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4b456-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4b456-119">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4b456-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4b456-120">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4b456-120">INPUTS</span></span>

### <span data-ttu-id="4b456-121">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="4b456-121">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="4b456-122">Vous pouvez diriger n’importe quel objet vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4b456-122">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="4b456-123">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4b456-123">OUTPUTS</span></span>

### <span data-ttu-id="4b456-124">Aucun</span><span class="sxs-lookup"><span data-stu-id="4b456-124">None</span></span>

<span data-ttu-id="4b456-125">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="4b456-125">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4b456-126">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4b456-126">NOTES</span></span>

* <span data-ttu-id="4b456-127">Les applets de commande qui contiennent le verbe **out** (applets de commande **out** ) n’ont pas de paramètres pour les noms ou les chemins d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="4b456-127">The cmdlets that contain the **Out** verb (the **Out** cmdlets) do not have parameters for names or file paths.</span></span> <span data-ttu-id="4b456-128">Pour envoyer des données à une applet de commande **out** , utilisez un opérateur de pipeline (|) pour envoyer la sortie d’une commande PowerShell à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4b456-128">To send data to an **Out** cmdlet, use a pipeline operator (|) to send the output of a PowerShell command to the cmdlet.</span></span> <span data-ttu-id="4b456-129">Vous pouvez également stocker les données dans une variable et utiliser le paramètre *InputObject* pour passer les données à l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4b456-129">You can also store data in a variable and use the *InputObject* parameter to pass the data to the cmdlet.</span></span> <span data-ttu-id="4b456-130">Pour plus d'informations, consultez les exemples.</span><span class="sxs-lookup"><span data-stu-id="4b456-130">For more information, see the examples.</span></span>
* <span data-ttu-id="4b456-131">**Out-NULL** ne retourne aucun objet de sortie.</span><span class="sxs-lookup"><span data-stu-id="4b456-131">**Out-Null** does not return any output objects.</span></span> <span data-ttu-id="4b456-132">Si vous dirigez la sortie de **out-NULL** vers l’applet de commande Get-Member, la commande **obtenir-Member** signale qu’aucun objet n’a été spécifié.</span><span class="sxs-lookup"><span data-stu-id="4b456-132">If you pipe the output of **Out-Null** to the Get-Member cmdlet, **Get-Member** reports that no objects have been specified.</span></span>

## <span data-ttu-id="4b456-133">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4b456-133">RELATED LINKS</span></span>

[<span data-ttu-id="4b456-134">Out-Default</span><span class="sxs-lookup"><span data-stu-id="4b456-134">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="4b456-135">Out-Host</span><span class="sxs-lookup"><span data-stu-id="4b456-135">Out-Host</span></span>](Out-Host.md)
