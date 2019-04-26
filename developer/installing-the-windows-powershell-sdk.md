---
title: Installation du SDK Windows PowerShell
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: da1b3dbb8a599aee2cdbab9115aedcab0b4c78c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082479"
---
# <a name="installing-the-windows-powershell-sdk"></a>Installation du Kit de développement logiciel Windows PowerShell

S’applique à : Windows PowerShell 2.0, Windows PowerShell 3.0

La rubrique suivante explique comment installer le SDK PowerShell sur différentes versions de Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installation du SDK Windows PowerShell 3.0 pour Windows 8 et Windows Server 2012

Windows PowerShell 3.0 est automatiquement installé avec Windows 8 et Windows Server 2012. De plus, vous pouvez télécharger et installer les assemblys de référence pour Windows PowerShell 3.0 avec le SDK Windows 8. Ces assemblys permettent d’écrire des applets de commande, des fournisseurs et des programmes hôtes pour Windows PowerShell 3.0. Quand vous installez le SDK Windows pour Windows 8, les assemblys Windows PowerShell sont automatiquement installés dans le dossier d’assemblys de référence, dans \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0. Pour plus d’informations, consultez le Kit de développement logiciel Windows 8 de site de téléchargement. Des exemples de code Windows PowerShell sont aussi disponibles dans le Centre de développement.
Pour plus d’informations, consultez la page d’exemples de code Windows Desktop sur le site Centre de développement.

Par ailleurs, Windows PowerShell 3.0 est rétrocompatible avec le SDK Windows PowerShell 2.0 qui comprend un certain nombre d’exemples de code. Pour plus d’informations sur la façon de télécharger le SDK Windows PowerShell 2.0, voir ci-dessous. (Même si les exemples de code 2.0 sont compatibles avec Windows 8 et Windows PowerShell 3.0, notez que vous ne pouvez pas installer Windows PowerShell 2.0 sur une plateforme Windows 8.)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installation du SDK Windows PowerShell 3.0 pour Windows 7 et Windows Server 2008 R2

PowerShell 2.0 est automatiquement installé sur Windows 7 et Windows Server 2008 R2. Par ailleurs, vous pouvez installer PowerShell 3.0 sur ces systèmes. (Pour plus d’informations, consultez Installation de Windows PowerShell.). Comme indiqué plus haut, vous pouvez aussi installer le SDK Windows 8 sur Windows 7 et Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installation du SDK Windows PowerShell 2.0 pour Windows 7, Vista, XP, Server 2003 et Server 2008

Le SDK Windows PowerShell 2.0 fournit les assemblys de référence nécessaires à l’écriture d’applets de commande, de fournisseurs et d’applications d’hébergement. Il propose aussi un exemple de code C# qui peut vous servir de point de départ pour commencer à écrire du code.

Pour installer ce SDK, consultez le Kit de développement logiciel Windows PowerShell 2.0.

### <a name="reference-assemblies"></a>Assemblys de référence

Assemblys de référence sont installés à l’emplacement suivant par défaut : c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0.

> [!NOTE]
>
> Le code compilé sur les assemblys Windows PowerShell 2.0 ne peut pas être chargé dans les installations de Windows PowerShell 1.0. En revanche, le code compilé sur les assemblys Windows PowerShell 1.0 peut être chargé dans les installations de Windows PowerShell 2.0.


### <a name="samples"></a>exemples

Par défaut, les exemples de code sont installés à l’emplacement suivant : C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\. Les sections suivantes fournissent une brève description de la fonction de chaque exemple.

#### <a name="cmdlet-samples"></a>Exemples d’applet de commande

- GetProcessSample01 - montre comment écrire une applet de commande simple qui obtient tous les processus sur l’ordinateur local.
- GetProcessSample02 - montre comment ajouter des paramètres à l’applet de commande. L’applet de commande prend un ou plusieurs noms de processus et retourne les processus correspondants.
- GetProcessSample03 - montre comment ajouter des paramètres qui acceptent les entrées du pipeline.
- GetProcessSample04 - montre comment gérer les erreurs sans fin d’exécution.
- GetProcessSample05 - montre comment afficher la liste des processus spécifiés.
- SelectObject - montre comment écrire un filtre pour sélectionner uniquement certains objets.
- SelectString - montre comment rechercher des fichiers de modèles spécifiés.
- StopProcessSample01 - montre comment implémenter un paramètre PassThru et comment demander des commentaires des utilisateurs en appelant les méthodes ShouldProcess et ShouldContinue. Les utilisateurs spécifier le paramètre PassThru lorsqu’ils veulent forcer l’applet de commande pour retourner un objet.
- StopProcessSample02 - montre comment arrêter un processus spécifique.
- StopProcessSample03 - montre comment déclarer des alias pour les paramètres et la prise en charge des caractères génériques.
- StopProcessSample04 - montre comment déclarer des jeux de paramètres, l’objet de l’applet de commande prend comme entrée et comment spécifier le paramètre par défaut configuré pour utiliser.

