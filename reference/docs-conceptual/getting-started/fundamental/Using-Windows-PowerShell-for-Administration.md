---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation de Windows PowerShell pour l’administration
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: 69790ddd6bae26dd18e30af860bad4c749cd86a5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954328"
---
# <a name="using-windows-powershell-for-administration"></a>Utilisation de Windows PowerShell pour l’administration
L’objectif fondamental de Windows PowerShell est d’améliorer et de faciliter le contrôle administratif des systèmes, soit de façon interactive, ou à l’aide de scripts. Ce chapitre décrit des solutions à de nombreux problèmes spécifiques liés à l’administration de systèmes Windows avec Windows PowerShell. Bien que nous n’ayons pas évoqué les scripts ou fonctions dans le Guide de l’utilisateur de Windows PowerShell, les solutions peuvent être utilisées à partir de scripts ou en tant que fonctions ultérieurement. Nous allons montrer des exemples incluant des fonctions dans le cadre de solutions visant à résoudre des problèmes.

Dans les descriptions de solutions, vous verrez un mélange de solutions utilisant des applets de commande spécifiques, l’applet de commande générale Get-WmiObject, voire des outils externes faisant partie des infrastructures Windows et .NET Framework. L’utilisation d’outils externes fait partie de l’objectif de conception à long terme de Windows PowerShell. Même si le système s’étoffe, les utilisateurs rencontreront toujours des situations où les jeux d’outils disponibles ne feront pas tout ce dont ils ont besoin. Au lieu de favoriser la dépendance des seules implémentations d’applets de commande, Windows PowerShell essaie prendre en charge l’intégration de solutions à partir de tous les scénarios alternatifs possibles.