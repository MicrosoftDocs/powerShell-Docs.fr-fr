---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimSession
ms.openlocfilehash: 0e531b3cc072b7cc1efe0ef06fb741326bf3a72b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598561"
---
# <span data-ttu-id="076da-102">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="076da-102">Get-CimSession</span></span>

## <span data-ttu-id="076da-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="076da-103">SYNOPSIS</span></span>
<span data-ttu-id="076da-104">Obtient les objets de session CIM de la session active.</span><span class="sxs-lookup"><span data-stu-id="076da-104">Gets the CIM session objects from the current session.</span></span>

## <span data-ttu-id="076da-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="076da-105">SYNTAX</span></span>

### <span data-ttu-id="076da-106">ComputerNameSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="076da-106">ComputerNameSet (Default)</span></span>

```
Get-CimSession [[-ComputerName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="076da-107">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="076da-107">SessionIdSet</span></span>

```
Get-CimSession [-Id] <UInt32[]> [<CommonParameters>]
```

### <span data-ttu-id="076da-108">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="076da-108">InstanceIdSet</span></span>

```
Get-CimSession -InstanceId <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="076da-109">NameSet</span><span class="sxs-lookup"><span data-stu-id="076da-109">NameSet</span></span>

```
Get-CimSession -Name <String[]> [<CommonParameters>]
```

## <span data-ttu-id="076da-110">Description</span><span class="sxs-lookup"><span data-stu-id="076da-110">DESCRIPTION</span></span>

<span data-ttu-id="076da-111">Par défaut, l’applet de commande obtient toutes les sessions CIM créées dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="076da-111">By default, the cmdlet gets all of the CIM sessions created in the current PowerShell session.</span></span> <span data-ttu-id="076da-112">Vous pouvez utiliser les paramètres de `Get-CimSession` pour obtenir les sessions qui sont destinées à des ordinateurs particuliers, ou vous pouvez identifier les sessions à l’aide de leurs noms ou d’autres identificateurs.</span><span class="sxs-lookup"><span data-stu-id="076da-112">You can use the parameters of `Get-CimSession` to get the sessions that are for particular computers, or you can identify sessions by their names or other identifiers.</span></span> <span data-ttu-id="076da-113">`Get-CimSession` n’obtient pas les sessions CIM qui ont été créées dans d’autres sessions PowerShell ou qui ont été créées sur d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="076da-113">`Get-CimSession` does not get CIM sessions that were created in other PowerShell sessions or that were created on other computers.</span></span>

