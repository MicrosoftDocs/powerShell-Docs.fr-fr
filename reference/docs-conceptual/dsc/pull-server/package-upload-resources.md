---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,installation
title: Empaqueter et charger des ressources vers un serveur Pull
description: Cet article explique comment charger des ressources sur un serveur Pull afin qu’elles puissent être téléchargées par des configurations sur les nœuds gérés par DSC.
ms.openlocfilehash: a19d04346a0ae546cfcaf70701fde870d3839f65
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661691"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="a2e53-104">Empaqueter et charger des ressources vers un serveur Pull</span><span class="sxs-lookup"><span data-stu-id="a2e53-104">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="a2e53-105">Les sections ci-dessous supposent que vous avez déjà configuré un serveur Pull.</span><span class="sxs-lookup"><span data-stu-id="a2e53-105">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="a2e53-106">Si vous n’avez pas configuré votre serveur Pull, vous pouvez utiliser les guides suivants :</span><span class="sxs-lookup"><span data-stu-id="a2e53-106">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="a2e53-107">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="a2e53-107">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="a2e53-108">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="a2e53-108">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="a2e53-109">Chaque nœud cible peut être configuré pour télécharger les configurations et les ressources, et même pour signaler son état.</span><span class="sxs-lookup"><span data-stu-id="a2e53-109">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="a2e53-110">Cet article montre comment charger des ressources afin qu’elles soient disponibles pour être téléchargées, et comment configurer les clients pour télécharger automatiquement des ressources.</span><span class="sxs-lookup"><span data-stu-id="a2e53-110">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="a2e53-111">Lorsque le nœud reçoit une configuration attribuée, via un serveur **Pull** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la configuration depuis l’emplacement spécifié dans le gestionnaire de configuration local (LCM).</span><span class="sxs-lookup"><span data-stu-id="a2e53-111">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="a2e53-112">Modules Resource Package</span><span class="sxs-lookup"><span data-stu-id="a2e53-112">Package Resource Modules</span></span>

