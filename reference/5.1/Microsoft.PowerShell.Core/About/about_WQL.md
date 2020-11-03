---
description: Décrit le langage de requêtes WMI (WQL) qui peut être utilisé pour obtenir des objets WMI dans Windows PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wql?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WQL
ms.openlocfilehash: c6fd523864d419fb400b7041e92ec8f0733724b7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207881"
---
# <a name="about-wql"></a><span data-ttu-id="69dc9-104">À propos de WQL</span><span class="sxs-lookup"><span data-stu-id="69dc9-104">About WQL</span></span>

## <a name="short-description"></a><span data-ttu-id="69dc9-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="69dc9-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="69dc9-106">Décrit le langage de requêtes WMI (WQL) qui peut être utilisé pour obtenir des objets WMI dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69dc9-106">Describes WMI Query Language (WQL), which can be used to get WMI objects in Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="69dc9-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="69dc9-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="69dc9-108">WQL est le langage de requête Windows Management Instrumentation (WMI), qui est le langage utilisé pour obtenir des informations à partir de WMI.</span><span class="sxs-lookup"><span data-stu-id="69dc9-108">WQL is the Windows Management Instrumentation (WMI) query language, which is the language used to get information from WMI.</span></span>

<span data-ttu-id="69dc9-109">Vous n’êtes pas obligé d’utiliser WQL pour exécuter une requête WMI dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69dc9-109">You are not required to use WQL to perform a WMI query in Windows PowerShell.</span></span>
<span data-ttu-id="69dc9-110">Au lieu de cela, vous pouvez utiliser les paramètres des applets de commande Get-WmiObject ou Get-CimInstance.</span><span class="sxs-lookup"><span data-stu-id="69dc9-110">Instead, you can use the parameters of the Get-WmiObject or Get-CimInstance cmdlets.</span></span> <span data-ttu-id="69dc9-111">Les requêtes WQL sont un peu plus rapides que les commandes de Get-WmiObject standard et les performances améliorées sont évidentes lorsque les commandes s’exécutent sur des centaines de systèmes.</span><span class="sxs-lookup"><span data-stu-id="69dc9-111">WQL queries are somewhat faster than standard Get-WmiObject commands and the improved performance is evident when the commands run on hundreds of systems.</span></span> <span data-ttu-id="69dc9-112">Toutefois, veillez à ce que le temps que vous consacrez à l’écriture d’une requête WQL réussie n’compense pas l’amélioration des performances.</span><span class="sxs-lookup"><span data-stu-id="69dc9-112">However, be sure that the time you spend to write a successful WQL query doesn't outweigh the performance improvement.</span></span>

<span data-ttu-id="69dc9-113">Les instructions WQL de base dont vous avez besoin pour utiliser WQL sont Select, where et from.</span><span class="sxs-lookup"><span data-stu-id="69dc9-113">The basic WQL statements you need to use WQL are Select, Where, and From.</span></span>

## <a name="when-to-use-wql"></a><span data-ttu-id="69dc9-114">QUAND UTILISER WQL</span><span class="sxs-lookup"><span data-stu-id="69dc9-114">WHEN TO USE WQL</span></span>

<span data-ttu-id="69dc9-115">Lorsque vous travaillez avec WMI, et en particulier avec WQL, n’oubliez pas que vous utilisez également Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69dc9-115">When working with WMI, and especially with WQL, do not forget that you are also using Windows PowerShell.</span></span> <span data-ttu-id="69dc9-116">Souvent, si une requête WQL ne fonctionne pas comme prévu, il est plus facile d’utiliser une commande Windows PowerShell standard que de déboguer la requête WQL.</span><span class="sxs-lookup"><span data-stu-id="69dc9-116">Often, if a WQL query does not work as expected, it's easier to use a standard Windows PowerShell command than to debug the WQL query.</span></span>

<span data-ttu-id="69dc9-117">À moins que vous ne retournaiez de grandes quantités de données à partir de systèmes distants limités en bande passante, il est rarement productif de consacrer des heures à une requête WQL compliquée et compliquée lorsqu’il existe une applet de commande Windows parfaitement acceptable qui fait la même chose, si un peu plus lentement.</span><span class="sxs-lookup"><span data-stu-id="69dc9-117">Unless you are returning massive amounts of data from across bandwidth-constrained remote systems, it is rarely productive to spend hours trying to perfect a complicated and convoluted WQL query when there is a perfectly acceptable Windows cmdlet that does the same thing, if a bit more slowly.</span></span>

## <a name="using-the-select-statement"></a><span data-ttu-id="69dc9-118">UTILISATION DE L’INSTRUCTION SELECT</span><span class="sxs-lookup"><span data-stu-id="69dc9-118">USING THE SELECT STATEMENT</span></span>

<span data-ttu-id="69dc9-119">Une requête WMI classique commence par une instruction SELECT qui obtient toutes les propriétés ou des propriétés particulières d’une classe WMI.</span><span class="sxs-lookup"><span data-stu-id="69dc9-119">A typical WMI query begins with a Select statement that gets all properties or particular properties of a WMI class.</span></span> <span data-ttu-id="69dc9-120">Pour sélectionner toutes les propriétés d’une classe WMI, utilisez un astérisque ( \* ).</span><span class="sxs-lookup"><span data-stu-id="69dc9-120">To select all properties of a WMI class, use an asterisk (\*).</span></span> <span data-ttu-id="69dc9-121">Le mot clé from spécifie la classe WMI.</span><span class="sxs-lookup"><span data-stu-id="69dc9-121">The From keyword specifies the WMI class.</span></span>

<span data-ttu-id="69dc9-122">Une instruction SELECT a le format suivant :</span><span class="sxs-lookup"><span data-stu-id="69dc9-122">A Select statement has the following format:</span></span>

```
Select <property> from <WMI-class>
```

<span data-ttu-id="69dc9-123">Par exemple, l’instruction SELECT suivante sélectionne toutes les propriétés (\*) des instances de la classe WMI Win32_Bios.</span><span class="sxs-lookup"><span data-stu-id="69dc9-123">For example, the following Select statement selects all properties (\*) from the instances of the Win32_Bios WMI class.</span></span>

```
Select * from Win32_Bios
```

