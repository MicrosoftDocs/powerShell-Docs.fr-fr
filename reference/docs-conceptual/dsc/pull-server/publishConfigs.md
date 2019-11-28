---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Publier sur un serveur Pull à l’aide d’ID de configuration (v4/v5)
ms.openlocfilehash: 3b094308338e62c783b19f4d3bb41634feee63f6
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417260"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="e6009-103">Publier sur un serveur Pull à l’aide d’ID de configuration (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="e6009-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="e6009-104">Les sections ci-dessous supposent que vous avez déjà configuré un serveur Pull.</span><span class="sxs-lookup"><span data-stu-id="e6009-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="e6009-105">Si vous n’avez pas configuré votre serveur Pull, vous pouvez utiliser les guides suivants :</span><span class="sxs-lookup"><span data-stu-id="e6009-105">If you haven't set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="e6009-106">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="e6009-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="e6009-107">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="e6009-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="e6009-108">Chaque nœud cible peut être configuré pour télécharger les configurations et les ressources, et même pour signaler son état.</span><span class="sxs-lookup"><span data-stu-id="e6009-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="e6009-109">Cet article montre comment charger des ressources afin qu’elles soient disponibles pour être téléchargées, et comment configurer les clients pour télécharger automatiquement des ressources.</span><span class="sxs-lookup"><span data-stu-id="e6009-109">This article shows you how to upload resources so they're available to be downloaded, and configure clients to automatically download resources.</span></span> <span data-ttu-id="e6009-110">Lorsque le nœud reçoit une configuration attribuée, via un serveur **Pull** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la configuration depuis l’emplacement spécifié dans le gestionnaire de configuration local (LCM).</span><span class="sxs-lookup"><span data-stu-id="e6009-110">When the node receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the Local Configuration Manager (LCM).</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="e6009-111">Compiler les configurations</span><span class="sxs-lookup"><span data-stu-id="e6009-111">Compile configurations</span></span>

<span data-ttu-id="e6009-112">La première étape pour stocker des [configurations](../configurations/configurations.md) sur un serveur Pull consiste à les compiler dans des fichiers `.mof`.</span><span class="sxs-lookup"><span data-stu-id="e6009-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into `.mof` files.</span></span> <span data-ttu-id="e6009-113">Pour effectuer une configuration générique et applicable à d’autres clients, utilisez `localhost` dans votre bloc de nœud.</span><span class="sxs-lookup"><span data-stu-id="e6009-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="e6009-114">L’exemple ci-dessous montre un interpréteur de commandes de configuration qui utilise `localhost` plutôt qu’un nom de client spécifique.</span><span class="sxs-lookup"><span data-stu-id="e6009-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="e6009-115">Une fois que vous avez compilé votre configuration générique, vous deez disposer d’un fichier `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="e6009-115">Once you've compiled your generic configuration, you should have a `localhost.mof` file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="e6009-116">Renommer le fichier MOF</span><span class="sxs-lookup"><span data-stu-id="e6009-116">Renaming the MOF file</span></span>

<span data-ttu-id="e6009-117">Vous pouvez stocker des fichiers de configuration `.mof` sur un serveur Pull à l’aide de **ConfigurationName** ou de **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="e6009-117">You can store Configuration `.mof` files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="e6009-118">Selon la façon dont vous souhaitez configurer vos clients Pull, vous pouvez choisir une section ci-dessous afin de renommer correctement vos fichiers `.mof` compilés.</span><span class="sxs-lookup"><span data-stu-id="e6009-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled `.mof` files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="e6009-119">ID (GUID) de configuration</span><span class="sxs-lookup"><span data-stu-id="e6009-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="e6009-120">Vous devez renommer votre fichier `localhost.mof` en fichier `<GUID>.mof`.</span><span class="sxs-lookup"><span data-stu-id="e6009-120">You'll need to rename your `localhost.mof` file to `<GUID>.mof` file.</span></span> <span data-ttu-id="e6009-121">Vous pouvez créer un **GUID** aléatoire à l’aide de l’exemple ci-dessous, ou en utilisant l’applet de commande [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid).</span><span class="sxs-lookup"><span data-stu-id="e6009-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="e6009-122">Sortie exemple</span><span class="sxs-lookup"><span data-stu-id="e6009-122">Sample Output</span></span>

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="e6009-123">Vous pouvez ensuite renommer votre fichier `.mof` à l’aide de n’importe quelle méthode valide.</span><span class="sxs-lookup"><span data-stu-id="e6009-123">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="e6009-124">L’exemple ci-dessous utilise l’applet de commande [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).</span><span class="sxs-lookup"><span data-stu-id="e6009-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="e6009-125">Pour plus d’informations sur l’utilisation des **GUID** dans votre environnement, consultez [Planifier les GUID](/powershell/scripting/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="e6009-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/scripting/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="e6009-126">Noms de configuration</span><span class="sxs-lookup"><span data-stu-id="e6009-126">Configuration names</span></span>

