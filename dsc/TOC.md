# [Vue d’ensemble](overview.md)

## [Présentation de la configuration de l’état souhaité pour les décideurs](decisionMaker.md)

## [Présentation de la configuration de l’état souhaité pour les ingénieurs](DscForEngineers.md)

## [Démarrage rapide avec DSC](quickStart.md)

# [Configurations](configurations.md)

## [Application des configurations](enactingConfigurations.md)

## [Séparation des données de configuration et d’environnement](separatingEnvData.md)

## [Utilisation de ressources avec plusieurs versions](sxsResource.md)

## [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md)

## [Spécification de dépendances entre nœuds](crossNodeDependencies.md)

## [Données de configuration](configData.md)

### [Options des informations d’identification dans les données de configuration](configDataCredentials.md)

## [Imbrication des configurations](compositeConfigs.md)

## [Sécurisation du fichier MOF de configuration](secureMOF.md)

## [Configurations partielles](partialConfigs.md)

## [Écriture de l’aide pour les configurations DSC](configHelp.md)

## [Configurer une machine virtuelle au démarrage initial à l’aide de DSC](bootstrapDsc.md)

### [Clé de Registre DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)

# [Ressources](resources.md)

## [Ressources intégrées](builtInResource.md)

### [Ressource Archive](archiveResource.md)

### [Ressource Environment](environmentResource.md)

### [Ressource File](fileResource.md)

### [Ressource Group](groupResource.md)

### [Ressource GroupSet](groupSetResource.md)

### [Ressource Log](logResource.md)

### [Ressource Package](packageResource.md)

### [Ressource ProcessSet](processSetResource.md)

### [Ressources Registry](registryResource.md)

### [Ressource Script](scriptResource.md)

### [Ressource Service](serviceResource.md)

### [Ressource ServiceSet](serviceSetResource.md)

### [Ressource User](userResource.md)

### [WaitForAllResource](waitForAllResource.md)

### [WaitForAnyResource](waitForAnyResource.md)

### [WaitForSomeResource](waitForSomeResource.md)

### [Ressource WindowsFeature](windowsfeatureResource.md)

### [Ressource WindowsFeatureSet](windowsFeatureSetResource.md)

### [Ressource WindowsOptionalFeature](windowsOptionalFeatureResource.md)

### [Ressource WindowsOptionalFeatureSet](windowsOptionalFeatureSetResource.md)

### [Ressource WindowsPackageCab](windowsPackageCabResource.md)

### [Ressource WindowsProcess](windowsProcessResource.md)

## [Création de ressources personnalisées](authoringResource.md) 

### [Ressources personnalisées MOF](authoringResourceMOF.md)

#### [Ressource MOF dans C#](authoringResourceMofCS.md)

### [Ressources personnalisées basées sur une classe](authoringResourceClass.md)

### [Ressources composites](authoringResourceComposite.md)

### [Écriture d’une ressource de DSC à instance unique (bonne pratique)](singleInstance.md)

### [Liste de vérification pour la création de ressources](resourceAuthoringChecklist.md)

## [Débogage des ressources DSC](debugResource.md)

## [Appel direct des méthodes des ressources DSC](directCallResource.md)

# Gestionnaire de configuration local

## [Configuration du gestionnaire de configuration local](metaConfig.md)

## [Configuration du gestionnaire de configuration local dans PowerShell 4.0](metaConfig4.md)

# Modèle DSC par extraction

## [Configuration d’un serveur collecteur web](pullServer.md)

## [Configuration d’un serveur collecteur SMB DSC](pullServerSMB.md)

## [Configuration d’un client collecteur](pullClient.md)

### [Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md)

### [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md)

## [Utilisation d’un serveur de rapports DSC](reportServer.md)

## [Bonnes pratiques pour le serveur collecteur](secureServer.md)

# [Exemples DSC](dscExamples.md)

## [Création d’un pipeline CI/CD avec DSC, Pester et Visual Studio Team Services](dscCiCd.md)

## [Séparation des données de configuration et d’environnement](separatingEnvData.md)

# [Résolution des problèmes liés à DSC](troubleshooting.md)

# [Utilisation de DSC sur Nano Server](nanoDsc.md)

# DSC sur Linux

## [Prise en main de DSC pour Linux](lnxGettingStarted.md)

## [Ressources intégrées pour Linux](lnxBuiltInResources.md)

### [Ressource nxArchive](lnxArchiveResource.md)

### [Ressource nxEnvironment](lnxEnvironmentResource.md)

### [Ressource nxFile](lnxFileResource.md)

### [Ressource nxFileLine](lnxFileLineResource.md)

### [Ressource nxGroup](lnxGroupResource.md)

### [Ressource nxPackage](lnxPackageResource.md)

### [Ressource nxService](lnxServiceResource.md)

### [Ressource nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md)

### [Ressource nxUser](lnxUserResource.md)

# [Utilisation de DSC sur Microsoft Azure](azureDsc.md)

# Informations de référence sur MOF DSC

## [Classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager.md)

### [Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-applyconfiguration.md)

### [Méthode DisableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)

### [Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)

### [Méthode GetConfiguration de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getconfiguration.md)

### [Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)

### [Méthode GetConfigurationStatus de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)

### [Méthode GetMetaConfiguration de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)

### [Méthode PerformRequiredConfigurationChecks de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)

### [Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-removeconfiguration.md)

### [Méthode ResourceGet de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-resourceget.md)

### [Méthode ResourceSet de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-resourceset.md)

### [Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-resourcetest.md)

### [Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-rollback.md)

### [Méthode SendConfiguration de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendconfiguration.md)

### [Méthode SendConfigurationApply de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)

### [Méthode SendConfigurationApplyAsync de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)

### [Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)

### [Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-stopconfiguration.md)

### [Méthode TestConfiguration de la classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-testconfiguration.md)

# Ressources complémentaires

## [Livres blancs](whitepapers.md)
