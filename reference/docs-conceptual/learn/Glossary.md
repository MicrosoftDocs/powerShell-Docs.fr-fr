---
ms.date: 06/11/2020
keywords: powershell,applet de commande
title: Glossaire PowerShell
ms.openlocfilehash: 8df76fa3a78e9701c28488db0bde25fa245b1160
ms.sourcegitcommit: 56463fb628a7d83dec4364e89417d83316c3e53b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2020
ms.locfileid: "84722862"
---
# <a name="powershell-glossary"></a>Glossaire PowerShell

|            Terme             | Définition |
| --------------------------- | ---------- |
| module binaire               | Module PowerShell dont le module racine est un fichier de module binaire (.dll). Un module binaire peut ou non inclure un manifeste de module. |
| paramètre commun            | Paramètre qui est ajouté à l’ensemble des applets de commande, fonctions avancées et workflows par le moteur PowerShell. |
| source de point                  | Dans PowerShell, permet de lancer une commande en tapant un point et un espace devant la commande. Les commandes sans source de point s’exécutent dans l’étendue actuelle plutôt que dans une nouvelle étendue. Les variables, alias, fonctions ou lecteurs que la commande crée sont créés dans l’étendue en cours, et sont disponibles pour les utilisateurs une fois l’exécution de la commande terminée. |
| module dynamique              | Module qui existe uniquement en mémoire. Les applets de commande New-Module et Import-PSSession créent des modules dynamiques. |
| paramètre dynamique           | Paramètre qui est ajouté à une applet de commande, une fonction ou un script PowerShell sous certaines conditions. Des applets de commande, des fonctions, des fournisseurs et des scripts peuvent ajouter des paramètres dynamiques. |
| fichier de mise en forme             | Fichier XML de PowerShell portant l’extension `.format.ps1xml`, qui définit la manière dont PowerShell affiche un objet en fonction de son type .NET Framework. |
| état de session global        | État de session contenant les données d’une session PowerShell qui sont accessibles à l’utilisateur. |
| host                        | Interface que le moteur PowerShell utilise pour communiquer avec l’utilisateur. Par exemple, l’hôte spécifie la manière dont les invites sont gérées entre PowerShell et l’utilisateur. |
| application hôte            | Programme qui charge le moteur PowerShell dans son processus et l’utilise pour effectuer des opérations. |
| méthode de traitement d’entrée     | Méthode qu’une applet de commande peut utiliser pour traiter les enregistrements qu’elle reçoit en entrée. Les méthodes de traitement d’entrée incluent la méthode BeginProcessing, la méthode ProcessRecord, la méthode EndProcessing et la méthode StopProcessing. |
| module de manifeste             | Module PowerShell disposant d’un manifeste et dont la clé RootModule est vide. |
| module                      | Unité réutilisable intégrée qui permet de partitionner, d’organiser et d’abstraire votre code PowerShell. Un module peut contenir des applets de commande, fournisseurs, fonctions, variables et autres types de ressources pouvant être importés en tant qu’unité unique. |
| manifeste de module             | Fichier de données PowerShell (`.psd1`) qui décrit le contenu d’un module et contrôle le mode de traitement de celui-ci. |
| état de session de module        | État de session contenant les données publiques et privées d’un module PowerShell. Les données privées dans cet état de session ne sont pas accessibles à l’utilisateur d’une session PowerShell. |
| erreur sans fin d’exécution       | Erreur qui n’empêche pas PowerShell de continuer à traiter la commande. |
| substantif                        | Mot qui suit le trait d’union dans un nom d’applet de commande PowerShell. Le substantif décrit la ressource sur laquelle l’applet de commande agit. |
| jeu de paramètres               | Groupe de paramètres qui peut être utilisé dans la même commande pour effectuer une action spécifique. |
| canal                        | Dans PowerShell, permet d’envoyer les résultats de la commande précédente en tant qu’entrée à la commande suivante dans le pipeline. |
| pipeline                    | Série de commandes connectées par des opérateurs de pipeline (&#124;) (ASCII 124). Chaque opérateur de pipeline envoie les résultats de la commande précédente en tant qu’entrée à la commande suivante. |
| Applet de commande PowerShell           | Commande unique qui participe à la sémantique de pipeline de PowerShell. Cela comprend les applets de commande binaires (C#), les fonctions de script avancées, le CDXML et les workflows. |
| Commande PowerShell          | Éléments dans un pipeline qui déclenchent l’exécution d’une action. Les commandes PowerShell sont tapées sur le clavier ou appelées par programmation. |
| Fichier de données PowerShell        | Fichier texte portant l’extension de nom de fichier `.psd1`. PowerShell utilise des fichiers de données à différentes fins, telles que le stockage des données de manifeste de module et le stockage de chaînes traduites pour l’internationalisation des scripts. |
| Lecteur PowerShell            | Disque virtuel qui fournit un accès direct à un magasin de données. Il peut être défini par un fournisseur PowerShell ou créé via la ligne de commande. Les lecteurs créés via la ligne de commande sont spécifiques d’une session et perdus lors de la fermeture de celle-ci. |
| provider                    | Programme Microsoft basé sur .NET Framework, qui met à disposition les données d’un magasin de données spécialisé dans PowerShell pour pouvoir les afficher et les gérer. |
| PSSession                   | Type d’une session PowerShell qui est créée, gérée et fermée par l’utilisateur. |
| module racine                 | Le module spécifié dans la clé RootModule d’un manifeste de module. |
| instance d’exécution                    | Dans PowerShell, environnement d’exploitation dans lequel chaque commande d’un pipeline est exécutée. |
| bloc de script                | Dans le langage de programmation de PowerShell, collection d’instructions ou d’expressions qui peuvent être utilisées comme une seule unité. Un bloc de script peut accepter des arguments et retourner des valeurs. |
| Fichier de script                 | Fichier portant l’extension `.ps1` et contenant un script écrit en langage PowerShell. |
| module de script               | Module PowerShell dont le module racine est un fichier de module de script (`.psm1`). Un module de script peut ou non inclure un manifeste de module. |
| fichier de module de script          | Fichier contenant un script PowerShell. Le script définit les membres que le module de script exporte. Les fichiers de module de script ont comme extension de nom de fichier `.psm1`. |
| shell                       | Interpréteur de commandes utilisé pour transmettre des commandes au système d’exploitation. |
| paramètre booléen            | Paramètre qui n’accepte pas d’argument. |
| erreur avec fin d’exécution           | Erreur qui empêche PowerShell de traiter la commande. |
| transaction                 | Une unité atomique de travail. Le travail dans une transaction doit être entièrement effectué. Si une partie de la transaction échoue, la transaction entière échoue. |
| fichier de type                  | Fichier XML de PowerShell qui porte l’extension `.ps1xml` et étend les propriétés de types Microsoft .NET Framework dans PowerShell. |
| verbe                        | Mot qui précède le trait d’union dans un nom d’applet de commande PowerShell. Le verbe décrit l’action que l’applet de commande exécute. |
| Windows PowerShell ISE      | Environnement d’écriture de scripts intégré - Application hôte Windows PowerShell qui permet d’exécuter des commandes ainsi que d’écrire, tester et déboguer des scripts dans un environnement convivial, compatible Unicode et proposant la coloration syntaxique. |
| composant logiciel enfichable Windows PowerShell  | Ressource définissant un ensemble d’applets de commande, de fournisseurs et de types Microsoft .NET Framework qui peuvent être ajoutés à l’environnement Windows PowerShell. |
| Windows PowerShell Workflow | Un workflow est une séquence d’étapes programmées et connectées qui effectuent des tâches de longue durée ou requièrent la coordination de plusieurs étapes sur plusieurs appareils ou nœuds gérés. Windows PowerShell Workflow permet aux professionnels de l’informatique et aux développeurs de créer des séquences d’activités de gestion multi-appareils, ou des tâches unique au sein d’un workflow en tant que workflow. Windows PowerShell Workflow permet d’adapter et d’exécuter des fichiers XAML et des scripts PowerShell comme des workflows. |
