---
description: Certificat
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/about/about_certificate_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur Certificate
ms.openlocfilehash: 6d78c587f79bb09c66700fb71519fe0f32318386
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208265"
---
# <a name="certificate-provider"></a><span data-ttu-id="5a0c7-104">Fournisseur Certificate</span><span class="sxs-lookup"><span data-stu-id="5a0c7-104">Certificate Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="5a0c7-105">Nom du fournisseur</span><span class="sxs-lookup"><span data-stu-id="5a0c7-105">Provider name</span></span>

<span data-ttu-id="5a0c7-106">Certificat</span><span class="sxs-lookup"><span data-stu-id="5a0c7-106">Certificate</span></span>

## <a name="drives"></a><span data-ttu-id="5a0c7-107">Lecteurs</span><span class="sxs-lookup"><span data-stu-id="5a0c7-107">Drives</span></span>

`Cert:`

## <a name="capabilities"></a><span data-ttu-id="5a0c7-108">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="5a0c7-108">Capabilities</span></span>

<span data-ttu-id="5a0c7-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="5a0c7-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="5a0c7-110">Description courte</span><span class="sxs-lookup"><span data-stu-id="5a0c7-110">Short description</span></span>

<span data-ttu-id="5a0c7-111">Fournit l’accès aux magasins de certificats X. 509 et aux certificats dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-111">Provides access to X.509 certificate stores and certificates in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="5a0c7-112">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="5a0c7-112">Detailed description</span></span>

<span data-ttu-id="5a0c7-113">Le fournisseur de **certificats** PowerShell vous permet d’acquérir, d’ajouter, de modifier, d’effacer et de supprimer des certificats et des magasins de certificats dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-113">The PowerShell **Certificate** provider lets you get, add, change, clear, and delete certificates and certificate stores in PowerShell.</span></span>

<span data-ttu-id="5a0c7-114">Le lecteur de **certificat** est un espace de noms hiérarchique contenant les magasins de certificats et les certificats sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-114">The **Certificate** drive is a hierarchical namespace containing the certificate stores and certificates on your computer.</span></span>

<span data-ttu-id="5a0c7-115">Le fournisseur de **certificats** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-115">The **Certificate** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="5a0c7-116">Get-Location</span><span class="sxs-lookup"><span data-stu-id="5a0c7-116">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="5a0c7-117">Set-Location</span><span class="sxs-lookup"><span data-stu-id="5a0c7-117">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="5a0c7-118">Get-Item</span><span class="sxs-lookup"><span data-stu-id="5a0c7-118">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="5a0c7-119">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5a0c7-119">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="5a0c7-120">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="5a0c7-120">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="5a0c7-121">Move-Item</span><span class="sxs-lookup"><span data-stu-id="5a0c7-121">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="5a0c7-122">New-Item</span><span class="sxs-lookup"><span data-stu-id="5a0c7-122">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="5a0c7-123">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="5a0c7-123">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="5a0c7-124">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5a0c7-124">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="5a0c7-125">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5a0c7-125">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="5a0c7-126">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5a0c7-126">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="5a0c7-127">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="5a0c7-127">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="5a0c7-128">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="5a0c7-128">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="5a0c7-129">Types exposés par ce fournisseur</span><span class="sxs-lookup"><span data-stu-id="5a0c7-129">Types exposed by this provider</span></span>

<span data-ttu-id="5a0c7-130">Le lecteur de certificat expose les types suivants.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-130">The Certificate drive exposes the following types.</span></span>

- <span data-ttu-id="5a0c7-131">Emplacements de stockage (Microsoft. PowerShell. Commands. X509StoreLocation), qui sont des conteneurs de haut niveau qui regroupent les certificats pour l’utilisateur actuel et pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-131">Store locations (Microsoft.PowerShell.Commands.X509StoreLocation), which are high-level containers that group the certificates for the current user and for all users.</span></span> <span data-ttu-id="5a0c7-132">Chaque système a un emplacement des magasins de l'utilisateur actuel (CurrentUser) et de l'ordinateur local (LocalMachine) (tous les utilisateurs).</span><span class="sxs-lookup"><span data-stu-id="5a0c7-132">Each system has a CurrentUser and LocalMachine (all users) store location.</span></span>

- <span data-ttu-id="5a0c7-133">Les magasins de certificats (System. Security. Cryptography. X509Certificates. X509Store), qui sont des magasins physiques dans lesquels les certificats sont enregistrés et gérés.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-133">Certificates stores (System.Security.Cryptography.X509Certificates.X509Store), which are physical stores in which certificates are saved and managed.</span></span>

- <span data-ttu-id="5a0c7-134">Les certificats **System. Security. Cryptography. X509Certificates. X509Certificate2** x. 509, chacun représentant un certificat X. 509 sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-134">X.509 **System.Security.Cryptography.X509Certificates.X509Certificate2** certificates, each of which represent an X.509 certificate on the computer.</span></span>
  <span data-ttu-id="5a0c7-135">Les certificats sont identifiés par leurs empreintes numériques.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-135">Certificates are identified by their thumbprints.</span></span>

## <a name="navigating-the-certificate-drive"></a><span data-ttu-id="5a0c7-136">Navigation dans le lecteur de certificat</span><span class="sxs-lookup"><span data-stu-id="5a0c7-136">Navigating the Certificate drive</span></span>

