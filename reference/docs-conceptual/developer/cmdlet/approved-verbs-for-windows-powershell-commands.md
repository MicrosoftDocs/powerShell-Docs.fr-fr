---
title: Verbes approuvés pour les commandes PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.assetid: 2d4e58a9-05bc-437c-86b9-d8d55cba7d48
caps.latest.revision: 36
ms.openlocfilehash: b1e551c93540bd6769021aaa2bff08cfa3879e2c
ms.sourcegitcommit: 7c7f8bb9afdc592d07bf7ff4179d000a48716f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82174107"
---
# <a name="approved-verbs-for-powershell-commands"></a>Verbes approuvés pour les commandes PowerShell

PowerShell utilise une paire verbe-nom pour les noms des applets de commande et pour leurs classes Microsoft .NET Framework dérivées. Par exemple, l' `Get-Command` applet de commande fournie par PowerShell est utilisée pour récupérer toutes les commandes qui sont inscrites dans PowerShell. La partie verbe du nom identifie l’action effectuée par l’applet de commande. La partie substantif du nom identifie l’entité sur laquelle l’action est effectuée.

> [!NOTE]
> PowerShell utilise le terme *verbe* pour décrire un mot qui implique une action même si ce mot n’est pas un verbe standard dans la langue anglaise. Par exemple, le terme *nouveau* est un nom de verbe PowerShell valide, car il implique une action, même s’il ne s’agit pas d’un verbe dans la langue anglaise.

## <a name="verb-naming-rules"></a>Règles d’affectation des noms de verbe

La liste suivante fournit des instructions à prendre en compte lorsque vous choisissez le verbe d’un nom d’applet de commande :

- Lorsque vous spécifiez le verbe, nous vous recommandons d’utiliser l’un des noms de verbe prédéfinis fournis par PowerShell (les alias de ces verbes prédéfinis sont inclus dans les tableaux suivants). Lorsque vous utilisez un verbe prédéfini, vous garantissez la cohérence entre les applets de commande que vous créez, les applets de commande fournies par PowerShell et les applets de commande conçues par d’autres.

- Utilisez les verbes prédéfinis pour décrire l’étendue générale de l’action et utilisez des paramètres pour affiner l’action de l’applet de commande.

- Pour garantir la cohérence entre les applets de commande, n’utilisez pas un synonyme d’un verbe approuvé.

- Utilisez uniquement le formulaire de chaque verbe qui est listé dans cette rubrique. Par exemple, utilisez « obtenir », mais n’utilisez pas « obtenir » ou « obtient ».

- Utilisez la casse Pascal pour les verbes. Dans la casse Pascal, la première lettre de chaque mot est en majuscule, par exemple « ForEach ».

- N’utilisez pas les verbes ou les alias réservés suivants. Ces verbes sont utilisés par le langage PowerShell, ou par des applets de commande de cas spéciaux fournies par PowerShell.
  - ForEach (foreach)
  - Format (f)
  - Groupe (GP)
  - Trier (SR)
  - Tee (te)
  - Où (BL)

Une liste complète des verbes peut être affichée à l' `Get-Verb` aide de l’applet de commande.

## <a name="similar-verbs-for-different-actions"></a>Verbes similaires pour différentes actions

Les verbes similaires suivants représentent des actions différentes.

### <a name="new-vs-set"></a>Nouveautés et définition

Le `New` verbe est utilisé pour créer une ressource. Le `Set` verbe est utilisé pour modifier une ressource existante, en créant éventuellement la ressource si elle n’existe pas, telle que l' `Set-Variable` applet de commande.

### <a name="find-vs-search"></a>Rechercher et Rechercher

Le `Find` verbe est utilisé pour rechercher un objet. Le `Search` verbe est utilisé pour créer une référence à une ressource dans un conteneur.

### <a name="get-vs-read"></a>Obtenir ou lire

Le `Get` verbe est utilisé pour récupérer une ressource, telle qu’un fichier. Le `Read` verbe est utilisé pour obtenir des informations à partir d’une source, telle qu’un fichier.

### <a name="invoke-vs-start"></a>Appeler et démarrer

