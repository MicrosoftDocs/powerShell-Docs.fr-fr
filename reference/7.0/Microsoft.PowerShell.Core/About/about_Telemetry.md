---
description: Décrit les données de télémétrie collectées dans PowerShell et comment les désactiver.
keywords: powershell
Locale: en-US
ms.date: 08/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_telemetry?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Telemetry
ms.openlocfilehash: 4aeab828d66d1f015946051419facd81ce2b78c1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206553"
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
