---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimclass?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimClass
ms.openlocfilehash: 551ac39084ff7bf1729618d09cfa521cb6858242
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204350"
---
# <span data-ttu-id="f8def-103">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="f8def-103">Get-CimClass</span></span>

## <span data-ttu-id="f8def-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f8def-104">SYNOPSIS</span></span>
<span data-ttu-id="f8def-105">Obtient une liste de classes CIM dans un espace de noms spécifique.</span><span class="sxs-lookup"><span data-stu-id="f8def-105">Gets a list of CIM classes in a specific namespace.</span></span>

## <span data-ttu-id="f8def-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f8def-106">SYNTAX</span></span>

### <span data-ttu-id="f8def-107">ComputerSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f8def-107">ComputerSet (Default)</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

### <span data-ttu-id="f8def-108">SessionSet</span><span class="sxs-lookup"><span data-stu-id="f8def-108">SessionSet</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

## <span data-ttu-id="f8def-109">Description</span><span class="sxs-lookup"><span data-stu-id="f8def-109">DESCRIPTION</span></span>

<span data-ttu-id="f8def-110">L' `Get-CimClass` applet de commande récupère une liste de classes CIM dans un espace de noms spécifique.</span><span class="sxs-lookup"><span data-stu-id="f8def-110">The `Get-CimClass` cmdlet retrieves a list of CIM classes in a specific namespace.</span></span> <span data-ttu-id="f8def-111">Si aucun nom de classe n’est fourni, l’applet de commande retourne toutes les classes de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f8def-111">If there is no class name supplied, then the cmdlet returns all the classes in the namespace.</span></span> <span data-ttu-id="f8def-112">Contrairement à une instance CIM, les classes CIM ne contiennent pas le nom de session ou d’ordinateur CIM à partir duquel elles sont récupérées.</span><span class="sxs-lookup"><span data-stu-id="f8def-112">Unlike a CIM instance, CIM classes do not contain the CIM session or computer name from which they are retrieved.</span></span>

## <span data-ttu-id="f8def-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f8def-113">EXAMPLES</span></span>

### <span data-ttu-id="f8def-114">Exemple 1 : récupération de toutes les définitions de classe</span><span class="sxs-lookup"><span data-stu-id="f8def-114">Example 1: Get all the class definitions</span></span>

<span data-ttu-id="f8def-115">Cet exemple obtient toutes les définitions de classe sous l’espace de noms **root/cimv2** .</span><span class="sxs-lookup"><span data-stu-id="f8def-115">This example gets all the class definitions under the namespace **root/cimv2** .</span></span>

```powershell
Get-CimClass
```

### <span data-ttu-id="f8def-116">Exemple 2 : obtenir les classes avec un nom spécifique</span><span class="sxs-lookup"><span data-stu-id="f8def-116">Example 2: Get the classes with a specific name</span></span>

<span data-ttu-id="f8def-117">Cet exemple obtient les classes qui contiennent le mot « **Disk** » dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="f8def-117">This example gets the classes that contain the word **disk** in their names.</span></span>

```powershell
Get-CimClass -ClassName *disk*
```

### <span data-ttu-id="f8def-118">Exemple 3 : obtenir les classes avec un nom de méthode spécifique</span><span class="sxs-lookup"><span data-stu-id="f8def-118">Example 3: Get the classes with a specific method name</span></span>

<span data-ttu-id="f8def-119">Cet exemple obtient les classes qui commencent par le nom **Win32** et qui ont un nom de méthode qui commence par **term** .</span><span class="sxs-lookup"><span data-stu-id="f8def-119">This example gets the classes that start with the name **Win32** and have a method name that starts with **Term** .</span></span>

```powershell
Get-CimClass -ClassName Win32* -MethodName Term*
```

### <span data-ttu-id="f8def-120">Exemple 4 : obtenir les classes avec un nom de propriété spécifique</span><span class="sxs-lookup"><span data-stu-id="f8def-120">Example 4: Get the classes with a specific property name</span></span>

<span data-ttu-id="f8def-121">Cet exemple obtient les classes qui commencent par le nom **Win32** et ont une propriété nommée **handle** .</span><span class="sxs-lookup"><span data-stu-id="f8def-121">This example gets the classes that start with the name **Win32** and have a property named **Handle** .</span></span>