#### <a name="remoting-samples"></a>Exemples de communication à distance

- RemoteRunspace01 - montre comment créer une instance d’exécution à distance qui est utilisé pour établir une connexion à distance.
- RemoteRunspacePool01 - montre comment construire un pool d’instance d’exécution à distance et comment exécuter plusieurs commandes simultanément à l’aide de ce pool.
- Serialization01 - montre comment examiner une classe .NET existante et vous assurer que les informations provenant des propriétés publiques sélectionnées de cette classe sont conservées sur la sérialisation/désérialisation.
- Serialization02 - montre comment examiner une classe .NET existante et vous assurer que les informations à partir de l’instance de cette classe sont conservées sur la sérialisation/désérialisation quand les informations ne sont pas disponibles dans les propriétés publiques de la classe.
- Serialization03 - montre comment examiner une classe .NET existante et vous assurer que les instances de cette classe et de classes dérivées sont désérialisées (réactivées) en objets .NET dynamiques.

#### <a name="event-samples"></a>Exemples d’événements

- Event01 - montre comment créer une applet de commande d’inscription d’événement en dérivant de la classe ObjectEventRegistrationBase.
- Event02 - montre comment montre comment recevoir des notifications d’événements de Windows PowerShell qui sont générés sur des ordinateurs distants. Elle utilise l’événement PSEventReceived exposé via la classe d’instance d’exécution.

#### <a name="hosting-application-samples"></a>Exemples d’applications d’hébergement

- Runspace01 - montre comment utiliser la classe de PowerShell pour exécuter le `Get-Process` applet de commande synchrone.
Le `Get-Process` applet de commande renvoie les objets de processus pour chaque processus en cours d’exécution sur l’ordinateur local.
- Runspace02 - montre comment utiliser la classe de PowerShell pour exécuter le `Get-Process` et `Sort-Object` applets de commande de façon synchrone. Le `Get-Process` applet de commande renvoie les objets de processus pour chaque processus en cours d’exécution sur l’ordinateur local et le `Sort-Object` trie les objets en fonction de leur propriété ID. Les résultats de ces commandes s’affiche à l’aide d’un contrôle DataGridView.
- Runspace03 - montre comment utiliser la classe de PowerShell pour exécuter un script de façon synchrone et comment gérer les erreurs sans fin d’exécution. Le script reçoit une liste de noms de processus et récupère ensuite ces processus. Le résultat du script, notamment les erreurs sans fin d’exécution qui ont été générées pendant l’exécution du script, s’affiche dans une fenêtre de console.
- Runspace04 - montre comment utiliser la classe de PowerShell pour exécuter des commandes et comment intercepter les erreurs qui sont levées lorsque vous exécutez les commandes de fin d’exécution. Les commandes exécutées sont au nombre de deux, et la dernière se voit transmettre un argument de paramètre non valide. Par conséquent, aucun objet n’est retourné et une erreur avec fin d’exécution est levée.
- Runspace05 - montre comment ajouter un composant logiciel enfichable à un objet InitialSessionState afin que l’applet de commande de l’utilisation du composant logiciel enfichable est disponible lorsque l’instance d’exécution est ouverte. Le composant logiciel enfichable fournit une cmdlet Get-Process (définie par l’exemple GetProcessSample01) qui est exécutée de façon synchrone à l’aide d’un objet PowerShell.
- Runspace06 - montre comment ajouter un module à un objet InitialSessionState afin que le module est chargé lorsque l’instance d’exécution est ouvert. Le module fournit une cmdlet Get-Process (définie par l’exemple GetProcessSample02) qui est exécutée de façon synchrone à l’aide d’un objet PowerShell.
- Runspace07 - montre comment créer une instance d’exécution et ensuite utiliser cette instance d’exécution pour exécuter deux applets de commande de façon synchrone à l’aide d’un objet PowerShell.
- Runspace08 - montre comment ajouter des commandes et arguments au pipeline d’un objet PowerShell et exécutez les commandes de façon synchrone.
- Runspace09 - montre comment ajouter un script au pipeline d’un objet PowerShell et exécuter le script de façon asynchrone. Des événements sont utilisés pour gérer la sortie du script.
- Runspace10 - montre comment créer un état de session initial par défaut, l’ajout d’une applet de commande à l’InitialSessionState, comment créer une instance d’exécution qui utilise l’état de session initiale et comment exécuter la commande à l’aide d’un objet PowerShell.
- Runspace11 - montre comment utiliser la classe ProxyCommand pour créer une commande de proxy qui appelle une applet de commande existante, mais limite l’ensemble des paramètres disponibles. La commande proxy est ensuite ajoutée à un état de session initial qui sert à créer une instance d’exécution contrainte. Cela signifie que l’utilisateur ne peut accéder à la fonctionnalité de l’applet de commande qu’au moyen de la commande proxy.
- PowerShell01 - montre comment créer une instance d’exécution contrainte à l’aide d’un objet InitialSessionState.
- PowerShell02 - montre comment utiliser un pool de l’instance d’exécution pour exécuter plusieurs commandes simultanément.