Le `Invoke` verbe est utilisé pour effectuer une opération qui est généralement une opération synchrone, telle que l’exécution d’une commande. Le `Start` verbe est utilisé pour commencer une opération qui est généralement une opération asynchrone, telle que le démarrage d’un processus.

### <a name="ping-vs-test"></a>Test ping et test

Utilisez le `Test` verbe.

## <a name="common-verbs"></a>Verbes courants

PowerShell utilise la classe d’énumération [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) pour définir des actions génériques qui peuvent s’appliquer à presque n’importe quelle applet de commande. Le tableau suivant répertorie la plupart des verbes définis.

|Verbe (alias)|Action|Commentaires|
|--------------------|------------|--------------|
|[Ajouter](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Ajoute une ressource à un conteneur ou attache un élément à un autre élément. Par exemple, l' `Add-Content` applet de commande ajoute du contenu à un fichier. Ce verbe est associé à `Remove`.|Pour cette action, n’utilisez pas de verbes tels que Append, Attach, Concatenate ou Insert.|
|[Clear](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (CL)|Supprime toutes les ressources d’un conteneur, mais ne supprime pas le conteneur. Par exemple, l' `Clear-Content` applet de commande supprime le contenu d’un fichier, mais ne supprime pas le fichier.|Pour cette action, n’utilisez pas de verbes tels que Flush, Erase, Release, UNMARK, unset ou annuler.|
|[Fermer](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (CS)|Modifie l’état d’une ressource pour la rendre inaccessible, non disponible ou inutilisable. Ce verbe est associé à`Open.`||
|[Copier](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (CP)|Copie une ressource vers un autre nom ou un autre conteneur. Par exemple, l' `Copy-Item` applet de commande utilisée pour accéder aux données stockées copie un élément d’un emplacement dans le magasin de données vers un autre emplacement.|Pour cette action, n’utilisez pas de verbes tels que le doublon, le clonage, la réplication ou la synchronisation.|
|[Entrée](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|Spécifie une action qui permet à l’utilisateur de se déplacer dans une ressource. Par exemple, l' `Enter-PSSession` applet de commande place l’utilisateur dans une session interactive. Ce verbe est associé à `Exit`.|Pour cette action, n’utilisez pas de verbes tels que Push ou into.|
|[Quitter](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|Définit l’environnement ou le contexte actuel sur le dernier contexte utilisé. Par exemple, l' `Exit-PSSession` applet de commande place l’utilisateur dans la session qui a été utilisée pour démarrer la session interactive. Ce verbe est associé à `Enter`.|Pour cette action, n’utilisez pas de verbes tels que POP ou out.|
|[Rechercher](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (FD)|Recherche un objet dans un conteneur inconnu, implicite, facultatif ou spécifié.||
|[Format](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Organise les objets dans un formulaire ou une disposition spécifiée.||
|[Obtient](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Spécifie une action qui récupère une ressource. Ce verbe est associé à `Set`.|Pour cette action, n’utilisez pas de verbes tels que lecture, ouvrir, Cat, type, dir, obtenir, vider, acquérir, examiner, Rechercher ou Rechercher.|
|[Masquer](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Rend une ressource indétectable. Par exemple, une applet de commande dont le nom comprend le verbe Hide peut masquer un service à un utilisateur. Ce verbe est associé à `Show`.|Pour cette action, n’utilisez pas un verbe tel que Block.|
|[Join](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Combine les ressources en une seule ressource. Par exemple, l' `Join-Path` applet de commande combine un chemin d’accès avec l’un de ses chemins enfants pour créer un chemin d’accès unique. Ce verbe est associé à `Split`.|Pour cette action, n’utilisez pas de verbes tels que combine, Unit, Connect ou Associate.|
|[Verrou](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (LK)|Sécurise une ressource. Ce verbe est associé à `Unlock`.|Pour cette action, n’utilisez pas de verbes tels que restreindre ou sécuriser.|
|[Déplacer](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Déplace une ressource d’un emplacement à un autre. Par exemple, l' `Move-Item` applet de commande déplace un élément d’un emplacement dans le magasin de données vers un autre emplacement.|Pour cette action, n’utilisez pas de verbes tels que Transfer, Name ou Migrate.|
|[Nouveau](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Crée une ressource. (Le `Set` verbe peut également être utilisé lors de la création d’une ressource qui comprend des données `Set-Variable` , telles que l’applet de commande.)|Pour cette action, n’utilisez pas de verbes tels que Create, Generate, Build, make ou Allocate.|
|[Ouvrir](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|Modifie l’état d’une ressource pour la rendre accessible, disponible ou utilisable. Ce verbe est associé à `Close`.||
|[Optimiser](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (OM)|Augmente l’efficacité d’une ressource.||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (POP)|Supprime un élément du haut d’une pile. Par exemple, l' `Pop-Location` applet de commande remplace l’emplacement actuel par l’emplacement qui a été le plus récemment placé sur la pile.||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|Ajoute un élément en haut d’une pile. Par exemple, l' `Push-Location` applet de commande pousse l’emplacement actuel sur la pile.||
|[Rétablir](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|Réinitialise une ressource à l’État qui a été annulé.||
|[Supprimer](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Supprime une ressource d’un conteneur. Par exemple, l' `Remove-Variable` applet de commande supprime une variable et sa valeur. Ce verbe est associé à `Add`.|Pour cette action, n’utilisez pas de verbes tels que Clear, Cut, dispose, ignore ou ERASE.|
|[Renommer](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (RN)|Modifie le nom d’une ressource. Par exemple, l' `Rename-Item` applet de commande, qui est utilisée pour accéder aux données stockées, modifie le nom d’un élément dans le magasin de données.|Pour cette action, n’utilisez pas un verbe tel que change.|
|[Réinitialiser](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (RS)|Restaure une ressource à son état d’origine.||
|[Recherche](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (SR)|Crée une référence à une ressource dans un conteneur.|Pour cette action, n’utilisez pas de verbes tels que Find ou Locate.|
|[Sélectionner](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (SC)|Localise une ressource dans un conteneur. Par exemple, l' `Select-String` applet de commande recherche du texte dans des chaînes et des fichiers.|Pour cette action, n’utilisez pas de verbes tels que Find ou Locate.|
|[Jeu](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Remplace des données sur une ressource existante ou crée une ressource qui contient des données. Par exemple, l' `Set-Date` applet de commande modifie l’heure système sur l’ordinateur local. (Le `New` verbe peut également être utilisé pour créer une ressource.) Ce verbe est associé à `Get`.|Pour cette action, n’utilisez pas de verbes tels que l’écriture, la réinitialisation, l’attribution ou la configuration.|
|[Afficher](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (SH)|Rend une ressource visible par l’utilisateur. Ce verbe est associé à `Hide`.|Pour cette action, n’utilisez pas de verbes tels que Display ou production.|
|[Ignorer](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (SK)|Ignore une ou plusieurs ressources ou points dans une séquence.|Pour cette action, n’utilisez pas un verbe comme Bypass ou Jump.|
|[Fractionner](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (SL)|Sépare les parties d’une ressource. Par exemple, l' `Split-Path` applet de commande retourne différentes parties d’un chemin d’accès. Ce verbe est associé à `Join`.|Pour cette action, n’utilisez pas un verbe comme distinct.|
|[Étape](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (St)|Passe au point ou à la ressource suivant dans une séquence.||
|[Commutateur](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (SW)|Spécifie une action qui alterne entre deux ressources, telles que la modification entre deux emplacements, responsabilités ou États.||
|[Annuler](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (un)|Définit une ressource à son état précédent.||
|[Déverrouiller](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (Royaume-Uni)|Libère une ressource qui a été verrouillée. Ce verbe est associé à `Lock`.|Pour cette action, n’utilisez pas de verbes tels que Release, UNRESTRICT ou unsecure.|
|[Espion](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (WC)|Inspecte ou surveille en permanence une ressource en vue de les modifier.||

## <a name="communications-verbs"></a>Verbes de communication

PowerShell utilise la classe [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) pour définir des actions qui s’appliquent aux communications. Le tableau suivant répertorie la plupart des verbes définis.

|Verbe (alias)|Action|Commentaires|
|--------------------|------------|--------------|
|[Connexion](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (CC)|Crée un lien entre une source et une destination. Ce verbe est associé à `Disconnect`.|Pour cette action, n’utilisez pas de verbes tels que JOIN ou Telnet.|
|[Déconnexion](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (DC)|Rompt le lien entre une source et une destination. Ce verbe est associé à `Connect`.|Pour cette action, n’utilisez pas de verbes tels que l’arrêt ou la fermeture de session.|
|[Lecture](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (RD)|Acquiert des informations à partir d’une source. Ce verbe est associé à `Write`.|Pour cette action, n’utilisez pas les verbes tels que Acquire, prompt ou obtenir.|
|[Recevoir](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (RC)|Accepte les informations envoyées à partir d’une source. Ce verbe est associé à `Send`.|Pour cette action, n’utilisez pas de verbes tels que lecture, accepter ou lire.|
|[Envoi](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (SD)|Fournit des informations à une destination. Ce verbe est associé à `Receive`.|Pour cette action, n’utilisez pas de verbes tels que put, diffusion, mail ou fax.|
|[Écriture](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (WR)|Ajoute des informations à une cible. Ce verbe est associé à `Read`.|Pour cette action, n’utilisez pas de verbes tels que put ou Print.|

## <a name="data-verbs"></a>Verbes de données

PowerShell utilise la classe [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData) pour définir des actions qui s’appliquent à la gestion des données. Le tableau suivant répertorie la plupart des verbes définis.

|Nom du verbe (alias)|Action|Commentaires|
|-------------------------|------------|--------------|
|[Sauvegarde](/dotnet/api/System.Management.Automation.VerbsData.Backup) (BA)|Stocke les données en les répliquant.|Pour cette action, n’utilisez pas de verbes tels que Save, Burn, replicate ou Sync.|
|[Point de contrôle](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|Crée un instantané de l’état actuel des données ou de sa configuration.|Pour cette action, n’utilisez pas de verbe comme diff.|
|[Comparer](/dotnet/api/System.Management.Automation.VerbsData.Compare) (CR)|Évalue les données d’une ressource par rapport aux données d’une autre ressource.|Pour cette action, n’utilisez pas de verbe comme diff.|
|[Compresser](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Compacte les données d’une ressource. Paires avec `Expand`.|Pour cette action, n’utilisez pas un verbe comme compact.|
|[Convertir](/dotnet/api/System.Management.Automation.VerbsData.Convert) (CV)|Modifie les données d’une représentation à une autre lorsque l’applet de commande prend en charge la conversion bidirectionnelle ou lorsque l’applet de commande prend en charge la conversion entre plusieurs types de données.|Pour cette action, n’utilisez pas de verbes tels que modifier, redimensionner ou rééchantillonner.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (CF)|Convertit un type principal d’entrée (le nom de l’applet de commande indique l’entrée) en un ou plusieurs types de sortie pris en charge.|Pour cette action, n’utilisez pas les verbes tels que l’exportation, la sortie ou l’extraction.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (CT)|Convertit à partir d’un ou de plusieurs types d’entrée en un type de sortie principal (le nom de l’applet de commande indique le type de sortie).|Pour cette action, n’utilisez pas de verbes tels que Import, Input ou in.|
|[Démontage](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (DM)|Détache une entité nommée d’un emplacement. Ce verbe est associé à `Mount`.|Pour cette action, n’utilisez pas de verbes tels que démonter ou dissocier.|
|[Modifier](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ED)|Modifie les données existantes en ajoutant ou en supprimant du contenu.|Pour cette action, n’utilisez pas de verbes tels que modifier, mettre à jour ou modifier.|
|[Développer](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Restaure les données d’une ressource qui a été compressée à son état d’origine. Ce verbe est associé à `Compress`.|Pour cette action, n’utilisez pas de verbes tels que Eclater ou décompresser.|
|[Exporter](/dotnet/api/System.Management.Automation.VerbsData.Export) (EP)|Encapsule l’entrée principale dans un magasin de données persistant, tel qu’un fichier, ou dans un format d’échange. Ce verbe est associé à `Import`.|Pour cette action, n’utilisez pas de verbes tels que Extract ou Backup.|
|[Groupe](/dotnet/api/System.Management.Automation.VerbsData.Group) (GP)|Organise ou associe une ou plusieurs ressources.|Pour cette action, n’utilisez pas de verbes tels que l’agrégation, l’organisation, l’Association ou la corrélation.|
|[Importation](/dotnet/api/System.Management.Automation.VerbsData.Import) (IP)|Crée une ressource à partir de données stockées dans un magasin de données persistant (tel qu’un fichier) ou dans un format d’échange. Par exemple, l' `Import-CSV` applet de commande importe des données à partir d’un fichier de valeurs séparées par des virgules (CSV) vers des objets qui peuvent être utilisés par d’autres applets de commande. Ce verbe est associé à `Export`.|Pour cette action, n’utilisez pas de verbes tels que BulkLoad ou Load.|
|[Initialiser](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (dans)|Prépare une ressource en vue de son utilisation et lui affecte un État par défaut.|Pour cette action, n’utilisez pas de verbes tels que Erase, init, Renew, Rebuild, Reinitialize ou Setup.|
|[Limite](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Applique des contraintes à une ressource.|Pour cette action, n’utilisez pas un verbe tel que quota.|
|[Fusion](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Crée une ressource unique à partir de plusieurs ressources.|Pour cette action, n’utilisez pas de verbes tels que combine ou join.|
|[Mount](/dotnet/api/System.Management.Automation.VerbsData.Mount) (MT)|Attache une entité nommée à un emplacement. Ce verbe est associé à `Dismount`.|Pour cette action, n’utilisez pas le verbe Connect.|
|[Sortie](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Envoie des données à partir de l’environnement. Par exemple, l' `Out-Printer` applet de commande envoie des données à une imprimante.||
|[Publication](/dotnet/api/System.Management.Automation.VerbsData.Publish) (PB)|Met une ressource à la disposition d’autres utilisateurs. Ce verbe est associé à `Unpublish`.|Pour cette action, n’utilisez pas de verbes tels que le déploiement, la mise en version ou l’installation.|
|[Restauration](/dotnet/api/System.Management.Automation.VerbsData.Restore) (RR)|Affecte à une ressource un État prédéfini, tel qu’un état défini par `Checkpoint`. Par exemple, l' `Restore-Computer` applet de commande démarre une restauration du système sur l’ordinateur local.|Pour cette action, n’utilisez pas de verbes tels que Repair, Return, Undo ou Fix.|
|[Enregistrer](/dotnet/api/System.Management.Automation.VerbsData.Save) (VP)|Préserve les données pour éviter toute perte.||
|[Synchronisation](/dotnet/api/System.Management.Automation.VerbsData.Sync) (SY)|Garantit que deux ressources ou plus sont dans le même État.|Pour cette action, n’utilisez pas de verbes tels que la réplication, la contrainte ou la correspondance.|
|[Annuler la publication](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (UB)|Rend une ressource indisponible pour d’autres. Ce verbe est associé à `Publish`.|Pour cette action, n’utilisez pas de verbes tels que Uninstall, Revert ou Hide.|
|[Mise à jour](/dotnet/api/System.Management.Automation.VerbsData.Update) (UD)|Met à jour une ressource pour conserver son état, sa précision, sa conformité ou sa conformité. Par exemple, l' `Update-FormatData` applet de commande met à jour et ajoute des fichiers de mise en forme à la console PowerShell actuelle.|Pour cette action, n’utilisez pas les verbes tels que l’actualisation, le renouvellement, le recalcul ou la réindexation.|

## <a name="diagnostic-verbs"></a>Verbes de diagnostic

PowerShell utilise la classe [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) pour définir des actions qui s’appliquent aux Diagnostics. Le tableau suivant répertorie la plupart des verbes définis.

|Verbe (alias)|Action|Commentaires|
|--------------------|------------|--------------|
|[Débogage](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (dB)|Examine une ressource pour diagnostiquer les problèmes opérationnels.|Pour cette action, n’utilisez pas de verbe tel que le diagnostic.|
|[Mesure](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (MS)|Identifie les ressources qui sont consommées par une opération spécifiée ou récupère des statistiques sur une ressource.|Pour cette action, n’utilisez pas de verbes tels que Calculate, determine ou Analyze.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)|Utilisez le `Test` verbe.||
|[Réparation](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (RP)|Restaure une ressource dans une condition utilisable|Pour cette action, n’utilisez pas de verbes tels que Fix ou Restore.|
|[Résoudre](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (RV)|Mappe une représentation sténographique d’une ressource à une représentation plus complète.|Pour cette action, n’utilisez pas de verbes tels que Expand ou determine.|
|[Test](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Vérifie l’opération ou la cohérence d’une ressource.|Pour cette action, n’utilisez pas de verbes tels que le diagnostic, l’analyse, la récupération ou la vérification.|
|[Suivi](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (TR)|Effectue le suivi des activités d’une ressource.|Pour cette action, n’utilisez pas de verbes tels que Track, follow, Inspect ou creuser.|

## <a name="lifecycle-verbs"></a>Verbes de cycle de vie

PowerShell utilise la classe [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) pour définir des actions qui s’appliquent au cycle de vie d’une ressource. Le tableau suivant répertorie la plupart des verbes définis.

|Verbe (alias)|Action|Commentaires|
|--------------------|------------|--------------|
|[Approuver](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (AP)|Confirme ou accepte l’état d’une ressource ou d’un processus.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (As)|Affirme l’état d’une ressource.|Pour cette action, n’utilisez pas de verbe tel que certifie.|
|[Build](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (BD)|Crée un artefact (généralement un fichier binaire ou un document) à partir d’un ensemble de fichiers d’entrée (généralement le code source ou les documents déclaratifs)|Ce verbe a été ajouté dans PowerShell V6|
|[Terminé](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (CP)|Conclut une opération.||
|[Confirmer](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (CN)|Accuse réception, vérifie ou valide l’état d’une ressource ou d’un processus.|Pour cette action, n’utilisez pas de verbes tels que la reconnaissance, l’acceptation, la certification, la validation ou la vérification.|
|[Deny](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (DN)|Refuse, objet, bloque ou s’oppose à l’état d’une ressource ou d’un processus.|Pour cette action, n’utilisez pas de verbes tels que Block, Object, Reject ou Reject.|
|[Déployer](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (DP)|Envoie une application, un site Web ou une solution à une cible distante [s] de manière à ce qu’un consommateur de cette solution puisse y accéder une fois le déploiement terminé.|Ce verbe a été ajouté dans PowerShell V6|
|[Désactiver](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Configure une ressource à un État indisponible ou inactif. Par exemple, l' `Disable-PSBreakpoint` applet de commande rend un point d’arrêt inactif. Ce verbe est associé à `Enable`.|Pour cette action, n’utilisez pas les verbes tels que halt ou Hide.|
|[Activer](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Configure une ressource à un état disponible ou actif. Par exemple, l' `Enable-PSBreakpoint` applet de commande rend un point d’arrêt actif. Ce verbe est associé à `Disable`.|Pour cette action, n’utilisez pas de verbes tels que Start ou BEGIN.|
|[Installer](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (est)|Place une ressource dans un emplacement et l’initialise éventuellement. Ce verbe est associé à `Uninstall`.|Pour cette action, n’utilisez pas de verbe comme le programme d’installation.|
|[Appeler](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Exécute une action, telle que l’exécution d’une commande ou d’une méthode.|Pour cette action, n’utilisez pas de verbes tels que exécuter ou démarrer.|
|[Inscrire](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (RG)|Crée une entrée pour une ressource dans un référentiel tel qu’une base de données. Ce verbe est associé à `Unregister`.||
|[Demande](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (RQ)|Demande une ressource ou demande des autorisations.||
|[Redémarrer](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (RT)|Arrête une opération, puis la redémarre. Par exemple, l' `Restart-Service` applet de commande s’arrête et démarre un service.|Pour cette action, n’utilisez pas de verbe tel que recycle.|
|[Reprendre](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (RU)|Démarre une opération qui a été suspendue. Par exemple, l' `Resume-Service` applet de commande démarre un service qui a été suspendu. Ce verbe est associé à `Suspend`.||
|[Start](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Lance une opération. Par exemple, l' `Start-Service` applet de commande démarre un service. Ce verbe est associé à `Stop`.|Pour cette action, n’utilisez pas de verbes tels que le lancement, l’initialisation ou le démarrage.|
|[Arrêter](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (SP)|Interrompt une activité. Ce verbe est associé à `Start`.|Pour cette action, n’utilisez pas de verbes tels que end, Kill, Terminate ou Cancel.|
|[Envoi](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (SB)|Présente une ressource pour approbation.|Pour cette action, n’utilisez pas un verbe tel que la publication.|
|[Suspendre](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (SS)|Suspend une activité. Par exemple, l' `Suspend-Service` applet de commande suspend un service. Ce verbe est associé à `Resume`.|Pour cette action, n’utilisez pas un verbe tel que pause.|
|[Désinstaller](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (US)|Supprime une ressource d’un emplacement indiqué. Ce verbe est associé à `Install`.||
|[Annuler l’inscription](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (votre)|Supprime l’entrée d’une ressource d’un référentiel. Ce verbe est associé à `Register`.|Pour cette action, n’utilisez pas de verbe tel que Remove.|
|[Wait](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Interrompt une opération jusqu’à ce qu’un événement spécifié se produise. Par exemple, l' `Wait-Job` applet de commande suspend les opérations jusqu’à ce qu’une ou plusieurs des tâches en arrière-plan soient terminées.|Pour cette action, n’utilisez pas de verbes tels que Sleep ou pause.|

## <a name="security-verbs"></a>Verbes de sécurité

PowerShell utilise la classe [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) pour définir des actions qui s’appliquent à la sécurité. Le tableau suivant répertorie la plupart des verbes définis.

|Verbe (alias)|Action|Commentaires|
|--------------------|------------|--------------|
|[Bloc](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (BL)|Restreint l’accès à une ressource. Ce verbe est associé à `Unblock`.|Pour cette action, n’utilisez pas de verbes tels que la fonction d’interdiction, de limite ou de refus.|
|[Grant](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (GR)|Autorise l’accès à une ressource. Ce verbe est associé à `Revoke`.|Pour cette action, n’utilisez pas de verbes tels que Allow ou Enable.|
|[Protéger](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (PT)|Protège une ressource contre les attaques ou les pertes. Ce verbe est associé à `Unprotect`.|Pour cette action, n’utilisez pas de verbes tels que le chiffrement, la protection ou le scellement.|
|[Révoquer](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (RK)|Spécifie une action qui n’autorise pas l’accès à une ressource. Ce verbe est associé à `Grant`.|Pour cette action, n’utilisez pas de verbes tels que Remove ou Disable.|
|[Débloquer](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (UL)|Supprime les restrictions d’une ressource. Ce verbe est associé à `Block`.|Pour cette action, n’utilisez pas de verbes tels que Clear ou Allow.|
|[Ôter la protection](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (haut)|Supprime les protections d’une ressource qui ont été ajoutées pour l’empêcher d’une attaque ou d’une perte. Ce verbe est associé à `Protect`.|Pour cette action, n’utilisez pas de verbes tels que le déchiffrement ou le déscellage.|

## <a name="other-verbs"></a>Autres verbes

PowerShell utilise la classe [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) pour définir des noms de verbes canoniques qui ne rentrent pas dans une catégorie de nom de verbe spécifique, tels que les verbes de noms de verbes communs, de communication, de données, de cycle de vie ou de sécurité.

|Verbe (alias)|Action|Commentaires|
|--------------------|------------|--------------|
|[Utilisation](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Utilise ou comprend une ressource pour effectuer une opération.||

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Déclaration d’applet de commande](./cmdlet-class-declaration.md)

[Guide de programmation pour Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md)

[Kit de développement logiciel Windows PowerShell Shell](../windows-powershell-reference.md)
