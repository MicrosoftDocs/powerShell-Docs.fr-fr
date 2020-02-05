---
title: Nouveautés de PowerShell Core 6.2
description: Nouvelles fonctionnalités et modifications de PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 98dd97b064e11509bf97e68e0a312e6b34b5d2bc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995476"
---
# <a name="whats-new-in-powershell-core-62"></a>Nouveautés de PowerShell Core 6.2

La version PowerShell Core 6.2 offre de meilleures performances, des correctifs de bogues, des applets de commande plus compactes et un meilleur langage, garantissant plus de qualité. Pour voir une liste complète des améliorations, consultez nos [journaux de modifications](https://github.com/PowerShell/PowerShell/releases) détaillés sur GitHub.

## <a name="experimental-features"></a>Fonctionnalités expérimentales

Les [fonctionnalités expérimentales][] étaient auparavant prises en charge. La version 6.2 propose quatre fonctionnalités expérimentales à tester. Veuillez nous faire part de vos commentaires pour nous permettre apporter des améliorations et décider si la fonctionnalité mérite d’être implémentée.

Utilisez `Get-ExperimentalFeature` pour obtenir la liste des fonctionnalités expérimentales disponibles. Vous pouvez activer ou désactiver ces fonctionnalités avec `Enable-ExperimentalFeature` et `Disable-ExperimentalFeature`.

### <a name="command-not-found-suggestions"></a>Suggestions en cas de commande introuvable

Cette fonctionnalité utilise la correspondance approximative afin de rechercher des suggestions pour les commandes ou applets de commande que vous avez peut-être mal saisies.

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>Exemple

Dans cet exemple, le nom de l’applet de commande mal orthographié est mis en correspondance avec plusieurs suggestions, par ordre de probabilité.

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a>Traitement par lot de la communication à distance implicite

Lorsque vous utilisez la [communication à distance implicite](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) dans un pipeline, PowerShell traite chaque commande du pipeline de manière indépendante. Les objets sont sérialisés et `de-serialized` à plusieurs reprises entre le client et le système distant lors de l’exécution du pipeline.

Avec cette fonctionnalité, PowerShell analyse le pipeline afin de déterminer si la commande peut s’exécuter sans risque et existe sur le système cible. Si la valeur est true, PowerShell exécute à distance l’ensemble du pipeline, puis sérialise et `de-serializes` les résultats retournés au client.

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

Un test de `Get-Process | Sort-Object` en conditions réelles via localhost réduit le délai de 10-15 secondes à 20-30 **millisecondes**. La fonctionnalité doit uniquement être activée sur le client. Aucune modification n’est nécessaire sur le serveur.

### <a name="temp-drive"></a>Lecteur temporaire

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

Si vous utilisez PowerShell Core sur différents systèmes d’exploitation, vous découvrirez que la variable d’environnement pour rechercher le répertoire temporaire est différente sur Windows, macOS et Linux ! Avec cette fonctionnalité, vous obtenez un [PSDrive][] appelé `Temp:` et automatiquement mappé au dossier temporaire du système d’exploitation que vous utilisez.

#### <a name="example"></a>Exemple

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

N’oubliez pas que les commandes de fichier natives (telles que `ls` sur Linux) ne reconnaissent pas les PSDrives et n’affichent pas le lecteur `Temp:`.

### <a name="abbreviation-expansion"></a>Expansion des abréviations

Les applets de commande PowerShell sont supposées afficher des noms descriptifs. Cela entraîne des noms longs plus difficiles à saisir. Cette fonctionnalité vous permet de saisir simplement les caractères majuscules de l’applet de commande et d’utiliser la saisie semi-automatique via la touche Tab pour rechercher une correspondance.

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>Exemple

```powershell
PS> i-arsavsf
```

Si vous appuyez sur la touche Tab et que le module Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) est installé, la saisie semi-automatique sera appliquée à :

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> Cette fonctionnalité est destinée à être utilisée de manière interactive. Les formes abrégées des applets de commande ne peuvent pas être exécutées.
> Cette fonctionnalité ne remplace pas les alias.

## <a name="breaking-changes"></a>Dernières modifications

