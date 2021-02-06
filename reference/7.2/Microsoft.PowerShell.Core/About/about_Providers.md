---
description: Décrit comment les fournisseurs PowerShell fournissent un accès aux données et aux composants qui ne seraient pas facilement accessibles à partir de la ligne de commande. Les données sont présentées dans un format cohérent qui ressemble à un lecteur du système de fichiers.
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: 6073ef13a6d0a02cded69073d7ffaef903a807ea
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596925"
---
# <a name="about-providers"></a><span data-ttu-id="10d06-104">À propos des fournisseurs</span><span class="sxs-lookup"><span data-stu-id="10d06-104">About Providers</span></span>

## <a name="short-description"></a><span data-ttu-id="10d06-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="10d06-105">Short description</span></span>
<span data-ttu-id="10d06-106">Décrit comment les fournisseurs PowerShell fournissent un accès aux données et aux composants qui ne seraient pas facilement accessibles à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="10d06-106">Describes how PowerShell providers provide access to data and components that wouldn't otherwise be easily accessible at the command line.</span></span>
<span data-ttu-id="10d06-107">Les données sont présentées dans un format cohérent qui ressemble à un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="10d06-107">The data is presented in a consistent format that resembles a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="10d06-108">Description longue</span><span class="sxs-lookup"><span data-stu-id="10d06-108">Long description</span></span>

<span data-ttu-id="10d06-109">Les fournisseurs PowerShell sont des programmes .NET qui fournissent un accès à des magasins de données spécialisés pour faciliter l’affichage et la gestion.</span><span class="sxs-lookup"><span data-stu-id="10d06-109">PowerShell providers are .NET programs that provide access to specialized data stores for easier viewing and management.</span></span> <span data-ttu-id="10d06-110">Les données apparaissent dans un lecteur, et vous accédez aux données dans un chemin d’accès comme sur un lecteur de disque dur.</span><span class="sxs-lookup"><span data-stu-id="10d06-110">The data appears in a drive, and you access the data in a path like you would on a hard disk drive.</span></span> <span data-ttu-id="10d06-111">Vous pouvez utiliser l’une des applets de commande intégrées que le fournisseur prend en charge pour gérer les données dans le lecteur du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="10d06-111">You can use any of the built-in cmdlets that the provider supports to manage the data in the provider drive.</span></span> <span data-ttu-id="10d06-112">De plus, vous pouvez utiliser des applets de commande personnalisées conçues spécialement pour les données.</span><span class="sxs-lookup"><span data-stu-id="10d06-112">And, you can use custom cmdlets that are designed especially for the data.</span></span>

<span data-ttu-id="10d06-113">Les fournisseurs peuvent également ajouter des paramètres dynamiques aux applets de commande intégrées.</span><span class="sxs-lookup"><span data-stu-id="10d06-113">The providers can also add dynamic parameters to the built-in cmdlets.</span></span> <span data-ttu-id="10d06-114">Ces paramètres sont disponibles uniquement lorsque vous utilisez l’applet de commande avec les données du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="10d06-114">These parameters are only available when you use the cmdlet with the provider data.</span></span>

## <a name="built-in-providers"></a><span data-ttu-id="10d06-115">Fournisseurs intégrés</span><span class="sxs-lookup"><span data-stu-id="10d06-115">Built-in providers</span></span>

<span data-ttu-id="10d06-116">PowerShell comprend un ensemble de fournisseurs intégrés que vous pouvez utiliser pour accéder aux différents types de magasins de données.</span><span class="sxs-lookup"><span data-stu-id="10d06-116">PowerShell includes a set of built-in providers that you can use to access the different types of data stores.</span></span>