<span data-ttu-id="5a0c7-137">Le fournisseur de **certificats** expose l’espace de noms de certificat en tant que `Cert:` lecteur dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-137">The **Certificate** provider exposes the certificate namespace as the `Cert:` drive in PowerShell.</span></span> <span data-ttu-id="5a0c7-138">Cette commande utilise la `Set-Location` commande pour changer l’emplacement actuel du magasin de certificats racine dans l’emplacement de magasin LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-138">This command uses the `Set-Location` command to change the current location to the Root certificate store in the LocalMachine store location.</span></span> <span data-ttu-id="5a0c7-139">Utilisez une barre oblique inverse ( \\ ) ou une barre oblique (/) pour indiquer un niveau du `Cert:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-139">Use a backslash (\\) or a forward slash (/) to indicate a level of the `Cert:` drive.</span></span>

```powershell
Set-Location Cert:
```

<span data-ttu-id="5a0c7-140">Vous pouvez également utiliser le fournisseur de certificats à partir de n’importe quel autre lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-140">You can also work with the certificate provider from any other PowerShell drive.</span></span> <span data-ttu-id="5a0c7-141">Pour référencer un alias à partir d’un autre emplacement, utilisez le `Cert:` nom du lecteur dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-141">To reference an alias from another location, use the `Cert:` drive name in the path.</span></span>

```powershell
PS Cert:\> Set-Location -Path LocalMachine\Root
```

<span data-ttu-id="5a0c7-142">Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-142">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="5a0c7-143">Par exemple, entrez :</span><span class="sxs-lookup"><span data-stu-id="5a0c7-143">For example, type:</span></span>

```powershell
Set-Location C:
```

> [!NOTE]
> <span data-ttu-id="5a0c7-144">PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-144">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="5a0c7-145">Les commandes telles que `dir` et `ls` sont maintenant des alias pour l’expression [« obtenir-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="5a0c7-145">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span>
> <span data-ttu-id="5a0c7-146">et `pwd` est un alias pour la récupération de l' [emplacement](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="5a0c7-146">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-contents-of-the-cert-drive"></a><span data-ttu-id="5a0c7-147">Affichage du contenu du lecteur Cert :</span><span class="sxs-lookup"><span data-stu-id="5a0c7-147">Displaying the Contents of the Cert: drive</span></span>

<span data-ttu-id="5a0c7-148">Cette commande utilise l' `Get-ChildItem` applet de commande pour afficher les magasins de certificats dans l’emplacement du magasin de certificats CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-148">This command uses the `Get-ChildItem` cmdlet to display the certificate stores in the CurrentUser certificate store location.</span></span>

<span data-ttu-id="5a0c7-149">Si vous n’êtes pas dans le `Cert:` lecteur, utilisez un chemin d’accès absolu.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-149">If you are not in the `Cert:` drive, use an absolute path.</span></span>

```powershell
PS Cert:\CurrentUser\> Get-ChildItem
```

### <a name="displaying-certificate-properties-within-the-cert-drive"></a><span data-ttu-id="5a0c7-150">Affichage des propriétés de certificat dans le lecteur Cert :</span><span class="sxs-lookup"><span data-stu-id="5a0c7-150">Displaying certificate properties within the Cert: drive</span></span>

<span data-ttu-id="5a0c7-151">Cet exemple obtient un certificat avec `Get-Item` et le stocke dans une variable.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-151">This example gets a certificate with `Get-Item` and stores it in a variable.</span></span>
<span data-ttu-id="5a0c7-152">L’exemple montre les nouvelles propriétés de script de certificat ( **DnsNameList** , **EnhancedKeyUsageList** , **SendAsTrustedIssuer** ) à l’aide de `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="5a0c7-152">The example shows the new certificate script properties ( **DnsNameList** , **EnhancedKeyUsageList** , **SendAsTrustedIssuer** ) using `Select-Object`.</span></span>

```powershell
$c = Get-Item cert:\LocalMachine\My\52A149D0393CE8A8D4AF0B172ED667A9E3A1F44E
$c | Format-List DnsNameList, EnhancedKeyUsageList, SendAsTrustedIssuer
```

```output
DnsNameList          : {SERVER01.contoso.com}
EnhancedKeyUsageList : {WiFi-Machine (1.3.6.1.4.1.311.42.2.6),
                       Client Authentication (1.3.6.1.5.5.7.3.2)}
SendAsTrustedIssuer  : False
```

### <a name="find-all-codesigning-certificates"></a><span data-ttu-id="5a0c7-153">Rechercher tous les certificats de coconception</span><span class="sxs-lookup"><span data-stu-id="5a0c7-153">Find all CodeSigning certificates</span></span>

<span data-ttu-id="5a0c7-154">Cette commande utilise les paramètres **CodeSigningCert** et **recurse** de l' `Get-ChildItem` applet de commande pour obtenir tous les certificats sur l’ordinateur qui disposent de l’autorité de signature de code.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-154">This command uses the **CodeSigningCert** and **Recurse** parameters of the `Get-ChildItem` cmdlet to get all of the certificates on the computer that have code-signing authority.</span></span>

```powershell
Get-ChildItem -Path cert: -CodeSigningCert -Recurse
```

### <a name="find-expired-certificates"></a><span data-ttu-id="5a0c7-155">Rechercher les certificats expirés</span><span class="sxs-lookup"><span data-stu-id="5a0c7-155">Find expired certificates</span></span>

<span data-ttu-id="5a0c7-156">Cette commande utilise le paramètre **ExpiringInDays** de l' `Get-ChildItem` applet de commande pour récupérer les certificats qui expirent dans les 30 prochains jours.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-156">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet to get certificates that will expire within the next 30 days.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\WebHosting -ExpiringInDays 30
```

### <a name="find-server-ssl-certificates"></a><span data-ttu-id="5a0c7-157">Rechercher des certificats SSL de serveur</span><span class="sxs-lookup"><span data-stu-id="5a0c7-157">Find Server SSL Certificates</span></span>

<span data-ttu-id="5a0c7-158">Cette commande utilise le paramètre **SSLServerAuthentication** de l' `Get-ChildItem` applet de commande pour récupérer tous les certificats SSL du serveur dans les magasins My et Webhosting.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-158">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get all Server SSL Certificates in the My and WebHosting stores.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\My, cert:\LocalMachine\WebHosting `
  -SSLServerAuthentication
```

### <a name="find-expired-certificates-on-remote-computers"></a><span data-ttu-id="5a0c7-159">Rechercher les certificats expirés sur les ordinateurs distants</span><span class="sxs-lookup"><span data-stu-id="5a0c7-159">Find expired certificates on remote computers</span></span>

<span data-ttu-id="5a0c7-160">Cette commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Get-ChildItem` commande sur les ordinateurs Srv01 et Srv02.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-160">This command uses the `Invoke-Command` cmdlet to run a `Get-ChildItem` command on the Srv01 and Srv02 computers.</span></span> <span data-ttu-id="5a0c7-161">La valeur zéro (0) dans le paramètre **ExpiringInDays** obtient les certificats sur les ordinateurs Srv01 et Srv02 qui ont expiré.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-161">A value of zero (0) in the **ExpiringInDays** parameter gets certificates on the Srv01 and Srv02 computers that have expired.</span></span>