<span data-ttu-id="a2e53-113">Chaque ressource disponible pour un client à télécharger doit être stockée dans un fichier `.zip`.</span><span class="sxs-lookup"><span data-stu-id="a2e53-113">Each resource available for a client to download must be stored in a `.zip` file.</span></span> <span data-ttu-id="a2e53-114">L’exemple ci-dessous montre les étapes nécessaires en utilisant la ressource [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0).</span><span class="sxs-lookup"><span data-stu-id="a2e53-114">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="a2e53-115">Si vous avez des clients qui utilisent PowerShell 4.0, vous devez aplatir la structure de dossiers des ressources et supprimer tous les dossiers de version.</span><span class="sxs-lookup"><span data-stu-id="a2e53-115">If you have any clients using PowerShell 4.0, you will need to flatten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="a2e53-116">Pour plus d’informations, consultez [Plusieurs versions de ressources](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="a2e53-116">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="a2e53-117">Vous pouvez compresser le répertoire des ressources à l’aide de l’utilitaire, du script ou de la méthode de votre choix.</span><span class="sxs-lookup"><span data-stu-id="a2e53-117">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="a2e53-118">Dans Windows, vous pouvez _cliquer avec le bouton droit_ sur le répertoire `xPSDesiredStateConfiguration`, sélectionner **Envoyer vers** , puis **Dossier compressé**.</span><span class="sxs-lookup"><span data-stu-id="a2e53-118">In Windows, you can _right-click_ on the `xPSDesiredStateConfiguration` directory, and select **Send To** , then **Compressed Folder**.</span></span>

![Clic droit - Envoyer vers - Dossier compressé](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="a2e53-120">Nommer l’archive de ressources</span><span class="sxs-lookup"><span data-stu-id="a2e53-120">Naming the Resource Archive</span></span>

<span data-ttu-id="a2e53-121">L’archive de ressources doit être nommée avec le format suivant :</span><span class="sxs-lookup"><span data-stu-id="a2e53-121">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="a2e53-122">Dans l’exemple ci-dessus, `xPSDesiredStateConfiguration.zip` doit être renommé `xPSDesiredStateConfiguration_8.4.4.0.zip`.</span><span class="sxs-lookup"><span data-stu-id="a2e53-122">In the example above, `xPSDesiredStateConfiguration.zip` should be renamed `xPSDesiredStateConfiguration_8.4.4.0.zip`.</span></span>

### <a name="create-checksums"></a><span data-ttu-id="a2e53-123">Créer des sommes de contrôle</span><span class="sxs-lookup"><span data-stu-id="a2e53-123">Create CheckSums</span></span>

<span data-ttu-id="a2e53-124">Une fois le module de ressources compressé et renommé, vous devez créer une **somme de contrôle**.</span><span class="sxs-lookup"><span data-stu-id="a2e53-124">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span> <span data-ttu-id="a2e53-125">La **somme de contrôle** est utilisée par le gestionnaire de configuration local sur le client pour déterminer si la ressource a été modifiée et doit être téléchargée à nouveau.</span><span class="sxs-lookup"><span data-stu-id="a2e53-125">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="a2e53-126">Vous pouvez créer une **somme de contrôle** avec l’applet de commande [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum), comme indiqué dans l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="a2e53-126">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="a2e53-127">Aucune sortie ne s’affichera, mais vous devriez maintenant voir un fichier « xPSDesiredStateConfiguration_8.4.4.0.zip.checksum ».</span><span class="sxs-lookup"><span data-stu-id="a2e53-127">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="a2e53-128">Vous pouvez également exécuter `New-DSCCheckSum` dans un répertoire de fichiers à l’aide du paramètre `-Path`.</span><span class="sxs-lookup"><span data-stu-id="a2e53-128">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="a2e53-129">Si une somme de contrôle existe déjà, vous pouvez forcer sa recréation avec le paramètre `-Force`.</span><span class="sxs-lookup"><span data-stu-id="a2e53-129">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="a2e53-130">Emplacement de stockage des archives de ressources</span><span class="sxs-lookup"><span data-stu-id="a2e53-130">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="a2e53-131">Sur un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="a2e53-131">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="a2e53-132">Lorsque vous configurez votre serveur Pull HTTP, comme expliqué dans la section [Configurer un serveur Pull HTTP DSC](pullServer.md), vous spécifiez des répertoires pour les clés **ModulePath** et **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="a2e53-132">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="a2e53-133">La clé **ConfigurationPath** indique l’emplacement où tous les fichiers « .mof » devraient être stockés.</span><span class="sxs-lookup"><span data-stu-id="a2e53-133">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="a2e53-134">La clé **ModulePath** indique l’emplacement où les modules de ressources DSC devraient être stockés.</span><span class="sxs-lookup"><span data-stu-id="a2e53-134">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="a2e53-135">Sur un partage SMB</span><span class="sxs-lookup"><span data-stu-id="a2e53-135">On an SMB Share</span></span>

<span data-ttu-id="a2e53-136">Si vous avez spécifié une clé **ResourceRepositoryShare** , lors de la configuration de votre client Pull, stockez les archives et les sommes de contrôle dans le répertoire **SourcePath** du bloc **ResourceRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="a2e53-136">If you specified a **ResourceRepositoryShare** , when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

<span data-ttu-id="a2e53-137">Si vous n’avez spécifié qu’une clé **ConfigurationRepositoryShare** , lors de la configuration de votre client Pull, stockez les archives et les sommes de contrôle dans le répertoire **SourcePath** du bloc **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="a2e53-137">If you specified only a **ConfigurationRepositoryShare** , when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="a2e53-138">Mise à jour des ressources</span><span class="sxs-lookup"><span data-stu-id="a2e53-138">Updating resources</span></span>

<span data-ttu-id="a2e53-139">Vous pouvez forcer un nœud à mettre à jour ses ressources en modifiant le numéro de version dans le nom de l’archive, ou en créant une somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="a2e53-139">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="a2e53-140">Le client Pull recherchera des versions plus récentes des ressources requises, ainsi que des mises à jour les sommes de contrôle, lorsque son gestionnaire de configuration local est actualisé.</span><span class="sxs-lookup"><span data-stu-id="a2e53-140">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2e53-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2e53-141">See also</span></span>

- [<span data-ttu-id="a2e53-142">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="a2e53-142">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="a2e53-143">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="a2e53-143">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
