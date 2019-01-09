---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Package et chargement des ressources à un serveur collecteur
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401239"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Package et chargement des ressources à un serveur collecteur

Les sections ci-dessous supposent que vous avez déjà configuré un serveur collecteur. Si vous n’avez pas configuré votre serveur collecteur, vous pouvez utiliser les guides suivants :

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)

Chaque nœud cible peut être configuré pour télécharger les configurations, ressources et même signaler son état. Cet article montre comment charger des ressources afin qu’ils soient disponibles pour être téléchargé et configurer les clients pour télécharger automatiquement les ressources. Lorsque le nœud reçoit une Configuration attribuée, via **extraire** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la Configuration à partir de l’emplacement spécifié dans le Gestionnaire de configuration local.

## <a name="package-resource-modules"></a>Modules de ressources de package

Chaque ressource disponible pour un client de télécharger doit être stockée dans un fichier « .zip ». L’exemple ci-dessous affiche les étapes nécessaires à l’aide de la [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) ressource.

> [!NOTE]
> Si vous avez tous les clients à l’aide de PowerShell 4.0, vous devez aplanir la structure de dossiers de ressources et supprimez tous les dossiers version. Pour plus d’informations, consultez [plusieurs Versions de ressources](../configurations/import-dscresource.md#multiple-resource-versions).

Vous pouvez compresser le répertoire de ressources à l’aide de n’importe quel utilitaire, un script ou une méthode que vous préférez. Dans Windows, vous pouvez *avec le bouton droit* sur le répertoire de « xPSDesiredStateConfiguration », puis sélectionnez « Envoyer vers », puis « Dossier compressé ».

![Cliquer avec le bouton droit](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>L’Archive de ressources d’affectation de noms

L’archive de ressources doit être nommée avec le format suivant :

```
{ModuleName}_{Version}.zip
```

Dans l’exemple ci-dessus, « xPSDesiredStateConfiguration.zip » doit être renommé « xPSDesiredStateConfiguration_8.4.4.0.zip ».

### <a name="create-checksums"></a>Créer des sommes de contrôle

Une fois le module de ressources a été compressé et renommé, vous devez créer un **somme de contrôle**.  Le **somme de contrôle** est utilisé par le Gestionnaire de configuration local sur le client, pour déterminer si la ressource a été modifiée et doit être téléchargée à nouveau. Vous pouvez créer un **CheckSum** avec la [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) applet de commande, comme indiqué dans l’exemple ci-dessous.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Aucune sortie ne s’affiche, mais vous devriez maintenant voir un « xPSDesiredStateConfiguration_8.4.4.0.zip.checksum ». Vous pouvez également exécuter `New-DSCCheckSum` par rapport à un répertoire de fichiers à l’aide de le `-Path` paramètre. Si une somme de contrôle existe déjà, vous pouvez le forcer à être recréé avec le `-Force` paramètre.

### <a name="where-to-store-resource-archives"></a>Emplacement où stocker les Archives de ressource

#### <a name="on-a-dsc-http-pull-server"></a>Sur un serveur HTTP tirage de DSC

Lorsque vous configurez votre serveur collecteur HTTP, comme expliqué dans [configurer un serveur Pull de DSC HTTP](pullServer.md), vous spécifiez des répertoires pour les **ModulePath** et **ConfigurationPath** clés. Le **ConfigurationPath** clé indique où tous les fichiers « .mof » doivent être stockées. Le **ModulePath** indique où les Modules de ressources DSC doit être stockées.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>Sur un partage SMB

Si vous avez spécifié un **ResourceRepositoryShare**, lors de la configuration de votre Client collecteur, stocker les archives et les sommes de contrôle dans le **SourcePath** répertoire à partir de la **ResourceRepositoryShare** bloc.

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

Si vous n’avez spécifié qu’un **ConfigurationRepositoryShare**, lors de la configuration de votre Client collecteur, stocker les archives et les sommes de contrôle dans le **SourcePath** répertoire à partir de la  **ConfigurationRepositoryShare** bloc.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Mise à jour des ressources

Vous pouvez forcer un nœud pour mettre à jour ses ressources en modifiant le numéro de version dans le nom de l’archive, ou en créant une nouvelle somme de contrôle. Le Client collecteur recherchera des versions plus récentes des ressources requises, ainsi que des mises à jour les sommes de contrôle, lorsque son gestionnaire de configuration local est actualisé.

## <a name="see-also"></a>Voir aussi

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)