<span data-ttu-id="69dc9-124">Pour sélectionner une propriété particulière d’une classe WMI, placez le nom de la propriété entre les mots clés SELECT et from.</span><span class="sxs-lookup"><span data-stu-id="69dc9-124">To select a particular property of a WMI class, place the property name between the Select and From keywords.</span></span>

<span data-ttu-id="69dc9-125">La requête suivante sélectionne uniquement le nom du BIOS de la classe WMI Win32_Bios.</span><span class="sxs-lookup"><span data-stu-id="69dc9-125">The following query selects only the name of the BIOS from the Win32_Bios WMI class.</span></span> <span data-ttu-id="69dc9-126">La commande enregistre la requête dans la variable $queryName.</span><span class="sxs-lookup"><span data-stu-id="69dc9-126">The command saves the query in the $queryName variable.</span></span>

```
Select Name from Win32_Bios
```

<span data-ttu-id="69dc9-127">Pour sélectionner plusieurs propriétés, utilisez des virgules pour séparer les noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="69dc9-127">To select more than one property, use commas to separate the property names.</span></span>
<span data-ttu-id="69dc9-128">La requête WMI suivante sélectionne le nom et la version de la classe Win32_Bios WMI.</span><span class="sxs-lookup"><span data-stu-id="69dc9-128">The following WMI query selects the name and the version of the Win32_Bios WMI class.</span></span> <span data-ttu-id="69dc9-129">La commande enregistre la requête dans la variable $queryNameVersion.</span><span class="sxs-lookup"><span data-stu-id="69dc9-129">The command saves the query in the $queryNameVersion variable.</span></span>

```
Select name, version from Win32_Bios
```

## <a name="using-the-wql-query"></a><span data-ttu-id="69dc9-130">UTILISATION DE LA REQUÊTE WQL</span><span class="sxs-lookup"><span data-stu-id="69dc9-130">USING THE WQL QUERY</span></span>

<span data-ttu-id="69dc9-131">Il existe trois façons d’utiliser la requête WQL dans la commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69dc9-131">There are three ways to use WQL query in Windows PowerShell command.</span></span>

- <span data-ttu-id="69dc9-132">Utiliser l’applet de commande Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="69dc9-132">Use the Get-WmiObject cmdlet</span></span>
- <span data-ttu-id="69dc9-133">Utiliser l’applet de commande Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="69dc9-133">Use the Get-CimInstance cmdlet</span></span>
- <span data-ttu-id="69dc9-134">Utilisez l’accélérateur de type [WmiSearcher].</span><span class="sxs-lookup"><span data-stu-id="69dc9-134">Use the [wmisearcher] type accelerator.</span></span>

## <a name="using-the-get-wmiobject-cmdlet"></a><span data-ttu-id="69dc9-135">UTILISATION DE L’APPLET DE COMMANDE « OBTIENT-WMIOBJECT »</span><span class="sxs-lookup"><span data-stu-id="69dc9-135">USING THE GET-WMIOBJECT CMDLET</span></span>

<span data-ttu-id="69dc9-136">La méthode la plus simple pour utiliser la requête WQL consiste à la placer entre guillemets (sous forme de chaîne), puis à utiliser la chaîne de requête comme valeur du paramètre de requête de l’applet de commande Get-WmiObject, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="69dc9-136">The most basic way to use the WQL query is to enclose it in quotation marks (as a string) and then use the query string as the value of the Query parameter of the Get-WmiObject cmdlet, as shown in the following example.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="69dc9-137">Vous pouvez également enregistrer l’instruction WQL dans une variable, puis utiliser la variable comme valeur du paramètre de requête, comme indiqué dans la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="69dc9-137">You can also save the WQL statement in a variable and then use the variable as the value of the Query parameter, as shown in the following command.</span></span>

```powershell
$query = "Select * from Win32_Bios"
Get-WmiObject -Query $query
```

<span data-ttu-id="69dc9-138">Vous pouvez utiliser l’un ou l’autre format avec n’importe quelle instruction WQL.</span><span class="sxs-lookup"><span data-stu-id="69dc9-138">You can use either format with any WQL statement.</span></span> <span data-ttu-id="69dc9-139">La commande suivante utilise la requête de la variable $queryName pour obtenir uniquement les propriétés Name et version du BIOS système.</span><span class="sxs-lookup"><span data-stu-id="69dc9-139">The following command uses the query in the $queryName variable to get only the name and version properties of the system BIOS.</span></span>

```powershell
$queryNameVersion = "Select Name, Version from Win32_Bios"
Get-WmiObject -Query $queryNameVersion
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

<span data-ttu-id="69dc9-140">N’oubliez pas que vous pouvez utiliser les paramètres de l’applet de commande Get-WmiObject pour obtenir le même résultat.</span><span class="sxs-lookup"><span data-stu-id="69dc9-140">Remember that you can use the parameters of the Get-WmiObject cmdlet to get the same result.</span></span> <span data-ttu-id="69dc9-141">Par exemple, la commande suivante obtient également les valeurs des propriétés Name et version des instances de la classe Win32_Bios WMI.</span><span class="sxs-lookup"><span data-stu-id="69dc9-141">For example, the following command also gets the values of the Name and Version properties of instances of the Win32_Bios WMI class.</span></span>

```powershell
Get-WmiObject -Class Win32_Bios -Property Name, Version
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

## <a name="using-the-get-ciminstance-cmdlet"></a><span data-ttu-id="69dc9-142">UTILISATION DE L’APPLET DE COMMANDE CIMINSTANCE</span><span class="sxs-lookup"><span data-stu-id="69dc9-142">USING THE GET-CIMINSTANCE CMDLET</span></span>

<span data-ttu-id="69dc9-143">À compter de Windows PowerShell 3,0, vous pouvez utiliser l’applet de commande Get-CimInstance pour exécuter des requêtes WQL.</span><span class="sxs-lookup"><span data-stu-id="69dc9-143">Beginning in Windows PowerShell 3.0, you can use the Get-CimInstance cmdlet to run WQL queries.</span></span>