#### <a name="host-samples"></a>Exemples d’hôtes

- Host01 - montre comment implémenter une application hôte qui utilise un hôte personnalisé. Dans cet exemple, qu'une instance d’exécution est créée qui utilise l’hôte personnalisé et ensuite l’API PowerShell est utilisé pour exécuter un script qui appelle « exit ». L’application hôte analyse ensuite la sortie du script et imprime les résultats.
- Host02 - montre comment écrire une application hôte qui utilise le runtime de Windows PowerShell avec une implémentation d’hôte personnalisé. L’application hôte définit la culture de l’hôte pour l’allemand, exécute le `Get-Process` applet de commande et affiche les résultats que vous les verriez avec pwrsh.exe pour ensuite imprimer la date et l’heure actuelle en allemand.
- Host03 - montre comment créer une application hôte console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.
- Host04 - montre comment créer une application hôte console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Cette application hôte prend aussi en charge l’affichage d’invites qui permettent à l’utilisateur de spécifier plusieurs options.
- Hôte05 - montre comment créer une application hôte console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Cette application hôte prend également en charge les appels à des ordinateurs distants à l’aide de la `Enter-PsSession` et `Exit-PsSession` applets de commande.
- Host06 - montre comment créer une application hôte console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console. Par ailleurs, cet exemple utilise les API génératrices de jetons pour spécifier la couleur du texte entré par l’utilisateur.

#### <a name="provider-samples"></a>Exemples de fournisseurs

- AccessDBProviderSample01 - montre comment déclarer une classe de fournisseur qui dérive directement de la classe CmdletProvider. Il est indiqué ici uniquement par souci de citer tous les exemples.

- AccessDBProviderSample02 - montre comment remplacer les méthodes NewDrive et RemoveDrive pour prendre en charge les appels à la `New-PSDrive` et `Remove-PSDrive` applets de commande. La classe de fournisseur dans cet exemple dérive de la classe DriveCmdletProvider.

- AccessDBProviderSample03 - montre comment remplacer les méthodes GetItem et SetItem pour prendre en charge les appels à la `Get-Item` et `Set-Item` applets de commande. La classe de fournisseur dans cet exemple dérive de la classe ItemCmdletProvider.

- AccessDBProviderSample04 - montre comment remplacer les méthodes de conteneur pour prendre en charge les appels à la `Copy-Item`, `Get-ChildItem`, `New-Item`, et `Remove-Item` applets de commande. Ces méthodes doivent être implémentées quand le magasin de données contient des éléments de type conteneur. Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent. La classe de fournisseur dans cet exemple dérive de la classe ItemCmdletProvider.

- AccessDBProviderSample05 - montre comment remplacer les méthodes de conteneur pour prendre en charge les appels à la `Move-Item` et `Join-Path` applets de commande. Ces méthodes doivent être implémentées quand l’utilisateur a besoin de déplacer des éléments dans un conteneur et si le magasin de données contient des conteneurs imbriqués. La classe de fournisseur dans cet exemple dérive de la classe NavigationCmdletProvider.

- AccessDBProviderSample06 - montre comment remplacer les méthodes de contenu pour prendre en charge les appels à la `Clear-Content`, `Get-Content`, et `Set-Content` applets de commande. Ces méthodes doivent être implémentées quand l’utilisateur a besoin de gérer le contenu des éléments situés dans le magasin de données. La classe de fournisseur dans cet exemple dérive de la classe NavigationCmdletProvider, et elle implémente l’interface IContentCmdletProvider.
