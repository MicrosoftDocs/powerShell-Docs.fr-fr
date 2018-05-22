---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Utilisation de DSC sur Nano Server
ms.openlocfilehash: 9e26c525b48e8656a3479db9c0a760eaeb8cf58a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="using-dsc-on-nano-server"></a>Utilisation de DSC sur Nano Server

> S’applique à : Windows PowerShell 5.0

**DSC sur Nano Server** est un package facultatif dans le dossier `NanoServer\Packages` du support Windows Server 2016. Le package peut être installé lorsque vous créez un disque dur virtuel pour Nano Server en spécifiant **Microsoft-NanoServer-DSC-Package** comme valeur du paramètre **Packages** de la fonction **New-NanoServerImage**. Par exemple, si vous créez un disque dur virtuel pour une machine virtuelle, la commande ressemble à ceci :

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Pour plus d’informations sur l’installation et l’utilisation de Nano Server, ainsi que sur le mode de gestion de Nano Server avec la communication à distance PowerShell, voir [Prise en main de Nano Server](https://technet.microsoft.com/library/mt126167.aspx).


## <a name="dsc-features-available-on-nano-server"></a>Fonctionnalités DSC disponibles sur Nano Server

 Comme Nano Server ne prend en charge qu’un ensemble limité d’API par rapport à une version complète de Windows Server, DSC sur Nano Server n’a pas exactement les mêmes fonctionnalités que DSC exécuté sur les références complètes pour l’instant. En effet, DSC sur Nano Server est en cours de développement et ne dispose pas encore de toutes les fonctionnalités.

 Les fonctionnalités DSC suivantes sont actuellement disponibles sur Nano Server :


* Modes par envoi et par extraction

* Toutes les applets de commande DSC qui existent sur une version complète de Windows Server, y compris les suivantes :
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn521621.aspx)
  * [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx)
  * [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [Stop-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)
  * [Publish-DscConfiguraiton](https://technet.microsoft.com/en-us/library/mt517875.aspx)
  * [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [Restore-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [Remove-DscConfigurationDocument](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [New-DscChecksum](https://technet.microsoft.com/en-us/library/dn521622.aspx)

* Compilation de configurations (voir [Configurations DSC](configurations.md))

  **Problème :** le chiffrement de mot de passe (voir [Sécurisation du fichier MOF](securemof.md)) pendant la compilation de la configuration ne fonctionne pas.

* Compilation de métaconfigurations (voir [Configuration du Gestionnaire de configuration local](metaConfig.md))

* Exécution d’une ressource sous un contexte utilisateur (voir [Exécution de DSC avec les informations d’identification de l’utilisateur (RunAs)](runAsUser.md))

* Ressources basées sur une classe (voir [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](authoringResourceClass.md))

* Débogage des ressources DSC (voir [Débogage des ressources DSC](debugresource.md))

  **Problème :** ne fonctionne pas si une ressource utilise PsDscRunAsCredential (voir [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md))

* [Spécification de dépendances entre nœuds](crossNodeDependencies.md)

* [Contrôle de version de ressources](sxsResource.md)

* Client collecteur (configurations et ressources) (voir [Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md))

* [Configurations partielles (envoi et extraction)](partialConfigs.md)

* [Rapports au serveur collecteur](reportServer.md)

* Chiffrement de document MOF

* Journalisation des événements

* Création de rapports DSC Azure Automation

* Ressources entièrement fonctionnelles
  * [Archive](archiveResource.md)
  * [Environment](environmentResource.md)
  * [File](fileResource.md)
  * [Log](logResource.md)
  * ProcessSet
  * [Registry](registryResource.md)
  * [Script](scriptResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)
  * WaitForAll (voir [Spécification de dépendances entre nœuds](crossNodeDependencies.md))
  * WaitForAny (voir [Spécification de dépendances entre nœuds](crossNodeDependencies.md))
  * WaitForSome (voir [Spécification de dépendances entre nœuds](crossNodeDependencies.md))

* Ressources partiellement fonctionnelles
  * [Groupe](groupResource.md)
  * GroupSet

  **Problème :** les ressources ci-dessus échouent si une instance spécifique est appelée deux fois (exécution de la même configuration deux fois)

  * [Service](serviceResource.md)
  * ServiceSet

  **Problème :** fonctionne uniquement pour le démarrage/l’arrêt du service (état). Échoue si vous essayez de modifier d’autres attributs de service, comme StartupType, les informations d’identification, la description, etc. L’erreur levée est semblable à :

  *Impossible de trouver le type [management.managementobject] : vérifiez que l’assembly contenant ce type est chargé.*

* Ressources non fonctionnelles
  * [User](userResource.md)


## <a name="dsc-features-not-available-on-nano-server"></a>Fonctionnalités DSC non disponibles sur Nano Server

Les fonctionnalités DSC suivantes ne sont pas disponibles sur Nano Server :

* Déchiffrement de documents MOF avec mots de passe cryptés
* Serveur collecteur : vous ne pouvez pas configurer un serveur collecteur sur Nano Server pour le moment
* Tout ce qui n’est pas dans la liste des fonctionnalités marche

## <a name="using-custom-dsc-resources-on-nano-server"></a>Utilisation de ressources DSC personnalisées sur Nano Server

En raison des ensembles limités d’API Windows et de bibliothèques CLR disponibles sur Nano Server, les ressources DSC qui fonctionnent sur la version CLR complète de Windows ne fonctionnent pas nécessairement sur Nano Server.
Effectuez les tests de bout en bout avant de déployer des ressources personnalisées DSC dans un environnement de production.

## <a name="see-also"></a>Voir aussi
- [Prise en main de Nano Server](https://technet.microsoft.com/library/mt126167.aspx)