```powershell
Invoke-Command -ComputerName Srv01, Srv02 {Get-ChildItem -Path cert:\* `
  -Recurse -ExpiringInDays 0}
```

### <a name="combining-filters-to-find-a-specific-set-of-certificates"></a><span data-ttu-id="5a0c7-162">Combinaison de filtres pour rechercher un ensemble spécifique de certificats</span><span class="sxs-lookup"><span data-stu-id="5a0c7-162">Combining filters to find a specific set of certificates</span></span>

<span data-ttu-id="5a0c7-163">Cette commande obtient tous les certificats de l’emplacement de magasin LocalMachine qui ont les attributs suivants :</span><span class="sxs-lookup"><span data-stu-id="5a0c7-163">This command gets all certificates in the LocalMachine store location that have the following attributes:</span></span>

- <span data-ttu-id="5a0c7-164">« Fabrikam » dans leur nom DNS</span><span class="sxs-lookup"><span data-stu-id="5a0c7-164">"fabrikam" in their DNS name</span></span>
- <span data-ttu-id="5a0c7-165">« Authentification du client » dans leur utilisation améliorée de la EKU</span><span class="sxs-lookup"><span data-stu-id="5a0c7-165">"Client Authentication" in their EKU</span></span>
- <span data-ttu-id="5a0c7-166">valeur de `$true` pour la propriété **SendAsTrustedIssuer**</span><span class="sxs-lookup"><span data-stu-id="5a0c7-166">a value of `$true` for the **SendAsTrustedIssuer** property</span></span>
- <span data-ttu-id="5a0c7-167">n’expirent pas dans les 30 prochains jours.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-167">do not expire within the next 30 days.</span></span>

<span data-ttu-id="5a0c7-168">La propriété **notAfter** stocke la date d’expiration du certificat.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-168">The **NotAfter** property stores the certificate expiration date.</span></span>

```powershell
[DateTime] $ValidThrough = (Get-Date) + (New-TimeSpan -Days 30)
Get-ChildItem -Path cert:\* -Recurse -DNSName "*fabrikam*" `
  -EKU "*Client Authentication*" | Where-Object {
                                     $_.SendAsTrustedIssuer -and `
                                     $_.NotAfter -gt $ValidThrough
                                   }
```

## <a name="opening-the-certificates-mmc-snap-in"></a><span data-ttu-id="5a0c7-169">Ouverture du composant logiciel enfichable MMC Certificats</span><span class="sxs-lookup"><span data-stu-id="5a0c7-169">Opening the Certificates MMC Snap-in</span></span>

<span data-ttu-id="5a0c7-170">L' `Invoke-Item` applet de commande utilise l’application par défaut pour ouvrir un chemin d’accès que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-170">The `Invoke-Item` cmdlet will use the default application to open a path you specify.</span></span> <span data-ttu-id="5a0c7-171">Pour les certificats, l’application par défaut est le composant logiciel enfichable Certificats de la console MMC.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-171">For certificates, the default application is the Certificates MMC snap-in.</span></span>

<span data-ttu-id="5a0c7-172">Cette commande ouvre le composant logiciel enfichable MMC Certificats pour gérer le certificat spécifié.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-172">This command opens the Certificates MMC snap-in to manage the specified certificate.</span></span>

```powershell
Invoke-Item cert:\CurrentUser\my\6B8223358119BB08840DEE50FD8AF9EA776CE66B
```

## <a name="copying-certificates"></a><span data-ttu-id="5a0c7-173">Copie des certificats</span><span class="sxs-lookup"><span data-stu-id="5a0c7-173">Copying Certificates</span></span>

<span data-ttu-id="5a0c7-174">La copie de certificats n’est pas prise en charge par le fournisseur de **certificats** .</span><span class="sxs-lookup"><span data-stu-id="5a0c7-174">Copying certificates is not supported by the **Certificate** provider.</span></span> <span data-ttu-id="5a0c7-175">Lorsque vous tentez de copier un certificat, vous voyez cette erreur.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-175">When you attempt to copy a certificate, you see this error.</span></span>

```
$path = "Cert:\LocalMachine\Root\E2C0F6662D3C569705B4B31FE2CBF3434094B254"
PS Cert:\LocalMachine\> Copy-Item -Path $path -Destination .\CA\
Copy-Item : Provider operation stopped because the provider does not support
this operation.
At line:1 char:1
+ Copy-Item -Path $path -Destination .\CA\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotImplemented: (:) [Copy-Item],
                              PSNotSupportedException
    + FullyQualifiedErrorId : NotSupported,
                              Microsoft.PowerShell.Commands.CopyItemCommand
```

## <a name="moving-certificates"></a><span data-ttu-id="5a0c7-176">Déplacement de certificats</span><span class="sxs-lookup"><span data-stu-id="5a0c7-176">Moving Certificates</span></span>

### <a name="move-all-ssl-server-authentication-certs-to-the-webhosting-store"></a><span data-ttu-id="5a0c7-177">Déplacer tous les certificats d’authentification de serveur SSL vers le magasin d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-177">Move all SSL Server authentication certs to the WebHosting store</span></span>

<span data-ttu-id="5a0c7-178">Cette commande utilise l' `Move-Item` applet de commande pour déplacer un certificat du magasin My vers le magasin d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-178">This command uses the `Move-Item` cmdlet to move a certificate from the My store to the WebHosting store.</span></span>

<span data-ttu-id="5a0c7-179">`Move-Item` ne déplace pas les magasins de certificats et les certificats ne sont pas déplacés vers un autre emplacement de stockage, par exemple le déplacement d’un certificat de LocalMachine à CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-179">`Move-Item` will not move certificate stores and it will not move certificates to a different store location, such as moving a certificate from LocalMachine to CurrentUser.</span></span> <span data-ttu-id="5a0c7-180">L' `Move-Item` applet de commande déplace les certificats, mais ne déplace pas les clés privées.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-180">The `Move-Item` cmdlet moves certificates, but it does not move private keys.</span></span>

<span data-ttu-id="5a0c7-181">Cette commande utilise le paramètre **SSLServerAuthentication** de l' `Get-ChildItem` applet de commande pour récupérer les certificats d’authentification de serveur SSL dans le magasin de certificats My.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-181">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get SSL server authentication certificates in the MY certificate store.</span></span>

<span data-ttu-id="5a0c7-182">Les certificats retournés sont dirigés vers l’applet de commande `Move-Item` , qui déplace les certificats vers le magasin d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-182">The returned certificates are piped to the `Move-Item` cmdlet, which moves the certificates to the WebHosting store.</span></span>

```powershell
Get-ChildItem cert:\LocalMachine\My -SSLServerAuthentication | Move-Item `
  -Destination cert:\LocalMachine\WebHosting
```

