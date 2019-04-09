---
title: Les verbes approuvés pour les commandes PowerShell | Microsoft Docs
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
ms.openlocfilehash: 4475b3f5e15826efbe8bab867011985cd7e2e1ae
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293348"
---
# <a name="approved-verbs-for-powershell-commands"></a>Verbes approuvés pour les commandes PowerShell

PowerShell utilise une paire verbe-substantif pour les noms des applets de commande et de leurs classes dérivées de Microsoft .NET Framework.
Par exemple, le `Get-Command` applet de commande fourni par PowerShell permet de récupérer toutes les commandes qui sont inscrits dans PowerShell.
La partie verbe de nom identifie l’action qui exécute l’applet de commande.
La partie substantif du nom identifie l’entité sur laquelle l’action est effectuée.

> [!NOTE]
> PowerShell utilise le terme *verbe* pour décrire un mot qui implique une action, même si ce mot n’est pas un verbe standard en langue anglaise.
> Par exemple, le terme *New* est un nom de verbe PowerShell valide, car il implique une action, même s’il n’est pas un verbe dans la langue anglaise.

## <a name="verb-naming-rules"></a>Règles d’affectation de noms de verbe

La liste suivante fournit des instructions à prendre en compte lorsque vous choisissez le verbe pour un nom de l’applet de commande :

* Lorsque vous spécifiez le verbe, nous vous recommandons d’utiliser un des noms de verbe prédéfinies fournies par PowerShell (alias pour ces verbes prédéfinis sont inclus dans les tableaux suivants).
  Lorsque vous utilisez un verbe prédéfini, vous garantir la cohérence entre les applets de commande que vous créez, les applets de commande qui sont fournies par PowerShell et les applets de commande qui sont conçues par d’autres utilisateurs.

* Utiliser les verbes prédéfinis pour décrire la portée générale de l’action et utiliser des paramètres pour affiner l’action de l’applet de commande.

* Pour appliquer la cohérence entre les applets de commande, n’utilisez pas un synonyme d’un verbe approuvé.

* Utilisez uniquement la forme de chaque verbe qui est répertorié dans cette rubrique.
  Par exemple, utilisez « Get », mais n’utilisez pas « Obtention de » ou « Obtient ».

* Utilisez la casse Pascal pour les verbes de mise en majuscules.
  Dans Pascal casse de la lettre initiale de chaque mot est en majuscules, telles que « ForEach ».

* N’utilisez pas les verbes réservés suivants ou les alias.
  Ces verbes sont utilisés par le langage PowerShell, ou par des applets de commande cas spécial fourni par PowerShell.
  - ForEach (foreach)
  - Format (f)
  - Groupe (gp)
  - Tri (sr)
  - Tee (te)
  - Où (q)

## <a name="similar-verbs-for-different-actions"></a>Verbes similaires pour différentes Actions

Les verbes similaire suivants représentent les différentes actions.

### <a name="new-vs-set"></a>Nouveau vs. Set
Le `New` verbe est utilisé pour créer une nouvelle ressource.
Le `Set` verbe est utilisé pour modifier une ressource existante, si vous le souhaitez créer la ressource si elle n’existe pas, comme le `Set-Variable` applet de commande.

### <a name="find-vs-search"></a>Trouver Visual Studio. Rechercher
Le `Find` verbe est utilisé pour la recherche d’un objet.
Le `Search` verbe est utilisé pour créer une référence à une ressource dans un conteneur.

### <a name="get-vs-read"></a>Obtenir Visual Studio. Lecture
Le `Get` verbe est utilisé pour récupérer une ressource, telle qu’un fichier.
Le `Read` verbe est utilisé pour obtenir des informations à partir d’une source, tel qu’un fichier.

### <a name="invoke-vs-start"></a>Appel de Visual Studio. Démarrer
Le `Invoke` verbe est utilisé pour effectuer une opération qui est généralement une opération synchrone, telles que l’exécution d’une commande.
Le `Start` verbe est utilisé pour lancer une opération qui est généralement une opération asynchrone, telles que le démarrage d’un processus.

