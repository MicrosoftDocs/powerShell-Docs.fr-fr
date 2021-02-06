---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimclass?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimClass
ms.openlocfilehash: 483b4b5b940a9effca99e942b86a967de5d26d68
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603659"
---
# <span data-ttu-id="6acf1-102">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="6acf1-102">Get-CimClass</span></span>

## <span data-ttu-id="6acf1-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6acf1-103">SYNOPSIS</span></span>
<span data-ttu-id="6acf1-104">Obtient une liste de classes CIM dans un espace de noms spécifique.</span><span class="sxs-lookup"><span data-stu-id="6acf1-104">Gets a list of CIM classes in a specific namespace.</span></span>

## <span data-ttu-id="6acf1-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="6acf1-105">SYNTAX</span></span>

### <span data-ttu-id="6acf1-106">ComputerSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="6acf1-106">ComputerSet (Default)</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

### <span data-ttu-id="6acf1-107">SessionSet</span><span class="sxs-lookup"><span data-stu-id="6acf1-107">SessionSet</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

## <span data-ttu-id="6acf1-108">Description</span><span class="sxs-lookup"><span data-stu-id="6acf1-108">DESCRIPTION</span></span>

<span data-ttu-id="6acf1-109">L' `Get-CimClass` applet de commande récupère une liste de classes CIM dans un espace de noms spécifique.</span><span class="sxs-lookup"><span data-stu-id="6acf1-109">The `Get-CimClass` cmdlet retrieves a list of CIM classes in a specific namespace.</span></span> <span data-ttu-id="6acf1-110">Si aucun nom de classe n’est fourni, l’applet de commande retourne toutes les classes de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="6acf1-110">If there is no class name supplied, then the cmdlet returns all the classes in the namespace.</span></span> <span data-ttu-id="6acf1-111">Contrairement à une instance CIM, les classes CIM ne contiennent pas le nom de session ou d’ordinateur CIM à partir duquel elles sont récupérées.</span><span class="sxs-lookup"><span data-stu-id="6acf1-111">Unlike a CIM instance, CIM classes do not contain the CIM session or computer name from which they are retrieved.</span></span>

## <span data-ttu-id="6acf1-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6acf1-112">EXAMPLES</span></span>

### <span data-ttu-id="6acf1-113">Exemple 1 : récupération de toutes les définitions de classe</span><span class="sxs-lookup"><span data-stu-id="6acf1-113">Example 1: Get all the class definitions</span></span>

<span data-ttu-id="6acf1-114">Cet exemple obtient toutes les définitions de classe sous l’espace de noms **root/cimv2**.</span><span class="sxs-lookup"><span data-stu-id="6acf1-114">This example gets all the class definitions under the namespace **root/cimv2**.</span></span>

```powershell
Get-CimClass
```

### <span data-ttu-id="6acf1-115">Exemple 2 : obtenir les classes avec un nom spécifique</span><span class="sxs-lookup"><span data-stu-id="6acf1-115">Example 2: Get the classes with a specific name</span></span>

<span data-ttu-id="6acf1-116">Cet exemple obtient les classes qui contiennent le mot « **Disk** » dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="6acf1-116">This example gets the classes that contain the word **disk** in their names.</span></span>

```powershell
Get-CimClass -ClassName *disk*
```

### <span data-ttu-id="6acf1-117">Exemple 3 : obtenir les classes avec un nom de méthode spécifique</span><span class="sxs-lookup"><span data-stu-id="6acf1-117">Example 3: Get the classes with a specific method name</span></span>

<span data-ttu-id="6acf1-118">Cet exemple obtient les classes qui commencent par le nom **Win32** et qui ont un nom de méthode qui commence par **term**.</span><span class="sxs-lookup"><span data-stu-id="6acf1-118">This example gets the classes that start with the name **Win32** and have a method name that starts with **Term**.</span></span>

```powershell
Get-CimClass -ClassName Win32* -MethodName Term*
```

### <span data-ttu-id="6acf1-119">Exemple 4 : obtenir les classes avec un nom de propriété spécifique</span><span class="sxs-lookup"><span data-stu-id="6acf1-119">Example 4: Get the classes with a specific property name</span></span>

<span data-ttu-id="6acf1-120">Cet exemple obtient les classes qui commencent par le nom **Win32** et ont une propriété nommée **handle**.</span><span class="sxs-lookup"><span data-stu-id="6acf1-120">This example gets the classes that start with the name **Win32** and have a property named **Handle**.</span></span>

