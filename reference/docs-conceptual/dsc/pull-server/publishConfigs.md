---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,installation
title: Publier sur un serveur Pull à l’aide d’ID de configuration (v4/v5)
description: Cet article montre comment charger des ressources afin qu’elles soient disponibles pour être téléchargées, et comment configurer les clients pour télécharger automatiquement des ressources.
ms.openlocfilehash: 20e12e3cac6b6e4a86563576f4a915429b18aadb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646828"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Publier sur un serveur Pull à l’aide d’ID de configuration (v4/v5)

Les sections ci-dessous supposent que vous avez déjà configuré un serveur Pull. Si vous n’avez pas configuré votre serveur Pull, vous pouvez utiliser les guides suivants :

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)

Chaque nœud cible peut être configuré pour télécharger les configurations et les ressources, et même pour signaler son état. Cet article montre comment charger des ressources afin qu’elles soient disponibles pour être téléchargées, et comment configurer les clients pour télécharger automatiquement des ressources. Lorsque le nœud reçoit une configuration attribuée, via un serveur **Pull** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la configuration depuis l’emplacement spécifié dans le gestionnaire de configuration local (LCM).

## <a name="compile-configurations"></a>Compiler les configurations

La première étape pour stocker des [configurations](../configurations/configurations.md) sur un serveur Pull consiste à les compiler dans des fichiers `.mof`. Pour effectuer une configuration générique et applicable à d’autres clients, utilisez `localhost` dans votre bloc de nœud. L’exemple ci-dessous montre un interpréteur de commandes de configuration qui utilise `localhost` plutôt qu’un nom de client spécifique.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Une fois que vous avez compilé votre configuration générique, vous deez disposer d’un fichier `localhost.mof`.

## <a name="renaming-the-mof-file"></a>Renommer le fichier MOF

Vous pouvez stocker des fichiers de configuration `.mof` sur un serveur Pull à l’aide de **ConfigurationName** ou de **ConfigurationID** . Selon la façon dont vous souhaitez configurer vos clients Pull, vous pouvez choisir une section ci-dessous afin de renommer correctement vos fichiers `.mof` compilés.

### <a name="configuration-ids-guid"></a>ID (GUID) de configuration

Vous devez renommer votre fichier `localhost.mof` en fichier `<GUID>.mof`. Vous pouvez créer un **GUID** aléatoire à l’aide de l’exemple ci-dessous, ou en utilisant l’applet de commande [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid).

```powershell
[System.Guid]::NewGuid()
```

Exemple de sortie

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Vous pouvez ensuite renommer votre fichier `.mof` à l’aide de n’importe quelle méthode valide. L’exemple ci-dessous utilise l’applet de commande [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Pour plus d’informations sur l’utilisation des **GUID** dans votre environnement, consultez [Planifier les GUID](secureServer.md#guids).

### <a name="configuration-names"></a>Noms de configuration

Vous devez renommer votre fichier `localhost.mof` en fichier `<Configuration Name>.mof`. L’exemple suivant utilise le nom de la configuration de la section précédente. Vous pouvez ensuite renommer votre fichier `.mof` à l’aide de n’importe quelle méthode valide. L’exemple ci-dessous utilise l’applet de commande [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Créer la somme de contrôle

Chaque fichier `.mof` stocké sur un serveur Pull ou sur un partage SMB doit être associé à un fichier `.checksum`.
Ce fichier permet aux clients de savoir quand le fichier `.mof` associé a changé et doit être téléchargé à nouveau.

Vous pouvez créer une **somme de contrôle** à l’aide de l’applet de commande [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum). Vous pouvez également exécuter `New-DSCCheckSum` dans un répertoire de fichiers à l’aide du paramètre `-Path`.
Si une somme de contrôle existe déjà, vous pouvez forcer sa recréation avec le paramètre `-Force`. L’exemple suivant a spécifié un répertoire contenant le fichier `.mof` à partir de la section précédente et utilise le paramètre `-Force`.

```powershell
New-DscChecksum -Path '.\' -Force
```

Aucune sortie ne s’affiche, mais vous devez maintenant voir un fichier `<GUID or Configuration Name>.mof.checksum`.

## <a name="where-to-store-mof-files-and-checksums"></a>Emplacement de stockage des fichiers MOF et sommes de contrôle

### <a name="on-a-dsc-http-pull-server"></a>Sur un serveur Pull HTTP DSC

Lorsque vous configurez votre serveur Pull HTTP, comme expliqué dans la section [Configurer un serveur Pull HTTP DSC](pullServer.md), vous spécifiez des répertoires pour les clés **ModulePath** et **ConfigurationPath** . La clé **ModulePath** indique l’emplacement de stockage des fichiers `.zip` empaquetés d’un module. La clé **ConfigurationPath** indique l’emplacement où tous les fichiers `.mof` et `.checksum` doivent être stockés.

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

Lorsque vous configurez un client Pull pour utiliser un partage SMB, vous spécifiez une clé **ConfigurationRepositoryShare** .
Tous les fichiers `.mof` et `.checksum` doivent alors être stockés dans le répertoire **SourcePath** du bloc **ConfigurationRepositoryShare** .

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Étapes suivantes

Vous devez ensuite configurer les clients Pull pour extraire la configuration spécifiée. Pour plus d’informations, consultez l’un des guides suivants :

- [Configurer un client Pull à l’aide d’ID de configuration (v4)](pullClientConfigId4.md)
- [Configurer un client Pull à l’aide d’ID de configuration (v5)](pullClientConfigId.md)
- [Configurer un client Pull à l’aide de noms de configuration (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>Voir aussi

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)
- [Empaqueter et charger des ressources vers un serveur Pull](package-upload-resources.md)
