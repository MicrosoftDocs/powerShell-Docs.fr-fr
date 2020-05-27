---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Glossaire Windows PowerShell
ms.openlocfilehash: 1e2285bb49ed6a30fb5624ab3cf136cbf06401b5
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809195"
---
# <a name="windows-powershell-glossary"></a>Glossaire Windows PowerShell

|Terme|Définition|
|--------|--------------|
|module binaire|Module Windows PowerShell dont module racine est un fichier de module binaire (.dll). Un module binaire peut ou non inclure un manifeste de module.|
|paramètre commun|Paramètre qui est ajouté à l’ensemble des applets de commande, fonctions avancées et flux de travail par le moteur Windows PowerShell.|
|source de point|Dans Windows PowerShell, permet de lancer une commande en tapant un point et une espace devant la commande. Les commandes sans source de point s’exécutent dans l’étendue actuelle plutôt que dans une nouvelle étendue. Les variables, alias, fonctions ou lecteurs que la commande crée sont créés dans l’étendue en cours, et sont disponibles pour les utilisateurs une fois l’exécution de la commande terminée.|
|module dynamique|Module qui existe uniquement en mémoire. Les applets de commande New-Module et Import-PSSession créent des modules dynamiques.|
|paramètre dynamique|Paramètre qui est ajouté à une applet de commande, une fonction ou un script Windows PowerShell sous certaines conditions. Des applets de commande, des fonctions, des fournisseurs et des scripts peuvent ajouter des paramètres dynamiques.|
|fichier de mise en forme|Fichier XML de Windows PowerShell portant l’extension .format.ps1xml, qui définit la manière dont Windows PowerShell affiche un objet en fonction de son type .NET Framework.|
|état de session global|État de session contenant les données qui sont accessibles à l’utilisateur d’une session Windows PowerShell.|
|host|Interface que le moteur Windows PowerShell utilise pour communiquer avec l’utilisateur. Par exemple, l’hôte spécifie la manière dont les invites sont gérées entre Windows PowerShell et l’utilisateur.|
|application hôte|Programme qui charge le moteur Windows PowerShell dans son processus et l’utilise pour effectuer des opérations.|
|méthode de traitement d’entrée|Méthode qu’une applet de commande peut utiliser pour traiter les enregistrements qu’elle reçoit en entrée. Les méthodes de traitement d’entrée incluent la méthode BeginProcessing, la méthode ProcessRecord, la méthode EndProcessing et la méthode StopProcessing.|
|module de manifeste|Module Windows PowerShell disposant d’un manifeste et dont la clé RootModule est vide.|
|manifeste de module|Fichier de données Windows PowerShell (.psd1) qui décrit le contenu d’un module et contrôle le mode de traitement de celui-ci.|
|état de session de module|État de session contenant les données publiques et privées d’un module Windows PowerShell. Les données privées dans cet état de session ne sont pas accessibles à l’utilisateur d’une session Windows PowerShell.|
|erreur sans fin d’exécution|Erreur qui n’empêche pas Windows PowerShell de continuer à traiter la commande.|
|substantif|Mot qui suit le trait d’union dans un nom d’applet de commande Windows PowerShell. Le substantif décrit la ressource sur laquelle l’applet de commande agit.|
|jeu de paramètres|Groupe de paramètres qui peut être utilisé dans la même commande pour effectuer une action spécifique.|
|canal|Dans Windows PowerShell, permet d’envoyer les résultats de la commande précédente en tant qu’entrée à la commande suivante dans le pipeline.|
|pipeline|Série de commandes connectées par des opérateurs de pipeline (&#124;) (ASCII 124). Chaque opérateur de pipeline envoie les résultats de la commande précédente en tant qu’entrée à la commande suivante.|
|PSSession|Type de session Windows PowerShell qui est créée, gérée et fermée par l’utilisateur.|
|module racine|Le module spécifié dans la clé RootModule d’un manifeste de module.|
|instance d’exécution|Dans Windows PowerShell, environnement d’exploitation dans lequel chaque commande d’un pipeline est exécutée.|
|bloc de script|Dans le langage de programmation de Windows PowerShell, collection d’instructions ou d’expressions qui peuvent être utilisées comme une seule unité. Un bloc de script peut accepter des arguments et retourner des valeurs.|
|module de script|Module Windows PowerShell dont le module racine est un fichier de module de script (.psm1). Un module de script peut ou non inclure un manifeste de module.|
|fichier de module de script|Fichier contenant un script Windows PowerShell. Le script définit les membres que le module de script exporte. Les fichiers de module de script ont l’extension de nom de fichier .psm1.|
|shell|Interpréteur de commandes utilisé pour transmettre des commandes au système d’exploitation.|
|paramètre booléen|Paramètre qui n’accepte pas d’argument.|
|erreur avec fin d’exécution|Erreur qui empêche Windows PowerShell de traiter la commande.|
|transaction|Une unité atomique de travail. Le travail dans une transaction doit être entièrement effectué. Si une partie de la transaction échoue, la transaction entière échoue.|
|fichier de type|Fichier XML de Windows PowerShell qui porte l’extension .ps1xml et étend les propriétés de types Microsoft .NET Framework dans Windows PowerShell.|
|verbe|Mot qui précède le trait d’union dans un nom d’applet de commande Windows PowerShell. Le verbe décrit l’action que l’applet de commande exécute.|
|Windows PowerShell|Technologie de script basée sur des tâches et un interpréteur de ligne de commande, qui fournit aux administrateurs informatiques un contrôle et une automatisation complets des tâches d’administration système.|
|Commande de Windows PowerShell|Éléments dans un pipeline qui déclenchent l’exécution d’une action. Les commandes Windows PowerShell sont tapées sur le clavier ou appelées par programme.|
|Fichier de données Windows PowerShell|Fichier texte portant l’extension de nom de fichier .psd1. Windows PowerShell utilise des fichiers de données à différentes fins, telles que le stockage des données de manifeste de module et le stockage de chaînes traduites pour l’internationalisation des scripts.|
|lecteur Windows PowerShell|Disque virtuel qui fournit un accès direct à un magasin de données. Il peut être défini par un fournisseur Windows PowerShell ou créé via la ligne de commande. Les lecteurs créés via la ligne de commande sont spécifiques d’une session et perdus lors de la fermeture de celle-ci.|
|Environnement d'écriture de scripts intégré de Windows PowerShell|Application hôte Windows PowerShell qui permet d’exécuter des commandes ainsi que d’écrire, tester et déboguer des scripts dans un environnement convivial, avec coloration de la syntaxe et compatible Unicode.|
|Module Windows PowerShell|Unité réutilisable intégrée qui permet de partitionner, d’organiser et d’abstraire votre code Windows PowerShell. Un module peut contenir des applets de commande, fournisseurs, fonctions, variables et autres types de ressources pouvant être importés en tant qu’unité unique.|
|fournisseur Windows PowerShell|Programme Microsoft basé sur .NET Framework, qui rend les données d’une banque de données spécialisée disponibles dans Windows PowerShell, afin que vous puissiez les afficher et les gérer.|
|script Windows PowerShell|Script écrit dans le langage Windows PowerShell.|
|fichier de script Windows PowerShell|Fichier portant l’extension .ps1 et contenant un script écrit dans le langage Windows PowerShell.|
|composant logiciel enfichable Windows PowerShell|Ressource définissant un ensemble d’applets de commande, de fournisseurs et de types Microsoft .NET Framework qui peuvent être ajoutés à l’environnement Windows PowerShell.|
|Windows PowerShell Workflow|Un workflow est une séquence d’étapes programmées et connectées qui effectuent des tâches de longue durée ou requièrent la coordination de plusieurs étapes sur plusieurs appareils ou nœuds gérés. Windows PowerShell Workflow permet aux professionnels de l’informatique et aux développeurs de créer des séquences d’activités de gestion multi-appareils, ou des tâches unique au sein d’un workflow en tant que workflow. Windows PowerShell Workflow permet d’adapter et d’exécuter des fichiers XAML et des scripts Windows PowerShell en tant que workflow.|
