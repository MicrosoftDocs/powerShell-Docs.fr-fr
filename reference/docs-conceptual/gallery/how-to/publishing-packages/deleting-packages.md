---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Supprimer des packages
ms.openlocfilehash: 6bfb43b95e51d38bd606198cb8d2d9af0aa0be1e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327930"
---
# <a name="deleting-packages"></a>Supprimer des packages

PowerShell Gallery ne prend pas en charge la suppression définitive de packages, car cela provoquerait l’arrêt de tous les éléments qui en dépendent.

Il est en revanche possible de retirer un package de la liste sur la page de gestion des packages du site web.
Quand un package est retiré de la liste, il ne s’affiche plus ni dans la recherche ni dans la liste des packages, aussi bien sur PowerShell Gallery qu’avec les commandes PowerShellGet.
Toutefois, il reste téléchargeable en spécifiant sa version exacte, ce qui permet aux scripts automatisés de continuer à fonctionner.

Si vous pensez vous trouver dans une situation exceptionnelle nécessitant la suppression d’un de vos packages, l’équipe PowerShell Gallery peut s’en charger manuellement.
Par exemple, la violation des droits d’auteur ou un contenu potentiellement dangereux peuvent constituer une raison valable de le supprimer.
Dans ce cas, vous devez soumettre une demande de support par le biais de [PowerShell Gallery](https://www.PowerShellGallery.com).
