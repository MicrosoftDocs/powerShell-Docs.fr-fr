---
ms.openlocfilehash: 84b29953f09eb62eb30f52d84b087eb4f1f90eed
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470645"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="310c5-101">Code de conduite Microsoft Open Source</span><span class="sxs-lookup"><span data-stu-id="310c5-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="310c5-102">Ce projet a adopté le [Code de conduite Microsoft Open Source](https://opensource.microsoft.com/codeofconduct/).</span><span class="sxs-lookup"><span data-stu-id="310c5-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="310c5-103">Pour plus d’informations, consultez le [Forum Aux Questions sur le Code de conduite](https://opensource.microsoft.com/codeofconduct/faq/) ou contactez [opencode@microsoft.com](mailto:opencode@microsoft.com) si vous avez d’autres questions ou des commentaires.</span><span class="sxs-lookup"><span data-stu-id="310c5-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

[live-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[staging-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a><span data-ttu-id="310c5-106">État de la build</span><span class="sxs-lookup"><span data-stu-id="310c5-106">Build Status</span></span>

| <span data-ttu-id="310c5-107">Branche active</span><span class="sxs-lookup"><span data-stu-id="310c5-107">Live Branch</span></span> | <span data-ttu-id="310c5-108">Branche de mise en lots</span><span class="sxs-lookup"><span data-stu-id="310c5-108">Staging Branch</span></span> |
|:------------|:---------------|
| <span data-ttu-id="310c5-109">[![live-badge][]][live-badge]</span><span class="sxs-lookup"><span data-stu-id="310c5-109">[![live-badge][]][live-badge]</span></span> | <span data-ttu-id="310c5-110">[![staging-badge][]][staging-badge]</span><span class="sxs-lookup"><span data-stu-id="310c5-110">[![staging-badge][]][staging-badge]</span></span>

## <a name="powershell-documentation"></a><span data-ttu-id="310c5-111">Documentation de PowerShell</span><span class="sxs-lookup"><span data-stu-id="310c5-111">PowerShell Documentation</span></span>

<span data-ttu-id="310c5-112">Bienvenue dans le référentiel de documents de PowerShell, qui héberge la documentation officielle de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="310c5-112">Welcome to the PowerShell-Docs repository, housing the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="310c5-113">Structure du dépôt</span><span class="sxs-lookup"><span data-stu-id="310c5-113">Repository Structure</span></span>

<span data-ttu-id="310c5-114">Chacun des dossiers de premier niveau suivants dans ce référentiel contient un ensemble de documents qui sont publiés dans [Microsoft Docs](https://docs.microsoft.com/powershell).</span><span class="sxs-lookup"><span data-stu-id="310c5-114">Each of the following top-level folders in this repo contain a DocSet that is published to [Microsoft Docs](https://docs.microsoft.com/powershell).</span></span>

- <span data-ttu-id="310c5-115">[/Developer/](https://docs.microsoft.com/powershell/developer/) est le futur site de la documentation du kit de développement logiciel (SDK) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="310c5-115">[/developer/](https://docs.microsoft.com/powershell/developer/) is the future home of the PowerShell SDK documentation</span></span>
  - <span data-ttu-id="310c5-116">Nous sommes en train de migrer ce contenu à partir de MSDN.</span><span class="sxs-lookup"><span data-stu-id="310c5-116">We are in the process of migrating this content from MSDN</span></span>
- <span data-ttu-id="310c5-117">[/dsc/](https://docs.microsoft.com/powershell/dsc/) correspond à la fonctionnalité de configuration d’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="310c5-117">[/dsc/](https://docs.microsoft.com/powershell/dsc/) is for the Desired State Configuration feature</span></span>
- <span data-ttu-id="310c5-118">[/gallery/](https://docs.microsoft.com/powershell/gallery) correspond à la [PowerShell Gallery](https://www.powershellgallery.com/)</span><span class="sxs-lookup"><span data-stu-id="310c5-118">[/gallery/](https://docs.microsoft.com/powershell/gallery) is for the [PowerShell Gallery](https://www.powershellgallery.com/)</span></span>
- <span data-ttu-id="310c5-119">[/jea/](https://docs.microsoft.com/powershell/jea/) correspond à la fonctionnalité JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="310c5-119">[/jea/](https://docs.microsoft.com/powershell/jea/) is for the Just Enough Administration feature</span></span>
- <span data-ttu-id="310c5-120">[/reference/](https://docs.microsoft.com/powershell/scripting/) correspond aux sujets conceptuels et à la référence de module PowerShell dans les versions 3.0, 4.0, 5.0, 5.1 et 6.0.</span><span class="sxs-lookup"><span data-stu-id="310c5-120">[/reference/](https://docs.microsoft.com/powershell/scripting/) is for PowerShell conceptual topics and module reference across versions 3.0, 4.0, 5.0, 5.1, and 6.0</span></span>
  - <span data-ttu-id="310c5-121">Ce contenu est également la source de contenu d’aide récupéré par l’applet de commande `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="310c5-121">This content is also the source of help content retrieved by the `Get-Help` cmdlet</span></span>
- <span data-ttu-id="310c5-122">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contient les notes de publication pour Windows Management Framework, le package utilisé pour distribuer les nouvelles versions de PowerShell aux versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="310c5-122">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contains release notes for the Windows Management Framework, the package used to distribute new versions of PowerShell to previous versions of Windows.</span></span>

## <a name="contributing"></a><span data-ttu-id="310c5-123">Contribution</span><span class="sxs-lookup"><span data-stu-id="310c5-123">Contributing</span></span>

<span data-ttu-id="310c5-124">Nous fusionnons activement les contributions dans ce dépôt via une [demande Pull](https://help.github.com/articles/using-pull-requests/) dans la branche de *préproduction*.</span><span class="sxs-lookup"><span data-stu-id="310c5-124">We actively merge contributions into this repository via [pull request](https://help.github.com/articles/using-pull-requests/) into the *staging* branch.</span></span>
<span data-ttu-id="310c5-125">Notez qu’avant d’envoyer une demande Pull, vous devez [signer un contrat de licence de contribution](https://cla.microsoft.com/) pour garantir que la communauté est libre d’utiliser vos envois.</span><span class="sxs-lookup"><span data-stu-id="310c5-125">Please note that before you submit a pull request you must [sign a Contribution License Agreement](https://cla.microsoft.com/) to ensure that the community is free to use your submissions.</span></span>

<span data-ttu-id="310c5-126">Pour plus d’informations sur la contribution, lisez notre [guide du contributeur](CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="310c5-126">For more information on contributing, read our [contributor's guide](CONTRIBUTING.md).</span></span>
<span data-ttu-id="310c5-127">Le guide du contributeur contient des informations détaillées sur la manière de contribuer à la documentation, les outils, ainsi que sur les exigences concernant le style et la mise en forme.</span><span class="sxs-lookup"><span data-stu-id="310c5-127">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span>
<span data-ttu-id="310c5-128">Utilisez les modèles « Issue » et « Pull Request » afin que la documentation soit cohérente entre les versions.</span><span class="sxs-lookup"><span data-stu-id="310c5-128">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="310c5-129">Licences</span><span class="sxs-lookup"><span data-stu-id="310c5-129">Licenses</span></span>

<span data-ttu-id="310c5-130">Il existe deux fichiers de licence pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="310c5-130">There are two license files for this project.</span></span>
<span data-ttu-id="310c5-131">La licence MIT s’applique au code contenu dans ce dépôt.</span><span class="sxs-lookup"><span data-stu-id="310c5-131">The MIT License applies to the code contained in this repo.</span></span>
<span data-ttu-id="310c5-132">La licence Creative Commons s’applique à la documentation.</span><span class="sxs-lookup"><span data-stu-id="310c5-132">The Creative Commons license applies to the documentation.</span></span>