```powershell
Get-CimClass -ClassName Win32* -PropertyName Handle
```

### <span data-ttu-id="f8def-122">Exemple 5 : obtenir les classes avec un nom de qualificateur spécifique</span><span class="sxs-lookup"><span data-stu-id="f8def-122">Example 5: Get the classes with a specific qualifier name</span></span>

<span data-ttu-id="f8def-123">Cet exemple obtient les classes qui commencent par le nom **Win32** , qui contiennent le mot **Disk** dans leurs noms et qui disposent de l' **Association** de qualificateurs spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f8def-123">This example gets the classes that start with the name **Win32** , contain the word **Disk** in their names and have the specified qualifier **Association** .</span></span>

```powershell
Get-CimClass -ClassName Win32*Disk* -QualifierName Association
```

### <span data-ttu-id="f8def-124">Exemple 6 : obtenir les définitions de classe à partir d’un espace de noms spécifique</span><span class="sxs-lookup"><span data-stu-id="f8def-124">Example 6: Get the class definitions from a specific namespace</span></span>

<span data-ttu-id="f8def-125">Cet exemple obtient les définitions de classe qui contiennent le mot **net** dans leurs noms à partir de la racine d’espace de noms spécifiée **/standardCimv2** .</span><span class="sxs-lookup"><span data-stu-id="f8def-125">This example gets the class definitions that contain the word **Net** in their names from the specified namespace **root/standardCimv2** .</span></span>

```powershell
Get-CimClass -Namespace root/standardCimv2 -ClassName *Net*
```

### <span data-ttu-id="f8def-126">Exemple 7 : obtenir les définitions de classe à partir d’un serveur distant</span><span class="sxs-lookup"><span data-stu-id="f8def-126">Example 7: Get the class definitions from a remote server</span></span>

<span data-ttu-id="f8def-127">Cet exemple obtient les définitions de classe qui contiennent le mot « **Disk** » dans leurs noms à partir des serveurs distants **SERVEUR01** et **Server02** spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f8def-127">This example gets the class definitions that contain the word **disk** in their names from the specified remote servers **Server01** and **Server02** .</span></span>

```powershell
Get-CimClass -ClassName *disk* -ComputerName Server01, Server02
```

### <span data-ttu-id="f8def-128">Exemple 8 : obtenir les classes à l’aide d’une session CIM</span><span class="sxs-lookup"><span data-stu-id="f8def-128">Example 8: Get the classes by using a CIM session</span></span>

```powershell
$s = New-CimSession -ComputerName Server01, Server02
Get-CimClass -ClassName *disk* -CimSession $s
```

<span data-ttu-id="f8def-129">Ce jeu de commandes crée une session avec plusieurs ordinateurs et le stocke dans une variable `$s` à l’aide de l’applet de commande `New-CimSession` , puis obtient les classes à l’aide de l’applet de commande `Get-CimClass` .</span><span class="sxs-lookup"><span data-stu-id="f8def-129">This set of commands creates a session with multiple computers and stores it into a variable `$s` using the `New-CimSession` cmdlet, and then gets the classes using the `Get-CimClass` cmdlet.</span></span>

## <span data-ttu-id="f8def-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f8def-130">PARAMETERS</span></span>

### <span data-ttu-id="f8def-131">-CimSession</span><span class="sxs-lookup"><span data-stu-id="f8def-131">-CimSession</span></span>

<span data-ttu-id="f8def-132">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f8def-132">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="f8def-133">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande `New-CimSession` ou `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="f8def-133">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span> <span data-ttu-id="f8def-134">La valeur par défaut est la session active sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f8def-134">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="f8def-135">-ClassName</span><span class="sxs-lookup"><span data-stu-id="f8def-135">-ClassName</span></span>

<span data-ttu-id="f8def-136">Spécifie le nom de la classe CIM pour laquelle effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="f8def-136">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="f8def-137">Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des classes, car PowerShell obtient une liste des classes du serveur WMI local pour fournir une liste de noms de classe.</span><span class="sxs-lookup"><span data-stu-id="f8def-137">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="f8def-138">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f8def-138">-ComputerName</span></span>

