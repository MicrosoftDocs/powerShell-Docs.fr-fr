---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-ciminstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimInstance
ms.openlocfilehash: d6eab5d6fcf1c4d983f2502465d76ad5df1db9dd
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205345"
---
# <span data-ttu-id="494bb-103">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="494bb-103">New-CimInstance</span></span>

## <span data-ttu-id="494bb-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="494bb-104">SYNOPSIS</span></span>
<span data-ttu-id="494bb-105">Crée une instance CIM.</span><span class="sxs-lookup"><span data-stu-id="494bb-105">Creates a CIM instance.</span></span>

## <span data-ttu-id="494bb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="494bb-106">SYNTAX</span></span>

### <span data-ttu-id="494bb-107">ClassNameComputerSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="494bb-107">ClassNameComputerSet (Default)</span></span>

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="494bb-108">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="494bb-108">ClassNameSessionSet</span></span>

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="494bb-109">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="494bb-109">ResourceUriSessionSet</span></span>

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="494bb-110">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="494bb-110">ResourceUriComputerSet</span></span>

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="494bb-111">CimClassSessionSet</span><span class="sxs-lookup"><span data-stu-id="494bb-111">CimClassSessionSet</span></span>

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="494bb-112">CimClassComputerSet</span><span class="sxs-lookup"><span data-stu-id="494bb-112">CimClassComputerSet</span></span>

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="494bb-113">Description</span><span class="sxs-lookup"><span data-stu-id="494bb-113">DESCRIPTION</span></span>

<span data-ttu-id="494bb-114">L' `New-CimInstance` applet de commande crée une instance d’une classe CIM basée sur la définition de classe sur l’ordinateur local ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="494bb-114">The `New-CimInstance` cmdlet creates an instance of a CIM class based on the class definition on either the local computer or a remote computer.</span></span> <span data-ttu-id="494bb-115">Par défaut, l' `New-CimInstance` applet de commande crée une instance sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="494bb-115">By default, the `New-CimInstance` cmdlet creates an instance on the local computer.</span></span>

## <span data-ttu-id="494bb-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="494bb-116">EXAMPLES</span></span>

### <span data-ttu-id="494bb-117">Exemple 1 : créer une instance d’une classe CIM</span><span class="sxs-lookup"><span data-stu-id="494bb-117">Example 1: Create an instance of a CIM class</span></span>

<span data-ttu-id="494bb-118">Cet exemple crée une instance d’une classe CIM nommée win32_environment dans l’espace de noms root/cimv2 sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="494bb-118">This example creates an instance of a CIM Class named win32_environment in the root/cimv2 namespace on the computer.</span></span>

```powershell
New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";VariableValue="testvalue";UserName="domain\user"}
```

<span data-ttu-id="494bb-119">Aucune validation côté client n’est effectuée si la classe n’existe pas, si les propriétés sont incorrectes ou si le serveur rejette l’appel.</span><span class="sxs-lookup"><span data-stu-id="494bb-119">No client side validation is performed if the class does not exist, the properties are wrong, or if the server rejects the call.</span></span> <span data-ttu-id="494bb-120">Si l’instance est créée avec succès, l’applet de commande génère l’instance nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="494bb-120">If the instance is created successfully, the cmdlet outputs the newly created instance.</span></span>

### <span data-ttu-id="494bb-121">Exemple 2 : créer une instance d’une classe CIM à l’aide d’un schéma de classe</span><span class="sxs-lookup"><span data-stu-id="494bb-121">Example 2: Create an instance of a CIM class using a class schema</span></span>

<span data-ttu-id="494bb-122">Cet exemple récupère un objet de classe CIM et le stocke dans une variable nommée `$class` .</span><span class="sxs-lookup"><span data-stu-id="494bb-122">This example retrieves a CIM class object and stores it in a variable named `$class`.</span></span> <span data-ttu-id="494bb-123">Le contenu de la variable est ensuite transmis à l' `New-CimInstance` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="494bb-123">The contents of the variable are then passed to the `New-CimInstance` cmdlet.</span></span>

```powershell
$class = Get-CimClass -ClassName Win32_Environment
New-CimInstance -CimClass $class -Property @{Name="testvar";VariableValue="testvalue";UserName="Contoso\User1"}
```

### <span data-ttu-id="494bb-124">Exemple 3 : créer une instance dynamique sur le client</span><span class="sxs-lookup"><span data-stu-id="494bb-124">Example 3: Create a dynamic instance on the client</span></span>