```powershell
Get-CimClass -ClassName Win32* -PropertyName Handle
```

### <span data-ttu-id="6acf1-121">Exemple 5 : obtenir les classes avec un nom de qualificateur spécifique</span><span class="sxs-lookup"><span data-stu-id="6acf1-121">Example 5: Get the classes with a specific qualifier name</span></span>

<span data-ttu-id="6acf1-122">Cet exemple obtient les classes qui commencent par le nom **Win32**, qui contiennent le mot **Disk** dans leurs noms et qui disposent de l' **Association** de qualificateurs spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6acf1-122">This example gets the classes that start with the name **Win32**, contain the word **Disk** in their names and have the specified qualifier **Association**.</span></span>

```powershell
Get-CimClass -ClassName Win32*Disk* -QualifierName Association
```

### <span data-ttu-id="6acf1-123">Exemple 6 : obtenir les définitions de classe à partir d’un espace de noms spécifique</span><span class="sxs-lookup"><span data-stu-id="6acf1-123">Example 6: Get the class definitions from a specific namespace</span></span>

<span data-ttu-id="6acf1-124">Cet exemple obtient les définitions de classe qui contiennent le mot **net** dans leurs noms à partir de la racine d’espace de noms spécifiée **/standardCimv2**.</span><span class="sxs-lookup"><span data-stu-id="6acf1-124">This example gets the class definitions that contain the word **Net** in their names from the specified namespace **root/standardCimv2**.</span></span>

```powershell
Get-CimClass -Namespace root/standardCimv2 -ClassName *Net*
```

### <span data-ttu-id="6acf1-125">Exemple 7 : obtenir les définitions de classe à partir d’un serveur distant</span><span class="sxs-lookup"><span data-stu-id="6acf1-125">Example 7: Get the class definitions from a remote server</span></span>

<span data-ttu-id="6acf1-126">Cet exemple obtient les définitions de classe qui contiennent le mot « **Disk** » dans leurs noms à partir des serveurs distants **SERVEUR01** et **Server02** spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6acf1-126">This example gets the class definitions that contain the word **disk** in their names from the specified remote servers **Server01** and **Server02**.</span></span>

```powershell
Get-CimClass -ClassName *disk* -ComputerName Server01, Server02
```

### <span data-ttu-id="6acf1-127">Exemple 8 : obtenir les classes à l’aide d’une session CIM</span><span class="sxs-lookup"><span data-stu-id="6acf1-127">Example 8: Get the classes by using a CIM session</span></span>

```powershell
$s = New-CimSession -ComputerName Server01, Server02
Get-CimClass -ClassName *disk* -CimSession $s
```

<span data-ttu-id="6acf1-128">Ce jeu de commandes crée une session avec plusieurs ordinateurs et le stocke dans une variable `$s` à l’aide de l’applet de commande `New-CimSession` , puis obtient les classes à l’aide de l’applet de commande `Get-CimClass` .</span><span class="sxs-lookup"><span data-stu-id="6acf1-128">This set of commands creates a session with multiple computers and stores it into a variable `$s` using the `New-CimSession` cmdlet, and then gets the classes using the `Get-CimClass` cmdlet.</span></span>

## <span data-ttu-id="6acf1-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6acf1-129">PARAMETERS</span></span>

### <span data-ttu-id="6acf1-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="6acf1-130">-CimSession</span></span>