<span data-ttu-id="076da-114">Pour plus d’informations sur les sessions CIM, consultez [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="076da-114">For more information about CIM sessions, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

## <span data-ttu-id="076da-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="076da-115">EXAMPLES</span></span>

### <span data-ttu-id="076da-116">Exemple 1 : récupérer des sessions CIM à partir de la session PowerShell active</span><span class="sxs-lookup"><span data-stu-id="076da-116">Example 1: Get CIM sessions from the current PowerShell session</span></span>

<span data-ttu-id="076da-117">Cet exemple crée des sessions CIM à l’aide [de New-CimSession](New-CimSession.md), puis obtient les sessions CIM à l’aide de `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="076da-117">This example creates CIM sessions using [New-CimSession](New-CimSession.md), and then gets the CIM sessions using `Get-CimSession`.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc3-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="076da-118">Exemple 2 : obtenir les sessions CIM sur un ordinateur spécifique</span><span class="sxs-lookup"><span data-stu-id="076da-118">Example 2: Get the CIM sessions to a specific computer</span></span>

<span data-ttu-id="076da-119">Cet exemple obtient les sessions CIM qui sont connectées à l’ordinateur nommé **Server02**.</span><span class="sxs-lookup"><span data-stu-id="076da-119">This example gets the CIM sessions that are connected to the computer named **Server02**.</span></span>

```powershell
Get-CimSession -ComputerName Server02
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="076da-120">Exemple 3 : obtenir la liste des sessions CIM, puis mettre en forme la liste</span><span class="sxs-lookup"><span data-stu-id="076da-120">Example 3: Get a list of CIM sessions and then format the list</span></span>

<span data-ttu-id="076da-121">Cet exemple obtient toutes les sessions CIM dans la session PowerShell en cours et affiche une table contenant uniquement les propriétés **ComputerName** et **InstanceID** .</span><span class="sxs-lookup"><span data-stu-id="076da-121">This example gets all CIM sessions in the current PowerShell session and displays a table containing only the **ComputerName** and **InstanceID** properties.</span></span>

```powershell
Get-CimSession | Format-Table -Property ComputerName,InstanceId
```

```Output
ComputerName InstanceId
------------ ----------
Server01     d1413bc3-162a-4cb8-9aec-4d2c61253d59
Server02     c0095981-52c5-4e7f-a5bb-c4c680541710
```

### <span data-ttu-id="076da-122">Exemple 4 : obtenir toutes les sessions CIM qui ont des noms spécifiques</span><span class="sxs-lookup"><span data-stu-id="076da-122">Example 4: Get all the CIM sessions that have specific names</span></span>

<span data-ttu-id="076da-123">Cet exemple obtient toutes les sessions CIM dont les noms commencent par **serv**.</span><span class="sxs-lookup"><span data-stu-id="076da-123">This example gets all CIM sessions that have names that begin with **serv**.</span></span>

```powershell
Get-CimSession -ComputerName Serv*
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="076da-124">Exemple 5 : obtenir une session CIM spécifique</span><span class="sxs-lookup"><span data-stu-id="076da-124">Example 5: Get a specific CIM session</span></span>

<span data-ttu-id="076da-125">Cet exemple obtient la session CIM dont l' **ID** est 2.</span><span class="sxs-lookup"><span data-stu-id="076da-125">This example gets the CIM session that has an **Id** of 2.</span></span>

```powershell
Get-CimSession -ID 2
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

## <span data-ttu-id="076da-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="076da-126">PARAMETERS</span></span>

### <span data-ttu-id="076da-127">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="076da-127">-ComputerName</span></span>

<span data-ttu-id="076da-128">Spécifie le nom de l’ordinateur auquel les sessions CIM doivent être connectées.</span><span class="sxs-lookup"><span data-stu-id="076da-128">Specifies the name of the computer to get CIM sessions connected to.</span></span> <span data-ttu-id="076da-129">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="076da-129">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="076da-130">-Id</span><span class="sxs-lookup"><span data-stu-id="076da-130">-Id</span></span>

<span data-ttu-id="076da-131">Spécifie l’identificateur de la session CIM à récupérer.</span><span class="sxs-lookup"><span data-stu-id="076da-131">Specifies the identifier of the CIM session to get.</span></span> <span data-ttu-id="076da-132">Pour plusieurs ID, utilisez des virgules pour séparer les ID ou utilisez l’opérateur de plage ( `..` ) pour spécifier une plage d’ID.</span><span class="sxs-lookup"><span data-stu-id="076da-132">For multiple IDs, use commas to separate the IDs or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="076da-133">Un **ID** est un entier qui identifie de façon unique la session CIM au sein de la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="076da-133">An **Id** is an integer that uniquely identifies the CIM session within the current PowerShell session.</span></span>

<span data-ttu-id="076da-134">Pour plus d’informations sur l’opérateur de plage, consultez [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="076da-134">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

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

### <span data-ttu-id="076da-135">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="076da-135">-InstanceId</span></span>

<span data-ttu-id="076da-136">Spécifie les ID d’instance de la session CIM à récupérer.</span><span class="sxs-lookup"><span data-stu-id="076da-136">Specifies the instance IDs of the CIM session to get.</span></span>

<span data-ttu-id="076da-137">**InstanceID** est un identificateur global unique (Guid) qui identifie de façon unique une session CIM.</span><span class="sxs-lookup"><span data-stu-id="076da-137">**InstanceId** is a globally-unique identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="076da-138">L' **InstanceID** est unique, même si plusieurs sessions sont en cours d’exécution dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="076da-138">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="076da-139">L' **InstanceID** est stocké dans la propriété **InstanceID** de l’objet qui représente une session CIM.</span><span class="sxs-lookup"><span data-stu-id="076da-139">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

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

### <span data-ttu-id="076da-140">-Name</span><span class="sxs-lookup"><span data-stu-id="076da-140">-Name</span></span>

<span data-ttu-id="076da-141">Obtient une ou plusieurs sessions CIM qui contiennent les noms conviviaux spécifiés.</span><span class="sxs-lookup"><span data-stu-id="076da-141">Gets one or more CIM sessions which contain the specified friendly names.</span></span> <span data-ttu-id="076da-142">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="076da-142">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="076da-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="076da-143">CommonParameters</span></span>
<span data-ttu-id="076da-144">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="076da-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="076da-145">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="076da-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="076da-146">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="076da-146">INPUTS</span></span>

### <span data-ttu-id="076da-147">None</span><span class="sxs-lookup"><span data-stu-id="076da-147">None</span></span>

## <span data-ttu-id="076da-148">SORTIES</span><span class="sxs-lookup"><span data-stu-id="076da-148">OUTPUTS</span></span>

### <span data-ttu-id="076da-149">Microsoft.Management.Infrastructure.CimSession</span><span class="sxs-lookup"><span data-stu-id="076da-149">Microsoft.Management.Infrastructure.CimSession</span></span>

## <span data-ttu-id="076da-150">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="076da-150">NOTES</span></span>

## <span data-ttu-id="076da-151">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="076da-151">RELATED LINKS</span></span>

[<span data-ttu-id="076da-152">Format-Table</span><span class="sxs-lookup"><span data-stu-id="076da-152">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="076da-153">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="076da-153">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="076da-154">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="076da-154">Remove-CimSession</span></span>](remove-cimsession.md)

[<span data-ttu-id="076da-155">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="076da-155">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)