<span data-ttu-id="f8def-139">Spécifie l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="f8def-139">Specifies the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="f8def-140">Vous pouvez spécifier un nom de domaine complet (FQDN), un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="f8def-140">You can specify a fully qualified domain name (FQDN) a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="f8def-141">Si vous spécifiez ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan.</span><span class="sxs-lookup"><span data-stu-id="f8def-141">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="f8def-142">Si vous ne spécifiez pas ce paramètre, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="f8def-142">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="f8def-143">Si plusieurs opérations sont exécutées sur le même ordinateur, l’utilisation d’une session CIM offre de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="f8def-143">If multiple operations are being performed on the same computer, using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8def-144">-MethodName</span><span class="sxs-lookup"><span data-stu-id="f8def-144">-MethodName</span></span>

<span data-ttu-id="f8def-145">Recherche les classes qui ont une méthode correspondant à ce nom.</span><span class="sxs-lookup"><span data-stu-id="f8def-145">Finds the classes that have a method matching this name.</span></span> <span data-ttu-id="f8def-146">Vous pouvez utiliser des caractères génériques avec ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="f8def-146">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="f8def-147">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="f8def-147">-Namespace</span></span>

<span data-ttu-id="f8def-148">Spécifie l’espace de noms pour l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="f8def-148">Specifies the namespace for CIM operation.</span></span> <span data-ttu-id="f8def-149">L’espace de noms par défaut est **root/cimv2** .</span><span class="sxs-lookup"><span data-stu-id="f8def-149">The default namespace is **root/cimv2** .</span></span> <span data-ttu-id="f8def-150">Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="f8def-150">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

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

### <span data-ttu-id="f8def-151">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="f8def-151">-OperationTimeoutSec</span></span>

<span data-ttu-id="f8def-152">Spécifie la durée pendant laquelle l’applet de commande attend une réponse de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f8def-152">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="f8def-153">Par défaut, la valeur de ce paramètre est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="f8def-153">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="f8def-154">Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion fiable de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables, car l’opération sur le serveur expire avant que le client puisse se reconnecter.</span><span class="sxs-lookup"><span data-stu-id="f8def-154">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="f8def-155">-PropertyName</span><span class="sxs-lookup"><span data-stu-id="f8def-155">-PropertyName</span></span>

<span data-ttu-id="f8def-156">Recherche les classes qui ont une propriété correspondant à ce nom.</span><span class="sxs-lookup"><span data-stu-id="f8def-156">Finds the classes which have a property matching this name.</span></span> <span data-ttu-id="f8def-157">Vous pouvez utiliser des caractères génériques avec ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="f8def-157">You can use wildcard characters with this parameter.</span></span>

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

### <span data-ttu-id="f8def-158">-QualifierName</span><span class="sxs-lookup"><span data-stu-id="f8def-158">-QualifierName</span></span>

<span data-ttu-id="f8def-159">Filtre les classes par nom de qualificateur au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="f8def-159">Filters the classes by class level qualifier name.</span></span> <span data-ttu-id="f8def-160">Vous pouvez utiliser des caractères génériques avec ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="f8def-160">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="f8def-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f8def-161">CommonParameters</span></span>

<span data-ttu-id="f8def-162">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f8def-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f8def-163">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f8def-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f8def-164">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f8def-164">INPUTS</span></span>

### <span data-ttu-id="f8def-165">Aucun</span><span class="sxs-lookup"><span data-stu-id="f8def-165">None</span></span>

<span data-ttu-id="f8def-166">Cette applet de commande n’accepte aucun objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="f8def-166">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="f8def-167">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f8def-167">OUTPUTS</span></span>

### <span data-ttu-id="f8def-168">Microsoft. Management. infrastructure. CimClass</span><span class="sxs-lookup"><span data-stu-id="f8def-168">Microsoft.Management.Infrastructure.CimClass</span></span>

<span data-ttu-id="f8def-169">Cette applet de commande retourne un objet de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="f8def-169">This cmdlet returns a CIM class object.</span></span>

## <span data-ttu-id="f8def-170">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f8def-170">NOTES</span></span>

## <span data-ttu-id="f8def-171">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f8def-171">RELATED LINKS</span></span>

[<span data-ttu-id="f8def-172">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="f8def-172">New-CimSession</span></span>](New-CimSession.md)