## <a name="deleting-certificates-and-private-keys"></a><span data-ttu-id="5a0c7-183">Suppression de certificats et de clés privées</span><span class="sxs-lookup"><span data-stu-id="5a0c7-183">Deleting Certificates and Private Keys</span></span>

<span data-ttu-id="5a0c7-184">L' `Remove-Item` applet de commande supprime les certificats que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-184">The `Remove-Item` cmdlet will remove certificates that you specify.</span></span> <span data-ttu-id="5a0c7-185">Le `-DeleteKey` paramètre Dynamic supprime la clé privée.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-185">The `-DeleteKey` dynamic parameter deletes the private key.</span></span>

### <a name="delete-a-certificate-from-the-ca-store"></a><span data-ttu-id="5a0c7-186">Supprimer un certificat du magasin de l’autorité de certification</span><span class="sxs-lookup"><span data-stu-id="5a0c7-186">Delete a Certificate from the CA store</span></span>

<span data-ttu-id="5a0c7-187">Cette commande supprime un certificat dans le magasin de certificats d'autorité de certification, mais laisse la clé privée associée intacte.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-187">This command deletes a certificate from the CA certificate store, but leaves the associated private key intact.</span></span>

<span data-ttu-id="5a0c7-188">Dans le `Cert:` lecteur, l' `Remove-Item` applet de commande prend en charge uniquement les paramètres **DeleteKey** , **path** , **WhatIf** et **Confirm** .</span><span class="sxs-lookup"><span data-stu-id="5a0c7-188">In the `Cert:` drive, the `Remove-Item` cmdlet supports only the **DeleteKey** , **Path** , **WhatIf** , and **Confirm** parameters.</span></span> <span data-ttu-id="5a0c7-189">Tous les autres paramètres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-189">All other parameters are ignored.</span></span>

```powershell
Remove-Item cert:\LocalMachine\CA\5DDC44652E62BF9AA1116DC41DE44AB47C87BDD0
```

### <a name="delete-a-certificate-using-a-wildcards-in-the-dns-name"></a><span data-ttu-id="5a0c7-190">Supprimer un certificat à l’aide de caractères génériques dans le nom DNS</span><span class="sxs-lookup"><span data-stu-id="5a0c7-190">Delete a Certificate using a wildcards in the DNS name</span></span>

<span data-ttu-id="5a0c7-191">Cette commande supprime tous les certificats qui ont un nom DNS contenant « Fabrikam ».</span><span class="sxs-lookup"><span data-stu-id="5a0c7-191">This command deletes all certificates that have a DNS name that contains "Fabrikam".</span></span> <span data-ttu-id="5a0c7-192">Elle utilise le paramètre **dNSName** de l' `Get-ChildItem` applet de commande pour récupérer les certificats et l' `Remove-Item` applet de commande pour les supprimer.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-192">It uses the **DNSName** parameter of the `Get-ChildItem` cmdlet to get the certificates and the `Remove-Item` cmdlet to delete them.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine -DnsName *Fabrikam* | Remove-Item
```

### <a name="delete-private-keys-from-a-remote-computer"></a><span data-ttu-id="5a0c7-193">Supprimer des clés privées d’un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="5a0c7-193">Delete private keys from a remote computer</span></span>

<span data-ttu-id="5a0c7-194">Cette série de commandes active la délégation, puis supprime le certificat et la clé privée associée sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-194">This series of commands enables delegation and then deletes the certificate and associated private key on a remote computer.</span></span> <span data-ttu-id="5a0c7-195">Pour supprimer une clé privée sur un ordinateur distant, vous devez utiliser des informations d'identification déléguées.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-195">To delete a private key on a remote computer, you must use delegated credentials.</span></span>

<span data-ttu-id="5a0c7-196">Utilisez l' `Enable-WSManCredSSP` applet de commande pour activer l’authentification CredSSP (Credential Security Service Provider) sur un client sur l’ordinateur distant S1.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-196">Use the `Enable-WSManCredSSP` cmdlet to enable Credential Security Service Provider (CredSSP) authentication on a client on the S1 remote computer.</span></span>
<span data-ttu-id="5a0c7-197">CredSSP autorise l'authentification déléguée.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-197">CredSSP permits delegated authentication.</span></span>

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer S1
```

<span data-ttu-id="5a0c7-198">Utilisez l' `Connect-WSMan` applet de commande pour connecter l’ordinateur S1 au service WinRM sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-198">Use the `Connect-WSMan` cmdlet to connect the S1 computer to the WinRM service on the local computer.</span></span> <span data-ttu-id="5a0c7-199">Lorsque cette commande est terminée, l’ordinateur S1 apparaît sur le `WSMan:` lecteur local dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-199">When this command completes, the S1 computer appears in the local `WSMan:` drive in PowerShell.</span></span>

```powershell
Connect-WSMan -ComputerName S1 -Credential Domain01\Admin01
```

<span data-ttu-id="5a0c7-200">À présent, vous pouvez utiliser l’applet de commande Set-Item dans le lecteur WSMan : pour activer l’attribut CredSSP pour le service WinRM.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-200">Now, you can use the Set-Item cmdlet in the WSMan: drive to enable the CredSSP attribute for the WinRM service.</span></span>

```powershell
Set-Item -Path WSMan:\S1\Service\Auth\CredSSP -Value $true
```