<span data-ttu-id="494bb-125">Cet exemple crée une instance dynamique d’une classe CIM nommée **Win32_Process** sur l’ordinateur client sans obtenir l’instance du serveur.</span><span class="sxs-lookup"><span data-stu-id="494bb-125">This example creates a dynamic instance of a CIM class named **Win32_Process** on the client computer without getting the instance from the server.</span></span> <span data-ttu-id="494bb-126">La nouvelle instance est stockée dans la variable `$a` .</span><span class="sxs-lookup"><span data-stu-id="494bb-126">The new instance is stored in the variable `$a`.</span></span> <span data-ttu-id="494bb-127">Cette instance dynamique peut être utilisée pour effectuer des opérations si l’instance avec cette clé existe sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="494bb-127">This dynamic instance can be used to perform operations if the instance with this key exists on the server.</span></span>

```powershell
$a = New-CimInstance -ClassName Win32_Process -Property @{Handle=0} -Key Handle -ClientOnly
Get-CimInstance -CimInstance $a
Invoke-CimMethod -CimInstance $a -MethodName GetOwner
```

```Output
ProcessId Name                HandleCount WorkingSetSize VirtualSize
--------- ----                ----------- -------------- -----------
0         System Idle Process 0           8192           8192

Domain         :
ReturnValue    : 2
User           :
PSComputerName :
```

<span data-ttu-id="494bb-128">L' `Get-CimInstance` applet de commande récupère ensuite une instance unique particulière.</span><span class="sxs-lookup"><span data-stu-id="494bb-128">The `Get-CimInstance` cmdlet then retrieves a particular single instance.</span></span> <span data-ttu-id="494bb-129">L' `Invoke-CimMethod` applet de commande appelle la méthode **GetOwner** sur l’instance récupérée.</span><span class="sxs-lookup"><span data-stu-id="494bb-129">The `Invoke-CimMethod` cmdlet calls the **GetOwner** method on the retrieved instance.</span></span>

### <span data-ttu-id="494bb-130">Exemple 4 : créer une instance pour une classe CIM d’un espace de noms spécifique</span><span class="sxs-lookup"><span data-stu-id="494bb-130">Example 4: Create an instance for a CIM class of a specific namespace</span></span>

<span data-ttu-id="494bb-131">Cet exemple obtient une instance d’une classe CIM nommée **MSFT_Something** dans la racine de l’espace de noms **/quelque part** et le stocke dans une variable nommée `$class` .</span><span class="sxs-lookup"><span data-stu-id="494bb-131">This example gets an instance of a CIM class named **MSFT_Something** in the namespace **root/somewhere** and stores it in a variable named `$class`.</span></span> <span data-ttu-id="494bb-132">La variable est transmise à l' `New-CimInstance` applet de commande pour créer une nouvelle instance CIM et effectuer des validations côté client sur la nouvelle instance.</span><span class="sxs-lookup"><span data-stu-id="494bb-132">The variable is passed to the `New-CimInstance` cmdlet to create a new CIM instance and perform client side validations on the new instance.</span></span>

```powershell
$class = Get-CimClass -ClassName MSFT_Something -Namespace root/somewhere
New-CimInstance -CimClass $class -Property @{"Prop1"=1;"Prop2"="value"} -ClientOnly
```

<span data-ttu-id="494bb-133">Dans cet exemple, l’utilisation du paramètre **CimClass** à la place du paramètre **className** confirme que **Prop1** et **Prop2** existent réellement et que les clés sont marquées correctement.</span><span class="sxs-lookup"><span data-stu-id="494bb-133">In this example, using the **CimClass** parameter instead of the **ClassName** parameter validates that **Prop1** and **Prop2** actually exist and that the keys are marked correctly.</span></span>

<span data-ttu-id="494bb-134">Vous ne pouvez pas utiliser le paramètre **ComputerName** ou **CimSession** avec le paramètre **ClientOnly** .</span><span class="sxs-lookup"><span data-stu-id="494bb-134">You cannot use the **ComputerName** or **CimSession** parameter with the **ClientOnly** parameter.</span></span>

## <span data-ttu-id="494bb-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="494bb-135">PARAMETERS</span></span>

### <span data-ttu-id="494bb-136">-CimClass</span><span class="sxs-lookup"><span data-stu-id="494bb-136">-CimClass</span></span>

<span data-ttu-id="494bb-137">Spécifie un objet de classe CIM qui représente le type de l’instance.</span><span class="sxs-lookup"><span data-stu-id="494bb-137">Specifies a CIM class object that represents the type of the instance.</span></span> <span data-ttu-id="494bb-138">Utilisez l' `Get-CimClass` applet de commande pour récupérer la déclaration de classe à partir d’un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="494bb-138">Use the `Get-CimClass` cmdlet to retrieve the class declaration from a computer.</span></span> <span data-ttu-id="494bb-139">L’utilisation de ce paramètre permet d’améliorer les validations de schéma côté client.</span><span class="sxs-lookup"><span data-stu-id="494bb-139">Using this parameter results in better client side schema validations.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassSessionSet, CimClassComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="494bb-140">-CimSession</span><span class="sxs-lookup"><span data-stu-id="494bb-140">-CimSession</span></span>

