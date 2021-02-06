---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 01/21/2020
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/invoke-cimmethod?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-CimMethod
ms.openlocfilehash: 1217e07d09213d7c0e223129207c085b9ba2d48d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595902"
---
# <span data-ttu-id="729ee-102">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="729ee-102">Invoke-CimMethod</span></span>

## <span data-ttu-id="729ee-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="729ee-103">SYNOPSIS</span></span>
<span data-ttu-id="729ee-104">Appelle une méthode d’une classe CIM.</span><span class="sxs-lookup"><span data-stu-id="729ee-104">Invokes a method of a CIM class.</span></span>

## <span data-ttu-id="729ee-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="729ee-105">SYNTAX</span></span>

### <span data-ttu-id="729ee-106">ClassNameComputerSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="729ee-106">ClassNameComputerSet (Default)</span></span>

```
Invoke-CimMethod [-ClassName] <String> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="729ee-107">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="729ee-107">ClassNameSessionSet</span></span>

```
Invoke-CimMethod [-ClassName] <String> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="729ee-108">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="729ee-108">ResourceUriComputerSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="729ee-109">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="729ee-109">CimInstanceSessionSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="729ee-110">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="729ee-110">CimInstanceComputerSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="729ee-111">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="729ee-111">ResourceUriSessionSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="729ee-112">CimClassComputerSet</span><span class="sxs-lookup"><span data-stu-id="729ee-112">CimClassComputerSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="729ee-113">CimClassSessionSet</span><span class="sxs-lookup"><span data-stu-id="729ee-113">CimClassSessionSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="729ee-114">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="729ee-114">QueryComputerSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="729ee-115">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="729ee-115">QuerySessionSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="729ee-116">Description</span><span class="sxs-lookup"><span data-stu-id="729ee-116">DESCRIPTION</span></span>

<span data-ttu-id="729ee-117">L' `Invoke-CimMethod` applet de commande appelle une méthode d’une classe CIM ou d’une instance CIM à l’aide des paires nom-valeur spécifiées par le paramètre **arguments** .</span><span class="sxs-lookup"><span data-stu-id="729ee-117">The `Invoke-CimMethod` cmdlet invokes a method of a CIM class or CIM instance using the name-value pairs specified by the **Arguments** parameter.</span></span>

