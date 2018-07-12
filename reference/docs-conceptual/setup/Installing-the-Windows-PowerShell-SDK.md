---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Installation du Kit de développement logiciel Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893536"
---
# <a name="installing-the-windows-powershell-sdk"></a>Installation du Kit de développement logiciel Windows PowerShell

La rubrique suivante explique comment installer le SDK PowerShell sur différentes versions de Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installation du SDK Windows PowerShell 3.0 pour Windows 8 et Windows Server 2012

Windows PowerShell 3.0 est automatiquement installé avec Windows 8 et Windows Server 2012.
De plus, vous pouvez télécharger et installer les assemblys de référence pour Windows PowerShell 3.0 avec le SDK Windows 8.
Ces assemblys permettent d’écrire des applets de commande, des fournisseurs et des programmes hôtes pour Windows PowerShell 3.0.
Quand vous installez le SDK Windows pour Windows 8, les assemblys Windows PowerShell sont installés automatiquement dans le dossier d’assemblys de référence, dans `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.
Pour plus d’informations, voir le [site de téléchargement du SDK Windows 8](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).
Des exemples de code Windows PowerShell sont aussi disponibles dans le Centre de développement.
Pour plus d’informations, voir la page d’exemples de code Windows Desktop sur le [site du Centre de développement](https://code.msdn.microsoft.com:443/windowsdesktop/).

Par ailleurs, Windows PowerShell 3.0 est rétrocompatible avec le SDK Windows PowerShell 2.0 qui comprend un certain nombre d’exemples de code.
Pour plus d’informations sur la façon de télécharger le SDK Windows PowerShell 2.0, voir ci-dessous.
(Même si les exemples de code 2.0 sont compatibles avec Windows 8 et Windows PowerShell 3.0, notez que vous ne pouvez pas installer Windows PowerShell 2.0 sur une plateforme Windows 8.)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installation du SDK Windows PowerShell 3.0 pour Windows 7 et Windows Server 2008 R2

PowerShell 2.0 est automatiquement installé sur Windows 7 et Windows Server 2008 R2.
Par ailleurs, vous pouvez installer PowerShell 3.0 sur ces systèmes.
(Pour plus d’informations, voir [Installation de Windows PowerShell](Installing-Windows-PowerShell.md).)
Comme indiqué plus haut, vous pouvez aussi installer le SDK Windows 8 sur Windows 7 et Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installation du SDK Windows PowerShell 2.0 pour Windows 7, Vista, XP, Server 2003 et Server 2008

Le SDK Windows PowerShell 2.0 fournit les assemblys de référence nécessaires à l’écriture d’applets de commande, de fournisseurs et d’applications d’hébergement. Il propose aussi un exemple de code C# qui peut vous servir de point de départ pour commencer à écrire du code.

Pour installer ce SDK, voir le [SDK Windows PowerShell 2.0 ](http://www.microsoft.com/en-us/download/details.aspx?id=2560).

## <a name="reference-assemblies"></a>Assemblys de référence

Les assemblys de référence sont installés dans l’emplacement par défaut suivant : `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> [!NOTE] 
> Le code compilé sur les assemblys Windows PowerShell 2.0 ne peut pas être chargé dans les installations de Windows PowerShell 1.0.
> En revanche, le code compilé sur les assemblys Windows PowerShell 1.0 peut être chargé dans les installations de Windows PowerShell 2.0.

## <a name="samples"></a>exemples

