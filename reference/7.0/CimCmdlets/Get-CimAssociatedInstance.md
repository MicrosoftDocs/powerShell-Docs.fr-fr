---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimassociatedinstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimAssociatedInstance
ms.openlocfilehash: d986ba683c091cb8652b077f7f915f399a556002
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205557"
---
# <span data-ttu-id="f2894-103">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="f2894-103">Get-CimAssociatedInstance</span></span>

## <span data-ttu-id="f2894-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f2894-104">SYNOPSIS</span></span>
<span data-ttu-id="f2894-105">Récupère les instances CIM qui sont connectées à une instance CIM spécifique par une association.</span><span class="sxs-lookup"><span data-stu-id="f2894-105">Retrieves the CIM instances that are connected to a specific CIM instance by an association.</span></span>

## <span data-ttu-id="f2894-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f2894-106">SYNTAX</span></span>

### <span data-ttu-id="f2894-107">ComputerSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f2894-107">ComputerSet (Default)</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] [-ComputerName <String[]>] [-KeyOnly] [<CommonParameters>]
```

### <span data-ttu-id="f2894-108">SessionSet</span><span class="sxs-lookup"><span data-stu-id="f2894-108">SessionSet</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] -CimSession <CimSession[]> [-KeyOnly] [<CommonParameters>]
```

## <span data-ttu-id="f2894-109">Description</span><span class="sxs-lookup"><span data-stu-id="f2894-109">DESCRIPTION</span></span>

<span data-ttu-id="f2894-110">L' `Get-CimAssociatedInstance` applet de commande récupère les instances CIM connectées à une instance CIM spécifique, appelée instance source, par une association.</span><span class="sxs-lookup"><span data-stu-id="f2894-110">The `Get-CimAssociatedInstance` cmdlet retrieves the CIM instances connected to a specific CIM instance, called the source instance, by an association.</span></span>

<span data-ttu-id="f2894-111">Dans une association, chaque instance CIM a un rôle nommé et la même instance CIM peut participer à une association dans des rôles différents.</span><span class="sxs-lookup"><span data-stu-id="f2894-111">In an association, each CIM instance has a named role and the same CIM instance can participate in an association in different roles.</span></span>

<span data-ttu-id="f2894-112">Si le paramètre InputObject n’est pas spécifié, l’applet de commande fonctionne de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2894-112">If the InputObject parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="f2894-113">Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande fonctionne sur le Windows Management Instrumentation local (WMI) à l’aide d’une session com (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="f2894-113">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="f2894-114">Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande fonctionne sur le serveur CIM spécifié par le paramètre **ComputerName** ou le paramètre **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="f2894-114">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="f2894-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f2894-115">EXAMPLES</span></span>

### <span data-ttu-id="f2894-116">Exemple 1 : obtenir toutes les instances associées d’une instance spécifique</span><span class="sxs-lookup"><span data-stu-id="f2894-116">Example 1: Get all the associated instances of a specific instance</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1]
```

<span data-ttu-id="f2894-117">Cet ensemble de commandes récupère les instances de la classe nommée Win32_LogicalDisk et stocke les informations dans une variable nommée `$disk` à l’aide de l’applet de commande `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="f2894-117">This set of commands retrieves the instances of the class named Win32_LogicalDisk and stores the information in a variable named `$disk` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="f2894-118">La première instance de disque logique dans la variable est ensuite utilisée comme objet d’entrée pour l’applet de commande `Get-CimAssociatedInstance` afin d’obtenir toutes les instances CIM associées de l’instance CIM spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f2894-118">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated CIM instances of the specified CIM instance.</span></span>

