---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Package et chargement des ressources à un serveur collecteur
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679460"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="67604-103">Package et chargement des ressources à un serveur collecteur</span><span class="sxs-lookup"><span data-stu-id="67604-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="67604-104">Les sections ci-dessous supposent que vous avez déjà configuré un serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="67604-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="67604-105">Si vous n’avez pas configuré votre serveur collecteur, vous pouvez utiliser les guides suivants :</span><span class="sxs-lookup"><span data-stu-id="67604-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="67604-106">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="67604-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="67604-107">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="67604-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="67604-108">Chaque nœud cible peut être configuré pour télécharger les configurations, ressources et même signaler son état.</span><span class="sxs-lookup"><span data-stu-id="67604-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="67604-109">Cet article montre comment charger des ressources afin qu’ils soient disponibles pour être téléchargé et configurer les clients pour télécharger automatiquement les ressources.</span><span class="sxs-lookup"><span data-stu-id="67604-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="67604-110">Lorsque le nœud reçoit une Configuration attribuée, via **extraire** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la Configuration à partir de l’emplacement spécifié dans le Gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="67604-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="67604-111">Modules de ressources de package</span><span class="sxs-lookup"><span data-stu-id="67604-111">Package Resource Modules</span></span>

<span data-ttu-id="67604-112">Chaque ressource disponible pour un client de télécharger doit être stockée dans un fichier « .zip ».</span><span class="sxs-lookup"><span data-stu-id="67604-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="67604-113">L’exemple ci-dessous affiche les étapes nécessaires à l’aide de la [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) ressource.</span><span class="sxs-lookup"><span data-stu-id="67604-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="67604-114">Si vous avez tous les clients à l’aide de PowerShell 4.0, vous devez aplanir la structure de dossiers de ressources et supprimez tous les dossiers version.</span><span class="sxs-lookup"><span data-stu-id="67604-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="67604-115">Pour plus d’informations, consultez [plusieurs Versions de ressources](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="67604-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="67604-116">Vous pouvez compresser le répertoire de ressources à l’aide de n’importe quel utilitaire, un script ou une méthode que vous préférez.</span><span class="sxs-lookup"><span data-stu-id="67604-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="67604-117">Dans Windows, vous pouvez *avec le bouton droit* sur le répertoire de « xPSDesiredStateConfiguration », puis sélectionnez « Envoyer vers », puis « Dossier compressé ».</span><span class="sxs-lookup"><span data-stu-id="67604-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Cliquer avec le bouton droit](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="67604-119">L’Archive de ressources d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="67604-119">Naming the Resource Archive</span></span>

<span data-ttu-id="67604-120">L’archive de ressources doit être nommée avec le format suivant :</span><span class="sxs-lookup"><span data-stu-id="67604-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="67604-121">Dans l’exemple ci-dessus, « xPSDesiredStateConfiguration.zip » doit être renommé « xPSDesiredStateConfiguration_8.4.4.0.zip ».</span><span class="sxs-lookup"><span data-stu-id="67604-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="67604-122">Créer des sommes de contrôle</span><span class="sxs-lookup"><span data-stu-id="67604-122">Create CheckSums</span></span>

<span data-ttu-id="67604-123">Une fois le module de ressources a été compressé et renommé, vous devez créer un **somme de contrôle**.</span><span class="sxs-lookup"><span data-stu-id="67604-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="67604-124">Le **somme de contrôle** est utilisé par le Gestionnaire de configuration local sur le client, pour déterminer si la ressource a été modifiée et doit être téléchargée à nouveau.</span><span class="sxs-lookup"><span data-stu-id="67604-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="67604-125">Vous pouvez créer un **CheckSum** avec la [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) applet de commande, comme indiqué dans l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="67604-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="67604-126">Aucune sortie ne s’affiche, mais vous devriez maintenant voir un « xPSDesiredStateConfiguration_8.4.4.0.zip.checksum ».</span><span class="sxs-lookup"><span data-stu-id="67604-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="67604-127">Vous pouvez également exécuter `New-DSCCheckSum` par rapport à un répertoire de fichiers à l’aide de le `-Path` paramètre.</span><span class="sxs-lookup"><span data-stu-id="67604-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="67604-128">Si une somme de contrôle existe déjà, vous pouvez le forcer à être recréé avec le `-Force` paramètre.</span><span class="sxs-lookup"><span data-stu-id="67604-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="67604-129">Emplacement où stocker les Archives de ressource</span><span class="sxs-lookup"><span data-stu-id="67604-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="67604-130">Sur un serveur HTTP tirage de DSC</span><span class="sxs-lookup"><span data-stu-id="67604-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="67604-131">Lorsque vous configurez votre serveur collecteur HTTP, comme expliqué dans [configurer un serveur Pull de DSC HTTP](pullServer.md), vous spécifiez des répertoires pour les **ModulePath** et **ConfigurationPath** clés.</span><span class="sxs-lookup"><span data-stu-id="67604-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="67604-132">Le **ConfigurationPath** clé indique où tous les fichiers « .mof » doivent être stockées.</span><span class="sxs-lookup"><span data-stu-id="67604-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="67604-133">Le **ModulePath** indique où les Modules de ressources DSC doit être stockées.</span><span class="sxs-lookup"><span data-stu-id="67604-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="67604-134">Sur un partage SMB</span><span class="sxs-lookup"><span data-stu-id="67604-134">On an SMB Share</span></span>

<span data-ttu-id="67604-135">Si vous avez spécifié un **ResourceRepositoryShare**, lors de la configuration de votre Client collecteur, stocker les archives et les sommes de contrôle dans le **SourcePath** répertoire à partir de la **ResourceRepositoryShare** bloc.</span><span class="sxs-lookup"><span data-stu-id="67604-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

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

<span data-ttu-id="67604-136">Si vous n’avez spécifié qu’un **ConfigurationRepositoryShare**, lors de la configuration de votre Client collecteur, stocker les archives et les sommes de contrôle dans le **SourcePath** répertoire à partir de la  **ConfigurationRepositoryShare** bloc.</span><span class="sxs-lookup"><span data-stu-id="67604-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="67604-137">Mise à jour des ressources</span><span class="sxs-lookup"><span data-stu-id="67604-137">Updating resources</span></span>

<span data-ttu-id="67604-138">Vous pouvez forcer un nœud pour mettre à jour ses ressources en modifiant le numéro de version dans le nom de l’archive, ou en créant une nouvelle somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="67604-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="67604-139">Le Client collecteur recherchera des versions plus récentes des ressources requises, ainsi que des mises à jour les sommes de contrôle, lorsque son gestionnaire de configuration local est actualisé.</span><span class="sxs-lookup"><span data-stu-id="67604-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="67604-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67604-140">See also</span></span>

- [<span data-ttu-id="67604-141">Configurer un serveur Pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="67604-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="67604-142">Configurer un serveur Pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="67604-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
