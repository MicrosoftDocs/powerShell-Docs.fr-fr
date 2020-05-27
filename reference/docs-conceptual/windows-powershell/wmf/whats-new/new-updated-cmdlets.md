---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Cmdlets nouvelles et mises à jour
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809115"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="9db26-103">Cmdlets nouvelles et mises à jour</span><span class="sxs-lookup"><span data-stu-id="9db26-103">New and updated cmdlets</span></span>

<span data-ttu-id="9db26-104">Nous avons ajouté de nouvelles cmdlets et en avons mis à jour d’autres d’après les commentaires de la communauté.</span><span class="sxs-lookup"><span data-stu-id="9db26-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="9db26-105">Applets de commande d’archive</span><span class="sxs-lookup"><span data-stu-id="9db26-105">Archive cmdlets</span></span>

<span data-ttu-id="9db26-106">Deux nouvelles applets de commande, `Compress-Archive` et `Expand-Archive`, permettent de compresser et de décompresser des fichiers ZIP.</span><span class="sxs-lookup"><span data-stu-id="9db26-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="9db26-107">Pour plus d’informations, voir la documentation du module [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/).</span><span class="sxs-lookup"><span data-stu-id="9db26-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="9db26-108">Applets de commande de catalogue</span><span class="sxs-lookup"><span data-stu-id="9db26-108">Catalog Cmdlets</span></span>

<span data-ttu-id="9db26-109">Deux nouvelles cmdlets ont été ajoutées au module Microsoft.PowerShell.Security.</span><span class="sxs-lookup"><span data-stu-id="9db26-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="9db26-110">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="9db26-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="9db26-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="9db26-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="9db26-112">Elles génèrent et valident des fichiers catalogue Windows.</span><span class="sxs-lookup"><span data-stu-id="9db26-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="9db26-113">Applets de commande de Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="9db26-113">Clipboard cmdlets</span></span>

<span data-ttu-id="9db26-114">`Get-Clipboard` et `Set-Clipboard` permettent de transférer du contenu vers et à partir d’une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9db26-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="9db26-115">Les applets de commande du Presse-papiers prennent en charge les images, les fichiers audio, les listes de fichiers et le texte.</span><span class="sxs-lookup"><span data-stu-id="9db26-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="9db26-116">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="9db26-116">For more information, see:</span></span>

