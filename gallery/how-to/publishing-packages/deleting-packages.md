---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Supprimer des packages
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084162"
---
# <a name="deleting-packages"></a>Supprimer des packages

PowerShell Gallery ne prend pas en charge la suppression définitive de packages, car cela provoquerait l’arrêt de tous les éléments qui en dépendent.

Il est en revanche possible de retirer un package de la liste sur la page de gestion des packages du site web.
Quand un package est retiré de la liste, il ne s’affiche plus ni dans la recherche ni dans la liste des packages, aussi bien sur PowerShell Gallery qu’avec les commandes PowerShellGet.
Toutefois, il reste téléchargeable en spécifiant sa version exacte, ce qui permet aux scripts automatisés de continuer à fonctionner.

Si vous pensez vous trouver dans une situation exceptionnelle nécessitant la suppression d’un de vos packages, l’équipe PowerShell Gallery peut s’en charger manuellement.
Par exemple, la violation des droits d’auteur ou un contenu potentiellement dangereux peuvent constituer une raison valable de le supprimer.
Dans ce cas, vous devez soumettre une demande de support par le biais de [PowerShell Gallery](http://www.PowerShellGallery.com).
