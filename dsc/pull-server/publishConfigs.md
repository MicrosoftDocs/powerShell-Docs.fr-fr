---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Publier sur un serveur collecteur à l’aide de l’ID de Configuration (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401312"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="dbdc0-103">Publier sur un serveur collecteur à l’aide de l’ID de Configuration (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="dbdc0-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="dbdc0-104">Les sections ci-dessous supposent que vous avez déjà configuré un serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="dbdc0-105">Si vous n’avez pas configuré votre serveur collecteur, vous pouvez utiliser les guides suivants :</span><span class="sxs-lookup"><span data-stu-id="dbdc0-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="dbdc0-106">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="dbdc0-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="dbdc0-107">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="dbdc0-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="dbdc0-108">Chaque nœud cible peut être configuré pour télécharger les configurations, ressources et même signaler son état.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="dbdc0-109">Cet article montre comment charger des ressources afin qu’ils soient disponibles pour être téléchargé et configurer les clients pour télécharger automatiquement les ressources.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="dbdc0-110">Lorsque le nœud reçoit une Configuration attribuée, via **extraire** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la Configuration à partir de l’emplacement spécifié dans le Gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="dbdc0-111">Compiler les Configurations</span><span class="sxs-lookup"><span data-stu-id="dbdc0-111">Compile Configurations</span></span>

<span data-ttu-id="dbdc0-112">La première étape pour un stockage [Configurations](../configurations/configurations.md) sur un serveur collecteur, consiste à les compiler dans des fichiers « .mof ».</span><span class="sxs-lookup"><span data-stu-id="dbdc0-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="dbdc0-113">Pour effectuer une configuration générique et applicables à plus de clients, utilisez `localhost` dans votre bloc de nœud.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="dbdc0-114">L’exemple ci-dessous montre un interpréteur de commandes de Configuration qui utilise `localhost` plutôt qu’un nom de client spécifique.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="dbdc0-115">Une fois que vous avez compilé votre configuration générique, vous devez disposer d’un fichier « localhost.mof ».</span><span class="sxs-lookup"><span data-stu-id="dbdc0-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="dbdc0-116">Renommer le fichier MOF</span><span class="sxs-lookup"><span data-stu-id="dbdc0-116">Renaming the MOF file</span></span>

<span data-ttu-id="dbdc0-117">Vous pouvez stocker des fichiers de Configuration de « .mof » sur un serveur collecteur par **ConfigurationName** ou **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="dbdc0-118">Selon la façon dont vous souhaitez configurer vos clients d’extraction, vous pouvez choisir une section ci-dessous pour renommer correctement vos fichiers .mof « compilés ».</span><span class="sxs-lookup"><span data-stu-id="dbdc0-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="dbdc0-119">ID (GUID) de la configuration</span><span class="sxs-lookup"><span data-stu-id="dbdc0-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="dbdc0-120">Vous devez renommer votre fichier de « localhost.mof » pour «<GUID>.mof « fichier.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="dbdc0-121">Vous pouvez créer un aléatoire **Guid** à l’aide de l’exemple ci-dessous, ou en utilisant le [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="dbdc0-122">Sortie exemple</span><span class="sxs-lookup"><span data-stu-id="dbdc0-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="dbdc0-123">Vous pouvez ensuite renommer votre fichier de « .mof » à l’aide de n’importe quelle méthode acceptable.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="dbdc0-124">L’exemple ci-dessous, utilise le [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="dbdc0-125">Pour plus d’informations sur l’utilisation de **GUID** dans votre environnement, consultez [planifier GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="dbdc0-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="dbdc0-126">Noms de configuration</span><span class="sxs-lookup"><span data-stu-id="dbdc0-126">Configuration Names</span></span>

<span data-ttu-id="dbdc0-127">Vous devez renommer votre fichier de « localhost.mof » pour «<Configuration Name>.mof « fichier.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="dbdc0-128">Dans l’exemple suivant, le nom de la configuration de la section précédente est utilisé.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="dbdc0-129">Vous pouvez ensuite renommer votre fichier de « .mof » à l’aide de n’importe quelle méthode acceptable.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="dbdc0-130">L’exemple ci-dessous, utilise le [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="dbdc0-131">Créer la somme de contrôle</span><span class="sxs-lookup"><span data-stu-id="dbdc0-131">Create the CheckSum</span></span>

<span data-ttu-id="dbdc0-132">Chaque fichier de « .mof » stocké sur un serveur collecteur, ou un partage SMB doit avoir un fichier associé « .checksum ».</span><span class="sxs-lookup"><span data-stu-id="dbdc0-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="dbdc0-133">Ce fichier permet aux clients de savoir quand le fichier .mof « associé » a changé et doit être téléchargé à nouveau.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="dbdc0-134">Vous pouvez créer un **CheckSum** avec la [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="dbdc0-135">Vous pouvez également exécuter `New-DSCCheckSum` par rapport à un répertoire de fichiers à l’aide de le `-Path` paramètre.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="dbdc0-136">Si une somme de contrôle existe déjà, vous pouvez le forcer à être recréé avec le `-Force` paramètre.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="dbdc0-137">L’exemple suivant a spécifié un répertoire contenant le fichier « .mof » à partir de la section précédente et utilise le `-Force` paramètre.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="dbdc0-138">Aucune sortie ne s’affiche, mais vous devriez maintenant voir un «<GUID or Configuration Name>. mof.checksum « fichier.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="dbdc0-139">Emplacement où stocker les fichiers MOF et les sommes de contrôle</span><span class="sxs-lookup"><span data-stu-id="dbdc0-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="dbdc0-140">Sur un serveur HTTP tirage de DSC</span><span class="sxs-lookup"><span data-stu-id="dbdc0-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="dbdc0-141">Lorsque vous configurez votre serveur collecteur HTTP, comme expliqué dans [configurer un serveur Pull de DSC HTTP](pullServer.md), vous spécifiez des répertoires pour les **ModulePath** et **ConfigurationPath** clés.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="dbdc0-142">Le **ConfigurationPath** clé indique où tous les fichiers « .mof » doivent être stockées.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="dbdc0-143">Le **ConfigurationPath** indique où tous les fichiers de « .mof » et « .checksum » les fichiers doivent être stockées.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="dbdc0-144">Sur un partage SMB</span><span class="sxs-lookup"><span data-stu-id="dbdc0-144">On an SMB Share</span></span>

<span data-ttu-id="dbdc0-145">Lorsque vous configurez un Client collecteur à utiliser un partage SMB, vous spécifiez un **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="dbdc0-146">Tous les fichiers de « .mof » et « .checksum » doit alors être stockée dans le **SourcePath** répertoire à partir de la **ConfigurationRepositoryShare** bloc.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="dbdc0-147">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="dbdc0-147">Next Steps</span></span>

<span data-ttu-id="dbdc0-148">Ensuite, vous devez configurer les Clients d’extraction pour extraire la configuration spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dbdc0-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="dbdc0-149">Pour plus d’informations, consultez un des guides suivants :</span><span class="sxs-lookup"><span data-stu-id="dbdc0-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="dbdc0-150">Configurer un Client collecteur à l’aide de l’ID de Configuration (v4)</span><span class="sxs-lookup"><span data-stu-id="dbdc0-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="dbdc0-151">Configurer un Client collecteur à l’aide de l’ID de Configuration (v5)</span><span class="sxs-lookup"><span data-stu-id="dbdc0-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="dbdc0-152">Configurer un Client collecteur à l’aide de noms de Configuration (v5)</span><span class="sxs-lookup"><span data-stu-id="dbdc0-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="dbdc0-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbdc0-153">See also</span></span>

- [<span data-ttu-id="dbdc0-154">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="dbdc0-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="dbdc0-155">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="dbdc0-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="dbdc0-156">Package et chargement des ressources à un serveur collecteur</span><span class="sxs-lookup"><span data-stu-id="dbdc0-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
