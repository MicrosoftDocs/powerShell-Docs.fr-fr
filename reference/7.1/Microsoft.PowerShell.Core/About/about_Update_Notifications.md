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
# <a name="about-update-notifications"></a><span data-ttu-id="febec-104">À propos des notifications de mise à jour</span><span class="sxs-lookup"><span data-stu-id="febec-104">About Update Notifications</span></span>

## <a name="short-description"></a><span data-ttu-id="febec-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="febec-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="febec-106">Informe les utilisateurs au démarrage de PowerShell qu’une nouvelle version de PowerShell a été publiée.</span><span class="sxs-lookup"><span data-stu-id="febec-106">Notifies users on startup of PowerShell that a new version of PowerShell has been released.</span></span>

## <a name="long-description"></a><span data-ttu-id="febec-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="febec-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="febec-108">À compter de PowerShell 7,0, PowerShell utilise des notifications de mise à jour pour alerter les utilisateurs à l’existence de mises à jour de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="febec-108">Beginning with PowerShell 7.0, PowerShell uses update notifications to alert users to the existence of updates to PowerShell.</span></span> <span data-ttu-id="febec-109">Une fois par jour, PowerShell interroge un service en ligne pour déterminer si une version plus récente est disponible.</span><span class="sxs-lookup"><span data-stu-id="febec-109">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="febec-110">Pendant la vérification de la mise à jour au cours de la première session d’une période de 24 heures, pour des raisons de performances, la notification s’affiche uniquement au début des sessions suivantes.</span><span class="sxs-lookup"><span data-stu-id="febec-110">While the update check happens during the first session in a given 24-hour period, for performance reasons, the notification will only be shown on the start of subsequent sessions.</span></span> <span data-ttu-id="febec-111">En outre, pour des raisons de performances, la vérification ne démarrera pas avant au moins 3 secondes après le début de la session.</span><span class="sxs-lookup"><span data-stu-id="febec-111">Also for performance reasons, the check will not start until at least 3 seconds after the session begins.</span></span>

<span data-ttu-id="febec-112">Par défaut, PowerShell s’abonne à l’un des deux canaux de notification différents en fonction de sa version/branche.</span><span class="sxs-lookup"><span data-stu-id="febec-112">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="febec-113">Les versions de PowerShell prises en charge généralement disponibles ne retournent de notifications que pour les versions mises à jour en disponibilité générale (GA).</span><span class="sxs-lookup"><span data-stu-id="febec-113">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="febec-114">La préversion et la version finale (RC) informent des mises à jour de la préversion, de la version finale (RC) et de la version en disponibilité générale (GA).</span><span class="sxs-lookup"><span data-stu-id="febec-114">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="febec-115">Le comportement de notification de mise à jour peut être modifié à l’aide de la variable d’environnement `POWERSHELL_UPDATECHECK`.</span><span class="sxs-lookup"><span data-stu-id="febec-115">The update notification behavior can be changed using the `POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="febec-116">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="febec-116">The following values are supported:</span></span>

- <span data-ttu-id="febec-117">`Off` désactive la fonctionnalité de notification de mise à jour</span><span class="sxs-lookup"><span data-stu-id="febec-117">`Off` turns off the update notification feature</span></span>
- <span data-ttu-id="febec-118">`Default` est identique à ne pas définir `POWERSHELL_UPDATECHECK` :</span><span class="sxs-lookup"><span data-stu-id="febec-118">`Default` is the same as not defining `POWERSHELL_UPDATECHECK`:</span></span>
  - <span data-ttu-id="febec-119">Les versions en disponibilité générale (GA) informent des mises à jour des versions GA</span><span class="sxs-lookup"><span data-stu-id="febec-119">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="febec-120">La préversion/les versions finales (RC) informent des mises à jour des versions en disponibilité générale (GA) et des préversions.</span><span class="sxs-lookup"><span data-stu-id="febec-120">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="febec-121">`LTS` notifie uniquement les mises à jour des versions GA LTS (long-term-service)</span><span class="sxs-lookup"><span data-stu-id="febec-121">`LTS` only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

<span data-ttu-id="febec-122">Les points de terminaison suivants sont actuellement utilisés pour déterminer la version la plus récente de chaque canal :</span><span class="sxs-lookup"><span data-stu-id="febec-122">The following endpoints are currently used for determining the latest version of each channel:</span></span>

- <span data-ttu-id="febec-123">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span><span class="sxs-lookup"><span data-stu-id="febec-123">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span></span>
- <span data-ttu-id="febec-124">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span><span class="sxs-lookup"><span data-stu-id="febec-124">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span></span>
- <span data-ttu-id="febec-125">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span><span class="sxs-lookup"><span data-stu-id="febec-125">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span></span>

<span data-ttu-id="febec-126">La notification de mise à jour n’offre aucun moyen de mettre à jour automatiquement PowerShell.</span><span class="sxs-lookup"><span data-stu-id="febec-126">The update notification doesn't provide any way to automatically update PowerShell.</span></span> <span data-ttu-id="febec-127">À l’avenir, il peut y avoir plus d’instructions ou de fonctionnalités à mettre à jour à partir de PowerShell, mais aujourd’hui, vous devez utiliser le même mécanisme d’installation que celui utilisé pour installer PowerShell pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="febec-127">In the future, there may be more instructions or capabilities to update from within PowerShell, but today, you should use the same install mechanism you used to install PowerShell to update it.</span></span>