| <span data-ttu-id="10d06-117">Fournisseur</span><span class="sxs-lookup"><span data-stu-id="10d06-117">Provider</span></span>   |   <span data-ttu-id="10d06-118">Lecteur (s)</span><span class="sxs-lookup"><span data-stu-id="10d06-118">Drive(s)</span></span>  |<span data-ttu-id="10d06-119">OutputType</span><span class="sxs-lookup"><span data-stu-id="10d06-119">OutputType</span></span>                                                    |
|----------- |------------ |--------------------------------------------------------------|
|<span data-ttu-id="10d06-120">Alias</span><span class="sxs-lookup"><span data-stu-id="10d06-120">Alias</span></span>       |<span data-ttu-id="10d06-121">Alias:</span><span class="sxs-lookup"><span data-stu-id="10d06-121">Alias:</span></span>       |<span data-ttu-id="10d06-122">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="10d06-122">System.Management.Automation.AliasInfo</span></span>                        |
|<span data-ttu-id="10d06-123">Certificat</span><span class="sxs-lookup"><span data-stu-id="10d06-123">Certificate</span></span> |<span data-ttu-id="10d06-124">Cert:</span><span class="sxs-lookup"><span data-stu-id="10d06-124">Cert:</span></span>        |<span data-ttu-id="10d06-125">Microsoft. PowerShell. Commands. X509StoreLocation</span><span class="sxs-lookup"><span data-stu-id="10d06-125">Microsoft.PowerShell.Commands.X509StoreLocation</span></span>               |
|            |             |<span data-ttu-id="10d06-126">System.Security.Cryptography.X509Certificates.X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="10d06-126">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>|
|<span data-ttu-id="10d06-127">Environnement</span><span class="sxs-lookup"><span data-stu-id="10d06-127">Environment</span></span> |<span data-ttu-id="10d06-128">Env:</span><span class="sxs-lookup"><span data-stu-id="10d06-128">Env:</span></span>         |<span data-ttu-id="10d06-129">System. Collections. DictionaryEntry</span><span class="sxs-lookup"><span data-stu-id="10d06-129">System.Collections.DictionaryEntry</span></span>                            |
|<span data-ttu-id="10d06-130">FileSystem</span><span class="sxs-lookup"><span data-stu-id="10d06-130">FileSystem</span></span>  |<span data-ttu-id="10d06-131">C : (\*)</span><span class="sxs-lookup"><span data-stu-id="10d06-131">C: (\*)</span></span>       |<span data-ttu-id="10d06-132">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="10d06-132">System.IO.FileInfo</span></span>                                            |
|            |             |<span data-ttu-id="10d06-133">System. IO. DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="10d06-133">System.IO.DirectoryInfo</span></span>                                       |
|<span data-ttu-id="10d06-134">Fonction</span><span class="sxs-lookup"><span data-stu-id="10d06-134">Function</span></span>    |<span data-ttu-id="10d06-135">Fonction :</span><span class="sxs-lookup"><span data-stu-id="10d06-135">Function:</span></span>    |<span data-ttu-id="10d06-136">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="10d06-136">System.Management.Automation.FunctionInfo</span></span>                     |
|<span data-ttu-id="10d06-137">Registre</span><span class="sxs-lookup"><span data-stu-id="10d06-137">Registry</span></span>    |<span data-ttu-id="10d06-138">HKLM : HKCU :</span><span class="sxs-lookup"><span data-stu-id="10d06-138">HKLM: HKCU:</span></span>  |<span data-ttu-id="10d06-139">Microsoft. Win32. RegistryKey</span><span class="sxs-lookup"><span data-stu-id="10d06-139">Microsoft.Win32.RegistryKey</span></span>                                   |
|<span data-ttu-id="10d06-140">Variable</span><span class="sxs-lookup"><span data-stu-id="10d06-140">Variable</span></span>    |<span data-ttu-id="10d06-141">Variable :</span><span class="sxs-lookup"><span data-stu-id="10d06-141">Variable:</span></span>    |<span data-ttu-id="10d06-142">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="10d06-142">System.Management.Automation.PSVariable</span></span>                       |
|<span data-ttu-id="10d06-143">WSMan</span><span class="sxs-lookup"><span data-stu-id="10d06-143">WSMan</span></span>       |<span data-ttu-id="10d06-144">WSMan :</span><span class="sxs-lookup"><span data-stu-id="10d06-144">WSMan:</span></span>       |<span data-ttu-id="10d06-145">Microsoft. WSMan. Management. WSManConfigContainerElement</span><span class="sxs-lookup"><span data-stu-id="10d06-145">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>        |

