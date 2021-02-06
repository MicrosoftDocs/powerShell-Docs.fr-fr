---
description: Décrit les données de télémétrie collectées dans PowerShell et comment les désactiver.
Locale: en-US
ms.date: 08/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_telemetry?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Telemetry
ms.openlocfilehash: 677d43b405fdc92e6b68d6e903847b11cb671a2c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598165"
---
# <a name="about-telemetry"></a>À propos des données de télémétrie

## <a name="short-description"></a>DESCRIPTION COURTE

Décrit les données de télémétrie collectées dans PowerShell et comment les désactiver.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

PowerShell envoie des données de télémétrie de base à Microsoft.
Ces données nous permettent de mieux comprendre les environnements dans lesquels PowerShell est utilisé, ainsi que de classer par ordre de priorité les correctifs et les nouvelles fonctionnalités.
Les points de télémétrie suivants sont enregistrés :

- Nombre de démarrages de PowerShell par type (console vs API)
- Nombre d’utilisations de PowerShell uniques
- Nombre de types d’exécutions suivants :
  - Application (commandes natives)
  - ExternalScript
  - Script
  - Fonction
  - Applet de commande
- Nombre de fonctionnalités expérimentales de Microsoft activées ou fonctionnalités expérimentales fournies avec PowerShell
- Nombre de sessions hébergées
- Nombre de modules appartenant à Microsoft chargés

Ces données incluent le nom du système d’exploitation, la version du système d’exploitation, la version de PowerShell et le canal de distribution.

Pour désactiver cette télémétrie, affectez à la variable d’environnement POWERSHELL_TELEMETRY_OPTOUT la valeur true, oui ou 1.