<span data-ttu-id="69dc9-144">Get-CimInstance obtient des instances de classes conformes à CIM, y compris les classes WMI.</span><span class="sxs-lookup"><span data-stu-id="69dc9-144">Get-CimInstance gets instances of CIM-compliant classes, including WMI classes.</span></span> <span data-ttu-id="69dc9-145">Les applets de commande CIM, ont introduit Windows PowerShell 3,0, effectuent les mêmes tâches que les applets de commande WMI.</span><span class="sxs-lookup"><span data-stu-id="69dc9-145">The CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="69dc9-146">Les applets de commande CIM sont conformes aux normes WS-Management (WSMan) et à la norme Common Information Model (CIM), qui permettent aux cmdlets d’utiliser les mêmes techniques pour gérer les ordinateurs Windows et les ordinateurs qui exécutent d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="69dc9-146">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard, which enables the cmdlets to use the same techniques to manage Windows computers and computers that are running other operating systems.</span></span>

<span data-ttu-id="69dc9-147">La commande suivante utilise l’applet de commande Get-CimInstance pour exécuter une requête WQL.</span><span class="sxs-lookup"><span data-stu-id="69dc9-147">The following command uses the Get-CimInstance cmdlet to run a WQL query.</span></span>

<span data-ttu-id="69dc9-148">Toute requête WQL qui peut être utilisée avec Get-WmiObject peut également être utilisée avec la fonction CimInstance.</span><span class="sxs-lookup"><span data-stu-id="69dc9-148">Any WQL query that can be used with Get-WmiObject can also be used with Get-CimInstance.</span></span>

```powershell
Get-CimInstance -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="69dc9-149">Get-CimInstance retourne un objet CimInstance à la place du ManagementObject retourné par Get-WmiObject, mais les objets sont très similaires.</span><span class="sxs-lookup"><span data-stu-id="69dc9-149">Get-CimInstance returns a CimInstance object, instead of the ManagementObject that Get-WmiObject returns, but the objects are quite similar.</span></span>

```
(Get-CimInstance -Query "Select * from Win32_Bios").GetType().FullName
Microsoft.Management.Infrastructure.CimInstance
(Get-WmiObject -Query "Select * from Win32_Bios").GetType().FullName
System.Management.ManagementObject
```

## <a name="using-the-wmisearcher-type-accelerator"></a><span data-ttu-id="69dc9-150">UTILISATION de l’accélérateur de TYPE [WmiSearcher]</span><span class="sxs-lookup"><span data-stu-id="69dc9-150">USING THE [wmisearcher] TYPE ACCELERATOR</span></span>

<span data-ttu-id="69dc9-151">L’accélérateur de type [WmiSearcher] crée un objet ManagementObjectSearcher à partir d’une chaîne d’instruction WQL.</span><span class="sxs-lookup"><span data-stu-id="69dc9-151">The [wmisearcher] type accelerator creates a ManagementObjectSearcher object from a WQL statement string.</span></span> <span data-ttu-id="69dc9-152">L’objet ManagementObjectSearcher a de nombreuses propriétés et méthodes, mais la méthode la plus basique est la méthode d’extraction, qui appelle la requête WMI spécifiée et retourne les objets résultants.</span><span class="sxs-lookup"><span data-stu-id="69dc9-152">The ManagementObjectSearcher object has many properties and methods, but the most basic method is the Get method, which invokes the specified WMI query and returns the resulting objects.</span></span>

<span data-ttu-id="69dc9-153">À l’aide de [WmiSearcher], vous pouvez accéder facilement à la classe ManagementObjectSearcher .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69dc9-153">By using the [wmisearcher], you gain easy access to the ManagementObjectSearcher .NET Framework class.</span></span> <span data-ttu-id="69dc9-154">Cela vous permet d’interroger WMI et de configurer le mode d’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="69dc9-154">This lets you query WMI and to configure the way the query is conducted.</span></span>

<span data-ttu-id="69dc9-155">Pour utiliser l’accélérateur de type [WmiSearcher] :</span><span class="sxs-lookup"><span data-stu-id="69dc9-155">To use the [wmisearcher] type accelerator:</span></span>

1. <span data-ttu-id="69dc9-156">Effectuez un cast de la chaîne WQL en objet ManagementObjectSearcher.</span><span class="sxs-lookup"><span data-stu-id="69dc9-156">Cast the  WQL string into a ManagementObjectSearcher object.</span></span>
2. <span data-ttu-id="69dc9-157">Appelez la méthode d’extraction de l’objet ManagementObjectSearcher.</span><span class="sxs-lookup"><span data-stu-id="69dc9-157">Call the Get method of the ManagementObjectSearcher object.</span></span>

<span data-ttu-id="69dc9-158">Par exemple, la commande suivante convertit la requête « sélectionner tout », enregistre le résultat dans la variable $bios, puis appelle la méthode d’extraction de l’objet ManagementObjectSearcher dans la variable $bios.</span><span class="sxs-lookup"><span data-stu-id="69dc9-158">For example, the following command casts the "select all" query, saves the result in the $bios variable, and then calls the Get method of the ManagementObjectSearcher object in the $bios variable.</span></span>

```powershell
$bios = [wmisearcher]"Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="69dc9-159">Remarque : seules les propriétés d’objet sélectionnées sont affichées par défaut.</span><span class="sxs-lookup"><span data-stu-id="69dc9-159">NOTE: Only selected object properties are displayed by default.</span></span> <span data-ttu-id="69dc9-160">Ces propriétés sont définies dans le fichier XML Types.ps1.</span><span class="sxs-lookup"><span data-stu-id="69dc9-160">These properties are defined in the Types.ps1xml file.</span></span>

<span data-ttu-id="69dc9-161">Vous pouvez utiliser l’accélérateur de type [WmiSearcher] pour effectuer un cast de la requête ou de la variable.</span><span class="sxs-lookup"><span data-stu-id="69dc9-161">You can use the [wmisearcher] type accelerator to cast the query or the variable.</span></span> <span data-ttu-id="69dc9-162">Dans l’exemple suivant, l’accélérateur de type [WmiSearcher] est utilisé pour effectuer un cast de la variable.</span><span class="sxs-lookup"><span data-stu-id="69dc9-162">In the following example, the [wmisearcher] type accelerator is used to cast the variable.</span></span> <span data-ttu-id="69dc9-163">Le résultat est le même.</span><span class="sxs-lookup"><span data-stu-id="69dc9-163">The result is the same.</span></span>

