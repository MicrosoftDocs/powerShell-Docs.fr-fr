---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Présentation des concepts importants de Windows PowerShell
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: 07ceaa2f3e6a192c6281cb4c99aed4c3f66afc7e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951084"
---
# <a name="understanding-important-windows-powershell-concepts"></a>Présentation des concepts importants de Windows PowerShell
La conception de Windows PowerShell intègre des concepts de différents environnements. Plusieurs d’entre eux sont déjà familiers aux utilisateurs ayant une expérience d’interpréteurs de commandes ou d’environnements de programmation spécifiques, mais très peu de gens les connaissent tous. L’examen de certains de ces concepts permet d’avoir une vue d’ensemble utile de l’interpréteur de commandes.

### <a name="commands-are-not-text-based"></a>Les commandes ne sont pas basées sur du texte
Contrairement aux commandes d’interface de ligne de commande traditionnelles, les applets de commande Windows PowerShell sont conçues pour traiter des informations structurées comme des objets, qui sont plus que des chaînes de caractères s’affichant à l’écran. Une sortie de commande comporte toujours des informations supplémentaires que vous pouvez utiliser si nécessaire. Nous approfondissons ce sujet dans ce document.

Si vous avez utilisé des outils de traitement de texte pour traiter des données de ligne de commande par le passé, vous constaterez qu’ils se comportent différemment si vous tentez de les utiliser dans Windows PowerShell. Dans la plupart des cas, vous n’avez pas besoin d’outils de traitement texte pour extraire des informations spécifiques. Vous pouvez accéder à des portions de données directement à l’aide des commandes de manipulation d’objets standard de Windows PowerShell.

### <a name="the-command-family-is-extensible"></a>La famille de commandes est extensible
Des interfaces telles que Cmd.exe n’offrent aucun moyen d’étendre directement le jeu de commandes intégré. Vous pouvez créer des outils en ligne de commande externes qui s’exécutent dans Cmd.exe, mais ceux-ci n’ont pas de services tels que l’intégration de l’aide, et Cmd.exe ne détermine pas automatiquement qu’il s’agit de commandes valides.

Les commandes binaires natives de Windows PowerShell, appelées *applets de commande* peuvent être complétées par des applets de commande que vous créez et ajoutez à Windows PowerShell à l’aide de composants logiciels enfichables. Les *composants logiciels enfichables* de Windows PowerShell sont compilés, à l’instar des outils binaires dans toute autre interface. Vous pouvez les utiliser pour ajouter des fournisseurs Windows PowerShell à l’interpréteur de commandes, ainsi que de nouvelles applets de commande.

En raison de la spécificité des commandes internes de Windows PowerShell, nous les appelons *applets de commande*.

> [!NOTE]
> Windows PowerShell peut exécuter des commandes autres que des applets de commande. Nous ne les décrivons pas en détail dans le Guide de l’utilisateur de Windows PowerShell, mais il est utile de les connaître en tant que catégories de types de commandes. Windows PowerShell prend en charge des scripts analogues aux scripts de l’interpréteur de commande UNIX et aux fichiers de commandes de Cmd.exe, mais dont l’extension de nom de fichier est .ps1. Windows PowerShell permet également de créer des fonctions internes directement utilisables dans l’interface ou dans des scripts.

### <a name="windows-powershell-handles-console-input-and-display"></a>Windows PowerShell gère l’entrée et l’affichage sur la console
Lorsque vous tapez une commande, Windows PowerShell traite toujours directement la saisie de la ligne de commande. Windows PowerShell met également en forme la sortie à l’écran. C’est important, car cela réduit le travail requis de chaque applet de commande et vous garantit de pouvoir toujours opérer de la même manière, quelle que soit l’applet de commande que vous utilisez. Un exemple de la manière dont cela simplifie la vie tant des développeurs d’outils que des utilisateurs, est l’aide relative à la ligne de commande.

Les outils en ligne de commande traditionnels ont leurs propres modes de demande et d’affichage de l’aide. Certains outils en ligne de commande utilisent **/?** pour déclencher l’affichage de l’aide. D’autres utilisent **-?**, **/H**, voire **//**. Certains affichent l’aide dans une fenêtre d’interface graphique utilisateur, plutôt que dans l’affichage de la console. Certains outils complexes, tels que des programmes de mise à jour d’application, décompressent des fichiers internes avant d’afficher leur aide. Si vous utilisez un paramètre incorrect, l’outil peut ignorer ce que vous avez tapé et commencer à exécuter une tâche automatiquement.

Lorsque vous entrez une commande dans Windows PowerShell, tout ce que vous saisissez est automatiquement analysé et pré-traité. Si vous utilisez le paramètre **-?** avec une applet de commande Windows PowerShell, il signifie toujours « afficher l’aide pour cette commande ». Les développeurs d’applets de commande n’ont pas besoin d’analyser la commande ; il leur suffit de fournir le texte d’aide.

Il est important de comprendre que les fonctionnalités d’aide de Windows PowerShell sont disponibles même lorsque vous exécutez des outils en ligne de commande traditionnels dans Windows PowerShell. Windows PowerShell traite les paramètres et transmet les résultats aux outils externes.

> [!NOTE]
> Si vous exécutez une application graphique dans Windows PowerShell, la fenêtre de l’application s’ouvre. Windows PowerShell intervient uniquement lors du traitement de l’entrée de ligne de commande que vous saisissez ou lors du renvoi de la sortie de l’application à la fenêtre de la console. Cela n’affecte en rien le fonctionnement interne de l’application.

### <a name="windows-powershell-uses-some-c-syntax"></a>Windows PowerShell utilise une syntaxe C#
Windows PowerShell dispose de fonctionnalités et de mots clés de syntaxe qui sont très similaires à ceux utilisés dans le langage de programmation C#, car Windows PowerShell est basé sur .NET Framework. L’apprentissage de Windows PowerShell facilite sensiblement l’apprentissage de C#, si ce langage vous intéresse.

Si vous n’êtes pas programmeur C#, cette similitude est sans importance. En revanche, si le langage C# vous est familier, les similitudes peuvent faciliter sensiblement l’apprentissage de Windows PowerShell.