<span data-ttu-id="10d06-146">(\*) Les lecteurs de système de fichiers varient en fonction de chaque système.</span><span class="sxs-lookup"><span data-stu-id="10d06-146">(\*) The FileSystem drives vary on each system.</span></span>

<span data-ttu-id="10d06-147">Vous pouvez également créer vos propres fournisseurs PowerShell, et vous pouvez installer des fournisseurs développés par d’autres.</span><span class="sxs-lookup"><span data-stu-id="10d06-147">You can also create your own PowerShell providers, and you can install providers that others develop.</span></span> <span data-ttu-id="10d06-148">Pour répertorier les fournisseurs disponibles dans votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="10d06-148">To list the providers that are available in your session, type:</span></span>

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a><span data-ttu-id="10d06-149">Installation et suppression de fournisseurs</span><span class="sxs-lookup"><span data-stu-id="10d06-149">Installing and removing providers</span></span>

<span data-ttu-id="10d06-150">Les fournisseurs sont généralement installés via des modules PowerShell.</span><span class="sxs-lookup"><span data-stu-id="10d06-150">Providers are typically installed via PowerShell modules.</span></span> <span data-ttu-id="10d06-151">L’importation du module charge le fournisseur dans votre session.</span><span class="sxs-lookup"><span data-stu-id="10d06-151">Importing the module loads the provider into your session.</span></span> <span data-ttu-id="10d06-152">Vous ne pouvez pas désinstaller les fournisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="10d06-152">You can't uninstall the built-in providers.</span></span> <span data-ttu-id="10d06-153">Vous pouvez désinstaller des fournisseurs chargés par d’autres modules.</span><span class="sxs-lookup"><span data-stu-id="10d06-153">You can uninstall providers loaded by other modules.</span></span>

<span data-ttu-id="10d06-154">Vous pouvez décharger un fournisseur de la session active à l’aide de l’applet de commande `Remove-Module` .</span><span class="sxs-lookup"><span data-stu-id="10d06-154">You can unload a provider from the current session using the `Remove-Module` cmdlet.</span></span> <span data-ttu-id="10d06-155">Cette applet de commande ne désinstalle pas le fournisseur, mais le fournisseur n’est pas disponible dans la session.</span><span class="sxs-lookup"><span data-stu-id="10d06-155">This cmdlet doesn't uninstall the provider, but it makes the provider unavailable in the session.</span></span>

<span data-ttu-id="10d06-156">Vous pouvez également utiliser l' `Remove-PSDrive` applet de commande pour supprimer un lecteur de la session active.</span><span class="sxs-lookup"><span data-stu-id="10d06-156">You can also use the `Remove-PSDrive` cmdlet to remove any drive from the current session.</span></span> <span data-ttu-id="10d06-157">Ces données sur le lecteur ne sont pas affectées, mais le lecteur n’est plus disponible dans cette session.</span><span class="sxs-lookup"><span data-stu-id="10d06-157">This data on the drive isn't affected, but the drive is no longer available in that session.</span></span>

## <a name="viewing-providers"></a><span data-ttu-id="10d06-158">Affichage des fournisseurs</span><span class="sxs-lookup"><span data-stu-id="10d06-158">Viewing providers</span></span>

<span data-ttu-id="10d06-159">Pour afficher les fournisseurs PowerShell sur votre ordinateur, tapez :</span><span class="sxs-lookup"><span data-stu-id="10d06-159">To view the PowerShell providers on your computer, type:</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="10d06-160">La sortie répertorie les fournisseurs intégrés et les fournisseurs que vous avez ajoutés à la session.</span><span class="sxs-lookup"><span data-stu-id="10d06-160">The output lists the built-in providers and the providers that you added to the session.</span></span>

## <a name="the-provider-cmdlets"></a><span data-ttu-id="10d06-161">Applets de commande du fournisseur</span><span class="sxs-lookup"><span data-stu-id="10d06-161">The provider cmdlets</span></span>

