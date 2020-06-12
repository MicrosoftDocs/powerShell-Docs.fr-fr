---
title: Prise en main de PowerShell
description: Où trouver et comment lancer PowerShell pour les nouveaux utilisateurs.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 0f72fb5baf5b829142b18ed774261e9b3b66291b
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438020"
---
# <a name="chapter-1---getting-started-with-powershell"></a>Chapitre 1 - Bien démarrer avec PowerShell

Lors des conférences ou des réunions de groupes d’utilisateurs visant à présenter PowerShell, j’ai remarqué que souvent, le présentateur avait déjà lancé PowerShell avant même que la présentation n’ait démarré. Ce livre commence par répondre aux questions qui m’ont été posées lors des conférences par ceux qui n’avaient jamais encore utilisé PowerShell.

Plus précisément, ce chapitre explique comment trouver et lancer PowerShell, et comment surmonter certaines difficultés que peuvent rencontrer les nouveaux utilisateurs de PowerShell. Il est important de suivre les exemples présentés dans ce chapitre sur votre ordinateur Windows 10 Lab Environment.

## <a name="what-do-i-need-to-get-started-with-powershell"></a>De quoi ai-je besoin pour bien démarrer avec PowerShell ?

Toutes les versions actuelles des systèmes d’exploitation Windows sont livrées avec PowerShell. Si vous exécutez une version antérieure à la version 5.1, vous devez installer la dernière version.

- Pour mettre à niveau votre version vers Windows PowerShell 5.1, consultez [Mise à niveau des instances Windows PowerShell existantes][].
- Pour installer la dernière version de PowerShell, consultez [Installation de PowerShell][].

## <a name="where-do-i-find-powershell"></a>Où trouver PowerShell ?

Le moyen le plus simple de rechercher PowerShell sur Windows 10 est de taper **PowerShell** dans la barre de recherche, comme le montre la figure 1-1.

![Figure 1-1](media/figure1-1.png)

Notez que la figure 1-1 montre quatre raccourcis différents pour PowerShell. Dans ce livre, l’ordinateur utilisé à des fins de démonstration exécute la version 64 bits de Windows 10. Vous avez donc une version 64 bits de la console PowerShell et de PowerShell ISE (environnement de script intégré), ainsi qu’une version 32 bits pour chacun, comme l’indique le suffixe (x86) dans les raccourcis. Si vous exécutez une version 32 bits de Windows 10, vous n’aurez que deux raccourcis. Ces éléments n’ont pas le suffixe (x86), mais il s’agit de la version 32 bits. Si vous disposez d’un système d’exploitation 64 bits, je vous recommande d’exécuter la version 64 bits de PowerShell, sauf si vous avez une raison particulière d’exécuter la version 32 bits.

Pour plus d’informations sur le démarrage de PowerShell sur d’autres versions de Windows, consultez [Démarrage de Windows PowerShell][].

## <a name="how-do-i-launch-powershell"></a>Comment lancer PowerShell ?

Dans les environnements d’entreprise de production dont j’ai la charge, j’utilise trois comptes d’utilisateur Active Directory différents. J’ai pris ces mêmes comptes comme exemple dans l’environnement lab de ce livre. Je me connecte à l’ordinateur Windows 10 en tant qu’utilisateur de domaine, mais pas en tant qu’administrateur de domaine ou administrateur local.

J’ai lancé la console PowerShell en cliquant sur le raccourci « Windows PowerShell », comme illustré dans la figure 1-1.

![Figure 1-4](media/figure1-4.png)

Notez que la barre de titre de la console PowerShell indique « Windows PowerShell », comme dans la figure 1-4. Certaines commandes s’exécutent bien, toutefois, PowerShell ne peut pas participer au contrôle de compte d’utilisateur (UAC). Cela signifie qu’il ne peut pas demander une élévation des privilèges pour les tâches qui nécessitent l’approbation d’un administrateur.
Le message d’erreur suivant est généré :

```powershell
Get-Service -Name W32Time | Stop-Service
```

```Output
Stop-Service : Service 'Windows Time (W32Time)' cannot be stopped due to the following
error: Cannot open W32Time service on computer '.'.
At line:1 char:29
+ Get-Service -Name W32Time | Stop-Service
+
    + CategoryInfo          : CloseError: (System.ServiceProcess.ServiceController:ServiceController)
     [Stop-Service], ServiceCommandException
    + FullyQualifiedErrorId : CouldNotStopService,Microsoft.PowerShell.Commands.StopServiceCommand
```

