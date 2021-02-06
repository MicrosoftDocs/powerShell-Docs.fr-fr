---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/set-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-CimInstance
ms.openlocfilehash: 041ef2d5b5541c250b98003099fe58018df155c2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598967"
---
# <span data-ttu-id="5ebe7-102">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="5ebe7-102">Set-CimInstance</span></span>

## <span data-ttu-id="5ebe7-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="5ebe7-103">SYNOPSIS</span></span>
<span data-ttu-id="5ebe7-104">Modifie une instance CIM sur un serveur CIM en appelant la méthode ModifyInstance de la classe CIM.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-104">Modifies a CIM instance on a CIM server by calling the ModifyInstance method of the CIM class.</span></span>

## <span data-ttu-id="5ebe7-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="5ebe7-105">SYNTAX</span></span>

### <span data-ttu-id="5ebe7-106">CimInstanceComputerSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="5ebe7-106">CimInstanceComputerSet (Default)</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="5ebe7-107">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="5ebe7-107">CimInstanceSessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="5ebe7-108">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="5ebe7-108">QuerySessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="5ebe7-109">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="5ebe7-109">QueryComputerSet</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="5ebe7-110">Description</span><span class="sxs-lookup"><span data-stu-id="5ebe7-110">DESCRIPTION</span></span>

<span data-ttu-id="5ebe7-111">Cette applet de commande modifie une instance CIM sur un serveur CIM.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-111">This cmdlet modifies a CIM instance on a CIM server.</span></span>

<span data-ttu-id="5ebe7-112">Si le paramètre **InputObject** n’est pas spécifié, l’applet de commande fonctionne de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ebe7-112">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="5ebe7-113">Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande fonctionne sur le Windows Management Instrumentation local (WMI) à l’aide d’une session com (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="5ebe7-113">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="5ebe7-114">Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande fonctionne sur le serveur CIM spécifié par le paramètre **ComputerName** ou le paramètre **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="5ebe7-114">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="5ebe7-115">Si le paramètre **InputObject** est spécifié, l’applet de commande fonctionne de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ebe7-115">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="5ebe7-116">Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande utilise la session CIM ou le nom de l’ordinateur à partir de l’objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-116">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="5ebe7-117">Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande utilise soit la valeur du paramètre **CimSession** , soit la valeur du paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="5ebe7-117">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="5ebe7-118">Ce n’est pas très courant.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-118">This is not very common.</span></span>

## <span data-ttu-id="5ebe7-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5ebe7-119">EXAMPLES</span></span>

### <span data-ttu-id="5ebe7-120">Exemple 1 : définir l’instance CIM</span><span class="sxs-lookup"><span data-stu-id="5ebe7-120">Example 1: Set the CIM instance</span></span>

<span data-ttu-id="5ebe7-121">Cet exemple affecte à la propriété **VariableValue** la valeur **ABCD** à l’aide du paramètre de **requête** .</span><span class="sxs-lookup"><span data-stu-id="5ebe7-121">This example sets the value of the **VariableValue** property to **abcd** using the **Query** parameter.</span></span> <span data-ttu-id="5ebe7-122">Vous pouvez modifier les instances correspondant à une requête WQL (Windows Management Instrumentation Query Language).</span><span class="sxs-lookup"><span data-stu-id="5ebe7-122">You can modify instances matching a Windows Management Instrumentation Query Language (WQL) query.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="5ebe7-123">Exemple 2 : définir la propriété d’instance CIM à l’aide d’un pipeline</span><span class="sxs-lookup"><span data-stu-id="5ebe7-123">Example 2: Set the CIM instance property using pipeline</span></span>

<span data-ttu-id="5ebe7-124">Cet exemple récupère l’objet d’instance CIM filtré par le paramètre de **requête** à l’aide de l’applet de commande `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="5ebe7-124">This example retrieves the CIM instance object filtered by the **Query** parameter using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="5ebe7-125">L' `Set-CimInstance` applet de commande modifie la valeur de la propriété **VariableValue** en **ABCD**.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-125">The `Set-CimInstance` cmdlet modifies the value of **VariableValue** property to **abcd**.</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' |
  Set-CimInstance -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="5ebe7-126">Exemple 3 : définir la propriété d’instance CIM à l’aide d’un objet d’entrée</span><span class="sxs-lookup"><span data-stu-id="5ebe7-126">Example 3: Set the CIM instance property using input object</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where Name="testvar"'
Set-CimInstance -InputObject $x -Property @{VariableValue="somevalue"} -PassThru
```