<span data-ttu-id="5a0c7-201">Démarrez une session à distance sur l’ordinateur S1 à l’aide de l’applet de commande `New-PSSession` et spécifiez l’authentification CredSSP.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-201">Start a remote session on the s1 computer using the `New-PSSession` cmdlet, and specify CredSSP authentication.</span></span> <span data-ttu-id="5a0c7-202">Enregistre la session dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-202">Saves the session in the `$s` variable.</span></span>

```powershell
$s  = New-PSSession S1 -Authentication CredSSP -Credential Domain01\Admin01
```

<span data-ttu-id="5a0c7-203">Enfin, utilisez l' `Invoke-Command` applet de commande pour exécuter une `Remove-Item` commande dans la session dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-203">Finally, use the `Invoke-Command` cmdlet to run a `Remove-Item` command in the session in the `$s` variable.</span></span> <span data-ttu-id="5a0c7-204">La `Remove-Item` commande utilise le paramètre **DeleteKey** pour supprimer la clé privée avec le certificat spécifié.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-204">The `Remove-Item` command uses the **DeleteKey** parameter to remove the private key along with the specified certificate.</span></span>

```powershell
Invoke-Command -Session $s { Remove-Item `
  -Path cert:\LocalMachine\My\D2D38EBA60CAA1C12055A2E1C83B15AD450110C2 `
  -DeleteKey
  }
```

### <a name="delete-expired-certificates"></a><span data-ttu-id="5a0c7-205">Supprimer les certificats expirés</span><span class="sxs-lookup"><span data-stu-id="5a0c7-205">Delete expired Certificates</span></span>

<span data-ttu-id="5a0c7-206">Cette commande utilise le paramètre **ExpiringInDays** de l' `Get-ChildItem` applet de commande avec la valeur 0 pour obtenir les certificats dans le magasin d’hébergement de contenus qui ont expiré.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-206">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet with a value of 0 to get certificates in the WebHosting store that have expired.</span></span>

<span data-ttu-id="5a0c7-207">La variable contenant les certificats renvoyés est dirigée vers l’applet de commande `Remove-Item` , qui les supprime.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-207">The variable containing the returned certificates is piped to the `Remove-Item` cmdlet, which deletes them.</span></span> <span data-ttu-id="5a0c7-208">La commande utilise le paramètre **DeleteKey** pour supprimer la clé privée avec le certificat.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-208">The command uses the **DeleteKey** parameter to delete the private key along with the certificate.</span></span>

```powershell
$expired = Get-ChildItem cert:\LocalMachine\WebHosting -ExpiringInDays 0
$expired | Remove-Item -DeleteKey
```

## <a name="creating-certificates"></a><span data-ttu-id="5a0c7-209">Création de certificats</span><span class="sxs-lookup"><span data-stu-id="5a0c7-209">Creating Certificates</span></span>

<span data-ttu-id="5a0c7-210">L' `New-Item` applet de commande ne crée pas de certificats dans le fournisseur de **certificats** .</span><span class="sxs-lookup"><span data-stu-id="5a0c7-210">The `New-Item` cmdlet does not create new certificates in the **Certificate** provider.</span></span> <span data-ttu-id="5a0c7-211">Utilisez l’applet de commande [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) pour créer un certificat à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-211">Use the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet to create a certificate for testing purposes.</span></span>

## <a name="creating-certificate-stores"></a><span data-ttu-id="5a0c7-212">Création de magasins de certificats</span><span class="sxs-lookup"><span data-stu-id="5a0c7-212">Creating Certificate Stores</span></span>

<span data-ttu-id="5a0c7-213">Dans le lecteur Cert :, l' `New-Item` applet de commande crée des magasins de certificats dans l’emplacement de magasin LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-213">In the Cert: drive, the `New-Item` cmdlet creates certificate stores in the LocalMachine store location.</span></span> <span data-ttu-id="5a0c7-214">Il prend en charge les paramètres **Name** , **path** , **WhatIf** et **Confirm** .</span><span class="sxs-lookup"><span data-stu-id="5a0c7-214">It supports the **Name** , **Path** , **WhatIf** , and **Confirm** parameters.</span></span> <span data-ttu-id="5a0c7-215">Tous les autres paramètres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-215">All other parameters are ignored.</span></span> <span data-ttu-id="5a0c7-216">La commande retourne un **System. Security. Cryptography. X509Certificates. X509Store** qui représente le nouveau magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-216">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

<span data-ttu-id="5a0c7-217">Cette commande crée un magasin de certificats nommé « CustomStore » à l'emplacement des magasins de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-217">This command creates a new certificate store named "CustomStore" in the LocalMachine store location.</span></span>

```powershell
New-Item -Path cert:\LocalMachine\CustomStore
```

### <a name="create-a-new-certificate-store-on-a-remote-computer"></a><span data-ttu-id="5a0c7-218">Créer un nouveau magasin de certificats sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="5a0c7-218">Create a new certificate store on a remote computer</span></span>

<span data-ttu-id="5a0c7-219">Cette commande crée un nouveau magasin de certificats nommé « HostingStore » à l'emplacement des magasins de l'ordinateur local sur l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-219">This command creates a new certificate store named "HostingStore" in the LocalMachine store location on the Server01 computer.</span></span>

<span data-ttu-id="5a0c7-220">La commande utilise l' `Invoke-Command` applet de commande pour exécuter une `New-Item` commande sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-220">The command uses the `Invoke-Command` cmdlet to run a `New-Item` command on the Server01 computer.</span></span> <span data-ttu-id="5a0c7-221">La commande retourne un **System. Security. Cryptography. X509Certificates. X509Store** qui représente le nouveau magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-221">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

```powershell
Invoke-Command { New-Item -Path cert:\LocalMachine\CustomStore } `
  -ComputerName Server01
