---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Résolution des problèmes des applets de commande
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328300"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="53203-103">Résolution des problèmes des applets de commande</span><span class="sxs-lookup"><span data-stu-id="53203-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="53203-104">Comment résoudre le problème « Avertissement : Échec du téléchargement du package 'nom_de_votre_package' »</span><span class="sxs-lookup"><span data-stu-id="53203-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="53203-105">Il a été signalé que `Install-Module` ou `Update-Module` échouait parfois sur certains ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="53203-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="53203-106">Selon nos recherches, cela est en rapport avec la connexion réseau.</span><span class="sxs-lookup"><span data-stu-id="53203-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="53203-107">Nous avons récemment mis à jour le fournisseur NuGet afin qu’il puisse télécharger des packages de façon fiable.</span><span class="sxs-lookup"><span data-stu-id="53203-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="53203-108">Vous pouvez suivre les instructions ci-dessous pour installer la build la plus récente du fournisseur NuGet, puis installer ou mettre à jour votre module.</span><span class="sxs-lookup"><span data-stu-id="53203-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="53203-109">Utilisons le module « Azure » à titre d’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="53203-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```