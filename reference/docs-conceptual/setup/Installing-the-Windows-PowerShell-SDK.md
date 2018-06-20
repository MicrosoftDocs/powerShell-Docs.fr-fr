---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Installation du Kit de développement logiciel Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 830b054c2cf2b49d935d3d96b79effa7131f6db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953563"
---
# <a name="installing-the-windows-powershell-sdk"></a>Installation du Kit de développement logiciel Windows PowerShell

La rubrique suivante explique comment installer le SDK PowerShell sur différentes versions de Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installation du SDK Windows PowerShell 3.0 pour Windows 8 et Windows Server 2012

Windows PowerShell 3.0 est automatiquement installé avec Windows 8 et Windows Server 2012.
De plus, vous pouvez télécharger et installer les assemblys de référence pour Windows PowerShell 3.0 avec le SDK Windows 8.
Ces assemblys permettent d’écrire des applets de commande, des fournisseurs et des programmes hôtes pour Windows PowerShell 3.0.
Quand vous installez le SDK Windows pour Windows 8, les assemblys Windows PowerShell sont automatiquement installés dans le dossier d’assemblys de référence, dans \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.
Pour plus d’informations, voir le [site de téléchargement du SDK Windows 8](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).
Des exemples de code Windows PowerShell sont aussi disponibles dans le Centre de développement.
Pour plus d’informations, voir la page d’exemples de code Windows Desktop sur le [site du Centre de développement](http://code.msdn.microsoft.com/windowsdesktop/).

Par ailleurs, Windows PowerShell 3.0 est rétrocompatible avec le SDK Windows PowerShell 2.0 qui comprend un certain nombre d’exemples de code.
Pour plus d’informations sur la façon de télécharger le SDK Windows PowerShell 2.0, voir ci-dessous.
(Même si les exemples de code 2.0 sont compatibles avec Windows 8 et Windows PowerShell 3.0, notez que vous ne pouvez pas installer Windows PowerShell 2.0 sur une plateforme Windows 8.)

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installation du SDK Windows PowerShell 3.0 pour Windows 7 et Windows Server 2008 R2

PowerShell 2.0 est automatiquement installé sur Windows 7 et Windows Server 2008 R2.
Par ailleurs, vous pouvez installer PowerShell 3.0 sur ces systèmes.
(Pour plus d’informations, voir [Installation de Windows PowerShell](Installing-Windows-PowerShell.md).)
Comme indiqué plus haut, vous pouvez aussi installer le SDK Windows 8 sur Windows 7 et Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installation du SDK Windows PowerShell 2.0 pour Windows 7, Vista, XP, Server 2003 et Server 2008

Le SDK Windows PowerShell 2.0 fournit les assemblys de référence nécessaires à l’écriture d’applets de commande, de fournisseurs et d’applications d’hébergement. Il propose aussi un exemple de code C# qui peut vous servir de point de départ pour commencer à écrire du code.

Pour installer ce SDK, voir le [SDK Windows PowerShell 2.0 ](http://go.microsoft.com/fwlink/?LinkId=184611).

## <a name="reference-assemblies"></a>Assemblys de référence

Les assemblys de référence sont installés dans l’emplacement par défaut suivant : `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> **Remarque** : Le code compilé sur les assemblys Windows PowerShell 2.0 ne peut pas être chargé dans les installations de Windows PowerShell 1.0.
>En revanche, le code compilé sur les assemblys Windows PowerShell 1.0 peut être chargé dans les installations de Windows PowerShell 2.0.

## <a name="samples"></a>exemples

Les exemples de code sont installés dans l’emplacement par défaut suivant : `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

Les sections suivantes fournissent une brève description de la fonction de chaque exemple.

## <a name="cmdlet-samples"></a>Exemples d’applet de commande
**GetProcessSample01**

Montre comment écrire une applet de commande simple qui obtient tous les processus sur l’ordinateur local.

**GetProcessSample02**

Montre comment ajouter des paramètres à une applet de commande.
L’applet de commande prend un ou plusieurs noms de processus et retourne les processus correspondants.

**GetProcessSample03**

Montre comment ajouter des paramètres qui acceptent une entrée provenant du pipeline.

**GetProcessSample04**

Montre comment gérer les erreurs sans fin d’exécution.

**GetProcessSample05**

Montre comment afficher une liste de processus spécifiés.

**SelectObject**

Montre comment écrire un filtre pour sélectionner uniquement certains objets.

**SelectString**

Montre comment rechercher des modèles spécifiés dans des fichiers.

**StopProcessSample01**

Montre comment implémenter un paramètre *PassThru* et comment demander des commentaires utilisateur en appelant les méthodes [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) et [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx).
Les utilisateurs spécifient le paramètre *PassThru* quand ils veulent forcer l’applet de commande à retourner un objet.

**StopProcessSample02**

Montre comment arrêter un processus spécifique.

**StopProcessSample03**

Montre comment déclarer des alias de paramètres et comment prendre en charge les caractères génériques.

**StopProcessSample04**

Montre comment déclarer des jeux de paramètres, l’objet que prend l’applet de commande comme entrée et comment spécifier le jeu de paramètres à utiliser par défaut.

## <a name="remoting-samples"></a>Exemples de communication à distance

**RemoteRunspace01**

Montre comment créer une instance d’exécution à distance servant à établir une connexion à distance.

**RemoteRunspacePool01**

Montre comment construire un pool d’instances d’exécution à distance et comment exécuter plusieurs commandes simultanément en utilisant ce pool.

**Serialization01**

Montre comment examiner une classe .NET existante et vérifier que les informations provenant des propriétés publiques sélectionnées de cette classe sont conservées à l’issue de la sérialisation/désérialisation.

**Serialization02**

Montre comment examiner une classe .NET existante et vérifier que les informations provenant de l’instance de cette classe sont conservées à l’issue de la sérialisation/désérialisation quand les informations ne sont pas disponibles dans les propriétés publiques de la classe.

**Serialization03**

Montre comment examiner une classe .NET existante et vérifier que les instances de cette classe et des classes dérivées sont désérialisées (réactivées) en objets .NET dynamiques.

## <a name="event-samples"></a>Exemples d’événements

**Event01**

Montre comment créer une applet de commande pour l’inscription d’événements en la dérivant de la classe ObjectEventRegistrationBase.

**Event02**

Montre comment recevoir des notifications d’événements Windows PowerShell générés sur des ordinateurs distants.
Il utilise l’événement PSEventReceived exposé via la classe [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx).

## <a name="hosting-application-samples"></a>Exemples d’applications d’hébergement

**Runspace01**

Montre comment utiliser la classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) pour exécuter l’applet de commande [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) de façon synchrone.
L’applet de commande [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) retourne des objets [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) pour chaque processus s’exécutant sur l’ordinateur local.

**Runspace02**

Montre comment utiliser la classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) pour exécuter les applets de commande [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) et [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) de façon synchrone.
L’applet de commande [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) retourne des objets [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) pour chaque processus s’exécutant sur l’ordinateur local, tandis que Sort-Object trie les objets en fonction de leur propriété [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx).
Le résultat de ces commandes s’affiche au moyen d’un contrôle [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx).

