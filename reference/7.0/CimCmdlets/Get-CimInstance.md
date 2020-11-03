---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: edc67596bdb446b18635339255376a17d3f67843
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205554"
---
# <span data-ttu-id="74f91-103">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="74f91-103">Get-CimInstance</span></span>

## <span data-ttu-id="74f91-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="74f91-104">SYNOPSIS</span></span>
<span data-ttu-id="74f91-105">Obtient les instances CIM d’une classe à partir d’un serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="74f91-105">Gets the CIM instances of a class from a CIM server.</span></span>

## <span data-ttu-id="74f91-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="74f91-106">SYNTAX</span></span>

### <span data-ttu-id="74f91-107">ClassNameComputerSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="74f91-107">ClassNameComputerSet (Default)</span></span>

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="74f91-108">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="74f91-108">ResourceUriSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="74f91-109">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="74f91-109">QuerySessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### <span data-ttu-id="74f91-110">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="74f91-110">ClassNameSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="74f91-111">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="74f91-111">CimInstanceSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="74f91-112">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="74f91-112">CimInstanceComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="74f91-113">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="74f91-113">ResourceUriComputerSet</span></span>

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="74f91-114">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="74f91-114">QueryComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## <span data-ttu-id="74f91-115">Description</span><span class="sxs-lookup"><span data-stu-id="74f91-115">DESCRIPTION</span></span>

<span data-ttu-id="74f91-116">L' `Get-CimInstance` applet de commande obtient les instances CIM d’une classe à partir d’un serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="74f91-116">The `Get-CimInstance` cmdlet gets the CIM instances of a class from a CIM server.</span></span> <span data-ttu-id="74f91-117">Vous pouvez spécifier soit le nom de la classe, soit une requête pour cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="74f91-117">You can specify either the class name or a query for this cmdlet.</span></span> <span data-ttu-id="74f91-118">Cette applet de commande retourne un ou plusieurs objets d’instance CIM représentant une capture instantanée des instances CIM présentes sur le serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="74f91-118">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances present on the CIM server.</span></span>

<span data-ttu-id="74f91-119">Si le paramètre **InputObject** n’est pas spécifié, l’applet de commande fonctionne de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="74f91-119">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="74f91-120">Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande fonctionne sur le Windows Management Instrumentation local (WMI) à l’aide d’une session com (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="74f91-120">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="74f91-121">Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande fonctionne sur le serveur CIM spécifié par le paramètre **ComputerName** ou le paramètre **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="74f91-121">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="74f91-122">Si le paramètre **InputObject** est spécifié, l’applet de commande fonctionne de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="74f91-122">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="74f91-123">Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande utilise la session CIM ou le nom de l’ordinateur à partir de l’objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="74f91-123">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="74f91-124">Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande utilise soit la valeur du paramètre CimSession, soit la valeur du paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="74f91-124">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the CimSession parameter value or **ComputerName** parameter value.</span></span>

## <span data-ttu-id="74f91-125">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="74f91-125">EXAMPLES</span></span>

### <span data-ttu-id="74f91-126">Exemple 1 : obtenir les instances CIM d’une classe spécifiée</span><span class="sxs-lookup"><span data-stu-id="74f91-126">Example 1: Get the CIM instances of a specified class</span></span>

<span data-ttu-id="74f91-127">Cet exemple récupère les instances CIM d’une classe nommée **Win32_Process** .</span><span class="sxs-lookup"><span data-stu-id="74f91-127">This example retrieves the CIM instances of a class named **Win32_Process** .</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process
```

### <span data-ttu-id="74f91-128">Exemple 2 : obtenir la liste des espaces de noms d’un serveur WMI</span><span class="sxs-lookup"><span data-stu-id="74f91-128">Example 2: Get a list of namespaces from a WMI server</span></span>

<span data-ttu-id="74f91-129">Cet exemple récupère une liste d’espaces de noms sous l’espace de noms **racine** sur un serveur WMI.</span><span class="sxs-lookup"><span data-stu-id="74f91-129">This example retrieves a list of namespaces under the **Root** namespace on a WMI server.</span></span>

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### <span data-ttu-id="74f91-130">Exemple 3 : obtenir des instances d’une classe filtrées à l’aide d’une requête</span><span class="sxs-lookup"><span data-stu-id="74f91-130">Example 3: Get instances of a class filtered by using a query</span></span>

<span data-ttu-id="74f91-131">Cet exemple récupère toutes les instances CIM qui commencent par la lettre **P** d’une classe nommée **Win32_Process** à l’aide de la requête spécifiée par un paramètre de **requête** .</span><span class="sxs-lookup"><span data-stu-id="74f91-131">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the query specified by a **Query** parameter.</span></span>

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### <span data-ttu-id="74f91-132">Exemple 4 : obtenir des instances d’une classe filtrées à l’aide d’un nom de classe et d’une expression de filtre</span><span class="sxs-lookup"><span data-stu-id="74f91-132">Example 4: Get instances of a class filtered by using a class name and a filter expression</span></span>

<span data-ttu-id="74f91-133">Cet exemple récupère toutes les instances CIM qui commencent par la lettre **P** d’une classe nommée **Win32_Process** à l’aide du paramètre Filter.</span><span class="sxs-lookup"><span data-stu-id="74f91-133">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the Filter parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### <span data-ttu-id="74f91-134">Exemple 5 : récupération des instances CIM avec uniquement les propriétés clés remplies</span><span class="sxs-lookup"><span data-stu-id="74f91-134">Example 5: Get the CIM instances with only key properties filled in</span></span>

<span data-ttu-id="74f91-135">Cet exemple crée une nouvelle instance CIM en mémoire pour une classe nommée **Win32_Process** avec la propriété de clé `@{ "Handle"=0 }` et la stocke dans une variable nommée `$x` .</span><span class="sxs-lookup"><span data-stu-id="74f91-135">This example creates a new CIM instance in memory for a class named **Win32_Process** with the key property `@{ "Handle"=0 }` and stores it in a variable named `$x`.</span></span> <span data-ttu-id="74f91-136">La variable est transmise en tant qu’instance CIM à l' `Get-CimInstance` applet de commande pour obtenir une instance particulière.</span><span class="sxs-lookup"><span data-stu-id="74f91-136">The variable is passed as a CIM instance to the `Get-CimInstance` cmdlet to get a particular instance.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### <span data-ttu-id="74f91-137">Exemple 6 : récupérer des instances CIM et les réutiliser</span><span class="sxs-lookup"><span data-stu-id="74f91-137">Example 6: Retrieve CIM instances and reuse them</span></span>

<span data-ttu-id="74f91-138">Cet exemple obtient les instances CIM d’une classe nommée **Win32_Process** et les stocke dans les variables `$x` et `$y` .</span><span class="sxs-lookup"><span data-stu-id="74f91-138">This example gets the CIM instances of a class named **Win32_Process** and stores them in the variables `$x` and `$y`.</span></span> <span data-ttu-id="74f91-139">La variable `$x` est ensuite mise en forme dans une table contenant uniquement les propriétés **Name** et **KernelModeTime** , la table définie sur **AutoSize** .</span><span class="sxs-lookup"><span data-stu-id="74f91-139">The variable `$x` is then formatted in a table containing only the **Name** and **KernelModeTime** properties, the table set to **AutoSize** .</span></span>

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### <span data-ttu-id="74f91-140">Exemple 7 : récupérer des instances CIM à partir d’un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="74f91-140">Example 7: Get CIM instances from remote computer</span></span>

<span data-ttu-id="74f91-141">Cet exemple récupère les instances CIM d’une classe nommée **Win32_ComputerSystem** à partir des ordinateurs distants **SERVEUR01** et **Server02** .</span><span class="sxs-lookup"><span data-stu-id="74f91-141">This example retrieves the CIM instances of a class named **Win32_ComputerSystem** from the remote computers named **Server01** and **Server02** .</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### <span data-ttu-id="74f91-142">Exemple 8 : obtention uniquement des propriétés de clé, et non de toutes les propriétés</span><span class="sxs-lookup"><span data-stu-id="74f91-142">Example 8: Getting only the key properties, instead of all properties</span></span>

<span data-ttu-id="74f91-143">Cet exemple récupère uniquement les propriétés de clé, ce qui réduit la taille de l’objet et du trafic réseau.</span><span class="sxs-lookup"><span data-stu-id="74f91-143">This example retrieves only the key properties, which reduces the size of the object and network traffic.</span></span>

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### <span data-ttu-id="74f91-144">Exemple 9 : obtention d’un seul sous-ensemble de propriétés, au lieu de toutes les propriétés</span><span class="sxs-lookup"><span data-stu-id="74f91-144">Example 9: Getting only a subset of properties, instead of all properties</span></span>

<span data-ttu-id="74f91-145">Cet exemple récupère uniquement un sous-ensemble de propriétés, ce qui réduit la taille de l’objet et du trafic réseau.</span><span class="sxs-lookup"><span data-stu-id="74f91-145">This example retrieves only a subset of properties, which reduces the size of the object and network traffic.</span></span>

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

<span data-ttu-id="74f91-146">L’instance Récupérée avec le paramètre **Property** peut être utilisée pour effectuer d’autres opérations CIM, par exemple `Set-CimInstance` ou `Invoke-CimMethod` .</span><span class="sxs-lookup"><span data-stu-id="74f91-146">The instance retrieved with the **Property** parameter can be used to perform other CIM operations, for example `Set-CimInstance` or `Invoke-CimMethod`.</span></span>

### <span data-ttu-id="74f91-147">Exemple 10 : récupération de l’instance CIM à l’aide d’une session CIM</span><span class="sxs-lookup"><span data-stu-id="74f91-147">Example 10: Get the CIM instance using CIM session</span></span>

<span data-ttu-id="74f91-148">Cet exemple crée une session CIM sur les ordinateurs nommés **SERVEUR01** et **Server02** à l’aide de l’applet de commande `New-CimSession` et stocke les informations de session dans une variable nommée `$s` .</span><span class="sxs-lookup"><span data-stu-id="74f91-148">This example creates a CIM session on the computers named **Server01** and **Server02** using the `New-CimSession` cmdlet and stores the session information in a variable named `$s`.</span></span> <span data-ttu-id="74f91-149">Le contenu de la variable est ensuite passé à `Get-CimInstance` en utilisant le paramètre **CimSession** pour récupérer les instances CIM de la classe nommée **Win32_ComputerSystem** .</span><span class="sxs-lookup"><span data-stu-id="74f91-149">The contents of the variable are then passed to `Get-CimInstance` by using the **CimSession** parameter, to get the CIM instances of the class named **Win32_ComputerSystem** .</span></span>

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## <span data-ttu-id="74f91-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="74f91-150">PARAMETERS</span></span>

### <span data-ttu-id="74f91-151">-CimSession</span><span class="sxs-lookup"><span data-stu-id="74f91-151">-CimSession</span></span>

<span data-ttu-id="74f91-152">Spécifie la session CIM à utiliser pour cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="74f91-152">Specifies the CIM session to use for this cmdlet.</span></span> <span data-ttu-id="74f91-153">Entrez une variable qui contient la session CIM ou une commande qui crée ou obtient la session CIM, telle que les `New-CimSession` applets de commande ou `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="74f91-153">Enter a variable that contains the CIM session or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="74f91-154">Pour plus d’informations, consultez [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="74f91-154">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="74f91-155">-ClassName</span><span class="sxs-lookup"><span data-stu-id="74f91-155">-ClassName</span></span>

<span data-ttu-id="74f91-156">Spécifie le nom de la classe CIM pour laquelle récupérer les instances CIM.</span><span class="sxs-lookup"><span data-stu-id="74f91-156">Specifies the name of the CIM class for which to retrieve the CIM instances.</span></span> <span data-ttu-id="74f91-157">Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des classes, car PowerShell obtient une liste des classes du serveur WMI local pour fournir une liste de noms de classe.</span><span class="sxs-lookup"><span data-stu-id="74f91-157">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74f91-158">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="74f91-158">-ComputerName</span></span>

<span data-ttu-id="74f91-159">Spécifie l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="74f91-159">Specifies computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="74f91-160">Vous pouvez spécifier un nom de domaine complet (FQDN), un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="74f91-160">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="74f91-161">Si vous ne spécifiez pas ce paramètre, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="74f91-161">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="74f91-162">Si vous spécifiez ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan.</span><span class="sxs-lookup"><span data-stu-id="74f91-162">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="74f91-163">Si plusieurs opérations sont exécutées sur le même ordinateur, connectez-vous à l’aide d’une session CIM pour obtenir de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="74f91-163">If multiple operations are being performed on the same computer, connect using a CIM session for better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, CimInstanceComputerSet, ResourceUriComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74f91-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="74f91-164">-Filter</span></span>

<span data-ttu-id="74f91-165">Spécifie une clause WHERE à utiliser comme filtre.</span><span class="sxs-lookup"><span data-stu-id="74f91-165">Specifies a where clause to use as a filter.</span></span> <span data-ttu-id="74f91-166">Spécifiez la clause dans le langage de requête **WQL** ou **CQL** .</span><span class="sxs-lookup"><span data-stu-id="74f91-166">Specify the clause in either the **WQL** or the **CQL** query language.</span></span> <span data-ttu-id="74f91-167">N’incluez pas le `WHERE` mot clé dans la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="74f91-167">Do not include the `WHERE` keyword in the value of the parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74f91-168">-InputObject</span><span class="sxs-lookup"><span data-stu-id="74f91-168">-InputObject</span></span>

<span data-ttu-id="74f91-169">Spécifie un objet d’instance CIM à utiliser comme entrée.</span><span class="sxs-lookup"><span data-stu-id="74f91-169">Specifies a CIM instance object to use as input.</span></span>

<span data-ttu-id="74f91-170">Si vous utilisez déjà un objet d’instance CIM, vous pouvez utiliser ce paramètre pour passer l’objet d’instance CIM afin d’obtenir l’instantané le plus récent à partir du serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="74f91-170">If you are already working with a CIM instance object, you can use this parameter to pass the CIM instance object in order to get the latest snapshot from the CIM server.</span></span> <span data-ttu-id="74f91-171">Lorsque vous transmettez un objet d’instance CIM en tant qu’entrée, `Get-CimInstance` retourne l’objet à partir du serveur à l’aide d’une opération d’extraction CIM, au lieu d’une opération d’énumération ou de requête.</span><span class="sxs-lookup"><span data-stu-id="74f91-171">When you pass a CIM instance object as an input, `Get-CimInstance` returns the object from server using a get CIM operation, instead of an enumerate or query operation.</span></span> <span data-ttu-id="74f91-172">L’utilisation d’une opération obtenir CIM est plus efficace que la récupération de toutes les instances, puis leur filtrage.</span><span class="sxs-lookup"><span data-stu-id="74f91-172">Using a get CIM operation is more efficient than retrieving all instances and then filtering them.</span></span>

<span data-ttu-id="74f91-173">Si la classe CIM n’implémente pas l’opération d’extraction, le fait de spécifier le paramètre **InputObject** retourne une erreur.</span><span class="sxs-lookup"><span data-stu-id="74f91-173">If the CIM class does not implement the get operation, then specifying the **InputObject** parameter returns an error.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceSessionSet, CimInstanceComputerSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="74f91-174">-Uniquement</span><span class="sxs-lookup"><span data-stu-id="74f91-174">-KeyOnly</span></span>

<span data-ttu-id="74f91-175">Indique que seuls les objets avec des propriétés de clé renseignés sont retournés.</span><span class="sxs-lookup"><span data-stu-id="74f91-175">Indicates that only objects with key properties populated are returned.</span></span> <span data-ttu-id="74f91-176">La spécification du paramètre **keyonly** réduit la quantité de données transférées sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="74f91-176">Specifying the **KeyOnly** parameter reduces the amount of data transferred over the network.</span></span>

<span data-ttu-id="74f91-177">Utilisez le paramètre **keyonly** pour retourner uniquement une petite partie de l’objet, qui peut être utilisée pour d’autres opérations, telles que `Set-CimInstance` les `Get-CimAssociatedInstance` applets de commande ou.</span><span class="sxs-lookup"><span data-stu-id="74f91-177">Use the **KeyOnly** parameter to return only a small portion of the object, which can be used for other operations, such as the `Set-CimInstance` or `Get-CimAssociatedInstance` cmdlets.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74f91-178">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="74f91-178">-Namespace</span></span>

<span data-ttu-id="74f91-179">Spécifie l’espace de noms de la classe CIM.</span><span class="sxs-lookup"><span data-stu-id="74f91-179">Specifies the namespace of CIM class.</span></span>

<span data-ttu-id="74f91-180">L’espace de noms par défaut est **root/cimv2** .</span><span class="sxs-lookup"><span data-stu-id="74f91-180">The default namespace is **root/cimv2** .</span></span> <span data-ttu-id="74f91-181">Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="74f91-181">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74f91-182">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="74f91-182">-OperationTimeoutSec</span></span>

<span data-ttu-id="74f91-183">Spécifie la durée pendant laquelle l’applet de commande attend une réponse de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="74f91-183">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="74f91-184">Par défaut, la valeur de ce paramètre est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="74f91-184">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="74f91-185">Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion fiable de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables, car l’opération sur le serveur expire avant que le client puisse se reconnecter.</span><span class="sxs-lookup"><span data-stu-id="74f91-185">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74f91-186">-Propriété</span><span class="sxs-lookup"><span data-stu-id="74f91-186">-Property</span></span>

<span data-ttu-id="74f91-187">Spécifie un jeu de propriétés d’instance à récupérer.</span><span class="sxs-lookup"><span data-stu-id="74f91-187">Specifies a set of instance properties to retrieve.</span></span> <span data-ttu-id="74f91-188">Utilisez ce paramètre lorsque vous devez réduire la taille de l’objet retourné, soit en mémoire, soit sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="74f91-188">Use this parameter when you need to reduce the size of the object returned, either in memory or over the network.</span></span> <span data-ttu-id="74f91-189">L’objet retourné contient également les propriétés de clé, même si vous ne les avez pas listées à l’aide du paramètre **Property** .</span><span class="sxs-lookup"><span data-stu-id="74f91-189">The object returned also contains the key properties even if you have not listed them using the **Property** parameter.</span></span> <span data-ttu-id="74f91-190">D’autres propriétés de la classe sont présentes, mais elles ne sont pas remplies.</span><span class="sxs-lookup"><span data-stu-id="74f91-190">Other properties of the class are present but they are not populated.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases: SelectProperties

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74f91-191">-Query</span><span class="sxs-lookup"><span data-stu-id="74f91-191">-Query</span></span>

<span data-ttu-id="74f91-192">Spécifie une requête à exécuter sur le serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="74f91-192">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="74f91-193">Si la valeur spécifiée contient des guillemets doubles, des `"` guillemets simples `'` ou une barre oblique inverse `\` , vous devez placer ces caractères dans une séquence d’échappement en les faisant précéder d’une barre oblique inverse.</span><span class="sxs-lookup"><span data-stu-id="74f91-193">If the value specified contains double quotes `"`, single quotes `'`, or a backslash `\`, you must escape those characters by prefixing them with the backslash character.</span></span> <span data-ttu-id="74f91-194">Si la valeur spécifiée utilise l’opérateur **Like** WQL, vous devez placer les caractères suivants dans une séquence d’échappement en les plaçant entre crochets `[]` : pourcentage, trait de `%` soulignement `_` ou crochet ouvrant `[` .</span><span class="sxs-lookup"><span data-stu-id="74f91-194">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets `[]`: percent `%`, underscore `_`, or opening square bracket `[`.</span></span>

<span data-ttu-id="74f91-195">Vous ne pouvez pas utiliser une requête de métadonnées pour récupérer une liste de classes ou une requête d’événement.</span><span class="sxs-lookup"><span data-stu-id="74f91-195">You cannot use a metadata query to retrieve a list of classes or an event query.</span></span> <span data-ttu-id="74f91-196">Pour récupérer une liste de classes, utilisez l' `Get-CimClass` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="74f91-196">To retrieve a list of classes, use the `Get-CimClass` cmdlet.</span></span> <span data-ttu-id="74f91-197">Pour récupérer une requête d’événement, utilisez l’applet de commande `Register-CimIndicationEvent` .</span><span class="sxs-lookup"><span data-stu-id="74f91-197">To retrieve an event query, use the `Register-CimIndicationEvent` cmdlet.</span></span>

<span data-ttu-id="74f91-198">Vous pouvez spécifier le dialecte de requête à l’aide du paramètre **QueryDialect** .</span><span class="sxs-lookup"><span data-stu-id="74f91-198">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74f91-199">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="74f91-199">-QueryDialect</span></span>

<span data-ttu-id="74f91-200">Spécifie le langage de requête utilisé pour le paramètre de requête.</span><span class="sxs-lookup"><span data-stu-id="74f91-200">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="74f91-201">Les valeurs acceptables pour ce paramètre sont les suivantes : **WQL** ou **CQL** .</span><span class="sxs-lookup"><span data-stu-id="74f91-201">The acceptable values for this parameter are: **WQL** or **CQL** .</span></span> <span data-ttu-id="74f91-202">La valeur par défaut est **WQL** .</span><span class="sxs-lookup"><span data-stu-id="74f91-202">The default value is **WQL** .</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QuerySessionSet, ClassNameSessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74f91-203">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="74f91-203">-ResourceUri</span></span>

<span data-ttu-id="74f91-204">Spécifie l’URI (Uniform Resource Identifier) de la ressource de la classe ou de l’instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="74f91-204">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="74f91-205">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="74f91-205">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="74f91-206">Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="74f91-206">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="74f91-207">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="74f91-207">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="74f91-208">Par défaut, si vous ne spécifiez pas ce paramètre, l’URI de ressource standard DMTF `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` est utilisé et le nom de la classe y est ajouté.</span><span class="sxs-lookup"><span data-stu-id="74f91-208">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="74f91-209">**Resourceuri** peut être utilisé uniquement avec les sessions CIM créées à l’aide du protocole WSMan, ou lors de la spécification du paramètre **ComputerName** , qui crée une session CIM à l’aide de wsman.</span><span class="sxs-lookup"><span data-stu-id="74f91-209">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="74f91-210">Si vous spécifiez ce paramètre sans spécifier le paramètre **ComputerName** ou si vous spécifiez une session CIM créée à l’aide du protocole DCOM, vous obtiendrez une erreur, car le protocole DCOM ne prend pas en charge le paramètre **resourceuri** .</span><span class="sxs-lookup"><span data-stu-id="74f91-210">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="74f91-211">Si le paramètre **resourceuri** et le paramètre **Filter** sont tous deux spécifiés, le paramètre **Filter** est ignoré.</span><span class="sxs-lookup"><span data-stu-id="74f91-211">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet, QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="74f91-212">-Superficielle</span><span class="sxs-lookup"><span data-stu-id="74f91-212">-Shallow</span></span>

<span data-ttu-id="74f91-213">Indique que les instances d’une classe sont retournées sans inclure les instances des classes enfants.</span><span class="sxs-lookup"><span data-stu-id="74f91-213">Indicates that the instances of a class are returned without including the instances of any child classes.</span></span> <span data-ttu-id="74f91-214">Par défaut, l’applet de commande retourne les instances d’une classe et de ses classes enfants.</span><span class="sxs-lookup"><span data-stu-id="74f91-214">By default, the cmdlet returns the instances of a class and its child classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="74f91-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="74f91-215">CommonParameters</span></span>

<span data-ttu-id="74f91-216">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="74f91-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="74f91-217">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="74f91-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="74f91-218">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="74f91-218">INPUTS</span></span>

### <span data-ttu-id="74f91-219">Instance CIM</span><span class="sxs-lookup"><span data-stu-id="74f91-219">CIM Instance</span></span>

<span data-ttu-id="74f91-220">Cette applet de commande accepte un objet d’entrée spécifié avec le paramètre InputObject.</span><span class="sxs-lookup"><span data-stu-id="74f91-220">This cmdlet accepts an input objects specified with the InputObject parameter.</span></span>

## <span data-ttu-id="74f91-221">SORTIES</span><span class="sxs-lookup"><span data-stu-id="74f91-221">OUTPUTS</span></span>

### <span data-ttu-id="74f91-222">Instance CIM</span><span class="sxs-lookup"><span data-stu-id="74f91-222">CIM Instance</span></span>

<span data-ttu-id="74f91-223">Cette applet de commande retourne un ou plusieurs objets d’instance CIM représentant une capture instantanée des instances CIM sur le serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="74f91-223">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances on the CIM server.</span></span>

## <span data-ttu-id="74f91-224">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="74f91-224">NOTES</span></span>

## <span data-ttu-id="74f91-225">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="74f91-225">RELATED LINKS</span></span>

[<span data-ttu-id="74f91-226">Format-Table</span><span class="sxs-lookup"><span data-stu-id="74f91-226">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="74f91-227">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="74f91-227">Get-CimAssociatedInstance</span></span>](Get-CimAssociatedInstance.md)

[<span data-ttu-id="74f91-228">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="74f91-228">Get-CimClass</span></span>](Get-CimClass.md)

[<span data-ttu-id="74f91-229">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="74f91-229">Invoke-CimMethod</span></span>](invoke-cimmethod.md)

[<span data-ttu-id="74f91-230">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="74f91-230">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="74f91-231">Register-CimIndicationEvent</span><span class="sxs-lookup"><span data-stu-id="74f91-231">Register-CimIndicationEvent</span></span>](Register-CimIndicationEvent.md)

[<span data-ttu-id="74f91-232">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="74f91-232">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="74f91-233">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="74f91-233">Set-CimInstance</span></span>](Set-CimInstance.md)