La solution à ce problème consiste à exécuter PowerShell en tant qu’utilisateur de domaine et administrateur local.
Voici la configuration de mon deuxième compte d’utilisateur de domaine. Si j’applique le principe du « privilège minimum », ce compte ne doit PAS être un administrateur de domaine, ni disposer de privilèges élevés au sein du domaine.

Fermez PowerShell. Relancez la console PowerShell, mais cette fois-ci, cliquez avec le bouton droit sur le raccourci **Windows PowerShell**, puis sélectionnez **Exécuter en tant qu’administrateur**, comme indiqué dans la figure 1-5.

![Figure 1-5](media/figure1-5.png)

Si vous êtes connecté à Windows en tant qu’utilisateur normal, vous êtes invité à entrer vos informations d’identification. Je vais entrer les informations d’identification de mon compte d’utilisateur, qui est un compte d’utilisateur de domaine et d’administrateur local, comme le montre la figure 1-6.

![Figure 1-6](media/figure1-6.png)

Une fois que vous avez relancé PowerShell en tant qu’administrateur, la barre de titre doit indiquer « Administrateur : Windows PowerShell», comme illustré à la figure 1-7.

![Figure 1-7](media/figure1-7.png)

Maintenant que PowerShell est exécuté avec une élévation des privilèges en tant qu’administrateur local, le contrôle de compte d’utilisateur ne posera plus de problème lorsque vous exécuterez une commande sur l’ordinateur local. Notez toutefois que toutes les autres commandes exécutées à partir de cette instance de la console PowerShell s’exécutent elles aussi avec des privilèges élevés.

Pour simplifier la recherche de PowerShell et le lancer en tant qu’administrateur, je vous recommande de l’épingler à la barre des tâches et de le configurer pour qu’il se lance automatiquement en tant qu’administrateur chaque fois qu’il est exécuté.

Recherchez de nouveau PowerShell, mais cette fois-ci, cliquez dessus avec le bouton droit, puis sélectionnez « Épingler à la barre des tâches », comme illustré à la figure 1-8.

![Figure 1-8](media/figure1-8.png)

Cliquez avec le bouton droit sur le raccourci PowerShell qui est maintenant épinglé à la barre des tâches, puis sélectionnez Propriétés, comme indiqué dans la figure 1-9.

![Figure 1-9](media/figure1-9.png)

Cliquez sur « Avancé », comme indiqué par le « 1 » dans la figure 1-10, cochez la case « Exécuter en tant qu’administrateur », comme indiqué par le « 2 » dans la figure 1-10, puis cliquez deux fois sur OK pour accepter les modifications et quitter les deux boîtes de dialogue.

![Figure 1-10](media/figure1-10.png)

Vous n’aurez plus à rechercher PowerShell ni à le configurer pour être exécuté en tant qu’administrateur.

Si vous exécutez PowerShell en tant qu’administrateur dans le but d’éviter les problèmes liés au contrôle de compte d’utilisateur, cela impactera uniquement les commandes qui sont exécutées sur l’ordinateur local. Cela n’aura aucun effet sur les commandes qui ciblent les ordinateurs distants.

## <a name="what-version-of-powershell-am-i-running"></a>Quelle est la version de mon instance PowerShell ?

Dans PowerShell, il existe plusieurs variables automatiques qui stockent des informations d’état. L’une de ces variables est `$PSVersionTable`, qui contient une table de hachage pouvant être utilisée pour afficher des informations utiles sur la version de PowerShell :

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      5.1.19041.1
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

Les versions récentes de Windows PowerShell sont distribuées avec Windows Management Framework (WMF). Chaque version de WMF nécessite une version spécifique de .NET Framework. Pour mettre à niveau votre version vers Windows PowerShell 5.1, consultez [Mise à niveau des instances Windows PowerShell existantes][].

## <a name="execution-policy"></a>Stratégie d’exécution

Contrairement à la croyance populaire, la stratégie d’exécution de PowerShell ne constitue pas une barrière de sécurité. Elle est conçue pour empêcher un utilisateur d’exécuter un script à son insu. Un utilisateur déterminé peut facilement contourner cette stratégie d’exécution dans PowerShell. Le tableau 1-2 montre la stratégie d’exécution par défaut des systèmes d’exploitation Windows actuels.

| Version du système d’exploitation Windows | Stratégie d’exécution par défaut |
| -------------------------------- | ------------------------ |
| Server 2019                      | RemoteSigned            |
| Server 2016                      | RemoteSigned            |
| Windows 10                       | Restreint               |

