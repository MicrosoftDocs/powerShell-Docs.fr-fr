---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Service
ms.openlocfilehash: 13ef4d483ad91b38c175f850da9cd4d1da771935
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201162"
---
# <span data-ttu-id="7c36c-103">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="7c36c-103">Remove-Service</span></span>

## <span data-ttu-id="7c36c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7c36c-104">SYNOPSIS</span></span>
<span data-ttu-id="7c36c-105">Supprime un service Windows.</span><span class="sxs-lookup"><span data-stu-id="7c36c-105">Removes a Windows service.</span></span>

## <span data-ttu-id="7c36c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7c36c-106">SYNTAX</span></span>

### <span data-ttu-id="7c36c-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="7c36c-107">Name (Default)</span></span>

```
Remove-Service [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7c36c-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="7c36c-108">InputObject</span></span>

```
Remove-Service [-InputObject <ServiceController>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7c36c-109">Description</span><span class="sxs-lookup"><span data-stu-id="7c36c-109">DESCRIPTION</span></span>

<span data-ttu-id="7c36c-110">L' `Remove-Service` applet de commande supprime un service Windows dans le registre et dans la base de données du service.</span><span class="sxs-lookup"><span data-stu-id="7c36c-110">The `Remove-Service` cmdlet removes a Windows service in the registry and in the service database.</span></span>

<span data-ttu-id="7c36c-111">L' `Remove-Service` applet de commande a été introduite dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="7c36c-111">The `Remove-Service` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="7c36c-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7c36c-112">EXAMPLES</span></span>

### <span data-ttu-id="7c36c-113">Exemple 1 : supprimer un service</span><span class="sxs-lookup"><span data-stu-id="7c36c-113">Example 1: Remove a service</span></span>

<span data-ttu-id="7c36c-114">Cela supprime un service nommé TestService.</span><span class="sxs-lookup"><span data-stu-id="7c36c-114">This removes a service named TestService.</span></span>

```powershell
Remove-Service -Name "TestService"
```

### <span data-ttu-id="7c36c-115">Exemple 2 : supprimer un service à l’aide du nom complet</span><span class="sxs-lookup"><span data-stu-id="7c36c-115">Example 2: Remove a service using the display name</span></span>

<span data-ttu-id="7c36c-116">Cet exemple supprime un service nommé TestService.</span><span class="sxs-lookup"><span data-stu-id="7c36c-116">This example removes a service named TestService.</span></span> <span data-ttu-id="7c36c-117">La commande utilise `Get-Service` pour obtenir un objet qui représente le service TestService à l’aide du nom complet.</span><span class="sxs-lookup"><span data-stu-id="7c36c-117">The command uses `Get-Service` to get an object that represents the TestService service using the display name.</span></span> <span data-ttu-id="7c36c-118">L’opérateur de pipeline ( `|` ) dirige l’objet vers `Remove-Service` , qui supprime le service.</span><span class="sxs-lookup"><span data-stu-id="7c36c-118">The pipeline operator (`|`) pipes the object to `Remove-Service`, which removes the service.</span></span>

```powershell
Get-Service -DisplayName "Test Service" | Remove-Service
```

## <span data-ttu-id="7c36c-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7c36c-119">PARAMETERS</span></span>

### <span data-ttu-id="7c36c-120">-InputObject</span><span class="sxs-lookup"><span data-stu-id="7c36c-120">-InputObject</span></span>

<span data-ttu-id="7c36c-121">Spécifie les objets **ServiceController** qui représentent les services à supprimer.</span><span class="sxs-lookup"><span data-stu-id="7c36c-121">Specifies **ServiceController** objects that represent the services to remove.</span></span> <span data-ttu-id="7c36c-122">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="7c36c-122">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="7c36c-123">-Name</span><span class="sxs-lookup"><span data-stu-id="7c36c-123">-Name</span></span>

<span data-ttu-id="7c36c-124">Spécifie les noms des services à supprimer.</span><span class="sxs-lookup"><span data-stu-id="7c36c-124">Specifies the service names of the services to remove.</span></span> <span data-ttu-id="7c36c-125">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="7c36c-125">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="7c36c-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7c36c-126">-Confirm</span></span>

<span data-ttu-id="7c36c-127">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7c36c-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7c36c-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7c36c-128">-WhatIf</span></span>

<span data-ttu-id="7c36c-129">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7c36c-129">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="7c36c-130">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="7c36c-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7c36c-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7c36c-131">CommonParameters</span></span>

<span data-ttu-id="7c36c-132">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7c36c-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7c36c-133">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7c36c-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7c36c-134">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7c36c-134">INPUTS</span></span>

### <span data-ttu-id="7c36c-135">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="7c36c-135">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="7c36c-136">Vous pouvez diriger un objet de service ou une chaîne qui contient le nom d’un service vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7c36c-136">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="7c36c-137">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7c36c-137">OUTPUTS</span></span>

### <span data-ttu-id="7c36c-138">Aucun</span><span class="sxs-lookup"><span data-stu-id="7c36c-138">None</span></span>

<span data-ttu-id="7c36c-139">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="7c36c-139">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="7c36c-140">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7c36c-140">NOTES</span></span>

<span data-ttu-id="7c36c-141">Pour exécuter cette applet de commande, démarrez PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="7c36c-141">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="7c36c-142">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7c36c-142">RELATED LINKS</span></span>

[<span data-ttu-id="7c36c-143">Get-Service</span><span class="sxs-lookup"><span data-stu-id="7c36c-143">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="7c36c-144">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="7c36c-144">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="7c36c-145">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="7c36c-145">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="7c36c-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="7c36c-146">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="7c36c-147">Start-Service</span><span class="sxs-lookup"><span data-stu-id="7c36c-147">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="7c36c-148">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="7c36c-148">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="7c36c-149">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="7c36c-149">Suspend-Service</span></span>](Suspend-Service.md)
