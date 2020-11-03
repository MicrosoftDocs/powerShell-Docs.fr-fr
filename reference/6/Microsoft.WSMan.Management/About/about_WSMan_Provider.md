---
description: WSMan
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_wsman_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur WSMan
ms.openlocfilehash: 011383112d453a4fa88745c69b52e432709aa9d3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206801"
---
# <a name="wsman-provider"></a><span data-ttu-id="c103d-104">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="c103d-104">WSMan Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="c103d-105">Nom du fournisseur</span><span class="sxs-lookup"><span data-stu-id="c103d-105">Provider name</span></span>

<span data-ttu-id="c103d-106">WSMan</span><span class="sxs-lookup"><span data-stu-id="c103d-106">WSMan</span></span>

## <a name="drives"></a><span data-ttu-id="c103d-107">Lecteurs</span><span class="sxs-lookup"><span data-stu-id="c103d-107">Drives</span></span>

`WSMan:`

## <a name="short-description"></a><span data-ttu-id="c103d-108">Description courte</span><span class="sxs-lookup"><span data-stu-id="c103d-108">Short description</span></span>

<span data-ttu-id="c103d-109">Fournit l'accès aux informations de configuration de WS-Management (Web Services for Management).</span><span class="sxs-lookup"><span data-stu-id="c103d-109">Provides access to Web Services for Management (WS-Management) configuration information.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="c103d-110">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="c103d-110">Detailed description</span></span>

<span data-ttu-id="c103d-111">Le fournisseur **WSMan** pour PowerShell vous permet d’ajouter, de modifier, d’effacer et de supprimer des WS-Management données de configuration sur des ordinateurs locaux ou distants.</span><span class="sxs-lookup"><span data-stu-id="c103d-111">The **WSMan** provider for PowerShell lets you add, change, clear, and delete WS-Management configuration data on local or remote computers.</span></span>

<span data-ttu-id="c103d-112">Le fournisseur **WSMan** expose un lecteur PowerShell avec une structure de répertoires qui correspond à un regroupement logique de paramètres de configuration de WS-Management.</span><span class="sxs-lookup"><span data-stu-id="c103d-112">The **WSMan** provider exposes a PowerShell drive with a directory structure that corresponds to a logical grouping of WS-Management configuration settings.</span></span> <span data-ttu-id="c103d-113">Ces regroupements sont appelés des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="c103d-113">These groupings are known as containers.</span></span>

<span data-ttu-id="c103d-114">À compter de Windows PowerShell 3,0, le fournisseur **WSMan** a été mis à jour pour prendre en charge de nouvelles propriétés pour les configurations de session, telles que **OutputBufferingMode** .</span><span class="sxs-lookup"><span data-stu-id="c103d-114">Beginning in Windows PowerShell 3.0, the **WSMan** provider has been updated to support new properties for session configurations, such as **OutputBufferingMode** .</span></span> <span data-ttu-id="c103d-115">Les configurations de session s’affichent sous la forme d’éléments dans le répertoire de plug-in du `WSMan:` lecteur et les propriétés apparaissent en tant qu’éléments dans chaque configuration de session.</span><span class="sxs-lookup"><span data-stu-id="c103d-115">The session configurations appear as items in the Plugin directory of the `WSMan:` drive and the properties appear as items in each session configuration.</span></span>

<span data-ttu-id="c103d-116">Le fournisseur **WSMan** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.</span><span class="sxs-lookup"><span data-stu-id="c103d-116">The **WSMan** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="c103d-117">Get-Location</span><span class="sxs-lookup"><span data-stu-id="c103d-117">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="c103d-118">Set-Location</span><span class="sxs-lookup"><span data-stu-id="c103d-118">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="c103d-119">Get-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-119">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="c103d-120">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="c103d-120">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="c103d-121">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-121">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="c103d-122">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-122">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

> [!NOTE]
> <span data-ttu-id="c103d-123">Vous pouvez utiliser les commandes du `WSMan:` lecteur pour modifier les valeurs des nouvelles propriétés.</span><span class="sxs-lookup"><span data-stu-id="c103d-123">You can use commands in the `WSMan:` drive to change the values of the new properties.</span></span> <span data-ttu-id="c103d-124">Toutefois, vous ne pouvez pas utiliser le `WSMan:` lecteur dans powershell 2,0 pour modifier les propriétés introduites dans Windows powershell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c103d-124">However, you cannot use the `WSMan:` drive in PowerShell 2.0 to change properties that are introduced in Windows PowerShell 3.0.</span></span>
> <span data-ttu-id="c103d-125">Bien qu’aucune erreur ne soit générée, les commandes ne sont pas efficaces pour modifier ces paramètres, utilisez le lecteur **WSMan** dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c103d-125">Although no error is generated, the commands are not effective To change these settings, use the **WSMan** drive in Windows PowerShell 3.0.</span></span>

### <a name="organization-of-the-wsman-drive"></a><span data-ttu-id="c103d-126">Organisation du lecteur WSMan :</span><span class="sxs-lookup"><span data-stu-id="c103d-126">Organization of the WSMan: Drive</span></span>

- <span data-ttu-id="c103d-127">**Client** : vous pouvez configurer différents aspects du client WS-Management.</span><span class="sxs-lookup"><span data-stu-id="c103d-127">**Client** : You can configure various aspects of the WS-Management client.</span></span> <span data-ttu-id="c103d-128">Les informations de configuration sont stockées dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="c103d-128">The configuration information is stored in the registry.</span></span>

- <span data-ttu-id="c103d-129">**Service** : vous pouvez configurer différents aspects du service WS-Management.</span><span class="sxs-lookup"><span data-stu-id="c103d-129">**Service** : You can configure various aspects of the WS-Management service.</span></span>
  <span data-ttu-id="c103d-130">Les informations de configuration sont stockées dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="c103d-130">The configuration information is stored in the registry.</span></span>
  > [!NOTE]
  > <span data-ttu-id="c103d-131">La configuration du service est parfois appelée configuration du serveur.</span><span class="sxs-lookup"><span data-stu-id="c103d-131">Service configuration is sometimes referred to as Server configuration.</span></span>