```powershell
[wmisearcher]$bios = "Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="69dc9-164">Quand vous utilisez l’accélérateur de type [WmiSearcher], il modifie la chaîne de requête en un objet ManagementObjectSearcher, comme indiqué dans les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="69dc9-164">When you use the [wmisearcher] type accelerator, it changes the query string into a ManagementObjectSearcher object, as shown in the following commands.</span></span>

```
$a = "Select * from Win32_Bios"
$a.GetType().FullName
System.String

$a = [wmisearcher]"Select * from Win32_Bios"
$a.GetType().FullName
System.Management.ManagementObjectSearcher
```

<span data-ttu-id="69dc9-165">Ce format de commande fonctionne sur toutes les requêtes.</span><span class="sxs-lookup"><span data-stu-id="69dc9-165">This command format works on any query.</span></span> <span data-ttu-id="69dc9-166">La commande suivante obtient la valeur de la propriété Name de la classe WMI Win32_Bios.</span><span class="sxs-lookup"><span data-stu-id="69dc9-166">The following command gets the value of the Name property of the Win32_Bios WMI class.</span></span>

```powershell
$biosname = [wmisearcher]"Select Name from Win32_Bios"
$biosname.Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

<span data-ttu-id="69dc9-167">Vous pouvez effectuer cette opération dans une commande unique, bien que la commande soit un peu plus difficile à interpréter.</span><span class="sxs-lookup"><span data-stu-id="69dc9-167">You can perform this operation in a single command, although the command is a bit more difficult to interpret.</span></span>

<span data-ttu-id="69dc9-168">Dans ce format, vous utilisez l’accélérateur de type [WmiSearcher] pour effectuer un cast de la chaîne de requête WQL en ManagementObjectSearcher, puis appeler la méthode d’extraction sur l’objet, le tout dans une même commande.</span><span class="sxs-lookup"><span data-stu-id="69dc9-168">In this format, you use the [wmisearcher] type accelerator to cast the WQL query string to a ManagementObjectSearcher, and then call the Get method on the object -- all in a single command.</span></span> <span data-ttu-id="69dc9-169">Les parenthèses () qui encadrent la chaîne transtypée dirigent Windows PowerShell pour effectuer un cast de la chaîne avant d’appeler la méthode.</span><span class="sxs-lookup"><span data-stu-id="69dc9-169">The parentheses () that enclose the casted string direct Windows PowerShell to cast the string before calling the method.</span></span>

```powershell
([wmisearcher]"Select name from Win32_Bios").Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

## <a name="using-the-basic-wql-where-statement"></a><span data-ttu-id="69dc9-170">UTILISATION DE L’INSTRUCTION WHERE WQL DE BASE</span><span class="sxs-lookup"><span data-stu-id="69dc9-170">USING THE BASIC WQL WHERE STATEMENT</span></span>

<span data-ttu-id="69dc9-171">Une instruction WHERE établit des conditions pour les données retournées par une instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="69dc9-171">A Where statement establishes conditions for the data that a Select statement returns.</span></span>

<span data-ttu-id="69dc9-172">L’instruction WHERE a le format suivant :</span><span class="sxs-lookup"><span data-stu-id="69dc9-172">The Where statement has the following format:</span></span>

```
where <property> <operator> <value>
```

<span data-ttu-id="69dc9-173">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="69dc9-173">For example:</span></span>

```
where Name = 'Notepad.exe'
```

<span data-ttu-id="69dc9-174">L’instruction WHERE est utilisée avec l’instruction SELECT, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="69dc9-174">The Where statement is used with the Select statement, as shown in the following example.</span></span>

```
Select * from Win32_Process where Name = 'Notepad.exe'
```

<span data-ttu-id="69dc9-175">Lorsque vous utilisez l’instruction WHERE, le nom et la valeur de la propriété doivent être précis.</span><span class="sxs-lookup"><span data-stu-id="69dc9-175">When using the Where statement, the property name and value must be accurate.</span></span>

<span data-ttu-id="69dc9-176">Par exemple, la commande suivante obtient les processus du bloc-notes sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="69dc9-176">For example, the following command gets the Notepad processes on the local computer.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad.exe'"
```

<span data-ttu-id="69dc9-177">Toutefois, la commande suivante échoue, car le nom du processus comprend l’extension de nom de fichier « . exe ».</span><span class="sxs-lookup"><span data-stu-id="69dc9-177">However, the following command fails, because the process name includes the ".exe" file name extension.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad'"
```

## <a name="where-statement-comparison-operators"></a><span data-ttu-id="69dc9-178">OPÉRATEURS DE COMPARAISON D’INSTRUCTIONS WHERE</span><span class="sxs-lookup"><span data-stu-id="69dc9-178">WHERE STATEMENT COMPARISON OPERATORS</span></span>

<span data-ttu-id="69dc9-179">Les opérateurs suivants sont valides dans une instruction WQL Where.</span><span class="sxs-lookup"><span data-stu-id="69dc9-179">The following operators are valid in a WQL Where statement.</span></span>

```
Operator    Description
-----------------------
=           Equal
!=          Not equal
<>          Not equal
<           Less than
>           Greater than
<=          Less than or equal
>=          Greater than or equal
LIKE        Wildcard match
IS          Evaluates null
ISNOT       Evaluates not null
ISA         Evaluates a member of a WMI class
```

<span data-ttu-id="69dc9-180">Il existe d’autres opérateurs, mais ceux-ci sont utilisés pour effectuer des comparaisons.</span><span class="sxs-lookup"><span data-stu-id="69dc9-180">There are other operators, but these are the ones used for making comparisons.</span></span>

<span data-ttu-id="69dc9-181">Par exemple, la requête suivante sélectionne les propriétés Name et Priority dans les processus de la classe Win32_Process, où la priorité du processus est supérieure ou égale à 11.</span><span class="sxs-lookup"><span data-stu-id="69dc9-181">For example, the following query selects the Name and Priority properties from processes in the Win32_Process class where the process priority is greater than or equal to 11.</span></span> <span data-ttu-id="69dc9-182">L’applet de commande Get-WmiObject exécute la requête.</span><span class="sxs-lookup"><span data-stu-id="69dc9-182">The Get-WmiObject cmdlet runs the query.</span></span>

```powershell
$highPriority = "Select Name, Priority from Win32_Process " +
  "where Priority >= 11"