```

## <a name="creating-client-certificates-for-ws-man"></a><span data-ttu-id="5a0c7-222">Création de certificats clients pour WS-Man</span><span class="sxs-lookup"><span data-stu-id="5a0c7-222">Creating Client Certificates for WS-Man</span></span>

<span data-ttu-id="5a0c7-223">Cette commande crée l’entrée **ClientCertificate** qui peut être utilisée par le client **WS-Management** .</span><span class="sxs-lookup"><span data-stu-id="5a0c7-223">This command creates **ClientCertificate** entry that can be used by the **WS-Management** client.</span></span> <span data-ttu-id="5a0c7-224">Le nouveau **ClientCertificate** s’affichera sous le répertoire **ClientCertificate** en tant que « ClientCertificate_1234567890 ».</span><span class="sxs-lookup"><span data-stu-id="5a0c7-224">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="5a0c7-225">Tous les paramètres sont obligatoires.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-225">All of the parameters are mandatory.</span></span> <span data-ttu-id="5a0c7-226">L' **émetteur** doit être l’empreinte numérique du certificat de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-226">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* -Credential $cred
```

## <a name="deleting-certificate-stores"></a><span data-ttu-id="5a0c7-227">Suppression de magasins de certificats</span><span class="sxs-lookup"><span data-stu-id="5a0c7-227">Deleting Certificate Stores</span></span>

### <a name="delete-a-certificate-store-from-a-remote-computer"></a><span data-ttu-id="5a0c7-228">Supprimer un magasin de certificats d’un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="5a0c7-228">Delete a certificate store from a remote computer</span></span>

<span data-ttu-id="5a0c7-229">Cette commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Remove-Item` commande sur les ordinateurs S1 et S2.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-229">This command uses the `Invoke-Command` cmdlet to run a `Remove-Item` command on the S1 and S2 computers.</span></span> <span data-ttu-id="5a0c7-230">La `Remove-Item` commande comprend le paramètre **recurse** , qui supprime les certificats dans le magasin avant de supprimer le magasin.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-230">The `Remove-Item` command includes the **Recurse** parameter, which deletes the certificates in the store before it deletes the store.</span></span>

```powershell
Invoke-Command { Remove-Item -Path cert:\LocalMachine\TestStore -Recurse } `
  -ComputerName S1, S2
```

## <a name="dynamic-parameters"></a><span data-ttu-id="5a0c7-231">Paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="5a0c7-231">Dynamic parameters</span></span>

<span data-ttu-id="5a0c7-232">Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés par un fournisseur PowerShell et sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur activé par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-232">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span> <span data-ttu-id="5a0c7-233">Ces paramètres sont valides dans tous les sous-répertoires du fournisseur de certificats, mais ils s’appliquent uniquement aux certificats.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-233">These parameters are valid in all subdirectories of the Certificate provider, but are effective only on certificates.</span></span>

> [!NOTE]
> <span data-ttu-id="5a0c7-234">Les paramètres qui effectuent un filtrage sur la `EnhancedKeyUsageList` propriété retournent également des éléments avec une `EnhancedKeyUsageList` valeur de propriété vide.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-234">Parameters that perform filtering against the `EnhancedKeyUsageList` property also return items with an empty `EnhancedKeyUsageList` property value.</span></span>
> <span data-ttu-id="5a0c7-235">Les certificats qui ont un **EnhancedKeyUsageList** vide peuvent être utilisés dans tous les cas.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-235">Certificates that have an empty **EnhancedKeyUsageList** can be used for all purposes.</span></span>

<span data-ttu-id="5a0c7-236">Les paramètres du fournisseur de certificats suivants ont été réintroduits dans PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-236">The following Certificate provider parameters were reintroduced in PowerShell 7.1.</span></span>

- <span data-ttu-id="5a0c7-237">DNSName</span><span class="sxs-lookup"><span data-stu-id="5a0c7-237">DNSName</span></span>
- <span data-ttu-id="5a0c7-238">DocumentEncryptionCert</span><span class="sxs-lookup"><span data-stu-id="5a0c7-238">DocumentEncryptionCert</span></span>
- <span data-ttu-id="5a0c7-239">EKU</span><span class="sxs-lookup"><span data-stu-id="5a0c7-239">EKU</span></span>
- <span data-ttu-id="5a0c7-240">ExpiringInDays</span><span class="sxs-lookup"><span data-stu-id="5a0c7-240">ExpiringInDays</span></span>
- <span data-ttu-id="5a0c7-241">SSLServerAuthentication</span><span class="sxs-lookup"><span data-stu-id="5a0c7-241">SSLServerAuthentication</span></span>

### <a name="codesigningcert-systemmanagementautomationswitchparameter"></a><span data-ttu-id="5a0c7-242">CodeSigningCert <System. Management. Automation. Paramètre_booléen></span><span class="sxs-lookup"><span data-stu-id="5a0c7-242">CodeSigningCert <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5a0c7-243">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="5a0c7-243">Cmdlets supported</span></span>

