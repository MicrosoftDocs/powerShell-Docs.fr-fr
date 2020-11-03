---
description: Informe les utilisateurs au démarrage de PowerShell qu’une nouvelle version de PowerShell a été publiée.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Update_Notifications
ms.openlocfilehash: 258eb9316ba063069d032bc115bdeb4614666f37
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208377"
---
# <a name="about-update-notifications"></a>À propos des notifications de mise à jour

## <a name="short-description"></a>DESCRIPTION COURTE

Informe les utilisateurs au démarrage de PowerShell qu’une nouvelle version de PowerShell a été publiée.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

À compter de PowerShell 7,0, PowerShell utilise des notifications de mise à jour pour alerter les utilisateurs à l’existence de mises à jour de PowerShell. Une fois par jour, PowerShell interroge un service en ligne pour déterminer si une version plus récente est disponible.

> [!NOTE]
> Pendant la vérification de la mise à jour au cours de la première session d’une période de 24 heures, pour des raisons de performances, la notification s’affiche uniquement au début des sessions suivantes. En outre, pour des raisons de performances, la vérification ne démarrera pas avant au moins 3 secondes après le début de la session.

Par défaut, PowerShell s’abonne à l’un des deux canaux de notification différents en fonction de sa version/branche. Les versions de PowerShell prises en charge généralement disponibles ne retournent de notifications que pour les versions mises à jour en disponibilité générale (GA). La préversion et la version finale (RC) informent des mises à jour de la préversion, de la version finale (RC) et de la version en disponibilité générale (GA).

Le comportement de notification de mise à jour peut être modifié à l’aide de la variable d’environnement `POWERSHELL_UPDATECHECK`. Les valeurs suivantes sont admises :

- `Off` désactive la fonctionnalité de notification de mise à jour
- `Default` est identique à ne pas définir `POWERSHELL_UPDATECHECK` :
  - Les versions en disponibilité générale (GA) informent des mises à jour des versions GA
  - La préversion/les versions finales (RC) informent des mises à jour des versions en disponibilité générale (GA) et des préversions.
- `LTS` notifie uniquement les mises à jour des versions GA LTS (long-term-service)

Les points de terminaison suivants sont actuellement utilisés pour déterminer la version la plus récente de chaque canal :

- `LTS`: https://aka.ms/pwsh-buildinfo-lts
- `Stable`: https://aka.ms/pwsh-buildinfo-stable
- `Preview`: https://aka.ms/pwsh-buildinfo-preview

La notification de mise à jour n’offre aucun moyen de mettre à jour automatiquement PowerShell. À l’avenir, il peut y avoir plus d’instructions ou de fonctionnalités à mettre à jour à partir de PowerShell, mais aujourd’hui, vous devez utiliser le même mécanisme d’installation que celui utilisé pour installer PowerShell pour le mettre à jour.

