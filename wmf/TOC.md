# [Présentation des Notes de publication de WMF](releasenotes.md)

# [Détails de l'installation](requirements.md)

# [Incompatibilités connues du produit](productincompat.md)

# [Commentaires](feedback.md)

# [Scénarios activés par WMF 5.0]()
## [Just Enough Administration (JEA)](jea_overview.md)
### [Création et connexion à un point de terminaison JEA](jea_endpoint.md)
### [Création de rapports sur JEA](jea_report.md)

## [Création de types personnalisés à l’aide de classes PowerShell](class_overview.md)
### [Définir des types personnalisés](class_newtype.md)
### [Déclarer une classe de base](class_base.md)
### [Déclarer une interface implémentée](class_interface.md)
### [Appeler un constructeur de classe de base](class_baseconstructor.md)
### [Appeler une méthode de classe de base](class_basemethod.md)

## [Améliorations apportées au débogage de script PowerShell](debug_overview.md)

## [Améliorations apportées à la Configuration d’état souhaité (DSC)](dsc_improvements.md)
### [Configurations]()
#### [Spécification de dépendances entre nœuds](dsc_waitfor.md)
#### [MOF chiffrés](dsc_encryptedmof.md)
#### [Aide à la prise en charge de la configuration DSC](dsc_confighelp.md)
#### [Améliorations liées à la création à l’aide de PowerShell ISE](dsc_authoring.md)
#### [Autorisation des ressources en double identiques dans une configuration](dsc_identicalduplicate.md)
#### [Le mot clé Import-DscResource prend en charge le paramètre -moduleversion](dsc_importdscresource.md)
#### [Prise en charge WOW64 pour le mot clé Configuration](dsc_wow64.md)
### [Ressources]()
#### [Ressources DSC basées sur une classe](dsc_classbasedresource.md)
#### [Débogage de script de ressources DSC](dsc_resourcedebugging.md)
#### [Prise en charge automatique de RunAs pour les ressources DSC](dsc_runas.md)
#### [Prise en charge du contrôle de version côte à côte pour les ressources DSC](dsc_sxsresource.md)
#### [Nouvelles ressources intégrées](dsc_newresources.md)
### [Gestionnaire de configuration local]()
#### [Configurer un nœud avec plusieurs fragments de configuration](dsc_partialconfig.md)
##### [Prise en charge du mode d’actualisation mixte](dsc_partialconfig_mixedmode.md)
#### [Configurer le moteur DSC avec un nouvel attribut](dsc_metaconfiguration.md)
#### [Combinaison de modes PUSH et PULL](dsc_mixedrefreshmode.md)
#### [Informations détaillées sur l’état du gestionnaire de configuration local](dsc_lcmstate.md)
#### [Les fréquences pour RefreshMode et ConfigurationMode ne doivent pas nécessairement être des multiples l’une de l’autre](dsc_freqnomultiple.md)
#### [Valeur supplémentaire pour la propriété RefreshMode](dsc_refreshmode.md)
### [Applets de commande]()
#### [Détails sur l’état de configuration](dsc_getconfigurationstatus.md)
#### [L’applet de commande Test-DscConfiguration prend en charge les configurations de référence](dsc_testconfiguration.md)
#### [Accès direct aux méthodes de ressources DSC](dsc_directaccess.md)
#### [Remettre le document de configuration sans l’appliquer](dsc_publishconfig.md)
#### [Supprimer des documents DSC](dsc_removeconfigdoc.md)
#### [État unifié et cohérent et représentation de l’état](dsc_statestatus.md)
#### [L’applet de commande Set-DscLocalConfigurationManager prend en charge le paramètre -force](dsc_setdsclcm.md)
### [Mode par extraction]()
#### [Extraction à la demande des configurations DSC](dsc_updateconfig.md)
#### [Séparation des ID de nœud et de configuration](dsc_nodeid.md)
#### [Séparation des dépôts de configuration, de ressources et de rapports](dsc_repository.md)
#### [Fournir un rapport sur l’état de la configuration à l’emplacement central](dsc_reporting.md)

## [Auditer l’utilisation de PowerShell à l’aide de la transcription et de la journalisation](audit_overview.md)
### [Options de transcription améliorées](audit_transcript.md)
### [Traçage et journalisation de script](audit_script.md)
### [Applets de commande CMS (Cryptographic Message Syntax)](audit_cms.md)

## [Découverte, installation et inventaire des logiciels avec PackageManagement](oneget_overview.md)
### [Applets de commande PackageManagement](oneget_cmdlets.md)

## [Découverte, installation et inventaire des modules PowerShell avec PowerShellGet](psget_module_overview.md)
### [Inscrire un dépôt PowerShell](psget_psrepository.md)
### [Prise en charge des versions côte à côte sur PowerShell 5.0 ou version ultérieure](psget_modulesxsinstall.md)
### [Installation des dépendances de modules](psget_moduledependency.md)
### [Applets de commande PowerShellGet pour la gestion des modules](psget_modulecmdlets.md)

## [Découverte, installation et gestion des scripts PowerShell avec PowerShellGet](psget_script_overview.md)
### [Applets de commande PowerShellGet pour la gestion des scripts](psget_scriptcmdlets.md)

## [Applets de commande nouvelles et mises à jour d’après les commentaires de la communauté ](feedback_cmdlets.md)
### [Liens symboliques avec les applets de commande Item](feedback_symbolic.md)
### [Applets de commande d’archive](feedback_archive.md)
### [Applets de commande de Presse-papiers](feedback_clipboard.md)
### [Convert-String](feedback_convertstring.md)
### [Extraire et analyser des objets structurés hors de contenu String](feedback_convertfromString.md)
### [Format-Hex](feedback_formathex.md)
### [Paramètre NoNewLine](feedback_nonewline.md)
### [New-TemporaryFile](feedback_tempfile.md)
### [New-Guid](feedback_newguid.md)
### [Get-ChildItem a un paramètre -Depth](feedback_getchilditem.md)
### [Mises à jour de l’objet FileInfo](feedback_fileinfo.md)
### [Prise en charge des modules pour la déclaration des plages de versions (1.*, etc.)](feedback_moduleversionranges.md)

## [Flux d’informations](informationstream_overview.md)

## [Générer des applets de commande PowerShell basées sur un point de terminaison OData](odata_overview.md)

## [Gestion du commutateur réseau avec PowerShell](networkswitch_overview.md)

## [Journalisation de l’inventaire logiciel](sil_overview.md)

# [Limitations et problèmes connus](limitation_overview.md)
## [Problèmes connus liés à la Configuration d’état souhaité (DSC)](limitation_dsc.md)
<!--HONumber=Mar16_HO2-->