<span data-ttu-id="5ebe7-127">Cet exemple récupère les objets d’instance CIM filtrés par le paramètre de requête dans une variable à `$x` l’aide de `Get-CimInstance` , puis passe le contenu de la variable à l’applet de commande `Set-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="5ebe7-127">This example retrieves the CIM instance objects filtered by the Query parameter in to a variable `$x` using `Get-CimInstance`, and then passes the contents of the variable to the `Set-CimInstance` cmdlet.</span></span> <span data-ttu-id="5ebe7-128">`Set-CimInstance` modifie ensuite la propriété **VariableValue** en **SomeValue**.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-128">`Set-CimInstance` then modifies the **VariableValue** property to **somevalue**.</span></span> <span data-ttu-id="5ebe7-129">Étant donné que le paramètre **PassThru** est utilisé, cet exemple retourne un objet d’instance CIM modifié.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-129">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

### <span data-ttu-id="5ebe7-130">Exemple 4 : définir la propriété d’instance CIM</span><span class="sxs-lookup"><span data-stu-id="5ebe7-130">Example 4: Set the CIM instance property</span></span>

<span data-ttu-id="5ebe7-131">Cet exemple récupère l’objet d’instance CIM qui est spécifié dans le paramètre de **requête** dans une variable `$x` à l’aide de l’applet de commande `Get-CimInstance` , puis modifie la valeur de la propriété **VariableValue** de l’objet pour changer.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-131">This example retrieves the CIM instance object that is specified in the **Query** parameter into a variable `$x` using the `Get-CimInstance` cmdlet, and changes the **VariableValue** property value of the object to change.</span></span> <span data-ttu-id="5ebe7-132">L’objet d’instance CIM est ensuite enregistré à l’aide de l’applet de commande `Set-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="5ebe7-132">The CIM instance object is then saved using the `Set-CimInstance` cmdlet.</span></span>
<span data-ttu-id="5ebe7-133">Étant donné que le paramètre **PassThru** est utilisé, cet exemple retourne un objet d’instance CIM modifié.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-133">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where name="testvar"'
$x.VariableValue = "Change"
Set-CimInstance -CimInstance $x -PassThru
```

### <span data-ttu-id="5ebe7-134">Exemple 5 : afficher la liste des instances CIM à modifier à l’aide de WhatIf</span><span class="sxs-lookup"><span data-stu-id="5ebe7-134">Example 5: Show the list of CIM instances to modify using WhatIf</span></span>

<span data-ttu-id="5ebe7-135">Cet exemple utilise le paramètre commun **WhatIf** pour spécifier que la modification ne doit pas être effectuée, mais uniquement en cas de résultat.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-135">This example uses the common parameter **WhatIf** to specify that the modification should not be done, but only output what would happen if it were done.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -WhatIf
```

### <span data-ttu-id="5ebe7-136">Exemple 6 : définir l’instance CIM après la confirmation de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="5ebe7-136">Example 6: Set the CIM instance after confirmation from the user</span></span>

<span data-ttu-id="5ebe7-137">Cet exemple utilise le paramètre commun **Confirm** pour spécifier que la modification doit être effectuée uniquement après confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-137">This example uses the common parameter **Confirm** to specify that the modification should be done only after confirmation from the user.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -Confirm
```

### <span data-ttu-id="5ebe7-138">Exemple 7 : définir l’instance CIM créée</span><span class="sxs-lookup"><span data-stu-id="5ebe7-138">Example 7: Set the created CIM instance</span></span>

<span data-ttu-id="5ebe7-139">Cet exemple crée une instance CIM avec les propriétés spécifiées à l’aide de l’applet de commande `New-CimInstance` et récupère son contenu dans une variable `$x` .</span><span class="sxs-lookup"><span data-stu-id="5ebe7-139">This example creates a CIM instance with the specified properties using the `New-CimInstance` cmdlet, and retrieves its contents in to a variable `$x`.</span></span> <span data-ttu-id="5ebe7-140">La variable est ensuite transmise à l’applet de commande `Set-CimInstance` , qui modifie la valeur de la propriété **VariableValue** en **SomeValue**.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-140">The variable is then passed to the `Set-CimInstance` cmdlet, which modifies the value of **VariableValue** property to **somevalue**.</span></span>
<span data-ttu-id="5ebe7-141">Étant donné que le paramètre **PassThru** est utilisé, cet exemple retourne un objet d’instance CIM modifié.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-141">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";UserName="domain\user"} -Keys Name,UserName -ClientOnly
Set-CimInstance -CimInstance $x -Property @{VariableValue="somevalue"} -PassThru
```

