---
title: Utilisation de PowerShell dans Docker
description: Guide pratique pour utiliser PowerShell préinstallé dans une image Docker.
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: b16a31a04ca863ab55c7c9718b1a1a973e61ee46
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "80646371"
---
# <a name="using-powershell-in-docker"></a><span data-ttu-id="fa91e-103">Utilisation de PowerShell dans Docker</span><span class="sxs-lookup"><span data-stu-id="fa91e-103">Using PowerShell in Docker</span></span>

<span data-ttu-id="fa91e-104">Nous publions les images Docker avec PowerShell préinstallé.</span><span class="sxs-lookup"><span data-stu-id="fa91e-104">We publish Docker images with PowerShell preinstalled.</span></span> <span data-ttu-id="fa91e-105">Cet article explique comment prendre en main PowerShell dans le conteneur Docker.</span><span class="sxs-lookup"><span data-stu-id="fa91e-105">This article shows you how to get started using PowerShell in the Docker container.</span></span>

## <a name="finding-available-images"></a><span data-ttu-id="fa91e-106">Recherche d’images disponibles</span><span class="sxs-lookup"><span data-stu-id="fa91e-106">Finding available images</span></span>

<span data-ttu-id="fa91e-107">La version 17.05 ou une version plus récente de Docker est nécessaire pour les images publiées.</span><span class="sxs-lookup"><span data-stu-id="fa91e-107">The released images require Docker 17.05 or newer.</span></span> <span data-ttu-id="fa91e-108">Il faut également être en mesure d’exécuter Docker sans `sudo` ni droits d’administrateur local.</span><span class="sxs-lookup"><span data-stu-id="fa91e-108">It is also expected that you are able to run Docker without `sudo` or local administrative rights.</span></span> <span data-ttu-id="fa91e-109">Suivez les [instructions][install] officielles de Docker pour installer `docker` correctement.</span><span class="sxs-lookup"><span data-stu-id="fa91e-109">Please follow Docker's official [instructions][install] to install `docker` correctly.</span></span>

<span data-ttu-id="fa91e-110">Les conteneurs de version dérivent de l’image de distribution officielle, par exemple `centos:7`, puis installent les dépendances et enfin le package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa91e-110">The release containers derive from the official distribution image, such as `centos:7`, then install dependencies, and finally install the PowerShell package.</span></span>

<span data-ttu-id="fa91e-111">Ces conteneurs se trouvent à l’adresse [hub.docker.com/r/microsoft/powershell][docker-release].</span><span class="sxs-lookup"><span data-stu-id="fa91e-111">These containers live at [hub.docker.com/r/microsoft/powershell][docker-release].</span></span>

<span data-ttu-id="fa91e-112">Pour plus d’informations sur ces images Docker, consultez le référentiel [PowerShell-Docker][PowerShell-Docker] sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="fa91e-112">For more information about these Docker images, visit the [PowerShell-Docker][PowerShell-Docker] repository on GitHub.</span></span>

## <a name="using-powershell-in-a-container"></a><span data-ttu-id="fa91e-113">Utilisation de PowerShell dans un conteneur</span><span class="sxs-lookup"><span data-stu-id="fa91e-113">Using PowerShell in a container</span></span>

<span data-ttu-id="fa91e-114">Les étapes suivantes montrent les commandes Docker nécessaires pour télécharger l’image et lancer une session PowerShell interactive.</span><span class="sxs-lookup"><span data-stu-id="fa91e-114">The following steps show the Docker commands required to download the image and start an interactive PowerShell session.</span></span>

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a><span data-ttu-id="fa91e-115">Suppression de l’image quand elle n’est plus nécessaire</span><span class="sxs-lookup"><span data-stu-id="fa91e-115">Remove the image when no longer needed</span></span>

<span data-ttu-id="fa91e-116">La commande suivante permet de supprimer l’image Docker lorsqu’elle n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fa91e-116">The following command is used to delete the Docker image when you no longer need it.</span></span>

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a><span data-ttu-id="fa91e-117">Licences et informations juridiques</span><span class="sxs-lookup"><span data-stu-id="fa91e-117">Legal and Licensing</span></span>

<span data-ttu-id="fa91e-118">PowerShell est concédé sous [licence MIT][].</span><span class="sxs-lookup"><span data-stu-id="fa91e-118">PowerShell is licensed under the [MIT license][].</span></span>

### <a name="windows-docker-file-and-image-licenses"></a><span data-ttu-id="fa91e-119">Licences d’images et de fichiers Windows Docker</span><span class="sxs-lookup"><span data-stu-id="fa91e-119">Windows Docker File and Image Licenses</span></span>

<span data-ttu-id="fa91e-120">En demandant et en utilisant l’image de système d’exploitation des conteneurs Windows, vous reconnaissez, comprenez et acceptez les termes du contrat de licence supplémentaires disponibles sur Docker Hub :</span><span class="sxs-lookup"><span data-stu-id="fa91e-120">By requesting and using the Container OS Image for Windows containers, you acknowledge, understand, and consent to the Supplemental License Terms available on Docker hub:</span></span>

- <span data-ttu-id="fa91e-121">[Windows Server Core][Window Server Core]</span><span class="sxs-lookup"><span data-stu-id="fa91e-121">[Window Server Core][Window Server Core]</span></span>
- <span data-ttu-id="fa91e-122">[Nano Server][Nano Server]</span><span class="sxs-lookup"><span data-stu-id="fa91e-122">[Nano Server][Nano Server]</span></span>

### <a name="telemetry"></a><span data-ttu-id="fa91e-123">Télémétrie</span><span class="sxs-lookup"><span data-stu-id="fa91e-123">Telemetry</span></span>

<span data-ttu-id="fa91e-124">Par défaut, PowerShell collecte des données de télémétrie limitées sans informations d’identification personnelle pour faciliter le développement de ses futures versions.</span><span class="sxs-lookup"><span data-stu-id="fa91e-124">By default, PowerShell collects limited telemetry without personally identifiable information to help aid development of future versions of PowerShell.</span></span> <span data-ttu-id="fa91e-125">Pour refuser l’envoi de données de télémétrie, créez une variable d’environnement nommée `POWERSHELL_TELEMETRY_OPTOUT` et définie sur la valeur `1` avant de lancer PowerShell à partir de l’emplacement d’installation.</span><span class="sxs-lookup"><span data-stu-id="fa91e-125">To opt-out of sending telemetry, create an environment variable called `POWERSHELL_TELEMETRY_OPTOUT` set to a value of `1` before starting PowerShell from the installed location.</span></span> <span data-ttu-id="fa91e-126">Les données de télémétrie que nous collectons relèvent de la [Déclaration de confidentialité Microsoft][privacy].</span><span class="sxs-lookup"><span data-stu-id="fa91e-126">The telemetry we collect falls under the [Microsoft Privacy Statement][privacy].</span></span>

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[Licence MIT]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
