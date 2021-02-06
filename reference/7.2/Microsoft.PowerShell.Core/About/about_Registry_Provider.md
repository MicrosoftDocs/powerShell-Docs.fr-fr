---
description: Registre
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur Registry
ms.openlocfilehash: 2d57afc164885b4d207108a360215e63a5431632
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603459"
---
# <a name="registry-provider"></a><span data-ttu-id="f9414-103">Fournisseur de Registre</span><span class="sxs-lookup"><span data-stu-id="f9414-103">Registry provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="f9414-104">Nom du fournisseur</span><span class="sxs-lookup"><span data-stu-id="f9414-104">Provider name</span></span>

<span data-ttu-id="f9414-105">Registre</span><span class="sxs-lookup"><span data-stu-id="f9414-105">Registry</span></span>

## <a name="drives"></a><span data-ttu-id="f9414-106">Lecteurs</span><span class="sxs-lookup"><span data-stu-id="f9414-106">Drives</span></span>

<span data-ttu-id="f9414-107">`HKLM:`, `HKCU:`</span><span class="sxs-lookup"><span data-stu-id="f9414-107">`HKLM:`, `HKCU:`</span></span>

## <a name="capabilities"></a><span data-ttu-id="f9414-108">Fonctions</span><span class="sxs-lookup"><span data-stu-id="f9414-108">Capabilities</span></span>

<span data-ttu-id="f9414-109">**ShouldProcess**, **UseTransactions**</span><span class="sxs-lookup"><span data-stu-id="f9414-109">**ShouldProcess**, **UseTransactions**</span></span>

## <a name="short-description"></a><span data-ttu-id="f9414-110">Description courte</span><span class="sxs-lookup"><span data-stu-id="f9414-110">Short description</span></span>

<span data-ttu-id="f9414-111">Permet d’accéder aux clés, aux entrées et aux valeurs de Registre dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f9414-111">Provides access to the registry keys, entries, and values in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="f9414-112">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="f9414-112">Detailed description</span></span>

<span data-ttu-id="f9414-113">Le fournisseur **Registry** PowerShell vous permet d’extraire, d’ajouter, de modifier, d’effacer et de supprimer des clés, des entrées et des valeurs de Registre dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f9414-113">The PowerShell **Registry** provider lets you get, add, change, clear, and delete registry keys, entries, and values in PowerShell.</span></span>

<span data-ttu-id="f9414-114">Les lecteurs **du Registre** sont un espace de noms hiérarchique contenant les clés de Registre et les sous-clés de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f9414-114">The **Registry** drives are a hierarchical namespace containing the registry keys and subkeys on your computer.</span></span> <span data-ttu-id="f9414-115">Les entrées et les valeurs de Registre ne sont pas des composants de cette hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="f9414-115">Registry entries and values are not components of that hierarchy.</span></span> <span data-ttu-id="f9414-116">Ce sont en fait des propriétés de chacune des clés.</span><span class="sxs-lookup"><span data-stu-id="f9414-116">Instead, they are properties of each of the keys.</span></span>

<span data-ttu-id="f9414-117">Le fournisseur **Registry** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.</span><span class="sxs-lookup"><span data-stu-id="f9414-117">The **Registry** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="f9414-118">Get-Location</span><span class="sxs-lookup"><span data-stu-id="f9414-118">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="f9414-119">Set-Location</span><span class="sxs-lookup"><span data-stu-id="f9414-119">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="f9414-120">Get-Item</span><span class="sxs-lookup"><span data-stu-id="f9414-120">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="f9414-121">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="f9414-121">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="f9414-122">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="f9414-122">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="f9414-123">Move-Item</span><span class="sxs-lookup"><span data-stu-id="f9414-123">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="f9414-124">New-Item</span><span class="sxs-lookup"><span data-stu-id="f9414-124">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="f9414-125">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="f9414-125">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="f9414-126">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f9414-126">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="f9414-127">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f9414-127">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="f9414-128">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f9414-128">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="f9414-129">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f9414-129">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="f9414-130">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="f9414-130">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="f9414-131">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="f9414-131">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="f9414-132">Types exposés par ce fournisseur</span><span class="sxs-lookup"><span data-stu-id="f9414-132">Types exposed by this provider</span></span>

<span data-ttu-id="f9414-133">Les clés de Registre sont représentées en tant qu’instances de la classe [Microsoft. Win32. RegistryKey](/dotnet/api/microsoft.win32.registrykey) .</span><span class="sxs-lookup"><span data-stu-id="f9414-133">Registry keys are represented as instances of the [Microsoft.Win32.RegistryKey](/dotnet/api/microsoft.win32.registrykey) class.</span></span> <span data-ttu-id="f9414-134">Les entrées de Registre sont représentées en tant qu’instances de la classe [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) .</span><span class="sxs-lookup"><span data-stu-id="f9414-134">Registry entries are represented as instances of the [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) class.</span></span>

