---
description: Décrit comment les fournisseurs PowerShell fournissent un accès aux données et aux composants qui ne seraient pas facilement accessibles à partir de la ligne de commande. Les données sont présentées dans un format cohérent qui ressemble à un lecteur du système de fichiers.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: cbafcab2b24e77a43d7b628ce9500f480ed9b5b8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206954"
---
# <a name="about-providers"></a><span data-ttu-id="eb646-105">À propos des fournisseurs</span><span class="sxs-lookup"><span data-stu-id="eb646-105">About Providers</span></span>

## <a name="short-description"></a><span data-ttu-id="eb646-106">Description courte</span><span class="sxs-lookup"><span data-stu-id="eb646-106">Short description</span></span>
<span data-ttu-id="eb646-107">Décrit comment les fournisseurs PowerShell fournissent un accès aux données et aux composants qui ne seraient pas facilement accessibles à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="eb646-107">Describes how PowerShell providers provide access to data and components that wouldn't otherwise be easily accessible at the command line.</span></span>
<span data-ttu-id="eb646-108">Les données sont présentées dans un format cohérent qui ressemble à un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="eb646-108">The data is presented in a consistent format that resembles a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="eb646-109">Description longue</span><span class="sxs-lookup"><span data-stu-id="eb646-109">Long description</span></span>

<span data-ttu-id="eb646-110">Les fournisseurs PowerShell sont des programmes .NET qui fournissent un accès à des magasins de données spécialisés pour faciliter l’affichage et la gestion.</span><span class="sxs-lookup"><span data-stu-id="eb646-110">PowerShell providers are .NET programs that provide access to specialized data stores for easier viewing and management.</span></span> <span data-ttu-id="eb646-111">Les données apparaissent dans un lecteur, et vous accédez aux données dans un chemin d’accès comme sur un lecteur de disque dur.</span><span class="sxs-lookup"><span data-stu-id="eb646-111">The data appears in a drive, and you access the data in a path like you would on a hard disk drive.</span></span> <span data-ttu-id="eb646-112">Vous pouvez utiliser l’une des applets de commande intégrées que le fournisseur prend en charge pour gérer les données dans le lecteur du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="eb646-112">You can use any of the built-in cmdlets that the provider supports to manage the data in the provider drive.</span></span> <span data-ttu-id="eb646-113">De plus, vous pouvez utiliser des applets de commande personnalisées conçues spécialement pour les données.</span><span class="sxs-lookup"><span data-stu-id="eb646-113">And, you can use custom cmdlets that are designed especially for the data.</span></span>

<span data-ttu-id="eb646-114">Les fournisseurs peuvent également ajouter des paramètres dynamiques aux applets de commande intégrées.</span><span class="sxs-lookup"><span data-stu-id="eb646-114">The providers can also add dynamic parameters to the built-in cmdlets.</span></span> <span data-ttu-id="eb646-115">Ces paramètres sont disponibles uniquement lorsque vous utilisez l’applet de commande avec les données du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="eb646-115">These parameters are only available when you use the cmdlet with the provider data.</span></span>

## <a name="built-in-providers"></a><span data-ttu-id="eb646-116">Fournisseurs intégrés</span><span class="sxs-lookup"><span data-stu-id="eb646-116">Built-in providers</span></span>

<span data-ttu-id="eb646-117">PowerShell comprend un ensemble de fournisseurs intégrés que vous pouvez utiliser pour accéder aux différents types de magasins de données.</span><span class="sxs-lookup"><span data-stu-id="eb646-117">PowerShell includes a set of built-in providers that you can use to access the different types of data stores.</span></span>

