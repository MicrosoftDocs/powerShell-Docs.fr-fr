---
ms.date: 01/25/2021
title: Résolution des problèmes des applets de commande
description: Cet article fournit des informations et les étapes pour résoudre les erreurs à l’aide de PowerShell Gallery
ms.openlocfilehash: 8139147683b655b5f8532c3068387db6df12a98f
ms.sourcegitcommit: 0f003644684422e425a59b7361121e05ac772e15
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98771806"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="b0fab-103">Résolution des problèmes des applets de commande</span><span class="sxs-lookup"><span data-stu-id="b0fab-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="b0fab-104">Comment résoudre le problème « Avertissement : Échec du téléchargement du package 'nom_de_votre_package' »</span><span class="sxs-lookup"><span data-stu-id="b0fab-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="b0fab-105">Il a été signalé que `Install-Module` ou `Update-Module` échouait parfois sur certains ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="b0fab-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="b0fab-106">Selon nos recherches, cela est en rapport avec la connexion réseau.</span><span class="sxs-lookup"><span data-stu-id="b0fab-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="b0fab-107">Nous avons récemment mis à jour le fournisseur NuGet afin qu’il puisse télécharger des packages de façon fiable.</span><span class="sxs-lookup"><span data-stu-id="b0fab-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="b0fab-108">Vous pouvez suivre les instructions ci-dessous pour installer la build la plus récente du fournisseur NuGet, puis installer ou mettre à jour votre module.</span><span class="sxs-lookup"><span data-stu-id="b0fab-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="b0fab-109">Utilisons le module « Azure » à titre d’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b0fab-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

## <a name="required-network-endpoints"></a><span data-ttu-id="b0fab-110">Points de terminaison réseau requis</span><span class="sxs-lookup"><span data-stu-id="b0fab-110">Required network endpoints</span></span>

<span data-ttu-id="b0fab-111">Les cmdlets d’installation et de mise à jour nécessitent un accès à Internet pour se connecter aux points de terminaison réseau utilisés par PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b0fab-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="b0fab-112">Assurez-vous que vos stratégies d’accès réseau vous permettent de vous connecter aux points de terminaison suivants.</span><span class="sxs-lookup"><span data-stu-id="b0fab-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="b0fab-113">`psg-prod-eastus.azureedge.net` - nom d'hôte CDN</span><span class="sxs-lookup"><span data-stu-id="b0fab-113">`psg-prod-eastus.azureedge.net` - CDN hostname</span></span>
- <span data-ttu-id="b0fab-114">`az818661.vo.msecnd.net` - nom d'hôte CDN</span><span class="sxs-lookup"><span data-stu-id="b0fab-114">`az818661.vo.msecnd.net` - CDN hostname</span></span>
- <span data-ttu-id="b0fab-115">`devopsgallerystorage.blob.core.windows.net` - nom d’hôte du compte de stockage</span><span class="sxs-lookup"><span data-stu-id="b0fab-115">`devopsgallerystorage.blob.core.windows.net` - storage account hostname</span></span>
- <span data-ttu-id="b0fab-116">`*.powershellgallery.com` - site web</span><span class="sxs-lookup"><span data-stu-id="b0fab-116">`*.powershellgallery.com` - website</span></span>
- <span data-ttu-id="b0fab-117">`go.microsoft.com` - service de redirection</span><span class="sxs-lookup"><span data-stu-id="b0fab-117">`go.microsoft.com` - redirection service</span></span>
- <span data-ttu-id="b0fab-118">`onegetcdn.azureedge.net` - amorcer le fournisseur NuGet dans `PowerShellGet/PackageManagement`</span><span class="sxs-lookup"><span data-stu-id="b0fab-118">`onegetcdn.azureedge.net` - bootstrap the NuGet Provider in `PowerShellGet/PackageManagement`</span></span>

> [!NOTE]
> <span data-ttu-id="b0fab-119">Les applets de commande qui interagissent avec PowerShell Gallery peuvent échouer avec des erreurs inattendues en cas d’arrêt des services PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b0fab-119">Cmdlets that interact with the PowerShell Gallery can fail with unexpected errors when there is an outage of the PowerShell Gallery services.</span></span> <span data-ttu-id="b0fab-120">Pour afficher l’état actuel de PowerShell Gallery, consultez la page [État de PowerShell Gallery](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="b0fab-120">To see the current status of the PowerShell Gallery, see the [PowerShell Gallery Status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) page on GitHub.</span></span>