## <span data-ttu-id="5ebe7-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5ebe7-142">PARAMETERS</span></span>

### <span data-ttu-id="5ebe7-143">-CimSession</span><span class="sxs-lookup"><span data-stu-id="5ebe7-143">-CimSession</span></span>

<span data-ttu-id="5ebe7-144">Exécute les applets de commande sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-144">Runs the cmdlets on a remote computer.</span></span> <span data-ttu-id="5ebe7-145">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande `New-CimSession` ou `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="5ebe7-145">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span>

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

### <span data-ttu-id="5ebe7-146">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="5ebe7-146">-ComputerName</span></span>

<span data-ttu-id="5ebe7-147">Spécifie le nom de l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-147">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="5ebe7-148">Vous pouvez spécifier un nom de domaine complet (FQDN) ou un nom NetBIOS.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-148">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="5ebe7-149">Si vous ne spécifiez pas ce paramètre, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="5ebe7-149">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="5ebe7-150">Si vous spécifiez ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-150">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="5ebe7-151">Si plusieurs opérations sont exécutées sur le même ordinateur, la connexion à l’aide d’une session CIM offre de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-151">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

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

### <span data-ttu-id="5ebe7-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="5ebe7-152">-InputObject</span></span>

<span data-ttu-id="5ebe7-153">Spécifie un objet d’instance CIM à utiliser comme entrée.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-153">Specifies a CIM instance object to use as input.</span></span>

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

### <span data-ttu-id="5ebe7-154">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="5ebe7-154">-Namespace</span></span>

<span data-ttu-id="5ebe7-155">Spécifie l’espace de noms pour l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-155">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="5ebe7-156">L’espace de noms par défaut est root/cimv2.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-156">The default namespace is root/cimv2.</span></span> <span data-ttu-id="5ebe7-157">Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-157">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5ebe7-158">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="5ebe7-158">-OperationTimeoutSec</span></span>

<span data-ttu-id="5ebe7-159">Spécifie la durée pendant laquelle l’applet de commande attend une réponse de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-159">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="5ebe7-160">Par défaut, la valeur de ce paramètre est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-160">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="5ebe7-161">Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion fiable de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables, car l’opération sur le serveur expire avant que le client puisse se reconnecter.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-161">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="5ebe7-162">-PassThru</span><span class="sxs-lookup"><span data-stu-id="5ebe7-162">-PassThru</span></span>

<span data-ttu-id="5ebe7-163">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-163">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="5ebe7-164">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-164">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="5ebe7-165">-Propriété</span><span class="sxs-lookup"><span data-stu-id="5ebe7-165">-Property</span></span>

<span data-ttu-id="5ebe7-166">Spécifie les propriétés de l’instance CIM sous la forme d’une table de hachage (à l’aide de paires nom-valeur).</span><span class="sxs-lookup"><span data-stu-id="5ebe7-166">Specifies the properties of the CIM instance as a hash table (using name-value pairs).</span></span> <span data-ttu-id="5ebe7-167">Seules les propriétés spécifiées à l’aide de ce paramètre sont modifiées.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-167">Only the properties specified using this parameter are changed.</span></span> <span data-ttu-id="5ebe7-168">Les autres propriétés de l’instance CIM ne sont pas modifiées.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-168">Other properties of the CIM instance are not changed.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet, QuerySessionSet, QueryComputerSet
Aliases: Arguments

