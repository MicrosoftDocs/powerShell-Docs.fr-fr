---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Concepts de base de Windows PowerShell
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: b21c6cd84ea29d5e8085ccf8df2a5a9199e1d859
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950530"
---
# <a name="windows-powershell-basics"></a>Concepts de base de Windows PowerShell
Les interfaces graphiques utilisateur utilisent des concepts de base bien connus de la plupart des utilisateurs d’ordinateur. Les utilisateurs s’appuient sur leur connaissance de ces interfaces pour accomplir des tâches. Les systèmes d’exploitation présentent aux utilisateurs une représentation graphique des éléments qui peuvent être parcourus, généralement avec des menus déroulants pour accéder à des fonctionnalités spécifiques, et des menus contextuels pour accéder à des fonctionnalités spécifique du contexte.

Une interface de ligne de commande (CLI) telle que Windows PowerShell doit utiliser une approche différente pour exposer les informations, car elle ne dispose ni de menus, ni de systèmes graphiques pour aider l’utilisateur. Pour pouvoir utiliser des commandes, vous devez connaître leur nom. Bien que vous puissiez taper des commandes complexes équivalentes aux fonctionnalités d’un environnement graphique, vous devez vous familiariser avec les commandes couramment utilisées et leurs paramètres.

La plupart des CLI n’ont pas de modèles pouvant aider l’utilisateur à apprendre l’interface. Du fait que les CLI étaient les premiers interpréteurs de commandes de système d’exploitation, de nombreux noms de commande et de paramètre ont été sélectionnés de façon arbitraire. Des noms de commande laconiques furent généralement choisis au lieu de noms clairs. Bien que des systèmes d’aide et des normes de conception de commande soient intégrés dans la plupart des CLI, ils ont été généralement été conçus pour assurer la compatibilité avec les commandes d’origine, de sorte que le jeu de commandes est encore aujourd’hui calqué sur des décisions prises il y a plusieurs dizaines d’années.

Windows PowerShell a été conçu pour tirer parti des connaissances historiques de l’utilisateur en matière de CLI. Ce chapitre présente des outils et concepts de base qui peuvent vous aider à apprendre rapidement à utiliser Windows PowerShell. Ils comprennent :

- Utilisation de [Get-Command](/powershell/module/Microsoft.PowerShell.Core/get-command)

- Utilisation de commandes [Cmd.exe](/windows-server/administration/windows-commands/cmd) et [UNIX](/windows/wsl/reference)

- [Utilisation de la saisie semi-automatique vie la touche Tab](../../core-powershell/console/using-tab-expansion.md)

- [Utilisation de Get-Help](./getting-detailed-help-information.md)