## <a name="navigating-the-registry-drives"></a><span data-ttu-id="f9414-135">Navigation dans les lecteurs de Registre</span><span class="sxs-lookup"><span data-stu-id="f9414-135">Navigating the Registry drives</span></span>

<span data-ttu-id="f9414-136">Le fournisseur de **Registre** expose son magasin de données comme deux lecteurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="f9414-136">The **Registry** provider exposes its data store as two default drives.</span></span> <span data-ttu-id="f9414-137">L’emplacement du Registre HKEY_LOCAL_MACHINE est mappé au `HKLM:` lecteur et HKEY_CURRENT_USER est mappé au `HKCU:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="f9414-137">The registry location HKEY_LOCAL_MACHINE is mapped to the `HKLM:` drive and HKEY_CURRENT_USER is mapped to the `HKCU:` drive.</span></span> <span data-ttu-id="f9414-138">Pour utiliser le registre, vous pouvez modifier votre emplacement sur le lecteur à l' `HKLM:` aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="f9414-138">To work with the registry, you can change your location to the `HKLM:` drive using the following command.</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="f9414-139">Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="f9414-139">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="f9414-140">Par exemple, entrez :</span><span class="sxs-lookup"><span data-stu-id="f9414-140">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="f9414-141">Vous pouvez également utiliser le fournisseur de **Registre** à partir de n’importe quel autre lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f9414-141">You can also work with the **Registry** provider from any other PowerShell drive.</span></span> <span data-ttu-id="f9414-142">Pour faire référence à une clé de Registre à partir d’un autre emplacement, utilisez le nom du lecteur ( `HKLM:` , `HKCU:` ) dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="f9414-142">To reference a registry key from another location, use the drive name (`HKLM:`, `HKCU:`) in the path.</span></span> <span data-ttu-id="f9414-143">Utilisez une barre oblique inverse ( \\ ) ou une barre oblique (/) pour indiquer un niveau du lecteur de **registre** .</span><span class="sxs-lookup"><span data-stu-id="f9414-143">Use a backslash (\\) or a forward slash (/) to indicate a level of the **Registry** drive.</span></span>

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> <span data-ttu-id="f9414-144">PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="f9414-144">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="f9414-145">Les commandes telles que `dir` et `ls` sont maintenant des alias pour [obtenir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location)et `pwd` est un alias pour la commande Set- [location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="f9414-145">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location), and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

<span data-ttu-id="f9414-146">Ce dernier exemple montre une autre syntaxe de chemin d’accès que vous pouvez utiliser pour naviguer dans le fournisseur de **Registre** .</span><span class="sxs-lookup"><span data-stu-id="f9414-146">This last example shows another path syntax you can use to navigate the **Registry** provider.</span></span> <span data-ttu-id="f9414-147">Cette syntaxe utilise le nom du fournisseur, suivi de deux signes deux-points `::` .</span><span class="sxs-lookup"><span data-stu-id="f9414-147">This syntax uses the provider name, followed by two colons `::`.</span></span> <span data-ttu-id="f9414-148">Cette syntaxe vous permet d’utiliser le nom de la ruche complète au lieu du nom du lecteur mappé `HKLM` .</span><span class="sxs-lookup"><span data-stu-id="f9414-148">This syntax allows you to use the full HIVE name, instead of the mapped drive name `HKLM`.</span></span>

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a><span data-ttu-id="f9414-149">Affichage du contenu des clés de Registre</span><span class="sxs-lookup"><span data-stu-id="f9414-149">Displaying the contents of registry keys</span></span>

<span data-ttu-id="f9414-150">Le Registre est divisé en clés, sous-clés et entrées.</span><span class="sxs-lookup"><span data-stu-id="f9414-150">The registry is divided into keys, subkeys, and entries.</span></span> <span data-ttu-id="f9414-151">Pour plus d’informations sur la structure du Registre, consultez [structure du Registre](/windows/desktop/sysinfo/structure-of-the-registry).</span><span class="sxs-lookup"><span data-stu-id="f9414-151">For more information about registry structure, see [Structure of the Registry](/windows/desktop/sysinfo/structure-of-the-registry).</span></span>

<span data-ttu-id="f9414-152">Dans un lecteur de **Registre** , chaque clé est un conteneur.</span><span class="sxs-lookup"><span data-stu-id="f9414-152">In a **Registry** drive, each key is a container.</span></span> <span data-ttu-id="f9414-153">Une clé peut contenir un nombre quelconque de clés.</span><span class="sxs-lookup"><span data-stu-id="f9414-153">A key can contain any number of keys.</span></span> <span data-ttu-id="f9414-154">Une clé de Registre qui a une clé parente est appelée une sous-clé.</span><span class="sxs-lookup"><span data-stu-id="f9414-154">A registry key that has a parent key is called a subkey.</span></span> <span data-ttu-id="f9414-155">Vous pouvez utiliser `Get-ChildItem` pour afficher les clés de Registre et `Set-Location` accéder à un chemin d’accès de clé.</span><span class="sxs-lookup"><span data-stu-id="f9414-155">You can use `Get-ChildItem` to view registry keys and `Set-Location` to navigate to a key path.</span></span>

<span data-ttu-id="f9414-156">Les valeurs de Registre sont des attributs d’une clé de registre.</span><span class="sxs-lookup"><span data-stu-id="f9414-156">Registry values are attributes of a registry key.</span></span> <span data-ttu-id="f9414-157">Dans le lecteur de **Registre** , elles sont appelées **propriétés d’élément**.</span><span class="sxs-lookup"><span data-stu-id="f9414-157">In the **Registry** drive, they are called **Item Properties**.</span></span> <span data-ttu-id="f9414-158">Une clé de Registre peut avoir à la fois des clés enfants et des propriétés d’élément.</span><span class="sxs-lookup"><span data-stu-id="f9414-158">A registry key can have both children keys and item properties.</span></span>

<span data-ttu-id="f9414-159">Dans cet exemple, la différence entre `Get-Item` et `Get-ChildItem` est indiquée.</span><span class="sxs-lookup"><span data-stu-id="f9414-159">In this example, the difference between `Get-Item` and `Get-ChildItem` is shown.</span></span> <span data-ttu-id="f9414-160">Lorsque vous utilisez `Get-Item` sur la clé de Registre « Spooler », vous pouvez afficher ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="f9414-160">When you use `Get-Item` on the "Spooler" registry key, you can view its properties.</span></span>

```
PS C:\ > Get-Item -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services


