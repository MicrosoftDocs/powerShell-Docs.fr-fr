---
title: Cycle de vie de support de PowerShell Core
description: Politiques régissant le support de PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: b8dd4891ecf245b87c3fe2fa61cd241a12209b57
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854374"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="eebd1-103">Cycle de vie de support de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="eebd1-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="eebd1-104">PowerShell Core est un ensemble d’outils et de composants distinct livré, installé et configuré séparément de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eebd1-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="eebd1-105">PowerShell Core n’est donc pas inclus dans les contrats de licence Windows 7/8.1/10 ou Windows Server.</span><span class="sxs-lookup"><span data-stu-id="eebd1-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="eebd1-106">Toutefois, PowerShell Core est pris en charge dans des contrats de support Microsoft classiques, dont [Premier][], les [contrats Entreprise Microsoft ][enterprise-agreement] et [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="eebd1-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="eebd1-107">Vous pouvez également payer pour obtenir un [support assisté][] pour PowerShell Core en faisant une demande de support pour votre problème.</span><span class="sxs-lookup"><span data-stu-id="eebd1-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="eebd1-108">Support de la communauté</span><span class="sxs-lookup"><span data-stu-id="eebd1-108">Community Support</span></span>

<span data-ttu-id="eebd1-109">Nous proposons également un [support de la communauté][] sur GitHub, où vous pouvez signaler un problème, un bogue ou une demande de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="eebd1-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="eebd1-110">Vous pouvez également bénéficier de l’aide d’autres membres de la communauté sur la [Communauté Microsoft][] générale ou la [Communauté technique PowerShell][] Microsoft.</span><span class="sxs-lookup"><span data-stu-id="eebd1-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="eebd1-111">Nous ne garantissons pas que la communauté traitera ou résoudra votre problème en temps voulu.</span><span class="sxs-lookup"><span data-stu-id="eebd1-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="eebd1-112">Si vous avez un problème nécessitant une attention immédiate, vous devez utiliser les options de support payantes classiques.</span><span class="sxs-lookup"><span data-stu-id="eebd1-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="eebd1-113">Cycle de vie de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="eebd1-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="eebd1-114">PowerShell Core adopte la [politique de support moderne Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="eebd1-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="eebd1-115">Cette politique de support est destinée à maintenir les clients à jour avec les dernières versions.</span><span class="sxs-lookup"><span data-stu-id="eebd1-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="eebd1-116">La branche PowerShell Core version 6.x sera mise à jour environ une fois tous les six mois (par exemple : 6.0, 6.1, 6.2, etc.)</span><span class="sxs-lookup"><span data-stu-id="eebd1-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eebd1-117">Vous devez effectuer la mise à jour dans les six mois après la publication de chaque nouvelle version mineure pour continuer à recevoir un support.</span><span class="sxs-lookup"><span data-stu-id="eebd1-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="eebd1-118">Par exemple, si PowerShell Core 6.1 est publié le 1er juillet 2018, vous êtes supposé effectuer la mise à jour vers PowerShell Core 6.1 avant le 1er janvier 2019 pour continuer à bénéficier du support.</span><span class="sxs-lookup"><span data-stu-id="eebd1-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eebd1-119">Vous devez effectuer la mise à jour dans les 30 jours après la publication de chaque nouvelle version de correctif pour continuer à recevoir un support.</span><span class="sxs-lookup"><span data-stu-id="eebd1-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="eebd1-120">Par exemple, si vous exécutez PowerShell Core 6.1 et que la version 6.1.3 a été publiée le 19 février 2019, vous êtes censé mettre à jour vers PowerShell Core 6.1.3 d’ici le 21 mars 2019, soit 30 jours après la publication, pour continuer à bénéficier du support.</span><span class="sxs-lookup"><span data-stu-id="eebd1-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="eebd1-121">Si des correctifs sont identifiés comme étant obligatoires, ils seront publiés dans notre prochaine mise à jour cumulative.</span><span class="sxs-lookup"><span data-stu-id="eebd1-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