- <span data-ttu-id="c103d-132">**Interpréteur** de commandes : vous pouvez configurer différents aspects de l’interpréteur de commandes WS-Management, comme le paramètre permettant l’accès au shell à distance ( **AllowRemoteShellAccess** ) et le nombre maximal d’utilisateurs simultanés autorisés ( **MaxConcurrentUsers** ).</span><span class="sxs-lookup"><span data-stu-id="c103d-132">**Shell** : You can configure various aspects of the WS-Management shell, such as the setting to allow remote shell access ( **AllowRemoteShellAccess** ) and the maximum number of concurrent users allowed ( **MaxConcurrentUsers** ).</span></span>

- <span data-ttu-id="c103d-133">**Écouteur** : vous pouvez créer et configurer un écouteur.</span><span class="sxs-lookup"><span data-stu-id="c103d-133">**Listener** : You can create and configure a listener.</span></span> <span data-ttu-id="c103d-134">Un écouteur est un service de gestion qui implémente le protocole WS-Management pour envoyer et recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="c103d-134">A listener is a management service that implements the WS-Management protocol to send and to receive messages.</span></span>

- <span data-ttu-id="c103d-135">**Plug-in** : les plug-ins sont chargés et utilisés par le service WS-Management pour fournir différentes fonctions.</span><span class="sxs-lookup"><span data-stu-id="c103d-135">**Plugin** : Plug-ins are loaded and used by the WS-Management service to provide various functions.</span></span> <span data-ttu-id="c103d-136">Par défaut, PowerShell fournit trois plug-ins :</span><span class="sxs-lookup"><span data-stu-id="c103d-136">By default, PowerShell provides three plug-ins:</span></span>
  - <span data-ttu-id="c103d-137">Plug-in de transfert d’événements.</span><span class="sxs-lookup"><span data-stu-id="c103d-137">The Event Forwarding plug-in.</span></span>
  - <span data-ttu-id="c103d-138">Le plug-in Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c103d-138">The Microsoft.PowerShell plug-in.</span></span>
  - <span data-ttu-id="c103d-139">Le plug-in du fournisseur Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="c103d-139">The Windows Management Instrumentation (WMI) Provider plug-in.</span></span>
  <span data-ttu-id="c103d-140">Ces trois plug-ins prennent en charge le transfert d’événements, la configuration et l’accès WMI.</span><span class="sxs-lookup"><span data-stu-id="c103d-140">These three plug-ins support event forwarding, configuration, and WMI access.</span></span>

- <span data-ttu-id="c103d-141">**ClientCertificate** : vous pouvez créer et configurer un certificat client.</span><span class="sxs-lookup"><span data-stu-id="c103d-141">**ClientCertificate** : You can create and configure a client certificate.</span></span>
  <span data-ttu-id="c103d-142">Un certificat client est utilisé quand le client WS-Management est configuré pour utiliser l'authentification par certificat.</span><span class="sxs-lookup"><span data-stu-id="c103d-142">A client certificate is used when the WS-Management client is configured to use certificate authentication.</span></span>

### <a name="directory-hierarchy-of-the-wsman-provider"></a><span data-ttu-id="c103d-143">Hiérarchie des répertoires du fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="c103d-143">Directory Hierarchy of the WSMan Provider</span></span>

<span data-ttu-id="c103d-144">La hiérarchie de répertoires du fournisseur WSMan pour l’ordinateur local est la suivante.</span><span class="sxs-lookup"><span data-stu-id="c103d-144">The directory hierarchy of the WSMan provider for the local computer is as follows.</span></span>

```
WSMan:\localhost
--- Client
--- Service
--- Shell
--- Listener
------ <Specific_Listener>
--- Plugin
------ Event Forwarding Plugin
--------- InitializationParameters
--------- Resources
------------ Security
------ Microsoft.Powershell
--------- InitializationParameters
--------- Resources
------------ Security
------ WMI Provider
--------- InitializationParameters
--------- Resources
------------ Security
--- ClientCertificate
```

<span data-ttu-id="c103d-145">La hiérarchie des répertoires du fournisseur WSMan pour un ordinateur distant est identique à celle d'un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c103d-145">The directory hierarchy of the WSMan provider for a remote computer is the same as a local computer.</span></span> <span data-ttu-id="c103d-146">Cependant, pour pouvoir accéder aux paramètres de configuration d'un ordinateur distant, vous devez établir une connexion avec l'ordinateur distant en utilisant [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span><span class="sxs-lookup"><span data-stu-id="c103d-146">However, in order to access the configuration settings of a remote computer, you need to make a connection to the remote computer using [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span></span> <span data-ttu-id="c103d-147">Une fois qu'une connexion est établie avec un ordinateur distant, le nom de l'ordinateur distant s'affiche dans le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c103d-147">Once a connection is made to a remote computer, the name of the remote computer shows up in the provider.</span></span>

```
WSMan:\<Remote_Computer_Name>
```

## <a name="navigating-the-wsman-drive"></a><span data-ttu-id="c103d-148">Navigation dans le lecteur WSMan :</span><span class="sxs-lookup"><span data-stu-id="c103d-148">Navigating the WSMan: Drive</span></span>

<span data-ttu-id="c103d-149">Cette commande utilise la `Set-Location` cmdlet pour modifier l’emplacement actuel sur le `WSMan:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="c103d-149">This command uses the `Set-Location` cmdlet to change the current location to the `WSMan:` drive.</span></span>

```powershell
Set-Location WSMan:
```

<span data-ttu-id="c103d-150">Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="c103d-150">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="c103d-151">Par exemple, tapez.</span><span class="sxs-lookup"><span data-stu-id="c103d-151">For example, type.</span></span>

```powershell
Set-Location C:
```

### <a name="navigating-to-a-remote-system-store-location"></a><span data-ttu-id="c103d-152">Navigation vers un emplacement du magasin système distant</span><span class="sxs-lookup"><span data-stu-id="c103d-152">Navigating to a remote system store location</span></span>

<span data-ttu-id="c103d-153">Cette commande utilise la `Set-Location` commande pour remplacer l’emplacement actuel par l’emplacement racine dans l’emplacement du magasin système distant.</span><span class="sxs-lookup"><span data-stu-id="c103d-153">This command uses the `Set-Location` command to change the current location to the root location in the remote system store location.</span></span> <span data-ttu-id="c103d-154">Utilisez une barre oblique inverse `\` ou une barre oblique `/` pour indiquer un niveau du `WSMan:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="c103d-154">Use a backslash `\` or forward slash `/` to indicate a level of the `WSMan:` drive.</span></span>

```powershell
Set-Location -Path  WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="c103d-155">La commande ci-dessus suppose qu'il existe déjà une connexion au système distant.</span><span class="sxs-lookup"><span data-stu-id="c103d-155">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="displaying-the-contents-of-the-wsman-drive"></a><span data-ttu-id="c103d-156">Affichage du contenu du lecteur WSMan :</span><span class="sxs-lookup"><span data-stu-id="c103d-156">Displaying the Contents of the WSMan: Drive</span></span>

