---
title: Nouveautés de PowerShell 7.1
description: Nouvelles fonctionnalités et modifications de PowerShell 7.1
ms.date: 11/11/2020
ms.openlocfilehash: 5596d3ca69f5d8ea47f01ff0915e6fa33c1c463f
ms.sourcegitcommit: fb1a4bc4b249afd3513663de2e1ba3025d63467e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2020
ms.locfileid: "94625718"
---
# <a name="whats-new-in-powershell-71"></a>Nouveautés de PowerShell 7.1

PowerShell 7.1 est une édition de multiplateforme open source (Windows, macOS et Linux) de PowerShell, conçue pour gérer des environnements hétérogènes et le cloud hybride.

En s'appuyant sur les bases établies dans PowerShell 7.0, nos efforts se sont concentrés sur les questions soulevées par la communauté et comprennent un certain nombre d'améliorations et de corrections. Nous nous engageons à faire en sorte que PowerShell reste une plateforme stable et performante.

PowerShell 7.1 inclut également PSReadLine 2.1.0. Cette version comprend IntelliSense prédictif. Pour plus d’informations sur la fonctionnalité IntelliSense prédictive, consultez l’[annonce](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/) dans le blog PowerShell.

## <a name="where-can-i-install-powershell"></a>Où puis-je installer PowerShell ?

<!-- TODO: Update list of OS below - make sure this is consistent across all docs -->

PowerShell 7.1 prend actuellement en charge les systèmes d’exploitation suivants sur x64, notamment :

- Windows 8.1/10 (y compris ARM64)
- Windows Server 2012 R2, 2016, 2019 et canal semi-annuel (SAC)
- Ubuntu 16.04/18.04/20.04 (y compris ARM64)
- Ubuntu 19.10 (via Snap Package)
- Debian 9/10
- CentOS et RHEL 7/8
- Fedora 32
- Alpine 3.11+ (y compris ARM64)
- macOS 10.13+

Nous proposons également un support de la communauté pour :

- Arch Linux
- Raspbian Linux
- Kali Linux

Pour plus d’informations à jour sur les systèmes d’exploitation pris en charge et le cycle de vie de support, consultez le [cycle de vie du support PowerShell](/powershell/scripting/powershell-support-lifecycle)

PowerShell 7.1 a été publié sur le Microsoft Store. Vous trouverez la version PowerShell sur le site Web du [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) ou dans l’application Store de Windows.

Avantages du package Microsoft Store :

- Mises à jour automatiques intégrées à Windows 10
- S’intègre à d’autres mécanismes de distribution de logiciels comme Intune et SCCM

> [!NOTE]
> Les paramètres de configuration au niveau du système, stockés dans `$PSHOME`, ne peuvent pas être modifiés. Cela comprend la configuration WSMAN. Cette stratégie empêche les sessions à distance de se connecter aux installations basées sur le magasin de PowerShell. Les configurations au niveau de l’utilisateur et l’accès à distance SSH sont pris en charge.

Consultez les instructions d’installation pour votre système d’exploitation par défaut :

- [Windows](/powershell/scripting/install/installing-powershell-core-on-windows)
- [macOS](/powershell/scripting/install/installing-powershell-core-on-macos)
- [Linux](/powershell/scripting/install/installing-powershell-core-on-linux)

En outre, PowerShell 7.1 prend en charge les versions ARM32 et ARM64 de Debian, Ubuntu et ARM64 Alpine Linux.