- [<span data-ttu-id="9db26-117">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="9db26-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="9db26-118">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="9db26-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="9db26-119">Applets de commande CMS (Cryptographic Message Syntax)</span><span class="sxs-lookup"><span data-stu-id="9db26-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="9db26-120">Les applets de commande Cryptographic Message Syntax prennent en charge le chiffrement et le déchiffrement de contenu au format IETF pour la protection par chiffrement des messages comme documenté dans la [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span><span class="sxs-lookup"><span data-stu-id="9db26-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="9db26-121">Le standard CMS implémente un chiffrement à clé publique, selon lequel la clé servant à chiffrer le contenu (la *clé publique*) et la clé servant à le déchiffrer (la *clé privée*) sont distinctes.</span><span class="sxs-lookup"><span data-stu-id="9db26-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="9db26-122">La clé publique, qui ne constitue pas une donnée sensible, est partageable à grande échelle.</span><span class="sxs-lookup"><span data-stu-id="9db26-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="9db26-123">Le contenu chiffré avec la clé publique ne peut être déchiffré qu’avec la clé privée.</span><span class="sxs-lookup"><span data-stu-id="9db26-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="9db26-124">Pour plus d’informations, consultez [Cryptographie asymétrique](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="9db26-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="9db26-125">Pour plus d’informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="9db26-125">For more information see:</span></span>

- [<span data-ttu-id="9db26-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="9db26-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [<span data-ttu-id="9db26-127">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="9db26-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [<span data-ttu-id="9db26-128">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="9db26-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

<span data-ttu-id="9db26-129">Les certificats ont besoin d’un identificateur EKU (utilisation améliorée de la clé), comme « signature du code » ou « courrier chiffré », pour être identifiés comme certificats de chiffrement de données dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9db26-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="9db26-130">Pour afficher des certificats de chiffrement de document dans le fournisseur de certificats, vous pouvez utiliser le paramètre dynamique **DocumentEncryptionCert**`Get-ChildItem` :</span><span class="sxs-lookup"><span data-stu-id="9db26-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="9db26-131">Extraire et analyser des objets structurés à partir de contenu de type chaîne</span><span class="sxs-lookup"><span data-stu-id="9db26-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="9db26-132">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="9db26-132">ConvertFrom-String</span></span>

<span data-ttu-id="9db26-133">La nouvelle cmdlet `ConvertFrom-String` prend en charge deux modes :</span><span class="sxs-lookup"><span data-stu-id="9db26-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="9db26-134">Analyse délimitée de base</span><span class="sxs-lookup"><span data-stu-id="9db26-134">Basic delimited parsing</span></span>
- <span data-ttu-id="9db26-135">Analyse générée automatiquement et axée sur des exemples</span><span class="sxs-lookup"><span data-stu-id="9db26-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="9db26-136">Par défaut, l’analyse délimitée fractionne l’entrée au niveau de l’espace blanc et elle affecte des noms de propriétés aux groupes résultants.</span><span class="sxs-lookup"><span data-stu-id="9db26-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="9db26-137">Le paramètre **-UpdateTemplate** enregistre les résultats de l’algorithme d’apprentissage sous forme de commentaire dans le fichier de modèle.</span><span class="sxs-lookup"><span data-stu-id="9db26-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="9db26-138">Ainsi, le processus d’apprentissage (l’étape la plus lente) a un coût unique.</span><span class="sxs-lookup"><span data-stu-id="9db26-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="9db26-139">L’exécution de `ConvertFrom-String` avec un modèle contenant l’algorithme d’apprentissage encodé est maintenant presque instantanée.</span><span class="sxs-lookup"><span data-stu-id="9db26-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="9db26-140">Pour plus d’informations, voir [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span><span class="sxs-lookup"><span data-stu-id="9db26-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="9db26-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="9db26-141">Convert-String</span></span>

<span data-ttu-id="9db26-142">`Convert-String` permet de fournir des exemples avant/après de l’apparence souhaitée du texte.</span><span class="sxs-lookup"><span data-stu-id="9db26-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="9db26-143">La cmdlet met automatiquement le texte en forme.</span><span class="sxs-lookup"><span data-stu-id="9db26-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="9db26-144">Pour plus d’informations, voir [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span><span class="sxs-lookup"><span data-stu-id="9db26-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="9db26-145">Mises à jour de l’objet FileInfo</span><span class="sxs-lookup"><span data-stu-id="9db26-145">Updates to FileInfo object</span></span>

<span data-ttu-id="9db26-146">Les informations de version de fichier peuvent prêter à confusion, notamment dans les cas où le fichier a été corrigé.</span><span class="sxs-lookup"><span data-stu-id="9db26-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="9db26-147">WMF 5.0 ajoute de nouvelles propriétés de script **FileVersionRaw** et **ProductVersionRaw** aux objets **FileInfo**.</span><span class="sxs-lookup"><span data-stu-id="9db26-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="9db26-148">Voici les propriétés telles qu’elles sont affichées pour powershell.exe (en supposant que $pid est l’ID du processus PowerShell) :</span><span class="sxs-lookup"><span data-stu-id="9db26-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="9db26-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="9db26-149">Format-Hex</span></span>

<span data-ttu-id="9db26-150">`Format-Hex` permet d’afficher du texte ou des données binaires au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="9db26-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="9db26-151">Pour plus d’informations, voir [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span><span class="sxs-lookup"><span data-stu-id="9db26-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="9db26-152">Get-ChildItem a un paramètre -Depth</span><span class="sxs-lookup"><span data-stu-id="9db26-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="9db26-153">`Get-ChildItem` comporte maintenant un paramètre **Depth** qui permet de limiter la récursivité lorsqu’il est utilisé avec **Recurse** :</span><span class="sxs-lookup"><span data-stu-id="9db26-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="9db26-154">Prise en charge des modules pour la déclaration des plages de versions (1.\*, etc.)</span><span class="sxs-lookup"><span data-stu-id="9db26-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="9db26-155">Il est maintenant possible de combiner **MinimumVersion** et  **MaximumVersion** pour importer le module dans une plage spécifique.</span><span class="sxs-lookup"><span data-stu-id="9db26-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="9db26-156">Les paramètres prennent également en charge les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="9db26-156">The parameters also support wildcards.</span></span>

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a><span data-ttu-id="9db26-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="9db26-157">New-Guid</span></span>

<span data-ttu-id="9db26-158">Un identificateur unique est nécessaire dans de nombreux scénarios.</span><span class="sxs-lookup"><span data-stu-id="9db26-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="9db26-159">La cmdlet `New-GUID` permet de créer un nouveau GUID.</span><span class="sxs-lookup"><span data-stu-id="9db26-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="9db26-160">Paramètre NoNewLine</span><span class="sxs-lookup"><span data-stu-id="9db26-160">NoNewLine parameter</span></span>

<span data-ttu-id="9db26-161">`Out-File`, `Add-Content` et `Set-Content` comportent maintenant un nouveau commutateur **NoNewline** qui omet la nouvelle ligne après la sortie.</span><span class="sxs-lookup"><span data-stu-id="9db26-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="9db26-162">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9db26-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

<span data-ttu-id="9db26-163">Sans **NoNewline**, chacun des fragments serait sur une ligne distincte :</span><span class="sxs-lookup"><span data-stu-id="9db26-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="9db26-164">Interagir avec des liens symboliques à l’aide des applets de commande Item améliorées</span><span class="sxs-lookup"><span data-stu-id="9db26-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="9db26-165">La cmdlet Item et quelques cmdlets associées ont été étendues de façon à prendre en charge les liens symboliques.</span><span class="sxs-lookup"><span data-stu-id="9db26-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="9db26-166">Fichiers de liens symboliques</span><span class="sxs-lookup"><span data-stu-id="9db26-166">Symbolic link files</span></span>

<span data-ttu-id="9db26-167">Dans cet exemple, nous créons dans C:\Temp un fichier SYLK nommé MySymLinkFile.txt, qui établit un lien avec $pshome\profile.ps1.</span><span class="sxs-lookup"><span data-stu-id="9db26-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="9db26-168">Les trois exemples produisent le même résultat.</span><span class="sxs-lookup"><span data-stu-id="9db26-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="9db26-169">Répertoires de liens symboliques</span><span class="sxs-lookup"><span data-stu-id="9db26-169">Symbolic link directories</span></span>

<span data-ttu-id="9db26-170">Dans cet exemple, nous créons dans C:\Temp un répertoire SYLK nommé MySymLinkDir, qui établit un lien avec le dossier $pshome.</span><span class="sxs-lookup"><span data-stu-id="9db26-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="9db26-171">Les trois exemples produisent le même résultat.</span><span class="sxs-lookup"><span data-stu-id="9db26-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="9db26-172">Liens physiques</span><span class="sxs-lookup"><span data-stu-id="9db26-172">Hard links</span></span>

<span data-ttu-id="9db26-173">Les combinaisons autorisées de **Path** et de **Name** décrites ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="9db26-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="9db26-174">Jonctions de répertoires</span><span class="sxs-lookup"><span data-stu-id="9db26-174">Directory junctions</span></span>

<span data-ttu-id="9db26-175">Les combinaisons autorisées de **Path** et de **Name** décrites ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="9db26-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="9db26-176">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="9db26-176">Get-ChildItem</span></span>

<span data-ttu-id="9db26-177">`Get-ChildItem` affiche maintenant un « l » dans la propriété **Mode** pour indiquer un fichier ou un répertoire SYLK.</span><span class="sxs-lookup"><span data-stu-id="9db26-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a><span data-ttu-id="9db26-178">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="9db26-178">Remove-Item</span></span>

<span data-ttu-id="9db26-179">La suppression des liens symboliques fonctionne comme pour n’importe quel type d’élément.</span><span class="sxs-lookup"><span data-stu-id="9db26-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="9db26-180">Utilisez le paramètre **Force** pour supprimer les fichiers du répertoire cible et le lien symbolique.</span><span class="sxs-lookup"><span data-stu-id="9db26-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="9db26-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="9db26-181">New-TemporaryFile</span></span>

<span data-ttu-id="9db26-182">Parfois, dans vos scripts, vous devez créer un fichier temporaire.</span><span class="sxs-lookup"><span data-stu-id="9db26-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="9db26-183">C’est maintenant possible avec la commande `New-TemporaryFile` :</span><span class="sxs-lookup"><span data-stu-id="9db26-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="9db26-184">Gestion du commutateur réseau avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="9db26-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="9db26-185">Les applets de commande du commutateur réseau, introduites dans WMF 5.0, permettent d’appliquer une configuration de port de commutateur réseau local virtuel (VLAN) et de commutateur réseau de base de couche 2 à des commutateurs réseau certifiés par logo Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="9db26-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="9db26-186">Ces applets de commande vous permettent d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9db26-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="9db26-187">Configuration globale du commutateur, par exemple :</span><span class="sxs-lookup"><span data-stu-id="9db26-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="9db26-188">Définir le nom d’hôte</span><span class="sxs-lookup"><span data-stu-id="9db26-188">Set host name</span></span>
  - <span data-ttu-id="9db26-189">Définir la bannière de commutateur</span><span class="sxs-lookup"><span data-stu-id="9db26-189">Set switch banner</span></span>
  - <span data-ttu-id="9db26-190">Conserver la configuration</span><span class="sxs-lookup"><span data-stu-id="9db26-190">Persist configuration</span></span>
  - <span data-ttu-id="9db26-191">Activer ou désactiver une fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="9db26-191">Enable or disable feature</span></span>

- <span data-ttu-id="9db26-192">Configuration de réseau local virtuel :</span><span class="sxs-lookup"><span data-stu-id="9db26-192">VLAN configuration:</span></span>
  - <span data-ttu-id="9db26-193">Créer ou supprimer un réseau local virtuel</span><span class="sxs-lookup"><span data-stu-id="9db26-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="9db26-194">Activer ou désactiver un réseau local virtuel</span><span class="sxs-lookup"><span data-stu-id="9db26-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="9db26-195">Énumérer les réseaux locaux virtuels</span><span class="sxs-lookup"><span data-stu-id="9db26-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="9db26-196">Définir le nom convivial d’un réseau local virtuel</span><span class="sxs-lookup"><span data-stu-id="9db26-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="9db26-197">Configuration de port de couche 2 :</span><span class="sxs-lookup"><span data-stu-id="9db26-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="9db26-198">Énumérer les ports</span><span class="sxs-lookup"><span data-stu-id="9db26-198">Enumerate ports</span></span>
  - <span data-ttu-id="9db26-199">Activer ou désactiver des ports</span><span class="sxs-lookup"><span data-stu-id="9db26-199">Enable or disable ports</span></span>
  - <span data-ttu-id="9db26-200">Définir les propriétés et les modes des ports</span><span class="sxs-lookup"><span data-stu-id="9db26-200">Set port modes and properties</span></span>
  - <span data-ttu-id="9db26-201">Ajouter ou associer un réseau local virtuel à Trunk ou Accès sur le port</span><span class="sxs-lookup"><span data-stu-id="9db26-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="9db26-202">Pour plus d’informations, voir la documentation [NetworkSwitchManager](/powershell/module/networkswitchmanager/).</span><span class="sxs-lookup"><span data-stu-id="9db26-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="9db26-203">Générer des cmdlets PowerShell basées sur un point de terminaison OData avec ODataUtils</span><span class="sxs-lookup"><span data-stu-id="9db26-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="9db26-204">Le module ODataUtils permet de générer des cmdlets PowerShell à partir de points de terminaison REST qui prennent en charge OData.</span><span class="sxs-lookup"><span data-stu-id="9db26-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="9db26-205">Le module Microsoft.PowerShell.ODataUtils comporte les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="9db26-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="9db26-206">Informations supplémentaires sur les canaux du point de terminaison côté serveur vers le côté client.</span><span class="sxs-lookup"><span data-stu-id="9db26-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="9db26-207">Prise en charge de la pagination côté client</span><span class="sxs-lookup"><span data-stu-id="9db26-207">Client-side paging support</span></span>
- <span data-ttu-id="9db26-208">Filtrage côté serveur à l’aide du paramètre -Select</span><span class="sxs-lookup"><span data-stu-id="9db26-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="9db26-209">Prise en charge des en-têtes de demande web</span><span class="sxs-lookup"><span data-stu-id="9db26-209">Support for web request headers</span></span>

<span data-ttu-id="9db26-210">Les cmdlets de proxy générées par la cmdlet `Export-ODataEndPointProxy` fournissent des informations supplémentaires provenant du point de terminaison OData côté serveur sur le flux **Information**.</span><span class="sxs-lookup"><span data-stu-id="9db26-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="9db26-211">Dans l’exemple suivant, nous récupérons les meilleurs produits et capturons la sortie dans la variable `$infoStream`.</span><span class="sxs-lookup"><span data-stu-id="9db26-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="9db26-212">En spécifiant le paramètre **IncludeTotalResponseCount**, nous obtenons le nombre total d’enregistrements **Product** disponibles sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="9db26-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="9db26-213">Il est possible de récupérer les enregistrements provenant du serveur par lots grâce à la prise en charge de la pagination côté client.</span><span class="sxs-lookup"><span data-stu-id="9db26-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="9db26-214">C’est utile quand vous devez obtenir une grande quantité de données à partir du serveur par le biais du réseau.</span><span class="sxs-lookup"><span data-stu-id="9db26-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="9db26-215">Les cmdlets de proxy générées prennent en charge le paramètre**Select**, qui sert de filtre pour ne recevoir que les propriétés d’enregistrements nécessaires au client.</span><span class="sxs-lookup"><span data-stu-id="9db26-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="9db26-216">Le filtrage s’effectue sur le serveur, ce qui réduit la quantité de données transférées sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="9db26-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="9db26-217">La cmdlet `Export-ODataEndpointProxy` et les cmdlets de proxy qu’elle génère prennent maintenant en charge le paramètre **Headers**.</span><span class="sxs-lookup"><span data-stu-id="9db26-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="9db26-218">L’en-tête peut servir à canaliser des informations supplémentaires attendues par le point de terminaison OData.</span><span class="sxs-lookup"><span data-stu-id="9db26-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="9db26-219">Dans l’exemple suivant, une table de hachage contenant une clé d’abonnement est fournie au paramètre **Headers**.</span><span class="sxs-lookup"><span data-stu-id="9db26-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="9db26-220">Il s’agit d’un exemple classique pour des services qui attendent une clé d’abonnement à des fins d’authentification.</span><span class="sxs-lookup"><span data-stu-id="9db26-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