<span data-ttu-id="eebd1-122">La stratégie de cycle de vie moderne exige également que Microsoft prévienne les clients 12 mois avant de mettre fin au support d’un produit (par exemple, PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="eebd1-122">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="eebd1-123">A terme, nous pensons que PowerShell Core adoptera l'approche du « service à long terme ».</span><span class="sxs-lookup"><span data-stu-id="eebd1-123">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="eebd1-124">Dans ce cas, nous exigerons uniquement les mises à jour de maintenance et de sécurité pour continuer à bénéficier du support pour une branche/version spécifique de 6.x.</span><span class="sxs-lookup"><span data-stu-id="eebd1-124">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="eebd1-125">Plateformes prises en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-125">Supported platforms</span></span>

<span data-ttu-id="eebd1-126">Le tableau suivant indique quelle plateforme est officiellement prise en charge par la version de PowerShell Core que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="eebd1-126">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="eebd1-127">Notre communauté a également proposé des packages pour certaines plateformes, mais ils ne sont pas officiellement pris en charge.</span><span class="sxs-lookup"><span data-stu-id="eebd1-127">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="eebd1-128">Ces packages sont marqués `Community` dans la table.</span><span class="sxs-lookup"><span data-stu-id="eebd1-128">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="eebd1-129">Les plateformes répertoriées en tant que `Experimental` ne sont pas officiellement prises en charge, mais sont disponibles pour l’expérimentation et les commentaires.</span><span class="sxs-lookup"><span data-stu-id="eebd1-129">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="eebd1-130">6.1</span><span class="sxs-lookup"><span data-stu-id="eebd1-130">6.1</span></span>         | <span data-ttu-id="eebd1-131">6.2</span><span class="sxs-lookup"><span data-stu-id="eebd1-131">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="eebd1-132">Windows 7, 8.1 et 10</span><span class="sxs-lookup"><span data-stu-id="eebd1-132">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="eebd1-133">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-133">Supported</span></span>   | <span data-ttu-id="eebd1-134">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-134">Supported</span></span>   |
| <span data-ttu-id="eebd1-135">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="eebd1-135">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="eebd1-136">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-136">Supported</span></span>   | <span data-ttu-id="eebd1-137">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-137">Supported</span></span>   |
| <span data-ttu-id="eebd1-138">[Canal semi-annuel Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="eebd1-138">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="eebd1-139">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-139">Supported</span></span>   | <span data-ttu-id="eebd1-140">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-140">Supported</span></span>   |
| <span data-ttu-id="eebd1-141">Ubuntu 16.04 et 18.04</span><span class="sxs-lookup"><span data-stu-id="eebd1-141">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="eebd1-142">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-142">Supported</span></span>   | <span data-ttu-id="eebd1-143">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-143">Supported</span></span>   |
| <span data-ttu-id="eebd1-144">Ubuntu 18.10 (via Snap Package)</span><span class="sxs-lookup"><span data-stu-id="eebd1-144">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="eebd1-145">Communauté</span><span class="sxs-lookup"><span data-stu-id="eebd1-145">Community</span></span>   | <span data-ttu-id="eebd1-146">Communauté</span><span class="sxs-lookup"><span data-stu-id="eebd1-146">Community</span></span>   |
| <span data-ttu-id="eebd1-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="eebd1-147">Debian 9</span></span>                                          | <span data-ttu-id="eebd1-148">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-148">Supported</span></span>   | <span data-ttu-id="eebd1-149">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-149">Supported</span></span>   |
| <span data-ttu-id="eebd1-150">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="eebd1-150">CentOS 7</span></span>                                          | <span data-ttu-id="eebd1-151">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-151">Supported</span></span>   | <span data-ttu-id="eebd1-152">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-152">Supported</span></span>   |
| <span data-ttu-id="eebd1-153">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="eebd1-153">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="eebd1-154">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-154">Supported</span></span>   | <span data-ttu-id="eebd1-155">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-155">Supported</span></span>   |
| <span data-ttu-id="eebd1-156">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="eebd1-156">openSUSE 42.3</span></span>                                     | <span data-ttu-id="eebd1-157">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-157">Supported</span></span>   | <span data-ttu-id="eebd1-158">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-158">Supported</span></span>   |
| <span data-ttu-id="eebd1-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="eebd1-159">Fedora 28</span></span>                                         | <span data-ttu-id="eebd1-160">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-160">Supported</span></span>   | <span data-ttu-id="eebd1-161">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-161">Supported</span></span>   |
| <span data-ttu-id="eebd1-162">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="eebd1-162">macOS 10.12+</span></span>                                      | <span data-ttu-id="eebd1-163">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-163">Supported</span></span>   | <span data-ttu-id="eebd1-164">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-164">Supported</span></span>   |
| <span data-ttu-id="eebd1-165">Arch</span><span class="sxs-lookup"><span data-stu-id="eebd1-165">Arch</span></span>                                              | <span data-ttu-id="eebd1-166">Communauté</span><span class="sxs-lookup"><span data-stu-id="eebd1-166">Community</span></span>   | <span data-ttu-id="eebd1-167">Communauté</span><span class="sxs-lookup"><span data-stu-id="eebd1-167">Community</span></span>   |
| <span data-ttu-id="eebd1-168">Raspbian</span><span class="sxs-lookup"><span data-stu-id="eebd1-168">Raspbian</span></span>                                          | <span data-ttu-id="eebd1-169">Communauté</span><span class="sxs-lookup"><span data-stu-id="eebd1-169">Community</span></span>   | <span data-ttu-id="eebd1-170">Communauté</span><span class="sxs-lookup"><span data-stu-id="eebd1-170">Community</span></span>   |
| <span data-ttu-id="eebd1-171">Kali</span><span class="sxs-lookup"><span data-stu-id="eebd1-171">Kali</span></span>                                              | <span data-ttu-id="eebd1-172">Communauté</span><span class="sxs-lookup"><span data-stu-id="eebd1-172">Community</span></span>   | <span data-ttu-id="eebd1-173">Communauté</span><span class="sxs-lookup"><span data-stu-id="eebd1-173">Community</span></span>   |
| <span data-ttu-id="eebd1-174">AppImage (fonctionne sur plusieurs plateformes Linux)</span><span class="sxs-lookup"><span data-stu-id="eebd1-174">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="eebd1-175">Communauté</span><span class="sxs-lookup"><span data-stu-id="eebd1-175">Community</span></span>   | <span data-ttu-id="eebd1-176">Communauté</span><span class="sxs-lookup"><span data-stu-id="eebd1-176">Community</span></span>   |
| [<span data-ttu-id="eebd1-177">Snap Package</span><span class="sxs-lookup"><span data-stu-id="eebd1-177">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="eebd1-178">Voir la remarque</span><span class="sxs-lookup"><span data-stu-id="eebd1-178">See note</span></span>    | <span data-ttu-id="eebd1-179">Voir la remarque</span><span class="sxs-lookup"><span data-stu-id="eebd1-179">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="eebd1-180">Les packages Snap sont pris en charge de la même manière que la distribution sur laquelle vous exécutez le package.</span><span class="sxs-lookup"><span data-stu-id="eebd1-180">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="eebd1-181">Fin de vie de versions de PowerShell</span><span class="sxs-lookup"><span data-stu-id="eebd1-181">PowerShell release end of life</span></span>

<span data-ttu-id="eebd1-182">Sur la base du [cycle de vie de PowerShell Core](#lifecycle-of-powershell-core), le tableau suivant répertorie les dates auxquelles les différentes versions ne seront plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="eebd1-182">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="eebd1-183">Version</span><span class="sxs-lookup"><span data-stu-id="eebd1-183">Version</span></span> | <span data-ttu-id="eebd1-184">Fin de vie</span><span class="sxs-lookup"><span data-stu-id="eebd1-184">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="eebd1-185">6.0</span><span class="sxs-lookup"><span data-stu-id="eebd1-185">6.0</span></span>     | <span data-ttu-id="eebd1-186">13 février 2019</span><span class="sxs-lookup"><span data-stu-id="eebd1-186">February 13, 2019</span></span>             |
| <span data-ttu-id="eebd1-187">6.1</span><span class="sxs-lookup"><span data-stu-id="eebd1-187">6.1</span></span>     | <span data-ttu-id="eebd1-188">28 septembre 2019</span><span class="sxs-lookup"><span data-stu-id="eebd1-188">September 28, 2019</span></span>            |
| <span data-ttu-id="eebd1-189">6.2</span><span class="sxs-lookup"><span data-stu-id="eebd1-189">6.2</span></span>     | <span data-ttu-id="eebd1-190">6 mois après la publication de la version 7</span><span class="sxs-lookup"><span data-stu-id="eebd1-190">6 months after 7 releases</span></span>     |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="eebd1-191">Plateformes qui ne sont plus prises en charge</span><span class="sxs-lookup"><span data-stu-id="eebd1-191">Platforms, which are out of support</span></span>

<span data-ttu-id="eebd1-192">Lorsqu’une version de plateforme arrive en fin de vie conformément à la définition du propriétaire de la plateforme, PowerShell Core cesse également de prendre en charge cette version de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="eebd1-192">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="eebd1-193">Les packages précédemment publiés resteront à la disposition des clients ayant besoin d’y accéder, mais il n’y aura plus ni prise en charge formelle ni mise à jour d’aucune sorte.</span><span class="sxs-lookup"><span data-stu-id="eebd1-193">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="eebd1-194">Les propriétaires de distribution ont donc mis fin au support pour les versions suivantes, qui ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="eebd1-194">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="eebd1-195">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="eebd1-195">OS</span></span>       | <span data-ttu-id="eebd1-196">Version</span><span class="sxs-lookup"><span data-stu-id="eebd1-196">Version</span></span> | <span data-ttu-id="eebd1-197">Fin de vie</span><span class="sxs-lookup"><span data-stu-id="eebd1-197">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="eebd1-198">Fedora</span><span class="sxs-lookup"><span data-stu-id="eebd1-198">Fedora</span></span>   | <span data-ttu-id="eebd1-199">24</span><span class="sxs-lookup"><span data-stu-id="eebd1-199">24</span></span>      | [<span data-ttu-id="eebd1-200">Août 2017</span><span class="sxs-lookup"><span data-stu-id="eebd1-200">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="eebd1-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="eebd1-201">Fedora</span></span>   | <span data-ttu-id="eebd1-202">25</span><span class="sxs-lookup"><span data-stu-id="eebd1-202">25</span></span>      | [<span data-ttu-id="eebd1-203">Décembre 2017</span><span class="sxs-lookup"><span data-stu-id="eebd1-203">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="eebd1-204">Fedora</span><span class="sxs-lookup"><span data-stu-id="eebd1-204">Fedora</span></span>   | <span data-ttu-id="eebd1-205">26</span><span class="sxs-lookup"><span data-stu-id="eebd1-205">26</span></span>      | [<span data-ttu-id="eebd1-206">Mai 2018</span><span class="sxs-lookup"><span data-stu-id="eebd1-206">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="eebd1-207">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="eebd1-207">openSUSE</span></span> | <span data-ttu-id="eebd1-208">42.1</span><span class="sxs-lookup"><span data-stu-id="eebd1-208">42.1</span></span>    | [<span data-ttu-id="eebd1-209">Mai 2017</span><span class="sxs-lookup"><span data-stu-id="eebd1-209">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="eebd1-210">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="eebd1-210">openSUSE</span></span> | <span data-ttu-id="eebd1-211">42.2</span><span class="sxs-lookup"><span data-stu-id="eebd1-211">42.2</span></span>    | [<span data-ttu-id="eebd1-212">Janvier 2018</span><span class="sxs-lookup"><span data-stu-id="eebd1-212">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="eebd1-213">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="eebd1-213">Ubuntu</span></span>   | <span data-ttu-id="eebd1-214">16.10</span><span class="sxs-lookup"><span data-stu-id="eebd1-214">16.10</span></span>   | [<span data-ttu-id="eebd1-215">Juillet 2017</span><span class="sxs-lookup"><span data-stu-id="eebd1-215">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="eebd1-216">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="eebd1-216">Ubuntu</span></span>   | <span data-ttu-id="eebd1-217">17.04</span><span class="sxs-lookup"><span data-stu-id="eebd1-217">17.04</span></span>   | [<span data-ttu-id="eebd1-218">Janvier 2018</span><span class="sxs-lookup"><span data-stu-id="eebd1-218">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="eebd1-219">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="eebd1-219">Ubuntu</span></span>   | <span data-ttu-id="eebd1-220">17.10</span><span class="sxs-lookup"><span data-stu-id="eebd1-220">17.10</span></span>   | [<span data-ttu-id="eebd1-221">Juillet 2018</span><span class="sxs-lookup"><span data-stu-id="eebd1-221">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="eebd1-222">Debian</span><span class="sxs-lookup"><span data-stu-id="eebd1-222">Debian</span></span>   | <span data-ttu-id="eebd1-223">8</span><span class="sxs-lookup"><span data-stu-id="eebd1-223">8</span></span>       | [<span data-ttu-id="eebd1-224">Juin 2018</span><span class="sxs-lookup"><span data-stu-id="eebd1-224">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="eebd1-225">Fedora</span><span class="sxs-lookup"><span data-stu-id="eebd1-225">Fedora</span></span>   | <span data-ttu-id="eebd1-226">27</span><span class="sxs-lookup"><span data-stu-id="eebd1-226">27</span></span>      | [<span data-ttu-id="eebd1-227">Novembre 2018</span><span class="sxs-lookup"><span data-stu-id="eebd1-227">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="eebd1-228">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="eebd1-228">Ubuntu</span></span>   | <span data-ttu-id="eebd1-229">14.04</span><span class="sxs-lookup"><span data-stu-id="eebd1-229">14.04</span></span>   | [<span data-ttu-id="eebd1-230">Avril 2019</span><span class="sxs-lookup"><span data-stu-id="eebd1-230">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="eebd1-231">Remarques sur les licences</span><span class="sxs-lookup"><span data-stu-id="eebd1-231">Notes on licensing</span></span>

<span data-ttu-id="eebd1-232">PowerShell Core est publié sous la [licence MIT][].</span><span class="sxs-lookup"><span data-stu-id="eebd1-232">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="eebd1-233">Sous cette licence et en l’absence d’un contrat de support payant, les utilisateurs sont limités au [support de la communauté][].</span><span class="sxs-lookup"><span data-stu-id="eebd1-233">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="eebd1-234">Dans le cadre du support de la communauté, Microsoft ne garantit pas la réactivité ni les correctifs.</span><span class="sxs-lookup"><span data-stu-id="eebd1-234">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="eebd1-235">Module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eebd1-235">Windows PowerShell Module</span></span>

<span data-ttu-id="eebd1-236">Le support de PowerShell Core n’inclut pas de modules du produit, sauf si ces modules prennent explicitement en charge PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="eebd1-236">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="eebd1-237">Par exemple, l’utilisation du module `ActiveDirectory` qui est fourni dans le cadre de Windows Server est un scénario non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="eebd1-237">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="eebd1-238">Toutefois, les modules qui ne prennent pas explicitement en charge PowerShell Core peuvent être compatibles dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="eebd1-238">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="eebd1-239">En installant le module [`WindowsPSModulePath`][] vous pouvez ajouter Windows PowerShell `PSModulePath` à PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="eebd1-239">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="eebd1-240">Installez d’abord le module `WindowsPSModulePath` à partir de PowerShell Gallery :</span><span class="sxs-lookup"><span data-stu-id="eebd1-240">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="eebd1-241">Après avoir installé ce module, exécutez l’applet de commande `Add-WindowsPSModulePath` pour ajouter Windows PowerShell `PSModulePath` à PowerShell Core :</span><span class="sxs-lookup"><span data-stu-id="eebd1-241">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="eebd1-242">Fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="eebd1-242">Experimental features</span></span>

<span data-ttu-id="eebd1-243">Les [fonctionnalités expérimentales][] sont limitées au [support de la communauté](#community-support).</span><span class="sxs-lookup"><span data-stu-id="eebd1-243">[Experimental features][] are limited to [community support](#community-support).</span></span>

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[support de la communauté]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Communauté Microsoft]: https://answers.microsoft.com/
[Microsoft Community]: https://answers.microsoft.com/
[Communauté technique PowerShell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[support assisté]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[Licence MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Fonctionnalités expérimentales]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
[Experimental features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