<span data-ttu-id="494bb-141">Exécute la commande à l’aide de la session CIM spécifiée.</span><span class="sxs-lookup"><span data-stu-id="494bb-141">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="494bb-142">Entrez une variable qui contient la session CIM ou une commande qui crée ou obtient la session CIM, telle que les `New-CimSession` applets de commande ou `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="494bb-142">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="494bb-143">Pour plus d’informations, consultez [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="494bb-143">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, ResourceUriSessionSet, CimClassSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="494bb-144">-ClassName</span><span class="sxs-lookup"><span data-stu-id="494bb-144">-ClassName</span></span>

<span data-ttu-id="494bb-145">Spécifie le nom de la classe CIM dont l’opération crée une instance.</span><span class="sxs-lookup"><span data-stu-id="494bb-145">Specifies the name of the CIM class of which the operation creates an instance.</span></span> <span data-ttu-id="494bb-146">Remarque : vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des classes, car PowerShell obtient une liste des classes du serveur WMI local pour fournir une liste de noms de classe.</span><span class="sxs-lookup"><span data-stu-id="494bb-146">NOTE: You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

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

### <span data-ttu-id="494bb-147">-ClientOnly</span><span class="sxs-lookup"><span data-stu-id="494bb-147">-ClientOnly</span></span>

<span data-ttu-id="494bb-148">Indique que l’instance est créée uniquement dans PowerShell sans passer par le serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="494bb-148">Indicates that the instance is only created in PowerShell without going to the CIM server.</span></span> <span data-ttu-id="494bb-149">Vous pouvez utiliser ce paramètre pour créer une instance CIM en mémoire à utiliser dans les opérations PowerShell suivantes.</span><span class="sxs-lookup"><span data-stu-id="494bb-149">You can use this parameter to create an in-memory CIM instance for use in subsequent PowerShell operations.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, CimClassSessionSet, CimClassComputerSet
Aliases: Local

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="494bb-150">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="494bb-150">-ComputerName</span></span>

<span data-ttu-id="494bb-151">Spécifie le nom de l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="494bb-151">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="494bb-152">Vous pouvez spécifier un nom de domaine complet (FQDN), un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="494bb-152">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="494bb-153">Si vous spécifiez ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WSMan.</span><span class="sxs-lookup"><span data-stu-id="494bb-153">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WSMan protocol.</span></span>

<span data-ttu-id="494bb-154">Si vous ne spécifiez pas ce paramètre, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="494bb-154">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="494bb-155">Si plusieurs opérations sont exécutées sur le même ordinateur, la connexion à l’aide d’une session CIM offre de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="494bb-155">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="494bb-156">-Clé</span><span class="sxs-lookup"><span data-stu-id="494bb-156">-Key</span></span>

<span data-ttu-id="494bb-157">Spécifie les propriétés utilisées comme clés.</span><span class="sxs-lookup"><span data-stu-id="494bb-157">Specifies the properties that are used as keys.</span></span> <span data-ttu-id="494bb-158">**CimSession** et **ComputerName** ne peuvent pas être utilisés quand **Key** est spécifié.</span><span class="sxs-lookup"><span data-stu-id="494bb-158">**CimSession** and **ComputerName** cannot be used when **Key** is specified.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="494bb-159">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="494bb-159">-Namespace</span></span>

<span data-ttu-id="494bb-160">Spécifie l’espace de noms de la classe pour la nouvelle instance.</span><span class="sxs-lookup"><span data-stu-id="494bb-160">Specifies the namespace of the class for the new instance.</span></span> <span data-ttu-id="494bb-161">L’espace de noms par défaut est **root/cimv2** .</span><span class="sxs-lookup"><span data-stu-id="494bb-161">The default namespace is **root/cimv2** .</span></span>
<span data-ttu-id="494bb-162">Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="494bb-162">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="494bb-163">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="494bb-163">-OperationTimeoutSec</span></span>

<span data-ttu-id="494bb-164">Spécifie la durée pendant laquelle l’applet de commande attend une réponse du serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="494bb-164">Specifies the amount of time that the cmdlet waits for a response from the CIM server.</span></span> <span data-ttu-id="494bb-165">Par défaut, la valeur de ce paramètre est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="494bb-165">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span> <span data-ttu-id="494bb-166">Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion fiable de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables, car l’opération sur le serveur expire avant que le client puisse se reconnecter.</span><span class="sxs-lookup"><span data-stu-id="494bb-166">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="494bb-167">-Propriété</span><span class="sxs-lookup"><span data-stu-id="494bb-167">-Property</span></span>

<span data-ttu-id="494bb-168">Spécifie les propriétés de l’instance CIM à l’aide d’une table de hachage (paires nom-valeur).</span><span class="sxs-lookup"><span data-stu-id="494bb-168">Specifies the properties of the CIM instance using a hash table (name-value pairs).</span></span>

<span data-ttu-id="494bb-169">Si vous spécifiez le paramètre **CimClass** , l' `New-CimInstance` applet de commande effectue une validation de propriété sur le client pour s’assurer que les propriétés spécifiées sont cohérentes avec la déclaration de classe sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="494bb-169">If you specify the **CimClass** parameter, then the `New-CimInstance` cmdlet performs a property validation on the client to make sure that the properties specified are consistent with the class declaration on the server.</span></span> <span data-ttu-id="494bb-170">Si le paramètre **CimClass** n’est pas spécifié, la validation de la propriété est effectuée sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="494bb-170">If the **CimClass** parameter is not specified, then the property validation is done on the server.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases: Arguments

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="494bb-171">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="494bb-171">-ResourceUri</span></span>

<span data-ttu-id="494bb-172">Spécifie l’URI (Uniform Resource Identifier) de la ressource de la classe ou de l’instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="494bb-172">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="494bb-173">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="494bb-173">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="494bb-174">Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="494bb-174">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="494bb-175">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="494bb-175">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="494bb-176">Par défaut, si vous ne spécifiez pas ce paramètre, l’URI de ressource standard DMTF `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` est utilisé et le nom de la classe y est ajouté.</span><span class="sxs-lookup"><span data-stu-id="494bb-176">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="494bb-177">**Resourceuri** peut être utilisé uniquement avec les sessions CIM créées à l’aide du protocole WSMan, ou lors de la spécification du paramètre **ComputerName** , qui crée une session CIM à l’aide de wsman.</span><span class="sxs-lookup"><span data-stu-id="494bb-177">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="494bb-178">Si vous spécifiez ce paramètre sans spécifier le paramètre **ComputerName** ou si vous spécifiez une session CIM créée à l’aide du protocole DCOM, vous obtiendrez une erreur, car le protocole DCOM ne prend pas en charge le paramètre **resourceuri** .</span><span class="sxs-lookup"><span data-stu-id="494bb-178">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="494bb-179">Si le paramètre **resourceuri** et le paramètre **Filter** sont tous deux spécifiés, le paramètre **Filter** est ignoré.</span><span class="sxs-lookup"><span data-stu-id="494bb-179">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="494bb-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="494bb-180">-Confirm</span></span>

<span data-ttu-id="494bb-181">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="494bb-181">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="494bb-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="494bb-182">-WhatIf</span></span>

<span data-ttu-id="494bb-183">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="494bb-183">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="494bb-184">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="494bb-184">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="494bb-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="494bb-185">CommonParameters</span></span>

<span data-ttu-id="494bb-186">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="494bb-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="494bb-187">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="494bb-187">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="494bb-188">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="494bb-188">INPUTS</span></span>

### <span data-ttu-id="494bb-189">Aucun</span><span class="sxs-lookup"><span data-stu-id="494bb-189">None</span></span>

<span data-ttu-id="494bb-190">Cette applet de commande n’accepte aucun objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="494bb-190">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="494bb-191">SORTIES</span><span class="sxs-lookup"><span data-stu-id="494bb-191">OUTPUTS</span></span>

### <span data-ttu-id="494bb-192">System.Object</span><span class="sxs-lookup"><span data-stu-id="494bb-192">System.Object</span></span>

<span data-ttu-id="494bb-193">Cette applet de commande retourne un objet qui contient les informations de l’instance CIM.</span><span class="sxs-lookup"><span data-stu-id="494bb-193">This cmdlet returns an object that contains the CIM instance information.</span></span>

## <span data-ttu-id="494bb-194">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="494bb-194">NOTES</span></span>

## <span data-ttu-id="494bb-195">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="494bb-195">RELATED LINKS</span></span>

[<span data-ttu-id="494bb-196">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="494bb-196">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="494bb-197">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="494bb-197">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="494bb-198">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="494bb-198">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="494bb-199">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="494bb-199">Set-CimInstance</span></span>](Set-CimInstance.md)
