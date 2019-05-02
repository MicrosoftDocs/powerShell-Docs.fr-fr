---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Publier sur un serveur Pull à l’aide d’ID de configuration (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079504"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="717d7-103">Publier sur un serveur Pull à l’aide d’ID de configuration (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="717d7-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="717d7-104">Les sections ci-dessous supposent que vous avez déjà configuré un serveur Pull.</span><span class="sxs-lookup"><span data-stu-id="717d7-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="717d7-105">Si vous n’avez pas configuré votre serveur Pull, vous pouvez utiliser les guides suivants :</span><span class="sxs-lookup"><span data-stu-id="717d7-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="717d7-106">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="717d7-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="717d7-107">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="717d7-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="717d7-108">Chaque nœud cible peut être configuré pour télécharger les configurations et les ressources, et même pour signaler son état.</span><span class="sxs-lookup"><span data-stu-id="717d7-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="717d7-109">Cet article montre comment uploader des ressources afin qu’elles soient disponibles pour être téléchargées, et comment configurer les clients pour télécharger automatiquement des ressources.</span><span class="sxs-lookup"><span data-stu-id="717d7-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="717d7-110">Lorsque le nœud reçoit une configuration attribuée, via un serveur **Pull** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la configuration depuis l’emplacement spécifié dans le gestionnaire de configuration local (LCM).</span><span class="sxs-lookup"><span data-stu-id="717d7-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="717d7-111">Compiler les configurations</span><span class="sxs-lookup"><span data-stu-id="717d7-111">Compile Configurations</span></span>

<span data-ttu-id="717d7-112">La première étape pour stocker des [configurations](../configurations/configurations.md) sur un serveur Pull, consiste à les compiler dans des fichiers « .mof ».</span><span class="sxs-lookup"><span data-stu-id="717d7-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="717d7-113">Pour effectuer une configuration générique et applicable à d’autres clients, utilisez `localhost` dans votre bloc de nœud.</span><span class="sxs-lookup"><span data-stu-id="717d7-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="717d7-114">L’exemple ci-dessous montre un interpréteur de commandes de configuration qui utilise `localhost` plutôt qu’un nom de client spécifique.</span><span class="sxs-lookup"><span data-stu-id="717d7-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="717d7-115">Une fois que vous avez compilé votre configuration générique, vous devriez disposer d’un fichier « localhost.mof ».</span><span class="sxs-lookup"><span data-stu-id="717d7-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="717d7-116">Renommer le fichier MOF</span><span class="sxs-lookup"><span data-stu-id="717d7-116">Renaming the MOF file</span></span>

<span data-ttu-id="717d7-117">Vous pouvez stocker des fichiers de configuration « .mof » sur un serveur Pull à l’aide de **ConfigurationName** ou de **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="717d7-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="717d7-118">Selon la façon dont vous souhaitez configurer vos clients Pull, vous pouvez choisir une section ci-dessous afin de renommer correctement vos fichiers « .mof » compilés.</span><span class="sxs-lookup"><span data-stu-id="717d7-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="717d7-119">ID (GUID) de configuration</span><span class="sxs-lookup"><span data-stu-id="717d7-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="717d7-120">Vous devrez renommer votre fichier « localhost.mof » en « <GUID>.mof ».</span><span class="sxs-lookup"><span data-stu-id="717d7-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="717d7-121">Vous pouvez créer un **GUID** aléatoire à l’aide de l’exemple ci-dessous, ou en utilisant l’applet de commande [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid).</span><span class="sxs-lookup"><span data-stu-id="717d7-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="717d7-122">Sortie exemple</span><span class="sxs-lookup"><span data-stu-id="717d7-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="717d7-123">Vous pouvez ensuite renommer votre fichier « .mof » à l’aide de n’importe quelle méthode valide.</span><span class="sxs-lookup"><span data-stu-id="717d7-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="717d7-124">L’exemple ci-dessous utilise l’applet de commande [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).</span><span class="sxs-lookup"><span data-stu-id="717d7-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="717d7-125">Pour plus d’informations sur l’utilisation des **GUID** dans votre environnement, consultez [Planifier les GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="717d7-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="717d7-126">Noms de configuration</span><span class="sxs-lookup"><span data-stu-id="717d7-126">Configuration Names</span></span>

<span data-ttu-id="717d7-127">Vous devrez renommer votre fichier « localhost.mof » en « <Configuration Name>.mof ».</span><span class="sxs-lookup"><span data-stu-id="717d7-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="717d7-128">L’exemple suivant utilise le nom de la configuration de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="717d7-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="717d7-129">Vous pouvez ensuite renommer votre fichier « .mof » à l’aide de n’importe quelle méthode valide.</span><span class="sxs-lookup"><span data-stu-id="717d7-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="717d7-130">L’exemple ci-dessous utilise l’applet de commande [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).</span><span class="sxs-lookup"><span data-stu-id="717d7-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="717d7-131">Créer la somme de contrôle</span><span class="sxs-lookup"><span data-stu-id="717d7-131">Create the CheckSum</span></span>

<span data-ttu-id="717d7-132">Chaque fichier « .mof » stocké sur un serveur Pull ou sur un partage SMB doit être associé à un fichier « .checksum ».</span><span class="sxs-lookup"><span data-stu-id="717d7-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="717d7-133">Ce fichier permet aux clients de savoir quand le fichier « .mof » associé a changé et doit être téléchargé à nouveau.</span><span class="sxs-lookup"><span data-stu-id="717d7-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="717d7-134">Vous pouvez créer une **somme de contrôle** à l’aide de l’applet de commande [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum).</span><span class="sxs-lookup"><span data-stu-id="717d7-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="717d7-135">Vous pouvez également exécuter `New-DSCCheckSum` dans un répertoire de fichiers à l’aide du paramètre `-Path`.</span><span class="sxs-lookup"><span data-stu-id="717d7-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="717d7-136">Si une somme de contrôle existe déjà, vous pouvez forcer sa recréation avec le paramètre `-Force`.</span><span class="sxs-lookup"><span data-stu-id="717d7-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="717d7-137">L’exemple suivant a spécifié un répertoire contenant le fichier « .mof » à partir de la section précédente et utilise le paramètre `-Force`.</span><span class="sxs-lookup"><span data-stu-id="717d7-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="717d7-138">Aucune sortie ne s’affichera, mais vous devriez maintenant voir un fichier « <GUID or Configuration Name>. mof.checksum ».</span><span class="sxs-lookup"><span data-stu-id="717d7-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="717d7-139">Emplacement de stockage des fichiers MOF et sommes de contrôle</span><span class="sxs-lookup"><span data-stu-id="717d7-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="717d7-140">Sur un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="717d7-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="717d7-141">Lorsque vous configurez votre serveur Pull HTTP, comme expliqué dans la section [Configurer un serveur Pull HTTP DSC](pullServer.md), vous spécifiez des répertoires pour les clés **ModulePath** et **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="717d7-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="717d7-142">La clé **ConfigurationPath** indique l’emplacement où tous les fichiers « .mof » devraient être stockés.</span><span class="sxs-lookup"><span data-stu-id="717d7-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="717d7-143">La clé **ConfigurationPath** indique l’emplacement où tous les fichiers « .mof » et « .checksum » devraient être stockés.</span><span class="sxs-lookup"><span data-stu-id="717d7-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="717d7-144">Sur un partage SMB</span><span class="sxs-lookup"><span data-stu-id="717d7-144">On an SMB Share</span></span>

<span data-ttu-id="717d7-145">Lorsque vous configurez un client Pull pour utiliser un partage SMB, vous spécifiez une clé **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="717d7-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="717d7-146">Tous les fichiers « .mof » et « .checksum » doivent alors être stockés dans le répertoire **SourcePath** du bloc **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="717d7-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="717d7-147">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="717d7-147">Next Steps</span></span>

<span data-ttu-id="717d7-148">Vous devrez ensuite configurer les clients Pull pour extraire la configuration spécifiée.</span><span class="sxs-lookup"><span data-stu-id="717d7-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="717d7-149">Pour plus d’informations, consultez l’un des guides suivants :</span><span class="sxs-lookup"><span data-stu-id="717d7-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="717d7-150">Configurer un client Pull à l’aide d’ID de configuration (v4)</span><span class="sxs-lookup"><span data-stu-id="717d7-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="717d7-151">Configurer un client Pull à l’aide d’ID de configuration (v5)</span><span class="sxs-lookup"><span data-stu-id="717d7-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="717d7-152">Configurer un client Pull à l’aide de noms de configuration (v5)</span><span class="sxs-lookup"><span data-stu-id="717d7-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="717d7-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="717d7-153">See also</span></span>

- [<span data-ttu-id="717d7-154">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="717d7-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="717d7-155">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="717d7-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="717d7-156">Empaqueter et charger des ressources vers un serveur Pull</span><span class="sxs-lookup"><span data-stu-id="717d7-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