Name        Property
----        --------
Spooler     DependOnService    : {RPCSS, http}
            Description        : @%systemroot%\system32\spoolsv.exe,-2
            DisplayName        : @%systemroot%\system32\spoolsv.exe,-1
            ErrorControl       : 1
            FailureActions     : {16, 14, 0, 0...}
            Group              : SpoolerGroup
            ImagePath          : C:\WINDOWS\System32\spoolsv.exe
            ObjectName         : LocalSystem
            RequiredPrivileges : {SeTcbPrivilege, SeImpersonatePrivilege, ...
            ServiceSidType     : 1
            Start              : 2
            Type               : 27
```

<span data-ttu-id="f9414-161">Chaque clé de Registre peut également avoir des sous-clés.</span><span class="sxs-lookup"><span data-stu-id="f9414-161">Each registry key can also have subkeys.</span></span> <span data-ttu-id="f9414-162">Lorsque vous utilisez `Get-Item` sur une clé de Registre, les sous-clés ne sont pas affichées.</span><span class="sxs-lookup"><span data-stu-id="f9414-162">When you use `Get-Item` on a registry key, the subkeys are not displayed.</span></span> <span data-ttu-id="f9414-163">L' `Get-ChildItem` applet de commande affiche les éléments enfants de la clé « Spooler », y compris les propriétés de chaque sous-clé.</span><span class="sxs-lookup"><span data-stu-id="f9414-163">The `Get-ChildItem` cmdlet will show you children items of the "Spooler" key, including each subkey's properties.</span></span> <span data-ttu-id="f9414-164">Les propriétés de clés parentes ne sont pas affichées lors de l’utilisation de `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="f9414-164">The parent keys properties are not shown when using `Get-ChildItem`.</span></span>

```
PS C:\> Get-ChildItem -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler


Name             Property
----             --------
Performance      Close           : PerfClose
                 Collect         : PerfCollect
                 Collect Timeout : 2000
                 Library         : C:\Windows\System32\winspool.drv
                 Object List     : 1450
                 Open            : PerfOpen
                 Open Timeout    : 4000
Security         Security : {1, 0, 20, 128...}
```

<span data-ttu-id="f9414-165">L' `Get-Item` applet de commande peut également être utilisée à l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="f9414-165">The `Get-Item` cmdlet can also be used on the current location.</span></span> <span data-ttu-id="f9414-166">L’exemple suivant permet d’accéder à la clé de Registre « spooler » et d’obtenir les propriétés de l’élément.</span><span class="sxs-lookup"><span data-stu-id="f9414-166">The following example navigates to the "Spooler" registry key and gets the item properties.</span></span>
<span data-ttu-id="f9414-167">Le point `.` est utilisé pour indiquer l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="f9414-167">The dot `.` is used to indicate the current location.</span></span>

```
PS C:\> cd HKLM:\System\CurrentControlSet\Services\Spooler
PS HKLM:\SYSTEM\CurrentControlSet\Services\Spooler> Get-Item .

    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services

Name             Property
----             --------
Spooler          DependOnService    : {RPCSS, http}
                 Description        : @%systemroot%\system32\spoolsv.exe,-2
...
```

<span data-ttu-id="f9414-168">Pour plus d’informations sur les applets de commande décrites dans cette section, consultez les articles suivants.</span><span class="sxs-lookup"><span data-stu-id="f9414-168">For more information on the cmdlets covered in this section, see the following articles.</span></span>

<span data-ttu-id="f9414-169">-[Recevoir un élément](xref:Microsoft.PowerShell.Management.Get-Item) 
- [Acquérir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="f9414-169">-[Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
-[Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span></span>

## <a name="viewing-registry-key-values"></a><span data-ttu-id="f9414-170">Affichage des valeurs de clés de Registre</span><span class="sxs-lookup"><span data-stu-id="f9414-170">Viewing registry key values</span></span>

<span data-ttu-id="f9414-171">Les valeurs de clé de Registre sont stockées en tant que propriétés de chaque clé de registre.</span><span class="sxs-lookup"><span data-stu-id="f9414-171">Registry key values are stored as properties of each registry key.</span></span> <span data-ttu-id="f9414-172">L' `Get-ItemProperty` applet de commande affiche les propriétés de clé de registre en utilisant le nom que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="f9414-172">The `Get-ItemProperty` cmdlet views registry key properties using the name you specify.</span></span> <span data-ttu-id="f9414-173">Le résultat est un **PSCustomObject** contenant les propriétés que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="f9414-173">The result is a **PSCustomObject** containing the properties you specify.</span></span>

<span data-ttu-id="f9414-174">L’exemple suivant utilise l' `Get-ItemProperty` applet de commande pour afficher toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="f9414-174">The Following example uses the `Get-ItemProperty` cmdlet to view all properties.</span></span> <span data-ttu-id="f9414-175">Le stockage de l’objet résultant dans une variable vous permet d’accéder à la valeur de propriété souhaitée.</span><span class="sxs-lookup"><span data-stu-id="f9414-175">Storing the resulting object in a variable allows you to access the desired property value.</span></span>

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

<span data-ttu-id="f9414-176">La spécification d’une valeur pour le `-Name` paramètre sélectionne les propriétés que vous spécifiez et retourne **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="f9414-176">Specifying a value for the `-Name` parameter selects the properties you specify and returns the **PSCustomObject**.</span></span>  <span data-ttu-id="f9414-177">L’exemple suivant illustre la différence de sortie lorsque vous utilisez le `-Name` paramètre.</span><span class="sxs-lookup"><span data-stu-id="f9414-177">The following example shows the difference in output when you use the `-Name` parameter.</span></span>

```
PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem

BUILD                      : 17134.1
Installation Directory     : C:\WINDOWS\system32\WBEM
MOF Self-Install Directory : C:\WINDOWS\system32\WBEM\MOF
PSPath                     : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName                : Wbem
PSDrive                    : HKLM
PSProvider                 : Microsoft.PowerShell.Core\Registry

PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD

BUILD        : 17134.1
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName  : Wbem
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
```

<span data-ttu-id="f9414-178">À compter de PowerShell 5,0, l' `Get-ItemPropertyValue` applet de commande retourne uniquement la valeur de la propriété que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="f9414-178">Beginning in PowerShell 5.0, the `Get-ItemPropertyValue` cmdlet returns only the value of the property you specify.</span></span>

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

<span data-ttu-id="f9414-179">Pour plus d’informations sur les applets de commande utilisées dans cette section, consultez les articles suivants.</span><span class="sxs-lookup"><span data-stu-id="f9414-179">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="f9414-180">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f9414-180">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="f9414-181">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="f9414-181">Get-ItemPropertyValue</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a><span data-ttu-id="f9414-182">Modification des valeurs de clés de Registre</span><span class="sxs-lookup"><span data-stu-id="f9414-182">Changing registry key values</span></span>

<span data-ttu-id="f9414-183">L' `Set-ItemProperty` applet de commande définit les attributs des clés de registre.</span><span class="sxs-lookup"><span data-stu-id="f9414-183">The `Set-ItemProperty` cmdlet will set attributes for registry keys.</span></span> <span data-ttu-id="f9414-184">L’exemple suivant utilise `Set-ItemProperty` pour changer le type de démarrage du service Spooler en Manual.</span><span class="sxs-lookup"><span data-stu-id="f9414-184">The following example uses `Set-ItemProperty` to change the spooler service start type to manual.</span></span> <span data-ttu-id="f9414-185">L’exemple rétablit la valeur *automatique* **à l’aide** de l’applet de commande `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="f9414-185">The example changes the **StartType** back to *Automatic* using the `Set-Service` cmdlet.</span></span>

```
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler Automatic

PS C:\> $path = "HKLM:\SYSTEM\CurrentControlSet\Services\Spooler\"
PS C:\> Set-ItemProperty -Path $path -Name Start -Value 3
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler    Manual

PS C:\> Set-Service -Name Spooler -StartupType Automatic
```

<span data-ttu-id="f9414-186">Chaque clé de registre a une valeur *par défaut* .</span><span class="sxs-lookup"><span data-stu-id="f9414-186">Each registry key has a *default* value.</span></span> <span data-ttu-id="f9414-187">Vous pouvez modifier la valeur *par défaut* d’une clé de Registre à l’aide de `Set-Item` ou de `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="f9414-187">You can change the *default* value for a registry key with either `Set-Item` or `Set-ItemProperty`.</span></span>

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

<span data-ttu-id="f9414-188">Pour plus d’informations sur les applets de commande utilisées dans cette section, consultez les articles suivants.</span><span class="sxs-lookup"><span data-stu-id="f9414-188">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="f9414-189">Set-Item</span><span class="sxs-lookup"><span data-stu-id="f9414-189">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="f9414-190">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f9414-190">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a><span data-ttu-id="f9414-191">Création de clés et de valeurs de Registre</span><span class="sxs-lookup"><span data-stu-id="f9414-191">Creating registry keys and values</span></span>

<span data-ttu-id="f9414-192">L' `New-Item` applet de commande crée des clés de Registre avec un nom que vous fournissez.</span><span class="sxs-lookup"><span data-stu-id="f9414-192">The `New-Item` cmdlet will create registry keys with a name that you provide.</span></span>
<span data-ttu-id="f9414-193">Vous pouvez également utiliser la `mkdir` fonction, qui appelle l’applet de commande en `New-Item` interne.</span><span class="sxs-lookup"><span data-stu-id="f9414-193">You can also use the `mkdir` function, which calls the `New-Item` cmdlet internally.</span></span>

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

<span data-ttu-id="f9414-194">Vous pouvez utiliser l' `New-ItemProperty` applet de commande pour créer des valeurs dans une clé de registre que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="f9414-194">You can use the `New-ItemProperty` cmdlet to create values in a registry key that you specify.</span></span> <span data-ttu-id="f9414-195">L’exemple suivant crée une nouvelle valeur DWORD sur la clé de Registre ContosoCompany.</span><span class="sxs-lookup"><span data-stu-id="f9414-195">The following example creates a new DWORD value on the ContosoCompany registry key.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> <span data-ttu-id="f9414-196">Consultez la section paramètres dynamiques dans cet article pour connaître les autres valeurs de type autorisées.</span><span class="sxs-lookup"><span data-stu-id="f9414-196">Review the dynamic parameters section in this article for other allowed type values.</span></span>

<span data-ttu-id="f9414-197">Pour plus d’informations sur l’utilisation des applets de commande, consultez [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).</span><span class="sxs-lookup"><span data-stu-id="f9414-197">For detailed cmdlet usage, see [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).</span></span>

## <a name="copying-registry-keys-and-values"></a><span data-ttu-id="f9414-198">Copie des clés et des valeurs de Registre</span><span class="sxs-lookup"><span data-stu-id="f9414-198">Copying registry keys and values</span></span>

<span data-ttu-id="f9414-199">Dans le fournisseur de **Registre** , utilisez l’applet de commande pour `Copy-Item` copier les clés et les valeurs de registre.</span><span class="sxs-lookup"><span data-stu-id="f9414-199">In the **Registry** provider, use the `Copy-Item` cmdlet copies registry keys and values.</span></span> <span data-ttu-id="f9414-200">Utilisez l' `Copy-ItemProperty` applet de commande pour copier uniquement les valeurs de registre.</span><span class="sxs-lookup"><span data-stu-id="f9414-200">Use the `Copy-ItemProperty` cmdlet to copy registry values only.</span></span>
<span data-ttu-id="f9414-201">La commande suivante copie la clé de Registre « contoso » et ses propriétés à l’emplacement spécifié « HKLM : \ Software\Fabrikam ».</span><span class="sxs-lookup"><span data-stu-id="f9414-201">The following command copies the "Contoso" registry key, and its properties to the specified location "HKLM:\Software\Fabrikam".</span></span>

<span data-ttu-id="f9414-202">`Copy-Item` crée la clé de destination si elle n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="f9414-202">`Copy-Item` creates the destination key if it does not exist.</span></span> <span data-ttu-id="f9414-203">Si la clé de destination existe, `Copy-Item` crée un doublon de la clé source en tant qu’élément enfant (sous-clé) de la clé de destination.</span><span class="sxs-lookup"><span data-stu-id="f9414-203">If the destination key exists, `Copy-Item` creates a duplicate of the source key as a child item (subkey) of the destination key.</span></span>

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

<span data-ttu-id="f9414-204">La commande suivante utilise la `Copy-ItemProperty` cmdlet pour copier la valeur « Server » de la clé « contoso » sur la clé « fabrikam ».</span><span class="sxs-lookup"><span data-stu-id="f9414-204">The following command uses the `Copy-ItemProperty` cmdlet to copy the "Server" value from the "Contoso" key to the "Fabrikam" key.</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

<span data-ttu-id="f9414-205">Pour plus d’informations sur les applets de commande utilisées dans cette section, consultez les articles suivants.</span><span class="sxs-lookup"><span data-stu-id="f9414-205">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="f9414-206">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="f9414-206">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="f9414-207">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f9414-207">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a><span data-ttu-id="f9414-208">Déplacement des clés et des valeurs de Registre</span><span class="sxs-lookup"><span data-stu-id="f9414-208">Moving registry keys and values</span></span>

<span data-ttu-id="f9414-209">Les `Move-Item` applets de commande et `Move-ItemProperty` se comportent comme leurs équivalents « copie ».</span><span class="sxs-lookup"><span data-stu-id="f9414-209">The `Move-Item` and `Move-ItemProperty` cmdlets behave like their "Copy" counterparts.</span></span> <span data-ttu-id="f9414-210">Si la destination existe, `Move-Item` déplace la clé source sous la clé de destination.</span><span class="sxs-lookup"><span data-stu-id="f9414-210">If the destination exists, `Move-Item` moves the source key underneath the destination key.</span></span> <span data-ttu-id="f9414-211">Si la clé de destination n’existe pas, la clé source est déplacée vers le chemin d’accès de destination.</span><span class="sxs-lookup"><span data-stu-id="f9414-211">If the destination key does not exist, the source key is moved to the destination path.</span></span>

<span data-ttu-id="f9414-212">La commande suivante déplace la clé « contoso » sur le chemin d’accès « HKLM : \ SOFTWARE\Fabrikam ».</span><span class="sxs-lookup"><span data-stu-id="f9414-212">The following command moves the "Contoso" key to the path "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

<span data-ttu-id="f9414-213">Cette commande déplace toutes les propriétés de « HKLM : \ SOFTWARE\ContosoCompany » vers « HKLM : \ SOFTWARE\Fabrikam ».</span><span class="sxs-lookup"><span data-stu-id="f9414-213">This command moves all of the properties from "HKLM:\SOFTWARE\ContosoCompany" to "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

<span data-ttu-id="f9414-214">Pour plus d’informations sur les applets de commande utilisées dans cette section, consultez les articles suivants.</span><span class="sxs-lookup"><span data-stu-id="f9414-214">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="f9414-215">Move-Item</span><span class="sxs-lookup"><span data-stu-id="f9414-215">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="f9414-216">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f9414-216">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a><span data-ttu-id="f9414-217">Attribution d’un nouveau nom aux clés et valeurs de Registre</span><span class="sxs-lookup"><span data-stu-id="f9414-217">Renaming registry keys and values</span></span>

<span data-ttu-id="f9414-218">Vous pouvez renommer les clés et les valeurs de Registre comme vous le feriez avec des fichiers et des dossiers.</span><span class="sxs-lookup"><span data-stu-id="f9414-218">You can rename registry keys and values just like you would files and folders.</span></span>
<span data-ttu-id="f9414-219">`Rename-Item` renomme les clés de Registre, tout en `Rename-ItemProperty` renomme les valeurs de registre.</span><span class="sxs-lookup"><span data-stu-id="f9414-219">`Rename-Item` renames registry keys, while `Rename-ItemProperty` renames registry values.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a><span data-ttu-id="f9414-220">Modification des descripteurs de sécurité</span><span class="sxs-lookup"><span data-stu-id="f9414-220">Changing security descriptors</span></span>

<span data-ttu-id="f9414-221">Vous pouvez restreindre l’accès aux clés de Registre à l’aide des `Get-Acl` applets de commande et `Set-Acl` .</span><span class="sxs-lookup"><span data-stu-id="f9414-221">You can restrict access to registry keys using the `Get-Acl` and `Set-Acl` cmdlets.</span></span> <span data-ttu-id="f9414-222">L’exemple suivant ajoute un nouvel utilisateur avec un contrôle total à la clé de Registre « HKLM : \ SOFTWARE\Contoso ».</span><span class="sxs-lookup"><span data-stu-id="f9414-222">The following example adds a new user with full control to the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

<span data-ttu-id="f9414-223">Pour obtenir plus d’exemples et des détails sur l’utilisation des applets de commande, consultez les articles suivants.</span><span class="sxs-lookup"><span data-stu-id="f9414-223">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="f9414-224">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="f9414-224">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="f9414-225">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="f9414-225">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a><span data-ttu-id="f9414-226">Suppression et effacement des clés et des valeurs de Registre</span><span class="sxs-lookup"><span data-stu-id="f9414-226">Removing and clearing registry keys and values</span></span>

<span data-ttu-id="f9414-227">Vous pouvez supprimer des éléments contenus à l’aide de **Remove-Item**, mais vous serez invité à confirmer la suppression si l’élément contient autre chose.</span><span class="sxs-lookup"><span data-stu-id="f9414-227">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="f9414-228">L’exemple suivant tente de supprimer une clé « HKLM : \ SOFTWARE\Contoso ».</span><span class="sxs-lookup"><span data-stu-id="f9414-228">The following example attempts to delete a key "HKLM:\SOFTWARE\Contoso".</span></span>

```
PS C:\> dir HKLM:\SOFTWARE\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Contoso

Name                           Property
----                           --------
ChildKey

PS C:\> Remove-Item -Path HKLM:\SOFTWARE\Contoso

Confirm
The item at HKLM:\SOFTWARE\Contoso has children and the -Recurse
parameter was not specified. If you continue, all children will be removed
with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="f9414-229">Pour supprimer des éléments contenus sans demander confirmation, spécifiez le `-Recurse` paramètre.</span><span class="sxs-lookup"><span data-stu-id="f9414-229">To delete contained items without prompting, specify the `-Recurse` parameter.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

<span data-ttu-id="f9414-230">Si vous souhaitez supprimer tous les éléments dans « HKLM : \ SOFTWARE\Contoso », mais pas « HKLM : \ SOFTWARE\Contoso », utilisez une barre oblique inverse de fin `\` suivie d’un caractère générique.</span><span class="sxs-lookup"><span data-stu-id="f9414-230">If you wanted to remove all items within "HKLM:\SOFTWARE\Contoso" but not "HKLM:\SOFTWARE\Contoso" itself, use a trailing backslash `\` followed by a wildcard.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

<span data-ttu-id="f9414-231">Cette commande supprime la valeur de Registre « ContosoTest » de la clé de Registre « HKLM : \ SOFTWARE\Contoso ».</span><span class="sxs-lookup"><span data-stu-id="f9414-231">This command deletes the "ContosoTest" registry value from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

<span data-ttu-id="f9414-232">`Clear-Item` efface toutes les valeurs de Registre pour une clé.</span><span class="sxs-lookup"><span data-stu-id="f9414-232">`Clear-Item` clears all registry values for a key.</span></span> <span data-ttu-id="f9414-233">L’exemple suivant efface toutes les valeurs de la clé de Registre « HKLM : \ SOFTWARE\Contoso ».</span><span class="sxs-lookup"><span data-stu-id="f9414-233">The following example clears all values from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span> <span data-ttu-id="f9414-234">Pour effacer uniquement une propriété spécifique, utilisez `Clear-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="f9414-234">To clear only a specific property, use `Clear-ItemProperty`.</span></span>

```
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name           Property
----           --------
Contoso        Server     : {a, b, c}
               HereString : {This is text which contains
               newlines. It also contains "quoted" strings}
               (default)  : 1

PS HKLM:\SOFTWARE\> Clear-Item .\Contoso\
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
Contoso
```

<span data-ttu-id="f9414-235">Pour obtenir plus d’exemples et des détails sur l’utilisation des applets de commande, consultez les articles suivants.</span><span class="sxs-lookup"><span data-stu-id="f9414-235">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="f9414-236">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="f9414-236">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="f9414-237">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f9414-237">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="f9414-238">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="f9414-238">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="f9414-239">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f9414-239">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a><span data-ttu-id="f9414-240">Paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="f9414-240">Dynamic parameters</span></span>

<span data-ttu-id="f9414-241">Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés par un fournisseur PowerShell et sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur activé par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="f9414-241">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="type-microsoftwin32registryvaluekind"></a><span data-ttu-id="f9414-242">Tapez <Microsoft. Win32. RegistryValueKind figurant></span><span class="sxs-lookup"><span data-stu-id="f9414-242">Type <Microsoft.Win32.RegistryValueKind></span></span>

<span data-ttu-id="f9414-243">Établit ou change le type de données d'une valeur de Registre.</span><span class="sxs-lookup"><span data-stu-id="f9414-243">Establishes or changes the data type of a registry value.</span></span> <span data-ttu-id="f9414-244">La valeur par défaut est `String` (REG_SZ).</span><span class="sxs-lookup"><span data-stu-id="f9414-244">The default is `String` (REG_SZ).</span></span>

<span data-ttu-id="f9414-245">Ce paramètre fonctionne comme prévu sur l'applet de commande [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty).</span><span class="sxs-lookup"><span data-stu-id="f9414-245">This parameter works as designed on the [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet.</span></span> <span data-ttu-id="f9414-246">Il est également disponible sur l'applet de commande [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) dans les lecteurs de Registre, mais il n'a pas effet.</span><span class="sxs-lookup"><span data-stu-id="f9414-246">It is also available on the [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet in the registry drives, but it has no effect.</span></span>

|<span data-ttu-id="f9414-247">Value</span><span class="sxs-lookup"><span data-stu-id="f9414-247">Value</span></span> | <span data-ttu-id="f9414-248">Description</span><span class="sxs-lookup"><span data-stu-id="f9414-248">Description</span></span> |
| ---- | ----------- |
| `String` | <span data-ttu-id="f9414-249">Spécifie une chaîne terminée par NULL.</span><span class="sxs-lookup"><span data-stu-id="f9414-249">Specifies a null-terminated string.</span></span> <span data-ttu-id="f9414-250">Équivalent à REG_SZ.</span><span class="sxs-lookup"><span data-stu-id="f9414-250">Equivalent to REG_SZ.</span></span> |
| `ExpandString` | <span data-ttu-id="f9414-251">Spécifie une chaîne terminée par le caractère null qui contient un non développé</span><span class="sxs-lookup"><span data-stu-id="f9414-251">Specifies a null-terminated string that contains unexpanded</span></span> |
|                | <span data-ttu-id="f9414-252">références aux variables d’environnement qui sont développées quand</span><span class="sxs-lookup"><span data-stu-id="f9414-252">references to environment variables that are expanded when</span></span> |
|                | <span data-ttu-id="f9414-253">la valeur est récupérée.</span><span class="sxs-lookup"><span data-stu-id="f9414-253">the value is retrieved.</span></span> <span data-ttu-id="f9414-254">Équivalent à REG_EXPAND_SZ.</span><span class="sxs-lookup"><span data-stu-id="f9414-254">Equivalent to REG_EXPAND_SZ.</span></span> |
| `Binary` | <span data-ttu-id="f9414-255">Spécifie des données binaires sous n'importe quelle forme.</span><span class="sxs-lookup"><span data-stu-id="f9414-255">Specifies binary data in any form.</span></span> <span data-ttu-id="f9414-256">Équivalent à REG_BINARY.</span><span class="sxs-lookup"><span data-stu-id="f9414-256">Equivalent to REG_BINARY.</span></span> |
| `DWord` | <span data-ttu-id="f9414-257">Spécifie un nombre binaire de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="f9414-257">Specifies a 32-bit binary number.</span></span> <span data-ttu-id="f9414-258">Équivalent à REG_DWORD.</span><span class="sxs-lookup"><span data-stu-id="f9414-258">Equivalent to REG_DWORD.</span></span> |
| `MultiString` | <span data-ttu-id="f9414-259">Spécifie un tableau de chaînes terminées par le caractère null qui se sont terminées par</span><span class="sxs-lookup"><span data-stu-id="f9414-259">Specifies an array of null-terminated strings terminated by</span></span> |
|               | <span data-ttu-id="f9414-260">deux caractères null.</span><span class="sxs-lookup"><span data-stu-id="f9414-260">two null characters.</span></span> <span data-ttu-id="f9414-261">Équivalent à REG_MULTI_SZ.</span><span class="sxs-lookup"><span data-stu-id="f9414-261">Equivalent to REG_MULTI_SZ.</span></span> |
| `QWord` | <span data-ttu-id="f9414-262">Spécifie un nombre binaire de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="f9414-262">Specifies a 64-bit binary number.</span></span> <span data-ttu-id="f9414-263">Équivalent à REG_DWORD.</span><span class="sxs-lookup"><span data-stu-id="f9414-263">Equivalent to REG_QWORD.</span></span> |
| `Unknown` | <span data-ttu-id="f9414-264">Indique un type de données de Registre non pris en charge, tel que</span><span class="sxs-lookup"><span data-stu-id="f9414-264">Indicates an unsupported registry data type, such as</span></span> |
|           | <span data-ttu-id="f9414-265">REG_RESOURCE_LIST.</span><span class="sxs-lookup"><span data-stu-id="f9414-265">REG_RESOURCE_LIST.</span></span> |

#### <a name="cmdlets-supported"></a><span data-ttu-id="f9414-266">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="f9414-266">Cmdlets supported</span></span>

- [<span data-ttu-id="f9414-267">Set-Item</span><span class="sxs-lookup"><span data-stu-id="f9414-267">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="f9414-268">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f9414-268">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a><span data-ttu-id="f9414-269">Utilisation du pipeline</span><span class="sxs-lookup"><span data-stu-id="f9414-269">Using the pipeline</span></span>

<span data-ttu-id="f9414-270">Les applets de commande du fournisseur acceptent l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="f9414-270">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="f9414-271">Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="f9414-271">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span> <span data-ttu-id="f9414-272">Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.</span><span class="sxs-lookup"><span data-stu-id="f9414-272">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="f9414-273">Obtenir de l’aide</span><span class="sxs-lookup"><span data-stu-id="f9414-273">Getting help</span></span>

<span data-ttu-id="f9414-274">Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="f9414-274">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="f9414-275">Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une `Get-Help` commande sur un lecteur du système de fichiers ou utilisez le paramètre **path** pour spécifier un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="f9414-275">To get the help topics that are customized for the file system drive, run a `Get-Help` command in a file system drive or use the **Path** parameter to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a><span data-ttu-id="f9414-276">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9414-276">See also</span></span>

 [<span data-ttu-id="f9414-277">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f9414-277">about_Providers</span></span>](../About/about_Providers.md)