<span data-ttu-id="c103d-157">Cette commande utilise l' `Get-Childitem` applet de commande pour afficher les WS-Management les magasins dans l’emplacement du magasin localhost.</span><span class="sxs-lookup"><span data-stu-id="c103d-157">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the Localhost store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\Localhost
```

<span data-ttu-id="c103d-158">Si vous êtes dans le `WSMan:` lecteur, vous pouvez omettre le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="c103d-158">If you are in the `WSMan:` drive, you can omit the drive name.</span></span>

<span data-ttu-id="c103d-159">Cette commande utilise l' `Get-Childitem` applet de commande pour afficher les magasins de WS-Management dans l’emplacement du magasin « SERVEUR01 » de l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="c103d-159">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the remote computer "SERVER01" store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="c103d-160">La commande ci-dessus suppose qu'il existe déjà une connexion au système distant.</span><span class="sxs-lookup"><span data-stu-id="c103d-160">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="setting-the-value-of-items-in-the--wsman-drive"></a><span data-ttu-id="c103d-161">Définition de la valeur des éléments dans le lecteur WSMAN :</span><span class="sxs-lookup"><span data-stu-id="c103d-161">Setting the value of items in the  WSMAN: drive</span></span>

<span data-ttu-id="c103d-162">Vous pouvez utiliser l' `Set-Item` applet de commande pour modifier les paramètres de configuration dans le `WSMAN` lecteur.</span><span class="sxs-lookup"><span data-stu-id="c103d-162">You can use the `Set-Item` cmdlet to change configuration settings in the `WSMAN` drive.</span></span> <span data-ttu-id="c103d-163">L’exemple suivant définit la valeur **TrustedHosts** pour accepter tous les ordinateurs hôtes avec le suffixe « contoso.com ».</span><span class="sxs-lookup"><span data-stu-id="c103d-163">The following example sets the **TrustedHosts** value to accept all hosts with the suffix "contoso.com".</span></span>

```powershell
# You do not need to specify the -Path parameter name when using Set-Item.
PS WSMAN:\localhost\Client> Set-Item .\TrustedHosts -Value "*.contoso.com"
```

<span data-ttu-id="c103d-164">L' `Set-Item` applet de commande prend en charge un paramètre supplémentaire `-Concatenate` qui ajoute une valeur au lieu de la modifier.</span><span class="sxs-lookup"><span data-stu-id="c103d-164">The `Set-Item` cmdlet supports an additional parameter `-Concatenate` that appends a value instead of changing it.</span></span> <span data-ttu-id="c103d-165">L’exemple suivant ajoute une nouvelle valeur « \*. domain2.com » à l’ancienne valeur stockée dans `TrustedHost:`</span><span class="sxs-lookup"><span data-stu-id="c103d-165">The following example will append a new value "\*.domain2.com" to the old value stored in `TrustedHost:`</span></span>

```powershell
Set-Item WSMAN:\localhost\Client\TrustedHosts *.domain2.com -Concatenate
```

## <a name="creating-items-in-the-wsman-drive"></a><span data-ttu-id="c103d-166">Création d’éléments dans le lecteur WSMAN :</span><span class="sxs-lookup"><span data-stu-id="c103d-166">Creating items in the WSMAN: drive</span></span>

### <a name="creating-a-new-listener"></a><span data-ttu-id="c103d-167">Création d’un nouvel écouteur</span><span class="sxs-lookup"><span data-stu-id="c103d-167">Creating a new listener</span></span>

<span data-ttu-id="c103d-168">L' `New-Item` applet de commande crée des éléments dans un lecteur du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c103d-168">The `New-Item` cmdlet creates items within a provider drive.</span></span> <span data-ttu-id="c103d-169">Chaque fournisseur a des types d’éléments différents que vous pouvez créer.</span><span class="sxs-lookup"><span data-stu-id="c103d-169">Each provider has different item types that you can create.</span></span> <span data-ttu-id="c103d-170">Dans le `WSMAN:` lecteur, vous pouvez créer des *écouteurs* que vous configurez pour recevoir les demandes distantes et y répondre.</span><span class="sxs-lookup"><span data-stu-id="c103d-170">In the `WSMAN:` drive, you can create *Listeners* which you configure to receive and respond to remote requests.</span></span> <span data-ttu-id="c103d-171">La commande suivante crée un nouvel écouteur HTTP à l’aide de l’applet de commande `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="c103d-171">The following command creates a new HTTP listener using the `New-Item` cmdlet.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Listener -Address * -Transport HTTP -force
```

### <a name="creating-a-new-plug-in"></a><span data-ttu-id="c103d-172">Création d’un nouveau plug-in</span><span class="sxs-lookup"><span data-stu-id="c103d-172">Creating a new plug-in</span></span>

<span data-ttu-id="c103d-173">Cette commande crée (enregistre) un plug-in pour le service WS-Management.</span><span class="sxs-lookup"><span data-stu-id="c103d-173">This command creates (registers) a plug-in for the WS-Management service.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin `
         -Plugin TestPlugin `
         -FileName %systemroot%\system32\WsmWmiPl.dll `
         -Resource http://schemas.dmtf.org/wbem/wscim/2/cim-schema `
         -SDKVersion 1 `
         -Capability "Get","Put","Invoke","Enumerate" `
         -XMLRenderingType text
```

### <a name="creating-a-new-resource-entry"></a><span data-ttu-id="c103d-174">Création d’une nouvelle entrée de ressource</span><span class="sxs-lookup"><span data-stu-id="c103d-174">Creating a new resource entry</span></span>

<span data-ttu-id="c103d-175">Cette commande crée une entrée de ressource dans le répertoire Resources d’un TestPlugin.</span><span class="sxs-lookup"><span data-stu-id="c103d-175">This command creates a resource entry in the Resources directory of a TestPlugin.</span></span> <span data-ttu-id="c103d-176">Cette commande suppose qu’un TestPlugin a été créé à l’aide d’une commande distincte.</span><span class="sxs-lookup"><span data-stu-id="c103d-176">This command assumes that a TestPlugin has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\Resources `
         -ResourceUri http://schemas.dmtf.org/wbem/wscim/3/cim-schema `
         -Capability "Enumerate"