### <a name="ping-vs-test"></a>Ping vs. Test
Utilisez le `Test` verbe.

## <a name="common-verbs"></a>Verbes courants

PowerShell utilise le [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) classe d’énumération pour définir les actions génériques qui peuvent s’appliquent à presque n’importe quel applet de commande.
Le tableau suivant répertorie la plupart des verbes définis.

|Verbe (alias)|Action|Commentaires|
|--------------------|------------|--------------|
|[Add](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Ajoute une ressource à un conteneur, ou attache un élément à un autre élément. Par exemple, le `Add-Content` applet de commande ajoute du contenu dans un fichier. Ce verbe est associé à `Remove`.|Pour cette action, ne pas utiliser verbes tels que Append, attacher, concaténer, ou insérer.|
|[Effacer](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Supprime toutes les ressources à partir d’un conteneur, mais ne supprime pas le conteneur. Par exemple, le `Clear-Content` cmdlet supprime le contenu d’un fichier, mais ne supprime pas le fichier.|Pour cette action, n’utilisez pas des verbes tels que le vidage, effacement, mise en production, ne pas marquer, annuler la définition ou annuler.|
|[Fermer](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|Modifie l’état d’une ressource pour la rendre inaccessible, indisponible ou inutilisable. Ce verbe est associé. `Open.`||
|[Copie](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|Copie une ressource à un autre nom ou à un autre conteneur. Par exemple, le `Copy-Item` applet de commande qui est utilisé pour accéder aux données stockées copie un élément d’un emplacement dans le magasin de données vers un autre emplacement.|Pour cette action, n’utilisez pas les verbes comme doublon, Clone, Replicate ou synchronisation.|
|[Entrez](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|Spécifie une action qui permet à l’utilisateur à déplacer vers une ressource. Par exemple, le `Enter-PSSession` applet de commande place l’utilisateur dans une session interactive. Ce verbe est associé à `Exit`.|Pour cette action, n’utilisez pas des verbes tels que de Push ou dans.|
|[Sortie](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|Définit le contexte ou l’environnement actuel pour le contexte des derniers fichiers utilisé. Par exemple, le `Exit-PSSession` applet de commande place l’utilisateur dans la session qui a été utilisée pour démarrer la session interactive. Ce verbe est associé à `Enter`.|Pour cette action, n’utilisez pas les verbes telles que Pop ou Out.|
|[Rechercher](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|Recherche un objet dans un conteneur qui est inconnu, implicite, facultatif ou spécifié.||
|[Format](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Organise les objets dans un formulaire ou d’une mise en page.||
|[Get](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Spécifie une action qui Récupère une ressource. Ce verbe est associé à `Set`.|Pour cette action, n’utilisez pas des verbes tels que lecture, Open, Cat, Type, Dir, obtenir, vidage, acquisition, examiner, rechercher ou recherche.|
|[Hide](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Empêche toute détection d’une ressource. Par exemple, une applet de commande dont le nom inclut le verbe Masquer peut masquer un service à partir d’un utilisateur. Ce verbe est associé à `Show`.|Pour cette action, n’utilisez pas un verbe, comme le blocage.|
|[Join](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Combine des ressources en une seule ressource. Par exemple, le `Join-Path` applet de commande combine un chemin d’accès avec l’un de ses chemins d’accès enfant pour créer un chemin d’accès unique. Ce verbe est associé à `Split`.|Pour cette action, n’utilisez pas des verbes tels que les combiner, Unite, Connect ou associer.|
|[Verrou](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|Permet de sécuriser une ressource. Ce verbe est associé à `Unlock`.|Pour cette action, n’utilisez pas les verbes tels que restreindre ou sécurisé.|
|[Move](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Déplace une ressource d’un emplacement vers un autre. Par exemple, le `Move-Item` applet de commande déplace un élément d’un emplacement dans le magasin de données vers un autre emplacement.|Pour cette action, n’utilisez pas des verbes tels que le transfert, le nom ou migrer.|
|[Nouvelle](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Crée une ressource. (Le `Set` verbe peut également être utilisé lors de la création d’une ressource qui inclut des données, tels que le `Set-Variable` applet de commande.)|Pour cette action, n’utilisez pas des verbes tels que créer, générer, Build, vérifiez ou allouer.|
|[Ouvrez](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|Modifie l’état d’une ressource pour le rendre utilisable, disponible ou accessible. Ce verbe est associé à `Close`.||
|[Optimize](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|Augmente l’efficacité d’une ressource.||
|[POP](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Supprime un élément du haut de la pile. Par exemple, le `Pop-Location` applet de commande modifie l’emplacement actuel vers l’emplacement qui a été récemment envoyée à la pile.||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|Ajoute un élément vers le haut de la pile. Par exemple, le `Push-Location` applet de commande place l’emplacement actuel dans la pile.||
|[Restauration par progression](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|Réinitialise une ressource à l’état qui a été annulée.||
|[Remove](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Supprime une ressource à partir d’un conteneur. Par exemple, le `Remove-Variable` applet de commande supprime une variable et sa valeur. Ce verbe est associé à `Add`.|Pour cette action, ne pas utiliser verbes ce type en clair, couper, supprimer, ignorer ou effacer.|
|[Renommer](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (rn)|Modifie le nom d’une ressource. Par exemple, le `Rename-Item` applet de commande, qui est utilisé pour accéder aux données stockées, modifie le nom d’un élément dans le magasin de données.|Pour cette action, n’utilisez pas un verbe, par exemple le changement.|
|[Réinitialiser](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (rs)|Définit une ressource à son état d’origine.||
|[Recherche](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|Crée une référence à une ressource dans un conteneur.|Pour cette action, n’utilisez pas des verbes tels que rechercher ou rechercher.|
|[Sélectionnez](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|Localise une ressource dans un conteneur. Par exemple, le `Select-String` applet de commande recherche du texte dans les chaînes et les fichiers.|Pour cette action, n’utilisez pas des verbes tels que rechercher ou rechercher.|
|[Définissez](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Remplace les données sur une ressource existante ou crée une ressource qui contient des données. Par exemple, le `Set-Date` applet de commande modifie l’heure système sur l’ordinateur local. (Le `New` verbe peut également être utilisé pour créer une ressource.) Ce verbe est associé à `Get`.|Pour cette action, n’utilisez pas des verbes tels que l’écriture, de réinitialisation, affectez ou configurer.|
|[Afficher](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|Rend une ressource visibles par l’utilisateur. Ce verbe est associé à `Hide`.|Pour cette action, n’utilisez pas les verbes tels que l’affichage ou de production.|
|[Skip](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (sk)|Ignore un ou plusieurs des ressources ou des points d’une séquence.|Pour cette action, n’utilisez pas un verbe telles que le contournement ou un lien.|
|[Fractionnement](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (sl)|Sépare les parties d’une ressource. Par exemple, le `Split-Path` applet de commande renvoie les différentes parties d’un chemin d’accès. Ce verbe est associé à `Join`.|Pour cette action, n’utilisez pas un verbe telle distinct.|
|[Étape](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|Se déplace vers le point suivant ou la ressource dans une séquence.||
|[Commutateur](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|Spécifie une action qui alterne entre deux ressources, telles que de changer entre deux emplacements, les responsabilités ou les États.||
|[Annuler](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (Annuler)|Définit une ressource dans son état précédent.||
|[Déverrouiller](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (Royaume-Uni)|Libère une ressource qui a été verrouillée. Ce verbe est associé à `Lock`.|Pour cette action, n’utilisez pas des verbes tels que la mise en production, Unrestrict ou non sécurisé.|
|[Espion](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc)|En permanence inspecte ou surveille une ressource pour les modifications.||

## <a name="communications-verbs"></a>Verbes de communications

PowerShell utilise le [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) classe pour définir les actions qui s’appliquent aux communications.
Le tableau suivant répertorie la plupart des verbes définis.

|Verbe (alias)|Action|Commentaires|
|--------------------|------------|--------------|
|[Se connecter](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (cc)|Crée un lien entre une source et une destination. Ce verbe est associé à `Disconnect`.|Pour cette action, n’utilisez pas des verbes tels que la jointure ou Telnet.|
|[Déconnecter](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|Rompt le lien entre une source et une destination. Ce verbe est associé à `Connect`.|Pour cette action, n’utilisez pas des verbes tels que l’arrêt ou la fermeture de session.|
|[Lecture](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|Acquiert des informations à partir d’une source. Ce verbe est associé à `Write`.|Pour cette action, ne pas utiliser verbes tels que Acquire, invite, ou obtenir.|
|[Réception](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|Accepte les informations envoyées à partir d’une source. Ce verbe est associé à `Send`.|Pour cette action, ne pas utiliser verbes tels que lecture, accepter, ou Aperçu.|
|[Envoyer](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (sd)|Fournit des informations à une destination. Ce verbe est associé à `Receive`.|Pour cette action, n’utilisez pas des verbes tels que Put, de diffusion, de messagerie ou de télécopie.|
|[Écrire](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (TA)|Ajoute des informations à une cible. Ce verbe est associé à `Read`.|Pour cette action, n’utilisez pas des verbes tels que Put ou impression.|

## <a name="data-verbs"></a>Verbes de données

PowerShell utilise le [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) classe pour définir les actions qui s’appliquent à la gestion des données.
Le tableau suivant répertorie la plupart des verbes définis.

|Nom du verbe (alias)|Action|Commentaires|
|-------------------------|------------|--------------|
|[Sauvegarde](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|Stocke les données en effectuant une réplication.|Pour cette action, n’utilisez pas les verbes tels qu’Enregistrer, Burn, de réplication ou de synchronisation.|
|[Point de contrôle](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|Crée un instantané de l’état actuel des données ou de sa configuration.|Pour cette action, n’utilisez pas un verbe de comparaison.|
|[Comparer](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|Évalue les données à partir d’une ressource sur les données à partir d’une autre ressource.|Pour cette action, n’utilisez pas un verbe de comparaison.|
|[Compresser](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Compacte les données d’une ressource. Paires avec `Expand`.|Pour cette action, n’utilisez pas un verbe telles que Compact.|
|[Convertir](/dotnet/api/System.Management.Automation.VerbsData.Convert) (cv)|Modifie les données d’une représentation à l’autre lors de l’applet de commande prend en charge la conversion de bidirectionnel ou lors de l’applet de commande prend en charge la conversion entre plusieurs types de données.|Pour cette action, ne pas utiliser verbes tels que des modifications, redimensionner, ou Resample.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|Convertit un type de principal de l’entrée (le nom de l’applet de commande indique l’entrée) à un ou plusieurs types de sortie pris en charge.|Pour cette action, n’utilisez pas des verbes tels que l’exportation, de sortie ou de sortie.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|Convertit à partir d’un ou plusieurs types d’entrée à un type de sortie principale (le nom de l’applet de commande indique le type de sortie).|Pour cette action, n’utilisez pas des verbes tels que l’importation, d’entrée, ou dans.|
|[Démonter](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|Détache une entité nommée à partir d’un emplacement. Ce verbe est associé à `Mount`.|Pour cette action, n’utilisez pas des verbes tels que démonter ou supprimer la liaison.|
|[Modifier](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Modifie les données existantes en ajoutant ou supprimant le contenu.|Pour cette action, n’utilisez pas des verbes tels que la modification, de mise à jour ou de modification.|
|[Développez](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Restaure les données d’une ressource qui a été compressée à son état d’origine. Ce verbe est associé à `Compress`.|Pour cette action, n’utilisez pas des verbes tels que Explode ou non.|
|[Exporter](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|Encapsule l’entrée principale dans un magasin de données persistant, tel qu’un fichier, ou dans un format d’échange. Ce verbe est associé à `Import`.|Pour cette action, n’utilisez pas des verbes tels que l’extraction ou sauvegarde.|
|[Groupe](/dotnet/api/System.Management.Automation.VerbsData.Group) (gp)|Réorganise ou associe une ou plusieurs ressources.|Pour cette action, ne pas utiliser verbes tels que de l’agrégat, organiser, associer, ou mettre en corrélation.|
|[Importation](/dotnet/api/System.Management.Automation.VerbsData.Import) (ip)|Crée une ressource à partir des données qui sont stockées dans un magasin de données persistantes (par exemple, un fichier) ou dans un format d’échange. Par exemple, le `Import-CSV` applet de commande importe les données à partir d’un fichier de valeurs séparées par des virgules (CSV) aux objets qui peuvent être utilisées par d’autres applets de commande. Ce verbe est associé à `Export`.|Pour cette action, n’utilisez pas des verbes tels que le chargement en bloc ou de charge.|
|[Initialiser](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Prépare une ressource à utiliser et lui affecte un état par défaut.|Pour cette action, n’utilisez pas des verbes tels que l’effacement, Init, renouveler, reconstruction, réinitialiser ou le programme d’installation.|
|[Limit](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Applique des contraintes à une ressource.|Pour cette action, n’utilisez pas un verbe de Quota.|
|[Fusion](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Crée une ressource unique à partir de plusieurs ressources.|Pour cette action, n’utilisez pas des verbes tels que combiner ou de jointure.|
|[Monter](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|Attache une entité nommée à un emplacement. Ce verbe est associé à `Dismount`.|Pour cette action, n’utilisez pas le verbe Connect.|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Envoie des données en dehors de l’environnement. Par exemple, le `Out-Printer` applet de commande envoie des données à une imprimante.||
|[Publier](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|Rend une ressource disponible à d’autres personnes. Ce verbe est associé à `Unpublish`.|Pour cette action, ne pas utiliser des verbes tels que de déployer, version, ou installer.|
|[Restaurer](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|Définit une ressource dans un état prédéfini, par exemple, un état défini par `Checkpoint`. Par exemple, le `Restore-Computer` applet de commande démarre une restauration du système sur l’ordinateur local.|Pour cette action, n’utilisez pas des verbes tels que la réparation, retour, d’annulation ou correctif.|
|[Enregistrer](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|Préserve les données pour éviter de perdre.||
|[Synchronisation](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|Garantit que deux ou plusieurs ressources sont dans le même état.|Pour cette action, ne pas utiliser verbes tels que Replicate, forcée, ou correspondre.|
|[Annuler la publication](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (ub)|Une ressource ne permet pas à d’autres personnes. Ce verbe est associé à `Publish`.|Pour cette action, ne pas utiliser verbes tels que de la désinstallation, Revert, ou masquer.|
|[Mise à jour](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|Met la ressource à jour pour mettre à jour son état, précision, la conformité ou conformité. Par exemple, le `Update-FormatData` applet de commande met à jour et ajoute les fichiers de mise en forme à la console PowerShell en cours.|Pour cette action, ne pas utiliser verbes tels que l’actualisation, renouveler, recalculer, ou réindexer.|

## <a name="diagnostic-verbs"></a>Verbes de Diagnostics

PowerShell utilise le [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) classe pour définir les actions qui s’appliquent aux diagnostics.
Le tableau suivant répertorie la plupart des verbes définis.

|Verbe (alias)|Action|Commentaires|
|--------------------|------------|--------------|
|[Déboguer](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (db)|Examine une ressource pour diagnostiquer les problèmes opérationnels.|Pour cette action, n’utilisez pas un verbe telles que de diagnostiquer.|
|[Mesure](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|Identifie les ressources qui sont consommées par une opération spécifiée, ou récupère des statistiques sur une ressource.|Pour cette action, n’utilisez pas des verbes tels que Calculate, déterminer ou analyser.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)|Utilisez le `Test` verbe.||
|[Réparation](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|Restaure une ressource à une condition exploitable|Pour cette action, n’utilisez pas des verbes tels que le correctif ou de restauration.|
|[Résoudre](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|Mappe une représentation sous forme de raccourci d’une ressource à une représentation plus complète.|Pour cette action, n’utilisez pas des verbes tels que développer ou déterminer.|
|[Test](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Vérifie l’opération ou la cohérence d’une ressource.|Pour cette action, n’utilisez pas des verbes tels que diagnostiquer, analyser, de récupération ou vérifiez.|
|[Trace](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|Suivi des activités d’une ressource.|Pour cette action, ne pas utiliser verbes tels que piste, suivi, inspecter, ou aller.|

## <a name="lifecycle-verbs"></a>Verbes de cycle de vie

PowerShell utilise le [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) classe pour définir les actions qui s’appliquent au cycle de vie d’une ressource.
Le tableau suivant répertorie la plupart des verbes définis.

|Verbe (alias)|Action|Commentaires|
|--------------------|------------|--------------|
|[Approuver](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|Confirme ou n’accepte pas l’état d’une ressource ou un processus.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (comme)|Confirmez l’état d’une ressource.|Pour cette action, n’utilisez pas un verbe telles que Certify.|
|[Build](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|Crée un artefact (généralement un fichier binaire ou document) en dehors d’un ensemble de fichiers d’entrée (généralement le code source ou documents déclaratifs)|Ce verbe a été ajouté dans PowerShell v6|
|[Complète](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (cp)|Termine une opération.||
|[Confirmer](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|Accuse réception vérifie ou, valide l’état d’une ressource ou un processus.|Pour cette action, n’utilisez pas des verbes tels que l’accusé de réception, accepte, Certify, valider ou vérifiez.|
|[Refuser](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|Refuse, objets, bloque ou s’oppose à l’état d’une ressource ou un processus.|Pour cette action, ne pas utiliser verbes tels que de bloc, objet, refuser, ou rejeter.|
|[Déployer](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|Envoie une application, un site Web ou une solution à une cible distante [s] de manière à ce qu’un consommateur de cette solution est accessible après que le déploiement est terminé|Ce verbe a été ajouté dans PowerShell v6|
|[Désactiver](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Configure une ressource à un état non disponible ou inactif. Par exemple, le `Disable-PSBreakpoint` applet de commande effectue un point d’arrêt inactive. Ce verbe est associé à `Enable`.|Pour cette action, n’utilisez pas des verbes tels que Halt ou masquer.|
|[Activer](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Configure une ressource à un état actif ou non disponible. Par exemple, le `Enable-PSBreakpoint` applet de commande rend un point d’arrêt actif. Ce verbe est associé à `Disable`.|Pour cette action, n’utilisez pas des verbes tels que Démarrer ou Begin.|
|[Installer](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (est)|Place une ressource dans un emplacement et l’initialise si vous le souhaitez. Ce verbe est associé à `Uninstall`.|Pour cette action, ne pas un verbe d’utilisation tels que le programme d’installation.|
|[Invoke](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Exécute une action, telles que l’exécution d’une commande ou une méthode.|Pour cette action, n’utilisez pas des verbes tels que le démarrage ou d’exécution.|
|[Inscrire](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|Crée une entrée pour une ressource dans un référentiel comme une base de données. Ce verbe est associé à `Unregister`.||
|[Demande](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (rq)|Demande une ressource ou demande des autorisations.||
|[Redémarrez](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (rt)|Arrête une opération avant de la lancer à nouveau. Par exemple, le `Restart-Service` applet de commande arrête et redémarre un service.|Pour cette action, n’utilisez pas un verbe de recyclage.|
|[Reprise](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Démarre une opération qui a été suspendue. Par exemple, le `Resume-Service` applet de commande démarre un service qui a été suspendu. Ce verbe est associé à `Suspend`.||
|[Démarrer](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Lance une opération. Par exemple, le `Start-Service` applet de commande démarre un service. Ce verbe est associé à `Stop`.|Pour cette action, n’utilisez pas des verbes tels que le lancement, de lancer ou de démarrage.|
|[Arrêter](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|Interrompt une activité. Ce verbe est associé à `Start`.|Pour cette action, ne pas utiliser verbes tels que de fin, Kill, Terminate, ou annuler.|
|[Envoyer](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|Présente une ressource pour l’approbation.|Pour cette action, n’utilisez pas un verbe, par exemple Post.|
|[Suspendre](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|Suspend une activité. Par exemple, le `Suspend-Service` applet de commande suspend un service. Ce verbe est associé à `Resume`.|Pour cette action, n’utilisez pas un verbe de Pause.|
|[Désinstaller](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (us)|Supprime une ressource à partir d’un emplacement indiqué. Ce verbe est associé à `Install`.||
|[Annuler l’inscription](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (vos)|Supprime l’entrée pour une ressource à partir d’un référentiel. Ce verbe est associé à `Register`.|Pour cette action, n’utilisez pas un verbe telles que supprimer.|
|[Attente](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Interrompt une opération jusqu'à ce qu’un événement spécifié se produit. Par exemple, le `Wait-Job` applet de commande suspend les opérations jusqu'à ce qu’une ou plusieurs tâches en arrière-plan sont terminées.|Pour cette action, n’utilisez pas des verbes tels que la mise en veille ou de Pause.|

## <a name="security-verbs"></a>Verbes de sécurité

PowerShell utilise le [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) classe pour définir les actions qui s’appliquent à la sécurité.
Le tableau suivant répertorie la plupart des verbes définis.

|Verbe (alias)|Action|Commentaires|
|--------------------|------------|--------------|
|[Bloc](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|Limite l’accès à une ressource. Ce verbe est associé à `Unblock`.|Pour cette action, n’utilisez pas des verbes tels qu’empêcher, de limiter ou refuser.|
|[Grant](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Autorise l’accès à une ressource. Ce verbe est associé à `Revoke`.|Pour cette action, n’utilisez pas des verbes tels qu’autoriser ou activer.|
|[Protéger](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|Protège une ressource à partir d’attaque ou de perte. Ce verbe est associé à `Unprotect`.|Pour cette action, n’utilisez pas des verbes tels que Encrypt, sauvegarde ou joint.|
|[Révoquer](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (Kit de ressources)|Spécifie une action qui n’autorise pas l’accès à une ressource. Ce verbe est associé à `Grant`.|Pour cette action, n’utilisez pas des verbes tels que de supprimer ou désactiver.|
|[Débloquer](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|Supprime les restrictions à une ressource. Ce verbe est associé à `Block`.|Pour cette action, n’utilisez pas des verbes tels que Clear ou autoriser.|
|[Déprotéger](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (jusqu'à)|Supprime les dispositifs de protection d’une ressource qui ont été ajoutées pour l’empêcher d’attaque ou de perte. Ce verbe est associé à `Protect`.|Pour cette action, n’utilisez pas des verbes tels que déchiffrer ou Unseal.|

## <a name="other-verbs"></a>Autres verbes

PowerShell utilise le [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) classe pour définir des noms de verbe canonique qui ne tiennent pas dans une catégorie de nom verbe spécifiques telles que le commun communications, données, du cycle de vie ou des noms de verbe de sécurité verbes.

|Verbe (alias)|Action|Commentaires|
|--------------------|------------|--------------|
|[Utilisez](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Utilise ou inclut une ressource pour faire quelque chose.||

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Déclaration de l’applet de commande](./cmdlet-class-declaration.md)

[Guide de programmation pour Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md)

[Interpréteur de commandes Windows PowerShell SDK](../windows-powershell-reference.md)
