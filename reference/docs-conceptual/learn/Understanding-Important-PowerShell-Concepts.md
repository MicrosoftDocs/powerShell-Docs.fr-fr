---
ms.date: 08/23/2018
keywords: powershell,applet de commande
title: Présentation des concepts importants de PowerShell
ms.openlocfilehash: 8f9af370db46ea47dbccbabb7cc90fc27b8f2765
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030982"
---
# <a name="understanding-important-powershell-concepts"></a>Présentation des concepts importants de PowerShell

La conception de PowerShell intègre des concepts de différents environnements. Plusieurs concepts seront familiers aux personnes ayant une expérience des interpréteurs de commandes ou des environnements de programmation. Toutefois, peu de gens les connaissent tous. L’examen de certains de ces concepts permet d’avoir une vue d’ensemble utile de l’interpréteur de commandes.

## <a name="output-is-object-based"></a>La sortie est basée sur les objets

Contrairement aux interfaces de ligne de commande traditionnelles, les applets de commande PowerShell sont conçues pour traiter des objets.
Un objet est une information structurée qui va au-delà de la seule chaîne de caractères s’affichant à l’écran. Une sortie de commande comporte toujours des informations supplémentaires que vous pouvez utiliser si nécessaire.

Si vous avez utilisé des outils de traitement de texte pour traiter des données dans le passé, vous constaterez qu’ils se comportent différemment lorsqu’ils sont utilisés dans PowerShell. Dans la plupart des cas, vous n’avez pas besoin d’outils de traitement texte pour extraire des informations spécifiques. Vous accédez directement à des portions de données à l’aide de la syntaxe d’objet PowerShell standard.

## <a name="the-command-family-is-extensible"></a>La famille de commandes est extensible

Les interfaces telles que **cmd.exe** n’offrent aucun moyen d’étendre directement le jeu de commandes intégré. Vous pouvez créer des outils en ligne de commande externes qui s’exécutent dans **cmd.exe**. Mais ces outils externes ne proposent pas de services comme l’intégration de l’aide. **cmd.exe** ne sait pas automatiquement que ces outils externes sont des commandes valides.

Les commandes natives dans PowerShell sont appelées *cmdlets* (prononcé applets de commande). Vous pouvez créer vos propres modules et fonctions de cmdlets à l’aide de codes ou de scripts compilés. Les modules peuvent ajouter des cmdlets et des fournisseurs à l’interpréteur de commandes. PowerShell prend également en charge des scripts analogues à ceux de l’interpréteur de commande UNIX et aux fichiers de traitement **cmd.exe**.

## <a name="powershell-handles-console-input-and-display"></a>PowerShell gère l’entrée et l’affichage sur la console

Lorsque vous tapez une commande, PowerShell traite toujours directement la saisie de la ligne de commande. PowerShell met également en forme la sortie sur écran. Cette différence est importante, car elle réduit le travail requis de chaque cmdlet. Elle garantit que vous pouvez toujours procéder de la même façon avec chaque cmdlet. Les développeurs de cmdlet n’ont besoin ni d’écrire du code pour analyser les arguments de ligne de commande, ni de mettre en forme la sortie.

Les outils en ligne de commande traditionnels ont leurs propres modes de demande et d’affichage de l’aide. Certains outils en ligne de commande utilisent **/?** pour déclencher l’affichage de l’aide. D’autres utilisent **-?** , **/H**, voire **//** . Certains affichent l’aide dans une fenêtre d’interface graphique utilisateur, plutôt que dans l’affichage de la console. Si vous utilisez un paramètre incorrect, l’outil peut ignorer ce que vous avez tapé et commencer à exécuter une tâche automatiquement.
Dans la mesure où PowerShell analyse et traite automatiquement la ligne de commande, le paramètre **- ?** signifie toujours « afficher l’aide de cette commande ».

> [!NOTE]
> Si vous exécutez une application graphique dans PowerShell, la fenêtre de l’application s’ouvre.
> PowerShell intervient uniquement lors du traitement de l’entrée de ligne de commande que vous saisissez ou lors du renvoi de la sortie de l’application à la fenêtre de la console. Cela n’affecte en rien le fonctionnement interne de l’application.

## <a name="powershell-uses-some-c-syntax"></a>PowerShell utilise une syntaxe C#

PowerShell est basé sur .NET Framework. Il a en commun certaines fonctionnalités de la syntaxe et des mots clés avec le langage de programmation C#. L’apprentissage de PowerShell peut grandement faciliter celui de C#. Si le langage C# vous est déjà familier, ces similitudes peuvent faciliter l’apprentissage de PowerShell.
