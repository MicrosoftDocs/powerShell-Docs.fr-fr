---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimInstance
ms.openlocfilehash: 5a23aaa59eb10ff35ecefb7365d3294cdb06f781
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597947"
---
# <span data-ttu-id="32c7a-102">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="32c7a-102">Remove-CimInstance</span></span>

## <span data-ttu-id="32c7a-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="32c7a-103">SYNOPSIS</span></span>
<span data-ttu-id="32c7a-104">Supprime une instance CIM d’un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="32c7a-104">Removes a CIM instance from a computer.</span></span>

## <span data-ttu-id="32c7a-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="32c7a-105">SYNTAX</span></span>

### <span data-ttu-id="32c7a-106">CimInstanceComputerSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="32c7a-106">CimInstanceComputerSet (Default)</span></span>

```
Remove-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="32c7a-107">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="32c7a-107">CimInstanceSessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="32c7a-108">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="32c7a-108">QuerySessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="32c7a-109">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="32c7a-109">QueryComputerSet</span></span>

```
Remove-CimInstance [-ComputerName <String[]>] [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="32c7a-110">Description</span><span class="sxs-lookup"><span data-stu-id="32c7a-110">DESCRIPTION</span></span>

<span data-ttu-id="32c7a-111">Cette applet de commande supprime une instance CIM d’un serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="32c7a-111">This cmdlet removes a CIM instance from a CIM server.</span></span> <span data-ttu-id="32c7a-112">Vous pouvez spécifier l’instance CIM à supprimer à l’aide d’un objet d’instance CIM récupéré par l’applet de commande `Get-CimInstance` ou en spécifiant une requête.</span><span class="sxs-lookup"><span data-stu-id="32c7a-112">You can specify the CIM instance to remove by using either a CIM instance object retrieved by the `Get-CimInstance` cmdlet, or by specifying a query.</span></span>

<span data-ttu-id="32c7a-113">Si le paramètre **InputObject** n’est pas spécifié, l’applet de commande fonctionne de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="32c7a-113">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="32c7a-114">Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande fonctionne sur le Windows Management Instrumentation local (WMI) à l’aide d’une session com (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="32c7a-114">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="32c7a-115">Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande fonctionne sur le serveur CIM spécifié par le paramètre **ComputerName** ou le paramètre **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="32c7a-115">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="32c7a-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="32c7a-116">EXAMPLES</span></span>

### <span data-ttu-id="32c7a-117">Exemple 1 : supprimer l’instance CIM</span><span class="sxs-lookup"><span data-stu-id="32c7a-117">Example 1: Remove the CIM instance</span></span>

<span data-ttu-id="32c7a-118">Cet exemple utilise le paramètre de **requête** pour supprimer des instances CIM de la classe nommée **Win32_Environment** qui commencent par la chaîne de caractères **testvar** .</span><span class="sxs-lookup"><span data-stu-id="32c7a-118">This example use the **Query** parameter to remove CIM instances from the class named **Win32_Environment** that start with the character string **testvar** .</span></span>

```powershell
Remove-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"'
```

### <span data-ttu-id="32c7a-119">Exemple 2 : supprimer l’instance CIM à l’aide d’un objet d’instance CIM</span><span class="sxs-lookup"><span data-stu-id="32c7a-119">Example 2: Remove the CIM instance using CIM instance object</span></span>

<span data-ttu-id="32c7a-120">Cet exemple récupère les objets d’instance CIM filtrés par le paramètre de **requête** et les stocke dans une variable nommée `$var` à l’aide de l’applet de commande `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="32c7a-120">This example retrieves the CIM instance objects filtered by the **Query** parameter and stores them in variable named `$var` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="32c7a-121">Le contenu de la variable est ensuite transmis à l' `Remove-CimInstance` applet de commande, qui supprime les instances CIM.</span><span class="sxs-lookup"><span data-stu-id="32c7a-121">The contents of the variable are then passed to the `Remove-CimInstance` cmdlet, which removes the CIM instances.</span></span>

```powershell
notepad.exe
$var = Get-CimInstance -Query 'Select * from Win32_Process where name LIKE "notepad%"'
Remove-CimInstance -InputObject $var
```

## <span data-ttu-id="32c7a-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="32c7a-122">PARAMETERS</span></span>

### <span data-ttu-id="32c7a-123">-CimSession</span><span class="sxs-lookup"><span data-stu-id="32c7a-123">-CimSession</span></span>

<span data-ttu-id="32c7a-124">Exécute la commande à l’aide de la session CIM spécifiée.</span><span class="sxs-lookup"><span data-stu-id="32c7a-124">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="32c7a-125">Entrez une variable qui contient la session CIM ou une commande qui crée ou obtient la session CIM, telle que les `New-CimSession` applets de commande ou `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="32c7a-125">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="32c7a-126">Pour plus d’informations, consultez [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="32c7a-126">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimInstanceSessionSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="32c7a-127">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="32c7a-127">-ComputerName</span></span>

<span data-ttu-id="32c7a-128">Spécifie le nom de l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="32c7a-128">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="32c7a-129">Vous pouvez spécifier un nom de domaine complet (FQDN) ou un nom NetBIOS.</span><span class="sxs-lookup"><span data-stu-id="32c7a-129">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="32c7a-130">Si vous spécifiez ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan.</span><span class="sxs-lookup"><span data-stu-id="32c7a-130">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="32c7a-131">Si vous ne spécifiez pas ce paramètre, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="32c7a-131">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="32c7a-132">Si plusieurs opérations sont exécutées sur le même ordinateur, la connexion à l’aide d’une session CIM offre de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="32c7a-132">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32c7a-133">-InputObject</span><span class="sxs-lookup"><span data-stu-id="32c7a-133">-InputObject</span></span>

<span data-ttu-id="32c7a-134">Spécifie un objet d’instance CIM à supprimer du serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="32c7a-134">Specifies a CIM instance object to be removed from the CIM server.</span></span> <span data-ttu-id="32c7a-135">L’objet passé à l’applet de commande n’est pas modifié, seule l’instance du serveur CIM est supprimée.</span><span class="sxs-lookup"><span data-stu-id="32c7a-135">The object passed to the cmdlet is not changed, only the instance in the CIM server is removed.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="32c7a-136">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="32c7a-136">-Namespace</span></span>

<span data-ttu-id="32c7a-137">Spécifie l’espace de noms pour l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="32c7a-137">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="32c7a-138">L’espace de noms par défaut est **root/cimv2**.</span><span class="sxs-lookup"><span data-stu-id="32c7a-138">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="32c7a-139">Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="32c7a-139">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32c7a-140">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="32c7a-140">-OperationTimeoutSec</span></span>

<span data-ttu-id="32c7a-141">Spécifie la durée pendant laquelle l’applet de commande attend une réponse de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="32c7a-141">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="32c7a-142">Par défaut, la valeur de ce paramètre est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="32c7a-142">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="32c7a-143">Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion fiable de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables, car l’opération sur le serveur expire avant que le client puisse se reconnecter.</span><span class="sxs-lookup"><span data-stu-id="32c7a-143">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="32c7a-144">-Query</span><span class="sxs-lookup"><span data-stu-id="32c7a-144">-Query</span></span>

<span data-ttu-id="32c7a-145">Spécifie une requête à exécuter sur le serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="32c7a-145">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="32c7a-146">Vous pouvez spécifier le dialecte de requête à l’aide du paramètre **QueryDialect** .</span><span class="sxs-lookup"><span data-stu-id="32c7a-146">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="32c7a-147">Si la valeur spécifiée contient des guillemets doubles ( `"` ), des guillemets simples ( `'` ) ou une barre oblique inverse ( `\` ), vous devez placer ces caractères dans une séquence d’échappement en les faisant précéder du caractère de barre oblique inverse ( `\` ).</span><span class="sxs-lookup"><span data-stu-id="32c7a-147">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="32c7a-148">Si la valeur spécifiée utilise l’opérateur LIKE WQL, vous devez placer les caractères suivants dans une séquence d’échappement en les mettant entre crochets ( `[]` ) : percent ( `%` ), trait de soulignement ( `_` ) ou crochet ouvrant ( `[` ).</span><span class="sxs-lookup"><span data-stu-id="32c7a-148">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32c7a-149">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="32c7a-149">-QueryDialect</span></span>

<span data-ttu-id="32c7a-150">Spécifie le langage de requête utilisé pour le paramètre de requête.</span><span class="sxs-lookup"><span data-stu-id="32c7a-150">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="32c7a-151">Les valeurs acceptables pour ce paramètre sont les suivantes : **WQL** ou **CQL**.</span><span class="sxs-lookup"><span data-stu-id="32c7a-151">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="32c7a-152">La valeur par défaut est **WQL**.</span><span class="sxs-lookup"><span data-stu-id="32c7a-152">The default value is **WQL**.</span></span>

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

### <span data-ttu-id="32c7a-153">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="32c7a-153">-ResourceUri</span></span>

<span data-ttu-id="32c7a-154">Spécifie l’URI (Uniform Resource Identifier) de la ressource de la classe ou de l’instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="32c7a-154">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="32c7a-155">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="32c7a-155">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="32c7a-156">Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="32c7a-156">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="32c7a-157">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="32c7a-157">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="32c7a-158">Par défaut, si vous ne spécifiez pas ce paramètre, l’URI de ressource standard DMTF `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` est utilisé et le nom de la classe y est ajouté.</span><span class="sxs-lookup"><span data-stu-id="32c7a-158">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="32c7a-159">ResourceURI peut être utilisé uniquement avec les sessions CIM créées à l’aide du protocole WSMan, ou lors de la spécification du paramètre ComputerName, qui crée une session CIM à l’aide de WSMan.</span><span class="sxs-lookup"><span data-stu-id="32c7a-159">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="32c7a-160">Si vous spécifiez ce paramètre sans spécifier le paramètre ComputerName ou si vous spécifiez une session CIM créée à l’aide du protocole DCOM, vous recevez une erreur, car le protocole DCOM ne prend pas en charge le paramètre ResourceURI.</span><span class="sxs-lookup"><span data-stu-id="32c7a-160">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="32c7a-161">Si le paramètre **resourceuri** et le paramètre **Filter** sont tous deux spécifiés, le paramètre **Filter** est ignoré.</span><span class="sxs-lookup"><span data-stu-id="32c7a-161">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32c7a-162">-Confirm</span><span class="sxs-lookup"><span data-stu-id="32c7a-162">-Confirm</span></span>

<span data-ttu-id="32c7a-163">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="32c7a-163">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="32c7a-164">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="32c7a-164">-WhatIf</span></span>

<span data-ttu-id="32c7a-165">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="32c7a-165">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="32c7a-166">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="32c7a-166">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="32c7a-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32c7a-167">CommonParameters</span></span>

<span data-ttu-id="32c7a-168">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="32c7a-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="32c7a-169">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="32c7a-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="32c7a-170">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="32c7a-170">INPUTS</span></span>

### <span data-ttu-id="32c7a-171">None</span><span class="sxs-lookup"><span data-stu-id="32c7a-171">None</span></span>

<span data-ttu-id="32c7a-172">Cette applet de commande n’accepte aucun objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="32c7a-172">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="32c7a-173">SORTIES</span><span class="sxs-lookup"><span data-stu-id="32c7a-173">OUTPUTS</span></span>

### <span data-ttu-id="32c7a-174">None</span><span class="sxs-lookup"><span data-stu-id="32c7a-174">None</span></span>

<span data-ttu-id="32c7a-175">Cette applet de commande ne produit aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="32c7a-175">This cmdlet produces no outputs.</span></span>

## <span data-ttu-id="32c7a-176">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="32c7a-176">NOTES</span></span>

## <span data-ttu-id="32c7a-177">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="32c7a-177">RELATED LINKS</span></span>

[<span data-ttu-id="32c7a-178">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="32c7a-178">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="32c7a-179">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="32c7a-179">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="32c7a-180">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="32c7a-180">Set-CimInstance</span></span>](Set-CimInstance.md)

