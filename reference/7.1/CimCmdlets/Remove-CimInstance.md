---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-ciminstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimInstance
ms.openlocfilehash: f236956b1da5f9632ff163cbf8a818bf190fd29a
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205449"
---
# <span data-ttu-id="9c914-103">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="9c914-103">Remove-CimInstance</span></span>

## <span data-ttu-id="9c914-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9c914-104">SYNOPSIS</span></span>
<span data-ttu-id="9c914-105">Supprime une instance CIM d’un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9c914-105">Removes a CIM instance from a computer.</span></span>

## <span data-ttu-id="9c914-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9c914-106">SYNTAX</span></span>

### <span data-ttu-id="9c914-107">CimInstanceComputerSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="9c914-107">CimInstanceComputerSet (Default)</span></span>

```
Remove-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9c914-108">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="9c914-108">CimInstanceSessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9c914-109">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="9c914-109">QuerySessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="9c914-110">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="9c914-110">QueryComputerSet</span></span>

```
Remove-CimInstance [-ComputerName <String[]>] [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="9c914-111">Description</span><span class="sxs-lookup"><span data-stu-id="9c914-111">DESCRIPTION</span></span>

<span data-ttu-id="9c914-112">Cette applet de commande supprime une instance CIM d’un serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="9c914-112">This cmdlet removes a CIM instance from a CIM server.</span></span> <span data-ttu-id="9c914-113">Vous pouvez spécifier l’instance CIM à supprimer à l’aide d’un objet d’instance CIM récupéré par l’applet de commande `Get-CimInstance` ou en spécifiant une requête.</span><span class="sxs-lookup"><span data-stu-id="9c914-113">You can specify the CIM instance to remove by using either a CIM instance object retrieved by the `Get-CimInstance` cmdlet, or by specifying a query.</span></span>

<span data-ttu-id="9c914-114">Si le paramètre **InputObject** n’est pas spécifié, l’applet de commande fonctionne de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="9c914-114">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="9c914-115">Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande fonctionne sur le Windows Management Instrumentation local (WMI) à l’aide d’une session com (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="9c914-115">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="9c914-116">Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande fonctionne sur le serveur CIM spécifié par le paramètre **ComputerName** ou le paramètre **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="9c914-116">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="9c914-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9c914-117">EXAMPLES</span></span>

### <span data-ttu-id="9c914-118">Exemple 1 : supprimer l’instance CIM</span><span class="sxs-lookup"><span data-stu-id="9c914-118">Example 1: Remove the CIM instance</span></span>

<span data-ttu-id="9c914-119">Cet exemple utilise le paramètre de **requête** pour supprimer des instances CIM de la classe nommée **Win32_Environment** qui commencent par la chaîne de caractères **testvar** .</span><span class="sxs-lookup"><span data-stu-id="9c914-119">This example use the **Query** parameter to remove CIM instances from the class named **Win32_Environment** that start with the character string **testvar** .</span></span>

```powershell
Remove-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"'
```

### <span data-ttu-id="9c914-120">Exemple 2 : supprimer l’instance CIM à l’aide d’un objet d’instance CIM</span><span class="sxs-lookup"><span data-stu-id="9c914-120">Example 2: Remove the CIM instance using CIM instance object</span></span>

<span data-ttu-id="9c914-121">Cet exemple récupère les objets d’instance CIM filtrés par le paramètre de **requête** et les stocke dans une variable nommée `$var` à l’aide de l’applet de commande `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="9c914-121">This example retrieves the CIM instance objects filtered by the **Query** parameter and stores them in variable named `$var` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="9c914-122">Le contenu de la variable est ensuite transmis à l' `Remove-CimInstance` applet de commande, qui supprime les instances CIM.</span><span class="sxs-lookup"><span data-stu-id="9c914-122">The contents of the variable are then passed to the `Remove-CimInstance` cmdlet, which removes the CIM instances.</span></span>

```powershell
notepad.exe
$var = Get-CimInstance -Query 'Select * from Win32_Process where name LIKE "notepad%"'
Remove-CimInstance -InputObject $var
```

## <span data-ttu-id="9c914-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9c914-123">PARAMETERS</span></span>

### <span data-ttu-id="9c914-124">-CimSession</span><span class="sxs-lookup"><span data-stu-id="9c914-124">-CimSession</span></span>

<span data-ttu-id="9c914-125">Exécute la commande à l’aide de la session CIM spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9c914-125">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="9c914-126">Entrez une variable qui contient la session CIM ou une commande qui crée ou obtient la session CIM, telle que les `New-CimSession` applets de commande ou `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="9c914-126">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="9c914-127">Pour plus d’informations, consultez [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="9c914-127">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

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

### <span data-ttu-id="9c914-128">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="9c914-128">-ComputerName</span></span>

<span data-ttu-id="9c914-129">Spécifie le nom de l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="9c914-129">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="9c914-130">Vous pouvez spécifier un nom de domaine complet (FQDN) ou un nom NetBIOS.</span><span class="sxs-lookup"><span data-stu-id="9c914-130">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="9c914-131">Si vous spécifiez ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan.</span><span class="sxs-lookup"><span data-stu-id="9c914-131">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="9c914-132">Si vous ne spécifiez pas ce paramètre, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="9c914-132">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="9c914-133">Si plusieurs opérations sont exécutées sur le même ordinateur, la connexion à l’aide d’une session CIM offre de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="9c914-133">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

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

### <span data-ttu-id="9c914-134">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9c914-134">-InputObject</span></span>

<span data-ttu-id="9c914-135">Spécifie un objet d’instance CIM à supprimer du serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="9c914-135">Specifies a CIM instance object to be removed from the CIM server.</span></span> <span data-ttu-id="9c914-136">L’objet passé à l’applet de commande n’est pas modifié, seule l’instance du serveur CIM est supprimée.</span><span class="sxs-lookup"><span data-stu-id="9c914-136">The object passed to the cmdlet is not changed, only the instance in the CIM server is removed.</span></span>

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

### <span data-ttu-id="9c914-137">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="9c914-137">-Namespace</span></span>

<span data-ttu-id="9c914-138">Spécifie l’espace de noms pour l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="9c914-138">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="9c914-139">L’espace de noms par défaut est **root/cimv2** .</span><span class="sxs-lookup"><span data-stu-id="9c914-139">The default namespace is **root/cimv2** .</span></span> <span data-ttu-id="9c914-140">Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="9c914-140">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

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

### <span data-ttu-id="9c914-141">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="9c914-141">-OperationTimeoutSec</span></span>

<span data-ttu-id="9c914-142">Spécifie la durée pendant laquelle l’applet de commande attend une réponse de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9c914-142">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="9c914-143">Par défaut, la valeur de ce paramètre est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="9c914-143">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="9c914-144">Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion fiable de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables, car l’opération sur le serveur expire avant que le client puisse se reconnecter.</span><span class="sxs-lookup"><span data-stu-id="9c914-144">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="9c914-145">-Query</span><span class="sxs-lookup"><span data-stu-id="9c914-145">-Query</span></span>

<span data-ttu-id="9c914-146">Spécifie une requête à exécuter sur le serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="9c914-146">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="9c914-147">Vous pouvez spécifier le dialecte de requête à l’aide du paramètre **QueryDialect** .</span><span class="sxs-lookup"><span data-stu-id="9c914-147">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="9c914-148">Si la valeur spécifiée contient des guillemets doubles ( `"` ), des guillemets simples ( `'` ) ou une barre oblique inverse ( `\` ), vous devez placer ces caractères dans une séquence d’échappement en les faisant précéder du caractère de barre oblique inverse ( `\` ).</span><span class="sxs-lookup"><span data-stu-id="9c914-148">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="9c914-149">Si la valeur spécifiée utilise l’opérateur LIKE WQL, vous devez placer les caractères suivants dans une séquence d’échappement en les mettant entre crochets ( `[]` ) : percent ( `%` ), trait de soulignement ( `_` ) ou crochet ouvrant ( `[` ).</span><span class="sxs-lookup"><span data-stu-id="9c914-149">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

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

### <span data-ttu-id="9c914-150">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="9c914-150">-QueryDialect</span></span>

<span data-ttu-id="9c914-151">Spécifie le langage de requête utilisé pour le paramètre de requête.</span><span class="sxs-lookup"><span data-stu-id="9c914-151">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="9c914-152">Les valeurs acceptables pour ce paramètre sont les suivantes : **WQL** ou **CQL** .</span><span class="sxs-lookup"><span data-stu-id="9c914-152">The acceptable values for this parameter are: **WQL** or **CQL** .</span></span> <span data-ttu-id="9c914-153">La valeur par défaut est **WQL** .</span><span class="sxs-lookup"><span data-stu-id="9c914-153">The default value is **WQL** .</span></span>

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

### <span data-ttu-id="9c914-154">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="9c914-154">-ResourceUri</span></span>

<span data-ttu-id="9c914-155">Spécifie l’URI (Uniform Resource Identifier) de la ressource de la classe ou de l’instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="9c914-155">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="9c914-156">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9c914-156">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="9c914-157">Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="9c914-157">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="9c914-158">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9c914-158">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="9c914-159">Par défaut, si vous ne spécifiez pas ce paramètre, l’URI de ressource standard DMTF `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` est utilisé et le nom de la classe y est ajouté.</span><span class="sxs-lookup"><span data-stu-id="9c914-159">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="9c914-160">ResourceURI peut être utilisé uniquement avec les sessions CIM créées à l’aide du protocole WSMan, ou lors de la spécification du paramètre ComputerName, qui crée une session CIM à l’aide de WSMan.</span><span class="sxs-lookup"><span data-stu-id="9c914-160">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="9c914-161">Si vous spécifiez ce paramètre sans spécifier le paramètre ComputerName ou si vous spécifiez une session CIM créée à l’aide du protocole DCOM, vous recevez une erreur, car le protocole DCOM ne prend pas en charge le paramètre ResourceURI.</span><span class="sxs-lookup"><span data-stu-id="9c914-161">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="9c914-162">Si le paramètre **resourceuri** et le paramètre **Filter** sont tous deux spécifiés, le paramètre **Filter** est ignoré.</span><span class="sxs-lookup"><span data-stu-id="9c914-162">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

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

### <span data-ttu-id="9c914-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9c914-163">-Confirm</span></span>

<span data-ttu-id="9c914-164">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9c914-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9c914-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9c914-165">-WhatIf</span></span>

<span data-ttu-id="9c914-166">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9c914-166">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9c914-167">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="9c914-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9c914-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9c914-168">CommonParameters</span></span>

<span data-ttu-id="9c914-169">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9c914-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9c914-170">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9c914-170">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9c914-171">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9c914-171">INPUTS</span></span>

### <span data-ttu-id="9c914-172">Aucun</span><span class="sxs-lookup"><span data-stu-id="9c914-172">None</span></span>

<span data-ttu-id="9c914-173">Cette applet de commande n’accepte aucun objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="9c914-173">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="9c914-174">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9c914-174">OUTPUTS</span></span>

### <span data-ttu-id="9c914-175">Aucun</span><span class="sxs-lookup"><span data-stu-id="9c914-175">None</span></span>

<span data-ttu-id="9c914-176">Cette applet de commande ne produit aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="9c914-176">This cmdlet produces no outputs.</span></span>

## <span data-ttu-id="9c914-177">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9c914-177">NOTES</span></span>

## <span data-ttu-id="9c914-178">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9c914-178">RELATED LINKS</span></span>

[<span data-ttu-id="9c914-179">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="9c914-179">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="9c914-180">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="9c914-180">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="9c914-181">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="9c914-181">Set-CimInstance</span></span>](Set-CimInstance.md)