### <span data-ttu-id="f2894-119">Exemple 2 : obtenir toutes les instances associées d’un type spécifique</span><span class="sxs-lookup"><span data-stu-id="f2894-119">Example 2: Get all the associated instances of a specific type</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1] -ResultClass Win32_DiskPartition
```

<span data-ttu-id="f2894-120">Ce jeu de commandes récupère toutes les instances de la classe **Win32_LogicalDisk** et les stocke dans une variable nommée `$disk` .</span><span class="sxs-lookup"><span data-stu-id="f2894-120">This set of commands retrieves all the instances of the **Win32_LogicalDisk** class and stores them in a variable named `$disk`.</span></span> <span data-ttu-id="f2894-121">La première instance de disque logique dans la variable est ensuite utilisée comme objet d’entrée pour l' `Get-CimAssociatedInstance` applet de commande afin d’obtenir toutes les instances associées qui sont associées via la classe d’association spécifiée **Win32_DiskPartition** .</span><span class="sxs-lookup"><span data-stu-id="f2894-121">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated instances that are associated through the specified association class **Win32_DiskPartition** .</span></span>

### <span data-ttu-id="f2894-122">Exemple 3 : obtenir toutes les instances associées par le biais du qualificateur d’une classe spécifique</span><span class="sxs-lookup"><span data-stu-id="f2894-122">Example 3: Get all the associated instances through qualifier of a specific class</span></span>

```powershell
$s = Get-CimInstance -Query "Select * from Win32_Service where name like 'Winmgmt'"
Get-CimClass -ClassName *Service* -Qualifier "Association"
$c.CimClasName
```

```Output
Win32_LoadOrderGroupServiceDependencies
Win32_DependentService
Win32_SystemServices
Win32_LoadOrderGroupServiceMembers
Win32_ServiceSpecificationService
```

```powershell
Get-CimAssociatedInstance -InputObject $s -Association Win32_DependentService
```

<span data-ttu-id="f2894-123">Cet ensemble de commandes récupère les services qui dépendent du service WMI et les stocke dans une variable nommée `$s` .</span><span class="sxs-lookup"><span data-stu-id="f2894-123">This set of commands retrieves the services that depend on WMI service and stores them in a variable named `$s`.</span></span> <span data-ttu-id="f2894-124">Le nom de la classe d’association pour le **Win32_DependentService** est récupéré à l’aide de l' `Get-CimClass` applet de commande en spécifiant **Association** comme qualificateur et est ensuite transmis avec $s à l' `Get-CimAssociatedInstance` applet de commande pour obtenir toutes les instances associées de la classe d’association récupérée.</span><span class="sxs-lookup"><span data-stu-id="f2894-124">The association class name for the **Win32_DependentService** is retrieved using the `Get-CimClass` cmdlet by specifying **Association** as the qualifier and is then passed with $s to the `Get-CimAssociatedInstance` cmdlet to get all the associated instances of the retrieved association class.</span></span>

## <span data-ttu-id="f2894-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f2894-125">PARAMETERS</span></span>

### <span data-ttu-id="f2894-126">-Association</span><span class="sxs-lookup"><span data-stu-id="f2894-126">-Association</span></span>

<span data-ttu-id="f2894-127">Spécifie le nom de la classe d’association.</span><span class="sxs-lookup"><span data-stu-id="f2894-127">Specifies the name of the association class.</span></span> <span data-ttu-id="f2894-128">Si vous ne spécifiez pas ce paramètre, l’applet de commande retourne tous les objets Association existants de tout type.</span><span class="sxs-lookup"><span data-stu-id="f2894-128">If you do not specify this parameter, the cmdlet returns all existing association objects of any type.</span></span>

<span data-ttu-id="f2894-129">Par exemple, si la classe A est associée à la classe B par le biais de deux associations, AB1 et AB2, ce paramètre peut être utilisé pour spécifier le type d’association, AB1 ou AB2.</span><span class="sxs-lookup"><span data-stu-id="f2894-129">For example, if class A is associated with class B through two associations, AB1 and AB2, then this parameter can be used to specify the type of association, either AB1 or AB2.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2894-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="f2894-130">-CimSession</span></span>

<span data-ttu-id="f2894-131">Exécute la commande à l’aide de la session CIM spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f2894-131">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="f2894-132">Entrez une variable qui contient la session CIM ou une commande qui crée ou obtient la session CIM, telle que `New-CimSession` ou `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="f2894-132">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as `New-CimSession` or `Get-CimSession`.</span></span> <span data-ttu-id="f2894-133">Pour plus d’informations, consultez [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="f2894-133">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f2894-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f2894-134">-ComputerName</span></span>

<span data-ttu-id="f2894-135">Spécifie le nom de l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="f2894-135">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="f2894-136">Vous pouvez spécifier un nom de domaine complet (FQDN) ou un nom NetBIOS.</span><span class="sxs-lookup"><span data-stu-id="f2894-136">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="f2894-137">Si vous spécifiez ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan.</span><span class="sxs-lookup"><span data-stu-id="f2894-137">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="f2894-138">Si vous ne spécifiez pas ce paramètre, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="f2894-138">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="f2894-139">Si plusieurs opérations sont exécutées sur le même ordinateur, la connexion à l’aide d’une session CIM offre de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="f2894-139">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2894-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f2894-140">-InputObject</span></span>

<span data-ttu-id="f2894-141">Spécifie l'entrée de cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f2894-141">Specifies the input to this cmdlet.</span></span> <span data-ttu-id="f2894-142">Vous pouvez utiliser ce paramètre ou vous adresser l'entrée à cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f2894-142">You can use this parameter, or you can pipe the input to this cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f2894-143">-Uniquement</span><span class="sxs-lookup"><span data-stu-id="f2894-143">-KeyOnly</span></span>

<span data-ttu-id="f2894-144">Retourne les objets avec uniquement les propriétés de clé remplies.</span><span class="sxs-lookup"><span data-stu-id="f2894-144">Returns objects with only key properties populated.</span></span> <span data-ttu-id="f2894-145">Cela réduit la quantité de données transférées sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="f2894-145">This reduces the amount of data that is transferred over the network.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2894-146">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="f2894-146">-Namespace</span></span>

<span data-ttu-id="f2894-147">Spécifie l’espace de noms pour l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="f2894-147">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="f2894-148">L’espace de noms par défaut est root/cimv2.</span><span class="sxs-lookup"><span data-stu-id="f2894-148">The default namespace is root/cimv2.</span></span>

> [!NOTE]
> <span data-ttu-id="f2894-149">Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="f2894-149">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2894-150">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="f2894-150">-OperationTimeoutSec</span></span>

<span data-ttu-id="f2894-151">Spécifie la durée pendant laquelle l’applet de commande attend une réponse de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f2894-151">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="f2894-152">Par défaut, la valeur de ce paramètre est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="f2894-152">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="f2894-153">Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion fiable de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables, car l’opération sur le serveur expire avant que le client puisse se reconnecter.</span><span class="sxs-lookup"><span data-stu-id="f2894-153">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2894-154">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="f2894-154">-ResourceUri</span></span>

<span data-ttu-id="f2894-155">Spécifie l’URI (Uniform Resource Identifier) de la ressource de la classe ou de l’instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="f2894-155">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="f2894-156">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f2894-156">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="f2894-157">Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="f2894-157">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="f2894-158">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f2894-158">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="f2894-159">Par défaut, si vous ne spécifiez pas ce paramètre, l’URI de ressource standard DMTF `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` est utilisé et le nom de la classe y est ajouté.</span><span class="sxs-lookup"><span data-stu-id="f2894-159">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="f2894-160">**Resourceuri** peut être utilisé uniquement avec les sessions CIM créées à l’aide du protocole WSMan, ou lors de la spécification du paramètre **ComputerName** , qui crée une session CIM à l’aide de wsman.</span><span class="sxs-lookup"><span data-stu-id="f2894-160">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="f2894-161">Si vous spécifiez ce paramètre sans spécifier le paramètre **ComputerName** ou si vous spécifiez une session CIM créée à l’aide du protocole DCOM, vous recevez une erreur, car le protocole DCOM ne prend pas en charge le paramètre **resourceuri** .</span><span class="sxs-lookup"><span data-stu-id="f2894-161">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="f2894-162">Si le paramètre **resourceuri** et le paramètre **Filter** sont tous deux spécifiés, le paramètre **Filter** est ignoré.</span><span class="sxs-lookup"><span data-stu-id="f2894-162">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2894-163">-ResultClassName</span><span class="sxs-lookup"><span data-stu-id="f2894-163">-ResultClassName</span></span>

<span data-ttu-id="f2894-164">Spécifie le nom de la classe des instances associées.</span><span class="sxs-lookup"><span data-stu-id="f2894-164">Specifies the class name of the associated instances.</span></span> <span data-ttu-id="f2894-165">Une instance CIM peut être associée à une ou plusieurs instances CIM.</span><span class="sxs-lookup"><span data-stu-id="f2894-165">A CIM instance can be associated with one or more CIM instances.</span></span> <span data-ttu-id="f2894-166">Toutes les instances CIM associées sont retournées si vous ne spécifiez pas le nom de classe de résultat.</span><span class="sxs-lookup"><span data-stu-id="f2894-166">All associated CIM instances are returned if you do not specify the result class name.</span></span>

<span data-ttu-id="f2894-167">Par défaut, la valeur de ce paramètre est null et toutes les instances CIM associées sont retournées.</span><span class="sxs-lookup"><span data-stu-id="f2894-167">By default, the value of this parameter is null, and all associated CIM instances are returned.</span></span>

<span data-ttu-id="f2894-168">Vous pouvez filtrer les résultats d’association pour qu’ils correspondent à un nom de classe spécifique.</span><span class="sxs-lookup"><span data-stu-id="f2894-168">You can filter the association results to match a specific class name.</span></span> <span data-ttu-id="f2894-169">Le filtrage se produit sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="f2894-169">Filtering happens on the server.</span></span> <span data-ttu-id="f2894-170">Si ce paramètre n’est pas spécifié, `Get-CIMAssociatedInstance` retourne toutes les associations existantes.</span><span class="sxs-lookup"><span data-stu-id="f2894-170">If this parameter is not specified, `Get-CIMAssociatedInstance` returns all existing associations.</span></span> <span data-ttu-id="f2894-171">Par exemple, si la classe A est associée aux classes B, C et D, ce paramètre peut être utilisé pour limiter la sortie à un type spécifique (B, C ou D).</span><span class="sxs-lookup"><span data-stu-id="f2894-171">For example, if class A is associated with classes B, C and D, then this parameter can be used to restrict the output to a specific type (B, C or D).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2894-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2894-172">CommonParameters</span></span>

<span data-ttu-id="f2894-173">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f2894-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2894-174">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f2894-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2894-175">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f2894-175">INPUTS</span></span>

### <span data-ttu-id="f2894-176">Aucun</span><span class="sxs-lookup"><span data-stu-id="f2894-176">None</span></span>

<span data-ttu-id="f2894-177">Cette applet de commande n’accepte aucun objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="f2894-177">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="f2894-178">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f2894-178">OUTPUTS</span></span>

### <span data-ttu-id="f2894-179">System.Object</span><span class="sxs-lookup"><span data-stu-id="f2894-179">System.Object</span></span>

<span data-ttu-id="f2894-180">Cette applet de commande retourne un objet.</span><span class="sxs-lookup"><span data-stu-id="f2894-180">This cmdlet returns an object.</span></span>

## <span data-ttu-id="f2894-181">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f2894-181">NOTES</span></span>

## <span data-ttu-id="f2894-182">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f2894-182">RELATED LINKS</span></span>

[<span data-ttu-id="f2894-183">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="f2894-183">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="f2894-184">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="f2894-184">Get-CimInstance</span></span>](get-ciminstance.md)