Quel que soit le paramètre de stratégie d’exécution, toutes les commandes PowerShell peuvent être exécutées de manière interactive. La stratégie d’exécution affecte uniquement les commandes qui s’exécutent dans un script. L’applet de commande `Get-ExecutionPolicy` est utilisée pour déterminer le paramètre de stratégie d’exécution qui est appliqué, et l’applet de commande `Set-ExecutionPolicy` est utilisée pour modifier la stratégie d’exécution. Je recommande d’utiliser la stratégie **RemoteSigned**, qui exige que les scripts téléchargés soient signés par un éditeur approuvé pour pouvoir être exécutés.

Vérifiez la stratégie d’exécution actuelle :

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

Les scripts PowerShell ne peuvent pas être exécutés lorsque la stratégie d’exécution est définie sur **Restricted**. Il s’agit du paramètre par défaut sur tous les systèmes d’exploitation clients Windows. Pour illustrer ce problème, enregistrez le code suivant sous la forme d’un fichier `.ps1` nommé `Stop-TimeService.ps1`.

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

Cette commande s’exécute de manière interactive sans erreur tant que PowerShell est exécuté avec une élévation des privilèges, en tant qu’administrateur. Toutefois, dès qu’il est enregistré sous la forme d’un fichier de script et que vous essayez de l’exécuter, celui-ci génère une erreur :

```powershell
.\Stop-TimeService.ps1
```

```Output
.\Stop-TimeService.ps1 : File C:\demo\Stop-TimeService.ps1 cannot be loaded because
running scripts is disabled on this system. For more information, see
about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Stop-TimeService.ps1
+
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

Notez que l’erreur qui s’affiche dans le jeu de résultats précédent vous indique exactement quel est le problème (l’exécution des scripts a été désactivée sur ce système). Dans PowerShell, quand vous exécutez une commande qui génère un message d’erreur, il est important de lire le message d’erreur au lieu de réexécuter simplement la commande en espérant que celle-ci s’exécute correctement cette fois-ci.

Modifiez la stratégie d’exécution PowerShell pour qu’elle soit signée à distance (RemoteSigned).

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

```Output
Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution
policy might expose you to the security risks described in the about_Execution_Policies help topic
at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"):y
```

Lisez l’avertissement qui s’affiche lorsque vous modifiez la stratégie d’exécution. Je vous conseille également de consulter la rubrique d’aide [about_Execution_Policies][] afin de bien comprendre ce qu’implique la modification d’une stratégie d’exécution au niveau de la sécurité.

Maintenant que la stratégie d’exécution a été définie sur **RemoteSigned**, le script `Stop-TimeService.ps1` s’exécute sans erreurs.

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

Pour ne pas rencontrer de problèmes imprévus, veillez à démarrer le service Temps Windows avant de continuer.

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a>Résumé

Dans ce chapitre, vous avez vu comment rechercher et lancer PowerShell, et comment créer un raccourci qui permet d’exécuter PowerShell en tant qu’administrateur. Vous avez également découvert la stratégie d’exécution par défaut et vous avez vu comment la modifier.

## <a name="review"></a>Révision

1. Comment savoir quelle version de PowerShell un ordinateur exécute ?
1. Pourquoi est-il important de lancer PowerShell avec une élévation de privilèges en tant qu’administrateur ?
1. Comment déterminer la stratégie d’exécution PowerShell actuellement appliquée ?
1. Que permet d’éviter la stratégie d’exécution PowerShell par défaut sur les ordinateurs clients Windows ?
1. Comment modifier la stratégie d’exécution PowerShell ?

## <a name="recommended-reading"></a>Lecture recommandée

Si vous souhaitez en savoir plus sur les sujets abordés dans ce chapitre, je vous conseille de lire les rubriques d’aide PowerShell suivantes.

- [about_Automatic_Variables][]
- [about_Execution_Policies][]

Dans le chapitre suivant, vous allez découvrir la détectabilité des commandes dans PowerShell. L’un des sujets abordés sera la mise à jour de PowerShell dans le but de rendre les rubriques d’aide consultables directement dans PowerShell au lieu d’avoir à les lire sur Internet.

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Execution_Policies]: /powershell//powershell/module/microsoft.powershell.core/about/about_execution_policies
[Mise à niveau des instances Windows PowerShell existantes]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[Installation de PowerShell]: /powershell/scripting/install/installing-powershell
[Démarrage de Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