| <span data-ttu-id="eb646-118">Fournisseur</span><span class="sxs-lookup"><span data-stu-id="eb646-118">Provider</span></span>   |   <span data-ttu-id="eb646-119">Lecteur (s)</span><span class="sxs-lookup"><span data-stu-id="eb646-119">Drive(s)</span></span>  |<span data-ttu-id="eb646-120">OutputType</span><span class="sxs-lookup"><span data-stu-id="eb646-120">OutputType</span></span>                                                    |
|----------- |------------ |--------------------------------------------------------------|
|<span data-ttu-id="eb646-121">Alias</span><span class="sxs-lookup"><span data-stu-id="eb646-121">Alias</span></span>       |<span data-ttu-id="eb646-122">Alias:</span><span class="sxs-lookup"><span data-stu-id="eb646-122">Alias:</span></span>       |<span data-ttu-id="eb646-123">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="eb646-123">System.Management.Automation.AliasInfo</span></span>                        |
|<span data-ttu-id="eb646-124">Certificat</span><span class="sxs-lookup"><span data-stu-id="eb646-124">Certificate</span></span> |<span data-ttu-id="eb646-125">Cert:</span><span class="sxs-lookup"><span data-stu-id="eb646-125">Cert:</span></span>        |<span data-ttu-id="eb646-126">Microsoft. PowerShell. Commands. X509StoreLocation</span><span class="sxs-lookup"><span data-stu-id="eb646-126">Microsoft.PowerShell.Commands.X509StoreLocation</span></span>               |
|            |             |<span data-ttu-id="eb646-127">System.Security.Cryptography.X509Certificates.X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="eb646-127">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>|
|<span data-ttu-id="eb646-128">Environnement</span><span class="sxs-lookup"><span data-stu-id="eb646-128">Environment</span></span> |<span data-ttu-id="eb646-129">Env:</span><span class="sxs-lookup"><span data-stu-id="eb646-129">Env:</span></span>         |<span data-ttu-id="eb646-130">System. Collections. DictionaryEntry</span><span class="sxs-lookup"><span data-stu-id="eb646-130">System.Collections.DictionaryEntry</span></span>                            |
|<span data-ttu-id="eb646-131">FileSystem</span><span class="sxs-lookup"><span data-stu-id="eb646-131">FileSystem</span></span>  |<span data-ttu-id="eb646-132">C : (\*)</span><span class="sxs-lookup"><span data-stu-id="eb646-132">C: (\*)</span></span>       |<span data-ttu-id="eb646-133">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="eb646-133">System.IO.FileInfo</span></span>                                            |
|            |             |<span data-ttu-id="eb646-134">System. IO. DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="eb646-134">System.IO.DirectoryInfo</span></span>                                       |
|<span data-ttu-id="eb646-135">Fonction</span><span class="sxs-lookup"><span data-stu-id="eb646-135">Function</span></span>    |<span data-ttu-id="eb646-136">Fonction :</span><span class="sxs-lookup"><span data-stu-id="eb646-136">Function:</span></span>    |<span data-ttu-id="eb646-137">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="eb646-137">System.Management.Automation.FunctionInfo</span></span>                     |
|<span data-ttu-id="eb646-138">Registre</span><span class="sxs-lookup"><span data-stu-id="eb646-138">Registry</span></span>    |<span data-ttu-id="eb646-139">HKLM : HKCU :</span><span class="sxs-lookup"><span data-stu-id="eb646-139">HKLM: HKCU:</span></span>  |<span data-ttu-id="eb646-140">Microsoft. Win32. RegistryKey</span><span class="sxs-lookup"><span data-stu-id="eb646-140">Microsoft.Win32.RegistryKey</span></span>                                   |
|<span data-ttu-id="eb646-141">Variable</span><span class="sxs-lookup"><span data-stu-id="eb646-141">Variable</span></span>    |<span data-ttu-id="eb646-142">Variable :</span><span class="sxs-lookup"><span data-stu-id="eb646-142">Variable:</span></span>    |<span data-ttu-id="eb646-143">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="eb646-143">System.Management.Automation.PSVariable</span></span>                       |
|<span data-ttu-id="eb646-144">WSMan</span><span class="sxs-lookup"><span data-stu-id="eb646-144">WSMan</span></span>       |<span data-ttu-id="eb646-145">WSMan :</span><span class="sxs-lookup"><span data-stu-id="eb646-145">WSMan:</span></span>       |<span data-ttu-id="eb646-146">Microsoft. WSMan. Management. WSManConfigContainerElement</span><span class="sxs-lookup"><span data-stu-id="eb646-146">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>        |

