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
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Publier sur un serveur collecteur à l’aide de l’ID de Configuration (v4/v5)

Les sections ci-dessous supposent que vous avez déjà configuré un serveur collecteur. Si vous n’avez pas configuré votre serveur collecteur, vous pouvez utiliser les guides suivants :

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)

Chaque nœud cible peut être configuré pour télécharger les configurations, ressources et même signaler son état. Cet article montre comment charger des ressources afin qu’ils soient disponibles pour être téléchargé et configurer les clients pour télécharger automatiquement les ressources. Lorsque le nœud reçoit une Configuration attribuée, via **extraire** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la Configuration à partir de l’emplacement spécifié dans le Gestionnaire de configuration local.

## <a name="compile-configurations"></a>Compiler les Configurations

La première étape pour un stockage [Configurations](../configurations/configurations.md) sur un serveur collecteur, consiste à les compiler dans des fichiers « .mof ». Pour effectuer une configuration générique et applicables à plus de clients, utilisez `localhost` dans votre bloc de nœud. L’exemple ci-dessous montre un interpréteur de commandes de Configuration qui utilise `localhost` plutôt qu’un nom de client spécifique.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Une fois que vous avez compilé votre configuration générique, vous devez disposer d’un fichier « localhost.mof ».

## <a name="renaming-the-mof-file"></a>Renommer le fichier MOF

Vous pouvez stocker des fichiers de Configuration de « .mof » sur un serveur collecteur par **ConfigurationName** ou **ConfigurationID**. Selon la façon dont vous souhaitez configurer vos clients d’extraction, vous pouvez choisir une section ci-dessous pour renommer correctement vos fichiers .mof « compilés ».

### <a name="configuration-ids-guid"></a>ID (GUID) de la configuration

Vous devez renommer votre fichier de « localhost.mof » pour «<GUID>.mof « fichier. Vous pouvez créer un aléatoire **Guid** à l’aide de l’exemple ci-dessous, ou en utilisant le [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) applet de commande.

```powershell
[System.Guid]::NewGuid()
```

Sortie exemple

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Vous pouvez ensuite renommer votre fichier de « .mof » à l’aide de n’importe quelle méthode acceptable. L’exemple ci-dessous, utilise le [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) applet de commande.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Pour plus d’informations sur l’utilisation de **GUID** dans votre environnement, consultez [planifier GUID](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Noms de configuration

Vous devez renommer votre fichier de « localhost.mof » pour «<Configuration Name>.mof « fichier. Dans l’exemple suivant, le nom de la configuration de la section précédente est utilisé. Vous pouvez ensuite renommer votre fichier de « .mof » à l’aide de n’importe quelle méthode acceptable. L’exemple ci-dessous, utilise le [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) applet de commande.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Créer la somme de contrôle

Chaque fichier de « .mof » stocké sur un serveur collecteur, ou un partage SMB doit avoir un fichier associé « .checksum ». Ce fichier permet aux clients de savoir quand le fichier .mof « associé » a changé et doit être téléchargé à nouveau.

Vous pouvez créer un **CheckSum** avec la [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) applet de commande. Vous pouvez également exécuter `New-DSCCheckSum` par rapport à un répertoire de fichiers à l’aide de le `-Path` paramètre. Si une somme de contrôle existe déjà, vous pouvez le forcer à être recréé avec le `-Force` paramètre. L’exemple suivant a spécifié un répertoire contenant le fichier « .mof » à partir de la section précédente et utilise le `-Force` paramètre.

```powershell
New-DscChecksum -Path '.\' -Force
```

Aucune sortie ne s’affiche, mais vous devriez maintenant voir un «<GUID or Configuration Name>. mof.checksum « fichier.

## <a name="where-to-store-mof-files-and-checksums"></a>Emplacement où stocker les fichiers MOF et les sommes de contrôle

### <a name="on-a-dsc-http-pull-server"></a>Sur un serveur HTTP tirage de DSC

Lorsque vous configurez votre serveur collecteur HTTP, comme expliqué dans [configurer un serveur Pull de DSC HTTP](pullServer.md), vous spécifiez des répertoires pour les **ModulePath** et **ConfigurationPath** clés. Le **ConfigurationPath** clé indique où tous les fichiers « .mof » doivent être stockées. Le **ConfigurationPath** indique où tous les fichiers de « .mof » et « .checksum » les fichiers doivent être stockées.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>Sur un partage SMB

Lorsque vous configurez un Client collecteur à utiliser un partage SMB, vous spécifiez un **ConfigurationRepositoryShare**. Tous les fichiers de « .mof » et « .checksum » doit alors être stockée dans le **SourcePath** répertoire à partir de la **ConfigurationRepositoryShare** bloc.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Étapes suivantes

Ensuite, vous devez configurer les Clients d’extraction pour extraire la configuration spécifiée. Pour plus d’informations, consultez un des guides suivants :

- [Configurer un Client collecteur à l’aide de l’ID de Configuration (v4)](pullClientConfigId4.md)
- [Configurer un Client collecteur à l’aide de l’ID de Configuration (v5)](pullClientConfigId.md)
- [Configurer un Client collecteur à l’aide de noms de Configuration (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>Voir aussi

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)
- [Package et chargement des ressources à un serveur collecteur](package-upload-resources.md)