<span data-ttu-id="10d06-162">Les applets de commande suivantes sont conçues pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="10d06-162">The following cmdlets are designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="10d06-163">Vous pouvez utiliser les mêmes cmdlets de la même façon pour gérer les différents types de données que les fournisseurs exposent.</span><span class="sxs-lookup"><span data-stu-id="10d06-163">You can use the same cmdlets in the same way to manage the different types of data that providers expose.</span></span> <span data-ttu-id="10d06-164">Une fois que vous avez appris à gérer les données d’un fournisseur, vous pouvez utiliser les mêmes procédures avec les données de n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="10d06-164">After you learn to manage the data of one provider, you can use the same procedures with the data from any provider.</span></span>

<span data-ttu-id="10d06-165">Par exemple, l' `New-Item` applet de commande crée un nouvel élément.</span><span class="sxs-lookup"><span data-stu-id="10d06-165">For example, the `New-Item` cmdlet creates a new item.</span></span> <span data-ttu-id="10d06-166">Dans le `C:` lecteur pris en charge par le fournisseur **FileSystem** , vous pouvez utiliser `New-Item` pour créer un nouveau fichier ou dossier.</span><span class="sxs-lookup"><span data-stu-id="10d06-166">In the `C:` drive that is supported by the **FileSystem** provider, you can use `New-Item` to create a new file or folder.</span></span> <span data-ttu-id="10d06-167">Dans les lecteurs pris en charge par le fournisseur de **Registre** , vous pouvez utiliser `New-Item` pour créer une nouvelle clé de registre.</span><span class="sxs-lookup"><span data-stu-id="10d06-167">In the drives that are supported by the **Registry** provider, you can use `New-Item` to create a new registry key.</span></span> <span data-ttu-id="10d06-168">Dans le `Alias:` lecteur, vous pouvez utiliser `New-Item` pour créer un nouvel alias.</span><span class="sxs-lookup"><span data-stu-id="10d06-168">In the `Alias:` drive, you can use `New-Item` to create a new alias.</span></span>

<span data-ttu-id="10d06-169">Pour obtenir des informations détaillées sur les applets de commande suivantes, tapez :</span><span class="sxs-lookup"><span data-stu-id="10d06-169">For detailed information about any of the following cmdlets, type:</span></span>

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a><span data-ttu-id="10d06-170">Applets de commande ChildItem</span><span class="sxs-lookup"><span data-stu-id="10d06-170">ChildItem cmdlets</span></span>