<span data-ttu-id="eb646-147">(\*) Les lecteurs de système de fichiers varient en fonction de chaque système.</span><span class="sxs-lookup"><span data-stu-id="eb646-147">(\*) The FileSystem drives vary on each system.</span></span>

<span data-ttu-id="eb646-148">Vous pouvez également créer vos propres fournisseurs PowerShell, et vous pouvez installer des fournisseurs développés par d’autres.</span><span class="sxs-lookup"><span data-stu-id="eb646-148">You can also create your own PowerShell providers, and you can install providers that others develop.</span></span> <span data-ttu-id="eb646-149">Pour répertorier les fournisseurs disponibles dans votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="eb646-149">To list the providers that are available in your session, type:</span></span>

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a><span data-ttu-id="eb646-150">Installation et suppression de fournisseurs</span><span class="sxs-lookup"><span data-stu-id="eb646-150">Installing and removing providers</span></span>

<span data-ttu-id="eb646-151">Les fournisseurs sont généralement installés via des modules PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb646-151">Providers are typically installed via PowerShell modules.</span></span> <span data-ttu-id="eb646-152">L’importation du module charge le fournisseur dans votre session.</span><span class="sxs-lookup"><span data-stu-id="eb646-152">Importing the module loads the provider into your session.</span></span> <span data-ttu-id="eb646-153">Vous ne pouvez pas désinstaller les fournisseurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="eb646-153">You can't uninstall the built-in providers.</span></span> <span data-ttu-id="eb646-154">Vous pouvez désinstaller des fournisseurs chargés par d’autres modules.</span><span class="sxs-lookup"><span data-stu-id="eb646-154">You can uninstall providers loaded by other modules.</span></span>

<span data-ttu-id="eb646-155">Vous pouvez décharger un fournisseur de la session active à l’aide de l’applet de commande `Remove-Module` .</span><span class="sxs-lookup"><span data-stu-id="eb646-155">You can unload a provider from the current session using the `Remove-Module` cmdlet.</span></span> <span data-ttu-id="eb646-156">Cette applet de commande ne désinstalle pas le fournisseur, mais le fournisseur n’est pas disponible dans la session.</span><span class="sxs-lookup"><span data-stu-id="eb646-156">This cmdlet doesn't uninstall the provider, but it makes the provider unavailable in the session.</span></span>

<span data-ttu-id="eb646-157">Vous pouvez également utiliser l' `Remove-PSDrive` applet de commande pour supprimer un lecteur de la session active.</span><span class="sxs-lookup"><span data-stu-id="eb646-157">You can also use the `Remove-PSDrive` cmdlet to remove any drive from the current session.</span></span> <span data-ttu-id="eb646-158">Ces données sur le lecteur ne sont pas affectées, mais le lecteur n’est plus disponible dans cette session.</span><span class="sxs-lookup"><span data-stu-id="eb646-158">This data on the drive isn't affected, but the drive is no longer available in that session.</span></span>

## <a name="viewing-providers"></a><span data-ttu-id="eb646-159">Affichage des fournisseurs</span><span class="sxs-lookup"><span data-stu-id="eb646-159">Viewing providers</span></span>

<span data-ttu-id="eb646-160">Pour afficher les fournisseurs PowerShell sur votre ordinateur, tapez :</span><span class="sxs-lookup"><span data-stu-id="eb646-160">To view the PowerShell providers on your computer, type:</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="eb646-161">La sortie répertorie les fournisseurs intégrés et les fournisseurs que vous avez ajoutés à la session.</span><span class="sxs-lookup"><span data-stu-id="eb646-161">The output lists the built-in providers and the providers that you added to the session.</span></span>

## <a name="the-provider-cmdlets"></a><span data-ttu-id="eb646-162">Applets de commande du fournisseur</span><span class="sxs-lookup"><span data-stu-id="eb646-162">The provider cmdlets</span></span>