Required: True (QuerySessionSet, QueryComputerSet), False (CimInstanceComputerSet, CimInstanceSessionSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5ebe7-169">-Query</span><span class="sxs-lookup"><span data-stu-id="5ebe7-169">-Query</span></span>

<span data-ttu-id="5ebe7-170">Spécifie une requête à exécuter sur le serveur CIM pour récupérer les instances CIM sur lesquelles exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-170">Specifies a query to run on the CIM server to retrieve CIM instances on which to run the cmdlet.</span></span> <span data-ttu-id="5ebe7-171">Vous pouvez spécifier le dialecte de requête à l’aide du paramètre QueryDialect.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-171">You can specify the query dialect using the QueryDialect parameter.</span></span>

<span data-ttu-id="5ebe7-172">Si la valeur spécifiée contient des guillemets doubles ( `"` ), des guillemets simples ( `'` ) ou une barre oblique inverse ( `\` ), vous devez placer ces caractères dans une séquence d’échappement en les faisant précéder du caractère de barre oblique inverse ( `\` ).</span><span class="sxs-lookup"><span data-stu-id="5ebe7-172">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="5ebe7-173">Si la valeur spécifiée utilise l’opérateur **Like** WQL, vous devez placer les caractères suivants dans une séquence d’échappement en les mettant entre crochets ( `[]` ) : percent ( `%` ), trait de soulignement ( `_` ) ou crochet ouvrant ( `[` ).</span><span class="sxs-lookup"><span data-stu-id="5ebe7-173">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5ebe7-174">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="5ebe7-174">-QueryDialect</span></span>

<span data-ttu-id="5ebe7-175">Spécifie le langage de requête utilisé pour le paramètre de requête.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-175">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="5ebe7-176">Les valeurs acceptables pour ce paramètre sont les suivantes : **WQL** ou **CQL**.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-176">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="5ebe7-177">La valeur par défaut est **WQL**.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-177">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5ebe7-178">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="5ebe7-178">-ResourceUri</span></span>

<span data-ttu-id="5ebe7-179">Spécifie l’URI (Uniform Resource Identifier) de la ressource de la classe ou de l’instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-179">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="5ebe7-180">L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-180">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="5ebe7-181">Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-181">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="5ebe7-182">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5ebe7-182">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="5ebe7-183">Par défaut, si vous ne spécifiez pas ce paramètre, l’URI de ressource standard DMTF `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` est utilisé et le nom de la classe y est ajouté.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-183">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="5ebe7-184">ResourceURI peut être utilisé uniquement avec les sessions CIM créées à l’aide du protocole WSMan, ou lors de la spécification du paramètre ComputerName, qui crée une session CIM à l’aide de WSMan.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-184">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="5ebe7-185">Si vous spécifiez ce paramètre sans spécifier le paramètre ComputerName ou si vous spécifiez une session CIM créée à l’aide du protocole DCOM, vous obtiendrez une erreur, car le protocole DCOM ne prend pas en charge le paramètre ResourceURI.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-185">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="5ebe7-186">Si le paramètre **resourceuri** et le paramètre **Filter** sont tous deux spécifiés, le paramètre **Filter** est ignoré.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-186">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

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

### <span data-ttu-id="5ebe7-187">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5ebe7-187">-Confirm</span></span>

<span data-ttu-id="5ebe7-188">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-188">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5ebe7-189">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5ebe7-189">-WhatIf</span></span>

<span data-ttu-id="5ebe7-190">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-190">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5ebe7-191">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-191">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5ebe7-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5ebe7-192">CommonParameters</span></span>

<span data-ttu-id="5ebe7-193">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5ebe7-194">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="5ebe7-194">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5ebe7-195">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="5ebe7-195">INPUTS</span></span>

### <span data-ttu-id="5ebe7-196">Microsoft.Management.Infrastructure.CimInstance</span><span class="sxs-lookup"><span data-stu-id="5ebe7-196">Microsoft.Management.Infrastructure.CimInstance</span></span>

## <span data-ttu-id="5ebe7-197">SORTIES</span><span class="sxs-lookup"><span data-stu-id="5ebe7-197">OUTPUTS</span></span>

### <span data-ttu-id="5ebe7-198">Microsoft.Management.Infrastructure.CimInstance</span><span class="sxs-lookup"><span data-stu-id="5ebe7-198">Microsoft.Management.Infrastructure.CimInstance</span></span>

<span data-ttu-id="5ebe7-199">Lorsque le paramètre **PassThru** est spécifié, cette applet de commande retourne un objet d’instance CIM modifié.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-199">When the **Passthru** parameter is specified, this cmdlet returns a modified CIM instance object.</span></span>

## <span data-ttu-id="5ebe7-200">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="5ebe7-200">NOTES</span></span>

## <span data-ttu-id="5ebe7-201">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="5ebe7-201">RELATED LINKS</span></span>

[<span data-ttu-id="5ebe7-202">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="5ebe7-202">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="5ebe7-203">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="5ebe7-203">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="5ebe7-204">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="5ebe7-204">Remove-CimInstance</span></span>](remove-ciminstance.md)