Get-WmiObject -Query $highPriority
```

## <a name="using-the-wql-operators-in-the-filter-parameter"></a><span data-ttu-id="69dc9-183">UTILISATION DES OPÉRATEURS WQL DANS LE PARAMÈTRE FILTER</span><span class="sxs-lookup"><span data-stu-id="69dc9-183">USING THE WQL OPERATORS IN THE FILTER PARAMETER</span></span>

<span data-ttu-id="69dc9-184">Les opérateurs WQL peuvent également être utilisés dans la valeur du paramètre Filter des applets de commande Get-WmiObject ou Get-CimInstance, ainsi que dans la valeur des paramètres de requête de ces applets de commande.</span><span class="sxs-lookup"><span data-stu-id="69dc9-184">The WQL operators can also be used in the value of the Filter parameter of the Get-WmiObject or Get-CimInstance cmdlets, as well as in the value of the Query parameters of these cmdlets.</span></span>

<span data-ttu-id="69dc9-185">Par exemple, la commande suivante obtient les propriétés Name et ProcessID des cinq derniers processus dont les valeurs ProcessID sont supérieures à 1004.</span><span class="sxs-lookup"><span data-stu-id="69dc9-185">For example, the following command gets the Name and ProcessID properties of the last five processes that have ProcessID values greater than 1004.</span></span> <span data-ttu-id="69dc9-186">La commande utilise le paramètre Filter pour spécifier la condition ProcessID.</span><span class="sxs-lookup"><span data-stu-id="69dc9-186">The command uses the Filter parameter to specify the ProcessID condition.</span></span>

```powershell
Get-WmiObject -Class Win32_Process `
-Property Name, ProcessID -Filter "ProcessID >= 1004" |
Sort ProcessID | Select Name, ProcessID -Last 5
```

```output
Name                                 ProcessID
----                                 ---------
SROSVC.exe                                4220
WINWORD.EXE                               4664
TscHelp.exe                               4744
SnagIt32.exe                              4748
WmiPrvSE.exe                              5056
```

## <a name="using-the-like-operator"></a><span data-ttu-id="69dc9-187">UTILISATION DE L’OPÉRATEUR LIKE</span><span class="sxs-lookup"><span data-stu-id="69dc9-187">USING THE LIKE OPERATOR</span></span>

<span data-ttu-id="69dc9-188">L’opérateur Like vous permet d’utiliser des caractères génériques pour filtrer les résultats d’une requête WQL.</span><span class="sxs-lookup"><span data-stu-id="69dc9-188">The Like operator lets you use wildcard characters to filter the results of a WQL query.</span></span>

```
Like Operator  Description
--------------------------------------------------
[]             Character in a range [a-f] or a set
               of characters [abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

^              Character not in a range [^a-f] or
               not in a set [^abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

%              A string of zero or more characters

_              One character.
(underscore)   NOTE: To use a literal underscore
               in a query string, enclose it in
               square brackets [_].
```

<span data-ttu-id="69dc9-189">Lorsque l’opérateur Like est utilisé sans caractères génériques ou opérateurs de plage, il se comporte comme l’opérateur d’égalité (=) et retourne des objets uniquement lorsqu’il s’agit d’une correspondance exacte pour le modèle.</span><span class="sxs-lookup"><span data-stu-id="69dc9-189">When the Like operator is used without any wildcard characters or range operators, it behaves like the equality operator (=) and returns objects only when they are an exact match for the pattern.</span></span>

<span data-ttu-id="69dc9-190">Vous pouvez combiner l’opération de plage avec le caractère générique de pourcentage pour créer des filtres simples, mais puissants.</span><span class="sxs-lookup"><span data-stu-id="69dc9-190">You can combine the range operation with the percent wildcard character to create simple, yet powerful filters.</span></span>

### <a name="like-operator-examples"></a><span data-ttu-id="69dc9-191">LIKE, EXEMPLES D’OPÉRATEURS</span><span class="sxs-lookup"><span data-stu-id="69dc9-191">LIKE OPERATOR EXAMPLES</span></span>

#### <a name="example-1-range"></a><span data-ttu-id="69dc9-192">EXEMPLE 1 : [ \<range> ]</span><span class="sxs-lookup"><span data-stu-id="69dc9-192">EXAMPLE 1: [\<range>]</span></span>

<span data-ttu-id="69dc9-193">Les commandes suivantes démarrent le bloc-notes, puis recherchent une instance de la classe Win32_Process dont le nom commence par une lettre comprise entre « H » et « N » (non-respect de la casse).</span><span class="sxs-lookup"><span data-stu-id="69dc9-193">The following commands start Notepad and then search for an instance of the Win32_Process class that has a name that starts with a letter between "H" and "N" (case-insensitive).</span></span>

<span data-ttu-id="69dc9-194">La requête doit retourner n’importe quel processus de Hotpad.exe via Notepad.exe.</span><span class="sxs-lookup"><span data-stu-id="69dc9-194">The query should return any process from Hotpad.exe through Notepad.exe.</span></span>

```powershell
Notepad   # Starts Notepad
$query = "Select * from win32_Process where Name LIKE '[H-N]otepad.exe'"
Get-WmiObject -Query $query | Select Name, ProcessID
```

```output
Name                                ProcessID
----                                ---------
notepad.exe                              1740
```

#### <a name="example-2-range-and-"></a><span data-ttu-id="69dc9-195">EXEMPLE 2 : [ \<range> ] et%</span><span class="sxs-lookup"><span data-stu-id="69dc9-195">EXAMPLE 2: [\<range>] and %</span></span>

<span data-ttu-id="69dc9-196">Les commandes suivantes sélectionnent tous les processus dont le nom commence par une lettre comprise entre A et P (non-respect de la casse) suivi de zéro, une ou plusieurs lettres dans n’importe quelle combinaison.</span><span class="sxs-lookup"><span data-stu-id="69dc9-196">The following commands select all process that have a name that begins with a letter between A and P (case-insensitive) followed by zero or more letters in any combination.</span></span>

