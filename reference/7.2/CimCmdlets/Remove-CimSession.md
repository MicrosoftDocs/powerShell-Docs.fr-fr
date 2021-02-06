---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: a3ff2132c531df1ab19bf7149a55ea0df4a787a8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597321"
---
# <span data-ttu-id="d99fd-102">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="d99fd-102">Remove-CimSession</span></span>

## <span data-ttu-id="d99fd-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d99fd-103">SYNOPSIS</span></span>
<span data-ttu-id="d99fd-104">Supprime une ou plusieurs sessions CIM.</span><span class="sxs-lookup"><span data-stu-id="d99fd-104">Removes one or more CIM sessions.</span></span>

## <span data-ttu-id="d99fd-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d99fd-105">SYNTAX</span></span>

### <span data-ttu-id="d99fd-106">CimSessionSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d99fd-106">CimSessionSet (Default)</span></span>

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d99fd-107">ComputerNameSet</span><span class="sxs-lookup"><span data-stu-id="d99fd-107">ComputerNameSet</span></span>

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d99fd-108">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="d99fd-108">SessionIdSet</span></span>

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d99fd-109">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="d99fd-109">InstanceIdSet</span></span>

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d99fd-110">NameSet</span><span class="sxs-lookup"><span data-stu-id="d99fd-110">NameSet</span></span>

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d99fd-111">Description</span><span class="sxs-lookup"><span data-stu-id="d99fd-111">DESCRIPTION</span></span>

<span data-ttu-id="d99fd-112">L' `Remove-CimSession` applet de commande supprime un ou plusieurs objets de session CIM de la session PowerShell locale.</span><span class="sxs-lookup"><span data-stu-id="d99fd-112">The `Remove-CimSession` cmdlet removes one or more CIM session objects from the local PowerShell session.</span></span>

## <span data-ttu-id="d99fd-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d99fd-113">EXAMPLES</span></span>

### <span data-ttu-id="d99fd-114">Exemple 1 : supprimer toutes les sessions CIM</span><span class="sxs-lookup"><span data-stu-id="d99fd-114">Example 1: Remove all the CIM sessions</span></span>

<span data-ttu-id="d99fd-115">Cet exemple récupère toutes les sessions CIM disponibles sur l’ordinateur local à l’aide de l’applet de commande [CimSession](Get-CimSession.md) , puis les supprime à l’aide de l’applet de commande `Remove-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="d99fd-115">This example retrieves all the available CIM sessions on the local computer using the [Get-CimSession](Get-CimSession.md) cmdlet, and then removes them using the `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

### <span data-ttu-id="d99fd-116">Exemple 2 : supprimer une session CIM spécifique</span><span class="sxs-lookup"><span data-stu-id="d99fd-116">Example 2: Remove a specific CIM session</span></span>

<span data-ttu-id="d99fd-117">Cet exemple supprime la session CIM qui a une valeur d' **ID** de 5.</span><span class="sxs-lookup"><span data-stu-id="d99fd-117">This example removes the CIM session that has an **Id** value of 5.</span></span>

```powershell
Remove-CimSession -Id 5
```

### <span data-ttu-id="d99fd-118">Exemple 3 : afficher la liste des sessions CIM à supprimer à l’aide du paramètre WhatIf</span><span class="sxs-lookup"><span data-stu-id="d99fd-118">Example 3: Show the list of CIM sessions to remove by using the WhatIf parameter</span></span>

<span data-ttu-id="d99fd-119">Cet exemple utilise le paramètre commun **WhatIf** pour spécifier que la suppression ne doit pas être effectuée, mais uniquement en cas de résultat.</span><span class="sxs-lookup"><span data-stu-id="d99fd-119">This example uses the common parameter **WhatIf** to specify that the removal should not be done, but only output what would happen if it were done.</span></span>

```powershell
Remove-CimSession -Name a* -WhatIf
```

## <span data-ttu-id="d99fd-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d99fd-120">PARAMETERS</span></span>

### <span data-ttu-id="d99fd-121">-CimSession</span><span class="sxs-lookup"><span data-stu-id="d99fd-121">-CimSession</span></span>

<span data-ttu-id="d99fd-122">Spécifie les objets de session des sessions CIM à fermer.</span><span class="sxs-lookup"><span data-stu-id="d99fd-122">Specifies the session objects of the CIM sessions to close.</span></span>