**Runspace03**

Montre comment utiliser la classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) pour exécuter un script de façon synchrone et comment gérer les erreurs sans fin d’exécution.
Le script reçoit une liste de noms de processus et récupère ensuite ces processus.
Le résultat du script, notamment les erreurs sans fin d’exécution qui ont été générées pendant l’exécution du script, s’affiche dans une fenêtre de console.

**Runspace04**

Montre comment utiliser la classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) pour exécuter des commandes et comment intercepter les erreurs avec fin d’exécution qui sont levées pendant l’exécution des commandes.
Les commandes exécutées sont au nombre de deux, et la dernière se voit transmettre un argument de paramètre non valide.
Par conséquent, aucun objet n’est retourné et une erreur avec fin d’exécution est levée.

**Runspace05**

Montre comment ajouter un composant logiciel enfichable à un objet [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) de telle sorte que l’applet de commande du composant logiciel enfichable soit disponible quand l’instance d’exécution est ouverte.
Le composant logiciel enfichable fournit une applet de commande Get-Process (définie par [l’exemple GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) qui est exécutée de façon synchrone à l’aide d’un objet [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).

**Runspace06**

Montre comment ajouter un module à un objet [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) de telle sorte que le module soit chargé quand l’instance d’exécution est ouverte.
Le module fournit une applet de commande Get-Process (définie par [l’exemple GetProcessSample02](https://technet.microsoft.com/library/ff602027.aspx)) qui est exécutée de façon synchrone à l’aide d’un objet [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).

**Runspace07**

Montre comment créer une instance d’exécution, puis s’en servir pour exécuter deux applets de commande de façon synchrone en utilisant un objet [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).

**Runspace08**

Montre comment ajouter des commandes et des arguments au pipeline d’un objet [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) et comment exécuter les commandes de façon synchrone.

**Runspace09**

Montre comment ajouter un script au pipeline d’un objet [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) et comment exécuter le script de façon asynchrone.
Des événements sont utilisés pour gérer la sortie du script.

**Runspace10**

Montre comment créer un état de session initial par défaut, comment ajouter une applet de commande à [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), comment créer une instance d’exécution qui utilise l’état de session initial et comment exécuter la commande en utilisant un objet [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).

**Runspace11**

Montre comment utiliser la classe [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) pour créer une commande proxy qui appelle une applet de commande existante, mais qui limite le jeu de paramètres disponibles.
La commande proxy est ensuite ajoutée à un état de session initial qui sert à créer une instance d’exécution contrainte.
Cela signifie que l’utilisateur ne peut accéder à la fonctionnalité de l’applet de commande qu’au moyen de la commande proxy.

**PowerShell01**

Montre comment créer une instance d’exécution contrainte en utilisant un objet [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx).

**PowerShell02**

Montre comment utiliser un pool d’instances d’exécution pour exécuter plusieurs commandes simultanément.

## <a name="host-samples"></a>Exemples d’hôtes

**Host01**

Montre comment implémenter une application hôte qui utilise un hôte personnalisé.
Dans cet exemple, l’instance d’exécution qui est créée utilise l’hôte personnalisé, puis l’API [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) est utilisée pour exécuter un script qui appelle « exit ».
L’application hôte analyse ensuite la sortie du script et imprime les résultats.

**Host02**

Montre comment écrire une application hôte qui utilise le runtime Windows PowerShell avec une implémentation d’hôte personnalisée.
L’application hôte définit la culture de l’hôte sur l’allemand, exécute l’applet de commande [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) et affiche les résultats comme vous les verriez avec pwrsh.exe pour ensuite imprimer la date et l’heure actuelles en allemand.

**Host03**

Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.

**Host04**

Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.
Cette application hôte prend aussi en charge l’affichage d’invites qui permettent à l’utilisateur de spécifier plusieurs options.

**Host05**

Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.
Cette application hôte prend aussi en charge les appels à des ordinateurs distants à l’aide des applets de commande [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) et [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212).

**Host06**

Montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.
Par ailleurs, cet exemple utilise les API génératrices de jetons pour spécifier la couleur du texte entré par l’utilisateur.

## <a name="provider-samples"></a>Exemples de fournisseurs

**AccessDBProviderSample01**

Montre comment déclarer une classe de fournisseur qui dérive directement de la classe [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx).
Il est indiqué ici uniquement par souci de citer tous les exemples.

**AccessDBProviderSample02**

Montre comment remplacer les méthodes [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) et [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) pour prendre en charge les appels aux applets de commande New-PSDrive et Remove-PSDrive.
La classe de fournisseur de cet exemple dérive de la classe [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx).

**AccessDBProviderSample03**

Montre comment remplacer les méthodes [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) et [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) pour prendre en charge les appels aux applets de commande Get-Item et Set-Item.
La classe de fournisseur de cet exemple dérive de la classe [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx).

**AccessDBProviderSample04**

Montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux applets de commande Copy-Item, Get-ChildItem, New-Item et Remove-Item.
Ces méthodes doivent être implémentées quand le magasin de données contient des éléments de type conteneur.
Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent.
La classe de fournisseur de cet exemple dérive de la classe [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx).

**AccessDBProviderSample05**

Montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux applets de commande Move-Item et Join-Path.
Ces méthodes doivent être implémentées quand l’utilisateur a besoin de déplacer des éléments dans un conteneur et si le magasin de données contient des conteneurs imbriqués.
La classe de fournisseur de cet exemple dérive de la classe [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx).

**AccessDBProviderSample06**

Montre comment remplacer les méthodes de contenu pour prendre en charge les appels aux applets de commande Clear-Content, Get-Content et Set-Content.
Ces méthodes doivent être implémentées quand l’utilisateur a besoin de gérer le contenu des éléments situés dans le magasin de données.
La classe de fournisseur de cet exemple dérive de la classe [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) et implémente l’interface [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx).