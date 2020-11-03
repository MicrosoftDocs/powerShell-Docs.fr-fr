---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: eae279aa9c5d3a99a9a522254c5b792970f74297
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205186"
---
# <span data-ttu-id="edd27-103">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="edd27-103">Remove-CimSession</span></span>

## <span data-ttu-id="edd27-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="edd27-104">SYNOPSIS</span></span>
<span data-ttu-id="edd27-105">Supprime une ou plusieurs sessions CIM.</span><span class="sxs-lookup"><span data-stu-id="edd27-105">Removes one or more CIM sessions.</span></span>

## <span data-ttu-id="edd27-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="edd27-106">SYNTAX</span></span>

### <span data-ttu-id="edd27-107">CimSessionSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="edd27-107">CimSessionSet (Default)</span></span>

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="edd27-108">ComputerNameSet</span><span class="sxs-lookup"><span data-stu-id="edd27-108">ComputerNameSet</span></span>

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="edd27-109">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="edd27-109">SessionIdSet</span></span>

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="edd27-110">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="edd27-110">InstanceIdSet</span></span>

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="edd27-111">NameSet</span><span class="sxs-lookup"><span data-stu-id="edd27-111">NameSet</span></span>

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="edd27-112">Description</span><span class="sxs-lookup"><span data-stu-id="edd27-112">DESCRIPTION</span></span>

<span data-ttu-id="edd27-113">L' `Remove-CimSession` applet de commande supprime un ou plusieurs objets de session CIM de la session PowerShell locale.</span><span class="sxs-lookup"><span data-stu-id="edd27-113">The `Remove-CimSession` cmdlet removes one or more CIM session objects from the local PowerShell session.</span></span>

## <span data-ttu-id="edd27-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="edd27-114">EXAMPLES</span></span>

### <span data-ttu-id="edd27-115">Exemple 1 : supprimer toutes les sessions CIM</span><span class="sxs-lookup"><span data-stu-id="edd27-115">Example 1: Remove all the CIM sessions</span></span>

<span data-ttu-id="edd27-116">Cet exemple récupère toutes les sessions CIM disponibles sur l’ordinateur local à l’aide de l’applet de commande [CimSession](Get-CimSession.md) , puis les supprime à l’aide de l’applet de commande `Remove-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="edd27-116">This example retrieves all the available CIM sessions on the local computer using the [Get-CimSession](Get-CimSession.md) cmdlet, and then removes them using the `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

### <span data-ttu-id="edd27-117">Exemple 2 : supprimer une session CIM spécifique</span><span class="sxs-lookup"><span data-stu-id="edd27-117">Example 2: Remove a specific CIM session</span></span>

<span data-ttu-id="edd27-118">Cet exemple supprime la session CIM qui a une valeur d' **ID** de 5.</span><span class="sxs-lookup"><span data-stu-id="edd27-118">This example removes the CIM session that has an **Id** value of 5.</span></span>

```powershell
Remove-CimSession -Id 5
```

### <span data-ttu-id="edd27-119">Exemple 3 : afficher la liste des sessions CIM à supprimer à l’aide du paramètre WhatIf</span><span class="sxs-lookup"><span data-stu-id="edd27-119">Example 3: Show the list of CIM sessions to remove by using the WhatIf parameter</span></span>

<span data-ttu-id="edd27-120">Cet exemple utilise le paramètre commun **WhatIf** pour spécifier que la suppression ne doit pas être effectuée, mais uniquement en cas de résultat.</span><span class="sxs-lookup"><span data-stu-id="edd27-120">This example uses the common parameter **WhatIf** to specify that the removal should not be done, but only output what would happen if it were done.</span></span>

```powershell
Remove-CimSession -Name a* -WhatIf
```

## <span data-ttu-id="edd27-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="edd27-121">PARAMETERS</span></span>

### <span data-ttu-id="edd27-122">-CimSession</span><span class="sxs-lookup"><span data-stu-id="edd27-122">-CimSession</span></span>

<span data-ttu-id="edd27-123">Spécifie les objets de session des sessions CIM à fermer.</span><span class="sxs-lookup"><span data-stu-id="edd27-123">Specifies the session objects of the CIM sessions to close.</span></span>