<span data-ttu-id="e6009-127">Vous devez renommer votre fichier `localhost.mof` en fichier `<Configuration Name>.mof`.</span><span class="sxs-lookup"><span data-stu-id="e6009-127">You'll need to rename your `localhost.mof` file to `<Configuration Name>.mof` file.</span></span> <span data-ttu-id="e6009-128">L’exemple suivant utilise le nom de la configuration de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="e6009-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="e6009-129">Vous pouvez ensuite renommer votre fichier `.mof` à l’aide de n’importe quelle méthode valide.</span><span class="sxs-lookup"><span data-stu-id="e6009-129">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="e6009-130">L’exemple ci-dessous utilise l’applet de commande [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).</span><span class="sxs-lookup"><span data-stu-id="e6009-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="e6009-131">Créer la somme de contrôle</span><span class="sxs-lookup"><span data-stu-id="e6009-131">Create the checkSum</span></span>

<span data-ttu-id="e6009-132">Chaque fichier `.mof` stocké sur un serveur Pull ou sur un partage SMB doit être associé à un fichier `.checksum`.</span><span class="sxs-lookup"><span data-stu-id="e6009-132">Each `.mof` file stored on a Pull Server, or SMB share needs to have an associated `.checksum` file.</span></span>
<span data-ttu-id="e6009-133">Ce fichier permet aux clients de savoir quand le fichier `.mof` associé a changé et doit être téléchargé à nouveau.</span><span class="sxs-lookup"><span data-stu-id="e6009-133">This file lets clients know when the associated `.mof` file has changed and should be downloaded again.</span></span>

<span data-ttu-id="e6009-134">Vous pouvez créer une **somme de contrôle** à l’aide de l’applet de commande [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum).</span><span class="sxs-lookup"><span data-stu-id="e6009-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="e6009-135">Vous pouvez également exécuter `New-DSCCheckSum` dans un répertoire de fichiers à l’aide du paramètre `-Path`.</span><span class="sxs-lookup"><span data-stu-id="e6009-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span>
<span data-ttu-id="e6009-136">Si une somme de contrôle existe déjà, vous pouvez forcer sa recréation avec le paramètre `-Force`.</span><span class="sxs-lookup"><span data-stu-id="e6009-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="e6009-137">L’exemple suivant a spécifié un répertoire contenant le fichier `.mof` à partir de la section précédente et utilise le paramètre `-Force`.</span><span class="sxs-lookup"><span data-stu-id="e6009-137">The following example specified a directory containing the `.mof` file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="e6009-138">Aucune sortie ne s’affiche, mais vous devez maintenant voir un fichier `<GUID or Configuration Name>.mof.checksum`.</span><span class="sxs-lookup"><span data-stu-id="e6009-138">No output will be shown, but you should now see a `<GUID or Configuration Name>.mof.checksum` file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="e6009-139">Emplacement de stockage des fichiers MOF et sommes de contrôle</span><span class="sxs-lookup"><span data-stu-id="e6009-139">Where to store MOF files and checkSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="e6009-140">Sur un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="e6009-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="e6009-141">Lorsque vous configurez votre serveur Pull HTTP, comme expliqué dans la section [Configurer un serveur Pull HTTP DSC](pullServer.md), vous spécifiez des répertoires pour les clés **ModulePath** et **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="e6009-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="e6009-142">La clé **ModulePath** indique l’emplacement de stockage des fichiers `.zip` empaquetés d’un module.</span><span class="sxs-lookup"><span data-stu-id="e6009-142">The **ModulePath** key indicates where a module's packaged `.zip` files should be stored.</span></span> <span data-ttu-id="e6009-143">La clé **ConfigurationPath** indique l’emplacement où tous les fichiers `.mof` et `.checksum` doivent être stockés.</span><span class="sxs-lookup"><span data-stu-id="e6009-143">The **ConfigurationPath** indicates where any `.mof` files and `.checksum` files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="e6009-144">Sur un partage SMB</span><span class="sxs-lookup"><span data-stu-id="e6009-144">On an SMB share</span></span>

<span data-ttu-id="e6009-145">Lorsque vous configurez un client Pull pour utiliser un partage SMB, vous spécifiez une clé **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="e6009-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span>
<span data-ttu-id="e6009-146">Tous les fichiers `.mof` et `.checksum` doivent alors être stockés dans le répertoire **SourcePath** du bloc **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="e6009-146">All `.mof` files and `.checksum` files should be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="e6009-147">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e6009-147">Next steps</span></span>

<span data-ttu-id="e6009-148">Vous devez ensuite configurer les clients Pull pour extraire la configuration spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e6009-148">Next, you'll want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="e6009-149">Pour plus d’informations, consultez l’un des guides suivants :</span><span class="sxs-lookup"><span data-stu-id="e6009-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="e6009-150">Configurer un client Pull à l’aide d’ID de configuration (v4)</span><span class="sxs-lookup"><span data-stu-id="e6009-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="e6009-151">Configurer un client Pull à l’aide d’ID de configuration (v5)</span><span class="sxs-lookup"><span data-stu-id="e6009-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="e6009-152">Configurer un client Pull à l’aide de noms de configuration (v5)</span><span class="sxs-lookup"><span data-stu-id="e6009-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="e6009-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6009-153">See also</span></span>

- [<span data-ttu-id="e6009-154">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="e6009-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="e6009-155">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="e6009-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="e6009-156">Empaqueter et charger des ressources vers un serveur Pull</span><span class="sxs-lookup"><span data-stu-id="e6009-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