```

### <a name="creating-a-new-security-entry-for-a-resource"></a><span data-ttu-id="c103d-177">Création d’une nouvelle entrée de sécurité pour une ressource</span><span class="sxs-lookup"><span data-stu-id="c103d-177">Creating a new security entry for a resource</span></span>

<span data-ttu-id="c103d-178">Cette commande crée une entrée de sécurité dans le répertoire Security de Resource_5967683 (une ressource spécifique).</span><span class="sxs-lookup"><span data-stu-id="c103d-178">This command creates a security entry in the Security directory of Resource_5967683 (a specific resource).</span></span> <span data-ttu-id="c103d-179">Cette commande suppose que l’entrée de ressource a été créée à l’aide d’une commande distincte.</span><span class="sxs-lookup"><span data-stu-id="c103d-179">This command assumes that the resource entry has been created using a separate command.</span></span>

```powershell
$path = "WSMan:\localhost\Plugin\TestPlugin\Resources\Resource_5967683"
New-Item -Path $path\Security `
         -Sddl "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GWGX;;;WD)"
```

### <a name="creating-a-new-client-certificate"></a><span data-ttu-id="c103d-180">Création d’un certificat client</span><span class="sxs-lookup"><span data-stu-id="c103d-180">Creating a new Client Certificate</span></span>

<span data-ttu-id="c103d-181">Cette commande crée l’entrée **ClientCertificate** qui peut être utilisée par le client WS-Management.</span><span class="sxs-lookup"><span data-stu-id="c103d-181">This command creates **ClientCertificate** entry that can be used by the WS-Management client.</span></span> <span data-ttu-id="c103d-182">Le nouveau **ClientCertificate** s’affichera sous le répertoire **ClientCertificate** en tant que « ClientCertificate_1234567890 ».</span><span class="sxs-lookup"><span data-stu-id="c103d-182">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="c103d-183">Tous les paramètres sont obligatoires.</span><span class="sxs-lookup"><span data-stu-id="c103d-183">All of the parameters are mandatory.</span></span> <span data-ttu-id="c103d-184">L' **émetteur** doit être l’empreinte numérique du certificat de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="c103d-184">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* `
         -Credential $cred;
```

### <a name="creating-a-new-initialization-parameter"></a><span data-ttu-id="c103d-185">Création d’un paramètre d’initialisation</span><span class="sxs-lookup"><span data-stu-id="c103d-185">Creating a new Initialization Parameter</span></span>

<span data-ttu-id="c103d-186">Cette commande crée un paramètre d’initialisation nommé « testparametername » dans le répertoire « InitializationParameters ».</span><span class="sxs-lookup"><span data-stu-id="c103d-186">This command creates an Initialization parameter named "testparametername" in the "InitializationParameters" directory.</span></span> <span data-ttu-id="c103d-187">Cette commande suppose que « TestPlugin » a été créé à l’aide d’une commande distincte.</span><span class="sxs-lookup"><span data-stu-id="c103d-187">This command assumes that the "TestPlugin" has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\InitializationParameters `
         -ParamName testparametername `
         -ParamValue testparametervalue
```

## <a name="dynamic-parameters"></a><span data-ttu-id="c103d-188">Paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="c103d-188">Dynamic parameters</span></span>

<span data-ttu-id="c103d-189">Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés par un fournisseur PowerShell et sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur activé par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c103d-189">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="address-string"></a><span data-ttu-id="c103d-190">Address \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-190">Address \<String\></span></span>

<span data-ttu-id="c103d-191">Spécifie l'adresse pour laquelle cet écouteur a été créé.</span><span class="sxs-lookup"><span data-stu-id="c103d-191">Specifies the address for which this listener was created.</span></span> <span data-ttu-id="c103d-192">Il peut s'agir de l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="c103d-192">The value can be one of the following:</span></span>

- <span data-ttu-id="c103d-193">Chaîne littérale « \* ».</span><span class="sxs-lookup"><span data-stu-id="c103d-193">The literal string "\*".</span></span> <span data-ttu-id="c103d-194">(Le caractère générique ( `*` ) permet à la commande de lier toutes les adresses IP sur toutes les cartes réseau.)</span><span class="sxs-lookup"><span data-stu-id="c103d-194">(The wildcard character (`*`) makes the command bind all the IP addresses on all the network adapters.)</span></span>
- <span data-ttu-id="c103d-195">Chaîne littérale « IP : » suivie d’une adresse IP valide au format décimal délimité par des points IPv4 ou au format hexadécimal cloné IPv6.</span><span class="sxs-lookup"><span data-stu-id="c103d-195">The literal string "IP:" followed by a valid IP address in either IPv4 dotted-decimal format or in IPv6 cloned-hexadecimal format.</span></span>
- <span data-ttu-id="c103d-196">Chaîne littérale « MAC : » suivie de l’adresse MAC d’un adaptateur.</span><span class="sxs-lookup"><span data-stu-id="c103d-196">The literal string "MAC:" followed by the MAC address of an adapter.</span></span>
  <span data-ttu-id="c103d-197">Par exemple : MAC : 32-a3-58 -90-a-CC.</span><span class="sxs-lookup"><span data-stu-id="c103d-197">For example: MAC:32-a3-58-90-be-cc.</span></span>

> [!NOTE]
> <span data-ttu-id="c103d-198">La valeur de Address est définie lors de la création d'un écouteur.</span><span class="sxs-lookup"><span data-stu-id="c103d-198">The Address value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-199">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-199">Cmdlets supported</span></span>

