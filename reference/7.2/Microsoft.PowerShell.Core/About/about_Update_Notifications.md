---
description: Informe les utilisateurs au démarrage de PowerShell qu’une nouvelle version de PowerShell a été publiée.
Locale: en-US
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Update_Notifications
ms.openlocfilehash: 1a9f8cfec15f83566fdb77175dcc1aed6d9e8c34
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598559"
---
# <a name="about-update-notifications"></a><span data-ttu-id="3a62b-103">À propos des notifications de mise à jour</span><span class="sxs-lookup"><span data-stu-id="3a62b-103">About Update Notifications</span></span>

## <a name="short-description"></a><span data-ttu-id="3a62b-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="3a62b-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="3a62b-105">Informe les utilisateurs au démarrage de PowerShell qu’une nouvelle version de PowerShell a été publiée.</span><span class="sxs-lookup"><span data-stu-id="3a62b-105">Notifies users on startup of PowerShell that a new version of PowerShell has been released.</span></span>

## <a name="long-description"></a><span data-ttu-id="3a62b-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="3a62b-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="3a62b-107">À compter de PowerShell 7,0, PowerShell utilise des notifications de mise à jour pour alerter les utilisateurs à l’existence de mises à jour de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a62b-107">Beginning with PowerShell 7.0, PowerShell uses update notifications to alert users to the existence of updates to PowerShell.</span></span> <span data-ttu-id="3a62b-108">Une fois par jour, PowerShell interroge un service en ligne pour déterminer si une version plus récente est disponible.</span><span class="sxs-lookup"><span data-stu-id="3a62b-108">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="3a62b-109">Pendant la vérification de la mise à jour au cours de la première session d’une période de 24 heures, pour des raisons de performances, la notification s’affiche uniquement au début des sessions suivantes.</span><span class="sxs-lookup"><span data-stu-id="3a62b-109">While the update check happens during the first session in a given 24-hour period, for performance reasons, the notification will only be shown on the start of subsequent sessions.</span></span> <span data-ttu-id="3a62b-110">En outre, pour des raisons de performances, la vérification ne démarrera pas avant au moins 3 secondes après le début de la session.</span><span class="sxs-lookup"><span data-stu-id="3a62b-110">Also for performance reasons, the check will not start until at least 3 seconds after the session begins.</span></span>

<span data-ttu-id="3a62b-111">Par défaut, PowerShell s’abonne à l’un des deux canaux de notification différents en fonction de sa version/branche.</span><span class="sxs-lookup"><span data-stu-id="3a62b-111">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="3a62b-112">Les versions de PowerShell prises en charge généralement disponibles ne retournent de notifications que pour les versions mises à jour en disponibilité générale (GA).</span><span class="sxs-lookup"><span data-stu-id="3a62b-112">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="3a62b-113">La préversion et la version finale (RC) informent des mises à jour de la préversion, de la version finale (RC) et de la version en disponibilité générale (GA).</span><span class="sxs-lookup"><span data-stu-id="3a62b-113">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="3a62b-114">Le comportement de notification de mise à jour peut être modifié à l’aide de la variable d’environnement `POWERSHELL_UPDATECHECK`.</span><span class="sxs-lookup"><span data-stu-id="3a62b-114">The update notification behavior can be changed using the `POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="3a62b-115">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="3a62b-115">The following values are supported:</span></span>

- <span data-ttu-id="3a62b-116">`Off` désactive la fonctionnalité de notification de mise à jour</span><span class="sxs-lookup"><span data-stu-id="3a62b-116">`Off` turns off the update notification feature</span></span>
- <span data-ttu-id="3a62b-117">`Default` est identique à ne pas définir `POWERSHELL_UPDATECHECK` :</span><span class="sxs-lookup"><span data-stu-id="3a62b-117">`Default` is the same as not defining `POWERSHELL_UPDATECHECK`:</span></span>
  - <span data-ttu-id="3a62b-118">Les versions en disponibilité générale (GA) informent des mises à jour des versions GA</span><span class="sxs-lookup"><span data-stu-id="3a62b-118">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="3a62b-119">La préversion/les versions finales (RC) informent des mises à jour des versions en disponibilité générale (GA) et des préversions.</span><span class="sxs-lookup"><span data-stu-id="3a62b-119">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="3a62b-120">`LTS` notifie uniquement les mises à jour des versions GA LTS (long-term-service)</span><span class="sxs-lookup"><span data-stu-id="3a62b-120">`LTS` only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

<span data-ttu-id="3a62b-121">Les points de terminaison suivants sont actuellement utilisés pour déterminer la version la plus récente de chaque canal :</span><span class="sxs-lookup"><span data-stu-id="3a62b-121">The following endpoints are currently used for determining the latest version of each channel:</span></span>

- <span data-ttu-id="3a62b-122">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span><span class="sxs-lookup"><span data-stu-id="3a62b-122">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span></span>
- <span data-ttu-id="3a62b-123">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span><span class="sxs-lookup"><span data-stu-id="3a62b-123">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span></span>
- <span data-ttu-id="3a62b-124">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span><span class="sxs-lookup"><span data-stu-id="3a62b-124">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span></span>

<span data-ttu-id="3a62b-125">La notification de mise à jour n’offre aucun moyen de mettre à jour automatiquement PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a62b-125">The update notification doesn't provide any way to automatically update PowerShell.</span></span> <span data-ttu-id="3a62b-126">À l’avenir, il peut y avoir plus d’instructions ou de fonctionnalités à mettre à jour à partir de PowerShell, mais aujourd’hui, vous devez utiliser le même mécanisme d’installation que celui utilisé pour installer PowerShell pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="3a62b-126">In the future, there may be more instructions or capabilities to update from within PowerShell, but today, you should use the same install mechanism you used to install PowerShell to update it.</span></span>

