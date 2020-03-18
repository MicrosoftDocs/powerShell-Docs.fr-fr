---
title: Nouveautés de PowerShell 7.0
description: Nouvelles fonctionnalités et modifications de PowerShell 7.0
ms.date: 03/04/2020
ms.openlocfilehash: 6915bb70d6e54da86d2b935e3feed8d7f3770ba9
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404999"
---
# <a name="whats-new-in-powershell-70"></a>Nouveautés de PowerShell 7.0

PowerShell 7.0 est une édition de multiplateforme open source (Windows, macOS et Linux) conçue pour gérer des environnements hétérogènes et le cloud hybride.

Dans cette version, nous présentons plusieurs fonctionnalités, notamment les suivantes :

- Parallélisation de pipeline avec `ForEach-Object -Parallel`
- Nouveaux opérateurs :
  - Opérateur ternaire : `a ? b : c`
  - Opérateurs de chaîne de pipeline : `||` et `&&`
  - Opérations conditionnelles Null : `??` et `??=`
- Un affichage des erreurs simplifié et dynamique ainsi qu’une cmdlet `Get-Error` pour étudier plus facilement les erreurs
- Une couche de compatibilité qui permet aux utilisateurs d’importer des modules dans une session Windows PowerShell implicite
- Notifications automatiques en cas de nouvelles versions
- La possibilité d’appeler des ressources DSC directement à partir de PowerShell 7 (stade expérimental)

Pour afficher une liste complète des fonctionnalités et des correctifs, consultez les [journaux des modifications](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).

## <a name="where-can-i-install-powershell"></a>Où puis-je installer PowerShell ?

PowerShell 7 prend actuellement en charge les systèmes d’exploitation suivants sur x64, notamment :

- Windows 8.1 et 10
- Windows Server 2012, 2012 R2, 2016 et 2019
- macOS 10.13+
- Red Hat Enterprise Linux (RHEL) / CentOS 7
- Fedora 30+
- Debian 9
- Ubuntu LTS 16.04+
- Alpine Linux 3.8+

En outre, PowerShell 7.0 prend en charge les versions ARM32 et ARM64 de Debian, Ubuntu et ARM64 Alpine Linux.

Consultez les instructions d’installation pour votre système d’exploitation par défaut [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) ou [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).