<span data-ttu-id="eb646-163">Les applets de commande suivantes sont conçues pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="eb646-163">The following cmdlets are designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="eb646-164">Vous pouvez utiliser les mêmes cmdlets de la même façon pour gérer les différents types de données que les fournisseurs exposent.</span><span class="sxs-lookup"><span data-stu-id="eb646-164">You can use the same cmdlets in the same way to manage the different types of data that providers expose.</span></span> <span data-ttu-id="eb646-165">Une fois que vous avez appris à gérer les données d’un fournisseur, vous pouvez utiliser les mêmes procédures avec les données de n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="eb646-165">After you learn to manage the data of one provider, you can use the same procedures with the data from any provider.</span></span>

<span data-ttu-id="eb646-166">Par exemple, l' `New-Item` applet de commande crée un nouvel élément.</span><span class="sxs-lookup"><span data-stu-id="eb646-166">For example, the `New-Item` cmdlet creates a new item.</span></span> <span data-ttu-id="eb646-167">Dans le `C:` lecteur pris en charge par le fournisseur **FileSystem** , vous pouvez utiliser `New-Item` pour créer un nouveau fichier ou dossier.</span><span class="sxs-lookup"><span data-stu-id="eb646-167">In the `C:` drive that is supported by the **FileSystem** provider, you can use `New-Item` to create a new file or folder.</span></span> <span data-ttu-id="eb646-168">Dans les lecteurs pris en charge par le fournisseur de **Registre** , vous pouvez utiliser `New-Item` pour créer une nouvelle clé de registre.</span><span class="sxs-lookup"><span data-stu-id="eb646-168">In the drives that are supported by the **Registry** provider, you can use `New-Item` to create a new registry key.</span></span> <span data-ttu-id="eb646-169">Dans le `Alias:` lecteur, vous pouvez utiliser `New-Item` pour créer un nouvel alias.</span><span class="sxs-lookup"><span data-stu-id="eb646-169">In the `Alias:` drive, you can use `New-Item` to create a new alias.</span></span>

<span data-ttu-id="eb646-170">Pour obtenir des informations détaillées sur les applets de commande suivantes, tapez :</span><span class="sxs-lookup"><span data-stu-id="eb646-170">For detailed information about any of the following cmdlets, type:</span></span>

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a><span data-ttu-id="eb646-171">Applets de commande ChildItem</span><span class="sxs-lookup"><span data-stu-id="eb646-171">ChildItem cmdlets</span></span>