<span data-ttu-id="edd27-124">Entrez une variable qui contient la session CIM ou une commande qui crée ou obtient la session CIM, telle que les [`New-CimSession`](New-CimSession.md) applets de commande ou [`Get-CimSession`](Get-CimSession.md) .</span><span class="sxs-lookup"><span data-stu-id="edd27-124">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the [`New-CimSession`](New-CimSession.md) or [`Get-CimSession`](Get-CimSession.md) cmdlets.</span></span>
<span data-ttu-id="edd27-125">Pour plus d’informations, consultez [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="edd27-125">For more information, see [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="edd27-126">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="edd27-126">-ComputerName</span></span>

<span data-ttu-id="edd27-127">Spécifie un tableau de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="edd27-127">Specifies an array of names of computers.</span></span> <span data-ttu-id="edd27-128">Supprime les sessions qui se connectent aux ordinateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="edd27-128">Removes the sessions that connect to the specified computers.</span></span> <span data-ttu-id="edd27-129">Vous pouvez spécifier un nom de domaine complet (FQDN) ou un nom NetBIOS.</span><span class="sxs-lookup"><span data-stu-id="edd27-129">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="edd27-130">-Id</span><span class="sxs-lookup"><span data-stu-id="edd27-130">-Id</span></span>

<span data-ttu-id="edd27-131">Spécifie l’ID de la session CIM à supprimer.</span><span class="sxs-lookup"><span data-stu-id="edd27-131">Specifies the ID of the CIM session to remove.</span></span> <span data-ttu-id="edd27-132">Spécifiez un ou plusieurs ID séparés par des virgules, ou utilisez l’opérateur de plage ( `..` ) pour spécifier une plage d’ID.</span><span class="sxs-lookup"><span data-stu-id="edd27-132">Specify one or more IDs separated by commas, or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="edd27-133">Un **ID** est un entier qui identifie de façon unique la session CIM dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="edd27-133">An **Id** is an integer that uniquely identifies the CIM session in the current PowerShell session.</span></span>

<span data-ttu-id="edd27-134">Pour plus d’informations sur l’opérateur de plage, consultez [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="edd27-134">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="edd27-135">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="edd27-135">-InstanceId</span></span>

<span data-ttu-id="edd27-136">Spécifie l’ID d’instance de la session CIM à supprimer.</span><span class="sxs-lookup"><span data-stu-id="edd27-136">Specifies the instance ID of the CIM session to remove.</span></span> <span data-ttu-id="edd27-137">**InstanceID** est un identificateur global unique (Guid) qui identifie de façon unique une session CIM.</span><span class="sxs-lookup"><span data-stu-id="edd27-137">**InstanceId** is a Globally Unique Identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="edd27-138">L' **InstanceID** est unique, même si plusieurs sessions sont en cours d’exécution dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="edd27-138">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="edd27-139">L' **InstanceID** est stocké dans la propriété **InstanceID** de l’objet qui représente une session CIM.</span><span class="sxs-lookup"><span data-stu-id="edd27-139">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="edd27-140">-Name</span><span class="sxs-lookup"><span data-stu-id="edd27-140">-Name</span></span>

<span data-ttu-id="edd27-141">Spécifie le nom convivial de la session CIM à supprimer.</span><span class="sxs-lookup"><span data-stu-id="edd27-141">Specifies the friendly name of the CIM session to remove.</span></span> <span data-ttu-id="edd27-142">Vous pouvez utiliser des caractères génériques avec ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="edd27-142">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="edd27-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="edd27-143">-Confirm</span></span>

<span data-ttu-id="edd27-144">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="edd27-144">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="edd27-145">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="edd27-145">-WhatIf</span></span>

<span data-ttu-id="edd27-146">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="edd27-146">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="edd27-147">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="edd27-147">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="edd27-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="edd27-148">CommonParameters</span></span>

<span data-ttu-id="edd27-149">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="edd27-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="edd27-150">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="edd27-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="edd27-151">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="edd27-151">INPUTS</span></span>

### <span data-ttu-id="edd27-152">Aucun</span><span class="sxs-lookup"><span data-stu-id="edd27-152">None</span></span>

<span data-ttu-id="edd27-153">Cette applet de commande n’accepte aucun objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="edd27-153">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="edd27-154">SORTIES</span><span class="sxs-lookup"><span data-stu-id="edd27-154">OUTPUTS</span></span>

### <span data-ttu-id="edd27-155">System.Object</span><span class="sxs-lookup"><span data-stu-id="edd27-155">System.Object</span></span>

<span data-ttu-id="edd27-156">Cette applet de commande retourne un objet qui contient des informations de session CIM.</span><span class="sxs-lookup"><span data-stu-id="edd27-156">This cmdlet returns an object that contains CIM session information.</span></span>

## <span data-ttu-id="edd27-157">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="edd27-157">NOTES</span></span>

## <span data-ttu-id="edd27-158">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="edd27-158">RELATED LINKS</span></span>

[<span data-ttu-id="edd27-159">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="edd27-159">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="edd27-160">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="edd27-160">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="edd27-161">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="edd27-161">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)