Bien qu’ils ne soit pas officiellement pris en charge, la communauté a également fourni des packages pour [Arch](https://aur.archlinux.org/packages/powershell/) et Kali Linux.

> [!NOTE]
> Debian 10 et CentOS 8 ne prennent actuellement pas en charge la communication à distance WinRM. Pour plus d’informations sur la configuration de la communication à distance basée sur SSH, consultez [Communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).

Pour plus d’informations à jour sur les systèmes d’exploitation pris en charge et le cycle de vie de support, consultez le [cycle de vie du support PowerShell](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).

## <a name="running-powershell-7"></a>Exécution de PowerShell 7

PowerShell 7 s’installe dans un nouveau répertoire et s’exécute côte à côte avec Windows PowerShell 5.1. Pour PowerShell Core 6.x, PowerShell 7 est une mise à niveau sur place qui supprime PowerShell Core 6.x.

- PowerShell 7 est installé sur `%programfiles%\PowerShell\7`
- Le dossier `%programfiles%\PowerShell\7` est ajouté à `$env:PATH`

Les packages d’installation PowerShell 7 mettent à niveau les versions précédentes de PowerShell Core 6.x :

- PowerShell Core 6.x sur Windows : `%programfiles%\PowerShell\6` est remplacé par `%programfiles%\PowerShell\7`
- Linux : `/opt/microsoft/powershell/6` est remplacée par `/opt/microsoft/powershell/7`
- macOS : `/usr/local/microsoft/powershell/6` est remplacée par `/usr/local/microsoft/powershell/7`

> [!NOTE]
> Dans Windows PowerShell, l’exécutable permettant de lancer PowerShell est nommé `powershell.exe`. Dans la version 6 et les versions ultérieures, l’exécutable est modifié pour prendre en charge l’exécution côte à côte. Le nouvel exécutable permettant de lancer PowerShell 7 est `pwsh.exe`. Les builds préliminaires sont conservées en tant que `pwsh-preview` au lieu de `pwsh` sous le répertoire 7-préversion.

## <a name="improved-backwards-compatibility-with-windows-powershell"></a>Compatibilité descendante avec Windows PowerShell améliorée

PowerShell 7.0 marque un passage à .NET Core 3.1, ce qui permet d’améliorer significativement la compatibilité descendante avec les modules Windows PowerShell existants. Ceci inclut de nombreux modules sur Windows qui nécessitent une fonctionnalité GUI comme `Out-GridView` et `Show-Command`, ainsi que de nombreux modules de gestion des rôles fournis avec Windows.

Pour Windows, un nouveau paramètre de commutateur **UseWindowsPowerShell** est ajouté à `Import-Module`. Ce commutateur crée un module proxy dans PowerShell 7, qui utilise un processus Windows PowerShell local pour exécuter implicitement toutes les cmdlets contenues dans ce module. Pour plus d’informations sur [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).

Pour plus d’informations sur les modules Microsoft fonctionnant avec PowerShell 7.0, consultez le [tableau de compatibilité des modules](https://aka.ms/PSModuleCompat).

## <a name="parallel-execution-added-to-foreach-object"></a>Exécution parallèle ajoutée à ForEach-Object

La cmdlet `ForEach-Object`, qui itère des éléments dans une collection, dispose maintenant d’un parallélisme intégré avec le nouveau paramètre **Parallèle**.

Par défaut, les blocs de scripts parallèles utilisent le répertoire de travail actuel de l’appelant qui a démarré les tâches parallèles.

Dans cet exemple, 50 000 entrées de 5 journaux système sont récupérées sur un ordinateur local Windows :

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

Le paramètre **Parallèle** spécifie le bloc de script exécuté en parallèle pour chaque nom du journal d’entrée.

Le nouveau paramètre **ThrottleLimit** limite le nombre de blocs de scripts exécutés en parallèle à un moment donné. La valeur par défaut est 5.

Utilisez la variable `$_` pour représenter l'objet d’entrée actuel dans le bloc de script. Utilisez l’étendue `$using:` pour transférer des références de variable vers le bloc de script en cours d’exécution.

Pour plus d’informations sur [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).

## <a name="ternary-operator"></a>Opérateur ternaire

PowerShell 7.0 introduit un opérateur ternaire qui se comporte comme une instruction `if-else` simplifiée.
L’opérateur ternaire de PowerShell est étroitement modélisé à partir de la syntaxe C# de l’opérateur ternaire :

```
<condition> ? <if-true> : <if-false>
```

L’expression de condition est toujours évaluée et son résultat est converti en **booléenne** pour déterminer la prochaine branche à évaluer :

- L’expression `<if-true>` est exécutée si l’expression `<condition>` a la valeur true
- L’expression `<if-false>` est exécutée si l’expression `<condition>` a la valeur false

Par exemple :

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

Dans cet exemple, si le chemin existe, **Le chemin existe** s’affiche. Si le chemin n’existe pas, **Chemin introuvable** s’affiche.

Pour plus d’informations [À propos de Si](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).

## <a name="pipeline-chain-operators"></a>Opérateurs de chaîne de pipeline

PowerShell 7 implémente les opérateurs `&&` et `||` pour attacher des pipelines de manière conditionnelle. Ces opérateurs sont connus dans PowerShell en tant qu’« opérateurs de chaîne de pipeline » et sont similaires à des listes AND et OR dans des interpréteurs de commandes tels que **Bash** et **Zsh**, de même que des symboles de traitement conditionnel dans l’interface de commande Windows (**cmd.exe**).

L’opérateur `&&` exécute le pipeline droit si l’exécution du pipeline gauche a réussi. Inversement, l’opérateur `||` exécute le pipeline droit si l’exécution du pipeline gauche a échoué.

> [!NOTE]
> Ces opérateurs utilisent les variables `$?` et `$LASTEXITCODE` pour déterminer si un pipeline a échoué. Cela vous permet de les utiliser avec des commandes natives, et pas seulement avec des cmdlet ou des fonctions.

Ici, la première commande réussit et la deuxième commande est exécutée :

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

Ici, la première commande échoue et la deuxième commande n’est pas exécutée :

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

Ici, la première commande réussit, la deuxième commande n’est pas exécutée :

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

Ici, la première commande échoue, donc la deuxième commande est exécutée :

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

Pour plus d'informations [À propos des opérateurs de chaîne de pipeline](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).

## <a name="null-coalescing-assignment-and-conditional-operators"></a>Coalesence Null, assignation et opérateurs conditionnels

PowerShell 7 inclut l’opérateur de coalescence Null `??`, l’assignation conditionnelle Null `??=` et les opérateurs d’accès conditionnel des membres `?.` et `?[]`.

### <a name="null-coalescing-operator-"></a>Opérateur de coalescence Null ??

L’opérateur de coalescence Null `??` retourne la valeur de son opérande gauche s’il n’est pas Null.
Dans le cas contraire, il évalue l’opérande droit et retourne son résultat. L’opérateur `??` n’évalue pas son opérande droit si l’opérande gauche a la valeur non Null.

```powershell
$x = $null
$x ?? 100
100
```

Dans l’exemple suivant, l’opérande droit n’est pas évalué :

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a>Opérateur d’assignation conditionnelle Null ??=

L’opérateur d’assignation conditionnelle Null `??=` assigne la valeur de son opérande droit à son opérande gauche uniquement si l’opérande gauche a la valeur Null. L’opérateur `??=` n’évalue pas son opérande droit si l’opérande gauche a la valeur non null.

```powershell
$x = $null
$x ??= 100
$x
100
```

Dans l’exemple suivant, l’opérande droit n’est pas évalué :

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a>Opérateurs d’accès conditionnel des membres Null ?. et ?[] (Expérimental)

> [!NOTE]
> Il s’agit d’une fonctionnalité expérimentale nommée **PSNullConditionalOperators**. En savoir plus [À Propos des fonctionnalités expérimentales](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).

Un opérateur conditionnel Null n’autorise les membres, `?.`, ou les éléments, `?[]`, à accéder à son opérande que si cet opérande a la valeur non Null ; sinon, il retourne la valeur Null.

> [!NOTE]
> Étant donné que PowerShell permet à `?` de faire partie du nom de la variable, la spécification formelle du nom de la variable est requise pour l’utilisation de ces opérateurs. Il est donc nécessaire d’utiliser `{}` autour des noms de variables comme `${a}` ou lorsque `?` fait partie du nom de la variable `${a?}`.

Dans l’exemple suivant, la valeur de la propriété de membre **État** est retournée :

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

L’exemple suivant retourne la valeur Null, sans essayer d’accéder au nom du membre **État** :

```powershell
$service = $Null
${Service}?.status
```

De même, avec `?[]`, la valeur de l’élément est retournée :

```powershell
$a = 1..10
${a}?[0]
1
```

Et lorsque l’opérande a la valeur Null, l’élément n’est pas accessible et la valeur Null est retournée :

```powershell
$a = $null
${a}?[0]
```

Pour plus d’informations [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).

## <a name="new-view-conciseview-and-cmdlet-get-error"></a>Nouvelle vue ConciseView et cmdlet Get-Error

L’affichage des messages d’erreur a été amélioré pour améliorer la lisibilité des erreurs de script et interactives avec un nouvel affichage par défaut **ConciseView**. Les affichages peuvent être sélectionnées par l’utilisateur via la variable de préférence `$ErrorView`.

Avec **ConciseView**, si une erreur ne provient pas d’un script ou d’un analyseur, le message d’erreur a une seule ligne :

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

Si l’erreur se produit pendant l’exécution du script ou s’il s’agit d’une erreur d’analyse, PowerShell retourne un message d’erreur de plusieurs lignes contenant l’erreur, un pointeur et un message d’erreur qui indique l’emplacement de l’erreur dans cette ligne. Si le terminal ne prend pas en charge les séquences d’échappement de couleur ANSI (VT100), les couleurs ne sont pas affichées.

![Affichage d’erreur à partir d’un script](./media/What-s-New-in-PowerShell-70/myscript-error.png)

L’affichage par défaut dans PowerShell 7 est **ConciseView**. L’affichage par défaut précédent était **NormalView** et peut être sélectionné par l’utilisateur en définissant la variable de préférence `$ErrorView`.

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> Une nouvelle propriété **ErrorAccentColor** est ajoutée à `$Host.PrivateData` pour prendre en charge la modification de la couleur d’accentuation du message d’erreur.

Une nouvelle cmdlet `Get-Error` fournit un affichage détaillé de l’erreur complète si vous le souhaitez.
Par défaut, la cmdlet affiche les détails complets, notamment les exceptions internes, de la dernière erreur qui s’est produite.

![Afficher à partir de la Get-Error](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

La cmdlet `Get-Error` prend en charge l’entrée du pipeline à l’aide de la variable intégrée `$Error`.
`Get-Error` affiche toutes les erreurs communiquées.

```powershell
$Error | Get-Error
```

La cmdlet `Get-Error` prend en charge le paramètre **le plus récent**, ce qui vous permet de spécifier le nombre d’erreurs de la session active que vous souhaitez afficher.

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

Pour plus d’informations sur [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).

## <a name="new-version-notification"></a>Notification en cas de nouvelle version

PowerShell 7 utilise des notifications de mise à jour pour avertir les utilisateurs de l’existence de mises à jour de PowerShell.
Une fois par jour, PowerShell interroge un service en ligne pour déterminer si une version plus récente est disponible.

> [!NOTE]
> La vérification des mises à jour a lieu pendant la première session sur une période donnée de 24 heures. Pour des raisons de performances, la vérification des mises à jour démarre 3 secondes après le début de la session. La notification s’affiche uniquement au début des sessions suivantes.

Par défaut, PowerShell s’abonne à l’un des deux canaux de notification différents en fonction de sa version/branche. Les versions de PowerShell prises en charge généralement disponibles ne retournent de notifications que pour les versions mises à jour en disponibilité générale (GA). La préversion et la version finale (RC) informent des mises à jour de la préversion, de la version finale (RC) et de la version en disponibilité générale (GA).

Le comportement de notification de mise à jour peut être modifié à l’aide de la variable d’environnement `$Env:POWERSHELL_UPDATECHECK`. Les valeurs suivantes sont admises :

- **Par défaut** revient à ne pas définir `$Env:POWERSHELL_UPDATECHECK`
  - Les versions en disponibilité générale (GA) informent des mises à jour des versions GA
  - La préversion/les versions finales (RC) informent des mises à jour des versions en disponibilité générale (GA) et des préversions.
- **Désactiver** désactive la fonctionnalité de notification de mise à jour
- **LTS** signale uniquement les mises à jour des versions GA LTS (Long-Term-Servicing)

> [!NOTE]
> La variable d’environnement `$Env:POWERSHELL_UPDATECHECK` n’existe pas tant qu’elle n’est pas définie pour la première fois.

Pour définir la notification de version pour les versions de `LTS` uniquement :

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

Pour définir la notification de version pour le comportement `Default` uniquement :

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

Pour plus d'informations [À propos des notifications de mise à jour](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a>Nouvelle prise en charge des ressources DSC avec Invoke-DSCResource (expérimental)

> [!NOTE]
> Il s’agit d’une fonctionnalité expérimentale nommée **PSDesiredStateConfiguration.InvokeDscResource**. En savoir plus [À Propos des fonctionnalités expérimentales](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).

La cmdlet `Invoke-DscResource` exécute une méthode d’une ressource Desired State Configuration (DSC) PowerShell spécifiée.

Cette cmdlet appelle directement une ressource DSC sans créer de document de configuration. À l’aide de cette cmdlet, les produits de gestion de la configuration peuvent gérer Windows ou Linux à l’aide de ressources DSC. Cette cmdlet de commande permet également de déboguer des ressources lorsque le moteur DSC s’exécute avec le débogage activé.

Cette commande appelle la méthode **Set** d’une ressource nommée Log et spécifie une propriété **Message**.

```powershell
Invoke-DscResource -Name Log -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Message = 'Hello World'
}
```

Pour plus d’informations sur [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).

## <a name="breaking-changes-and-improvements"></a>Dernières modifications et améliorations

### <a name="breaking-changes"></a>Dernières modifications

- Prise en charge de LTS et des canaux par défaut par la notification de mise à jour (#11132)
- Mise à jour de Test-Connection pour qu’elle fonctionne de façon plus similaire à Windows PowerShell (#10697) (Merci @vexx32 !)
- Preserve $? pour ParenExpression, SubExpression et ArrayExpression (#11040)
- Transformation du répertoire de travail en répertoire actuel dans Start-Job (#10920) (Merci @iSazonov !)
- Reflet cohérent par $PSCulturedes modifications de culture dans la session (#10138) (Merci @iSazonov !)

### <a name="engine-updates-and-fixes"></a>Mises à jour et correctifs du moteur

- Améliorations des API de point d’arrêt pour les scénarios distants (#11312)
- Correction de la fuite de définition de classe PowerShell dans une autre instance d’exécution (#11273)
- Correction d’une régression dans la mise en forme provoquée par la primitive FirstOrDefault ajoutée à 7.0.0-Preview1 (#11258)
- Modules Microsoft supplémentaires à suivre dans la télémétrie PS7 (#10751)
- Transformation des fonctionnalités approuvées en fonctionnalités non expérimentales (#11303)
- Mise à jour de ConciseView pour utiliser TargetObject le cas échéant (#11075)
- Correction de NullReferenceException dans les méthodes publiques CompletionCompleters (#11274)
- Correction de la vérification de l’état du cloisonnement de threads sur les plateformes non-Windows (#11301)
- Mise à jour du paramètre PSModulePath pour concaténer les variables d’environnement du processus et de l’ordinateur (#11276)
- Passage de .NET Core à 3.1.0 (#11260)
- Correction de la détection de $PSHOME devant $env:PATH (#11141)
- Autorisation pour pwsh d’hériter de $env:PSModulePath et d’activer powershell.exe pour démarrer correctement (#11057)
- Passage à .NET Core 3.1 préversion 1 (#10798)
- Refactorisation des vérifications d’étiquettes d’analyse dans le fournisseur du système de fichiers (#10431) (Merci @iSazonov !)
- Remplacement de CR et de la nouvelle ligne par un caractère 0x23CE dans la journalisation des scripts (#10616)
- Correction d’une fuite de ressources en annulant l’inscription du gestionnaire d’événements dans AppDomain.CurrentDomain.ProcessExit (#10626)
- Ajout de la prise en charge à ActionPreference.Break pour s’arrêter dans le débogueur lorsque des messages de débogage, d’erreur, d’information, de progression, de commentaires ou d’avertissement sont générés (#8205) (Merci @KirkMunro !)
- Activation du démarrage des compléments du panneau de configuration dans PowerShell Core sans spécifier une extension .CPL. (#9828)

### <a name="general-cmdlet-updates-and-fixes"></a>Mises à jour et correctifs d’applets de commande générales

- Correction du problème sur Raspbian pour la définition de la date des modifications de fichier dans la fonctionnalité expérimentale UnixStat (#11313)
- Ajout de -AsPlainText à ConvertFrom-SecureString (#11142)
- Vérification de la version de WindowsPS ajoutée pour WinCompat (#11148)
- Correction des rapports d’erreur dans certains scénarios WinCompat (#11259)
- Ajout d’un programme de résolution binaire natif (#11032) (Merci @iSazonov !)
- Mise à jour du calcul de la largeur de char pour respecter correctement les chars CJK (#11262)
- Ajout d’Unblock-File pour macOS (#11137)
- Correction de la régression dans Get-PSCallStack (#11210) (Merci @iSazonov !)
- Suppression du chargement automatique du module ScheduledJob lors de l’utilisation de cmdlets de tâches (#11194)
- Ajout d’OutputType à la cmdlet Get-Error et conservation du nom de type (#10856)
- Correction de la référence null dans la propriété SupportsVirtualTerminal (#11105)
- Ajout de la limite d’enregistrement dans Get-WinEvent (#10648) (Merci @iSazonov !)
- Correction du runtime de telle manière que StopUpstreamCommandsException ne soit pas rempli dans -ErrorVariable (#10840)
- Définition de l’encodage de sortie sur [console]::OutputEncoding pour les commandes natives (#10824)
- Prise en charge des blocs de code multilignes dans des exemples (#10776) (Merci @Greg-Smulko !)
- Ajout d’un paramètre de culture à la cmdlet Select-String (#10943) (Merci @iSazonov!)
- Correction du chemin du répertoire de Start-Job avec la barre oblique inverse de fin (#11041)
- ConvertFrom-Json : Désencapsulage des collections par défaut (#10861) (Merci @danstur !)
- Utilisation de la table de hachage pour la cmdlet Group-Object avec les commutateurs -CaseSensitive et -AsHashtable (#11030) (Merci @vexx32 !)
- Gestion d’exception en cas d’échec de l’énumération des fichiers lors de la reconstruction du chemin pour obtenir une casse correcte (#11014)
- Correction de ConciseView pour afficher l’activité au lieu de myCommand (#11007)
- Autorisation de cmdlets web d’ignorer les états d’erreur HTTP (#10466) (Merci @vdamewood !)
- Correction de la canalisation de plusieurs CommandInfo vers Get-Command (#10929)
- Rajout de l’applet de commande pour Windows (#10933)
- Traitement de [AutomationNull]::Value et [NullString]::Value en tant que $null par ConvertTo-JSON (#10957)
- Suppression des crochets de l’adresse ipv6 pour la communication à distance SSH (#10968)
- Correction d’incident si la commande envoyée à pwsh est simplement un espace blanc (#10977)
- Ajout de Get-Clipboard et Set-Clipboard multiplateformes (#10340)
- Correction du paramètre du chemin d’origine de l’objet système de fichiers pour qu’il n’ait pas de barre oblique de fin supplémentaire (#10959)
- Prise en charge de $Null pour ConvertTo-Json (#10947)
- Rajout de la commande Out-Printer sur Windows (#10906)
- Correction de Start-Job-WorkingDirectory avec un espace blanc (#10951)
- Retourne la valeur par défaut lors de l’obtention de Null pour un paramètre dans PSConfiguration.cs (#10963) (Merci @iSazonov !)
- Gestion de l’exception d’E/S comme étant sans fin d’exécution (#10950)
- Ajout d’un assembly GraphicalHost pour activer Out-GridView, Show-Command et Get-Help-ShowWindow (#10899)
- Prise de ComputerName via pipeline dans Get-HotFix (#10852) (Merci @kvprasoon !)
- Correction de la saisie semi-automatique des paramètres via la touche Tab pour afficher les paramètres communs disponibles (#10850)
- Correction de GetCorrectCasedPath() pour commencer par vérifier si des entrées de fichier système sont retournées avant d’appeler First() (#10930)
- Transformation du répertoire de travail en répertoire actuel dans Start-Job (#10920) (Merci @iSazonov !)
- Modification de TabExpansion2 pour ne pas demander -CursorColumn et traitement en tant que $InputScript.Length (#10849)
- Gestion au cas où l’hôte ne peut pas retourner des lignes ou des colonnes d’écran (#10938)
- Correction de l’utilisation des couleurs d’accentuation pour les hôtes qui ne les prennent pas en charge (#10937)
- Rajout de la commande Update-List (#10922)
- Mise à jour de l’ID FWLink pour Clear-RecycleBin (#10925)
- Lors de la saisie semi-automatique via la touche Tab, ignorer le fichier si la lecture de ses attributs est impossible (#10910)
- Rajout de Clear-RecycleBin pour Windows (#10909)
- Ajout de `$env:__SuppressAnsiEscapeSequences` pour contrôler s’il faut avoir une séquence d’échappement VT dans la sortie (#10814)
- Ajout du paramètre NoEmphasize pour colorier la sortie Select-String (#8963) (Merci @derek-xia !)
- Rajout de la cmdlet Get-HotFix (#10740)
- Add-Type rendu utilisable dans les applications qui hébergent PowerShell (#10587)
- Utilisation d’un ordre d’évaluation plus efficace dans LanguagePrimitives.IsNullLike() (#10781) (Merci @vexx32 !)
- Amélioration de la gestion de l’entrée redirigée de collection mixte et des flux d’entrée redirigés au Format-Hex (#8674) (Merci @vexx32 !)
- Utilisation de la conversion de type dans les tables de hachage SSHConnection quand la valeur ne correspond pas au type attendu (#10720) (Merci @SeeminglyScience !)
- Correction du comportement de Get-Content -ReadCount 0 quand -TotalCount est défini (#10749) (Merci @eugenesmlv !)
- Message d’erreur d’accès de reformulation refusé dans Get-WinEvent (#10639) (Merci @iSazonov !)
- Activation de la saisie semi-automatique via la touche Tab pour l’affectation de variable qui est une énumération ou un type avec restriction (#10646)
- Suppression de la propriété de communication à distance SourceLength inutilisée provoquant des problèmes de mise en forme (#10765)
- Ajout du paramètre -Delimiter à ConvertFrom-StringData (#10665) (Merci @steviecoaster !)
- Ajout du paramètre de position pour ScriptBlock lorsqu’Invoke-Command est utilisé avec SSH (#10721) (Merci @machgo !)
- Affichage d’informations de contexte de ligne s’il y a plusieurs lignes, mais pas de nom de script pour ConciseView (#10746)
- Ajout de la prise en charge de \\wsl$\ paths au fournisseur de système de fichiers (#10674)
- Ajout du jeton manquant pour TokenKind.QuestionMark dans l’analyseur (#10706)
- Définition du répertoire de travail actuel de chaque script d’exécution ForEach-Object-Parallel au même emplacement que le script appelant. (#10672)
- Remplacement d’api-ms-win-core-file-l1-2-2.dll par Kernell32.dll pour les API FindFirstStreamW et FindNextStreamW (#10680) (Merci @iSazonov !)
- Adaptation du script d’aide à la mise en forme pour une meilleure tolérance StrictMode (#10563)
- Ajout du paramètre -SecurityDescriptorSDDL à New-Service (#10483) (Merci @kvprasoon !)
- Suppression de la sortie d’information, consolidation de l’utilisation du test ping dans Test-Connection (#10478) (Merci @vexx32 !)
- Lecture des points d’analyse spéciaux sans y accéder (#10662) (Merci @iSazonov !)
- Sortie directe Clear-Host sur le terminal (#10681) (Merci @iSazonov !)
- Rajout d’une nouvelle ligne pour le regroupement avec Format-Table et -Property (#10653)
- Suppression de [ValidateNotNullOrEmpty] de -InputObject sur Get-Random pour autoriser une chaîne vide (#10644)
- Algorithme de distance de la chaîne système rendu insensible à la casse (#10549) (Merci @iSazonov !)
- Correction de l’exception de référence Null dans le traitement de l’entrée ForEach-Object-Parallel (#10577)
- Ajout de définitions de stratégie de groupe PowerShell Core (#10468)
- Mise à jour de l’hôte de la console pour prendre en charge les séquences de contrôle XTPUSHSGR/XTPOPSGR VT utilisées dans les scénarios de composabilité. (#10208)
- Ajout du paramètre WorkingDirectory à Start-Job (#10324) (Merci @davinci26 !)
- Suppression du gestionnaire d’événements à l’origine de la réplication erronée des modifications de point d’arrêt dans le débogueur de l’instance d’exécution de l’hôte (#10503) (Merci @KirkMunro !)
- Remplacement d’api-ms-win-core-job-12-1-0.dll par Kernell32.dll dans l’API Microsoft.PowerShell.Commands.NativeMethods P/Invoke (#10417) (Merci @iSazonov !)
- Correction de la sortie incorrecte pour New-Service dans l’affectation de variable et de-OutVariable (#10444) (Merci @kvprasoon !)
- Résolution des problèmes d’outils globaux autour du code de sortie, des paramètres de ligne de commande et du chemin avec des espaces (#10461)
- Correction de la récursivité dans OneDrive : modification de FindFirstFileEx() pour utiliser le type SafeFindHandle (#10405)
- Chargement automatique de PSReadLine sur Windows ignoré si le lecteur d’écran NVDA est actif (#10385)
- Passage des versions de module built-with-PowerShell vers 7.0.0.0 (#10356)
- Ajout de la levée d’une erreur dans Add-Type si un type portant le même nom existe déjà (#9609) (Merci @iSazonov !)

### <a name="performance"></a>Performances

- Éviter d’utiliser la fermeture dans Parser.SaveError (#11006)
- Amélioration de la mise en cache lors de la création d’instances Regex (#10657) (Merci @iSazonov !)
- Amélioration du traitement des données de type PowerShell intégrées detypes.ps1xml, typesV3.ps1xml et GetEvent.types.ps1xml (#10898)
- Mise à jour de PSConfiguration.ReadValueFromFile pour l’accélérer et augmenter l’efficacité de la mémoire (#10839)
- Ajout d’améliorations de performances mineures pour l’initialisation de l’instance d’exécution (#10569) (Merci @iSazonov !)
- Accélération de ForEach-Object pour ses scénarios couramment utilisés (#10454) et résolution du problème de performance ForEach-Object-Parallel avec de nombreuses instances d’exécution (#10455)

### <a name="code-cleanup"></a>Nettoyage du code

- Modification du texte des commentaires et des éléments pour respecter les normes Microsoft (#11304)
- Problèmes de style de nettoyage dans Compiler.cs (#10368) (Merci @iSazonov !)
- Suppression du convertisseur de type inutilisé pour CommaDelimitedStringCollection (#11000) (Merci @iSazonov !)
- Style de nettoyage dans InitialSessionState.cs (#10865) (Merci @iSazonov !)
- Nettoyage du code pour la classe PSSession (#11001)
- Suppression de la fonctionnalité « exécuter Update-Help de Get-Help lorsque Get-Help s’exécute pour la première fois » (#10974)
- Résolution des problèmes de style (#10998) (Merci @iSazonov !)
- Nettoyage : utilisez l’alias de type intégré (#10882) (Merci @iSazonov !)
- Suppression de la clé de paramètre inutilisée ConsolePrompting et évitement d’une création de chaîne inutile lors de l’interrogation du paramètre ExecutionPolicy (#10985)
- Désactivation du contrôle de notification de mise à jour pour les builds quotidiennes (#10903) (Merci @bergmeister !)
- Rétablissement de l’API de débogage perdue dans #10338 (#10808)
- Suppression de la référence WorkflowJobSourceAdapter qui n’est plus utilisée (#10326) (Merci @KirkMunro !)
- Nettoyage des interfaces COM dans le code de liste de raccourcis en résolvant les attributs PreserveSig (#9899) (Merci @weltkante !)
- Ajout d’un commentaire décrivant la raison pour laquelle -ia n’est pas l’alias du paramètre commun -InformationAction (#10703) (Merci @KirkMunro !)
- Renommage d’InvokeCommandCmdlet.cs en InvokeExpressionCommand.cs (#10659) (Merci @kilasuit !)
- Ajout des nettoyages de code mineurs relatifs aux notifications de mise à jour (#10698)
- Suppression de la logique de flux de travail dépréciée des scripts d’installation de communication à distance (#10320) (Merci @KirkMunro !)
- Mise à jour du format d’aide pour utiliser la casse appropriée (#10678) (Merci @tnieto88 !)
- Nettoyage des problèmes de style CodeFactor arrivant dans les validations pour le mois dernier (#10591) (Merci @iSazonov !)
- Correction de la faute de frappe dans la description de la fonctionnalité expérimentale PSTernaryOperator (#10586) (Merci @bergmeister !)
- Convertissement de la valeur d’énumération ActionPreference.Suspend en un État réservé non pris en charge et suppression de la restriction de l’utilisation d’ActionPreference.Ignore dans les variables de préférence (#10317) (Merci @KirkMunro !)
- Remplacement d’ArrayList par List<T> pour obtenir du code plus lisible et plus fiable sans modifier les fonctionnalités (#10333) (Merci @iSazonov !)
- Corrections de style de code dans TestConnectionCommand (#10439) (Merci @vexx32 !)
- Nettoyage d’AutomationEngine et suppression de l’appel de méthode SetSessionStateDrive supplémentaire (#10416) (Merci @iSazonov !)
- Renommage de ParameterSetName par défaut en séparateur pour ConvertTo-Csv et ConvertFrom-Csv (#10425)

### <a name="tools"></a>Outils

- Ajout du paramètre par défaut pour la propriété SDKToUse afin qu’elle soit générée dans VS (#11085)
- Install-Powershell.ps1 : Ajout d’un paramètre pour utiliser l’installation MSI (#10921) (Merci @MJECloud !)
- Ajout d’exemples de base pour install-PowerShell.ps1 (#10914) (Merci @kilasuit !)
- Gestion d’une chaîne vide par Install-PowerShellRemoting.ps1 dans le paramètre PowerShellHome (#10526) (Merci @Orca88 !)
- Basculement de /etc/lsb-release vers /etc/os-release dans install-powershell.sh (#10773) (Merci @Himura2la !)
- Vérification de pwsh.exe et de pwsh dans la version quotidienne sur Windows (#10738) (Merci @centreboard !)
- Suppression de l’actionnement inutile dans installpsh-osx.sh (#10752)
- Mise à jour d’install-PowerShell.ps1 pour vérifier la build quotidienne déjà installée (#10489)

### <a name="tests"></a>Tests

- Mise en attente du test DSC non fiable (#11131)
- Correction du test StringData pour valider correctement les clés de tables de hachage (#10810)
- Déchargement des modules de test (#11061) (Merci @iSazonov !)
- Augmentation du temps entre les nouvelles tentatives de test d’URL (#11015)
- Mise à jour les tests pour décrire précisément les actions de test. (#10928) (Merci @romero126 !)
- Le test non fiable TestAppDomainProcessExitEvenHandlerNotLeaking est temporairement ignoré (#10827)
- Stabilisation du test de fuite du gestionnaire d'événements (#10790)
- Synchronisation de la mise en majuscules dans CI YAML (#10767) (Merci @RDIL !)
- Ajout d’un test pour la correction de fuite du gestionnaire d'événements (#10768)
- Ajout du test Get-ChildItem (#10507) (Merci @iSazonov !)
- Remplacement du langage ambigu des tests du commutateur au paramètre pour garantir la précision (#10666) (Merci @romero126 !)
- Ajout d’une vérification expérimentale aux tests ForEach-Object-Parallel (#10354) (Merci @KirkMunro !)
- Mise à jour des tests de validation Alpine (#10428)

### <a name="build-and-package-improvements"></a>Améliorations des builds et des packages

- Correction de la signature de package NuGet pour la génération de packages coordonnés (#11316)
- Mise à jour des dépendances de PowerShell Gallery et de NuGet (#11323)
- Passage de Microsoft.ApplicationInsights 2.11.0 à 2.12.0 (#11305)
- Passage de Microsoft.CodeAnalysis.CSharp de 3.3.1 à 3.4.0 (#11265)
- Mise à jour des packages pour Debian 10 et 11 (#11236)
- Activation des fonctionnalités expérimentales antérieures à la version RC uniquement (#11162)
- Mise à jour de la version macOS minimale (#11163)
- Passage de NJsonSchema de 10.0.27 à 10.0.28 (#11170)
- Mise à jour des liens dans README.md et metadata.json pour la préversion 5 (#10854)
- Sélection des fichiers pour les tests de compatibilité détenus par PowerShell (#10837)
- Autorisation de la génération du package win7x86 msix. (Interne 10515)
- Autorisation du passage des versions sémantiques à la fonction NormalizeVersion (#11087)
- Passage de l’infrastructure .NET Core à la version 3.1-preview.3 (#11079)
- Passage de PSReadLine de 2.0.0-beta5 à 2.0.0-beta6 dans/src/Modules (#11078)
- Passage de Newtonsoft.Json de 12.0.2 à 12.0.3 (#11037) (#11038)
- Ajout des packages Debian 10, 11 et CentOS 8 (#11028)
- Chargement du fichier Json Build-info avec le champ ReleaseDate (#10986)
- Passage de l’infrastructure .NET Core à la version 3.1-preview.2 (#10993)
- Activation de la build du package MSIX x86 (#10934)
- Mise à jour de l’URL du script d’installation du kit de développement logiciel (SDK) dotnet dans build.psm1 (#10927)
- Passage de Markdig.Signed de 0.17.1 à 0.18.0 (#10887)
- Passage de ThreadJob de 2.0.1 à 2.0.2 (#10886)
- Mise à jour du manifeste AppX et du module de packaging pour respecter les exigences du MS Store (#10878)
- Mise à jour de la référence de package pour le kit de développement logiciel (SDK) PowerShell vers preview.5 (interne 10295)
- Mise à jour de ThirdPartyNotices.txt (#10834)
- Passage de Microsoft. PowerShell.Native à 7.0.0-preview.3 (#10826)
- Passage de Microsoft.ApplicationInsights 2.10.0 à 2.11.0 (#10608)
- Passage de NJsonSchema de 10.0.24 à 10.0.27 (#10756)
- Ajout de la prise en charge MacPorts au système de build (#10736) (Merci @Lucius-Q-User !)
- Passage de PackageManagement de 1.4.4 à 1.4.5 (#10728)
- Passage de NJsonSchema de 10.0.23 à 10.0.24 (#10635)
- Ajout d’une variable d’environnement pour différencier la télémétrie client/serveur dans MSI (#10612)
- Passage de PSDesiredStateConfiguration de 2.0.3 à 2.0.4 (#10603)
- Passage de Microsoft.CodeAnalysis.CSharp de 3.2.1 à 3.3.1 (#10607)
- Mise à jour vers .Net Core 3.0 RTM (#10604) (Merci @bergmeister !)
- Mise à jour du packaging MSIX pour que la version réponde aux exigences du Windows Store (#10588)
- Passage de la version PowerShellGet de 2.2 à 2.2.1 (#10382)
- Passage de PackageManagement de 1.4.3 à 1.4.4 (#10383)
- Mise à jour de README.md et de metadata.json vers 7.0.0-preview.4 (interne 10011)
- Mise à niveau de la version de .Net Core 3.0 de la préversion 9 à la version finale RC1 (#10552) (Merci @bergmeister !)
- Correction de la génération de la liste ExperimentalFeature (interne 9996)
- Passage de la version de PSReadLine de 2.0.0-beta4 à 2.0.0-beta5 (#10536)
- Correction du script de build de version pour définir la balise de mise en production
- Mise à jour de la version de Microsoft.PowerShell.Native vers 7.0.0-preview.2 (#10519)
- Mise à niveau vers Netcoreapp3.0 preview9 (#10484) (Merci @bergmeister !)
- Assurez-vous que la build coordonnée quotidienne sait qu’il s’agit d’une build quotidienne (#10464)
- Mise à jour de la build du package combiné pour publier les builds quotidiennes (#10449)
- Suppression de la référence appveyor (#10445) (Merci @RDIL !)
- Passage de la version de NJsonSchema de 10.0.22 à 10.0.23 (#10421)
- Suppression de l’effacement du dossier de build Linux-x64, car certaines dépendances pour Alpine en ont besoin (#10407)

### <a name="documentation-and-help-content"></a>Contenu de la documentation et de l'aide

- Refactorisation des journaux de modification dans un seul journal par version (#11165)
- Correction de FWLinks pour les documents d’aide en ligne de PowerShell 7 (#11071)
- Mise à jour de CONTRIBUTING.md (#11096) (Merci @mklement0 !)
- Correction des liens du document d’installation dans README.md (#11083)
- Ajout d’exemples au script install-powershell.ps1 (#11024) (Merci @kilasuit !)
- Correction de l’accentuation de Select-String et d’Import-DscResource dans CHANGELOG.md (#10890)
- Suppression du lien obsolète de powershell-beginners-guide.md (#10926)
- Fusion des journaux de modification stables et de maintenance (#10527)
- Mise à jour de la version .NET utilisée dans les documents de build (#10775) (Merci @Greg-Smulko !)
- Remplacez les liens de MSDN par docs.microsoft.com dans powershell-beginners-guide.md (#10778) (Merci @iSazonov !)
- Correction du lien de vue d’ensemble DSC rompu (#10702)
- Mise à jour de Support_Question.md pour créer un lien vers Stack Overflow comme une autre ressource de la communauté (#10638) (Merci @mklement0 !)
- Ajout d’une architecture de processeur au modèle de demande de distribution (#10661)
- Ajout d’un nouveau livre PowerShell MoL aux documents d’apprentissage PowerShell (#10602)
- Mise à jour de README.md et des métadonnées pour les versions v6.1.6 and v6.2.3 (#10523)
- Correction d’une faute de frappe dans README.md (#10465) (Merci @vedhasp !)
- Ajout d’une référence au module PSKoans de la documentation des ressources de formation (#10369) (Merci @vexx32!)
- Mise à jour de README.md et de metadata.json vers 7.0.0-preview.3 (interne 10393)
