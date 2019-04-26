---
ms.openlocfilehash: 6e36e6599e36218ce2a925dceda7aa0ee6811057
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068823"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="d5392-101">Code de conduite Microsoft Open Source</span><span class="sxs-lookup"><span data-stu-id="d5392-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="d5392-102">Ce projet a adopté le [Code de conduite Microsoft Open Source](https://opensource.microsoft.com/codeofconduct/).</span><span class="sxs-lookup"><span data-stu-id="d5392-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="d5392-103">Pour plus d’informations, consultez le [Forum Aux Questions sur le Code de conduite](https://opensource.microsoft.com/codeofconduct/faq/) ou contactez [opencode@microsoft.com](mailto:opencode@microsoft.com) si vous avez d’autres questions ou des commentaires.</span><span class="sxs-lookup"><span data-stu-id="d5392-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

<span data-ttu-id="d5392-104">[![État de la build](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)</span><span class="sxs-lookup"><span data-stu-id="d5392-104">[![Build status](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)</span></span>

## <a name="powershell-documentation"></a><span data-ttu-id="d5392-105">Documentation de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5392-105">PowerShell Documentation</span></span>

<span data-ttu-id="d5392-106">Bienvenue dans le référentiel de documents de PowerShell, qui héberge la documentation officielle de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5392-106">Welcome to the PowerShell-Docs repository, housing the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="d5392-107">Structure du dépôt</span><span class="sxs-lookup"><span data-stu-id="d5392-107">Repository Structure</span></span>

<span data-ttu-id="d5392-108">Chacun des dossiers de premier niveau suivants dans ce référentiel contient un ensemble de documents qui sont publiés dans [Microsoft Docs](https://docs.microsoft.com/powershell).</span><span class="sxs-lookup"><span data-stu-id="d5392-108">Each of the following top-level folders in this repo contain a DocSet that is published to [Microsoft Docs](https://docs.microsoft.com/powershell).</span></span>

- <span data-ttu-id="d5392-109">[/Developer/](https://docs.microsoft.com/powershell/developer/) est le futur site de la documentation du kit de développement logiciel (SDK) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5392-109">[/developer/](https://docs.microsoft.com/powershell/developer/) is the future home of the PowerShell SDK documentation</span></span>
  - <span data-ttu-id="d5392-110">Nous sommes en train de migrer ce contenu à partir de MSDN.</span><span class="sxs-lookup"><span data-stu-id="d5392-110">We are in the process of migrating this content from MSDN</span></span>
- <span data-ttu-id="d5392-111">[/dsc/](https://docs.microsoft.com/powershell/dsc/) correspond à la fonctionnalité de configuration d’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="d5392-111">[/dsc/](https://docs.microsoft.com/powershell/dsc/) is for the Desired State Configuration feature</span></span>
- <span data-ttu-id="d5392-112">[/gallery/](https://docs.microsoft.com/powershell/gallery) correspond à la [PowerShell Gallery](https://www.powershellgallery.com/)</span><span class="sxs-lookup"><span data-stu-id="d5392-112">[/gallery/](https://docs.microsoft.com/powershell/gallery) is for the [PowerShell Gallery](https://www.powershellgallery.com/)</span></span>
- <span data-ttu-id="d5392-113">[/jea/](https://docs.microsoft.com/powershell/jea/) correspond à la fonctionnalité JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="d5392-113">[/jea/](https://docs.microsoft.com/powershell/jea/) is for the Just Enough Administration feature</span></span>
- <span data-ttu-id="d5392-114">[/reference/](https://docs.microsoft.com/powershell/scripting/) correspond aux sujets conceptuels et à la référence de module PowerShell dans les versions 3.0, 4.0, 5.0, 5.1 et 6.0.</span><span class="sxs-lookup"><span data-stu-id="d5392-114">[/reference/](https://docs.microsoft.com/powershell/scripting/) is for PowerShell conceptual topics and module reference across versions 3.0, 4.0, 5.0, 5.1, and 6.0</span></span>
  - <span data-ttu-id="d5392-115">Ce contenu est également la source de contenu d’aide récupéré par l’applet de commande `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="d5392-115">This content is also the source of help content retrieved by the `Get-Help` cmdlet</span></span>
- <span data-ttu-id="d5392-116">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contient les notes de publication pour Windows Management Framework, le package utilisé pour distribuer les nouvelles versions de PowerShell aux versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="d5392-116">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contains release notes for the Windows Management Framework, the package used to distribute new versions of PowerShell to previous versions of Windows.</span></span>

## <a name="contributing"></a><span data-ttu-id="d5392-117">Contribution</span><span class="sxs-lookup"><span data-stu-id="d5392-117">Contributing</span></span>

<span data-ttu-id="d5392-118">Nous fusionnons activement les contributions dans ce dépôt via une [demande Pull](https://help.github.com/articles/using-pull-requests/) dans la branche de *préproduction*.</span><span class="sxs-lookup"><span data-stu-id="d5392-118">We actively merge contributions into this repository via [pull request](https://help.github.com/articles/using-pull-requests/) into the *staging* branch.</span></span>
<span data-ttu-id="d5392-119">Notez qu’avant d’envoyer une demande Pull, vous devez [signer un contrat de licence de contribution](https://cla.microsoft.com/) pour garantir que la communauté est libre d’utiliser vos envois.</span><span class="sxs-lookup"><span data-stu-id="d5392-119">Please note that before you submit a pull request you must [sign a Contribution License Agreement](https://cla.microsoft.com/) to ensure that the community is free to use your submissions.</span></span>

<span data-ttu-id="d5392-120">Pour plus d’informations sur la contribution, lisez notre [guide du contributeur](CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="d5392-120">For more information on contributing, read our [contributor's guide](CONTRIBUTING.md).</span></span>
<span data-ttu-id="d5392-121">Le guide du contributeur contient des informations détaillées sur la manière de contribuer à la documentation, les outils, ainsi que sur les exigences concernant le style et la mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d5392-121">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span>
<span data-ttu-id="d5392-122">Utilisez les modèles « Issue » et « Pull Request » afin que la documentation soit cohérente entre les versions.</span><span class="sxs-lookup"><span data-stu-id="d5392-122">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="d5392-123">Licences</span><span class="sxs-lookup"><span data-stu-id="d5392-123">Licenses</span></span>

<span data-ttu-id="d5392-124">Il existe deux fichiers de licence pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="d5392-124">There are two license files for this project.</span></span>
<span data-ttu-id="d5392-125">La licence MIT s’applique au code contenu dans ce dépôt.</span><span class="sxs-lookup"><span data-stu-id="d5392-125">The MIT License applies to the code contained in this repo.</span></span>
<span data-ttu-id="d5392-126">La licence Creative Commons s’applique à la documentation.</span><span class="sxs-lookup"><span data-stu-id="d5392-126">The Creative Commons license applies to the documentation.</span></span>