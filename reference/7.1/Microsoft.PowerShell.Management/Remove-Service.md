---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Service
ms.openlocfilehash: b23e263c2d6ff64ca2a799614d213f1e549cdfe3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202058"
---
# <span data-ttu-id="f3ac1-103">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="f3ac1-103">Remove-Service</span></span>

## <span data-ttu-id="f3ac1-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f3ac1-104">SYNOPSIS</span></span>
<span data-ttu-id="f3ac1-105">Supprime un service Windows.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-105">Removes a Windows service.</span></span>

## <span data-ttu-id="f3ac1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f3ac1-106">SYNTAX</span></span>

### <span data-ttu-id="f3ac1-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f3ac1-107">Name (Default)</span></span>

```
Remove-Service [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f3ac1-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="f3ac1-108">InputObject</span></span>

```
Remove-Service [-InputObject <ServiceController>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f3ac1-109">Description</span><span class="sxs-lookup"><span data-stu-id="f3ac1-109">DESCRIPTION</span></span>

<span data-ttu-id="f3ac1-110">L' `Remove-Service` applet de commande supprime un service Windows dans le registre et dans la base de données du service.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-110">The `Remove-Service` cmdlet removes a Windows service in the registry and in the service database.</span></span>

<span data-ttu-id="f3ac1-111">L' `Remove-Service` applet de commande a été introduite dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-111">The `Remove-Service` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="f3ac1-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f3ac1-112">EXAMPLES</span></span>

### <span data-ttu-id="f3ac1-113">Exemple 1 : supprimer un service</span><span class="sxs-lookup"><span data-stu-id="f3ac1-113">Example 1: Remove a service</span></span>

<span data-ttu-id="f3ac1-114">Cela supprime un service nommé TestService.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-114">This removes a service named TestService.</span></span>

```powershell
Remove-Service -Name "TestService"
```

### <span data-ttu-id="f3ac1-115">Exemple 2 : supprimer un service à l’aide du nom complet</span><span class="sxs-lookup"><span data-stu-id="f3ac1-115">Example 2: Remove a service using the display name</span></span>

<span data-ttu-id="f3ac1-116">Cet exemple supprime un service nommé TestService.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-116">This example removes a service named TestService.</span></span> <span data-ttu-id="f3ac1-117">La commande utilise `Get-Service` pour obtenir un objet qui représente le service TestService à l’aide du nom complet.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-117">The command uses `Get-Service` to get an object that represents the TestService service using the display name.</span></span> <span data-ttu-id="f3ac1-118">L’opérateur de pipeline ( `|` ) dirige l’objet vers `Remove-Service` , qui supprime le service.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-118">The pipeline operator (`|`) pipes the object to `Remove-Service`, which removes the service.</span></span>

```powershell
Get-Service -DisplayName "Test Service" | Remove-Service
```

## <span data-ttu-id="f3ac1-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f3ac1-119">PARAMETERS</span></span>

### <span data-ttu-id="f3ac1-120">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f3ac1-120">-InputObject</span></span>

<span data-ttu-id="f3ac1-121">Spécifie les objets **ServiceController** qui représentent les services à supprimer.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-121">Specifies **ServiceController** objects that represent the services to remove.</span></span> <span data-ttu-id="f3ac1-122">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-122">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f3ac1-123">-Name</span><span class="sxs-lookup"><span data-stu-id="f3ac1-123">-Name</span></span>

<span data-ttu-id="f3ac1-124">Spécifie les noms des services à supprimer.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-124">Specifies the service names of the services to remove.</span></span> <span data-ttu-id="f3ac1-125">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-125">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="f3ac1-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f3ac1-126">-Confirm</span></span>

<span data-ttu-id="f3ac1-127">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-127">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3ac1-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f3ac1-128">-WhatIf</span></span>

<span data-ttu-id="f3ac1-129">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-129">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f3ac1-130">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-130">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3ac1-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f3ac1-131">CommonParameters</span></span>

<span data-ttu-id="f3ac1-132">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f3ac1-133">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f3ac1-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f3ac1-134">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f3ac1-134">INPUTS</span></span>

### <span data-ttu-id="f3ac1-135">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="f3ac1-135">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="f3ac1-136">Vous pouvez diriger un objet de service ou une chaîne qui contient le nom d’un service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-136">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="f3ac1-137">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f3ac1-137">OUTPUTS</span></span>

### <span data-ttu-id="f3ac1-138">Aucun</span><span class="sxs-lookup"><span data-stu-id="f3ac1-138">None</span></span>

<span data-ttu-id="f3ac1-139">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="f3ac1-139">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="f3ac1-140">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f3ac1-140">NOTES</span></span>

<span data-ttu-id="f3ac1-141">Pour exécuter cette applet de commande, démarrez PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="f3ac1-141">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="f3ac1-142">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f3ac1-142">RELATED LINKS</span></span>

[<span data-ttu-id="f3ac1-143">Get-Service</span><span class="sxs-lookup"><span data-stu-id="f3ac1-143">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="f3ac1-144">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="f3ac1-144">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="f3ac1-145">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="f3ac1-145">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="f3ac1-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="f3ac1-146">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="f3ac1-147">Start-Service</span><span class="sxs-lookup"><span data-stu-id="f3ac1-147">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="f3ac1-148">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="f3ac1-148">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="f3ac1-149">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="f3ac1-149">Suspend-Service</span></span>](Suspend-Service.md)

