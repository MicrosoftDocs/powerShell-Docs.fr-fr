---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Résolution des problèmes des applets de commande
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "72352106"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="37624-103">Résolution des problèmes des applets de commande</span><span class="sxs-lookup"><span data-stu-id="37624-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="37624-104">Comment résoudre le problème « Avertissement : Échec du téléchargement du package 'nom_de_votre_package' »</span><span class="sxs-lookup"><span data-stu-id="37624-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="37624-105">Il a été signalé que `Install-Module` ou `Update-Module` échouait parfois sur certains ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="37624-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="37624-106">Selon nos recherches, cela est en rapport avec la connexion réseau.</span><span class="sxs-lookup"><span data-stu-id="37624-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="37624-107">Nous avons récemment mis à jour le fournisseur NuGet afin qu’il puisse télécharger des packages de façon fiable.</span><span class="sxs-lookup"><span data-stu-id="37624-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="37624-108">Vous pouvez suivre les instructions ci-dessous pour installer la build la plus récente du fournisseur NuGet, puis installer ou mettre à jour votre module.</span><span class="sxs-lookup"><span data-stu-id="37624-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="37624-109">Utilisons le module « Azure » à titre d’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="37624-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a><span data-ttu-id="37624-110">Points de terminaison réseau requis</span><span class="sxs-lookup"><span data-stu-id="37624-110">Required network endpoints</span></span>

<span data-ttu-id="37624-111">Les cmdlets d’installation et de mise à jour nécessitent un accès à Internet pour se connecter aux points de terminaison réseau utilisés par PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="37624-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="37624-112">Assurez-vous que vos stratégies d’accès réseau vous permettent de vous connecter aux points de terminaison suivants.</span><span class="sxs-lookup"><span data-stu-id="37624-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="37624-113">oneget.org</span><span class="sxs-lookup"><span data-stu-id="37624-113">oneget.org</span></span>
- <span data-ttu-id="37624-114">go.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="37624-114">go.microsoft.com</span></span>
- <span data-ttu-id="37624-115">az818661.vo.msecnd.net</span><span class="sxs-lookup"><span data-stu-id="37624-115">az818661.vo.msecnd.net</span></span>
- <span data-ttu-id="37624-116">www.powershellgallery.com</span><span class="sxs-lookup"><span data-stu-id="37624-116">www.powershellgallery.com</span></span>
- <span data-ttu-id="37624-117">devopsgallerystorage.blob.core.windows.net</span><span class="sxs-lookup"><span data-stu-id="37624-117">devopsgallerystorage.blob.core.windows.net</span></span>
