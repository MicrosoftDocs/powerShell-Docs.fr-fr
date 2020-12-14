---
ms.date: 09/07/2018
ms.topic: reference
title: Verbes approuvés pour les commandes PowerShell
description: Verbes approuvés pour les commandes PowerShell
ms.openlocfilehash: fc1ff989ae86862e0f9cc24d8bcba2ff02ef68cc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355100"
---
# <a name="approved-verbs-for-powershell-commands"></a>Verbes approuvés pour les commandes PowerShell

PowerShell utilise une paire verbe-nom pour les noms des applets de commande et pour leurs classes .NET dérivées.
La partie verbe du nom identifie l’action effectuée par l’applet de commande. La partie substantif du nom identifie l’entité sur laquelle l’action est effectuée. Par exemple, l’applet de commande `Get-Command` récupère toutes les commandes qui sont inscrites dans PowerShell.

> [!NOTE]
> PowerShell utilise le terme _verbe_ pour décrire un mot qui implique une action, même si ce mot n’est pas un verbe standard en anglais. Par exemple, le terme _New_ est un nom de verbe PowerShell valide, car il implique une action, même s’il ne s’agit pas d’un verbe en langue anglaise.

Chaque verbe approuvé a un _préfixe d’alias_ correspondant défini. Nous utilisons ce préfixe d’alias dans des alias pour les commandes qui utilisent ce verbe. Par exemple, le préfixe d’alias pour `Import` est `ip` et, en conséquence, l’alias pour `Import-Module` est `ipmo`. Il s’agit d’une recommandation, mais pas d’une règle ; il n’est pas nécessaire de la respecter en particulier pour les alias de commande imitant des commandes bien connues d’autres environnements.

## <a name="verb-naming-recommendations"></a>Recommandations relatives au nommage des verbes

Les recommandations suivantes vous aideront à choisir un verbe approprié pour votre applet de commande, afin de garantir la cohérence entre les applets de commande que vous créez, celles fournies par PowerShell et celles conçues par d’autres personnes.

- Utilisez l’un des noms de verbes prédéfinis fournis par PowerShell.
- Utilisez le verbe pour décrire l’étendue générale de l’action, et des paramètres pour affiner l’action de l’applet de commande.
- N’utilisez pas un synonyme d’un verbe approuvé. Par exemple, utilisez toujours `Remove` ; n’utilisez jamais `Delete` ou `Eliminate`.
- Utilisez uniquement la forme de chaque verbe qui est listée dans cette rubrique. Par exemple, utilisez `Get`, mais n’utilisez pas `Getting` ou `Gets`.
- N’utilisez pas les verbes ou alias réservés suivants. Le langage PowerShell ou quelques rares applets de commande utilisent ces verbes dans des circonstances exceptionnelles.
  - ForEach (foreach)
  - [Format](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f) : organise des objets sous une forme ou dans une disposition spécifiée.
  - [Group](/dotnet/api/System.Management.Automation.VerbsData.Group) (gp) : organise ou associe une ou plusieurs ressources.
  - [Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)
  - Sort (sr)
  - Tee (te)
  - Where (wh)

Vous pouvez obtenir une liste complète des verbes avec l’applet de commande `Get-Verb`.

## <a name="similar-verbs-for-different-actions"></a>Verbes similaires pour des actions différentes

Les verbes similaires suivants représentent des actions différentes.

### <a name="new-vs-set"></a>New vs. Set

Utilisez le verbe `New` pour créer une ressource. Utilisez le verbe `Set` pour modifier une ressource existante, éventuellement la créer si elle n’existe pas, comme dans `Set-Variable`.

### <a name="find-vs-search"></a>Find vs. Search

Utilisez le verbe `Find` pour rechercher un objet. Utilisez le verbe `Search` pour créer une référence à une ressource dans un conteneur.

### <a name="get-vs-read"></a>Get vs. Read

Utilisez le verbe `Get` pour obtenir des informations sur une ressource (par exemple un fichier) ou pour obtenir un objet avec lequel vous pouvez ultérieurement accéder à la ressource. Utilisez le verbe `Read` pour ouvrir une ressource et extraire des informations contenues dedans.

### <a name="invoke-vs-start"></a>Invoke vs. Start

Utilisez le verbe `Invoke` pour effectuer des opérations synchrones, comme exécuter une commande et attendre qu’elle se termine. Utilisez le verbe `Start` pour commencer des opérations asynchrones, par exemple démarrer un processus autonome.

### <a name="ping-vs-test"></a>Ping vs. Test