- [<span data-ttu-id="5a0c7-244">Get-Item</span><span class="sxs-lookup"><span data-stu-id="5a0c7-244">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

- [<span data-ttu-id="5a0c7-245">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5a0c7-245">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="5a0c7-246">Ce paramètre obtient les certificats dont la valeur de propriété **EnhancedKeyUsageList** est « signature du code ».</span><span class="sxs-lookup"><span data-stu-id="5a0c7-246">This parameter gets certificates that have "Code Signing" in their **EnhancedKeyUsageList** property value.</span></span>

### <a name="deletekey-systemmanagementautomationswitchparameter"></a><span data-ttu-id="5a0c7-247">DeleteKey <System. Management. Automation. Paramètre_booléen></span><span class="sxs-lookup"><span data-stu-id="5a0c7-247">DeleteKey <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5a0c7-248">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="5a0c7-248">Cmdlets supported</span></span>

- [<span data-ttu-id="5a0c7-249">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="5a0c7-249">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

<span data-ttu-id="5a0c7-250">Ce paramètre supprime la clé privée associée quand elle supprime le certificat.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-250">This parameter deletes the associated private key when it deletes the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a0c7-251">Pour supprimer une clé privée associée à un certificat d’utilisateur dans le `Cert:\CurrentUser` magasin sur un ordinateur distant, vous devez utiliser des informations d’identification déléguées.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-251">To delete a private key that is associated with a user certificate in the `Cert:\CurrentUser` store on a remote computer, you must use delegated credentials.</span></span> <span data-ttu-id="5a0c7-252">L' `Invoke-Command` applet de commande prend en charge la délégation des informations d’identification à l’aide du paramètre **CredSSP** .</span><span class="sxs-lookup"><span data-stu-id="5a0c7-252">The `Invoke-Command` cmdlet supports credential delegation using the **CredSSP** parameter.</span></span> <span data-ttu-id="5a0c7-253">Vous devez prendre en compte tous les risques de sécurité avant d’utiliser `Remove-Item` avec `Invoke-Command` et la délégation des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-253">You should consider any security risks before using `Remove-Item` with `Invoke-Command` and credential delegation.</span></span>

<span data-ttu-id="5a0c7-254">Ce paramètre a été réintroduit dans PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="5a0c7-254">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="dnsname-microsoftpowershellcommandsdnsnamerepresentation"></a><span data-ttu-id="5a0c7-255">DnsName <Microsoft. PowerShell. Commands. DnsNameRepresentation></span><span class="sxs-lookup"><span data-stu-id="5a0c7-255">DnsName <Microsoft.PowerShell.Commands.DnsNameRepresentation></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5a0c7-256">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="5a0c7-256">Cmdlets supported</span></span>

- [<span data-ttu-id="5a0c7-257">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5a0c7-257">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="5a0c7-258">Ce paramètre obtient les certificats qui ont le nom de domaine ou le modèle de nom spécifié dans la propriété **DNSNameList** du certificat.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-258">This parameter gets certificates that have the specified domain name or name pattern in the **DNSNameList** property of the certificate.</span></span> <span data-ttu-id="5a0c7-259">La valeur de ce paramètre peut être « Unicode » ou « ASCII ».</span><span class="sxs-lookup"><span data-stu-id="5a0c7-259">The value of this parameter can either be "Unicode" or "ASCII".</span></span> <span data-ttu-id="5a0c7-260">Les valeurs Punycode sont converties en Unicode.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-260">Punycode values are converted to Unicode.</span></span> <span data-ttu-id="5a0c7-261">Les caractères génériques ( `*` ) sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-261">Wildcard characters (`*`) are permitted.</span></span>

<span data-ttu-id="5a0c7-262">Ce paramètre a été réintroduit dans PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="5a0c7-262">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="documentencryptioncert-systemmanagementautomationswitchparameter"></a><span data-ttu-id="5a0c7-263">DocumentEncryptionCert <System. Management. Automation. Paramètre_booléen></span><span class="sxs-lookup"><span data-stu-id="5a0c7-263">DocumentEncryptionCert <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5a0c7-264">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="5a0c7-264">Cmdlets supported</span></span>

- [<span data-ttu-id="5a0c7-265">Get-Item</span><span class="sxs-lookup"><span data-stu-id="5a0c7-265">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

- [<span data-ttu-id="5a0c7-266">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5a0c7-266">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="5a0c7-267">Ce paramètre obtient les certificats dont la valeur de propriété **EnhancedKeyUsageList** est « chiffrement de document ».</span><span class="sxs-lookup"><span data-stu-id="5a0c7-267">This parameter gets certificates that have "Document Encryption" in their **EnhancedKeyUsageList** property value.</span></span>

### <a name="eku-systemstring"></a><span data-ttu-id="5a0c7-268">EKU <System. String></span><span class="sxs-lookup"><span data-stu-id="5a0c7-268">EKU <System.String></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5a0c7-269">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="5a0c7-269">Cmdlets supported</span></span>

- [<span data-ttu-id="5a0c7-270">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5a0c7-270">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="5a0c7-271">Ce paramètre obtient les certificats qui ont le texte ou le modèle de texte spécifié dans la `EnhancedKeyUsageList` propriété du certificat.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-271">This parameter gets certificates that have the specified text or text pattern in the `EnhancedKeyUsageList` property of the certificate.</span></span> <span data-ttu-id="5a0c7-272">Les caractères génériques ( `*` ) sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-272">Wildcard characters (`*`) are permitted.</span></span> <span data-ttu-id="5a0c7-273">La `EnhancedKeyUsageList` propriété contient le nom convivial et les champs OID de l’utilisation améliorée de la EKU.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-273">The `EnhancedKeyUsageList` property contains the friendly name and the OID fields of the EKU.</span></span>

<span data-ttu-id="5a0c7-274">Ce paramètre a été réintroduit dans PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="5a0c7-274">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="expiringindays-systemint32"></a><span data-ttu-id="5a0c7-275">ExpiringInDays <System. Int32></span><span class="sxs-lookup"><span data-stu-id="5a0c7-275">ExpiringInDays <System.Int32></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5a0c7-276">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="5a0c7-276">Cmdlets supported</span></span>

- [<span data-ttu-id="5a0c7-277">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5a0c7-277">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="5a0c7-278">Ce paramètre obtient les certificats qui expirent dans ou avant le nombre de jours spécifié.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-278">This parameter gets certificates that are expiring in or before the specified number of days.</span></span> <span data-ttu-id="5a0c7-279">Une valeur de 0 (zéro) obtient les certificats qui sont expirés.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-279">A value of 0 (zero) gets certificates that have expired.</span></span>

<span data-ttu-id="5a0c7-280">Ce paramètre a été réintroduit dans PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="5a0c7-280">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="itemtype-string"></a><span data-ttu-id="5a0c7-281">ItemType \<String\></span><span class="sxs-lookup"><span data-stu-id="5a0c7-281">ItemType \<String\></span></span>

<span data-ttu-id="5a0c7-282">Ce paramètre vous permet de spécifier le type d’élément créé par `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="5a0c7-282">This parameter allows you to specify the type of item created by `New-Item`.</span></span>

<span data-ttu-id="5a0c7-283">Dans un `Certificate` lecteur, les valeurs suivantes sont autorisées :</span><span class="sxs-lookup"><span data-stu-id="5a0c7-283">In a `Certificate` drive, the following values are allowed:</span></span>

- <span data-ttu-id="5a0c7-284">Fournisseur Certificate</span><span class="sxs-lookup"><span data-stu-id="5a0c7-284">Certificate Provider</span></span>
- <span data-ttu-id="5a0c7-285">Certificat</span><span class="sxs-lookup"><span data-stu-id="5a0c7-285">Certificate</span></span>
- <span data-ttu-id="5a0c7-286">Magasin</span><span class="sxs-lookup"><span data-stu-id="5a0c7-286">Store</span></span>
- <span data-ttu-id="5a0c7-287">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="5a0c7-287">StoreLocation</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5a0c7-288">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="5a0c7-288">Cmdlets Supported</span></span>

- [<span data-ttu-id="5a0c7-289">New-Item</span><span class="sxs-lookup"><span data-stu-id="5a0c7-289">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sslserverauthentication-systemmanagementautomationswitchparameter"></a><span data-ttu-id="5a0c7-290">SSLServerAuthentication <System. Management. Automation. Paramètre_booléen></span><span class="sxs-lookup"><span data-stu-id="5a0c7-290">SSLServerAuthentication <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="5a0c7-291">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="5a0c7-291">Cmdlets supported</span></span>

- [<span data-ttu-id="5a0c7-292">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5a0c7-292">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="5a0c7-293">Obtient seulement les certificats serveur pour l'hébergement web SSL.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-293">Gets only server certificates for SSL web hosting.</span></span> <span data-ttu-id="5a0c7-294">Ce paramètre obtient les certificats qui ont une valeur de propriété « authentification du serveur » `EnhancedKeyUsageList` .</span><span class="sxs-lookup"><span data-stu-id="5a0c7-294">This parameter gets certificates that have "Server Authentication" in their `EnhancedKeyUsageList` property value.</span></span>

<span data-ttu-id="5a0c7-295">Ce paramètre a été réintroduit dans PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="5a0c7-295">This parameter was reintroduced in PowerShell 7.1</span></span>

## <a name="script-properties"></a><span data-ttu-id="5a0c7-296">Propriétés du script</span><span class="sxs-lookup"><span data-stu-id="5a0c7-296">Script properties</span></span>

<span data-ttu-id="5a0c7-297">De nouvelles propriétés de script ont été ajoutées à l’objet **X509Certificate2** qui représente les certificats pour faciliter la recherche et la gestion des certificats.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-297">New script properties have been added to the **x509Certificate2** object that represents the certificates to make it easy to search and manage the certificates.</span></span>

- <span data-ttu-id="5a0c7-298">`DnsNameList`: Pour remplir la `DnsNameList` propriété, le fournisseur de certificats copie le contenu de l’entrée dNSName dans l’extension SubjectAlternativeName (San).</span><span class="sxs-lookup"><span data-stu-id="5a0c7-298">`DnsNameList`: To populate the `DnsNameList` property, the Certificate provider copies the content from the DNSName entry in the SubjectAlternativeName (SAN) extension.</span></span> <span data-ttu-id="5a0c7-299">Si l'extension SAN est vide, la propriété est affectée du contenu du champ Objet du certificat.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-299">If the SAN extension is empty, the property is populated with content from the Subject field of the certificate.</span></span>

- <span data-ttu-id="5a0c7-300">`EnhancedKeyUsageList`: Pour remplir la `EnhancedKeyUsageList` propriété, le fournisseur de certificats copie les propriétés OID du champ champ EnhancedKeyUsage (EKU) dans le certificat et crée un nom convivial pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-300">`EnhancedKeyUsageList`: To populate the `EnhancedKeyUsageList` property, the Certificate provider copies the OID properties of the EnhancedKeyUsage (EKU) field in the certificate and creates a friendly name for it.</span></span>

- <span data-ttu-id="5a0c7-301">`SendAsTrustedIssuer`: Pour remplir la `SendAsTrustedIssuer` propriété, le fournisseur de certificats copie la `SendAsTrustedIssuer` propriété du certificat.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-301">`SendAsTrustedIssuer`: To populate the `SendAsTrustedIssuer` property, the Certificate provider copies the `SendAsTrustedIssuer` property from the certificate.</span></span>  <span data-ttu-id="5a0c7-302">Pour plus d’informations, consultez [gestion des émetteurs approuvés pour l’authentification du client](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers).</span><span class="sxs-lookup"><span data-stu-id="5a0c7-302">For more information see [Management of trusted issuers for client authentication](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers).</span></span>

<span data-ttu-id="5a0c7-303">Ces nouvelles fonctionnalités vous permettent de rechercher des certificats d'après leur nom DNS et leur date d'expiration, et de distinguer les certificats d'authentification client et serveur par la valeur de leurs propriétés d'utilisation améliorée de la clé (EKU).</span><span class="sxs-lookup"><span data-stu-id="5a0c7-303">These new features let you search for certificates based on their DNS names and expiration dates, and distinguish client and server authentication certificates by the value of their Enhanced Key Usage (EKU) properties.</span></span>

## <a name="using-the-pipeline"></a><span data-ttu-id="5a0c7-304">Utilisation du pipeline</span><span class="sxs-lookup"><span data-stu-id="5a0c7-304">Using the pipeline</span></span>

<span data-ttu-id="5a0c7-305">Les applets de commande du fournisseur acceptent l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-305">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="5a0c7-306">Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-306">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="5a0c7-307">Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-307">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="5a0c7-308">Obtenir de l’aide</span><span class="sxs-lookup"><span data-stu-id="5a0c7-308">Getting help</span></span>

<span data-ttu-id="5a0c7-309">Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-309">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="5a0c7-310">Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) dans un lecteur du système de fichiers ou utilisez le `-Path` paramètre de `Get-Help` pour spécifier un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="5a0c7-310">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of `Get-Help` to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path cert:
```

## <a name="see-also"></a><span data-ttu-id="5a0c7-311">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a0c7-311">See also</span></span>

[<span data-ttu-id="5a0c7-312">about_Providers</span><span class="sxs-lookup"><span data-stu-id="5a0c7-312">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="5a0c7-313">about_Signing</span><span class="sxs-lookup"><span data-stu-id="5a0c7-313">about_Signing</span></span>](../../Microsoft.PowerShell.Core/About/about_Signing.md)

[<span data-ttu-id="5a0c7-314">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="5a0c7-314">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)

[<span data-ttu-id="5a0c7-315">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="5a0c7-315">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[<span data-ttu-id="5a0c7-316">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="5a0c7-316">Get-PfxCertificate</span></span>](xref:Microsoft.PowerShell.Security.Get-PfxCertificate)