- [<span data-ttu-id="10d06-171">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="10d06-171">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a><span data-ttu-id="10d06-172">Applets de commande de contenu</span><span class="sxs-lookup"><span data-stu-id="10d06-172">Content Cmdlets</span></span>

- [<span data-ttu-id="10d06-173">Add-Content</span><span class="sxs-lookup"><span data-stu-id="10d06-173">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="10d06-174">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="10d06-174">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="10d06-175">Get-Content</span><span class="sxs-lookup"><span data-stu-id="10d06-175">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="10d06-176">Set-Content</span><span class="sxs-lookup"><span data-stu-id="10d06-176">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a><span data-ttu-id="10d06-177">Applets de commande Item</span><span class="sxs-lookup"><span data-stu-id="10d06-177">Item Cmdlets</span></span>

- [<span data-ttu-id="10d06-178">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="10d06-178">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="10d06-179">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="10d06-179">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="10d06-180">Get-Item</span><span class="sxs-lookup"><span data-stu-id="10d06-180">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="10d06-181">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="10d06-181">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="10d06-182">Move-Item</span><span class="sxs-lookup"><span data-stu-id="10d06-182">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="10d06-183">New-Item</span><span class="sxs-lookup"><span data-stu-id="10d06-183">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="10d06-184">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="10d06-184">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="10d06-185">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="10d06-185">Rename-Item</span></span>](xref:Microsoft.PowerShell.Management.Rename-Item)
- [<span data-ttu-id="10d06-186">Set-Item</span><span class="sxs-lookup"><span data-stu-id="10d06-186">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a><span data-ttu-id="10d06-187">Applets de commande ItemProperty</span><span class="sxs-lookup"><span data-stu-id="10d06-187">ItemProperty cmdlets</span></span>

- [<span data-ttu-id="10d06-188">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="10d06-188">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="10d06-189">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="10d06-189">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [<span data-ttu-id="10d06-190">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="10d06-190">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="10d06-191">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="10d06-191">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [<span data-ttu-id="10d06-192">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="10d06-192">New-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [<span data-ttu-id="10d06-193">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="10d06-193">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="10d06-194">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="10d06-194">Rename-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [<span data-ttu-id="10d06-195">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="10d06-195">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a><span data-ttu-id="10d06-196">Applets de commande Location</span><span class="sxs-lookup"><span data-stu-id="10d06-196">Location cmdlets</span></span>

- [<span data-ttu-id="10d06-197">Get-Location</span><span class="sxs-lookup"><span data-stu-id="10d06-197">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="10d06-198">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="10d06-198">Pop-Location</span></span>](xref:Microsoft.PowerShell.Management.Pop-Location)
- [<span data-ttu-id="10d06-199">Push-Location</span><span class="sxs-lookup"><span data-stu-id="10d06-199">Push-Location</span></span>](xref:Microsoft.PowerShell.Management.Push-Location)
- [<span data-ttu-id="10d06-200">Set-Location</span><span class="sxs-lookup"><span data-stu-id="10d06-200">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a><span data-ttu-id="10d06-201">Applets de commande Path</span><span class="sxs-lookup"><span data-stu-id="10d06-201">Path cmdlets</span></span>

- [<span data-ttu-id="10d06-202">Join-Path</span><span class="sxs-lookup"><span data-stu-id="10d06-202">Join-Path</span></span>](xref:Microsoft.PowerShell.Management.Join-Path)
- [<span data-ttu-id="10d06-203">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="10d06-203">Convert-Path</span></span>](xref:Microsoft.PowerShell.Management.Convert-Path)
- [<span data-ttu-id="10d06-204">Split-Path</span><span class="sxs-lookup"><span data-stu-id="10d06-204">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)
- [<span data-ttu-id="10d06-205">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="10d06-205">Resolve-Path</span></span>](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [<span data-ttu-id="10d06-206">Test-Path</span><span class="sxs-lookup"><span data-stu-id="10d06-206">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a><span data-ttu-id="10d06-207">PSDrive, applets de commande</span><span class="sxs-lookup"><span data-stu-id="10d06-207">PSDrive cmdlets</span></span>

- [<span data-ttu-id="10d06-208">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="10d06-208">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="10d06-209">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="10d06-209">New-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [<span data-ttu-id="10d06-210">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="10d06-210">Remove-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a><span data-ttu-id="10d06-211">Applets de commande PSProvider</span><span class="sxs-lookup"><span data-stu-id="10d06-211">PSProvider Cmdlets</span></span>

- [<span data-ttu-id="10d06-212">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="10d06-212">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a><span data-ttu-id="10d06-213">Affichage des données du fournisseur</span><span class="sxs-lookup"><span data-stu-id="10d06-213">Viewing provider data</span></span>

<span data-ttu-id="10d06-214">Le principal avantage d’un fournisseur est qu’il expose ses données de manière familière et cohérente.</span><span class="sxs-lookup"><span data-stu-id="10d06-214">The primary benefit of a provider is that it exposes its data in a familiar and consistent way.</span></span> <span data-ttu-id="10d06-215">Le modèle de présentation des données est un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="10d06-215">The model for data presentation is a file system drive.</span></span>

<span data-ttu-id="10d06-216">Le fournisseur vous permet d’afficher, de parcourir et de modifier des éléments dans le magasin de données comme s’il s’agissait de données dans un système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="10d06-216">The provider allows you to view, navigate, and change items in the data store as though they were data in a file system.</span></span> <span data-ttu-id="10d06-217">Le magasin de données est accessible par le nom du lecteur qu’il prend en charge.</span><span class="sxs-lookup"><span data-stu-id="10d06-217">The data store is accessed by the name of the drive that it supports.</span></span>

<span data-ttu-id="10d06-218">Le lecteur est indiqué dans l’affichage par défaut de l’applet de commande `Get-PSProvider` , mais vous pouvez obtenir des informations sur le lecteur du fournisseur à l’aide de l’applet de commande `Get-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="10d06-218">The drive is listed in the default display of the `Get-PSProvider` cmdlet, but you can get information about the provider drive using the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="10d06-219">Par exemple, pour obtenir toutes les propriétés du lecteur function :, tapez :</span><span class="sxs-lookup"><span data-stu-id="10d06-219">For example, to get all the properties of the Function: drive, type:</span></span>

```powershell
Get-PSDrive Function | Format-List *
```

<span data-ttu-id="10d06-220">Vous pouvez afficher et parcourir les données d’un lecteur du fournisseur comme vous le feriez sur un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="10d06-220">You can view and move through the data in a provider drive just as you would on a file system drive.</span></span>

<span data-ttu-id="10d06-221">Pour afficher le contenu d’un lecteur de fournisseur, utilisez les applets de commande Get-Item ou Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="10d06-221">To view the contents of a provider drive, use the Get-Item or Get-ChildItem cmdlets.</span></span> <span data-ttu-id="10d06-222">Tapez le nom du lecteur suivi d’un signe deux-points ( :).</span><span class="sxs-lookup"><span data-stu-id="10d06-222">Type the drive name followed by a colon (:).</span></span> <span data-ttu-id="10d06-223">Par exemple, pour afficher le contenu du lecteur Alias :, tapez :</span><span class="sxs-lookup"><span data-stu-id="10d06-223">For example, to view the contents of the Alias: drive, type:</span></span>

```powershell
Get-Item alias:
```

<span data-ttu-id="10d06-224">Vous pouvez afficher et gérer les données de n’importe quel lecteur à partir d’un autre lecteur en incluant le nom du lecteur dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="10d06-224">You can view and manage the data in any drive from another drive by including the drive name in the path.</span></span> <span data-ttu-id="10d06-225">Par exemple, pour afficher la clé de Registre HKLM\Software dans le lecteur HKLM : à partir d’un autre lecteur, tapez :</span><span class="sxs-lookup"><span data-stu-id="10d06-225">For example, to view the HKLM\Software registry key in the HKLM: drive from another drive, type:</span></span>

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

<span data-ttu-id="10d06-226">Pour ouvrir le lecteur, utilisez l’applet de commande Set-Location.</span><span class="sxs-lookup"><span data-stu-id="10d06-226">To open the drive, use the Set-Location cmdlet.</span></span> <span data-ttu-id="10d06-227">N’oubliez pas le signe deux-points lorsque vous spécifiez le chemin d’accès au lecteur.</span><span class="sxs-lookup"><span data-stu-id="10d06-227">Remember the colon when you specify the drive path.</span></span> <span data-ttu-id="10d06-228">Par exemple, pour remplacer votre emplacement par le répertoire racine du lecteur Cert :, tapez :</span><span class="sxs-lookup"><span data-stu-id="10d06-228">For example, to change your location to the root directory of the Cert: drive, type:</span></span>

```powershell
Set-Location cert:
```

<span data-ttu-id="10d06-229">Ensuite, pour afficher le contenu du lecteur Cert :, tapez :</span><span class="sxs-lookup"><span data-stu-id="10d06-229">Then, to view the contents of the Cert: drive, type:</span></span>

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a><span data-ttu-id="10d06-230">Déplacement dans des données hiérarchiques</span><span class="sxs-lookup"><span data-stu-id="10d06-230">Moving through hierarchical data</span></span>

<span data-ttu-id="10d06-231">Vous pouvez vous déplacer dans un lecteur du fournisseur comme vous le feriez pour un lecteur de disque dur.</span><span class="sxs-lookup"><span data-stu-id="10d06-231">You can move through a provider drive just as you would a hard disk drive.</span></span>
<span data-ttu-id="10d06-232">Si les données sont organisées dans une hiérarchie d’éléments dans les éléments, utilisez une barre oblique inverse ( `\` ) pour indiquer un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="10d06-232">If the data is arranged in a hierarchy of items within items, use a backslash (`\`) to indicate a child item.</span></span> <span data-ttu-id="10d06-233">Utilisez le format suivant :</span><span class="sxs-lookup"><span data-stu-id="10d06-233">Use the following format:</span></span>

```
drive:\location\child-location\...
```

<span data-ttu-id="10d06-234">Par exemple, pour modifier l’emplacement de la clé de Registre HKLM\Software, tapez une commande Set-Location, par exemple :</span><span class="sxs-lookup"><span data-stu-id="10d06-234">For example, to change your location to the HKLM\Software registry key, type a Set-Location command, such as:</span></span>

```powershell
Set-Location HKLM:\SOFTWARE\
```

<span data-ttu-id="10d06-235">Si un élément du nom complet comprend des espaces, vous devez placer le nom entre guillemets doubles ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="10d06-235">If any element in the fully qualified name includes spaces, you must enclose the name in double-quotation marks (`"`).</span></span> <span data-ttu-id="10d06-236">L’exemple suivant montre un chemin d’accès complet qui comprend des espaces.</span><span class="sxs-lookup"><span data-stu-id="10d06-236">The following example shows a fully qualified path that includes spaces.</span></span>

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

<span data-ttu-id="10d06-237">Vous pouvez également utiliser des références relatives à des emplacements.</span><span class="sxs-lookup"><span data-stu-id="10d06-237">You can also use relative references to locations.</span></span> <span data-ttu-id="10d06-238">Un point ( `.` ) représente l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="10d06-238">A dot (`.`) represents the current location.</span></span> <span data-ttu-id="10d06-239">Par exemple, si vous êtes dans la `HKLM:\Software\Microsoft` clé de Registre et que vous souhaitez répertorier les sous-clés de Registre dans la `HKLM:\Software\Microsoft\PowerShell` clé, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="10d06-239">For example, if you are in the `HKLM:\Software\Microsoft` registry key, and you want to list the registry subkeys in the `HKLM:\Software\Microsoft\PowerShell` key, type the following command:</span></span>

```powershell
Get-ChildItem .\PowerShell
```

<span data-ttu-id="10d06-240">En outre, les doubles points ( `..` ) font référence au répertoire ou au conteneur situé juste au-dessus de votre emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="10d06-240">Also, double-dots (`..`) refers to the directory or container directly above your current location.</span></span> <span data-ttu-id="10d06-241">Vous pouvez utiliser des points doubles ( `..` ) pour naviguer dans une hiérarchie de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="10d06-241">You can use double-dots (`..`) to navigate through a provider hierarchy.</span></span>

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a><span data-ttu-id="10d06-242">Page d’hébergement du fournisseur</span><span class="sxs-lookup"><span data-stu-id="10d06-242">Provider Home</span></span>

<span data-ttu-id="10d06-243">Les fournisseurs disposent également d’un emplacement d' **hébergement** .</span><span class="sxs-lookup"><span data-stu-id="10d06-243">Providers also have a **Home** location.</span></span>  <span data-ttu-id="10d06-244">Cet emplacement est partagé par `PSDrives` le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="10d06-244">This location is shared by all `PSDrives` backed by the provider.</span></span> <span data-ttu-id="10d06-245">Il peut être récupéré en affichant la propriété de **démarrage** du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="10d06-245">It can be retrieved by viewing the **Home** property of the provider.</span></span>

```powershell
Get-PSProvider | Format-Table Name, Home
```

```Output
Name        Home
----        ----
Registry
Alias
Environment
FileSystem  C:\Users\username
Function
Variable
Certificate
```

<span data-ttu-id="10d06-246">Le fournisseur **FileSystem** est le seul fournisseur qui a une valeur par défaut pour la **page d’hébergement**.</span><span class="sxs-lookup"><span data-stu-id="10d06-246">The **FileSystem** provider is the only provider that has a default value for **Home**.</span></span> <span data-ttu-id="10d06-247">Il s’agit de la même valeur que `$Home` .</span><span class="sxs-lookup"><span data-stu-id="10d06-247">It's the same value as `$Home`.</span></span> <span data-ttu-id="10d06-248">Pour plus d’informations, consultez [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="10d06-248">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="10d06-249">Vous pouvez définir le répertoire de **départ** pour un fournisseur, pour la session active, à l’aide de sa propriété.</span><span class="sxs-lookup"><span data-stu-id="10d06-249">You can set the **Home** directory for a provider, for the current session, using its property.</span></span>

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

<span data-ttu-id="10d06-250">Le `~` caractère peut être utilisé pour représenter le répertoire de départ du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="10d06-250">The `~` character can be used to represent the provider's home directory.</span></span>
<span data-ttu-id="10d06-251">Si le fournisseur n’a pas d’emplacement de **départ** défini, une erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="10d06-251">If the provider doesn't have a **Home** location set, you see an error.</span></span>

```powershell
Cert:\> Set-Location ~
```

```Output
Set-Location : Home location for this provider isn't set. To set the home
location, call "(get-psprovider 'Certificate').Home = 'path'".
At line:1 char:1
+ Set-Location ~
+ ~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Set-Location],
                              PSInvalidOperationException
...
```

## <a name="finding-dynamic-parameters"></a><span data-ttu-id="10d06-252">Recherche de paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="10d06-252">Finding dynamic parameters</span></span>

<span data-ttu-id="10d06-253">Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés à une applet de commande par un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="10d06-253">Dynamic parameters are cmdlet parameters that are added to a cmdlet by a provider.</span></span> <span data-ttu-id="10d06-254">Ces paramètres sont disponibles uniquement lorsque l’applet de commande est utilisée avec le fournisseur qui les a ajoutés.</span><span class="sxs-lookup"><span data-stu-id="10d06-254">These parameters are available only when the cmdlet is used with the provider that added them.</span></span>

<span data-ttu-id="10d06-255">Par exemple, le `Cert:` lecteur ajoute le paramètre **CodeSigningCert** aux `Get-Item` applets de commande et `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="10d06-255">For example, the `Cert:` drive adds the **CodeSigningCert** parameter to the `Get-Item` and `Get-ChildItem` cmdlets.</span></span> <span data-ttu-id="10d06-256">Vous pouvez utiliser ce paramètre uniquement lorsque vous utilisez `Get-Item` ou `Get-ChildItem` dans le `Cert:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="10d06-256">You can use this parameter only when you use `Get-Item` or `Get-ChildItem` in the `Cert:` drive.</span></span>

<span data-ttu-id="10d06-257">Pour obtenir la liste des paramètres dynamiques pris en charge par un fournisseur, consultez le fichier d’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="10d06-257">For a list of the dynamic parameters that a provider supports, see the Help file for the provider.</span></span> <span data-ttu-id="10d06-258">Tapez :</span><span class="sxs-lookup"><span data-stu-id="10d06-258">Type:</span></span>

```
Get-Help <provider-name>
```

<span data-ttu-id="10d06-259">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="10d06-259">For example:</span></span>

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a><span data-ttu-id="10d06-260">En savoir plus sur les fournisseurs</span><span class="sxs-lookup"><span data-stu-id="10d06-260">Learning about providers</span></span>

<span data-ttu-id="10d06-261">Bien que toutes les données du fournisseur apparaissent dans les lecteurs et que vous utilisiez les mêmes méthodes pour les parcourir, la similarité s’arrête là.</span><span class="sxs-lookup"><span data-stu-id="10d06-261">Although all provider data appears in drives and you use the same methods to move through them, the similarity stops there.</span></span> <span data-ttu-id="10d06-262">Les magasins de données exposés par le fournisseur peuvent être aussi variés que les emplacements de Active Directory et les boîtes aux lettres de Microsoft Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="10d06-262">The data stores that the provider exposes can be as varied as Active Directory locations and Microsoft Exchange Server mailboxes.</span></span>

<span data-ttu-id="10d06-263">Pour plus d’informations sur les différents fournisseurs PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="10d06-263">For information about individual PowerShell providers, type:</span></span>

```
Get-Help <ProviderName>
```

<span data-ttu-id="10d06-264">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="10d06-264">For example:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="10d06-265">Pour obtenir la liste des rubriques d’aide sur les fournisseurs, tapez :</span><span class="sxs-lookup"><span data-stu-id="10d06-265">For a list of Help topics about the providers, type:</span></span>

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a><span data-ttu-id="10d06-266">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10d06-266">See also</span></span>

[<span data-ttu-id="10d06-267">about_Locations</span><span class="sxs-lookup"><span data-stu-id="10d06-267">about_Locations</span></span>](about_Locations.md)

[<span data-ttu-id="10d06-268">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="10d06-268">about_Path_Syntax</span></span>](about_Path_Syntax.md)