Utilisez le verbe `Test`.

## <a name="common-verbs"></a>Verbes courants

PowerShell utilise la classe d’énumération [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) pour définir des actions génériques qui peuvent s’appliquer à presque n’importe quelle applet de commande. Le tableau suivant liste la plupart des verbes définis.

|Verbe (alias)|Action|Synonymes à éviter|
|--------------------|------------|--------------|
|[Add](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Ajoute une ressource à un conteneur, ou attache un élément à un autre élément. Par exemple, l’applet de commande `Add-Content` ajoute du contenu à un fichier. Ce verbe est associé à `Remove`.|Append, Attach, Concatenate, Insert|
|[Clear](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Supprime toutes les ressources d’un conteneur, mais ne supprime pas le conteneur. Par exemple, l’applet de commande `Clear-Content` supprime le contenu d’un fichier, mais ne supprime pas le fichier.|Flush, Erase, Release, Unmark, Unset, Nullify|
|[Close](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|Change l’état d’une ressource afin de la rendre inaccessible, indisponible ou inutilisable. Ce verbe est associé à `Open.`||
|[Copy](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|Copie une ressource vers un autre nom ou un autre conteneur. Par exemple, l’applet de commande `Copy-Item` copie un élément (tel qu’un fichier) d’un emplacement dans le magasin de données vers un autre emplacement.|Duplicate, Clone, Replicate, Sync|
|[Enter](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|Spécifie une action qui permet à l’utilisateur de se déplacer vers une ressource. Par exemple, l’applet de commande `Enter-PSSession` place l’utilisateur dans une session interactive. Ce verbe est associé à `Exit`.|Push, Into|
|[Exit](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|Définit le dernier contexte utilisé comme environnement ou contexte actuel. Par exemple, l’applet de commande `Exit-PSSession` place l’utilisateur dans la session qui a été utilisée pour démarrer la session interactive. Ce verbe est associé à `Enter`.|Pop, Out|
|[Find](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|Recherche un objet dans un conteneur inconnu, implicite, facultatif ou spécifié.|Search|
|[Get](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Spécifie une action qui récupère une ressource. Ce verbe est associé à `Set`.|Read, Open, Cat, Type, Dir, Obtain, Dump, Acquire, Examine, Find, Search|
|[Hide](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Rend une ressource indétectable. Par exemple, une applet de commande dont le nom comprend le verbe Hide peut masquer un service aux yeux d’un utilisateur. Ce verbe est associé à `Show`.|Block|
|[Join](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Combine des ressources en une seule ressource. Par exemple, l’applet de commande `Join-Path` combine un chemin avec l’un de ses chemins enfants afin de créer un chemin unique. Ce verbe est associé à `Split`.|Combine, Unite, Connect, Associate|
|[Lock](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|Sécurise une ressource. Ce verbe est associé à `Unlock`.|Restrict, Secure|
|[Move](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Déplace une ressource d’un emplacement à un autre. Par exemple, l’applet de commande `Move-Item` déplace un élément d’un emplacement dans le magasin de données vers un autre emplacement.|Transfer, Name, Migrate|
|[New](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Crée une ressource. (Le verbe `Set` peut également être utilisé lors de la création d’une ressource qui comprend des données, comme dans l’applet de commande `Set-Variable`.)|Create, Generate, Build, Make, Allocate|
|[Open](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|Change l’état d’une ressource afin de la rendre accessible, disponible ou utilisable. Ce verbe est associé à `Close`.||
|[Optimize](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|Augmente l’efficacité d’une ressource.||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Supprime un élément du haut d’une pile. Par exemple, l’applet de commande `Pop-Location` définit comme emplacement actuel le dernier emplacement placé sur la pile.||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|Ajoute un élément en haut d’une pile. Par exemple, l’applet de commande `Push-Location` place l’emplacement actuel sur la pile.||
|[Redo](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|Réinitialise une ressource à l’état qui a été annulé.||
|[Remove](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Supprime une ressource d’un conteneur. Par exemple, l’applet de commande `Remove-Variable` supprime une variable et sa valeur. Ce verbe est associé à `Add`.|Clear, Cut, Dispose, Discard, Erase|
|[Rename](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (rn)|Change le nom d’une ressource. Par exemple, l’applet de commande `Rename-Item`, qui sert à accéder à des données stockées, change le nom d’un élément dans le magasin de données.|Change|
|[Reset](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (rs)|Restaure une ressource à son état d’origine.||
|[Resize](/dotnet/api/System.Management.Automation.VerbsCommon.Resize)(rz)|Change la taille d’une ressource.||
|[Search](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|Crée une référence à une ressource dans un conteneur.|Find, Locate|
|[Select](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|Localise une ressource dans un conteneur. Par exemple, l’applet de commande `Select-String` recherche du texte dans des chaînes et des fichiers.|Find, Locate|
|[Set](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Remplace des données sur une ressource existante, ou crée une ressource qui contient des données. Par exemple, l’applet de commande `Set-Date` change l’heure système sur l’ordinateur local. (Le verbe `New` peut également être utilisé pour créer une ressource.) Ce verbe est associé à `Get`.|Write, Reset, Assign, Configure|
|[Show](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|Rend une ressource visible par l’utilisateur. Ce verbe est associé à `Hide`.|Display, Produce|
|[Skip](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (sk)|Ignore une ou plusieurs ressources ou points dans une séquence.|Bypass, Jump|
|[Split](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (sl)|Sépare les parties d’une ressource. Par exemple, l’applet de commande `Split-Path` retourne différentes parties d’un chemin. Ce verbe est associé à `Join`.|Separate|
|[Step](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|Passe au point ou à la ressource suivant(e) dans une séquence.||
|[Switch](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|Spécifie une action qui alterne entre deux ressources, telles que le changement entre deux emplacements, responsabilités ou états.||
|[Undo](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (un)|Définit une ressource à son état précédent.||
|[Unlock](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (uk)|Libère une ressource qui a été verrouillée. Ce verbe est associé à `Lock`.|Release, Unrestrict, Unsecure|
|[Watch](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc)|Inspecte ou supervise en permanence une ressource afin de détecter les modifications.||

## <a name="communications-verbs"></a>Verbes de communication

PowerShell utilise la classe [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) pour définir des actions qui s’appliquent aux communications. Le tableau suivant liste la plupart des verbes définis.

|Verbe (alias)|Action|Synonymes à éviter|
|--------------------|------------|--------------|
|[Connect](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (cc)|Crée un lien entre une source et une destination. Ce verbe est associé à `Disconnect`.|Join, Telnet|
|[Disconnect](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|Rompt le lien entre une source et une destination. Ce verbe est associé à `Connect`.|Break, Logoff|
|[Read](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|Acquiert des informations à partir d’une source. Ce verbe est associé à `Write`.|Acquire, Prompt, Get|
|[Receive](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|Accepte les informations envoyées à partir d’une source. Ce verbe est associé à `Send`.|Read, Accept, Peek|
|[Send](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (sd)|Envoie des informations à une destination. Ce verbe est associé à `Receive`.|Put, Broadcast, Mail, Fax|
|[Write](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (wr)|Ajoute des informations à une cible. Ce verbe est associé à `Read`.|Put, Print|

## <a name="data-verbs"></a>Verbes de données

PowerShell utilise la classe [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) pour définir des actions qui s’appliquent à la gestion des données. Le tableau suivant liste la plupart des verbes définis.

|Nom du verbe (alias)|Action|Synonymes à éviter|
|-------------------------|------------|--------------|
|[Backup](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|Stocke des données en les répliquant.|Save, Burn, Replicate, Sync|
|[Checkpoint](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|Crée un instantané de l’état actuel des données ou de sa configuration.|Diff|
|[Compare](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|Évalue les données d’une ressource par rapport aux données d’une autre ressource.|Diff|
|[Compress](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Compacte les données d’une ressource. Associé à `Expand`.|Compact|
|[Convert](/dotnet/api/System.Management.Automation.VerbsData.Convert) (cv)|Change les données d’une représentation en une autre lorsque l’applet de commande prend en charge la conversion bidirectionnelle ou la conversion entre plusieurs types de données.|Change, Resize, Resample|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|Convertit un type principal d’entrée (le substantif de l’applet de commande indique l’entrée) en un ou plusieurs types de sortie pris en charge.|Export, Output, Out|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|Convertit à partir d’un ou plusieurs types d’entrée en un type de sortie principal (le substantif de l’applet de commande indique le type de sortie).|Import, Input, In|
|[Dismount](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|Détache une entité nommée d’un emplacement. Ce verbe est associé à `Mount`.|Unmount, Unlink|
|[Edit](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Modifie des données existantes en ajoutant ou en supprimant du contenu.|Change, Update, Modify|
|[Expand](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Restaure l’état d’origine des données d’une ressource qui a été compressée. Ce verbe est associé à `Compress`.|Explode, Uncompress|
|[Export](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|Encapsule l’entrée principale dans un magasin de données persistant, tel qu’un fichier, ou dans un format d’échange. Ce verbe est associé à `Import`.|Extract, Backup|
|[Import](/dotnet/api/System.Management.Automation.VerbsData.Import) (ip)|Crée une ressource à partir de données stockées dans un magasin de données persistant (tel qu’un fichier) ou dans un format d’échange. Par exemple, l’applet de commande `Import-CSV` importe des données à partir d’un fichier de valeurs séparées par des virgules (CSV) vers des objets qui peuvent être utilisés par d’autres applets de commande. Ce verbe est associé à `Export`.|BulkLoad, Load|
|[Initialize](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Prépare une ressource en vue de l’utiliser, et lui affecte un état par défaut.|Erase, Init, Renew, Rebuild, Reinitialize, Setup|
|[Limit](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Applique des contraintes à une ressource.|Quota|
|[Merge](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Crée une ressource unique à partir de plusieurs ressources.|Combine, Join|
|[Mount](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|Attache une entité nommée à un emplacement. Ce verbe est associé à `Dismount`.|Connect|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Envoie des données à partir de l’environnement. Par exemple, l’applet de commande `Out-Printer` envoie des données à une imprimante.||
|[Publish](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|Met une ressource à la disposition d’autres utilisateurs. Ce verbe est associé à `Unpublish`.|Deploy, Release, Install|
|[Restore](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|Affecte à une ressource un état prédéfini, tel qu’un état défini par `Checkpoint`. Par exemple, l’applet de commande `Restore-Computer` démarre une restauration du système sur l’ordinateur local.|Repair, Return, Undo, Fix|
|[Save](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|Préserve des données afin d’éviter toute perte.||
|[Sync](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|Garantit que deux ressources ou plus sont dans le même état.|Replicate, Coerce, Match|
|[Unpublish](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (ub)|Rend une ressource inaccessible à d’autres personnes. Ce verbe est associé à `Publish`.|Uninstall, Revert, Hide|
|[Update](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|Met à jour une ressource afin de maintenir son état, son exactitude ou sa conformité. Par exemple, l’applet de commande `Update-FormatData` met à jour et ajoute des fichiers de mise en forme à la console PowerShell actuelle.|Refresh, Renew, Recalculate, Re-index|

## <a name="diagnostic-verbs"></a>Verbes de diagnostic

PowerShell utilise la classe [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) pour définir des actions qui s’appliquent à des diagnostics. Le tableau suivant liste la plupart des verbes définis.

|Verbe (alias)|Action|Synonymes à éviter|
|--------------------|------------|--------------|
|[Debug](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (db)|Examine une ressource pour diagnostiquer les problèmes opérationnels.|Diagnose|
|[Measure](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|Identifie les ressources qui sont consommées par une opération spécifiée, ou récupère des statistiques sur une ressource.|Calculate, Determine, Analyze|
|[Repair](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|Restaure une ressource dans une condition utilisable.|Fix, Restore|
|[Resolve](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|Mappe une représentation abrégée d’une ressource à une représentation plus complète.|Expand, Determine|
|[Test](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Vérifie l’opération ou la cohérence d’une ressource.|Diagnose, Analyze, Salvage, Verify|
|[Trace](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|Effectue le suivi des activités d’une ressource.|Track, Follow, Inspect, Dig|

## <a name="lifecycle-verbs"></a>Verbes de cycle de vie

PowerShell utilise la classe [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) pour définir des actions qui s’appliquent au cycle de vie d’une ressource. Le tableau suivant liste la plupart des verbes définis.

|Verbe (alias)|Action|Synonymes à éviter|
|--------------------|------------|--------------|
|[Approve](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|Confirme ou accepte l’état d’une ressource ou d’un processus.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (as)|Affirme l’état d’une ressource.|Certify|
|[Build](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|Crée un artefact (généralement un fichier binaire ou un document) à partir d’un ensemble de fichiers d’entrée (généralement du code source ou des documents déclaratifs). Ce verbe a été ajouté dans PowerShell 6.||
|[Complete](/dotnet/api/system.management.automation.host.buffercelltype) (cp)|Conclut une opération.||
|[Confirm](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|Accuse réception, vérifie ou valide l’état d’une ressource ou d’un processus.|Acknowledge, Agree, Certify, Validate, Verify|
|[Deny](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|Refuse, objecte, bloque ou s’oppose à l’état d’une ressource ou d’un processus.|Block, Object, Refuse, Reject|
|[Deploy](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|Envoie une application, un site web ou une solution à une ou plusieurs cibles distantes de manière à ce qu’un consommateur de cette solution puisse y accéder une fois le déploiement terminé. Ce verbe a été ajouté dans PowerShell 6.||
|[Disable](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Configure une ressource à un état indisponible ou inactif. Par exemple, l’applet de commande `Disable-PSBreakpoint` rend un point d’arrêt inactif. Ce verbe est associé à `Enable`.|Halt, Hide|
|[Enable](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Configure une ressource à un état disponible ou actif. Par exemple, l’applet de commande `Enable-PSBreakpoint` rend un point d’arrêt actif. Ce verbe est associé à `Disable`.|Start, Begin|
|[Install](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (is)|Place une ressource dans un emplacement et l’initialise éventuellement. Ce verbe est associé à `Uninstall`.|Setup|
|[Invoke](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Effectue une action, telle que l’exécution d’une commande ou d’une méthode.|Run, Start|
|[Register](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|Crée une entrée pour une ressource dans un référentiel tel qu’une base de données. Ce verbe est associé à `Unregister`.||
|[Request](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (rq)|Demande une ressource ou des autorisations.||
|[Restart](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (rt)|Arrête une opération, puis la redémarre. Par exemple, l’applet de commande `Restart-Service` arrête, puis démarre un service.|Recycle|
|[Resume](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Démarre une opération qui a été suspendue. Par exemple, l’applet de commande `Resume-Service` démarre un service qui a été suspendu. Ce verbe est associé à `Suspend`.||
|[Start](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Lance une opération. Par exemple, l’applet de commande `Start-Service` démarre un service. Ce verbe est associé à `Stop`.|Launch, Initiate, Boot|
|[Stop](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|Interrompt une activité. Ce verbe est associé à `Start`.|End, Kill, Terminate, Cancel|
|[Submit](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|Présente une ressource pour approbation.|Post|
|[Suspend](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|Suspend une activité. Par exemple, l’applet de commande `Suspend-Service` suspend un service. Ce verbe est associé à `Resume`.|Pause|
|[Uninstall](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (us)|Supprime une ressource d’un emplacement indiqué. Ce verbe est associé à `Install`.||
|[Unregister](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (ur)|Supprime l’entrée d’une ressource d’un référentiel. Ce verbe est associé à `Register`.|Remove|
|[Wait](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Suspend une opération jusqu’à ce qu’un événement spécifié se produise. Par exemple, l’applet de commande `Wait-Job` suspend les opérations jusqu’à ce qu’un ou plusieurs des travaux en arrière-plan soient terminée.|Sleep, Pause|

## <a name="security-verbs"></a>Verbes de sécurité

PowerShell utilise la classe [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) pour définir des actions qui s’appliquent à la sécurité. Le tableau suivant liste la plupart des verbes définis.

|Verbe (alias)|Action|Synonymes à éviter|
|--------------------|------------|--------------|
|[Block](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|Restreint l’accès à une ressource. Ce verbe est associé à `Unblock`.|Prevent, Limit, Deny|
|[Grant](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Autorise l’accès à une ressource. Ce verbe est associé à `Revoke`.|Allow, Enable|
|[Protect](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|Protège une ressource contre les attaques ou pertes. Ce verbe est associé à `Unprotect`.|Encrypt, Safeguard, Seal|
|[Revoke](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (rk)|Spécifie une action qui n’autorise pas l’accès à une ressource. Ce verbe est associé à `Grant`.|Remove, Disable|
|[Unblock](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|Supprime les restrictions applicables à une ressource. Ce verbe est associé à `Block`.|Clear, Allow|
|[Unprotect](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (up)|Supprime les protections d’une ressource qui ont été ajoutées afin de la protéger contre les attaques ou pertes. Ce verbe est associé à `Protect`.|Decrypt, Unseal|

## <a name="other-verbs"></a>Autres verbes

PowerShell utilise la classe [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) pour définir des noms de verbes canoniques qui ne correspondent à aucune catégorie de nom de verbe spécifique (comme les noms de verbes courants, de communication, de données, de cycle de vie ou de sécurité).

|Verbe (alias)|Action|Synonymes à éviter|
|--------------------|------------|--------------|
|[Use](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Utilise ou inclut une ressource pour effectuer une opération.||

## <a name="see-also"></a>Voir aussi

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)
- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)
- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)
- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)
- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)
- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)
- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)
- [Déclaration d’applet de commande](./cmdlet-class-declaration.md)
- [Guide de programmation pour Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md)
- [Kit SDK Windows PowerShell](../windows-powershell-reference.md)
