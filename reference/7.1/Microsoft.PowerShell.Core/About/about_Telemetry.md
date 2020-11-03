---
description: Décrit les données de télémétrie collectées dans PowerShell et comment les désactiver.
keywords: powershell
Locale: en-US
ms.date: 08/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_telemetry?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Telemetry
ms.openlocfilehash: ef921d0feefe277c2832c0a459ae150c9a6b4acb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207457"
---
# <a name="about-telemetry"></a><span data-ttu-id="9b00f-104">À propos des données de télémétrie</span><span class="sxs-lookup"><span data-stu-id="9b00f-104">About Telemetry</span></span>

## <a name="short-description"></a><span data-ttu-id="9b00f-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="9b00f-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="9b00f-106">Décrit les données de télémétrie collectées dans PowerShell et comment les désactiver.</span><span class="sxs-lookup"><span data-stu-id="9b00f-106">Describes the telemetry collected in PowerShell and how to opt-out.</span></span>

## <a name="long-description"></a><span data-ttu-id="9b00f-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="9b00f-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="9b00f-108">PowerShell envoie des données de télémétrie de base à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9b00f-108">PowerShell sends basic telemetry data to Microsoft.</span></span>
<span data-ttu-id="9b00f-109">Ces données nous permettent de mieux comprendre les environnements dans lesquels PowerShell est utilisé, ainsi que de classer par ordre de priorité les correctifs et les nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="9b00f-109">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>
<span data-ttu-id="9b00f-110">Les points de télémétrie suivants sont enregistrés :</span><span class="sxs-lookup"><span data-stu-id="9b00f-110">The following telemetry points are recorded:</span></span>

- <span data-ttu-id="9b00f-111">Nombre de démarrages de PowerShell par type (console vs API)</span><span class="sxs-lookup"><span data-stu-id="9b00f-111">Count of PowerShell Starts by type (API vs console)</span></span>
- <span data-ttu-id="9b00f-112">Nombre d’utilisations de PowerShell uniques</span><span class="sxs-lookup"><span data-stu-id="9b00f-112">Count of unique PowerShell usage</span></span>
- <span data-ttu-id="9b00f-113">Nombre de types d’exécutions suivants :</span><span class="sxs-lookup"><span data-stu-id="9b00f-113">Count of the following execution types:</span></span>
  - <span data-ttu-id="9b00f-114">Application (commandes natives)</span><span class="sxs-lookup"><span data-stu-id="9b00f-114">Application (native commands)</span></span>
  - <span data-ttu-id="9b00f-115">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="9b00f-115">ExternalScript</span></span>
  - <span data-ttu-id="9b00f-116">Script</span><span class="sxs-lookup"><span data-stu-id="9b00f-116">Script</span></span>
  - <span data-ttu-id="9b00f-117">Fonction</span><span class="sxs-lookup"><span data-stu-id="9b00f-117">Function</span></span>
  - <span data-ttu-id="9b00f-118">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="9b00f-118">Cmdlet</span></span>
- <span data-ttu-id="9b00f-119">Nombre de fonctionnalités expérimentales de Microsoft activées ou fonctionnalités expérimentales fournies avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b00f-119">Count of enabled Microsoft owned experimental features or experimental features shipped with PowerShell</span></span>
- <span data-ttu-id="9b00f-120">Nombre de sessions hébergées</span><span class="sxs-lookup"><span data-stu-id="9b00f-120">Count of hosted sessions</span></span>
- <span data-ttu-id="9b00f-121">Nombre de modules appartenant à Microsoft chargés</span><span class="sxs-lookup"><span data-stu-id="9b00f-121">Count of Microsoft owned modules loaded</span></span>

<span data-ttu-id="9b00f-122">Ces données incluent le nom du système d’exploitation, la version du système d’exploitation, la version de PowerShell et le canal de distribution.</span><span class="sxs-lookup"><span data-stu-id="9b00f-122">This data includes the OS name, OS version, the PowerShell version, and the distribution channel.</span></span>

<span data-ttu-id="9b00f-123">Pour désactiver cette télémétrie, affectez à la variable d’environnement POWERSHELL_TELEMETRY_OPTOUT la valeur true, oui ou 1.</span><span class="sxs-lookup"><span data-stu-id="9b00f-123">To opt-out of this telemetry, set the environment variable POWERSHELL_TELEMETRY_OPTOUT to true, yes, or 1.</span></span>