- [<span data-ttu-id="eb646-172">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="eb646-172">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a><span data-ttu-id="eb646-173">Applets de commande de contenu</span><span class="sxs-lookup"><span data-stu-id="eb646-173">Content Cmdlets</span></span>

- [<span data-ttu-id="eb646-174">Add-Content</span><span class="sxs-lookup"><span data-stu-id="eb646-174">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="eb646-175">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="eb646-175">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="eb646-176">Get-Content</span><span class="sxs-lookup"><span data-stu-id="eb646-176">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="eb646-177">Set-Content</span><span class="sxs-lookup"><span data-stu-id="eb646-177">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a><span data-ttu-id="eb646-178">Applets de commande Item</span><span class="sxs-lookup"><span data-stu-id="eb646-178">Item Cmdlets</span></span>

- [<span data-ttu-id="eb646-179">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="eb646-179">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="eb646-180">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="eb646-180">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="eb646-181">Get-Item</span><span class="sxs-lookup"><span data-stu-id="eb646-181">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="eb646-182">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="eb646-182">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="eb646-183">Move-Item</span><span class="sxs-lookup"><span data-stu-id="eb646-183">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="eb646-184">New-Item</span><span class="sxs-lookup"><span data-stu-id="eb646-184">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="eb646-185">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="eb646-185">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="eb646-186">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="eb646-186">Rename-Item</span></span>](xref:Microsoft.PowerShell.Management.Rename-Item)
- [<span data-ttu-id="eb646-187">Set-Item</span><span class="sxs-lookup"><span data-stu-id="eb646-187">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a><span data-ttu-id="eb646-188">Applets de commande ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb646-188">ItemProperty cmdlets</span></span>

- [<span data-ttu-id="eb646-189">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb646-189">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="eb646-190">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb646-190">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [<span data-ttu-id="eb646-191">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb646-191">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="eb646-192">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb646-192">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [<span data-ttu-id="eb646-193">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb646-193">New-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [<span data-ttu-id="eb646-194">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb646-194">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="eb646-195">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb646-195">Rename-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [<span data-ttu-id="eb646-196">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb646-196">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a><span data-ttu-id="eb646-197">Applets de commande Location</span><span class="sxs-lookup"><span data-stu-id="eb646-197">Location cmdlets</span></span>

- [<span data-ttu-id="eb646-198">Get-Location</span><span class="sxs-lookup"><span data-stu-id="eb646-198">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="eb646-199">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="eb646-199">Pop-Location</span></span>](xref:Microsoft.PowerShell.Management.Pop-Location)
- [<span data-ttu-id="eb646-200">Push-Location</span><span class="sxs-lookup"><span data-stu-id="eb646-200">Push-Location</span></span>](xref:Microsoft.PowerShell.Management.Push-Location)
- [<span data-ttu-id="eb646-201">Set-Location</span><span class="sxs-lookup"><span data-stu-id="eb646-201">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a><span data-ttu-id="eb646-202">Applets de commande Path</span><span class="sxs-lookup"><span data-stu-id="eb646-202">Path cmdlets</span></span>

- [<span data-ttu-id="eb646-203">Join-Path</span><span class="sxs-lookup"><span data-stu-id="eb646-203">Join-Path</span></span>](xref:Microsoft.PowerShell.Management.Join-Path)
- [<span data-ttu-id="eb646-204">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="eb646-204">Convert-Path</span></span>](xref:Microsoft.PowerShell.Management.Convert-Path)
- [<span data-ttu-id="eb646-205">Split-Path</span><span class="sxs-lookup"><span data-stu-id="eb646-205">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)
- [<span data-ttu-id="eb646-206">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="eb646-206">Resolve-Path</span></span>](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [<span data-ttu-id="eb646-207">Test-Path</span><span class="sxs-lookup"><span data-stu-id="eb646-207">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a><span data-ttu-id="eb646-208">PSDrive, applets de commande</span><span class="sxs-lookup"><span data-stu-id="eb646-208">PSDrive cmdlets</span></span>

- [<span data-ttu-id="eb646-209">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="eb646-209">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="eb646-210">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="eb646-210">New-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [<span data-ttu-id="eb646-211">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="eb646-211">Remove-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a><span data-ttu-id="eb646-212">Applets de commande PSProvider</span><span class="sxs-lookup"><span data-stu-id="eb646-212">PSProvider Cmdlets</span></span>

- [<span data-ttu-id="eb646-213">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="eb646-213">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a><span data-ttu-id="eb646-214">Affichage des données du fournisseur</span><span class="sxs-lookup"><span data-stu-id="eb646-214">Viewing provider data</span></span>

<span data-ttu-id="eb646-215">Le principal avantage d’un fournisseur est qu’il expose ses données de manière familière et cohérente.</span><span class="sxs-lookup"><span data-stu-id="eb646-215">The primary benefit of a provider is that it exposes its data in a familiar and consistent way.</span></span> <span data-ttu-id="eb646-216">Le modèle de présentation des données est un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="eb646-216">The model for data presentation is a file system drive.</span></span>

<span data-ttu-id="eb646-217">Le fournisseur vous permet d’afficher, de parcourir et de modifier des éléments dans le magasin de données comme s’il s’agissait de données dans un système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="eb646-217">The provider allows you to view, navigate, and change items in the data store as though they were data in a file system.</span></span> <span data-ttu-id="eb646-218">Le magasin de données est accessible par le nom du lecteur qu’il prend en charge.</span><span class="sxs-lookup"><span data-stu-id="eb646-218">The data store is accessed by the name of the drive that it supports.</span></span>

<span data-ttu-id="eb646-219">Le lecteur est indiqué dans l’affichage par défaut de l’applet de commande `Get-PSProvider` , mais vous pouvez obtenir des informations sur le lecteur du fournisseur à l’aide de l’applet de commande `Get-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="eb646-219">The drive is listed in the default display of the `Get-PSProvider` cmdlet, but you can get information about the provider drive using the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="eb646-220">Par exemple, pour obtenir toutes les propriétés du lecteur function :, tapez :</span><span class="sxs-lookup"><span data-stu-id="eb646-220">For example, to get all the properties of the Function: drive, type:</span></span>

```powershell
Get-PSDrive Function | Format-List *
```

<span data-ttu-id="eb646-221">Vous pouvez afficher et parcourir les données d’un lecteur du fournisseur comme vous le feriez sur un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="eb646-221">You can view and move through the data in a provider drive just as you would on a file system drive.</span></span>

<span data-ttu-id="eb646-222">Pour afficher le contenu d’un lecteur de fournisseur, utilisez les applets de commande Get-Item ou Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="eb646-222">To view the contents of a provider drive, use the Get-Item or Get-ChildItem cmdlets.</span></span> <span data-ttu-id="eb646-223">Tapez le nom du lecteur suivi d’un signe deux-points ( :).</span><span class="sxs-lookup"><span data-stu-id="eb646-223">Type the drive name followed by a colon (:).</span></span> <span data-ttu-id="eb646-224">Par exemple, pour afficher le contenu du lecteur Alias :, tapez :</span><span class="sxs-lookup"><span data-stu-id="eb646-224">For example, to view the contents of the Alias: drive, type:</span></span>

```powershell
Get-Item alias:
```

<span data-ttu-id="eb646-225">Vous pouvez afficher et gérer les données de n’importe quel lecteur à partir d’un autre lecteur en incluant le nom du lecteur dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="eb646-225">You can view and manage the data in any drive from another drive by including the drive name in the path.</span></span> <span data-ttu-id="eb646-226">Par exemple, pour afficher la clé de Registre HKLM\Software dans le lecteur HKLM : à partir d’un autre lecteur, tapez :</span><span class="sxs-lookup"><span data-stu-id="eb646-226">For example, to view the HKLM\Software registry key in the HKLM: drive from another drive, type:</span></span>

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

<span data-ttu-id="eb646-227">Pour ouvrir le lecteur, utilisez l’applet de commande Set-Location.</span><span class="sxs-lookup"><span data-stu-id="eb646-227">To open the drive, use the Set-Location cmdlet.</span></span> <span data-ttu-id="eb646-228">N’oubliez pas le signe deux-points lorsque vous spécifiez le chemin d’accès au lecteur.</span><span class="sxs-lookup"><span data-stu-id="eb646-228">Remember the colon when you specify the drive path.</span></span> <span data-ttu-id="eb646-229">Par exemple, pour remplacer votre emplacement par le répertoire racine du lecteur Cert :, tapez :</span><span class="sxs-lookup"><span data-stu-id="eb646-229">For example, to change your location to the root directory of the Cert: drive, type:</span></span>

```powershell
Set-Location cert:
```

<span data-ttu-id="eb646-230">Ensuite, pour afficher le contenu du lecteur Cert :, tapez :</span><span class="sxs-lookup"><span data-stu-id="eb646-230">Then, to view the contents of the Cert: drive, type:</span></span>

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a><span data-ttu-id="eb646-231">Déplacement dans des données hiérarchiques</span><span class="sxs-lookup"><span data-stu-id="eb646-231">Moving through hierarchical data</span></span>

<span data-ttu-id="eb646-232">Vous pouvez vous déplacer dans un lecteur du fournisseur comme vous le feriez pour un lecteur de disque dur.</span><span class="sxs-lookup"><span data-stu-id="eb646-232">You can move through a provider drive just as you would a hard disk drive.</span></span>
<span data-ttu-id="eb646-233">Si les données sont organisées dans une hiérarchie d’éléments dans les éléments, utilisez une barre oblique inverse ( `\` ) pour indiquer un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="eb646-233">If the data is arranged in a hierarchy of items within items, use a backslash (`\`) to indicate a child item.</span></span> <span data-ttu-id="eb646-234">Utilisez le format suivant :</span><span class="sxs-lookup"><span data-stu-id="eb646-234">Use the following format:</span></span>

```
drive:\location\child-location\...
```

<span data-ttu-id="eb646-235">Par exemple, pour modifier l’emplacement de la clé de Registre HKLM\Software, tapez une commande Set-Location, par exemple :</span><span class="sxs-lookup"><span data-stu-id="eb646-235">For example, to change your location to the HKLM\Software registry key, type a Set-Location command, such as:</span></span>

```powershell
Set-Location HKLM:\SOFTWARE\
```

<span data-ttu-id="eb646-236">Si un élément du nom complet comprend des espaces, vous devez placer le nom entre guillemets doubles ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="eb646-236">If any element in the fully qualified name includes spaces, you must enclose the name in double-quotation marks (`"`).</span></span> <span data-ttu-id="eb646-237">L’exemple suivant montre un chemin d’accès complet qui comprend des espaces.</span><span class="sxs-lookup"><span data-stu-id="eb646-237">The following example shows a fully qualified path that includes spaces.</span></span>

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

<span data-ttu-id="eb646-238">Vous pouvez également utiliser des références relatives à des emplacements.</span><span class="sxs-lookup"><span data-stu-id="eb646-238">You can also use relative references to locations.</span></span> <span data-ttu-id="eb646-239">Un point ( `.` ) représente l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="eb646-239">A dot (`.`) represents the current location.</span></span> <span data-ttu-id="eb646-240">Par exemple, si vous êtes dans la `HKLM:\Software\Microsoft` clé de Registre et que vous souhaitez répertorier les sous-clés de Registre dans la `HKLM:\Software\Microsoft\PowerShell` clé, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="eb646-240">For example, if you are in the `HKLM:\Software\Microsoft` registry key, and you want to list the registry subkeys in the `HKLM:\Software\Microsoft\PowerShell` key, type the following command:</span></span>

```powershell
Get-ChildItem .\PowerShell
```

<span data-ttu-id="eb646-241">En outre, les doubles points ( `..` ) font référence au répertoire ou au conteneur situé juste au-dessus de votre emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="eb646-241">Also, double-dots (`..`) refers to the directory or container directly above your current location.</span></span> <span data-ttu-id="eb646-242">Vous pouvez utiliser des points doubles ( `..` ) pour naviguer dans une hiérarchie de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="eb646-242">You can use double-dots (`..`) to navigate through a provider hierarchy.</span></span>

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a><span data-ttu-id="eb646-243">Page d’hébergement du fournisseur</span><span class="sxs-lookup"><span data-stu-id="eb646-243">Provider Home</span></span>

<span data-ttu-id="eb646-244">Les fournisseurs disposent également d’un emplacement d' **hébergement** .</span><span class="sxs-lookup"><span data-stu-id="eb646-244">Providers also have a **Home** location.</span></span>  <span data-ttu-id="eb646-245">Cet emplacement est partagé par `PSDrives` le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="eb646-245">This location is shared by all `PSDrives` backed by the provider.</span></span> <span data-ttu-id="eb646-246">Il peut être récupéré en affichant la propriété de **démarrage** du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="eb646-246">It can be retrieved by viewing the **Home** property of the provider.</span></span>

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

<span data-ttu-id="eb646-247">Le fournisseur **FileSystem** est le seul fournisseur qui a une valeur par défaut pour la **page d’hébergement** .</span><span class="sxs-lookup"><span data-stu-id="eb646-247">The **FileSystem** provider is the only provider that has a default value for **Home** .</span></span> <span data-ttu-id="eb646-248">Il s’agit de la même valeur que `$Home` .</span><span class="sxs-lookup"><span data-stu-id="eb646-248">It's the same value as `$Home`.</span></span> <span data-ttu-id="eb646-249">Pour plus d’informations, consultez [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="eb646-249">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="eb646-250">Vous pouvez définir le répertoire de **départ** pour un fournisseur, pour la session active, à l’aide de sa propriété.</span><span class="sxs-lookup"><span data-stu-id="eb646-250">You can set the **Home** directory for a provider, for the current session, using its property.</span></span>

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

<span data-ttu-id="eb646-251">Le `~` caractère peut être utilisé pour représenter le répertoire de départ du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="eb646-251">The `~` character can be used to represent the provider's home directory.</span></span>
<span data-ttu-id="eb646-252">Si le fournisseur n’a pas d’emplacement de **départ** défini, une erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="eb646-252">If the provider doesn't have a **Home** location set, you see an error.</span></span>

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

## <a name="finding-dynamic-parameters"></a><span data-ttu-id="eb646-253">Recherche de paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="eb646-253">Finding dynamic parameters</span></span>

<span data-ttu-id="eb646-254">Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés à une applet de commande par un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="eb646-254">Dynamic parameters are cmdlet parameters that are added to a cmdlet by a provider.</span></span> <span data-ttu-id="eb646-255">Ces paramètres sont disponibles uniquement lorsque l’applet de commande est utilisée avec le fournisseur qui les a ajoutés.</span><span class="sxs-lookup"><span data-stu-id="eb646-255">These parameters are available only when the cmdlet is used with the provider that added them.</span></span>

<span data-ttu-id="eb646-256">Par exemple, le `Cert:` lecteur ajoute le paramètre **CodeSigningCert** aux `Get-Item` applets de commande et `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="eb646-256">For example, the `Cert:` drive adds the **CodeSigningCert** parameter to the `Get-Item` and `Get-ChildItem` cmdlets.</span></span> <span data-ttu-id="eb646-257">Vous pouvez utiliser ce paramètre uniquement lorsque vous utilisez `Get-Item` ou `Get-ChildItem` dans le `Cert:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="eb646-257">You can use this parameter only when you use `Get-Item` or `Get-ChildItem` in the `Cert:` drive.</span></span>

<span data-ttu-id="eb646-258">Pour obtenir la liste des paramètres dynamiques pris en charge par un fournisseur, consultez le fichier d’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="eb646-258">For a list of the dynamic parameters that a provider supports, see the Help file for the provider.</span></span> <span data-ttu-id="eb646-259">Tapez :</span><span class="sxs-lookup"><span data-stu-id="eb646-259">Type:</span></span>

```
Get-Help <provider-name>
```

<span data-ttu-id="eb646-260">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="eb646-260">For example:</span></span>

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a><span data-ttu-id="eb646-261">En savoir plus sur les fournisseurs</span><span class="sxs-lookup"><span data-stu-id="eb646-261">Learning about providers</span></span>

<span data-ttu-id="eb646-262">Bien que toutes les données du fournisseur apparaissent dans les lecteurs et que vous utilisiez les mêmes méthodes pour les parcourir, la similarité s’arrête là.</span><span class="sxs-lookup"><span data-stu-id="eb646-262">Although all provider data appears in drives and you use the same methods to move through them, the similarity stops there.</span></span> <span data-ttu-id="eb646-263">Les magasins de données exposés par le fournisseur peuvent être aussi variés que les emplacements de Active Directory et les boîtes aux lettres de Microsoft Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="eb646-263">The data stores that the provider exposes can be as varied as Active Directory locations and Microsoft Exchange Server mailboxes.</span></span>

<span data-ttu-id="eb646-264">Pour plus d’informations sur les différents fournisseurs PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="eb646-264">For information about individual PowerShell providers, type:</span></span>

```
Get-Help <ProviderName>
```

<span data-ttu-id="eb646-265">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="eb646-265">For example:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="eb646-266">Pour obtenir la liste des rubriques d’aide sur les fournisseurs, tapez :</span><span class="sxs-lookup"><span data-stu-id="eb646-266">For a list of Help topics about the providers, type:</span></span>

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a><span data-ttu-id="eb646-267">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb646-267">See also</span></span>

[<span data-ttu-id="eb646-268">about_Locations</span><span class="sxs-lookup"><span data-stu-id="eb646-268">about_Locations</span></span>](about_Locations.md)

[<span data-ttu-id="eb646-269">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="eb646-269">about_Path_Syntax</span></span>](about_Path_Syntax.md)