<span data-ttu-id="729ee-118">Si le paramètre **InputObject** n’est pas spécifié, l’applet de commande fonctionne de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="729ee-118">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="729ee-119">Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande fonctionne sur le Windows Management Instrumentation local (WMI) à l’aide d’une session com (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="729ee-119">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="729ee-120">Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande fonctionne sur le serveur CIM spécifié par le paramètre **ComputerName** ou le paramètre **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="729ee-120">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="729ee-121">Si le paramètre **InputObject** est spécifié, l’applet de commande fonctionne de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="729ee-121">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="729ee-122">Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande utilise la session CIM ou le nom de l’ordinateur à partir de l’objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="729ee-122">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="729ee-123">Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande utilise soit la valeur du paramètre **CimSession** , soit la valeur du paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="729ee-123">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="729ee-124">Ce scénario n’est pas courant.</span><span class="sxs-lookup"><span data-stu-id="729ee-124">This is not a common scenario.</span></span>

## <span data-ttu-id="729ee-125">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="729ee-125">EXAMPLES</span></span>

### <span data-ttu-id="729ee-126">Exemple 1 : appeler une méthode</span><span class="sxs-lookup"><span data-stu-id="729ee-126">Example 1: Invoke a method</span></span>

<span data-ttu-id="729ee-127">Cet exemple appelle la méthode **Terminate** de la classe **Win32_Process** .</span><span class="sxs-lookup"><span data-stu-id="729ee-127">This example invokes the **Terminate** method of the **Win32_Process** class.</span></span>

```powershell
Invoke-CimMethod -Query 'select * from Win32_Process where name like "notepad%"' -MethodName "Terminate"
```

### <span data-ttu-id="729ee-128">Exemple 2 : appeler une méthode à l’aide d’un objet d’instance CIM</span><span class="sxs-lookup"><span data-stu-id="729ee-128">Example 2: Invoke a method using CIM instance object</span></span>

<span data-ttu-id="729ee-129">Cet exemple récupère l’objet d’instance CIM et le stocke dans une variable nommée `$x` à l’aide de l’applet de commande `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="729ee-129">This example retrieves the CIM instance object and stores it in a variable named `$x` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="729ee-130">Le contenu de la variable est ensuite utilisé comme **InputObject** pour l’applet de commande `Invoke-CimMethod` .</span><span class="sxs-lookup"><span data-stu-id="729ee-130">The contents of the variable are then used as the **InputObject** for the `Invoke-CimMethod` cmdlet.</span></span> <span data-ttu-id="729ee-131">La méthode **GetOwner** est appelée pour **CimInstance**.</span><span class="sxs-lookup"><span data-stu-id="729ee-131">The **GetOwner** method is invoked for the **CimInstance**.</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Process where name like "notepad%"'
Invoke-CimMethod -InputObject $x -MethodName GetOwner
```

### <span data-ttu-id="729ee-132">Exemple 3 : appeler une méthode statique à l’aide d’arguments</span><span class="sxs-lookup"><span data-stu-id="729ee-132">Example 3: Invoke a static method using arguments</span></span>

<span data-ttu-id="729ee-133">Cet exemple appelle la méthode **Create** nommée à l’aide du paramètre **arguments** .</span><span class="sxs-lookup"><span data-stu-id="729ee-133">This example invokes the **Create** method named using the **Arguments** parameter.</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Process -MethodName "Create" -Arguments @{
  CommandLine = 'notepad.exe'; CurrentDirectory = "C:\windows\system32"
}
```

### <span data-ttu-id="729ee-134">Exemple 4 : validation côté client</span><span class="sxs-lookup"><span data-stu-id="729ee-134">Example 4: Client-side validation</span></span>

<span data-ttu-id="729ee-135">Cet exemple effectue une validation côté client pour la méthode **xyz** en passant un objet **CimClass** à `Invoke-CimMethod` .</span><span class="sxs-lookup"><span data-stu-id="729ee-135">This example performs client-side validation for the **xyz** method by passing a **CimClass** object to `Invoke-CimMethod`.</span></span>

```powershell
$c = Get-CimClass -ClassName Win32_Process
Invoke-CimMethod -CimClass $c -MethodName "xyz" -Arguments @{ CommandLine = 'notepad.exe' }
```

## <span data-ttu-id="729ee-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="729ee-136">PARAMETERS</span></span>

### <span data-ttu-id="729ee-137">-Arguments</span><span class="sxs-lookup"><span data-stu-id="729ee-137">-Arguments</span></span>

<span data-ttu-id="729ee-138">Spécifie les paramètres à passer à la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="729ee-138">Specifies the parameters to pass to the called method.</span></span> <span data-ttu-id="729ee-139">Spécifiez les valeurs de ce paramètre en tant que paires nom-valeur, stockées dans une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="729ee-139">Specify the values for this parameter as name-value pairs, stored in a hash table.</span></span> <span data-ttu-id="729ee-140">L’ordre des valeurs entrées n’est pas important.</span><span class="sxs-lookup"><span data-stu-id="729ee-140">The order of the values entered isn't important.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="729ee-141">-CimClass</span><span class="sxs-lookup"><span data-stu-id="729ee-141">-CimClass</span></span>

<span data-ttu-id="729ee-142">Spécifie un objet de classe CIM qui représente une définition de classe CIM sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="729ee-142">Specifies a CIM class object that represents a CIM class definition on the server.</span></span> <span data-ttu-id="729ee-143">Utilisez ce paramètre lors de l’appel d’une méthode statique d’une classe.</span><span class="sxs-lookup"><span data-stu-id="729ee-143">Use this parameter when invoking a static method of a class.</span></span>

<span data-ttu-id="729ee-144">Vous pouvez utiliser l' `Get-CimClass` applet de commande pour récupérer une définition de classe à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="729ee-144">You can use the `Get-CimClass` cmdlet to retrieve a class definition from the server.</span></span>

<span data-ttu-id="729ee-145">L’utilisation de ce paramètre permet d’améliorer les validations de schéma côté client.</span><span class="sxs-lookup"><span data-stu-id="729ee-145">Using this parameter results in better client side schema validations.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassComputerSet, CimClassSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="729ee-146">-CimSession</span><span class="sxs-lookup"><span data-stu-id="729ee-146">-CimSession</span></span>

<span data-ttu-id="729ee-147">Exécute la commande à l’aide de la session CIM spécifiée.</span><span class="sxs-lookup"><span data-stu-id="729ee-147">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="729ee-148">Entrez une variable qui contient la session CIM ou une commande qui crée ou obtient la session CIM, telle que les `New-CimSession` applets de commande ou `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="729ee-148">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="729ee-149">Pour plus d’informations, consultez [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="729ee-149">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, CimInstanceSessionSet, CimClassSessionSet, QuerySessionSet, ResourceUriSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="729ee-150">-ClassName</span><span class="sxs-lookup"><span data-stu-id="729ee-150">-ClassName</span></span>

<span data-ttu-id="729ee-151">Spécifie le nom de la classe CIM pour laquelle effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="729ee-151">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="729ee-152">Ce paramètre est utilisé uniquement pour les méthodes statiques.</span><span class="sxs-lookup"><span data-stu-id="729ee-152">This parameter is only used for static methods.</span></span> <span data-ttu-id="729ee-153">Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des classes, car PowerShell obtient une liste des classes du serveur WMI local pour fournir une liste de noms de classe.</span><span class="sxs-lookup"><span data-stu-id="729ee-153">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases: Class

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="729ee-154">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="729ee-154">-ComputerName</span></span>

<span data-ttu-id="729ee-155">Spécifie le nom de l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="729ee-155">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="729ee-156">Vous pouvez spécifier un nom de domaine complet (FQDN), un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="729ee-156">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="729ee-157">Lors de l’utilisation de ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan.</span><span class="sxs-lookup"><span data-stu-id="729ee-157">When using this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span> <span data-ttu-id="729ee-158">Dans le cas contraire, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="729ee-158">Otherwise, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="729ee-159">Connectez-vous à l’aide d’une session CIM pour obtenir de meilleures performances lorsque plusieurs opérations sont exécutées sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="729ee-159">Connect using a CIM session for better performance when multiple operations are being performed on the same computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet, CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="729ee-160">-InputObject</span><span class="sxs-lookup"><span data-stu-id="729ee-160">-InputObject</span></span>

<span data-ttu-id="729ee-161">Spécifie un objet d’instance CIM à utiliser comme entrée pour appeler une méthode.</span><span class="sxs-lookup"><span data-stu-id="729ee-161">Specifies a CIM instance object to use as input to invoke a method.</span></span> <span data-ttu-id="729ee-162">Ce paramètre ne peut être utilisé que pour appeler des méthodes d’instance.</span><span class="sxs-lookup"><span data-stu-id="729ee-162">This parameter can only be used to invoke instance methods.</span></span> <span data-ttu-id="729ee-163">Pour appeler des méthodes statiques de classe, utilisez le paramètre **Class** ou le paramètre **CimClass** .</span><span class="sxs-lookup"><span data-stu-id="729ee-163">To invoke class static methods, use the **Class** parameter or the **CimClass** parameter.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="729ee-164">-MethodName</span><span class="sxs-lookup"><span data-stu-id="729ee-164">-MethodName</span></span>

<span data-ttu-id="729ee-165">Spécifie le nom de la méthode CIM à appeler.</span><span class="sxs-lookup"><span data-stu-id="729ee-165">Specifies the name of the CIM method to invoke.</span></span> <span data-ttu-id="729ee-166">Ce paramètre est obligatoire et ne peut ni avoir la valeur Null ni être vide.</span><span class="sxs-lookup"><span data-stu-id="729ee-166">This parameter is mandatory and cannot be null or empty.</span></span> <span data-ttu-id="729ee-167">Pour appeler la méthode statique d’une classe CIM, utilisez le paramètre **className** ou **CimClass** .</span><span class="sxs-lookup"><span data-stu-id="729ee-167">To invoke static method of a CIM class use the **ClassName** or the **CimClass** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Name

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="729ee-168">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="729ee-168">-Namespace</span></span>

<span data-ttu-id="729ee-169">Spécifie l’espace de noms pour l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="729ee-169">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="729ee-170">L’espace de noms par défaut est **root/cimv2**.</span><span class="sxs-lookup"><span data-stu-id="729ee-170">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="729ee-171">Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="729ee-171">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriComputerSet, ResourceUriSessionSet, QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="729ee-172">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="729ee-172">-OperationTimeoutSec</span></span>

<span data-ttu-id="729ee-173">Spécifie la durée pendant laquelle l’applet de commande attend une réponse de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="729ee-173">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="729ee-174">Par défaut, la valeur est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="729ee-174">By default, the value is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="729ee-175">Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion par défaut de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables.</span><span class="sxs-lookup"><span data-stu-id="729ee-175">If the **OperationTimeoutSec** parameter is set to a value less than the default connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable.</span></span>

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

### <span data-ttu-id="729ee-176">-Query</span><span class="sxs-lookup"><span data-stu-id="729ee-176">-Query</span></span>

<span data-ttu-id="729ee-177">Spécifie une requête à exécuter sur le serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="729ee-177">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="729ee-178">Une méthode est appelée sur les instances reçues à la suite de la requête.</span><span class="sxs-lookup"><span data-stu-id="729ee-178">A method is invoked on the instances received as a result of the query.</span></span> <span data-ttu-id="729ee-179">Vous pouvez spécifier le dialecte de requête à l’aide du paramètre **QueryDialect** .</span><span class="sxs-lookup"><span data-stu-id="729ee-179">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="729ee-180">Si la valeur spécifiée contient des guillemets doubles ( `"` ), des guillemets simples ( `'` ) ou une barre oblique inverse ( `\` ), vous devez placer ces caractères dans une séquence d’échappement en les faisant précéder du caractère de barre oblique inverse ( `\` ).</span><span class="sxs-lookup"><span data-stu-id="729ee-180">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="729ee-181">Si la valeur spécifiée utilise l’opérateur LIKE WQL, vous devez placer les caractères suivants dans une séquence d’échappement en les mettant entre crochets ( `[]` ) : percent ( `%` ), trait de soulignement ( `_` ) ou crochet ouvrant ( `[` ).</span><span class="sxs-lookup"><span data-stu-id="729ee-181">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

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

### <span data-ttu-id="729ee-182">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="729ee-182">-QueryDialect</span></span>

<span data-ttu-id="729ee-183">Spécifie le langage de requête utilisé pour le paramètre de requête.</span><span class="sxs-lookup"><span data-stu-id="729ee-183">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="729ee-184">Les valeurs acceptables pour ce paramètre sont les suivantes : **WQL** ou **CQL**.</span><span class="sxs-lookup"><span data-stu-id="729ee-184">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span>

<span data-ttu-id="729ee-185">La valeur par défaut est **WQL**.</span><span class="sxs-lookup"><span data-stu-id="729ee-185">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="729ee-186">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="729ee-186">-ResourceUri</span></span>

<span data-ttu-id="729ee-187">Spécifie l’URI (Uniform Resource Identifier) de la ressource de la classe ou de l’instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="729ee-187">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="729ee-188">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="729ee-188">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="729ee-189">Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="729ee-189">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="729ee-190">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="729ee-190">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="729ee-191">Par défaut, si vous ne spécifiez pas ce paramètre, l’URI de ressource standard DMTF `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` est utilisé et le nom de la classe y est ajouté.</span><span class="sxs-lookup"><span data-stu-id="729ee-191">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="729ee-192">**Resourceuri** peut être utilisé uniquement avec les sessions CIM créées à l’aide du protocole WSMan, ou lors de la spécification du paramètre **ComputerName** , qui crée une session CIM à l’aide de wsman.</span><span class="sxs-lookup"><span data-stu-id="729ee-192">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span>

<span data-ttu-id="729ee-193">Lorsque vous spécifiez ce paramètre sans spécifier le paramètre **ComputerName** , ou lorsque vous spécifiez une session CIM créée à l’aide du protocole DCOM, vous recevez une erreur.</span><span class="sxs-lookup"><span data-stu-id="729ee-193">When you specify this parameter without specifying the **ComputerName** parameter, or when you specify a CIM session created using DCOM protocol, you get an error.</span></span> <span data-ttu-id="729ee-194">Le protocole DCOM ne prend pas en charge le paramètre **resourceuri** .</span><span class="sxs-lookup"><span data-stu-id="729ee-194">The DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="729ee-195">Si le paramètre **resourceuri** et le paramètre **Filter** sont tous deux spécifiés, le paramètre **Filter** est ignoré.</span><span class="sxs-lookup"><span data-stu-id="729ee-195">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="729ee-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="729ee-196">-Confirm</span></span>

<span data-ttu-id="729ee-197">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="729ee-197">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="729ee-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="729ee-198">-WhatIf</span></span>

<span data-ttu-id="729ee-199">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="729ee-199">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="729ee-200">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="729ee-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="729ee-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="729ee-201">CommonParameters</span></span>

<span data-ttu-id="729ee-202">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="729ee-202">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="729ee-203">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="729ee-203">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="729ee-204">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="729ee-204">INPUTS</span></span>

### <span data-ttu-id="729ee-205">Classe CIM</span><span class="sxs-lookup"><span data-stu-id="729ee-205">CIM class</span></span>

<span data-ttu-id="729ee-206">Cette applet de commande accepte une classe CIM comme objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="729ee-206">This cmdlet accepts a CIM class as an input object.</span></span>

### <span data-ttu-id="729ee-207">Instance CIM</span><span class="sxs-lookup"><span data-stu-id="729ee-207">CIM instance</span></span>

<span data-ttu-id="729ee-208">Cette applet de commande accepte une instance CIM comme objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="729ee-208">This cmdlet accepts a CIM instance as an input object.</span></span>

## <span data-ttu-id="729ee-209">SORTIES</span><span class="sxs-lookup"><span data-stu-id="729ee-209">OUTPUTS</span></span>

### <span data-ttu-id="729ee-210">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="729ee-210">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="729ee-211">Cette applet de commande retourne un objet.</span><span class="sxs-lookup"><span data-stu-id="729ee-211">This cmdlet returns an object.</span></span>

## <span data-ttu-id="729ee-212">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="729ee-212">NOTES</span></span>

## <span data-ttu-id="729ee-213">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="729ee-213">RELATED LINKS</span></span>

[<span data-ttu-id="729ee-214">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="729ee-214">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="729ee-215">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="729ee-215">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="729ee-216">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="729ee-216">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="729ee-217">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="729ee-217">New-CimSession</span></span>](New-CimSession.md)