- [<span data-ttu-id="c103d-200">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-200">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="capability-enumeration"></a><span data-ttu-id="c103d-201">Capability \<Enumeration\></span><span class="sxs-lookup"><span data-stu-id="c103d-201">Capability \<Enumeration\></span></span>

<span data-ttu-id="c103d-202">Quand vous utilisez des *plug-ins* , ce paramètre spécifie une opération prise en charge sur cet Uniform Resource Identifier (Uri).</span><span class="sxs-lookup"><span data-stu-id="c103d-202">When working with *Plug-ins* this parameter specifies an operation that is supported on this Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="c103d-203">Vous devez créer une entrée pour chaque type d'opération pris en charge par l'URI.</span><span class="sxs-lookup"><span data-stu-id="c103d-203">You have to create one entry for each type of operation that the URI supports.</span></span> <span data-ttu-id="c103d-204">Vous pouvez spécifier des attributs valides pour une opération donnée, si l’opération la prend en charge.</span><span class="sxs-lookup"><span data-stu-id="c103d-204">You can specify any valid attributes for a given operation, if the operation supports it.</span></span>

<span data-ttu-id="c103d-205">Ces attributs incluent **SupportsFiltering** et **SupportsFragment** .</span><span class="sxs-lookup"><span data-stu-id="c103d-205">These attributes include **SupportsFiltering** and **SupportsFragment** .</span></span>

- <span data-ttu-id="c103d-206">**Créer** : les opérations Create sont prises en charge sur l’URI.</span><span class="sxs-lookup"><span data-stu-id="c103d-206">**Create** : Create operations are supported on the URI.</span></span>
  - <span data-ttu-id="c103d-207">L’attribut **SupportFragment**  est utilisé si l’opération de création prend en charge le concept.</span><span class="sxs-lookup"><span data-stu-id="c103d-207">The **SupportFragment**  attribute is used if the Create operation supports the concept.</span></span>
  - <span data-ttu-id="c103d-208">L’attribut **SupportFiltering** n’est pas valide pour les opérations Create et doit être défini sur « false ».</span><span class="sxs-lookup"><span data-stu-id="c103d-208">The **SupportFiltering** attribute is NOT valid for Create operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="c103d-209">Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="c103d-209">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="c103d-210">**Delete** : les opérations de suppression sont prises en charge sur l’URI.</span><span class="sxs-lookup"><span data-stu-id="c103d-210">**Delete** : Delete operations are supported on the URI.</span></span>
  - <span data-ttu-id="c103d-211">L’attribut **SupportFragment** est utilisé si l’opération de suppression prend en charge le concept.</span><span class="sxs-lookup"><span data-stu-id="c103d-211">The **SupportFragment** attribute is used if the Delete operation supports the concept.</span></span>
  - <span data-ttu-id="c103d-212">L’attribut **SupportFiltering** n’est pas valide pour les opérations DELETE et doit être défini sur « false ».</span><span class="sxs-lookup"><span data-stu-id="c103d-212">The **SupportFiltering** attribute is NOT valid for Delete operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="c103d-213">Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="c103d-213">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="c103d-214">**Énumérer** : les opérations d’énumération sont prises en charge sur l’URI.</span><span class="sxs-lookup"><span data-stu-id="c103d-214">**Enumerate** : Enumerate operations are supported on the URI.</span></span>
  - <span data-ttu-id="c103d-215">L’attribut **SupportFragment** n’est pas pris en charge pour les opérations d’énumération et doit avoir la valeur false.</span><span class="sxs-lookup"><span data-stu-id="c103d-215">The **SupportFragment** attribute is NOT supported for Enumerate operations and should be set to False.</span></span>
  - <span data-ttu-id="c103d-216">L’attribut **SupportFiltering** est valide, et si le plug-in prend en charge le filtrage, cet attribut doit avoir la valeur « true ».</span><span class="sxs-lookup"><span data-stu-id="c103d-216">The **SupportFiltering** attribute is valid, and if the plug-in supports filtering, this attribute should be set to "True".</span></span>
  > [!NOTE]
  > <span data-ttu-id="c103d-217">Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="c103d-217">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="c103d-218">**Obtient** : les opérations d’extraction sont prises en charge sur l’URI.</span><span class="sxs-lookup"><span data-stu-id="c103d-218">**Get** : Get operations are supported on the URI.</span></span>
  - <span data-ttu-id="c103d-219">L’attribut **SupportFragment** est utilisé si l’opération d’extraction prend en charge le concept.</span><span class="sxs-lookup"><span data-stu-id="c103d-219">The **SupportFragment** attribute is used if the Get operation supports the concept.</span></span>
  - <span data-ttu-id="c103d-220">L’attribut **SupportFiltering** n’est pas valide pour les opérations d’extraction et doit être défini sur « false ».</span><span class="sxs-lookup"><span data-stu-id="c103d-220">The **SupportFiltering** attribute is NOT valid for Get operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="c103d-221">Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="c103d-221">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="c103d-222">**Invoke** : les opérations d’appel sont prises en charge sur l’URI.</span><span class="sxs-lookup"><span data-stu-id="c103d-222">**Invoke** : Invoke operations are supported on the URI.</span></span>
  - <span data-ttu-id="c103d-223">L’attribut **SupportFragment** n’est pas pris en charge pour les opérations d’appel et doit avoir la valeur false.</span><span class="sxs-lookup"><span data-stu-id="c103d-223">The **SupportFragment** attribute is not supported for Invoke operations and should be set to False.</span></span>
  - <span data-ttu-id="c103d-224">L’attribut **SupportFiltering** n’est pas valide et doit être défini sur « false ».</span><span class="sxs-lookup"><span data-stu-id="c103d-224">The **SupportFiltering** attribute is not valid and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="c103d-225">Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="c103d-225">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="c103d-226">**Put** : les opérations put sont prises en charge sur l’URI.</span><span class="sxs-lookup"><span data-stu-id="c103d-226">**Put** : Put operations are supported on the URI.</span></span>
  - <span data-ttu-id="c103d-227">L’attribut **SupportFragment** est utilisé si l’opération put prend en charge le concept.</span><span class="sxs-lookup"><span data-stu-id="c103d-227">The **SupportFragment** attribute is used if the Put operation supports the concept.</span></span>
  - <span data-ttu-id="c103d-228">L’attribut **SupportFiltering** n’est pas valide pour les opérations put et doit être défini sur « false ».</span><span class="sxs-lookup"><span data-stu-id="c103d-228">The **SupportFiltering** attribute is not valid for Put operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="c103d-229">Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="c103d-229">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="c103d-230">**Subscribe** : les opérations d’abonnement sont prises en charge sur l’URI.</span><span class="sxs-lookup"><span data-stu-id="c103d-230">**Subscribe** : Subscribe operations are supported on the URI.</span></span>
  - <span data-ttu-id="c103d-231">L’attribut **SupportFragment** n’est pas pris en charge pour les opérations subscribe et doit être défini sur false.</span><span class="sxs-lookup"><span data-stu-id="c103d-231">The **SupportFragment** attribute is not supported for Subscribe operations and should be set to False.</span></span>
  - <span data-ttu-id="c103d-232">L’attribut **SupportFiltering** n’est pas valide pour les opérations subscribe et doit être défini sur « false ».</span><span class="sxs-lookup"><span data-stu-id="c103d-232">The **SupportFiltering** attribute is not valid for Subscribe operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="c103d-233">Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="c103d-233">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="c103d-234">**Shell** : les opérations Shell sont prises en charge sur l’URI.</span><span class="sxs-lookup"><span data-stu-id="c103d-234">**Shell** : Shell operations are supported on the URI.</span></span>
  - <span data-ttu-id="c103d-235">L’attribut **SupportFragment** n’est pas pris en charge pour les opérations de Shell et doit être défini sur « false ».</span><span class="sxs-lookup"><span data-stu-id="c103d-235">The **SupportFragment** attribute is not supported for Shell operations and should be set to "False".</span></span>
  - <span data-ttu-id="c103d-236">L’attribut **SupportFiltering** n’est pas valide pour les opérations de Shell et doit être défini sur « false ».</span><span class="sxs-lookup"><span data-stu-id="c103d-236">The **SupportFiltering** attribute is not valid for Shell operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="c103d-237">Cette opération n’est pas valide pour un URI si une autre opération est également prise en charge.</span><span class="sxs-lookup"><span data-stu-id="c103d-237">This operation is not valid for a URI if ANY other operation is also supported.</span></span>
  > [!NOTE]
  > <span data-ttu-id="c103d-238">Si une opération Shell est configurée pour un URI, les opérations Get, Put, Create, Delete, Invoke et Enumerate sont traitées en interne dans le service WS-Management (WinRM) pour gérer les interpréteurs de commandes.</span><span class="sxs-lookup"><span data-stu-id="c103d-238">If a Shell operation is configured for a URI, Get, Put, Create, Delete, Invoke, and Enumerate operations are processed internally within the WS-Management (WinRM) service to manage shells.</span></span> <span data-ttu-id="c103d-239">Par conséquent, le plug-in ne peut pas gérer les opérations.</span><span class="sxs-lookup"><span data-stu-id="c103d-239">As a result, the plug-in cannot handle the operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-240">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-240">Cmdlets supported</span></span>

- [<span data-ttu-id="c103d-241">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-241">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="certificatethumbprint-string"></a><span data-ttu-id="c103d-242">CertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-242">CertificateThumbprint \<String\></span></span>

<span data-ttu-id="c103d-243">Spécifie l'empreinte numérique du certificat de service.</span><span class="sxs-lookup"><span data-stu-id="c103d-243">Specifies the thumbprint of the service certificate.</span></span>

<span data-ttu-id="c103d-244">Cette valeur représente la chaîne de valeurs hexadécimales à deux chiffres du champ Thumbprint du certificat.</span><span class="sxs-lookup"><span data-stu-id="c103d-244">This value represents the string of two-digit hexadecimal values in the Thumbprint field of the certificate.</span></span> <span data-ttu-id="c103d-245">Elle spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'effectuer cette action.</span><span class="sxs-lookup"><span data-stu-id="c103d-245">It specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="c103d-246">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="c103d-246">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="c103d-247">Ils peuvent être mappés uniquement à des comptes d'utilisateurs locaux ; ils ne fonctionnent pas avec des comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="c103d-247">They can be mapped only to local user accounts, and they do not work with domain accounts.</span></span> <span data-ttu-id="c103d-248">Pour obtenir une empreinte numérique de certificat, utilisez les `Get-Item` `Get-ChildItem` applets de commande ou dans le `Cert:` lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c103d-248">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` cmdlets in the PowerShell `Cert:` drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-249">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-249">Cmdlets supported</span></span>

- [<span data-ttu-id="c103d-250">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-250">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="enabled-boolean"></a><span data-ttu-id="c103d-251">Enabled \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="c103d-251">Enabled \<Boolean\></span></span>

<span data-ttu-id="c103d-252">Spécifie si l'écouteur est activé ou désactivé.</span><span class="sxs-lookup"><span data-stu-id="c103d-252">Specifies whether the listener is enabled or disabled.</span></span> <span data-ttu-id="c103d-253">La valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="c103d-253">The default is True.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-254">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-254">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-255">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-255">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="filename-plugin-string"></a><span data-ttu-id="c103d-256">FileName (Plugin) \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-256">FileName (Plugin) \<String\></span></span>

<span data-ttu-id="c103d-257">Spécifie le nom de fichier du plug-in d’opérations.</span><span class="sxs-lookup"><span data-stu-id="c103d-257">Specifies the file name of the operations plug-in.</span></span> <span data-ttu-id="c103d-258">Toutes les variables d’environnement qui sont placées dans cette entrée seront étendues dans le contexte de l’utilisateur lors de la réception d’une demande.</span><span class="sxs-lookup"><span data-stu-id="c103d-258">Any environment variables that are put in this entry will be expanded in the users' context when a request is received.</span></span> <span data-ttu-id="c103d-259">Étant donné que chaque utilisateur peut avoir une version différente de la même variable d’environnement, chaque utilisateur peut avoir un plug-in différent.</span><span class="sxs-lookup"><span data-stu-id="c103d-259">Because each user could have a different version of the same environment variable, each user could have a different plug-in.</span></span> <span data-ttu-id="c103d-260">Cette entrée ne peut pas être vide et doit pointer vers un plug-in valide.</span><span class="sxs-lookup"><span data-stu-id="c103d-260">This entry cannot be blank and must point to a valid plug-in.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-261">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-261">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-262">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-262">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="hostname-string"></a><span data-ttu-id="c103d-263">HostName \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-263">HostName \<String\></span></span>

<span data-ttu-id="c103d-264">Spécifie le nom d'hôte de l'ordinateur sur lequel s'exécute le service WS-Management (WinRM).</span><span class="sxs-lookup"><span data-stu-id="c103d-264">Specifies the host name of the computer on which the WS-Management (WinRM) service is running.</span></span>

<span data-ttu-id="c103d-265">La valeur doit être un nom de domaine complet, une chaîne littérale IPv4 ou IPv6, ou un caractère générique.</span><span class="sxs-lookup"><span data-stu-id="c103d-265">The value must be a fully qualified domain name, an IPv4 or IPv6 literal string, or a wildcard character.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-266">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-266">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-267">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-267">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="issuer-string"></a><span data-ttu-id="c103d-268">Issuer \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-268">Issuer \<String\></span></span>

<span data-ttu-id="c103d-269">Spécifie le nom de l'autorité de certification qui a émis le certificat.</span><span class="sxs-lookup"><span data-stu-id="c103d-269">Specifies the name of the certification authority that issued the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-270">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-270">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-271">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-271">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="plugin--ws-management-plug-ins-are-native-dynamic-link-libraries-dlls"></a><span data-ttu-id="c103d-272">\<\>Les plug-ins WS-Management plug-ins sont des bibliothèques de liens dynamiques (dll) natives</span><span class="sxs-lookup"><span data-stu-id="c103d-272">Plugin \<\> WS-Management plug-ins are native dynamic link libraries (DLLs)</span></span>

<span data-ttu-id="c103d-273">Cela permet de s’intégrer à et d’étendre les fonctionnalités de WS-Management.</span><span class="sxs-lookup"><span data-stu-id="c103d-273">that plug in to and extend the functionality of WS-Management .</span></span> <span data-ttu-id="c103d-274">L’API de plug-in WSW-Management fournit des fonctionnalités qui permettent à un utilisateur d’écrire des plug-ins en implémentant certaines API pour les opérations et les URI de ressources pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c103d-274">The WSW-Management Plug-in API provides functionality that enables a user to write plug-ins by implementing certain APIs for supported resource URIs and operations.</span></span> <span data-ttu-id="c103d-275">Une fois les plug-ins configurés pour le service WS-Management (WinRM) ou pour IIS (Internet Information Services), ces plug-ins sont chargés respectivement dans l'hôte de WS-Management ou dans l'hôte IIS.</span><span class="sxs-lookup"><span data-stu-id="c103d-275">After the plug-ins are configured for either the WS-Management (WinRM) service or for Internet Information Services (IIS), the plug-ins are loaded in the WS-Management host or in the IIS host, respectively.</span></span> <span data-ttu-id="c103d-276">Les requêtes distantes sont routées vers ces points d'entrée du plug-in pour effectuer des opérations.</span><span class="sxs-lookup"><span data-stu-id="c103d-276">Remote requests are routed to these plug-in entry points to perform operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-277">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-277">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-278">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-278">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="port-unsigned-short-integer"></a><span data-ttu-id="c103d-279">Port \<Unsigned Short Integer\></span><span class="sxs-lookup"><span data-stu-id="c103d-279">Port \<Unsigned Short Integer\></span></span>

<span data-ttu-id="c103d-280">Spécifie le port TCP pour lequel cet écouteur est créé.</span><span class="sxs-lookup"><span data-stu-id="c103d-280">Specifies the TCP port for which this listener is created.</span></span> <span data-ttu-id="c103d-281">Vous pouvez spécifier n'importe quelle valeur comprise entre 1 et 65 535.</span><span class="sxs-lookup"><span data-stu-id="c103d-281">You can specify any value from 1 through 65535.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-282">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-282">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-283">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-283">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="c103d-284">Resource \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-284">Resource \<String\></span></span>

<span data-ttu-id="c103d-285">Spécifie un point de terminaison qui représente un type distinct d'opération ou de valeur de gestion.</span><span class="sxs-lookup"><span data-stu-id="c103d-285">Specifies an endpoint that represents a distinct type of management operation or value.</span></span> <span data-ttu-id="c103d-286">Un service expose une ou plusieurs ressources, et des ressources peuvent avoir plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="c103d-286">A service exposes one or more resources, and some resources can have more than one instance.</span></span> <span data-ttu-id="c103d-287">Une ressource de gestion est similaire à une classe WMI ou à une table de base de données, et une instance est similaire à une instance de la classe ou à une ligne dans la table.</span><span class="sxs-lookup"><span data-stu-id="c103d-287">A management resource is similar to a WMI class or to a database table, and an instance is similar to an instance of the class or to a row in the table.</span></span> <span data-ttu-id="c103d-288">Par exemple, la classe **Win32_LogicalDisk** représente une ressource.</span><span class="sxs-lookup"><span data-stu-id="c103d-288">For example, the **Win32_LogicalDisk** class represents a resource.</span></span> <span data-ttu-id="c103d-289">`Win32_LogicalDisk="C:\\"` est une instance spécifique de la ressource.</span><span class="sxs-lookup"><span data-stu-id="c103d-289">`Win32_LogicalDisk="C:\\"` is a specific instance of the resource.</span></span>

<span data-ttu-id="c103d-290">Un URI contient un préfixe et un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="c103d-290">A Uniform Resource Identifier (URI) contains a prefix and a path to a resource.</span></span>
<span data-ttu-id="c103d-291">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c103d-291">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-292">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-292">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-293">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-293">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="c103d-294">Resource \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-294">Resource \<String\></span></span>

<span data-ttu-id="c103d-295">Spécifie l'URI (Uniform Resource Identifier) qui identifie un type de ressource spécifique, comme un disque ou un processus, sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c103d-295">Specifies the Uniform Resource Identifier (URI) that identifies a specific type of resource, such as a disk or a process, on a computer.</span></span>

<span data-ttu-id="c103d-296">Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="c103d-296">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="c103d-297">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c103d-297">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-298">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-298">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-299">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-299">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sdkversion-string"></a><span data-ttu-id="c103d-300">SDKVersion \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-300">SDKVersion \<String\></span></span>

<span data-ttu-id="c103d-301">Spécifie la version du Kit de développement logiciel (SDK) du plug-in WS-Management.</span><span class="sxs-lookup"><span data-stu-id="c103d-301">Specifies the version of the WS-Management plug-in SDK.</span></span> <span data-ttu-id="c103d-302">La seule valeur valide est </span><span class="sxs-lookup"><span data-stu-id="c103d-302">The only valid value is</span></span>
1.

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-303">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-303">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-304">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-304">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="subject-string"></a><span data-ttu-id="c103d-305">Subject \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-305">Subject \<String\></span></span>

<span data-ttu-id="c103d-306">Spécifie l'entité qui est identifiée par le certificat.</span><span class="sxs-lookup"><span data-stu-id="c103d-306">Specifies the entity that is identified by the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-307">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-307">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-308">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-308">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="transport-string"></a><span data-ttu-id="c103d-309">Transport \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-309">Transport \<String\></span></span>

<span data-ttu-id="c103d-310">Spécifie le transport à utiliser pour envoyer et recevoir les demandes et les réponses du protocole WS-Management.</span><span class="sxs-lookup"><span data-stu-id="c103d-310">Specifies the transport to use to send and receive WS-Management protocol requests and responses.</span></span> <span data-ttu-id="c103d-311">La valeur doit être HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c103d-311">The value must be either HTTP or HTTPS.</span></span>

<span data-ttu-id="c103d-312">Remarque : la valeur de transport est définie lors de la création d’un écouteur.</span><span class="sxs-lookup"><span data-stu-id="c103d-312">Note: The Transport value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-313">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-313">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-314">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-314">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="uri-string"></a><span data-ttu-id="c103d-315">URI \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-315">URI \<String\></span></span>

<span data-ttu-id="c103d-316">Identifie l'URI pour lequel l'accès est autorisé en fonction de la valeur du paramètre Sddl.</span><span class="sxs-lookup"><span data-stu-id="c103d-316">Identifies the URI for which access is authorized based on the value of the Sddl parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-317">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-317">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-318">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-318">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="urlprefix-string"></a><span data-ttu-id="c103d-319">URLPrefix \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-319">URLPrefix \<String\></span></span>

<span data-ttu-id="c103d-320">Un préfixe d'URL sur laquelle accepter les demandes HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c103d-320">A URL prefix on which to accept HTTP or HTTPS requests.</span></span> <span data-ttu-id="c103d-321">Il s’agit d’une chaîne contenant uniquement les caractères,,, le trait de `[a-z]` `[A-Z]` `[9-0]` soulignement ( `_` ) et la barre oblique inverse ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="c103d-321">This is a string containing only the characters `[a-z]`, `[A-Z]`, `[9-0]`, underscore (`_`) and backslash (`/`).</span></span> <span data-ttu-id="c103d-322">La chaîne ne doit pas commencer par une barre oblique inverse () ni se terminer par une barre oblique inverse ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="c103d-322">The string must not start with or end with a backslash (`/`).</span></span> <span data-ttu-id="c103d-323">Par exemple, si le nom de l’ordinateur est « Exempleordinateur », le client WS-Management spécifie `http://SampleMachine/URLPrefix` dans l’adresse de destination.</span><span class="sxs-lookup"><span data-stu-id="c103d-323">For example, if the computer name is "SampleComputer", the WS-Management client would specify `http://SampleMachine/URLPrefix` in the destination address.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-324">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-324">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-325">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-325">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="value-string"></a><span data-ttu-id="c103d-326">Value \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-326">Value \<String\></span></span>

<span data-ttu-id="c103d-327">Spécifie la valeur d'un paramètre d'initialisation, qui est une valeur spécifique au plug-in et qui est utilisée pour spécifier des options de configuration.</span><span class="sxs-lookup"><span data-stu-id="c103d-327">Specifies the value of an initialization parameter, which is a plug-in-specific value that is used to specify configuration options.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-328">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-328">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-329">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-329">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="xmlrenderingtype-string"></a><span data-ttu-id="c103d-330">XMLRenderingType \<String\></span><span class="sxs-lookup"><span data-stu-id="c103d-330">XMLRenderingType \<String\></span></span>

<span data-ttu-id="c103d-331">Spécifie le format dans lequel le code XML est passé aux plug-ins via l’objet **WSMAN_DATA** .</span><span class="sxs-lookup"><span data-stu-id="c103d-331">Specifies the format in which XML is passed to plug-ins through the **WSMAN_DATA** object.</span></span> <span data-ttu-id="c103d-332">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c103d-332">The following are valid values:</span></span>

- <span data-ttu-id="c103d-333">Texte : les données XML entrantes sont contenues dans une structure **WSMAN_DATA_TYPE_TEXT** , qui représente le XML sous la forme d’une mémoire tampon **PCWSTR** .</span><span class="sxs-lookup"><span data-stu-id="c103d-333">Text: Incoming XML data is contained in a **WSMAN_DATA_TYPE_TEXT** structure, which represents the XML as a **PCWSTR** memory buffer.</span></span>
- <span data-ttu-id="c103d-334">XMLReader : les données XML entrantes sont contenues dans une structure **WSMAN_DATA_TYPE_WS_XML_READER** , qui représente le XML sous la forme d’un objet **XmlReader** , qui est défini dans le fichier d’en-tête « WebServices. h ».</span><span class="sxs-lookup"><span data-stu-id="c103d-334">XMLReader: Incoming XML data is contained in a **WSMAN_DATA_TYPE_WS_XML_READER** structure, which represents the XML as an **XmlReader** object, which is defined in the "WebServices.h" header file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="c103d-335">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="c103d-335">Cmdlets Supported</span></span>

- [<span data-ttu-id="c103d-336">New-Item</span><span class="sxs-lookup"><span data-stu-id="c103d-336">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="c103d-337">Utilisation du pipeline</span><span class="sxs-lookup"><span data-stu-id="c103d-337">Using the pipeline</span></span>

<span data-ttu-id="c103d-338">Les applets de commande du fournisseur acceptent l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="c103d-338">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="c103d-339">Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c103d-339">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="c103d-340">Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.</span><span class="sxs-lookup"><span data-stu-id="c103d-340">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="c103d-341">Obtenir de l’aide</span><span class="sxs-lookup"><span data-stu-id="c103d-341">Getting help</span></span>

<span data-ttu-id="c103d-342">Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="c103d-342">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="c103d-343">Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) dans un lecteur du système de fichiers ou utilisez le `-Path` paramètre de la commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) pour spécifier un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="c103d-343">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path wsman:
```

## <a name="see-also"></a><span data-ttu-id="c103d-344">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c103d-344">See also</span></span>

[<span data-ttu-id="c103d-345">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c103d-345">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)