<span data-ttu-id="6acf1-131">Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="6acf1-131">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="6acf1-132">Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande `New-CimSession` ou `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="6acf1-132">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span> <span data-ttu-id="6acf1-133">La valeur par défaut est la session active sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6acf1-133">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="6acf1-134">-ClassName</span><span class="sxs-lookup"><span data-stu-id="6acf1-134">-ClassName</span></span>

<span data-ttu-id="6acf1-135">Spécifie le nom de la classe CIM pour laquelle effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="6acf1-135">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="6acf1-136">Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des classes, car PowerShell obtient une liste des classes du serveur WMI local pour fournir une liste de noms de classe.</span><span class="sxs-lookup"><span data-stu-id="6acf1-136">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

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

### <span data-ttu-id="6acf1-137">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="6acf1-137">-ComputerName</span></span>

<span data-ttu-id="6acf1-138">Spécifie l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="6acf1-138">Specifies the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="6acf1-139">Vous pouvez spécifier un nom de domaine complet (FQDN), un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="6acf1-139">You can specify a fully qualified domain name (FQDN) a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="6acf1-140">Si vous spécifiez ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan.</span><span class="sxs-lookup"><span data-stu-id="6acf1-140">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="6acf1-141">Si vous ne spécifiez pas ce paramètre, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="6acf1-141">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="6acf1-142">Si plusieurs opérations sont exécutées sur le même ordinateur, l’utilisation d’une session CIM offre de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="6acf1-142">If multiple operations are being performed on the same computer, using a CIM session gives better performance.</span></span>

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

### <span data-ttu-id="6acf1-143">-MethodName</span><span class="sxs-lookup"><span data-stu-id="6acf1-143">-MethodName</span></span>

<span data-ttu-id="6acf1-144">Recherche les classes qui ont une méthode correspondant à ce nom.</span><span class="sxs-lookup"><span data-stu-id="6acf1-144">Finds the classes that have a method matching this name.</span></span> <span data-ttu-id="6acf1-145">Vous pouvez utiliser des caractères génériques avec ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="6acf1-145">You can use wildcard characters with this parameter.</span></span>

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

### <span data-ttu-id="6acf1-146">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="6acf1-146">-Namespace</span></span>

<span data-ttu-id="6acf1-147">Spécifie l’espace de noms pour l’opération CIM.</span><span class="sxs-lookup"><span data-stu-id="6acf1-147">Specifies the namespace for CIM operation.</span></span> <span data-ttu-id="6acf1-148">L’espace de noms par défaut est **root/cimv2**.</span><span class="sxs-lookup"><span data-stu-id="6acf1-148">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="6acf1-149">Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="6acf1-149">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

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

### <span data-ttu-id="6acf1-150">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="6acf1-150">-OperationTimeoutSec</span></span>

<span data-ttu-id="6acf1-151">Spécifie la durée pendant laquelle l’applet de commande attend une réponse de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6acf1-151">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="6acf1-152">Par défaut, la valeur de ce paramètre est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="6acf1-152">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="6acf1-153">Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion fiable de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables, car l’opération sur le serveur expire avant que le client puisse se reconnecter.</span><span class="sxs-lookup"><span data-stu-id="6acf1-153">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="6acf1-154">-PropertyName</span><span class="sxs-lookup"><span data-stu-id="6acf1-154">-PropertyName</span></span>

<span data-ttu-id="6acf1-155">Recherche les classes qui ont une propriété correspondant à ce nom.</span><span class="sxs-lookup"><span data-stu-id="6acf1-155">Finds the classes which have a property matching this name.</span></span> <span data-ttu-id="6acf1-156">Vous pouvez utiliser des caractères génériques avec ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="6acf1-156">You can use wildcard characters with this parameter.</span></span>

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

### <span data-ttu-id="6acf1-157">-QualifierName</span><span class="sxs-lookup"><span data-stu-id="6acf1-157">-QualifierName</span></span>

<span data-ttu-id="6acf1-158">Filtre les classes par nom de qualificateur au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="6acf1-158">Filters the classes by class level qualifier name.</span></span> <span data-ttu-id="6acf1-159">Vous pouvez utiliser des caractères génériques avec ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="6acf1-159">You can use wildcard characters with this parameter.</span></span>

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

### <span data-ttu-id="6acf1-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6acf1-160">CommonParameters</span></span>

<span data-ttu-id="6acf1-161">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6acf1-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6acf1-162">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6acf1-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6acf1-163">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6acf1-163">INPUTS</span></span>

### <span data-ttu-id="6acf1-164">None</span><span class="sxs-lookup"><span data-stu-id="6acf1-164">None</span></span>

<span data-ttu-id="6acf1-165">Cette applet de commande n’accepte aucun objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="6acf1-165">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="6acf1-166">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6acf1-166">OUTPUTS</span></span>

### <span data-ttu-id="6acf1-167">Microsoft. Management. infrastructure. CimClass</span><span class="sxs-lookup"><span data-stu-id="6acf1-167">Microsoft.Management.Infrastructure.CimClass</span></span>

<span data-ttu-id="6acf1-168">Cette applet de commande retourne un objet de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="6acf1-168">This cmdlet returns a CIM class object.</span></span>

## <span data-ttu-id="6acf1-169">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6acf1-169">NOTES</span></span>

## <span data-ttu-id="6acf1-170">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6acf1-170">RELATED LINKS</span></span>

[<span data-ttu-id="6acf1-171">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="6acf1-171">New-CimSession</span></span>](New-CimSession.md)

