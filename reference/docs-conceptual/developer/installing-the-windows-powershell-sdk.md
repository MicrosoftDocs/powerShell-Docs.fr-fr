---
ms.date: 03/30/2020
ms.topic: reference
title: Installation du Kit de développement logiciel Windows PowerShell
description: Installation du Kit de développement logiciel Windows PowerShell
ms.openlocfilehash: 07108ede640b8c6c02bea6d9e2b63116b5b8f969
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657299"
---
# <a name="installing-the-windows-powershell-sdk"></a>Installation du Kit de développement logiciel Windows PowerShell

S’applique à : Windows PowerShell 2,0, Windows PowerShell 3,0

La rubrique suivante explique comment installer le SDK PowerShell sur différentes versions de Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installation du SDK Windows PowerShell 3.0 pour Windows 8 et Windows Server 2012

Windows PowerShell 3.0 est automatiquement installé avec Windows 8 et Windows Server 2012. De plus, vous pouvez télécharger et installer les assemblys de référence pour Windows PowerShell 3.0 avec le SDK Windows 8. Ces assemblys permettent d’écrire des applets de commande, des fournisseurs et des programmes hôtes pour Windows PowerShell 3.0. Quand vous installez le SDK Windows pour Windows 8, les assemblys Windows PowerShell sont installés automatiquement dans le dossier d’assemblys de référence, dans `\Program Files
(x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`. Pour plus d’informations, voir le site de téléchargement du SDK Windows 8. Des exemples de code Windows PowerShell sont également disponibles dans le référentiel [PowerShell-SDK-Samples](https://github.com/MicrosoftDocs/powershell-sdk-samples/tree/master/SDK-3.0) .

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installation du SDK Windows PowerShell 3.0 pour Windows 7 et Windows Server 2008 R2

PowerShell 2.0 est automatiquement installé sur Windows 7 et Windows Server 2008 R2. Par ailleurs, vous pouvez installer PowerShell 3.0 sur ces systèmes. Vous pouvez également installer le kit de développement logiciel (SDK) Windows 8 sur Windows 7 et Windows Server 2008 R2 comme décrit ci-dessus.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installation du SDK Windows PowerShell 2.0 pour Windows 7, Vista, XP, Server 2003 et Server 2008

Le SDK Windows PowerShell 2.0 fournit les assemblys de référence nécessaires à l’écriture d’applets de commande, de fournisseurs et d’applications d’hébergement. Il propose aussi un exemple de code C# qui peut vous servir de point de départ pour commencer à écrire du code. Vous pouvez télécharger les exemples de code à partir de [https://www.microsoft.com/download/details.aspx?id=2560](https://www.microsoft.com/download/details.aspx?id=2560) .

### <a name="reference-assemblies"></a>Assemblys de référence

Les assemblys de référence sont installés dans l’emplacement par défaut suivant : `c:\Program Files\Reference
Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> [!NOTE]
> Le code compilé sur les assemblys Windows PowerShell 2.0 ne peut pas être chargé dans les installations de Windows PowerShell 1.0. En revanche, le code compilé sur les assemblys Windows PowerShell 1.0 peut être chargé dans les installations de Windows PowerShell 2.0.

### <a name="samples"></a>Exemples

Les exemples de code sont installés dans l’emplacement par défaut suivant : `C:\Program Files\Microsoft
SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`. Les sections suivantes fournissent une brève description de la fonction de chaque exemple.

#### <a name="cmdlet-samples"></a>Exemples d’applet de commande

- GetProcessSample01 : indique comment écrire une applet de commande simple qui obtient tous les processus sur l’ordinateur local.
- GetProcessSample02 : indique comment ajouter des paramètres à l’applet de commande. L’applet de commande prend un ou plusieurs noms de processus et retourne les processus correspondants.
- GetProcessSample03 : indique comment ajouter des paramètres qui acceptent les entrées du pipeline.
- GetProcessSample04 : indique comment gérer les erreurs sans fin d’arrêt.
- GetProcessSample05 : indique comment afficher une liste de processus spécifiés.
- SelectObject : indique comment écrire un filtre pour sélectionner uniquement certains objets.
- SelectString : indique comment rechercher des modèles spécifiés dans les fichiers.
- StopProcessSample01 : montre comment implémenter un paramètre PassThru et comment demander des commentaires utilisateur en appelant les méthodes ShouldProcess et ShouldContinue. Les utilisateurs spécifient le paramètre PassThru quand ils veulent forcer l’applet de commande à retourner un objet.
- StopProcessSample02 : indique comment arrêter un processus spécifique.
- StopProcessSample03 : indique comment déclarer des alias pour les paramètres et comment prendre en charge les caractères génériques.
- StopProcessSample04 : indique comment déclarer des jeux de paramètres, l’objet que l’applet de commande prend comme entrée et comment spécifier le jeu de paramètres par défaut à utiliser.

#### <a name="remoting-samples"></a>Exemples de communication à distance

- RemoteRunspace01 : indique comment créer une instance d’exécution distante qui est utilisée pour établir une connexion à distance.
- RemoteRunspacePool01 : montre comment construire un pool d’instances d’exécution à distance et comment exécuter plusieurs commandes simultanément à l’aide de ce pool.
- Serialization01 : montre comment examiner une classe .NET existante et s’assurer que les informations des propriétés publiques sélectionnées de cette classe sont conservées au cours de la sérialisation/désérialisation.
- Serialization02 : montre comment examiner une classe .NET existante et s’assurer que les informations de l’instance de cette classe sont conservées au cours de la sérialisation ou de la désérialisation lorsque les informations ne sont pas disponibles dans les propriétés publiques de la classe.
- Serialization03 : montre comment examiner une classe .NET existante et s’assurer que les instances de cette classe et des classes dérivées sont désérialisées (réalimentées) dans des objets .NET en temps réel.

#### <a name="event-samples"></a>Exemples d’événements

- Event01 : indique comment créer une applet de commande pour l’inscription des événements en dérivant de ObjectEventRegistrationBase.
- Event02 : indique comment recevoir des notifications d’événements Windows PowerShell générés sur des ordinateurs distants. Il utilise l’événement PSEventReceived exposé via la classe Runspace.

#### <a name="hosting-application-samples"></a>Exemples d’applications d’hébergement

- Runspace01 : indique comment utiliser la classe PowerShell pour exécuter l’applet de commande de `Get-Process` façon synchrone.
  L' `Get-Process` applet de commande retourne les objets de processus pour chaque processus en cours d’exécution sur l’ordinateur local.
- Runspace02 : indique comment utiliser la classe PowerShell pour exécuter les `Get-Process` applets de commande et de `Sort-Object` façon synchrone. L' `Get-Process` applet de commande retourne les objets de processus pour chaque processus en cours d’exécution sur l’ordinateur local, et `Sort-Object` trie les objets en fonction de leur propriété ID. Le résultat de ces commandes s’affiche au moyen d’un contrôle DataGridView.
- Runspace03 : montre comment utiliser la classe PowerShell pour exécuter un script de façon synchrone et comment gérer les erreurs sans fin d’exécution. Le script reçoit une liste de noms de processus et récupère ensuite ces processus. Le résultat du script, notamment les erreurs sans fin d’exécution qui ont été générées pendant l’exécution du script, s’affiche dans une fenêtre de console.
- Runspace04 : indique comment utiliser la classe PowerShell pour exécuter des commandes et comment intercepter les erreurs de fin levées lors de l’exécution des commandes. Les commandes exécutées sont au nombre de deux, et la dernière se voit transmettre un argument de paramètre non valide. Par conséquent, aucun objet n’est retourné et une erreur avec fin d’exécution est levée.
- Runspace05 : indique comment ajouter un composant logiciel enfichable à un objet InitialSessionState afin que l’applet de commande du composant logiciel enfichable soit disponible lorsque l’instance d’exécution est ouverte. Le composant logiciel enfichable fournit une applet de commande Get-Proc (définie par l’exemple GetProcessSample01) qui est exécutée de façon synchrone à l’aide d’un objet PowerShell.
- Runspace06 : indique comment ajouter un module à un objet InitialSessionState de sorte que le module soit chargé lorsque l’instance d’exécution est ouverte. Le module fournit une applet de commande Get-Proc (définie par l’exemple GetProcessSample02) qui est exécutée de façon synchrone à l’aide d’un objet PowerShell.
- Runspace07 : indique comment créer une instance d’exécution, puis utiliser cette instance d’exécution pour exécuter deux applets de commande de façon synchrone à l’aide d’un objet PowerShell.
- Runspace08 : indique comment ajouter des commandes et des arguments au pipeline d’un objet PowerShell et comment exécuter les commandes de façon synchrone.
- Runspace09 : montre comment ajouter un script au pipeline d’un objet PowerShell et comment exécuter le script de manière asynchrone. Des événements sont utilisés pour gérer la sortie du script.
- Runspace10 : indique comment créer un état de session initial par défaut, comment ajouter une applet de commande à InitialSessionState, comment créer une instance d’exécution qui utilise l’état de session initial et comment exécuter la commande à l’aide d’un objet PowerShell.
- Runspace11 : montre comment utiliser la classe ProxyCommand pour créer une commande de proxy qui appelle une applet de commande existante, mais qui limite l’ensemble des paramètres disponibles. La commande proxy est ensuite ajoutée à un état de session initial qui sert à créer une instance d’exécution contrainte. Cela signifie que l’utilisateur ne peut accéder à la fonctionnalité de l’applet de commande qu’au moyen de la commande proxy.
- PowerShell01 : indique comment créer une instance d’exécution avec restriction à l’aide d’un objet InitialSessionState.
- PowerShell02 : indique comment utiliser un pool d’instances d’exécution pour exécuter plusieurs commandes simultanément.

#### <a name="host-samples"></a>Exemples d’hôtes

- Host01 : indique comment implémenter une application hôte qui utilise un hôte personnalisé. Dans cet exemple, une instance d’exécution est créée et utilise l’hôte personnalisé, puis l’API PowerShell est utilisée pour exécuter un script qui appelle `exit` . L’application hôte analyse ensuite la sortie du script et imprime les résultats.
- Host02 : montre comment écrire une application hôte qui utilise le runtime Windows PowerShell avec une implémentation d’hôte personnalisée. L’application hôte définit la culture de l’hôte en allemand, exécute l’applet de commande `Get-Process` et affiche les résultats comme vous le feriez à l’aide de pwrsh.exe, puis imprime les données actuelles et l’heure en allemand.
- Host03 : indique comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.
- Host04 : indique comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Cette application hôte prend aussi en charge l’affichage d’invites qui permettent à l’utilisateur de spécifier plusieurs options.
- Host05 : indique comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Cette application hôte prend également en charge les appels à des ordinateurs distants à l’aide des `Enter-PsSession` applets de commande et `Exit-PsSession` .
- Host06 : indique comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Par ailleurs, cet exemple utilise les API génératrices de jetons pour spécifier la couleur du texte entré par l’utilisateur.

#### <a name="provider-samples"></a>Exemples de fournisseurs

- AccessDBProviderSample01 : indique comment déclarer une classe de fournisseur qui dérive directement de la classe CmdletProvider. Il est indiqué ici uniquement par souci de citer tous les exemples.

- AccessDBProviderSample02 : montre comment remplacer les méthodes les et RemoveDrive pour prendre en charge les appels aux `New-PSDrive` applets de commande et `Remove-PSDrive` . La classe de fournisseur de cet exemple dérive de la classe DriveCmdletProvider.

- AccessDBProviderSample03 : montre comment remplacer les méthodes GetItem et SetItem pour prendre en charge les appels aux `Get-Item` applets de commande et `Set-Item` . La classe de fournisseur de cet exemple dérive de la classe ItemCmdletProvider.

- AccessDBProviderSample04 : indique comment remplacer les méthodes de conteneur pour prendre en charge les appels aux `Copy-Item` applets de commande,, `Get-ChildItem` `New-Item` et `Remove-Item` . Ces méthodes doivent être implémentées quand le magasin de données contient des éléments de type conteneur. Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent. La classe de fournisseur de cet exemple dérive de la classe ItemCmdletProvider.

- AccessDBProviderSample05 : indique comment remplacer les méthodes de conteneur pour prendre en charge les appels aux `Move-Item` applets de commande et `Join-Path` . Ces méthodes doivent être implémentées quand l’utilisateur a besoin de déplacer des éléments dans un conteneur et si le magasin de données contient des conteneurs imbriqués. La classe de fournisseur de cet exemple dérive de la classe NavigationCmdletProvider.

- AccessDBProviderSample06 : montre comment remplacer les méthodes de contenu pour prendre en charge les appels aux `Clear-Content` applets de commande, `Get-Content` et `Set-Content` . Ces méthodes doivent être implémentées quand l’utilisateur a besoin de gérer le contenu des éléments situés dans le magasin de données. La classe de fournisseur de cet exemple dérive de la classe NavigationCmdletProvider et implémente l’interface IContentCmdletProvider.