<span data-ttu-id="69dc9-197">L’applet de commande Get-WmiObject exécute la requête, l’applet de commande Select-Object obtient les propriétés Name et ProcessID, et l’applet de commande Sort-Object trie les résultats par ordre alphabétique par nom.</span><span class="sxs-lookup"><span data-stu-id="69dc9-197">The Get-WmiObject cmdlet runs the query, the Select-Object cmdlet gets the Name and ProcessID properties, and the Sort-Object cmdlet sorts the results in alphabetical order by name.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE '[A-P]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-3-not-in-range-"></a><span data-ttu-id="69dc9-198">EXEMPLE 3 : pas dans la plage (^)</span><span class="sxs-lookup"><span data-stu-id="69dc9-198">EXAMPLE 3: Not in Range (^)</span></span>

<span data-ttu-id="69dc9-199">La commande suivante obtient les processus dont les noms ne commencent pas par les lettres suivantes : A, S, W, P, R, C, U, N</span><span class="sxs-lookup"><span data-stu-id="69dc9-199">The following command gets processes whose names do not begin with any of the following letters: A, S, W, P, R, C, U, N</span></span>

<span data-ttu-id="69dc9-200">et ont suivi zéro ou plusieurs lettres.</span><span class="sxs-lookup"><span data-stu-id="69dc9-200">and followed zero or more letters.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE '[^ASWPRCUN]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-4-any-characters----or-none-"></a><span data-ttu-id="69dc9-201">EXEMPLE 4 : tous les caractères--ou aucun (%)</span><span class="sxs-lookup"><span data-stu-id="69dc9-201">EXAMPLE 4: Any characters -- or none (%)</span></span>

<span data-ttu-id="69dc9-202">Les commandes suivantes obtiennent des processus dont le nom commence par « Calc ».</span><span class="sxs-lookup"><span data-stu-id="69dc9-202">The following commands get processes that have names that begin with "calc".</span></span>
<span data-ttu-id="69dc9-203">Le symbole% dans WQL est équivalent au symbole astérisque ( \* ) dans les expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="69dc9-203">The % symbol in WQL is equivalent to the asterisk (\*) symbol in regular expressions.</span></span>

```powershell
$query = "Select * from win32_Process where Name LIKE 'calc%'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                               ProcessID
----                               ---------
calc.exe                                4424
```

#### <a name="example-5-one-character-_"></a><span data-ttu-id="69dc9-204">EXEMPLE 5 : un caractère (_)</span><span class="sxs-lookup"><span data-stu-id="69dc9-204">EXAMPLE 5: One character (_)</span></span>

<span data-ttu-id="69dc9-205">Les commandes suivantes obtiennent les processus dont les noms ont le modèle suivant, « c_lc.exe », où le caractère de soulignement représente un caractère quelconque.</span><span class="sxs-lookup"><span data-stu-id="69dc9-205">The following commands get processes that have names that have the following pattern, "c_lc.exe" where the underscore character represents any one character.</span></span> <span data-ttu-id="69dc9-206">Ce modèle met en correspondance n’importe quel nom de calc.exe via czlc.exe ou c9lc.exe, mais ne correspond pas aux noms dans lesquels « c » et « l » sont séparés par plusieurs caractères.</span><span class="sxs-lookup"><span data-stu-id="69dc9-206">This pattern matches any name from calc.exe through czlc.exe, or c9lc.exe, but does not match names in which the "c" and "l" are separated by more than one character.</span></span>

```powershell
$query = "Select * from Win32_Process where Name LIKE 'c_lc.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                                 ProcessID
----                                 ---------
calc.exe                                  4424
```

#### <a name="example-6-exact-match"></a><span data-ttu-id="69dc9-207">EXEMPLE 6 : correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="69dc9-207">EXAMPLE 6: Exact match</span></span>

<span data-ttu-id="69dc9-208">Les commandes suivantes obtiennent des processus nommés WLIDSVC.exe.</span><span class="sxs-lookup"><span data-stu-id="69dc9-208">The following commands get processes named WLIDSVC.exe.</span></span> <span data-ttu-id="69dc9-209">Même si la requête utilise le mot clé like, elle nécessite une correspondance exacte, car la valeur n’inclut pas de caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="69dc9-209">Even though the query uses the Like keyword, it requires an exact match, because the value does not include any wildcard characters.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE 'WLIDSVC.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```powershell

```output
Name                                 ProcessID
----                                 ---------
WLIDSVC.exe                                84
```

## <a name="using-the-or-operator"></a><span data-ttu-id="69dc9-210">UTILISATION DE L’OPÉRATEUR OR</span><span class="sxs-lookup"><span data-stu-id="69dc9-210">USING THE OR OPERATOR</span></span>

<span data-ttu-id="69dc9-211">Pour spécifier plusieurs conditions indépendantes, utilisez le mot clé ou.</span><span class="sxs-lookup"><span data-stu-id="69dc9-211">To specify multiple independent conditions, use the Or keyword.</span></span> <span data-ttu-id="69dc9-212">Le mot clé ou apparaît dans la clause WHERE.</span><span class="sxs-lookup"><span data-stu-id="69dc9-212">The Or keyword appears in the Where clause.</span></span> <span data-ttu-id="69dc9-213">Il effectue une opération inclusif ou sur deux (ou plus) conditions et retourne des éléments qui répondent à l’une des conditions.</span><span class="sxs-lookup"><span data-stu-id="69dc9-213">It performs an inclusive OR operation on two (or more) conditions and returns items that meet any of the conditions.</span></span>

<span data-ttu-id="69dc9-214">L’opérateur or a le format suivant :</span><span class="sxs-lookup"><span data-stu-id="69dc9-214">The Or operator has the following format:</span></span>

```
Where <property> <operator> <value> or <property> <operator> <value> ...
```

<span data-ttu-id="69dc9-215">Par exemple, les commandes suivantes récupèrent toutes les instances de la classe Win32_Process WMI, mais les retournent uniquement si le nom du processus est winword.exe ou excel.exe.</span><span class="sxs-lookup"><span data-stu-id="69dc9-215">For example, the following commands get all instances of the Win32_Process WMI class but returns them only if the process name is winword.exe or excel.exe.</span></span>

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe'"
Get-WmiObject -Query $q
```

<span data-ttu-id="69dc9-216">L’instruction ou peut être utilisée avec plus de deux conditions.</span><span class="sxs-lookup"><span data-stu-id="69dc9-216">The Or statement can be used with more than two conditions.</span></span> <span data-ttu-id="69dc9-217">Dans la requête suivante, l’instruction ou obtient Winword.exe, Excel.exe ou Powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="69dc9-217">In the following query, the Or statement gets Winword.exe, Excel.exe, or Powershell.exe.</span></span>

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe' or Name='powershell.exe'"
```

## <a name="using-the-and-operator"></a><span data-ttu-id="69dc9-218">UTILISATION DE L’OPÉRATEUR AND</span><span class="sxs-lookup"><span data-stu-id="69dc9-218">USING THE AND OPERATOR</span></span>

<span data-ttu-id="69dc9-219">Pour spécifier plusieurs conditions connexes, utilisez le mot clé and.</span><span class="sxs-lookup"><span data-stu-id="69dc9-219">To specify multiple related conditions, use the And keyword.</span></span> <span data-ttu-id="69dc9-220">Le mot clé et apparaît dans la clause WHERE.</span><span class="sxs-lookup"><span data-stu-id="69dc9-220">The And keyword appears in the Where clause.</span></span> <span data-ttu-id="69dc9-221">Elle retourne les éléments qui remplissent toutes les conditions.</span><span class="sxs-lookup"><span data-stu-id="69dc9-221">It returns items that meet all of the conditions.</span></span>

<span data-ttu-id="69dc9-222">L’opérateur and a le format suivant :</span><span class="sxs-lookup"><span data-stu-id="69dc9-222">The And operator has the following format:</span></span>

```
Where <property> <operator> <value> and <property> <operator> <value> ...
```

<span data-ttu-id="69dc9-223">Par exemple, les commandes suivantes obtiennent des processus dont le nom est « Winword.exe » et l’ID de processus 6512.</span><span class="sxs-lookup"><span data-stu-id="69dc9-223">For example, the following commands get processes that have a name of "Winword.exe" and the process ID of 6512.</span></span>

<span data-ttu-id="69dc9-224">Notez que les commandes utilisent l’applet de commande Get-CimInstance.</span><span class="sxs-lookup"><span data-stu-id="69dc9-224">Note that the commands use the Get-CimInstance cmdlet.</span></span>

```powershell
$q = "Select * from Win32_Process where Name = 'winword.exe' " +
  "and ProcessID =6512"
Get-CimInstance -Query $q
```

```output
ProcessId   Name             HandleCount      WorkingSetSize   VirtualSize
---------   ----             -----------      --------------   -----------
# 6512      WINWORD.EXE      768              117170176        633028608
```

<span data-ttu-id="69dc9-225">Tous les opérateurs, y compris les opérateurs like, sont valides avec les opérateurs or et and.</span><span class="sxs-lookup"><span data-stu-id="69dc9-225">All operators, including the Like operators are valid with the Or and And operators.</span></span> <span data-ttu-id="69dc9-226">Et, vous pouvez combiner les opérateurs or et and dans une seule requête avec des parenthèses qui indiquent à Windows PowerShell les clauses à traiter en premier.</span><span class="sxs-lookup"><span data-stu-id="69dc9-226">And, you can combine the Or and And operators in a single query with parentheses that tell Windows PowerShell which clauses to process first.</span></span>

<span data-ttu-id="69dc9-227">Cette commande utilise le caractère de continuation Windows PowerShell (') divise la commande en deux lignes.</span><span class="sxs-lookup"><span data-stu-id="69dc9-227">This command uses the Windows PowerShell continuation character (\`) divide the command into two lines.</span></span>

```powershell
$q = "Select * from Win32_Process `
where (Name = 'winword.exe' or Name = 'excel.exe') and HandleCount > 700"
Get-CimInstance -Query $q
```

```output
ProcessId    Name             HandleCount      WorkingSetSize   VirtualSize
---------    ----             -----------      --------------   -----------
     6512    WINWORD.EXE      797              117268480        634425344
     9610    EXCEL.EXE        727               38858752        323227648
```

## <a name="searching-for-null-values"></a><span data-ttu-id="69dc9-228">RECHERCHE DE VALEURS NULL</span><span class="sxs-lookup"><span data-stu-id="69dc9-228">SEARCHING FOR NULL VALUES</span></span>

<span data-ttu-id="69dc9-229">La recherche de valeurs NULL dans WMI est complexe, car elle peut entraîner des résultats imprévisibles.</span><span class="sxs-lookup"><span data-stu-id="69dc9-229">Searching for null values in WMI is challenging, because it can lead to unpredictable results.</span></span> <span data-ttu-id="69dc9-230">NULL n’est pas égal à zéro et n’est pas équivalent ou n’est pas une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="69dc9-230">Null is not zero and it is not equivalent or to an empty string.</span></span> <span data-ttu-id="69dc9-231">Certaines propriétés de classe WMI sont initialisées et d’autres pas. par conséquent, une recherche de valeur NULL peut ne pas fonctionner pour toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="69dc9-231">Some WMI class properties are initialized and others are not, so a search for null might not work for all properties.</span></span>

<span data-ttu-id="69dc9-232">Pour rechercher des valeurs NULL, utilisez l’opérateur is avec la valeur « null ».</span><span class="sxs-lookup"><span data-stu-id="69dc9-232">To search for null values, use the Is operator with a value of "null".</span></span>

<span data-ttu-id="69dc9-233">Par exemple, les commandes suivantes obtiennent des processus qui ont une valeur null pour la propriété IntallDate.</span><span class="sxs-lookup"><span data-stu-id="69dc9-233">For example, the following commands get processes that have a null value for the IntallDate property.</span></span> <span data-ttu-id="69dc9-234">Les commandes retournent de nombreux processus.</span><span class="sxs-lookup"><span data-stu-id="69dc9-234">The commands return many processes.</span></span>

```powershell
$q = "Select * from Win32_Process where InstallDate is null"
Get-WmiObject -Query $q
```

<span data-ttu-id="69dc9-235">À l’inverse, la commande suivante obtient les comptes d’utilisateur qui ont une valeur null pour la propriété Description.</span><span class="sxs-lookup"><span data-stu-id="69dc9-235">In contrast, the following command, gets user accounts that have a null value for the Description property.</span></span> <span data-ttu-id="69dc9-236">Cette commande ne retourne aucun compte d’utilisateur, même si la plupart des comptes d’utilisateur n’ont aucune valeur pour la propriété Description.</span><span class="sxs-lookup"><span data-stu-id="69dc9-236">This command does not return any user accounts, even though most user accounts do not have any value for the Description property.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Description is null"
Get-WmiObject -Query $q
```

<span data-ttu-id="69dc9-237">Pour rechercher les comptes d’utilisateur qui n’ont pas de valeur pour la propriété Description, utilisez l’opérateur d’égalité pour obtenir une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="69dc9-237">To find the user accounts that have no value for the Description property, use the equality operator to get an empty string.</span></span> <span data-ttu-id="69dc9-238">Pour représenter la chaîne vide, utilisez deux guillemets simples consécutifs.</span><span class="sxs-lookup"><span data-stu-id="69dc9-238">To represent the empty string, use two consecutive single quotation marks.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Description = '' "
```

## <a name="using-true-or-false"></a><span data-ttu-id="69dc9-239">UTILISATION DE TRUE OU FALSE</span><span class="sxs-lookup"><span data-stu-id="69dc9-239">USING TRUE OR FALSE</span></span>

<span data-ttu-id="69dc9-240">Pour récupérer des valeurs booléennes dans les propriétés des objets WMI, utilisez true et false.</span><span class="sxs-lookup"><span data-stu-id="69dc9-240">To get Boolean values in the properties of WMI objects, use True and False.</span></span>
<span data-ttu-id="69dc9-241">Elles ne sont pas sensibles à la casse.</span><span class="sxs-lookup"><span data-stu-id="69dc9-241">They are not case sensitive.</span></span>

<span data-ttu-id="69dc9-242">La requête WQL suivante retourne uniquement les comptes d’utilisateurs locaux d’un ordinateur joint à un domaine.</span><span class="sxs-lookup"><span data-stu-id="69dc9-242">The following WQL query returns only local user accounts from a domain joined computer.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = True"
Get-CimInstance -Query $q
```

<span data-ttu-id="69dc9-243">Pour rechercher les comptes de domaine, utilisez la valeur false, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="69dc9-243">To find domain accounts, use a value of False, as shown in the following example.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = False"
Get-CimInstance -Query $q
```

## <a name="using-the-escape-character"></a><span data-ttu-id="69dc9-244">UTILISATION DU CARACTÈRE D’ÉCHAPPEMENT</span><span class="sxs-lookup"><span data-stu-id="69dc9-244">USING THE ESCAPE CHARACTER</span></span>

<span data-ttu-id="69dc9-245">WQL utilise la barre oblique inverse ( \) comme caractère d’échappement.</span><span class="sxs-lookup"><span data-stu-id="69dc9-245">WQL uses the backslash (\) as its escape character.</span></span> <span data-ttu-id="69dc9-246">Ceci est différent de Windows PowerShell, qui utilise le caractère de soulignement («»).</span><span class="sxs-lookup"><span data-stu-id="69dc9-246">This is different from Windows PowerShell, which uses the backtick character (\`).</span></span>

<span data-ttu-id="69dc9-247">Les guillemets, et les caractères utilisés pour les guillemets, doivent souvent être échappés afin qu’ils ne soient pas mal interprétés.</span><span class="sxs-lookup"><span data-stu-id="69dc9-247">Quotation marks, and the characters used for quotation marks, often need to be escaped so that they are not misinterpreted.</span></span>

<span data-ttu-id="69dc9-248">Pour rechercher un utilisateur dont le nom comprend un guillemet simple, utilisez une barre oblique inverse pour échapper le guillemet simple, comme indiqué dans la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="69dc9-248">To find a user whose name includes a single quotation mark, use a backslash to escape the single quotation mark, as shown in the following command.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Name = 'Tim O\'Brian'"
Get-CimInstance -Query $q
```

```output
Name             Caption          AccountType      SID              Domain
----             -------          -----------      ---              ------
Tim O'Brian      FABRIKAM\TimO    512              S-1-5-21-1457... FABRIKAM
```

<span data-ttu-id="69dc9-249">Dans certains cas, la barre oblique inverse doit également être placée dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="69dc9-249">In some case, the backslash also needs to be escaped.</span></span> <span data-ttu-id="69dc9-250">Par exemple, les commandes suivantes génèrent une erreur de requête non valide en raison de la barre oblique inverse dans la valeur de légende.</span><span class="sxs-lookup"><span data-stu-id="69dc9-250">For example, the following commands generate an Invalid Query error due to the backslash in the Caption value.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\TimO'"
Get-CimInstance -Query $q
```

```output
Get-CimInstance : Invalid query
At line:1 char:1
+ Get-CimInstance -Query $q
+ ~~~~~~~~~~~
  + CategoryInfo          : InvalidArgument: (:) [Get-CimInstance], CimExcep
  + FullyQualifiedErrorId : HRESULT 0x80041017,Microsoft.Management.Infrastr
```

<span data-ttu-id="69dc9-251">Pour échapper à la barre oblique inverse, utilisez une deuxième barre oblique inverse, comme indiqué dans la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="69dc9-251">To escape the backslash, use a second backslash character, as shown in the following command.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\\TimO'"
Get-CimInstance -Query $q
```

## <a name="see-also"></a><span data-ttu-id="69dc9-252">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="69dc9-252">SEE ALSO</span></span>

[<span data-ttu-id="69dc9-253">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="69dc9-253">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="69dc9-254">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="69dc9-254">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="69dc9-255">about_WMI</span><span class="sxs-lookup"><span data-stu-id="69dc9-255">about_WMI</span></span>](about_WMI.md)

[<span data-ttu-id="69dc9-256">about_WMI_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="69dc9-256">about_WMI_Cmdlets</span></span>](about_WMI_Cmdlets.md)