<span data-ttu-id="d99fd-123">Entrez une variable qui contient la session CIM ou une commande qui crée ou obtient la session CIM, telle que les [`New-CimSession`](New-CimSession.md) applets de commande ou [`Get-CimSession`](Get-CimSession.md) .</span><span class="sxs-lookup"><span data-stu-id="d99fd-123">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the [`New-CimSession`](New-CimSession.md) or [`Get-CimSession`](Get-CimSession.md) cmdlets.</span></span>
<span data-ttu-id="d99fd-124">Pour plus d’informations, consultez [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="d99fd-124">For more information, see [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

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

### <span data-ttu-id="d99fd-125">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="d99fd-125">-ComputerName</span></span>

<span data-ttu-id="d99fd-126">Spécifie un tableau de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="d99fd-126">Specifies an array of names of computers.</span></span> <span data-ttu-id="d99fd-127">Supprime les sessions qui se connectent aux ordinateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d99fd-127">Removes the sessions that connect to the specified computers.</span></span> <span data-ttu-id="d99fd-128">Vous pouvez spécifier un nom de domaine complet (FQDN) ou un nom NetBIOS.</span><span class="sxs-lookup"><span data-stu-id="d99fd-128">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

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

### <span data-ttu-id="d99fd-129">-Id</span><span class="sxs-lookup"><span data-stu-id="d99fd-129">-Id</span></span>

<span data-ttu-id="d99fd-130">Spécifie l’ID de la session CIM à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d99fd-130">Specifies the ID of the CIM session to remove.</span></span> <span data-ttu-id="d99fd-131">Spécifiez un ou plusieurs ID séparés par des virgules, ou utilisez l’opérateur de plage ( `..` ) pour spécifier une plage d’ID.</span><span class="sxs-lookup"><span data-stu-id="d99fd-131">Specify one or more IDs separated by commas, or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="d99fd-132">Un **ID** est un entier qui identifie de façon unique la session CIM dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="d99fd-132">An **Id** is an integer that uniquely identifies the CIM session in the current PowerShell session.</span></span>

<span data-ttu-id="d99fd-133">Pour plus d’informations sur l’opérateur de plage, consultez [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="d99fd-133">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

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

### <span data-ttu-id="d99fd-134">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="d99fd-134">-InstanceId</span></span>

<span data-ttu-id="d99fd-135">Spécifie l’ID d’instance de la session CIM à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d99fd-135">Specifies the instance ID of the CIM session to remove.</span></span> <span data-ttu-id="d99fd-136">**InstanceID** est un identificateur global unique (Guid) qui identifie de façon unique une session CIM.</span><span class="sxs-lookup"><span data-stu-id="d99fd-136">**InstanceId** is a Globally Unique Identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="d99fd-137">L' **InstanceID** est unique, même si plusieurs sessions sont en cours d’exécution dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d99fd-137">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="d99fd-138">L' **InstanceID** est stocké dans la propriété **InstanceID** de l’objet qui représente une session CIM.</span><span class="sxs-lookup"><span data-stu-id="d99fd-138">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

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

### <span data-ttu-id="d99fd-139">-Name</span><span class="sxs-lookup"><span data-stu-id="d99fd-139">-Name</span></span>

<span data-ttu-id="d99fd-140">Spécifie le nom convivial de la session CIM à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d99fd-140">Specifies the friendly name of the CIM session to remove.</span></span> <span data-ttu-id="d99fd-141">Vous pouvez utiliser des caractères génériques avec ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="d99fd-141">You can use wildcard characters with this parameter.</span></span>

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

### <span data-ttu-id="d99fd-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d99fd-142">-Confirm</span></span>

<span data-ttu-id="d99fd-143">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d99fd-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d99fd-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d99fd-144">-WhatIf</span></span>

<span data-ttu-id="d99fd-145">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d99fd-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d99fd-146">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d99fd-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d99fd-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d99fd-147">CommonParameters</span></span>

<span data-ttu-id="d99fd-148">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d99fd-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d99fd-149">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d99fd-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d99fd-150">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d99fd-150">INPUTS</span></span>

### <span data-ttu-id="d99fd-151">None</span><span class="sxs-lookup"><span data-stu-id="d99fd-151">None</span></span>

<span data-ttu-id="d99fd-152">Cette applet de commande n’accepte aucun objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d99fd-152">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="d99fd-153">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d99fd-153">OUTPUTS</span></span>

### <span data-ttu-id="d99fd-154">System.Object</span><span class="sxs-lookup"><span data-stu-id="d99fd-154">System.Object</span></span>

<span data-ttu-id="d99fd-155">Cette applet de commande retourne un objet qui contient des informations de session CIM.</span><span class="sxs-lookup"><span data-stu-id="d99fd-155">This cmdlet returns an object that contains CIM session information.</span></span>

## <span data-ttu-id="d99fd-156">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d99fd-156">NOTES</span></span>

## <span data-ttu-id="d99fd-157">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d99fd-157">RELATED LINKS</span></span>

[<span data-ttu-id="d99fd-158">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="d99fd-158">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="d99fd-159">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="d99fd-159">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="d99fd-160">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="d99fd-160">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)

