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
# <a name="about-telemetry"></a><span data-ttu-id="70199-103">À propos des données de télémétrie</span><span class="sxs-lookup"><span data-stu-id="70199-103">About Telemetry</span></span>

## <a name="short-description"></a><span data-ttu-id="70199-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="70199-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="70199-105">Décrit les données de télémétrie collectées dans PowerShell et comment les désactiver.</span><span class="sxs-lookup"><span data-stu-id="70199-105">Describes the telemetry collected in PowerShell and how to opt-out.</span></span>

## <a name="long-description"></a><span data-ttu-id="70199-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="70199-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="70199-107">PowerShell envoie des données de télémétrie de base à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="70199-107">PowerShell sends basic telemetry data to Microsoft.</span></span>
<span data-ttu-id="70199-108">Ces données nous permettent de mieux comprendre les environnements dans lesquels PowerShell est utilisé, ainsi que de classer par ordre de priorité les correctifs et les nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="70199-108">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>
<span data-ttu-id="70199-109">Les points de télémétrie suivants sont enregistrés :</span><span class="sxs-lookup"><span data-stu-id="70199-109">The following telemetry points are recorded:</span></span>

- <span data-ttu-id="70199-110">Nombre de démarrages de PowerShell par type (console vs API)</span><span class="sxs-lookup"><span data-stu-id="70199-110">Count of PowerShell Starts by type (API vs console)</span></span>
- <span data-ttu-id="70199-111">Nombre d’utilisations de PowerShell uniques</span><span class="sxs-lookup"><span data-stu-id="70199-111">Count of unique PowerShell usage</span></span>
- <span data-ttu-id="70199-112">Nombre de types d’exécutions suivants :</span><span class="sxs-lookup"><span data-stu-id="70199-112">Count of the following execution types:</span></span>
  - <span data-ttu-id="70199-113">Application (commandes natives)</span><span class="sxs-lookup"><span data-stu-id="70199-113">Application (native commands)</span></span>
  - <span data-ttu-id="70199-114">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="70199-114">ExternalScript</span></span>
  - <span data-ttu-id="70199-115">Script</span><span class="sxs-lookup"><span data-stu-id="70199-115">Script</span></span>
  - <span data-ttu-id="70199-116">Fonction</span><span class="sxs-lookup"><span data-stu-id="70199-116">Function</span></span>
  - <span data-ttu-id="70199-117">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="70199-117">Cmdlet</span></span>
- <span data-ttu-id="70199-118">Nombre de fonctionnalités expérimentales de Microsoft activées ou fonctionnalités expérimentales fournies avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="70199-118">Count of enabled Microsoft owned experimental features or experimental features shipped with PowerShell</span></span>
- <span data-ttu-id="70199-119">Nombre de sessions hébergées</span><span class="sxs-lookup"><span data-stu-id="70199-119">Count of hosted sessions</span></span>
- <span data-ttu-id="70199-120">Nombre de modules appartenant à Microsoft chargés</span><span class="sxs-lookup"><span data-stu-id="70199-120">Count of Microsoft owned modules loaded</span></span>

<span data-ttu-id="70199-121">Ces données incluent le nom du système d’exploitation, la version du système d’exploitation, la version de PowerShell et le canal de distribution.</span><span class="sxs-lookup"><span data-stu-id="70199-121">This data includes the OS name, OS version, the PowerShell version, and the distribution channel.</span></span>

<span data-ttu-id="70199-122">Pour désactiver cette télémétrie, affectez à la variable d’environnement POWERSHELL_TELEMETRY_OPTOUT la valeur true, oui ou 1.</span><span class="sxs-lookup"><span data-stu-id="70199-122">To opt-out of this telemetry, set the environment variable POWERSHELL_TELEMETRY_OPTOUT to true, yes, or 1.</span></span>

