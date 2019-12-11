---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Nouveautés dans Windows PowerShell 5.0
ms.openlocfilehash: 08775c1767f1d9d18dafab39d188db152073e69d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417567"
---
# <a name="whats-new-in-windows-powershell-50"></a>Nouveautés dans Windows PowerShell 5.0

Windows PowerShell 5.0 intègre plusieurs nouvelles fonctionnalités importantes qui, en plus d’étendre et de simplifier son utilisation, vous permettent de contrôler et de gérer des environnements Windows plus facilement et plus complètement.

Windows PowerShell 5.0 offre une compatibilité descendante. Les applets de commande, fournisseurs, modules, composants logiciels enfichables, scripts, fonctions et profils conçus pour Windows PowerShell 4.0, Windows PowerShell 3.0 et Windows PowerShell 2.0 fonctionnent généralement dans Windows PowerShell 5.0 sans aucune modification.

## <a name="installing-windows-powershell"></a>Installation de Windows PowerShell

Windows PowerShell 5.0 est installé par défaut sur Windows Server 2016 Technical Preview et Windows 10.

Pour installer Windows PowerShell 5.0 sur Windows Server 2012 R2, Windows 8.1 Entreprise ou Windows 8.1 Professionnel, téléchargez et installez [Windows Management Framework 5.0](https://aka.ms/wmf5download). Avant d'installer Windows Management Framework 5.0, veillez à prendre connaissance des détails du téléchargement et à vérifier la configuration système requise.

## <a name="in-this-topic"></a>Dans cette rubrique

- [Mises à jour de la DSC de Windows PowerShell 4.0 dans KB 3000850](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Nouvelles fonctionnalités de Windows PowerShell 5.0](#new-features-in-windows-powershell-50)
- [Nouvelles fonctionnalités de Windows PowerShell 4.0](#new-features-in-windows-powershell-40)
- [Nouvelles fonctionnalités de Windows PowerShell 3.0](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Mises à jour de Windows PowerShell 4.0 dans le correctif cumulatif de novembre 2014 (KB 3000850)

Plusieurs mises à jour et améliorations de la configuration d’état souhaité Windows PowerShell dans Windows PowerShell 4.0 sont disponibles dans le [correctif cumulatif de novembre 2014 pour Windows RT 8.1, Windows 8.1 et Windows Server 2012 R2](https://support.microsoft.com/kb/3000850/) (KB 3000850). Pour déterminer si KB 3000850 est installé sur votre système, exécutez `Get-Hotfix -Id KB3000850` dans Windows PowerShell.

- Mises à jour des applets de commande existantes dans le module [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx)
  - [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) : plus rapide (en particulier dans ISE).
  - [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) : a un nouveau paramètre, -UseExisting, qui réapplique la dernière configuration appliquée.
  - [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) : le paramètre Force a été corrigé.
  - [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx) : affiche davantage d’informations utiles sur l’état du moteur.
  - [Test-DscConfiguration](https://technet.microsoft.com/library/dn407382.aspx) : renvoie maintenant le nom de l’ordinateur avec la valeur True ou False.
  - [Nouveau-DscChecksum](https://technet.microsoft.com/library/dn521622.aspx) : prend maintenant en charge les chemins d’accès UNC.

- Nouvelles applets de commande dans le module [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx)
  - [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541(v=wps.630).aspx) :  effectue une vérification du serveur Pull à la demande.
  - [Stop-DscConfiguration](https://technet.microsoft.com/library/mt143542(v=wps.630).aspx) :  arrête une configuration en cours d’exécution.
  - [Remove-DscConfigurationDocument](https://technet.microsoft.com/library/mt143544(v=wps.630).aspx) :  permet de supprimer des documents de configuration dans différentes phases (en attente, précédente ou actuelle).

- Rehaussement du langage
  - DependsOn prend maintenant en charge des ressources composites.
  - DependsOn prend maintenant en charge les chiffres dans les noms d’instance de ressource.
  - Les expressions de nœud évaluées comme vides ne déclenchent plus d’erreurs.
  - L’erreur qui se produisait quand une expression de nœud était évaluée comme vide a été corrigée.
  - Les configurations appelant des configurations fonctionnent maintenant dans la console Windows PowerShell.

- Rehaussement du mode par extraction
  - Le mode par extraction prend maintenant en charge tous les fichiers ZIP.
  - **AllowModuleOverwrite** fonctionne maintenant correctement.

- Améliorations apportées à la résilience
  - Le nouveau **DebugMode** permet de recharger des modules de ressources.
  - En cas d’erreur de configuration, le fichier pending.mof n’est plus supprimé.
  - Le gestionnaire de configuration local (LCM) est maintenant plus résilient en cas d’endommagement des paramètres de métaconfiguration.

- Améliorations apportées au diagnostic
  - Un avertissement s’affiche lorsque le LCM modifie les paramètres que vous avez définis pour le minuteur.
  - Les fichiers journaux des erreurs contiennent maintenant la pile des appels pour les ressources Windows PowerShell.

- Améliorations apportées à l’extensibilité
  - La ressource LocalConfigurationManager a une nouvelle propriété, **ActionAfterReboot**.
    - ContinueConfiguration (valeur par défaut) : reprend automatiquement une configuration après le redémarrage d’un nœud cible.
    - StopConfiguration : ne reprend pas automatiquement une configuration après le redémarrage d’un nœud.
  - Une série de tests de cohérence peut maintenant se produire plus souvent qu’une opération d’extraction, ou inversement.
  - Prise en charge de la gestion de versions :  DSC peut maintenant reconnaître un document généré sur un client plus récent (intégrée à [WMF 5.0](https://aka.ms/wmf5download)).

- Améliorations apportées à la prévention des erreurs
  - La version de module est maintenant appliquée avant une configuration.
  - La variable **DebugPreference** est maintenant définie correctement pour les appels Get-TargetResource, Set-TargetResource et Test-TargetResource.

- Améliorations apportées à la gestion des informations d’identification
  - Un certificat est maintenant utilisé, si **Certificate** et **PSDscAllowPlainTextPassword** sont spécifiés.
  - Les informations d’identification sont déchiffrées, même pour les appels Get-TargetResource.
  - Les informations d’identification de métaconfiguration sont chiffrées et déchiffrées.
  - Les PSCredentials sont maintenant déchiffrées quand elles figurent dans un objet incorporé.

- Améliorations apportées aux ressources intégrées
  - Package resource
    - N’installe plus le package incorrect (à partir de sources locales ou web).
    - Prend maintenant en charge le protocole HTTPS.
  - [Package resource](https://technet.microsoft.com/library/dn282132.aspx) prend maintenant en charge le protocole HTTPS.
  - [Archive resource](https://technet.microsoft.com/library/dn249917.aspx) prend maintenant en charge les informations d’identification.

## <a name="new-features-in-windows-powershell-50"></a>Nouvelles fonctionnalités dans Windows PowerShell 5.0

- [Nouvelles fonctionnalités de Windows PowerShell](#new-features-in-windows-powershell)
- [Nouvelles fonctionnalités de la DSC (Configuration de l’état souhaité) de Windows PowerShell](#new-features-in-windows-powershell-desired-state-configuration)
- [Nouvelles fonctionnalités dans Windows PowerShell ISE](#new-features-in-windows-powershell-ise)
- [Nouvelles fonctionnalités des services web Windows PowerShell](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Correctifs de bogues importants dans Windows PowerShell 5.0](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Nouvelles fonctionnalités de Windows PowerShell

- À partir de Windows PowerShell 5.0, vous pouvez développer à l’aide de classes, en utilisant une syntaxe et une sémantique formelles similaires à celles d’autres langages de programmation orientée objet. Des mots clés tels que **Class** et **Enum** ont été ajoutés au langage Windows PowerShell pour prendre en charge la nouvelle fonctionnalité. Pour plus d’informations sur l’utilisation des classes, voir about_Classes.

- Windows PowerShell 5.0 introduit un nouveau flux d’informations structurées qui permet d’échanger des données structurées entre un script et ses appelants (ou un environnement d’hébergement). Vous pouvez maintenant utiliser Write-Host pour envoyer la sortie au flux d’informations. Les flux d’informations fonctionnent également pour PowerShell.Streams, les travaux, les travaux planifiés et les workflows. Les fonctionnalités suivantes prennent en charge le flux d’informations.
  - Une nouvelle applet de commande, Write-Information, permet de spécifier la manière dont Windows PowerShell gère les données de flux d’informations pour une commande. Write-Host est un wrapper pour Write-Information. Write-Information est également une activité de flux de travail prise en charge.
  - Deux nouveaux paramètres courants, InformationVariable et InformationAction, permettent de déterminer le mode d’affichage des flux d’informations en provenance d’une commande. Les valeurs valides pour InformationAction sont SilentlyContinue, Stop, Continue, Inquire, Ignore ou Suspend, SilentlyContinue étant la valeur par défaut. InformationVariable spécifie une chaîne en tant que nom d’une variable dans laquelle vous souhaitez enregistrer les données Write-Host en provenance d’une commande.
  - Une nouvelle variable de préférence, InformationPreference, spécifie votre préférence par défaut pour les données du flux d’informations dans une session Windows PowerShell. La valeur par défaut est SilentlyContinue.
  - Deux nouveaux paramètres communs de workflow, PSInformation et InformationAction, ont été ajoutés.
  - Quand vous utilisez la commande Format-Table, les colonnes de table sont maintenant mises en forme automatiquement en évaluant les 300 premières millisecondes de données qui transitent dans le flux.

- En collaboration avec [Microsoft Research](https://research.microsoft.com/), une nouvelle applet de commande, ConvertFrom-String, a été ajoutée. L’applet de commande ConvertFrom-String permet d’extraire des objets structurés du contenu de chaînes de texte, et de les analyser. Pour plus d’informations, voir ConvertFrom-String.
- Une nouvelle applet de commande, Convert-String, met en forme automatiquement le texte sur la base d’un exemple que vous fournissez dans un paramètre -Example.
- Un nouveau module, Microsoft.PowerShell.Archive, inclut des applets de commande qui vous permettent de compresser des fichiers et dossiers dans des fichiers d’archives (également appelés ZIP), d’extraire des fichiers de fichiers ZIP, et de mettre à jour des fichiers ZIP avec des versions plus récentes des fichiers qui y sont compressés.
- Un nouveau module, PackageManagement, permet de détecter des packages logiciels sur Internet, et de les installer. Le module PackageManagement (anciennement OneGet) est un gestionnaire ou multiplexeur de gestionnaires de package existants (également appelés fournisseurs du package), destiné à unifier la gestion des packages Windows avec une seule interface Windows PowerShell.
- Un nouveau module, PowerShellGet, permet de rechercher, d’installer, de publier et de mettre à jour des modules et des ressources DSC dans la [Galerie PowerShell](https://www.powershellgallery.com/), ou dans un dépôt de module interne que vous pouvez configurer en exécutant l’applet de commande Register-PSRepository.
- Un nouveau mot clé du langage, **Hidden**, a été ajouté pour spécifier qu’un membre (une propriété ou une méthode) n’est pas affiché par défaut dans les résultats de l’applet de commande Get-Member (sauf si vous ajoutez le paramètre -Force). Les propriétés ou méthodes marquées pour être masquées n’apparaissent pas non plus dans les résultats d’IntelliSense, sauf si vous êtes dans un contexte où le membre doit être visible. Par exemple, la variable automatique $This doit afficher les membres masqués dans le contexte de la méthode Class.
- Les applets de commande New-Item, Remove-Item et Get-ChildItem ont été améliorées pour prendre en charge la création et la gestion des [liens symboliques](https://en.wikipedia.org/wiki/Symbolic_link). Le paramètre **-ItemType** de l’applet de commande New-Item accepte une nouvelle valeur, **SymbolicLink**. Vous pouvez maintenant créer des liens symboliques en une seule ligne, en exécutant l’applet de commande New-Item.
- L’applet de commande Get-ChildItem dispose également d’un nouveau paramètre, -Depth, que vous pouvez utiliser avec le paramètre -Recurse pour limiter la récursivité. Par exemple, la commande Get-ChildItem -Recurse -Depth 2 retourne des résultats à partir du dossier actif, de tous les dossiers enfants de ce dossier et de tous les sous-dossiers des dossiers enfants.
- L’applet de commande Copy-Item permet maintenant de copier des fichiers ou dossiers d’une session Windows PowerShell vers une autre. Vous pouvez ainsi copier des fichiers vers des sessions connectées à des ordinateurs distants (notamment les ordinateurs exécutant [Nano Server](https://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx), qui n’ont donc pas d’autre interface). Pour copier des fichiers, spécifiez des ID PSSession comme valeurs pour les nouveaux paramètres -FromSession et -ToSession, en ajoutant -Path et -Destination pour spécifier respectivement le chemin d’origine et la destination. Par exemple, Copy-Item -Path c:\\myFile.txt -ToSession $s -Destination d:\\destinationFolder.
- La transcription Windows PowerShell a été améliorée pour s’appliquer non seulement à l’hôte de la console (**powershell.exe**), mais aussi à toutes les applications d’hébergement telles que Windows PowerShell ISE. Vous pouvez configurer des options de transcription (notamment la transcription à l’échelle du système) en activant le paramètre de stratégie de groupe **Activer la transcription PowerShell** accessible dans Modèles d’administration/Composants Windows/Windows PowerShell.
- Une nouvelle fonctionnalité de traçage de script détaillé vous permet d’activer le suivi et l’analyse détaillés de l’utilisation des scripts Windows PowerShell sur un système. Une fois que vous avez activé le traçage de script détaillé, Windows PowerShell enregistre tous les blocs de scripts dans le journal des événements Suivi d’événements pour Windows (ETW), **Microsoft-Windows-PowerShell/Operational**.
- À partir de Windows PowerShell 5.0, de nouvelles applets de commande CMS (Cryptographic Message Syntax) prennent en charge le chiffrement et le déchiffrement de contenu à l’aide du format IETF standard pour protéger par chiffrement des messages, comme décrit dans le document [RFC (Request For Comments) 5652](https://tools.ietf.org/html/rfc5652). Les applets de commande Get-CmsMessage, Protect-CmsMessage et Unprotect-CmsMessage ont été ajoutées au module [Microsoft.PowerShell.Security](https://technet.microsoft.com/library/hh849807.aspx).
- Les nouvelles applets de commande du module [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) (Get-Runspace, Debug-Runspace, Get-RunspaceDebug, Enable-RunspaceDebug et Disable-RunspaceDebug) vous permettent de définir des options de débogage ainsi que de démarrer et d’arrêter le débogage sur une instance d’exécution. Pour le débogage d’instances d’exécution arbitraires (c’est-à-dire autres que l’instance d’exécution par défaut pour une console Windows PowerShell ou une session Windows PowerShell ISE), Windows PowerShell permet de définir des points d’arrêt dans un script, qui interrompent l’exécution de celui-ci jusqu’à ce que vous puissiez attacher un débogueur pour déboguer le script de l’instance d’exécution. Une prise en charge du débogage imbriqué pour les instances d’exécution arbitraires a été ajoutée au débogueur de script Windows PowerShell pour les instances d’exécution.
- Une nouvelle applet de commande, Format-Hex, a été ajoutée au module [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx). Format-Hex permet d’afficher du texte ou des données binaires au format hexadécimal.
- Les applets de commande Get-Clipboard et Set-Clipboard ont été ajoutées au module [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) pour faciliter l’échange de contenu entre sessions Windows PowerShell. Les applets de commande du Presse-papiers prennent en charge les images, les fichiers audio, les listes de fichiers et le texte.
- Une nouvelle applet de commande, Clear-RecycleBin, a été ajoutée au module [Microsoft.PowerShell.Management](https://technet.microsoft.com/library/hh849827(v=wps.640).aspx). Elle permet de vider la Corbeille d’un lecteur fixe, notamment s’il s’agit d’un lecteur externe. Par défaut, vous êtes invité à confirmer une commande Clear-RecycleBin, car la propriété ConfirmImpact de l’applet de commande a la valeur ConfirmImpact.High.
- Une nouvelle applet de commande, New-TemporaryFile, permet de créer un fichier temporaire dans le cadre d’un script. Par défaut, le fichier temporaire est créé dans ```C:\Users\<user name>\AppData\Local\Temp```.
- Les applets de commande Out-File, Add-Content et Set-Content disposent maintenant d’un nouveau paramètre, -NoNewline, qui omet toute nouvelle ligne après la sortie.
- L’applet de commande New-Guid tire parti de la classe Guid du .NET Framework pour générer un GUID utile quand vous écrivez des scripts ou des ressources DSC.
- Étant donné que les informations sur la version d’un fichier peuvent être trompeuses, en particulier après correction de celui-ci, de nouvelles propriétés de script, FileVersionRaw et ProductVersionRaw, sont disponibles pour les objets FileInfo. Par exemple, vous pouvez exécuter la commande suivante pour afficher les valeurs de ces propriétés pour powerShell.exe, où $pid contient l’ID de processus d’une session active de Windows PowerShell :  ```Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force```
- Les nouvelles applets de commande Enter-PSHostProcess et Exit-PSHostProcess permettent de déboguer des scripts Windows PowerShell dans des processus distincts du processus en cours d’exécution sur la console Windows PowerShell. Exécutez Enter-PSHostProcess pour entrer dans ou associer à un ID de processus spécifique, puis exécutez Get-Runspace pour retourner les instances d’exécution actives au sein du processus. Exécutez Exit-PSHostProcess pour dissocier du processus quand vous avez fini de déboguer le script au sein du processus.
- Une nouvelle applet de commande, Wait-Debugger, a été ajoutée au module [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx). L’applet de commande Wait-Debugger permet d’arrêter l’exécution d’un script dans le débogueur avant d’exécuter l’instruction suivante du script.
- Le débogueur Windows PowerShell Workflow prend maintenant en charge l’exécution par commande ou via la touche Tab, et vous pouvez déboguer des fonctions de workflow imbriquées. Vous pouvez maintenant appuyer sur **Ctrl+Pause** pour activer le débogueur dans un script en cours d’exécution, dans des sessions tant locales que distantes, et dans un script de workflow.
- Une applet de commande, Debug-Job, a été ajoutée au module [Microsoft.PowerShell.Core](https://technet.microsoft.com/library/hh849695.aspx). Elle permet de déboguer des scripts de travail en cours d’exécution pour Windows PowerShell Workflow, l’arrière-plan et les travaux en cours d’exécution dans des sessions à distance.
- Un nouvel état, AtBreakpoint, a été ajouté pour les travaux Windows PowerShell. L’état AtBreakpoint s’applique quand un travail exécute un script incluant une série de points d’arrêt, au moment où le script atteint un point d’arrêt. Quand un travail est interrompu à un point d’arrêt de débogage, vous devez déboguer le travail en exécutant l’applet de commande Debug-Job.
- Windows PowerShell 5.0 prend en charge plusieurs versions d’un module Windows PowerShell à l’intérieur du même dossier dans $PSModulePath. Une propriété, RequiredVersion, a été ajoutée à la classe ModuleSpecification pour vous aider à obtenir la version souhaitée d’un module. Cette propriété ne peut pas être utilisée en même temps que la propriété ModuleVersion. La propriété RequiredVersion est maintenant prise en charge. Elle est incluse dans la valeur du paramètre FullyQualifiedName des applets de commande Get-Module, Import-Module et Remove-Module.
- Vous pouvez maintenant effectuer une validation de la version du module en exécutant l’applet de commande Test-ModuleManifest.
- Les résultats de l’applet de commande Get-Command affichent maintenant une colonne Version suite à l’ajout d’une nouvelle propriété, Version, à la classe CommandInfo. L’applet de commande Get-Command affiche les commandes de plusieurs versions du même module. La propriété Version fait également partie des classes dérivées de CmdletInfo : CmdletInfo et ApplicationInfo.
- L’applet de commande Get-Command dispose d’un nouveau paramètre, -ShowCommandInfo, qui retourne les informations de ShowCommand en tant que PSObjects. Cette fonctionnalité est particulièrement utile quand l’applet de commande Show-Command est exécutée dans Windows PowerShell ISE à l’aide de la communication à distance Windows PowerShell. Le paramètre -ShowCommandInfo remplace la fonction Get-SerializedCommand existante du module Microsoft.PowerShell.Utility, mais le script Get-SerializedCommand est toujours disponible pour prendre en charge les scripts de bas niveau.
- Une nouvelle applet de commande, Get-ItemPropertyValue, permet d’obtenir la valeur d’une propriété sans utiliser de notation par points. Par exemple, dans les versions plus anciennes de Windows PowerShell, vous pouvez exécuter la commande suivante pour obtenir la valeur de la propriété de base de l’application de la clé de Registre PowerShellEngine : **(Get-ItemProperty -Path HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine -Name ApplicationBase).ApplicationBase**. À partir de Windows PowerShell 5.0, vous pouvez exécuter **Get-ItemPropertyValue -Path HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine -Name ApplicationBase**.
- La console Windows PowerShell utilise à présent une coloration de la syntaxe, tout comme dans Windows PowerShell ISE.
- Un nouveau module, NetworkSwitch, contient des applets de commande permettant d’appliquer un commutateur, un réseau local virtuel (VLAN) et une configuration de port de commutateur réseau de couche 2 de base à des commutateurs réseau certifiés par le logo Windows PowerShell 2012 R2.
- Le paramètre FullyQualifiedName a été ajouté aux applets de commande Import-Module et Remove-Module pour prendre en charge le stockage de plusieurs versions d’un même module.
- Les applets de commande Save-Help, Update-Help, Import-PSSession, Export-PSSession et Get-Command disposent d’un nouveau paramètre, FullyQualifiedModule, de type ModuleSpecification. Ajoutez ce paramètre pour spécifier un module par son nom complet.
- La valeur de **$PSVersionTable.PSVersion** a été mise à jour. Il s’agit maintenant de 5.0.
- WMF 5.0 (PowerShell 5.0) inclut le module **Pester**.  Pester est un framework de tests unitaires pour PowerShell. Il fournit quelques mots clés simples à utiliser qui vous permettent de créer des tests pour vos scripts.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Nouvelles fonctionnalités dans la configuration d’état souhaité de Windows PowerShell

- Le rehaussement du langage Windows PowerShell permet de définir des ressources de configuration d’état souhaité (DSC) Windows PowerShell à l’aide de classes. Import-DscResource est maintenant un vrai mot clé dynamique. Windows PowerShell analyse le module racine du module spécifié, en recherchant des classes contenant l’attribut DscResource. Vous pouvez maintenant utiliser des classes pour définir des ressources DSC, dans lesquelles un fichier MOF ou un sous-dossier DSCResource dans le dossier du module ne sont pas requis. Un fichier de module Windows PowerShell peut contenir plusieurs classes de ressources DSC.
- Un nouveau paramètre, ThrottleLimit, a été ajouté aux applets de commande suivantes dans le module PSDesiredStateConfiguration. Ajoutez le paramètre ThrottleLimit pour spécifier le nombre d’ordinateurs cibles ou d’appareils sur lesquels vous souhaitez que la commande opère simultanément.
  - Get-DscConfiguration
  - Get-DscConfigurationStatus
  - Get-DscLocalConfigurationManager
  - Restore-DscConfiguration
  - Test-DscConfiguration
  - Compare-DscConfiguration
  - Publish-DscConfiguration
  - Set-DscLocalConfigurationManager
  - Start-DscConfiguration
  - Update-DscConfiguration
- Avec le signalement d’erreurs DSC centralisé, outre que les informations d’erreur complètes sont enregistrées dans le journal des événements, celles-ci peuvent être envoyées à un emplacement central à des fins d’analyse ultérieure. Vous pouvez utiliser cet emplacement central pour stocker des erreurs de configuration DSC qui se sont produites pour un serveur quelconque dans son environnement. Une fois le serveur de rapports défini dans la métaconfiguration, toutes les erreurs sont envoyées au serveur de rapports et stockées dans une base de données. Vous pouvez configurer cette fonctionnalité, indépendamment du fait qu’un nœud cible soit configuré ou non pour extraire des configurations d’un serveur collecteur.
- Les améliorations apportées à Windows PowerShell ISE facilitent la création de ressources DSC. Vous pouvez maintenant effectuer les opérations suivantes.
  - Énumération de toutes les ressources DSC dans un bloc **configuration** ou **node** en entrant **Ctrl+Espace** dans une ligne vide du bloc.
  - Saisie semi-automatique sur les propriétés de ressources du type **enumeration**.
  - Saisie semi-automatique sur la propriété **DependsOn** des ressources DSC, basée sur d’autres instances de ressources dans la configuration.
  - Saisie semi-automatique via la touche Tab améliorée pour les valeurs de propriété de ressource.
- Un utilisateur peut maintenant exécuter une ressource sous un ensemble spécifié d’informations d’identification en ajoutant l’attribut **PSDscRunAsCredential** à un bloc de nœud. Par exemple, PSDscRunAsCredential = Get-Credential Contoso\\DscUser. Cette fonctionnalité est utile pour créer des configurations qui exécutent Windows Installer et des programmes d’installation exécutables, accèdent à la ruche du Registre par utilisateur ou effectuent d’autres tâches en dehors du contexte de l’utilisateur actuel.
- La prise en charge 32 bits (avec processeur x86) a été ajoutée pour le mot clé **Configuration**.
- Windows PowerShell inclut maintenant la prise en charge de l’aide personnalisée pour les configurations DSC, définie par l’ajout de \[CmdletBinding()] à la fonction de configuration générée.
- Un nouvel attribut, **DscLocalConfigurationManager**, désigne un bloc de configuration en tant que métaconfiguration, qui sert à configurer le gestionnaire de configuration local DSC. Avec cet attribut, une configuration peut contenir uniquement des éléments qui configurent le gestionnaire de configuration local DSC. Pendant le traitement, cette configuration génère un fichier \*.meta.mof qui est ensuite envoyé aux nœuds cibles appropriés en exécutant l’applet de commande Set-DscLocalConfigurationManager.
- Les configurations partielles sont maintenant autorisées dans Windows PowerShell 5.0. Vous pouvez distribuer des documents de configuration à un nœud en plusieurs fragments. Pour qu’un nœud reçoive plusieurs fragments d’un document de configuration, il faut que son Gestionnaire de configuration local soit configuré pour spécifier les fragments attendus.
- La synchronisation entre ordinateurs est une nouveauté de DSC dans Windows PowerShell 5.0. Avec les ressources WaitFor\* intégrées (**WaitForAll**, **WaitForAny** et **WaitForSome**), vous pouvez maintenant spécifier des dépendances entre ordinateurs lors d’exécutions de configuration, sans orchestration externe. Ces ressources fournissent une synchronisation de nœud à nœud à l’aide de connexions CIM sur le protocole WS-Man. Une configuration peut attendre que l’état d’une ressource spécifique d’un autre ordinateur change.
- Une nouvelle fonctionnalité de sécurité de délégation, JEA (Just Enough Administration), tire parti de DSC et des instances d’exécution contraintes de Windows PowerShell pour protéger les entreprises contre la perte de données ou des actes préjudiciables commis par employés, intentionnellement ou non. Pour plus d’informations sur la fonctionnalité JEA, y compris l’emplacement à partir duquel vous pouvez télécharger la ressource DSC xJEA, voir [Just Enough Administration, Step by Step](https://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx) (en anglais).
- Les nouvelles applets de commande suivantes ont été ajoutées au module PSDesiredStateConfiguration.
  - Une nouvelle applet de commande, Get-DscConfigurationStatus, obtient des informations de haut niveau sur l’état de configuration à partir d’un nœud cible. Vous pouvez obtenir l’état de la dernière configuration ou de toutes les configurations.
  - Une nouvelle applet de commande, Compare-DscConfiguration, compare une configuration spécifiée à l’état réel d’un ou plusieurs nœuds cibles.
  - Une nouvelle applet de commande, Publish-DscConfiguration, copie un fichier MOF de configuration sur un nœud cible, mais n’applique pas la configuration. Cette configuration est appliquée durant le contrôle de cohérence suivant ou quand vous exécutez l’applet de commande Update-DscConfiguration.
  - Une nouvelle applet de commande, Test-DscConfiguration, permet de vérifier si une configuration obtenue correspond à la configuration souhaitée, en retournant la valeur True si c’est le cas, ou la valeur False si ça ne l’est pas.
  - Une nouvelle applet de commande, Update-DscConfiguration, force le traitement d’une configuration. Si le gestionnaire de configuration local est en mode par extraction, l’applet de commande obtient la configuration à partir du serveur collecteur avant de l’appliquer.

### <a name="new-features-in-windows-powershell-ise"></a>Nouvelles fonctionnalités dans Windows PowerShell ISE

- Vous pouvez maintenant modifier des scripts et fichiers Windows PowerShell distants dans une copie locale de Windows PowerShell ISE, en exécutant Enter-PSSession pour démarrer une session à distance sur l’ordinateur qui stocke les fichiers à modifier, puis en exécutant **PSEdit \<chemin et nom de fichier sur l’ordinateur distant\>** . Cette fonctionnalité facilite la modification de fichiers Windows PowerShell stockés sur l’option d’installation minimale de Windows Server, où Windows PowerShell ISE ne peut pas s’exécuter.
- L’applet de commande Start-Transcript est maintenant prise en charge dans Windows PowerShell ISE.
- Vous pouvez maintenant déboguer des scripts à distance dans Windows PowerShell ISE.
- Une nouvelle option de menu, **Interrompre tout** (Ctrl+B) arrête le débogueur pour les scripts s’exécutant tant en local qu’à distance.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Nouvelles fonctionnalités dans Windows PowerShell Web Services (Extension ISS Management OData)

- À partir de Windows PowerShell 5.0, vous pouvez générer un ensemble d’applets de commande Windows PowerShell basées sur la fonctionnalité exposée par un point de terminaison OData, en exécutant l’applet de commande Export-ODataEndpointProxy, figurant dans le nouveau module [Microsoft.PowerShell.OdataUtils](https://technet.microsoft.com/library/dn818507(v=wps.640).aspx).

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Correctifs de bogues notables dans Windows PowerShell 5.0

- Windows PowerShell 5.0 inclut une nouvelle implémentation de COM, qui améliore sensiblement les performances quand vous travaillez avec des objets COM. Pour une démonstration vidéo de l’effet obtenu, voir [Com_Perf_Improvements](https://1drv.ms/1qu3UPZ).
- Les performances de la première saisie semi-automatique par le biais de la touche Tab dans une session Windows PowerShell ont été sensiblement améliorées. Le temps d’exécution a en effet été raccourci de près de 500 ms.

## <a name="new-features-in-windows-powershell-40"></a>Nouvelles fonctionnalités dans Windows PowerShell 4.0

Windows PowerShell 4.0 offre une compatibilité descendante. Les applets de commande, fournisseurs, modules, composants logiciels enfichables, scripts, fonctions et profils conçus pour Windows PowerShell 3.0 et Windows PowerShell 2.0 fonctionnent dans Windows PowerShell 4.0 sans aucune modification.

Windows PowerShell 4.0 est installé par défaut sur Windows 8.1 et Windows Server 2012 R2. Pour installer Windows PowerShell 4.0 sur Windows 7 avec SP1, ou Windows Server 2008 R2, téléchargez et installez [Windows Management Framework 4.0](https://www.microsoft.com/download/details.aspx?id=40855). Avant d'installer Windows Management Framework 4.0, veillez à prendre connaissance des détails du téléchargement et à vérifier la configuration système requise.

- [Nouvelles fonctionnalités de Windows PowerShell](#new-features-in-windows-powershell-1)
- [Nouvelles fonctionnalités de l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Nouvelles fonctionnalités de Windows PowerShell Workflow](#new-features-in-windows-powershell-workflow)
- [Nouvelles fonctionnalités des services web Windows PowerShell](#new-features-in-windows-powershell-web-services)
- [Nouvelles fonctionnalités d’Accès web Windows PowerShell](#new-features-in-windows-powershell-web-access)
- [Correctifs de bogues importants dans Windows PowerShell 4.0](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0 intègre les nouvelles fonctionnalités suivantes.

### <a name="a-namenew-features-in-windows-powershell-1-new-features-in-windows-powershell"></a><a name="new-features-in-windows-powershell-1" />Nouvelles fonctionnalités dans Windows PowerShell

- La **configuration d’état souhaité (DSC) Windows PowerShell** est un nouveau système de gestion dans Windows PowerShell 4.0, qui permet de déployer et de gérer les données de configuration de services logiciels et l’environnement dans lequel ces services s’exécutent. Pour plus d’informations sur DSC, voir [Prendre en main la configuration d’état souhaité Windows PowerShell](https://technet.microsoft.com/library/c134aa32-b085-4656-9a89-955d8ff768d0).
- L’applet de commande **Save-Help** permet maintenant d’enregistrer l’aide pour des modules installés sur des ordinateurs distants. Vous pouvez utiliser Save-Help pour télécharger l'aide des modules à partir d'un client connecté à Internet (sur lequel les modules au sujet desquels vous avez besoin d'aide ne sont pas tous forcément installés), puis copier l'aide enregistrée dans un dossier partagé distant ou un ordinateur distant n'ayant pas accès à Internet.
- Le débogueur Windows PowerShell a été amélioré pour permettre de déboguer des workflows Windows PowerShell, ainsi que des scripts qui s’exécutent sur des ordinateurs distants. Il est maintenant possible de déboguer les workflows Windows PowerShell au niveau du script soit à partir de la ligne de commande Windows PowerShell, soit à partir de Windows PowerShell ISE. Les scripts Windows PowerShell, notamment les workflows de script, peuvent maintenant être débogués sur des sessions à distance. Les sessions de débogage à distance sont conservées sur des sessions à distance Windows PowerShell qui sont déconnectées, puis reconnectées.
- Le paramètre **RunNow** pour les applets de commande **Register-ScheduledJob** et **Set-ScheduledJob** vous évite de devoir définir une date et une heure de démarrage immédiat pour les travaux à l’aide du paramètre **Trigger**.
- Les applets de commande **Invoke-RestMethod** et **Invoke-WebRequest** vous permettent maintenant de définir tous les en-têtes à l’aide du paramètre Headers. Bien que ce paramètre ait toujours existé, il faisait partie des quelques paramètres d'applets de commande web qui généraient des erreurs ou des exceptions.
- L’applet de commande **Get-Module** dispose d’un nouveau paramètre, **FullyQualifiedName**, du type **ModuleSpecification\[]** . Le paramètre **FullyQualifiedName** de l’applet de commande Get-Module permet maintenant de spécifier un module par son nom, sa version et éventuellement son GUID.
- Le paramètre de stratégie d’exécution par défaut sur Windows Server 2012 R2 est **RemoteSigned**. Sur Windows 8.1, le paramètre par défaut ne change pas.
- À partir de Windows PowerShell 4.0, l’appel de méthode à l’aide de noms de méthodes dynamiques est pris en charge. Vous pouvez utiliser une variable pour stocker un nom de méthode, puis appeler la méthode de façon dynamique en appelant la variable.
- Les travaux de flux de travail asynchrones ne sont plus supprimés au terme du délai d’attente spécifié par le paramètre commun de flux de travail **PSElapsedTimeoutSec**.
- Un nouveau paramètre, **RepeatIndefinitely**, a été ajouté aux applets de commande **New-JobTrigger** et **Set-JobTrigger**. Celui-ci vous évite de devoir affecter une valeur **TimeSpan.MaxValue** au paramètre **RepetitionDuration** pour exécuter un travail planifié à plusieurs reprises pendant une durée indéterminée.
- Le paramètre **Passthru** a été ajouté aux applets de commande **Enable-JobTrigger** et **Disable-JobTrigger**. Le paramètre Passthru affiche tous les objets créés ou modifiés par votre commande.
- Les noms des paramètres utilisés pour spécifier un groupe de travail dans les applets de commande **Add-Computer** et **Remove-Computer** sont maintenant cohérents. Les deux applets de commande utilisent maintenant le paramètre **WorkgroupName**.
- Un nouveau paramètre commun, **PipelineVariable**, a été ajouté. PipelineVariable vous permet d'enregistrer les résultats d'une commande dirigée (ou une partie de celle-ci) en tant que variable pouvant être passée via le reste du pipeline.
- Le filtrage de collection à l'aide d'une syntaxe de méthode est maintenant pris en charge. Cela signifie que vous pouvez à présent filtrer une collection d'objets à l'aide d'une syntaxe simplifiée, semblable à celle utilisée pour Where() ou Where-Object, dont le format est celui d'un appel de méthode. Voici un exemple : (Get-Process).where({$_.Name -match 'powershell'})
- L’applet de commande **Get-Process** dispose d’un nouveau paramètre de commutateur, **IncludeUserName**.
- Une nouvelle applet de commande, **Get-FileHash**, a été ajoutée. Celle-ci retourne un hachage de fichier dans l’un des formats disponibles pour un fichier spécifié.
- Dans Windows PowerShell 4.0, si un module utilise la clé **DefaultCommandPrefix** dans son manifeste ou que l’utilisateur importe un module avec le paramètre **Prefix**, la propriété **ExportedCommands** du module affiche les commandes dans le module avec le préfixe. Quand vous exécutez les commandes à l’aide de la syntaxe propre au module (NomDeModule\\NomDeCommande), les noms des commandes doivent inclure le préfixe.
- La valeur de **$PSVersionTable.PSVersion** a été mise à jour. Il s’agit maintenant de 4.0.
- Le comportement de l’opérateur **Where()** a changé. `Collection.Where('property -match name')` n’accepte plus d’expression de chaîne au format `"Property -CompareOperator Value"`. En revanche, l’opérateur **Where()** accepte toujours les expressions de chaîne au format bloc de script.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Nouvelles fonctionnalités de l'environnement d'écriture de scripts intégré (ISE) de Windows PowerShell

- Windows PowerShell ISE prend en charge le débogage et le débogage de script à distance de Windows PowerShell Workflow.
- La prise en charge d’IntelliSense a été ajoutée pour les configurations et les fournisseurs de configuration d’état souhaité Windows PowerShell.

### <a name="new-features-in-windows-powershell-workflow"></a>Nouvelles fonctionnalités de Windows PowerShell Workflow

- Un nouveau paramètre commun, **PipelineVariable**, est maintenant pris en charge dans le contexte des pipelines itératifs, comme ceux utilisés par System Center Orchestrator. Il s’agit en fait des pipelines qui exécutent simplement les commandes de gauche à droite, par opposition à une exécution parsemée via une diffusion en continu.
- La liaison de paramètre a été considérablement améliorée pour fonctionner en dehors des scénarios de saisie semi-automatique par tabulation, comme avec les commandes qui n'existent pas dans l'instance d'exécution actuelle.
- Les activités de conteneur personnalisées sont maintenant prises en charge dans Windows PowerShell Workflow. Si un paramètre d’activité est de type **Activity** ou **Activity\[]** (ou bien une collection générique d’activités) et que l’utilisateur a fourni un bloc de script comme argument, Windows PowerShell Workflow convertit le bloc de script au format XAML, comme lors d’une compilation de script à workflow Windows PowerShell normale.
- Après un incident, Windows PowerShell Workflow se reconnecte automatiquement aux nœuds gérés.
- Vous pouvez également limiter les instructions d’activités **Foreach -Parallel** à l’aide de la propriété **ThrottleLimit**.
- Le paramètre commun **ErrorAction** offre une nouvelle valeur valide, **Suspend**, réservée exclusivement aux workflows.
- Un point de terminaison de workflow se ferme maintenant automatiquement en l'absence de sessions actives, de tâches en cours et de tâches en attente. Cette fonctionnalité conserve les ressources sur l'ordinateur jouant le rôle de serveur de workflow quand les conditions de fermeture automatique sont remplies.

### <a name="new-features-in-windows-powershell-web-services"></a>Nouvelles fonctionnalités de Windows PowerShell Web Services

- Si une erreur se produit dans Windows PowerShell Web Services (PSWS ou Extension ISS Management OData) alors qu’une applet de commande est en cours d’exécution, des messages d’erreur plus détaillés sont retournés à l’appelant. En outre, les codes d’erreur suivent [instructions relatives aux codes d’erreur d’API REST de Windows Azure](https://msdn.microsoft.com/library/windowsazure/dd179357.aspx).
- Un point de terminaison peut maintenant définir la version de l'API et forcer l'utilisation d'une version spécifique de l'API. En cas d'incompatibilité de version entre le client et le serveur, les erreurs sont affichées à la fois sur le client et le serveur.
- La génération automatique des valeurs des champs manquants dans le schéma de répartition simplifie la gestion du schéma. La génération se produit, comme point de départ utile, même si le schéma de distribution n'existe pas.
- La gestion des types dans PSWS a été améliorée pour prendre en charge les types qui utilisent un constructeur autre que le constructeur par défaut. Le comportement adopté est similaire à celui de **PSTypeConverter** dans Windows PowerShell. Vous pouvez ainsi utiliser des types complexes avec PSWS.
- PSWS permet maintenant d'étendre une instance associée lors de l'exécution d'une requête. Pour le contenu binaire plus volumineux (comme des images, des fichiers audio ou des vidéos), le coût de transfert est élevé. Il est donc préférable de transférer les données binaires sans encodage. PSWS utilise des flux de ressources nommés pour le transfert sans encodage. Le flux de ressources nommé est une propriété d’une entité de type **Edm.Stream**. Chaque flux de ressources nommé possède un URI distinct pour les opérations GET ou UPDATE.
- Les actions OData proposent maintenant un mécanisme pour appeler des méthodes non CRUD (Create, Read, Update et Delete) sur une ressource. Vous pouvez appeler une action en envoyant une demande HTTP POST à l'URI qui est défini pour l'action. Les paramètres de l'action sont définis dans le corps de la demande POST.
- Par souci de cohérence avec les recommandations Windows Azure, toutes les URL doivent être simplifiées. Suite à une modification apportée à **Key As Segment**, des clés uniques peuvent être représentées en tant que segments. Comme précédemment, si des références utilisent plusieurs valeurs de clé, les valeurs doivent être séparées par des virgules et incluses entre parenthèses.
- Avant cette version de PSWS, la seule façon d'effectuer des opérations Create, Update ou Delete consistait à appeler Post, Put ou Delete sur une ressource de niveau supérieur. Dans cette version de PSWS, les opérations sur les ressources contenues permettent non seulement d'obtenir les mêmes résultats, mais aussi d'atteindre les mêmes ressources de manière moins directe (comme si ces ressources étaient contenues).

### <a name="new-features-in-windows-powershell-web-access"></a>Nouvelles fonctionnalités de Windows PowerShell Web Access

- Vous pouvez vous déconnecter de sessions existantes et vous y reconnecter par l’intermédiaire de la console Accès Web Windows PowerShell. Le bouton **Enregistrer** dans la console web permet de vous déconnecter d’une session sans la supprimer et de vous y reconnecter ultérieurement.
- Vous pouvez afficher les paramètres par défaut dans la page de connexion. Pour afficher les paramètres par défaut, configurez les valeurs de tous les paramètres affichés dans la zone **Paramètres de connexion facultatifs** de la page de connexion dans un fichier nommé **web.config**. Vous pouvez utiliser le fichier **web.config** pour configurer tous les paramètres de connexion facultatifs, à l’exception d’un deuxième ou d’un autre ensemble d’informations d’identification.
- Dans Windows Server 2012 R2, vous pouvez gérer à distance les règles d’autorisation pour Accès Web Windows PowerShell. Les applets de commande **Add-PswaAuthorizationRule** et **Test-PswaAuthorizationRule** incluent maintenant un paramètre Credential qui permet aux administrateurs de gérer les règles d’autorisation à partir d’un ordinateur distant ou dans une session Accès Web Windows PowerShell.
- Vous pouvez maintenant avoir plusieurs sessions Accès Web Windows PowerShell dans une même session de navigateur. Pour cela, il vous suffit d’ouvrir un nouvel onglet de navigateur pour chaque session. Il n’est plus nécessaire d’ouvrir une nouvelle session de navigateur pour se connecter à une nouvelle session dans la console web Windows PowerShell.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Correctifs de bogues importants dans Windows PowerShell 4.0

- L’applet de commande **Get-Counter** peut maintenant retourner des compteurs qui contiennent une apostrophe dans les éditions françaises de Windows.
- Vous pouvez maintenant afficher la méthode **GetType** sur des objets désérialisés.
- Les instructions **#Requires** permettent maintenant aux utilisateurs d’exiger des droits d’accès réservés aux administrateurs, si nécessaire.
- L’applet de commande **Import-Csv** ignore maintenant les lignes vides.
- Un problème lié à une utilisation trop importante de la mémoire par Windows PowerShell ISE lors de l’exécution d’une commande **Invoke-WebRequest** a été résolu.
- L’applet de commande **Get-Module** affiche maintenant les versions des modules dans une colonne **Version**.
- Remove-Item -Recurse supprime maintenant les éléments des sous-dossiers comme prévu.
- La propriété **UserName** a été ajoutée aux objets de sortie **Get-Process**.
- L’applet de commande **Invoke-RestMethod** retourne maintenant tous les résultats disponibles.
- L’applet de commende **Add\-Member** s’applique maintenant aux tables de hachage, même si celles-ci n’ont pas encore été sollicitées.
- L’applet de commande **Select-Object -Expand** n’échoue plus et ne génère plus d’exception si la valeur de la propriété est null ou vide.
- L’applet de commende **Get-Process** peut maintenant être utilisée dans un pipeline avec d’autres commandes qui obtiennent la propriété **ComputerName** d’objets.
- Les applets de commande **ConvertTo-Json** et **ConvertFrom-Json** peuvent maintenant accepter les termes entre guillemets doubles, et leurs messages d’erreur sont localisables.
- L’applet de commande **Get-Job** retourne maintenant toutes les travaux planifiés terminés, même dans de nouvelles sessions.
- Les problèmes liés au montage et au démontage de disques durs virtuels à l’aide du fournisseur **FileSystem** dans Windows PowerShell 4.0 ont été résolus. Windows PowerShell peut maintenant détecter de nouveaux lecteurs quand ils sont montés dans la même session.
- Il n’est plus nécessaire de charger explicitement les modules **ScheduledJob** et **Workflow** pour utiliser leurs types de travaux.
- Les performances du processus d'importation de workflows définissant des workflows imbriqués ont été améliorées. Ce processus est maintenant plus rapide.

## <a name="new-features-in-windows-powershell-30"></a>Nouvelles fonctionnalités dans Windows PowerShell 3.0

Windows PowerShell 3.0 intègre les nouvelles fonctionnalités suivantes.

- [Windows PowerShell Workflow](#windows-powershell-workflow)
- [Accès Web Windows PowerShell](#windows-powershell-web-access)
- [Nouvelles fonctionnalités de Windows PowerShell ISE](#new-windows-powershell-ise-features)
- [Prise en charge du Microsoft .NET Framework 4.0](#support-for-microsoft-net-framework-4)
- [Prise en charge de l’environnement de préinstallation Windows (WinPE)](#support-for-windows-preinstallation-environment)
- [Sessions déconnectées](#disconnected-sessions)
- [Connectivité robuste des sessions](#robust-session-connectivity)
- [Système d’aide actualisable](#updatable-help-system)
- [Aide en ligne améliorée](#enhanced-online-help)
- [Intégration de CIM](#cim-integration)
- [Fichiers de configuration de session](#session-configuration-files)
- [Travaux planifiés et intégration du Planificateur de tâches](#scheduled-jobs-and-task-scheduler-integration)
- [Améliorations apportées au langage Windows PowerShell](#windows-powershell-language-enhancements)
- [Nouvelles applets de commande principales](#new-core-cmdlets)
- [Améliorations apportées aux applets de commande principales et aux fournisseurs existants](#improvements-to-existing-core-cmdlets-and-providers)
- [Importation et découverte des modules à distance](#remote-module-import-and-discovery)
- [Amélioration de la saisie semi-automatique via la touche Tab](#enhanced-tab-completion)
- [Chargement automatique des modules](#module-auto-loading)
- [Améliorations de l’expérience des modules](#module-experience-improvements)
- [Découverte des commandes simplifiée](#simplified-command-discovery)
- [Prise en charge améliorée de la journalisation, du diagnostic et de la stratégie de groupe](#improved-logging-diagnostics-and-group-policy-support)
- [Améliorations apportées à la mise en forme et aux sorties](#formatting-and-output-improvements)
- [Amélioration de l’expérience de l’hôte de la console](#enhanced-console-host-experience)
- [Nouvelles API d’applet de commande et d’hébergement](#new-cmdlet-and-hosting-apis)
- [Améliorations des performances](#performance-improvements)
- [Prise en charge de RunAs et des hôtes partagés](#runas-and-shared-host-support)
- [Améliorations de la gestion des caractères spéciaux](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Windows PowerShell Workflow

Grâce au workflow Windows PowerShell, vous bénéficiez de toute la puissance de Windows Workflow Foundation dans Windows PowerShell. Vous pouvez écrire des workflows en XAML ou dans le langage Windows PowerShell, et les exécuter de la même façon qu’une applet de commande. L’applet de commande [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) obtient les commandes de workflow et l’applet de commande [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) obtient de l’aide sur les workflows.

Les workflows sont des séquences d'activités de gestion de plusieurs ordinateurs. Ces séquences sont longues, reproductibles, fréquentes, parallèles et redémarrables ; elles peuvent aussi être interrompues et suspendues. Il est possible de reprendre des workflows suite à une interruption accidentelle ou intentionnelle, une indisponibilité du réseau, un redémarrage de Windows ou une panne de courant.

Les workflows sont aussi portables, c'est-à-dire qu'ils peuvent être exportés vers des fichiers XAML ou importés à partir de ceux-ci. Vous pouvez écrire des configurations de session personnalisées qui permettent à des utilisateurs délégués ou subordonnés d'exécuter un workflow ou les activités qu'il contient.

Les avantages de Windows PowerShell Workflow sont les suivants :

- Automatisation des tâches séquencées et longues.
- **Surveillance à distance des tâches longues**. Visibilité à tout moment de l'état et de la progression des activités.
- **Gestion de plusieurs ordinateurs.** Exécution simultanée de tâches en tant que workflows sur des centaines de nœuds gérés. Windows PowerShell Workflow inclut une bibliothèque intégrée de paramètres de gestion communs, tels que **PSComputerName**, qui prennent en charge les scénarios de gestion de plusieurs ordinateurs.
- **Exécution en une seule tâche de processus complexes.** Vous pouvez combiner des scripts associés dans un seul workflow pour implémenter un scénario complet de bout en bout.
- **Persistance.** Un flux de travail est enregistré à des points de contrôle spécifiques définis par son auteur, ce qui permet de reprendre le flux de travail à partir de la dernière tâche persistante (ou point de contrôle) au lieu de redémarrer le flux de travail depuis le début.
- **Robustesse.** Récupération après défaillance automatisée. Les workflows survivent aux redémarrages planifiés et non planifiés. Vous pouvez suspendre l'exécution d'un workflow, puis le reprendre à partir du dernier point de persistance. Les auteurs de workflows peuvent désigner des activités spécifiques à réexécuter en cas de défaillance sur un ou plusieurs nœuds gérés.
- **Possibilité de déconnexion, de reconnexion et d’exécution dans des sessions déconnectées.** Les utilisateurs peuvent se connecter au serveur de workflow et s'en déconnecter, mais le workflow s'exécute en continu. Vous pouvez fermer la session sur l'ordinateur client ou redémarrer ce dernier, et surveiller l'exécution du workflow à partir d'un autre ordinateur sans l’interrompre.
- **Planification.** Les tâches de workflow peuvent être planifiées comme une applet de commande ou un script Windows PowerShell.
- **Limitation des workflows et des connexions.** Vous pouvez limiter l'exécution des workflows et les connexions aux nœuds, ce qui permet de prendre en charge des scénarios évolutifs et à haute disponibilité.

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web Access

Accès Web Windows PowerShell est une fonctionnalité Windows Server 2012 qui permet aux utilisateurs d’exécuter des commandes et des scripts Windows PowerShell dans une console web. Les appareils qui utilisent la console web ne nécessitent ni Windows PowerShell, ni un logiciel de gestion à distance, ni l’installation d’un plug-in de navigateur. Il suffit de disposer d’une passerelle Accès Web Windows PowerShell correctement configurée, et d’un navigateur d’appareil client prenant en charge JavaScript et acceptant les cookies.

Pour plus d’informations, voir [Déployer un Accès Windows PowerShell Web](https://go.microsoft.com/fwlink/p/?LinkID=221050).

### <a name="new-windows-powershell-ise-features"></a>Nouvelles fonctionnalités de Windows PowerShell ISE

Pour Windows PowerShell 3.0, l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell comprend de nombreuses nouveautés, notamment IntelliSense, une fenêtre Show-Command, un volet de console unifiée, des extraits de code, la correspondance d’accolade, des sections à développement/réduction, l’enregistrement automatique, une liste des éléments récents, la copie riche, la copie de blocs, ainsi que la prise en charge complète de l’écriture de workflows de scripts Windows PowerShell. Pour plus d’informations, voir [about_Windows_PowerShell_ISE [v3]](https://technet.microsoft.com/library/dfa54d47-60c6-4fff-8197-c747e8d411bb).

### <a name="support-for-microsoft-net-framework-4"></a>Prise en charge du Microsoft .NET Framework 4

Windows PowerShell repose sur le Common Language Runtime 4.0. Les auteurs d’applets de commande, de scripts et de flux de travail peuvent utiliser les nouvelles classes Microsoft .NET Framework 4 de Windows PowerShell. Ils peuvent ainsi bénéficier de fonctionnalités comme la compatibilité et le déploiement d’applications, Managed Extensibility Framework, l’informatique parallèle, la mise en réseau, Windows Communication Foundation et Windows Workflow Foundation.

### <a name="support-for-windows-preinstallation-environment"></a>Prise en charge de l'environnement de préinstallation Windows

Windows PowerShell 3.0 est un composant facultatif de l'environnement de préinstallation Windows (WinPE) 4.0 pour Windows 8. Windows PE est un système d’exploitation minimal qui permet de démarrer un ordinateur sans système d’exploitation et qui le prépare en vue de l’installation de Windows. Windows PE peut être utilisé pour partitionner et formater des disques durs, copier des images de disque sur un ordinateur et initier l’installation de Windows à partir d’un partage réseau. Windows PowerShell 3.0 peut être utilisé sur Windows PE pour gérer des scénarios de déploiement, de diagnostic et de récupération.

### <a name="disconnected-sessions"></a>Sessions déconnectées

À compter de Windows PowerShell 3.0, les sessions persistantes gérées par l'utilisateur (« PSSessions ») que vous créez à l'aide de l'applet de commande New-PSSession sont enregistrées sur l'ordinateur distant. Elles ne dépendent donc plus de la session dans laquelle elles ont été créées.

Vous pouvez maintenant vous déconnecter d'une session sans interrompre les commandes en cours d'exécution dans la session. Vous pouvez fermer la session et arrêter votre ordinateur. Par la suite, vous pouvez vous reconnecter à la session à partir d'une session différente sur le même ordinateur ou un ordinateur différent.

Le paramètre **ComputerName** de l’applet de commande [Get-PSSession](https://technet.microsoft.com/library/b2b10531-d0df-4746-b877-e75c09955cb6) obtient maintenant toutes les sessions de l’utilisateur qui se connectent à l’ordinateur, même si elles ont été démarrées dans une session différente sur un autre ordinateur. Vous pouvez vous connecter aux sessions, obtenir les résultats des commandes, démarrer de nouvelles commandes, puis vous déconnecter de la session.

De nouvelles applets de commande ont été ajoutées pour prendre en charge la fonctionnalité Sessions déconnectées, notamment [Disconnect-PSSession](https://technet.microsoft.com/library/f8f95111-612f-4cba-9098-77904b0473d8), [Connect-PSSession](https://technet.microsoft.com/library/b803dd29-f208-4079-80d4-db04d778f060) et Receive-PSSession. Par ailleurs, de nouveaux paramètres ont été ajoutés aux applets de commande qui gèrent PSSessions, comme le paramètre **InDisconnectedSession** de l’applet de commande [Invoke-Command](https://technet.microsoft.com/library/906b4b41-7da8-4330-9363-e7164e5e6970).

La fonctionnalité Sessions déconnectées n'est prise en charge que si les ordinateurs situés à chaque extrémité de la connexion (le « client » à l'origine et le « serveur » à la fin) exécutent Windows PowerShell 3.0.

### <a name="robust-session-connectivity"></a>Connectivité fiable des sessions

Windows PowerShell 3.0 détecte les pertes inattendues de connectivité entre le client et le serveur. En cas de perte de connectivité, il tente de la rétablir et de reprendre l'exécution automatiquement. Si la connexion client-serveur ne peut pas être rétablie dans le délai imparti, l'utilisateur est notifié et la session est déconnectée. Lors de la tentative de reconnexion, Windows PowerShell fournit des commentaires en continu à l'utilisateur.

Si la session déconnectée a été démarrée à l'aide de l'applet de commande InvokeCommand, Windows PowerShell crée une tâche pour la session déconnectée pour faciliter la reconnexion et la reprise de l'exécution.

Ces fonctionnalités rendent l'expérience de communication à distance plus fiable et facilitent la récupération. Elles permettent aussi aux utilisateurs d'effectuer des tâches longues qui nécessitent des sessions fiables, comme des workflows.

### <a name="updatable-help-system"></a>Système d'aide actualisable

Vous pouvez à présent télécharger des fichiers d'aide mis à jour pour les applets de commande dans vos modules. L’applet de commande [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) identifie les fichiers d’aide les plus récents, les télécharge à partir d’Internet, les décompresse, les valide, puis les installe dans le répertoire spécifique à la langue du module.

Pour utiliser les fichiers d’aide mis à jour, tapez simplement `Get-Help`. Il n’est pas nécessaire de redémarrer Windows ou Windows PowerShell. Pour mettre à jour l’aide pour les modules dans le répertoire $pshome, démarrez Windows PowerShell avec l’option « Exécuter en tant qu’administrateur ».

Pour prendre en charge les utilisateurs qui n’ont pas accès à Internet et ceux qui se trouvent derrière des pare-feu, la nouvelle applet de commande [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) télécharge les fichiers d’aide vers un répertoire du système de fichiers, tel qu’un partage de fichiers. Les utilisateurs peuvent ensuite utiliser l’applet de commande [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) pour obtenir les fichiers d’aide à jour à partir du partage de fichiers.

Vous pouvez utiliser l’applet de commande [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) pour mettre à jour les fichiers d’aide de tous les modules ou de certains d’entre eux dans toutes les cultures d’interface utilisateur prises en charge. Vous pouvez même placer une commande [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) dans votre profil Windows PowerShell. Par défaut, Windows PowerShell télécharge les fichiers d’aide d’un module au maximum une fois par jour.

Les modules Windows 8 et Windows Server 2012 ne contiennent pas de fichiers d’aide. Pour télécharger les derniers fichiers d’aide, tapez `Update-Help`. Pour plus d’informations, tapez `Get-Help` (sans paramètre) ou consultez [about_Updatable_Help](https://technet.microsoft.com/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

Si les fichiers d’aide d’une applet de commande ne sont pas installés sur l’ordinateur, l’applet de commande [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) affiche maintenant une aide générée automatiquement. L’aide générée automatiquement contient la syntaxe de la commande et des instructions relatives à l’utilisation de l’applet de commande [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) pour télécharger les fichiers d’aide.

Tout auteur de module peut prendre en charge l'aide actualisable. Vous pouvez soit inclure des fichiers d'aide dans le module et utiliser l'aide actualisable pour les mettre à jour, soit omettre les fichiers d'aide et utiliser l'aide actualisable pour les installer. Pour plus d’informations sur la prise en charge de l’aide actualisable, voir [Prise en charge de l’aide actualisable](https://go.microsoft.com/FWLink/?LinkID=242129) dans MSDN.

### <a name="enhanced-online-help"></a>Aide en ligne améliorée

L’aide en ligne de Windows PowerShell est une ressource précieuse pour tous les utilisateurs, mais elle est particulièrement importante pour les utilisateurs qui choisissent de ne pas installer les fichiers d’aide mis à jour ou qui ne peuvent pas le faire.

Pour accéder à l’aide en ligne relative à une applet de commande Windows PowerShell, tapez :

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell ouvre la version en ligne de la rubrique d’aide dans votre navigateur Internet par défaut.

La fonctionnalité **Get-Help -Online** dans Windows PowerShell 3.0 est encore plus performante, car elle fonctionne même si les fichiers d’aide correspondant à l’applet de commande ne sont pas installés sur l’ordinateur. La fonctionnalité **Get-Help -Online** obtient l’URI de la rubrique d’aide en ligne à partir de la propriété HelpUri d’applets de commande et de fonctions avancées.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
https://go.microsoft.com/fwlink/?LinkID=223923
```

À compter de Windows PowerShell 3.0, les auteurs d’applets de commande en C# peuvent remplir la propriété **HelpUri** en créant un attribut **HelpUri** sur la classe de l’applet de commande. Les auteurs de fonctions avancées peuvent définir une propriété **HelpUri** sur l’attribut **CmdletBinding**. La valeur de la propriété **HelpUri** doit commencer par « http » ou « https ».

Il est aussi possible d’inclure une valeur **HelpUri** dans le premier lien associé d’un fichier d’aide d’applet de commande en XML ou la directive .Link de l’aide basée sur les commentaires dans une fonction.

Pour plus d’informations sur la prise en charge de l’aide en ligne, consultez [Prise en charge de l’aide en ligne](/powershell/scripting/developer/module/supporting-online-help) dans la documentation Microsoft.

### <a name="cim-integration"></a>Intégration de CIM

Windows PowerShell 3.0 prend en charge le modèle CIM (Common Information Model). Celui-ci fournit des définitions communes pour les informations de gestion des systèmes, réseaux, applications et services, ce qui permet l’échange d’informations de gestion entre systèmes hétérogènes. La prise en charge du modèle CIM dans Windows PowerShell 3.0 permet la création d’applets de commande Windows PowerShell basées sur des classes CIM nouvelles ou existantes, la création de commandes basées sur des fichiers XML de définition d’applets de commande, ainsi que la prise en charge de l’API .NET Framework CIM, des applets de commande de gestion CIM et des fournisseurs WMI 2.0.

### <a name="session-configuration-files"></a>Fichiers de configuration de session

À compter de Windows PowerShell 3.0, vous pouvez concevoir une configuration de session personnalisée à l’aide d’un fichier. Le nouveau fichier de configuration de session vous permet de déterminer l'environnement des sessions qui utilisent la configuration de session, y compris : les modules, scripts et fichiers de format chargés dans les sessions ; les applets de commande et éléments de langage que les utilisateurs peuvent utiliser ; les modules et scripts qu'ils peuvent s'exécuter ; ainsi que les variables qu'ils peuvent afficher.

Vous pouvez concevoir soit une session dans laquelle les utilisateurs peuvent uniquement exécuter les applets de commande d'un module particulier, soit une session dans laquelle les utilisateurs disposent à la fois d'un accès complet à tous les modules avec tous les éléments de langage et d'un accès aux scripts qui effectuent des tâches avancées.

Dans les versions précédentes de Windows PowerShell, le contrôle à ce niveau était uniquement disponible aux personnes capables d’écrire un programme en C# ou un script de démarrage complexe. À présent, tout membre du groupe Administrateurs sur l'ordinateur peut personnaliser une configuration de session à l'aide d'un fichier de configuration.

Pour créer un fichier de configuration de session, utilisez l’applet de commande [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866). Pour appliquer le fichier de configuration de session à une configuration de session, utilisez l’applet de commande [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) ou [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea).

Pour plus d’informations, voir [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-5.0) et [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866).

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Travaux planifiés et intégration du Planificateur de tâches

Vous pouvez maintenant planifier des travaux Windows PowerShell en arrière-plan, puis les gérer dans Windows PowerShell et dans le Planificateur de tâches.

Les travaux planifiés Windows PowerShell sont des tâches hybrides qui regroupent les avantages des travaux Windows PowerShell en arrière-plan et des tâches du Planificateur de tâches.

Au même titre que les travaux Windows PowerShell en arrière-plan, les travaux planifiés s’exécutent de manière asynchrone en arrière-plan. Vous pouvez gérer les instances de travaux planifiés terminés à l’aide d’applets de commande job, telles que [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) et [Get-Job](https://technet.microsoft.com/library/1352c534-7193-46ca-9ab1-0c5219a661ad).

À l'instar des tâches du Planificateur de tâches, vous pouvez exécuter des tâches planifiées selon une planification ponctuelle ou périodique, ou encore en réponse à une action ou un événement. Vous pouvez afficher et gérer les travaux planifiés dans le Planificateur de tâches, les activer et les désactiver selon les besoins, les exécuter ou les utiliser en tant que modèles, et définir les conditions dans lesquelles ils démarrent.

Les travaux planifiés sont également fournis avec un ensemble personnalisé d'applets de commande permettant de les gérer. Les applets de commande vous permettent non seulement de créer, modifier, gérer, désactiver et réactiver des tâches planifiées, mais aussi de créer des déclencheurs et définir les options des tâches planifiées.

Pour plus d’informations sur les travaux planifiés, voir [about_Scheduled_Jobs](https://technet.microsoft.com/library/3b546629-703c-4939-b44f-52dd567bce92).

### <a name="windows-powershell-language-enhancements"></a>Améliorations apportées au langage Windows PowerShell

Windows PowerShell 3.0 comprend de nombreuses fonctionnalités conçues non seulement pour simplifier le langage et le rendre plus convivial, mais aussi pour éviter les erreurs courantes. Parmi les améliorations apportées, citons l'énumération de propriétés, les propriétés count et length sur les objets scalaires, les nouveaux opérateurs de redirection, le modificateur de portée $Using, la variable automatique PSItem, le format de script flexible, les attributs des variables, la simplification des arguments d'attribut, les noms des commandes numériques, l'opérateur Stop-Parsing, la projection de tableau, de nouveaux opérateurs de bits, des dictionnaires ordonnés, le cast PSCustomObject et l'aide basée sur les commentaires.

### <a name="new-core-cmdlets"></a>Nouvelles applets de commande Core

De nouvelles applets de commande ont été ajoutées à l'installation de Windows PowerShell Core, notamment pour gérer les tâches planifiées, les sessions déconnectées, l'intégration CIM et le système d'aide actualisable.

|||
|-|-|
|Add-JobTrigger|New-JobTrigger|
|Connect-PSSession|New-PSSessionConfigurationFile|
|ConvertFrom-Json|New-PSTransportOption|
|ConvertTo-Json|New-PSWorkflowExecutionOption|
|Disable-JobTrigger|New-PSWorkflowSession|
|Disable-ScheduledJob|New-ScheduledJobOption|
|Disconnect-PSSession|New-WinEvent|
|Enable-JobTrigger|Receive-PSSession|
|Enable-ScheduledJob|Register-CimIndicationEvent|
|Get-CimAssociatedInstance|Register-ScheduledJob|
|Get-CimClass|Remove-CimInstance|
|Get-CimInstance|Remove-CimSession|
|Get-CimSession|Remove-TypeData|
|Get-ControlPanelItem|Rename-Computer|
|Get-IseSnippet|Resume-Job|
|Get-JobTrigger|Save-Help|
|Get-ScheduledJob|Set-CimInstance|
|Get-ScheduledJobOption|Set-JobTrigger|
|Get-TypeData|Set-ScheduledJob|
|Import-IseSnippet|Set-ScheduledJobOption|
|Invoke-AsWorkflow|Show-Command|
|Invoke-CimMethod|Show-ControlPanelItem|
|Invoke-RestMethod|Suspend-Job|
|Invoke-WebRequest|Test-PSSessionConfigurationFile|
|New-CimInstance|Unblock-File|
|New-CimSession|Unregister-ScheduledJob|
|New-CimSessionOption|Update-Help|
|New-IseSnippet||

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Améliorations apportées aux applets de commande et aux fournisseurs Core existants

Windows PowerShell 3.0 inclut de nouvelles fonctionnalités pour les applets de commande existantes, comme la syntaxe simplifiée, et de nouveaux paramètres pour les applets de commande suivantes : Computer, CSV, Get-ChildItem, Get-Command, Get-Content, Get-History, Measure-Object, Security, Select-Object, Select-String, Split-Path, Start-Process, Tee-Object, Test-Connection, Add-Member et WMI.

Les fournisseurs Windows PowerShell ont également bénéficié d'améliorations considérables. Citons notamment la prise en charge du fournisseur Certificate pour la gestion des certificats SSL (Secure Socket Layer) dans le cadre de l'hébergement web, la prise en charge des informations d'identification, les lecteurs réseau persistants et d'autres flux de données dans les lecteurs du système de fichiers.

### <a name="remote-module-import-and-discovery"></a>Importation et découverte des modules à distance

Windows PowerShell 3.0 étend aux ordinateurs distants les fonctionnalités de découverte de module, d’importation et de communication à distance de manière implicite. Les applets de commande Module obtiennent les modules sur les ordinateurs distants et les importent sur l'ordinateur distant ou local via la communication à distance Windows PowerShell. Grâce à la prise en charge des sessions CIM, vous pouvez utiliser CIM et WMI pour gérer des ordinateurs non Windows en important sur l'ordinateur local des commandes qui s'exécutent de manière implicite sur l'ordinateur distant.

Pour plus d’informations, consultez les rubriques d’aide relatives aux applets de commande [Get-Module](https://technet.microsoft.com/library/2cccd4c4-9a21-4c77-b691-984ee57242e1) et [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade).

### <a name="enhanced-tab-completion"></a>Saisie semi-automatique par tabulation améliorée

La saisie semi-automatique par le biais de la touche Tab dans la console Windows PowerShell permet maintenant de terminer les noms d’applets de commande, de paramètres, de valeurs de paramètre, d’énumérations, de types .NET Framework, d’objets COM, de répertoires cachés, et bien plus. La fonctionnalité de saisie semi-automatique par tabulation a été entièrement réécrite. Elle repose à présent sur un nouvel analyseur et une nouvelle arborescence de syntaxe abstraite qui prennent en charge davantage de scénarios, y compris les arborescences d'analyse en mémoire et la saisie semi-automatique par tabulation en milieu de ligne.

### <a name="module-auto-loading"></a>Chargement automatique des modules

L’applet de commande [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) obtient maintenant l’ensemble des applets de commande et des fonctions de tous les modules installés sur l’ordinateur, même si un module n’est pas importé dans la session active.

Quand vous obtenez l'applet de commande dont vous avez besoin, vous pouvez l'utiliser immédiatement sans importer de modules. Les modules Windows PowerShell sont maintenant importés automatiquement quand vous utilisez une applet de commande dans le module. Vous n'avez plus besoin de rechercher le module et de l'importer pour utiliser ses applets de commande.

Pour déclencher l’importation automatique des modules, utilisez l’applet de commande dans une commande, puis exécutez **Get-Command** pour une applet de commande sans caractères génériques ou [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) pour une applet de commande avec caractères génériques.

Pour activer, désactiver et configurer l’importation automatique de modules, utilisez la variable de préférence **$PSModuleAutoLoadingPreference**.

Pour plus d’informations, voir [about_Modules](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-5.0), [about_Preference_Variables [v4]](https://technet.microsoft.com/library/31344314-be29-4286-b039-afa5460cbe8b) et les rubriques d’aide relatives aux applets de commande [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) et [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade).

### <a name="module-experience-improvements"></a>Améliorations apportées aux fonctionnalités des modules

À partir de Windows PowerShell 3.0, les modules prennent en charge des fonctionnalités avancées, notamment les nouvelles fonctionnalités suivantes.

1. Journalisation des modules individuels (LogPipelineExecutionDetails) et nouveau paramètre de stratégie de groupe « Activer l'enregistrement des modules ».
2. Objets de module étendus qui exposent les valeurs à partir du manifeste de module.
3. Nouvelle propriété **ExportedCommands** des modules, y compris les modules imbriqués, qui combine des commandes de tous types.
4. Détection améliorée des modules disponibles (non importés), offrant notamment la possibilité d’utiliser les paramètres **Path** et **ListAvailable** dans la même commande
5. Nouvelle clé **DefaultCommandPrefix** dans les manifestes de module, qui évite les conflits de nom sans modifier le code du module.
6. Amélioration des spécifications des modules, y compris les modules requis complets avec version et GUID et l'importation automatique des modules requis.
7. Opération simplifiée et silencieuse de l’applet de commande [New-ModuleManifest](https://technet.microsoft.com/library/512adced-f42f-4e88-ba7c-834fc9e5d047).
8. Nouveau paramètre **Module** pour #Requires
9. Amélioration de l’applet de commande [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) avec les paramètres **MinimumVersion** et **RequiredVersion**.

### <a name="simplified-command-discovery"></a>Découverte des commandes simplifiée

Vous n'avez plus besoin d'importer tous les modules pour découvrir les commandes disponibles dans votre session. Dans Windows PowerShell 3.0, l’applet de commande [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) obtient toutes les commandes de tous les modules installés. Si vous utilisez une commande, le module qui exporte la commande est automatiquement importé dans votre session.

La nouvelle applet de commande [Show-Command](https://technet.microsoft.com/library/65bba50b-91a8-49d5-80a2-a30fc684ba41) est conçue spécialement pour les débutants. Vous pouvez rechercher des commandes dans une fenêtre. Vous pouvez afficher toutes les commandes ou les filtrer par module, importer un module en cliquant sur un bouton, utiliser des zones de texte et des listes déroulantes pour construire une commande valide, puis copier ou exécuter la commande sans jamais quitter la fenêtre.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>Prise en charge améliorée de la journalisation, du diagnostic et de la stratégie de groupe

Windows PowerShell 3.0 améliore la prise en charge de la journalisation et du traçage pour les commandes et les modules. Il prend également en charge les journaux de suivi d’événements pour Windows (ETW), une propriété **LogPipelineExecutionDetails** modifiable des modules, ainsi que le paramètre de stratégie de groupe « Activer l’enregistrement des modules ». Vous pouvez maintenant obtenir les valeurs de paramètres à partir des détails du journal en affichant les propriétés du journal.

### <a name="formatting-and-output-improvements"></a>Améliorations apportées à la mise en forme et à la sortie

Les améliorations apportées à la mise en forme et à la sortie permettent d’accroître la productivité de tous les utilisateurs de Windows PowerShell. Parmi ces améliorations, citons la redirection de la sortie de tous les flux, une applet de commande Update-Type améliorée qui ajoute dynamiquement des types sans les fichiers Format.ps1xml, le retour automatique à la ligne de la sortie, les propriétés de mise en forme par défaut des objets personnalisés, le type **PSCustomObject**, la mise en forme améliorée des objets WMI et des objets hétérogènes, ainsi que la prise en charge de la découverte des surcharges de méthode.

### <a name="enhanced-console-host-experience"></a>Améliorations apportées aux fonctionnalités de l'hôte de console

Le programme hôte de la console Windows PowerShell comprend de nouvelles fonctionnalités disponibles dans Windows PowerShell 3.0, dont un thread unique cloisonné par défaut. La nouvelle option « Exécuter avec PowerShell » dans l'Explorateur de fichiers vous permet d'exécuter des scripts dans une session non restreinte d'un simple clic droit. La nouvelle logique de lancement de l'hôte de la console démarre Windows PowerShell plus rapidement, et de nouvelles polices vous permettent de personnaliser l'expérience dans la fenêtre de la console.

Pour plus d’informations, voir [about_Run_With_PowerShell](https://technet.microsoft.com/library/c9d9ca5f-eff9-4409-be9d-e43b5b4087eb).

### <a name="new-cmdlet-and-hosting-apis"></a>Nouvelles API Cmdlet et Hosting

Les nouvelles API Cmdlet et Hosting incluent des API d'arborescence de syntaxe avancée publiques, ainsi que des API pour la pagination des pipelines, les pipelines imbriqués, la saisie semi-automatique par tabulation des pools d'instance d'exécution, Windows RT, l'attribut d'applet de commande Obsolete et les propriétés Verb et Noun de l'objet FunctionInfo.

### <a name="performance-improvements"></a>Améliorations des performances

Les gains importants en termes de performances dans Windows PowerShell proviennent du nouvel analyseur de langage, qui repose sur Dynamic Runtime Language (DLR) dans .NET Framework 4., mais aussi de la compilation des scripts au moment de l’exécution, des améliorations en matière de fiabilité du moteur et des modifications apportées à l’algorithme de l’applet de commande [Get-ChildItem](https://technet.microsoft.com/library/75cf79bb-4db6-4a67-8c36-3d20754e2190). Tout cela contribue à l’amélioration des performances de Windows PowerShell, en particulier lors de la recherche sur des partages réseau.

### <a name="runas-and-shared-host-support"></a>Prise en charge de RunAs et de SharedHost

Windows PowerShell 3.0 prend en charge les fonctionnalités RunAs et SharedHost.

La fonctionnalité *RunAs*, conçue pour Windows PowerShell Workflow, permet aux utilisateurs d’une configuration de session de créer des sessions qui s’exécutent avec l’autorisation d’un compte d’utilisateur partagé. Elle permet aux utilisateurs moins privilégiés d'exécuter des commandes et des scripts particuliers avec des autorisations d'administrateur, ce qui évite l'ajout d'utilisateurs expérimentés au groupe Administrateurs.

Grâce à la fonctionnalité **SharedHost**, plusieurs utilisateurs sur différents ordinateurs peuvent se connecter simultanément à une session de workflow et surveiller sa progression. Les utilisateurs peuvent démarrer un workflow sur un ordinateur, puis se connecter à la session de workflow sur un autre ordinateur sans déconnecter la session de l'ordinateur d'origine. Les utilisateurs doivent avoir les mêmes autorisations et utiliser la même configuration de session. Pour plus d'informations, consultez « Exécution d'un workflow Windows PowerShell » dans Prise en main de Windows PowerShell Workflow.

### <a name="special-character-handling-improvements"></a>Améliorations apportées à la gestion des caractères spéciaux

Pour améliorer l’interprétation et la gestion des caractères spéciaux dans Windows PowerShell 3.0, le paramètre **LiteralPath**, qui gère les caractères spéciaux dans les chemins d’accès, est valide sur pratiquement toutes les applets de commande possédant un paramètre **Path**, dont les nouvelles applets de commande [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) et [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa). L’analyseur inclut également une logique spéciale qui améliore la gestion de l’accent grave (\`) et des crochets dans les chemins et les noms de fichiers.

## <a name="see-also"></a>Voir aussi

- [about_Windows_PowerShell_5.0](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116)