- Correction du comportement de `-NoEnumerate` dans `Write-Output` pour le rendre cohérent avec Windows PowerShell. (#9069)
- Modification du résultat `Join-String -InputObject 1,2,3` pour le rendre égal à `1,2,3 | Join-String` (#8611) (merci @sethvs !)
- Ajout de `-Stable` à `Sort-Object` et aux tests associés (#7862) (merci @KirkMunro !)
- Amélioration de l’applet de commande `Start-Sleep` pour accepter les fractions de seconde (#8537) (merci @Prototyyppi !)
- Modification de la table de hachage pour rendre OrdinalIgnoreCase `case-insensitive` dans toutes les cultures (#8566)
- Correction de **LiteralPath** dans `Import-Csv` pour la liaison au résultat `Get-ChildItem` (#8277) (merci @iSazonov !)
- N’ignore plus une colonne sans nom si le délimiteur de guillemet double est utilisé dans `Import-Csv` (#7899) (merci @Topping !)
- `Get-ExperimentalFeature` ne comporte plus de commutateur `-ListAvailable` (#8318)
- Le paramètre de débogage définit maintenant `$DebugPreference` sur **Continue** au lieu de **Inquire** (#8195) (merci @KirkMunro !)
- Honorer `-OutputFormat` si spécifié dans une commande non interactive, redirigée, encodée utilisée avec pwsh (#8115)
- Chargement de l’assembly à partir du chemin de base du module avant d’essayer de le charger à partir du GAC (#8073)
- Suppression du tilde des packages en version préliminaire Linux (#8244)
- Déplacement du traitement de `-WorkingDirectory` avant le traitement des profils (#8079)
- Pas d’ajout de la variable d’environnement `PATHEXT` sur Unix (#7697) (merci @iSazonov !)

## <a name="known-issues"></a>Problèmes connus

- La communication à distance sur les plateformes Windows IOT ARM entraîne un problème de chargement des modules. Voir (#8053)

## <a name="general-updates-and-fixes"></a>Mises à jour et correctifs généraux

- Activation de la saisie semi-automatique via la touche Tab pour les fichiers et dossiers sur le système de fichiers respectant la casse (#8128)
- Publication de PSVersionInfo.PSVersion et PSVersionInfo.PSEdition (#8054) (merci @KirkMunro !)
- Ajout de l’inférence de type `$_` / `$PSItem` dans les blocs `catch{ }` (#8020) (merci @vexx32 !)
- Correction de l’inférence de type d’appel à la méthode statique (#8018) (merci @SeeminglyScience !)
- Création des types déduits pour `Select-Object`, `Group-Object`, **PSObject** et **Hashtable** (#7231) (merci @powercode !)
- Prise en charge de la méthode d’appel avec les paramètres de type `ByRef-like` (#7721)
- Gestion du cas où le chemin d’accès du module Windows PowerShell est déjà dans l’élément PSModulePath de l’environnement (#7727)
- Activation des applets de commande `SecureString` pour Non-Windows en stockant le texte brut (#9199)
- Amélioration du message d’erreur sur les systèmes non Windows lors de l’importation de clixml avec securestring (#7997)
- Ajout du paramètre ReplyTo à `Send-MailMessage` (#8727) (merci @replicaJunction !)
- Ajout d’un message obsolète à `Send-MailMessage` (#9178)
- Correctif `Restart-Computer` pour travailler sur `localhost` en l’absence de WinRM (#9160)
- Amener `Start-Job` à générer une erreur de fin d’exécution lorsque PowerShell est hébergé (#9128)
- Ajout d’accélérateurs de type de style C# et de suffixes pour ushort, uint, ulong et les littéraux courts (#7813) (merci @vexx32 !)
- Ajout de nouveaux suffixes pour les littéraux numériques - [about_Numeric_Literals][] (#7901) (merci @vexx32 !)
- Création d’un rapport correct sur le niveau d’impact lorsque SupportsShouldProcess n’est pas défini sur « true » (#8209) (merci @vexx32 !)
- Correction des problèmes de jeu de caractères dans les applets de commande Web (#8742) (merci @markekraus !)
- Correction du problème attendu `100-continue` avec les applets de commande Web (#8679) (merci @markekraus !)
- Correction du problème de blocage de fichier avec les applets de commande Web (#7676) (merci @Claustn !)
- Correction du problème d’analyse de la page de codes dans `Invoke-RestMethod` (#8694) (merci @markekraus !)
- Refactorisation de `ConvertTo-Json` pour exposer JsonObject.ConvertToJson comme une API publique (#8682)
- Ajout d’une profondeur maximale configurable dans `ConvertFrom-Json` avec -Depth (#8199) (merci @louistio !)
- Ajout d’un paramètre EscapeHandling dans l’applet de commande `ConvertTo-Json` (#7775) (merci @iSazonov !)
- Ajout de `-CustomPipeName` à pwsh et `Enter-PSHostProcess` (#8889)
- Activation de la création de liens symboliques relatifs sur Windows avec `New-Item` (8783 #)
- Autoriser les utilisateurs Windows en mode développeur à créer des liens symboliques sans élévation (#8534)
- Activation de `Write-Information` pour accepter `$null` (#8774)
- Correctif `Get-Help` pour les fonctions avancées avec contenu d’aide MAML (8353 #)
- Correction du problème `Get-Help` PSTypeName avec -Parameter lorsque qu’un seul paramètre est déclaré (#8754) (merci @pougetat !)
- Correction du calcul du jeton pour `Get-Help` exécuté sur ScriptBlock pour l’aide sur les commentaires. (#8238) (merci @hubuk !)
- Modification du paramètre -Parameter pour l’applet de commande `Get-Help` afin d’accepter des tableaux de chaînes (#8454) (merci @sethvs !)
- Résolution de PAGER si son chemin d’accès contient des espaces (#8571) (merci @pougetat !)
- Ajout d’une invite pour utiliser `less` dans la fonction 'help' afin d’indiquer à utilisateur comment quitter (#7998)
- Ajout de la prise en charge des types enum et char dans l’applet de commande `Format-Hex` (#8191) (merci @iSazonov !)
- Suppression de ShouldProcess de `Format-Hex` (#8178)
- Ajout des nouveaux paramètres Offset et Count pour `Format-Hex` et refactorisation de l’applet de commande (#7877) (merci @iSazonov !)
- Autoriser 'name' comme clé d’alias pour 'label' dans `ConvertTo-Html`, autoriser l’entrée 'width' à être un entier (#8426) (merci @mklement0 !)
- Rendre les propriétés calculées basées sur Scriptblock réutilisables `ConvertTo-Html` (#8427) (merci @mklement0 !)
- Ajout de l’applet de commande `Join-String` pour la création de texte à partir de l’entrée du pipeline (#7660) (merci @powercode !)
- Correctif `Join-String` pour la logique du paramètre FormatString de l’applet de commande (#8449) (merci @sethvs !)
- Retour de `Clear-Host` à `$RAWUI` et autorisation d’utiliser la communication à distance (#8609)
- Modification de `Clear-Host` en `[console]::clear` et suppression des alias clairs d’Unix (#8603)
- Correction de LiteralPath dans `Import-Csv` pour la liaison au résultat `Get-ChildItem` (#8277) (merci @iSazonov !)
- la fonction help ne devrait pas utiliser la radiomessagerie pour AliasHelpInfo (#8552)
- Ajout de `-UseMinimalHeader` à `Start-Transcript` pour réduire l’en-tête de transcription (#8402) (merci @lukexjeremy !)
- Ajouter les applets de commande `Enable-ExperimentalFeature` et `Disable-ExperimentalFeature` (#8318)
- Exposition de toutes les applets de commande depuis **PSDiagnostics** si logman.exe est disponible (#8366)
- Suppression du paramètre **Persist** de `New-PSDrive` sur la plateforme `non-Windows` (#8291) (merci @lukexjeremy !)
- Ajout de la prise en charge de `cd +` (#7206) (merci @bergmeister !)
- Autoriser `Set-Location -LiteralPath` à utiliser des dossiers nommés - et + (#8089)
- `Test-Path` renvoie `$false` avec une valeur de chemin d’accès vide ou `$null` (#8080) (merci @vexx32 !)
- Autoriser le renvoi d’un paramètre dynamique même si le chemin d’accès ne correspond à aucun fournisseur (#7957)
- Prise en charge de `Get-PSHostProcessInfo` et `Enter-PSHostProcess` sur les plateformes Unix (#8232)
- Réduction des allocations dans l’applet de commande `Get-Content` (#8103) (merci @iSazonov !)
- Autoriser `Add-Content` à partager l’accès en lecture avec d’autres outils pendant l’écriture de contenu (#8091)
- `Get/Add-Content` génère une erreur améliorée lors du ciblage d’un conteneur (#7823) (merci @kvprasoon !)
- Ajout des paramètres `-Name`, `-NoUserOverrides` et `-ListAvailable` à l’applet de commande `Get-Culture` (#7702) (merci @iSazonov !)
- Ajout d’un attribut unifié pour finaliser le paramètre **Encoding**. (#7732) (merci @ThreeFive-O !)
- Autoriser des ID numériques et un nom de pages de codes enregistrées dans les paramètres **Encoding** (#7636) (merci @iSazonov !)
- Correctif `Rename-Item -Path` avec caractère générique char (#7398) (merci @kwkam !)
- Si vous utilisez `Start-Transcript` et que le fichier existe, utiliser un fichier vide plutôt que de le supprimer (#8131) (merci @paalbra !)
- Créer des fichiers open source `Add-Type` avec **FileAccess.Read** et **FileShare.Read** explicitement (#7915) (merci @IISResetMe !)
- Correctif `Enter-PSSession -ContainerId` pour la dernière version Windows (#7883)
- Vérification que la propriété **NestedModules** est remplie par `Test-ModuleManifest` (#7859)
- Ajout d’un cas `%F` à `Get-Date` - UFormat (#7630) (merci @britishben !)
- Correctif `Set-Service -Status Stopped` pour arrêter les services avec des dépendances (#5525) (merci @zhenggu !)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Fonctionnalités expérimentales]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