Bien qu’ils ne soit pas officiellement pris en charge, la communauté a également fourni des packages pour [Arch](https://aur.archlinux.org/packages/powershell/) et Kali Linux.

> [!NOTE]
> Debian 10+, CentOS 8+, Ubuntu 20.04, Alpine et Arm ne prennent actuellement pas en charge la communication à distance WinRM. Pour plus d’informations sur la configuration de la communication à distance basée sur SSH, consultez [Communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## <a name="running-powershell-71"></a>Exécution de PowerShell 7.1

PowerShell 7.1 s’installe dans un nouveau répertoire et s’exécute côte à côte avec Windows PowerShell 5.1.
PowerShell 7.1 est une mise à niveau sur place qui remplace PowerShell 6.x. ou PowerShell 7.0.

- PowerShell 7.1 est installé sur `%programfiles%\PowerShell\7`
- Le dossier `%programfiles%\PowerShell\7` est ajouté à `$env:PATH`

Les packages d’installation PowerShell 7.1 mettent à niveau les versions précédentes de PowerShell Core 6.x :

- PowerShell Core 6.x sur Windows : `%programfiles%\PowerShell\6` est remplacé par `%programfiles%\PowerShell\7`
- Linux : `/opt/microsoft/powershell/6` est remplacée par `/opt/microsoft/powershell/7`
- macOS : `/usr/local/microsoft/powershell/6` est remplacée par `/usr/local/microsoft/powershell/7`

> [!NOTE]
> Dans Windows PowerShell, l’exécutable permettant de lancer PowerShell est nommé `powershell.exe`. Dans la version 6 et les versions ultérieures, l’exécutable est modifié pour prendre en charge l’exécution côte à côte. Le nouvel exécutable permettant de lancer PowerShell 7.1 est `pwsh.exe`. Les builds préliminaires sont conservées en tant que `pwsh-preview` au lieu de `pwsh` sous le répertoire 7-préversion.

## <a name="breaking-changes-and-improvements"></a>Dernières modifications et améliorations

Pour obtenir les informations les plus récentes sur les modifications et les améliorations, consultez le [journal des modifications](https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG) dans le référentiel GitHub.

### <a name="breaking-changes"></a>Dernières modifications

<!-- TODO: Add descriptions for each breaking change - this might need to be a separate article that we link to -->

- Corriger `$?` pour ne pas être `$false` lorsque la commande native écrit dans `stderr` (#13395)
- Renommer `-FromUnixTime` en `-UnixTimeSeconds` sur `Get-Date` pour autoriser l’entrée de temps UNIX (#13084) (merci @aetos382 !)
- Configurer `$ErrorActionPreference` pour ne pas affecter la sortie `stderr` des commandes natives (#13361)
- Autoriser le paramètre nommé explicitement spécifié à remplacer le même paramètre dans la projection de la table de hachage (#13162)
- Rendre le paramètre de commutateur `-Qualifier` non positionnel pour `Split-Path` (#12960) (merci @yecril71pl !)
- Résoudre le répertoire de travail comme chemin d’accès littéral pour `Start-Process` lorsqu’il n’est pas spécifié (#11946) (merci @NoMoreFood !)
- Modifier le paramètre `-OutFile` dans les applets de commande Web pour qu’il fonctionne comme `-LiteralPath` (#11701) (merci @iSazonov !)
- Corriger la liaison de paramètre de chaîne pour les littéraux numériques `BigInteger` (#11634) (merci @vexx32 !)
- Sur Windows, `Start-Process` crée un environnement de processus avec toutes les variables d’environnement à partir de la session active, et `-UseNewEnvironment` crée un nouvel environnement de processus par défaut (#10830) (merci @iSazonov !)
- Ne pas encapsuler le résultat retourné à `PSObject` lors de la conversion d’un ScriptBlock en délégué (#10619)
- Utiliser la conversion de chaîne de culture invariante pour l’opérateur `-replace` (#10954) (merci @iSazonov !)

### <a name="experimental-features"></a>Fonctionnalités expérimentales

Pour plus d’informations sur les fonctionnalités expérimentales, consultez [Utilisation des fonctionnalités expérimentales](../learn/experimental-features.md).

- Retirer la fonctionnalité `PSNullConditionalOperators` des fonctionnalités expérimentales (#13529)
- Retirer la fonctionnalité `PSUnixFileStat` des fonctionnalités expérimentales
- Ajouter le paramètre `-Runspace` à toutes les applets de commande `*-PSBreakpoint` (#10492) (merci @KirkMunro !)
- Ajouter `PSNativePSPathResolution` pour prendre en charge le passage de `PSPath` à des commandes natives (#12386)
- Utiliser la conversion de chaîne de culture invariante pour l’opérateur `-replace` (#10954) (merci @iSazonov !)
- Ajouter `PSSubsystemPluginModel` pour prendre en charge de futurs plug-ins IntelliSense prédictif

### <a name="general-cmdlet-updates-and-fixes"></a>Mises à jour et correctifs d’applets de commande générales

- Émettre un avertissement si `ConvertTo-Json` dépasse la valeur `-Depth` (#13692)
- Résoudre le cas où un message d’exception contient uniquement ``"`n"`` sur Windows (#13684)
- Reconnaître `CONOUT$` et `CONIN$` en tant que noms d’appareils réservés (#13508) (merci @davidreis97 !)
- Corriger `ConciseView` pour la fonction avancée interactive lors de l’écriture d’une erreur (#13623)
- Ajouter la prise en charge de `TLS` 1.3 dans les applets de commande Web (#13409) (merci @iSazonov !)
- Ajouter un contrôle de valeur null pour `args` dans `CommandLineParser` (#13451) (merci @iSazonov !)
- Traiter les points de d’analyse pour les applications du Microsoft Store (#13481) (merci @iSazonov !)
- Utiliser le champ si la propriété n’existe pas pour `ObRoot` lors de l’utilisation de PowerShell Direct dans un conteneur (#13375) (merci @hemisphera !)
- Supprimer les avertissements `UTF-7` obsolètes (#13484)
- Éviter les énumérations multiples d’une instance de `IEnumerable<Expression>` dans `Compiler.cs` (#13491)
- Modifier `Add-Type -OutputType` pour ne pas prendre en charge `ConsoleApplication` et `WindowsApplication` (#13440)
- Créer des avertissements quand `UTF-7` est spécifié en tant qu’encodage (#13430)
- Corriger le message d’erreur de la nouvelle cible de lien symbolique (#13085) (merci @yecril71pl !)
- Définir le paramètre `args` pour ne pas accepter les valeurs nulles dans les API `ConsoleHost` publiques (#13429)
- Ajouter la suppression manquante pour `CancellationTokenSource` (#13420) (merci @Youssef1313 !)
- Corriger l’erreur où `Get-Help` ne s’affiche pas correctement si le paramètre prend en charge les caractères génériques (#13353) (merci @ThomasNieto !)
- Mettre à jour l’aide `pwsh` pour le paramètre de `-InputFormat` (#13355) (merci @sethvs !)
- Déclarer la licence MIT pour les fichiers copiés à partir de Roslyn (#13305) (merci @xtqqczze !)
- Améliorer les comportements de conversion `BigInteger` (#12629) (merci @vexx32 !)
- Corriger le comportement de `Get-Acl -LiteralPath "HKLM:Software\Classes\*"` (#13107) (merci @Shriram0908 !)
- Ajouter la méthode `DefaultVisit` à l’interface et à la classe du visiteur (#13258)
- Corriger le commutateur de raccourci (STA) conflictuel `-s` pour `pwsh` (#13262) (merci @iSazonov !)
- Modifier `Read-Host -MaskInput` pour utiliser le chemin d’accès `SecureString` existant, mais retourner en texte brut (#13256)
- La suppression de `ComEnumerator` en tant qu’objets COM à l’aide de `IEnumerator` est désormais prise en charge dans .NET 5.0 (#13259)
- Utiliser le chemin d’accès personnel temporaire au démarrage de l’instance lorsque la variable d’environnement « HOME » n’est pas définie (#13239)
- Corriger `Invoke-Command` pour détecter l’appel récursif de la même entrée d’historique (#13197)
- Modifier l’exécutable `pwsh` `-inputformat` du préfixe de commutateur `-in` en `-inp` pour résoudre le conflit avec `-interactive` (#13205) (merci @iSazonov !)
- Gérer le chemin du système de fichiers WSL lors de l’analyse de la zone de sécurité d’un fichier (#13120)
- Rendre les autres commutateurs obligatoires dans `Split-Path` (#13150) (merci @kvprasoon !)
- Nouvelle icône Fluent Design pour PowerShell 7 (#13100) (merci @sarthakmalik !)
- Corriger `Move-Item` pour prendre en charge les déplacements entre montages sur UNIX (#13044)
- Corriger `NullReferenceException` dans `CommandSearcher.GetNextCmdlet` (#12659) (merci @powercode !)
- Empêcher `NullReferenceException` dans les applets de commande d’ordinateur UNIX avec des crochets de test actifs (#12651) (merci @vexx32 !)
- Résoudre le problème dans `Select-Object` où les membres `Hashtable` (par exemple `Keys`) ne peuvent pas être utilisés avec `-Property` ou `-ExpandProperty` (#11097) (merci @vexx32 !)
- Corriger le commutateur de raccourci conflictuel `-w` pour pwsh (#12945)
- Renommer le fichier de ressources `CimCmdlet` (#12955) (merci @iSazonov !)
- Supprimer l’utilisation de `Test-Path` dans `ConciseView` (#12778)
- Définir la clause de condition d’instruction du commutateur `default` comme mot clé (#10487) (merci @msftrncs !)
- Ajouter le paramètre `SchemaFile` à l’applet de commande `Test-Json` (#11934) (merci @beatcracker !)
- Rétablir les paramètres du fournisseur de certificats (#10622) (merci @iSazonov !)
- Corriger `New-Item` pour créer un lien symbolique vers la cible du chemin d’accès relatif (#12797) (merci @iSazonov !)
- Ajouter la propriété `CommandLine` au processus (#12288) (merci @iSazonov !)
- Ajouter le paramètre `-MaskInput` à `Read-Host` (#10908) (merci @davinci26 !)
- Modifier `CimCmdlets` pour utiliser `AliasAttribute` (#12617) (merci @thlac !)
- Corriger l’index incorrect de la chaîne de format dans ParameterBinderBase (#12630) (merci @powercode !)
- Copier la propriété `CommandInfo` dans `Command.Clone()` (#12301) (merci @TylerLeonhardt !)
- Appliquer `-IncludeEqual` dans `Compare-Object` lorsque `-ExcludeDifferent` est spécifié (#12317) (merci @davidseibel !)
- Modifier `Get-FileHash` pour fermer les descripteurs de fichiers avant d’écrire la sortie (#12474) (merci @HumanEquivalentUnit !)
- Corriger le message d’exception incohérent dans l’opérateur `-replace` (#12388) (merci @jackdcasey !)
- Corriger le chargement du module `WinCompat` pour traiter les modules PowerShell 7 avec une priorité plus élevée (#12269)
- Implémenter la réutilisation de l’instance d’exécution `ForEach-Object -Parallel` (#12122)
- Corriger `Get-Service` pour ne pas modifier la collection pendant l’énumération (#11851) (merci @NextTurn !)
- Nettoyer le canal nommé IPC à la sortie PowerShell (#12187)
- Corriger l’expression régulière de détection `<img />` dans les applets de commande Web (#12099) (merci @vexx32 !)
- Autoriser les littéraux hexadécimaux signés plus courts avec les suffixes de type appropriés (#11844) (merci @vexx32 !)
- Mettre à jour le comportement du paramètre `UseNewEnvironment` de l’applet de commande `Start-Process` sur Windows (#10830) (merci @iSazonov !)
- Ajouter le commutateur `-Shuffle` à la commande `Get-Random` (#11093) (merci @eugenesmlv !)
- Rendre `GetWindowsPowerShellModulePath` compatible avec plusieurs installations PS (#12280)
- Corriger `Start-Job` pour fonctionner sur les systèmes sur lesquels Windows PowerShell n’est pas inscrit comme interpréteur de commandes par défaut (#12296)
- La spécification d’un alias et de `-Syntax` pour `Get-Command` retourne la syntaxe de commandes avec alias (#10784) (merci @ChrisLGardner !)
- Faire fonctionner les applets de commande CSV lorsque vous utilisez `-AsNeeded` et qu’une ligne est incomplète (#12281) (merci @iSazonov !)
- Dans les appels locaux, plus besoin de `-PowerShellVersion 5.1` pour `Get-FormatData` afin d’afficher voir toutes les données de format. (#11270) (merci @mklement0 !)
- Ajout de la prise en charge des `UTF-32` Big endian (#11947) (merci @NoMoreFood!)
- Supprimer un risque de concurrence qui entraîne la suppression de l’objet PowerShell dans `ForEach-Object -Parallel` (#12227)
- Ajouter `-FromUnixTime` à `Get-Date` pour autoriser l’entrée de temps UNIX (#12179) (merci @jackdcasey !)
- Modifier les couleurs de premier plan et d’arrière-plan par défaut de la progression pour offrir un meilleur contraste (#11455) (merci @rkeithhill !)
- Corriger `foreach -parallel` lorsque le lecteur actuel n’est pas disponible (#12197)
- Ne pas encapsuler le résultat retourné à `PSObject` lors de la conversion de `ScriptBlock` en `delegate` (#10619)
- Ne pas écrire les erreurs de résolution DNS sur `Test-Connection -Quiet` (#12204) (merci @vexx32 !)
- Utiliser des threads dédiés pour lire les flux de sortie et d’erreur redirigés à partir du processus enfant pour les travaux hors processus (#11713)
- Corriger un problème d’ordre de préférence d’opérateur dans le code Binder (#12075) (merci @DamirAinullin!)
- Corriger `NullReferenceException` lors de la liaison de paramètres communs de type `ActionPreference` (#12124)
- Corriger la mise en forme par défaut des objets `MatchInfo` désérialisés (#11728) (merci @iSazonov !)
- Utiliser des flux asynchrones dans `Invoke-RestMethod` (#11095) (merci @iSazonov !)
- Résoudre la détection UTF-8 dans `Get-Content -Tail` (#11899) (merci @NoMoreFood !)
- Gérer `IOException` dans `Get-FileHash` (#11944) (merci @iSazonov !)
- Remplacer `PowerShell Core` par `PowerShell` dans une chaîne de ressource (#11928) (merci @alexandair !)
- Rétablir `MainWindowTitle` dans `PSHostProcessInfo` (#11885) (merci @iSazonov !)
- Diverses mises à jour mineures pour la compatibilité Windows (#11980)
- Corriger `ConciseView` pour fractionner `PositionMessage` avec `[Environment]::NewLine` (#12010)
- Supprimer la restriction du tronçon réseau pour les sessions interactives (#11920)
- Corriger `NullReferenceException` dans `SuspendStoppingPipeline()` et `RestoreStoppingPipeline()` (#11870) (merci @iSazonov !)
- Générer un GUID pour `FormatViewDefinition` `InstanceId` s’il n’est pas fourni (#11896)
- Corriger `ConciseView` où le message d’erreur est plus large que la fenêtre et n’a pas d’espace blanc (#11880)
- Autoriser l’échange de clé à distance `CAPI-compatible` multiplateforme (#11185) (merci @silijon !)
- Corriger le message d’erreur (#11862) (merci @NextTurn !)
- Corriger `ConciseView` pour gérer le cas où il n’existe aucune console pour obtenir la largeur (#11784)
- Mettre à jour `CmsCommands` pour utiliser le magasin ou fournisseur de certificat (#11643) (merci @mikeTWC1984 !)
- Autoriser `pwsh` à fonctionner sur les systèmes Windows où `mpr.dll` et STA ne sont pas disponibles (#11748)
- Refactoriser et implémenter `Restart-Computer` pour `Un*x` et macOS (#11319)
- Ajouter une implémentation de `Stop-Computer` pour Linux et macOS (#11151)
- Corriger la fonction `help` pour vérifier si `less` est disponible avant utilisation (#11737)
- Mettre à jour `PSPath` dans `certificate_format_ps1.xml` (#11603) (merci @xtqqczze !)
- Modifier l’expression régulière pour qu’elle corresponde aux types de relation sans guillemets dans l’en-tête du lien (#11711) (merci @Marusyk !)
- Corriger le message d’erreur lors de la suppression du lien symbolique (#11331)
- Ajouter un type `Selected.*` personnalisé à `PSCustomObject` dans `Select-Object` une seule fois (#11548) (merci @iSazonov !)
- Ajouter `-AsUTC` à l’applet de commande `Get-Date` (#11611)
- Corriger le comportement de regroupement avec des valeurs booléennes dans `Format-Hex` (#11587) (merci @vexx32 !)
- Configurer `Test-Connection` pour toujours utiliser le contexte de synchronisation par défaut pour l’envoi de requêtes ping (#11517)
- Corriger les messages d’erreur de démarrage (#11473) (merci @iSazonov !)
- Ignorer les en-têtes avec des valeurs Null dans les applets de commande Web (#11424) (merci @iSazonov !)
- Ajouter à nouveau la vérification de la suppression du travail `Invoke-Command`. (#11388)
- Rétablir le message « Mettre à jour le formateur pour ne pas écrire de nouvelles lignes si le contenu est vide (#11193) » (#11342) (merci @iSazonov !)
- Autoriser `CompleteInput` à retourner des résultats à partir de `ArgumentCompleter` quand `AST` ou un script inclut une définition de fonction correspondante (#10574) (merci @M1kep !)
- Mettre à jour le formateur pour ne pas écrire de nouvelles lignes si le contenu est vide (#11193)

<!-- TODO: add more general contributor thank you listing -->
