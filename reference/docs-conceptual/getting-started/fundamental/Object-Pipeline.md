---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Pipeline d’objet
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 6102ec6e8fbf38fdc2bc5fa9c583244ef639dec8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30948208"
---
# <a name="object-pipeline"></a>Pipeline d’objet
Les pipelines agissent comme une série de segments de canal connectés. Les éléments se déplaçant dans pipeline passent par chaque segment. Pour créer un pipeline dans Windows PowerShell, vous interconnectez des commandes à l’aide que l’opérateur barre verticale « | » (pipe). La sortie de chaque commande est utilisée en tant qu’entrée pour la commande suivante.

Les pipelines constituent indubitablement le concept plus important utilisé dans les interfaces de ligne de commande. Correctement utilisés, les pipelines non seulement réduisent l’effort que nécessite la saisie de commandes complexes, mais aussi facilitent l’affichage du flux de travail dans les commandes. Une caractéristique utile connexe des pipelines est que, comme ils opèrent sur chaque élément séparément, vous n’avez pas à les modifier selon qu’ils contiennent zéro, un ou plusieurs éléments. En outre, chaque commande dans un pipeline (appelée élément de pipeline) transmet généralement sa sortie à la commande suivante, élément par élément. Généralement, cela réduit la demande de ressources de commandes complexes, et permet de commencer à recevoir la sortie immédiatement.

Dans ce chapitre, nous expliquons en quoi le pipeline Windows PowerShell diffère des pipelines des interpréteurs de commandes les plus populaires, puis présentons des outils de base que vous pouvez utiliser pour contrôler la sortie du pipeline et voir comment celui-ci fonctionne.