Les exemples de code sont installés dans l’emplacement par défaut suivant : `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

Les sections suivantes fournissent une brève description de la fonction de chaque exemple.

## <a name="cmdlet-samples"></a>Exemples d’applet de commande

### <a name="getprocesssample01"></a>GetProcessSample01

Montre comment écrire une applet de commande simple qui obtient tous les processus sur l’ordinateur local.

### <a name="getprocesssample02"></a>GetProcessSample02

Montre comment ajouter des paramètres à une applet de commande.
L’applet de commande prend un ou plusieurs noms de processus et retourne les processus correspondants.

### <a name="getprocesssample03"></a>GetProcessSample03

Montre comment ajouter des paramètres qui acceptent une entrée provenant du pipeline.

### <a name="getprocesssample04"></a>GetProcessSample04

Montre comment gérer les erreurs sans fin d’exécution.

### <a name="getprocesssample05"></a>GetProcessSample05

Montre comment afficher une liste de processus spécifiés.

### <a name="selectobject"></a>SelectObject

Montre comment écrire un filtre pour sélectionner uniquement certains objets.

### <a name="selectstring"></a>SelectString

Montre comment rechercher des modèles spécifiés dans des fichiers.

### <a name="stopprocesssample01"></a>StopProcessSample01

Montre comment implémenter un paramètre *PassThru* et comment demander des commentaires utilisateur en appelant les méthodes [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) et [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue).
Les utilisateurs spécifient le paramètre *PassThru* quand ils veulent forcer l’applet de commande à retourner un objet.

### <a name="stopprocesssample02"></a>StopProcessSample02

Montre comment arrêter un processus spécifique.

### <a name="stopprocesssample03"></a>StopProcessSample03

Montre comment déclarer des alias de paramètres et comment prendre en charge les caractères génériques.

### <a name="stopprocesssample04"></a>StopProcessSample04

Montre comment déclarer des jeux de paramètres, l’objet que prend l’applet de commande comme entrée et comment spécifier le jeu de paramètres à utiliser par défaut.

## <a name="remoting-samples"></a>Exemples de communication à distance

### <a name="remoterunspace01"></a>RemoteRunspace01

Montre comment créer une instance d’exécution à distance servant à établir une connexion à distance.

### <a name="remoterunspacepool01"></a>RemoteRunspacePool01

Montre comment construire un pool d’instances d’exécution à distance et comment exécuter plusieurs commandes simultanément en utilisant ce pool.

### <a name="serialization01"></a>Serialization01

Montre comment examiner une classe .NET existante et vérifier que les informations provenant des propriétés publiques sélectionnées de cette classe sont conservées à l’issue de la sérialisation/désérialisation.

### <a name="serialization02"></a>Serialization02

Montre comment examiner une classe .NET existante et vérifier que les informations provenant de l’instance de cette classe sont conservées à l’issue de la sérialisation/désérialisation quand les informations ne sont pas disponibles dans les propriétés publiques de la classe.

### <a name="serialization03"></a>Serialization03

Montre comment examiner une classe .NET existante et vérifier que les instances de cette classe et des classes dérivées sont désérialisées (réactivées) en objets .NET dynamiques.

## <a name="event-samples"></a>Exemples d’événements

### <a name="event01"></a>Event01

Montre comment créer une applet de commande pour l’inscription d’événements en la dérivant de la classe ObjectEventRegistrationBase.

### <a name="event02"></a>Event02

Montre comment recevoir des notifications d’événements Windows PowerShell générés sur des ordinateurs distants.
Il utilise l’événement PSEventReceived exposé via la classe [Runspace](/dotnet/api/system.management.automation.runspaces.runspace).

## <a name="hosting-application-samples"></a>Exemples d’applications d’hébergement

### <a name="runspace01"></a>Runspace01

Montre comment utiliser la classe [PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter l’applet de commande [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) de façon synchrone.
L’applet de commande [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourne des objets [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) pour chaque processus s’exécutant sur l’ordinateur local.

### <a name="runspace02"></a>Runspace02

Montre comment utiliser la classe [PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter les applets de commande [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) et [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) de façon synchrone.
L’applet de commande [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourne des objets [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) pour chaque processus s’exécutant sur l’ordinateur local, tandis que `Sort-Object` trie les objets en fonction de leur propriété [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx).
Le résultat de ces commandes s’affiche au moyen d’un contrôle [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx).

### <a name="runspace03"></a>Runspace03

Montre comment utiliser la classe [PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter un script de façon synchrone et comment gérer les erreurs sans fin d’exécution.
Le script reçoit une liste de noms de processus et récupère ensuite ces processus.
Le résultat du script, notamment les erreurs sans fin d’exécution qui ont été générées pendant l’exécution du script, s’affiche dans une fenêtre de console.

### <a name="runspace04"></a>Runspace04

Montre comment utiliser la classe [PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter des commandes et comment intercepter les erreurs avec fin d’exécution qui sont levées pendant l’exécution des commandes.
Les commandes exécutées sont au nombre de deux, et la dernière se voit transmettre un argument de paramètre non valide.
Par conséquent, aucun objet n’est retourné et une erreur avec fin d’exécution est levée.

### <a name="runspace05"></a>Runspace05

Montre comment ajouter un composant logiciel enfichable à un objet [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) de telle sorte que l’applet de commande du composant logiciel enfichable soit disponible quand l’instance d’exécution est ouverte.
Le composant logiciel enfichable fournit une applet de commande Get-Process (définie par [l’exemple GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) qui est exécutée de façon synchrone à l’aide d’un objet [PowerShell](/dotnet/api/system.management.automation.powershell).

### <a name="runspace06"></a>Runspace06

Montre comment ajouter un module à un objet [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) de telle sorte que le module soit chargé quand l’instance d’exécution est ouverte.
Le module fournit une applet de commande Get-Process (définie par [l’exemple GetProcessSample02](https://technet.microsoft.com/library/ff602027.aspx)) qui est exécutée de façon synchrone à l’aide d’un objet [PowerShell](/dotnet/api/system.management.automation.powershell).

### <a name="runspace07"></a>Runspace07

Montre comment créer une instance d’exécution, puis s’en servir pour exécuter deux applets de commande de façon synchrone en utilisant un objet [PowerShell](/dotnet/api/system.management.automation.powershell).

### <a name="runspace08"></a>Runspace08

Montre comment ajouter des commandes et des arguments au pipeline d’un objet [PowerShell](/dotnet/api/system.management.automation.powershell) et comment exécuter les commandes de façon synchrone.

### <a name="runspace09"></a>Runspace09

Montre comment ajouter un script au pipeline d’un objet [PowerShell](/dotnet/api/system.management.automation.powershell) et comment exécuter le script de façon asynchrone.
Des événements sont utilisés pour gérer la sortie du script.

### <a name="runspace10"></a>Runspace10

Montre comment créer un état de session initial par défaut, comment ajouter une applet de commande à [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), comment créer une instance d’exécution qui utilise l’état de session initial et comment exécuter la commande en utilisant un objet [PowerShell](/dotnet/api/system.management.automation.powershell).

### <a name="runspace11"></a>Runspace11

Montre comment utiliser la classe [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) pour créer une commande proxy qui appelle une applet de commande existante, mais qui limite le jeu de paramètres disponibles.
La commande proxy est ensuite ajoutée à un état de session initial qui sert à créer une instance d’exécution contrainte.
Cela signifie que l’utilisateur ne peut accéder à la fonctionnalité de l’applet de commande qu’au moyen de la commande proxy.

### <a name="powershell01"></a>PowerShell01

Montre comment créer une instance d’exécution contrainte en utilisant un objet [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate).

### <a name="powershell02"></a>PowerShell02

Montre comment utiliser un pool d’instances d’exécution pour exécuter plusieurs commandes simultanément.

## <a name="host-samples"></a>Exemples d’hôtes

### <a name="host01"></a>Host01

Montre comment implémenter une application hôte qui utilise un hôte personnalisé.
Dans cet exemple, l’instance d’exécution qui est créée utilise l’hôte personnalisé, puis l’API [PowerShell](/dotnet/api/system.management.automation.powershell) est utilisée pour exécuter un script qui appelle « exit ».
L’application hôte analyse ensuite la sortie du script et imprime les résultats.

### <a name="host02"></a>Host02

Montre comment écrire une application hôte qui utilise le runtime Windows PowerShell avec une implémentation d’hôte personnalisée.
L’application hôte définit la culture de l’hôte sur l’allemand, exécute l’applet de commande [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) et affiche les résultats comme vous les verriez avec pwrsh.exe pour ensuite imprimer la date et l’heure actuelles en allemand.

### <a name="host03"></a>Host03

Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.

### <a name="host04"></a>Host04

Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.
Cette application hôte prend aussi en charge l’affichage d’invites qui permettent à l’utilisateur de spécifier plusieurs options.

### <a name="host05"></a>Host05

Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.
Cette application hôte prend aussi en charge les appels à des ordinateurs distants à l’aide des applets de commande [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) et [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession).

### <a name="host06"></a>Host06

Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.
Par ailleurs, cet exemple utilise les API génératrices de jetons pour spécifier la couleur du texte entré par l’utilisateur.

## <a name="provider-samples"></a>Exemples de fournisseurs

### <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

Montre comment déclarer une classe de fournisseur qui dérive directement de la classe [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider).
Il est indiqué ici uniquement par souci de citer tous les exemples.

### <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

Montre comment remplacer les méthodes [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) et [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) pour prendre en charge les appels aux applets de commande `New-PSDrive` et `Remove-PSDrive`.
La classe de fournisseur de cet exemple dérive de la classe [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider).

### <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Montre comment remplacer les méthodes [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) et [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) pour prendre en charge les appels aux applets de commande `Get-Item` et `Set-Item`.
La classe de fournisseur de cet exemple dérive de la classe [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider).

### <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux applets de commande `Copy-Item`, `Get-ChildItem`, `New-Item` et `Remove-Item`.
Ces méthodes doivent être implémentées quand le magasin de données contient des éléments de type conteneur.
Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent.
La classe de fournisseur de cet exemple dérive de la classe [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider).

### <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

Montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux applets de commande `Move-Item` et `Join-Path`.
Ces méthodes doivent être implémentées quand l’utilisateur a besoin de déplacer des éléments dans un conteneur et si le magasin de données contient des conteneurs imbriqués.
La classe de fournisseur de cet exemple dérive de la classe [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider).

### <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Montre comment remplacer les méthodes de contenu pour prendre en charge les appels aux applets de commande `Clear-Content`, `Get-Content` et `Set-Content`.
Ces méthodes doivent être implémentées quand l’utilisateur a besoin de gérer le contenu des éléments situés dans le magasin de données.
La classe de fournisseur de cet exemple dérive de la classe [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) et implémente l’interface [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider).