---
title: Cycle de vie de support de PowerShell Core
description: Politiques régissant le support de PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 178e5c43520f9a392ca219b9f785eb18b1ec5436
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623856"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="abd9f-103">Cycle de vie de support de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="abd9f-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="abd9f-104">PowerShell Core est un ensemble d’outils et de composants distinct livré, installé et configuré séparément de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abd9f-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="abd9f-105">PowerShell Core n’est donc pas inclus dans les contrats de licence Windows 7/8.1/10 ou Windows Server.</span><span class="sxs-lookup"><span data-stu-id="abd9f-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="abd9f-106">Toutefois, PowerShell Core est pris en charge dans des contrats de support Microsoft classiques, dont [Premier][], les [contrats Entreprise Microsoft ][enterprise-agreement] et [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="abd9f-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="abd9f-107">Vous pouvez également payer pour obtenir un [support assisté][] pour PowerShell Core en faisant une demande de support pour votre problème.</span><span class="sxs-lookup"><span data-stu-id="abd9f-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="abd9f-108">Support de la communauté</span><span class="sxs-lookup"><span data-stu-id="abd9f-108">Community Support</span></span>

<span data-ttu-id="abd9f-109">Nous proposons également un [support de la communauté][] sur GitHub, où vous pouvez signaler un problème, un bogue ou une demande de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="abd9f-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="abd9f-110">Vous pouvez également bénéficier de l’aide d’autres membres de la communauté sur la [Communauté Microsoft][] générale ou la [Communauté technique PowerShell][] Microsoft.</span><span class="sxs-lookup"><span data-stu-id="abd9f-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="abd9f-111">Nous ne garantissons pas que la communauté traitera ou résoudra votre problème en temps voulu.</span><span class="sxs-lookup"><span data-stu-id="abd9f-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="abd9f-112">Si vous avez un problème nécessitant une attention immédiate, vous devez utiliser les options de support payantes classiques.</span><span class="sxs-lookup"><span data-stu-id="abd9f-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="abd9f-113">Cycle de vie de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="abd9f-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="abd9f-114">PowerShell Core adopte la [politique de support moderne Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="abd9f-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="abd9f-115">Cette politique de support est destinée à maintenir les clients à jour avec les dernières versions.</span><span class="sxs-lookup"><span data-stu-id="abd9f-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="abd9f-116">La branche PowerShell Core version 6.x sera mise à jour environ une fois tous les six mois (par exemple : 6.0, 6.1, 6.2, etc.)</span><span class="sxs-lookup"><span data-stu-id="abd9f-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abd9f-117">Vous devez effectuer la mise à jour dans les six mois après la publication de chaque nouvelle version mineure pour continuer à recevoir un support.</span><span class="sxs-lookup"><span data-stu-id="abd9f-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="abd9f-118">Par exemple, si PowerShell Core 6.1 est publié le 1er juillet 2018, vous êtes supposé effectuer la mise à jour vers PowerShell Core 6.1 avant le 1er janvier 2019 pour continuer à bénéficier du support.</span><span class="sxs-lookup"><span data-stu-id="abd9f-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abd9f-119">Vous devez effectuer la mise à jour dans les 30 jours après la publication de chaque nouvelle version de correctif pour continuer à recevoir un support.</span><span class="sxs-lookup"><span data-stu-id="abd9f-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="abd9f-120">Par exemple, si vous exécutez PowerShell Core 6.1 et que la version 6.1.3 a été publiée le 19 février 2019, vous êtes censé mettre à jour vers PowerShell Core 6.1.3 d’ici le 21 mars 2019, soit 30 jours après la publication, pour continuer à bénéficier du support.</span><span class="sxs-lookup"><span data-stu-id="abd9f-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="abd9f-121">Si des correctifs sont identifiés comme étant obligatoires, ils seront publiés dans notre prochaine mise à jour cumulative.</span><span class="sxs-lookup"><span data-stu-id="abd9f-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

![Cycle de vie de branche PowerShell Core][lifecycle-chart]

<span data-ttu-id="abd9f-123">La stratégie de cycle de vie moderne exige également que Microsoft prévienne les clients 12 mois avant de mettre fin au support d’un produit (par exemple, PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="abd9f-123">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="abd9f-124">A terme, nous pensons que PowerShell Core adoptera l'approche du « service à long terme ».</span><span class="sxs-lookup"><span data-stu-id="abd9f-124">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="abd9f-125">Dans ce cas, nous exigerons uniquement les mises à jour de maintenance et de sécurité pour continuer à bénéficier du support pour une branche/version spécifique de 6.x.</span><span class="sxs-lookup"><span data-stu-id="abd9f-125">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="abd9f-126">Plateformes prises en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-126">Supported platforms</span></span>

<span data-ttu-id="abd9f-127">Le tableau suivant indique quelle plateforme est officiellement prise en charge par la version de PowerShell Core que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="abd9f-127">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="abd9f-128">Notre communauté a également proposé des packages pour certaines plateformes, mais ils ne sont pas officiellement pris en charge.</span><span class="sxs-lookup"><span data-stu-id="abd9f-128">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="abd9f-129">Ces packages sont marqués `Community` dans la table.</span><span class="sxs-lookup"><span data-stu-id="abd9f-129">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="abd9f-130">Les plateformes répertoriées en tant que `Experimental` ne sont pas officiellement prises en charge, mais sont disponibles pour l’expérimentation et les commentaires.</span><span class="sxs-lookup"><span data-stu-id="abd9f-130">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="abd9f-131">6.1</span><span class="sxs-lookup"><span data-stu-id="abd9f-131">6.1</span></span>         | <span data-ttu-id="abd9f-132">6.2</span><span class="sxs-lookup"><span data-stu-id="abd9f-132">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="abd9f-133">Windows 7, 8.1 et 10</span><span class="sxs-lookup"><span data-stu-id="abd9f-133">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="abd9f-134">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-134">Supported</span></span>   | <span data-ttu-id="abd9f-135">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-135">Supported</span></span>   |
| <span data-ttu-id="abd9f-136">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="abd9f-136">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="abd9f-137">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-137">Supported</span></span>   | <span data-ttu-id="abd9f-138">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-138">Supported</span></span>   |
| <span data-ttu-id="abd9f-139">[Canal semi-annuel Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="abd9f-139">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="abd9f-140">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-140">Supported</span></span>   | <span data-ttu-id="abd9f-141">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-141">Supported</span></span>   |
| <span data-ttu-id="abd9f-142">Ubuntu 16.04 et 18.04</span><span class="sxs-lookup"><span data-stu-id="abd9f-142">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="abd9f-143">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-143">Supported</span></span>   | <span data-ttu-id="abd9f-144">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-144">Supported</span></span>   |
| <span data-ttu-id="abd9f-145">Ubuntu 18.10 (via Snap Package)</span><span class="sxs-lookup"><span data-stu-id="abd9f-145">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="abd9f-146">Communauté</span><span class="sxs-lookup"><span data-stu-id="abd9f-146">Community</span></span>   | <span data-ttu-id="abd9f-147">Communauté</span><span class="sxs-lookup"><span data-stu-id="abd9f-147">Community</span></span>   |
| <span data-ttu-id="abd9f-148">Debian 9</span><span class="sxs-lookup"><span data-stu-id="abd9f-148">Debian 9</span></span>                                          | <span data-ttu-id="abd9f-149">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-149">Supported</span></span>   | <span data-ttu-id="abd9f-150">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-150">Supported</span></span>   |
| <span data-ttu-id="abd9f-151">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="abd9f-151">CentOS 7</span></span>                                          | <span data-ttu-id="abd9f-152">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-152">Supported</span></span>   | <span data-ttu-id="abd9f-153">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-153">Supported</span></span>   |
| <span data-ttu-id="abd9f-154">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="abd9f-154">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="abd9f-155">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-155">Supported</span></span>   | <span data-ttu-id="abd9f-156">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-156">Supported</span></span>   |
| <span data-ttu-id="abd9f-157">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="abd9f-157">openSUSE 42.3</span></span>                                     | <span data-ttu-id="abd9f-158">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-158">Supported</span></span>   | <span data-ttu-id="abd9f-159">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-159">Supported</span></span>   |
| <span data-ttu-id="abd9f-160">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="abd9f-160">Fedora 28</span></span>                                         | <span data-ttu-id="abd9f-161">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-161">Supported</span></span>   | <span data-ttu-id="abd9f-162">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-162">Supported</span></span>   |
| <span data-ttu-id="abd9f-163">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="abd9f-163">macOS 10.12+</span></span>                                      | <span data-ttu-id="abd9f-164">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-164">Supported</span></span>   | <span data-ttu-id="abd9f-165">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-165">Supported</span></span>   |
| <span data-ttu-id="abd9f-166">Arch</span><span class="sxs-lookup"><span data-stu-id="abd9f-166">Arch</span></span>                                              | <span data-ttu-id="abd9f-167">Communauté</span><span class="sxs-lookup"><span data-stu-id="abd9f-167">Community</span></span>   | <span data-ttu-id="abd9f-168">Communauté</span><span class="sxs-lookup"><span data-stu-id="abd9f-168">Community</span></span>   |
| <span data-ttu-id="abd9f-169">Raspbian</span><span class="sxs-lookup"><span data-stu-id="abd9f-169">Raspbian</span></span>                                          | <span data-ttu-id="abd9f-170">Communauté</span><span class="sxs-lookup"><span data-stu-id="abd9f-170">Community</span></span>   | <span data-ttu-id="abd9f-171">Communauté</span><span class="sxs-lookup"><span data-stu-id="abd9f-171">Community</span></span>   |
| <span data-ttu-id="abd9f-172">Kali</span><span class="sxs-lookup"><span data-stu-id="abd9f-172">Kali</span></span>                                              | <span data-ttu-id="abd9f-173">Communauté</span><span class="sxs-lookup"><span data-stu-id="abd9f-173">Community</span></span>   | <span data-ttu-id="abd9f-174">Communauté</span><span class="sxs-lookup"><span data-stu-id="abd9f-174">Community</span></span>   |
| <span data-ttu-id="abd9f-175">AppImage (fonctionne sur plusieurs plateformes Linux)</span><span class="sxs-lookup"><span data-stu-id="abd9f-175">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="abd9f-176">Communauté</span><span class="sxs-lookup"><span data-stu-id="abd9f-176">Community</span></span>   | <span data-ttu-id="abd9f-177">Communauté</span><span class="sxs-lookup"><span data-stu-id="abd9f-177">Community</span></span>   |
| [<span data-ttu-id="abd9f-178">Snap Package</span><span class="sxs-lookup"><span data-stu-id="abd9f-178">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="abd9f-179">Voir la remarque</span><span class="sxs-lookup"><span data-stu-id="abd9f-179">See note</span></span>    | <span data-ttu-id="abd9f-180">Voir la remarque</span><span class="sxs-lookup"><span data-stu-id="abd9f-180">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="abd9f-181">Les packages Snap sont pris en charge de la même manière que la distribution sur laquelle vous exécutez le package.</span><span class="sxs-lookup"><span data-stu-id="abd9f-181">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="abd9f-182">Fin de vie de versions de PowerShell</span><span class="sxs-lookup"><span data-stu-id="abd9f-182">PowerShell release end of life</span></span>

<span data-ttu-id="abd9f-183">Sur la base du [cycle de vie de PowerShell Core](#lifecycle-of-powershell-core), le tableau suivant répertorie les dates auxquelles les différentes versions ne seront plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="abd9f-183">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="abd9f-184">Version</span><span class="sxs-lookup"><span data-stu-id="abd9f-184">Version</span></span> | <span data-ttu-id="abd9f-185">Fin de vie</span><span class="sxs-lookup"><span data-stu-id="abd9f-185">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="abd9f-186">6.0</span><span class="sxs-lookup"><span data-stu-id="abd9f-186">6.0</span></span>     | <span data-ttu-id="abd9f-187">13 février 2019</span><span class="sxs-lookup"><span data-stu-id="abd9f-187">February 13, 2019</span></span>             |
| <span data-ttu-id="abd9f-188">6.1</span><span class="sxs-lookup"><span data-stu-id="abd9f-188">6.1</span></span>     | <span data-ttu-id="abd9f-189">28 septembre 2019</span><span class="sxs-lookup"><span data-stu-id="abd9f-189">September 28, 2019</span></span>            |
| <span data-ttu-id="abd9f-190">6.2</span><span class="sxs-lookup"><span data-stu-id="abd9f-190">6.2</span></span>     | <span data-ttu-id="abd9f-191">6 mois après la publication de 6.3</span><span class="sxs-lookup"><span data-stu-id="abd9f-191">6 months after 6.3 releases</span></span>   |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="abd9f-192">Plateformes qui ne sont plus prises en charge</span><span class="sxs-lookup"><span data-stu-id="abd9f-192">Platforms, which are out of support</span></span>

<span data-ttu-id="abd9f-193">Lorsqu’une version de plateforme arrive en fin de vie conformément à la définition du propriétaire de la plateforme, PowerShell Core cesse également de prendre en charge cette version de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="abd9f-193">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="abd9f-194">Les packages précédemment publiés resteront à la disposition des clients ayant besoin d’y accéder, mais il n’y aura plus ni prise en charge formelle ni mise à jour d’aucune sorte.</span><span class="sxs-lookup"><span data-stu-id="abd9f-194">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="abd9f-195">Les propriétaires de distribution ont donc mis fin au support pour les versions suivantes, qui ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="abd9f-195">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="abd9f-196">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="abd9f-196">OS</span></span>       | <span data-ttu-id="abd9f-197">Version</span><span class="sxs-lookup"><span data-stu-id="abd9f-197">Version</span></span> | <span data-ttu-id="abd9f-198">Fin de vie</span><span class="sxs-lookup"><span data-stu-id="abd9f-198">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="abd9f-199">Fedora</span><span class="sxs-lookup"><span data-stu-id="abd9f-199">Fedora</span></span>   | <span data-ttu-id="abd9f-200">24</span><span class="sxs-lookup"><span data-stu-id="abd9f-200">24</span></span>      | [<span data-ttu-id="abd9f-201">Août 2017</span><span class="sxs-lookup"><span data-stu-id="abd9f-201">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="abd9f-202">Fedora</span><span class="sxs-lookup"><span data-stu-id="abd9f-202">Fedora</span></span>   | <span data-ttu-id="abd9f-203">25</span><span class="sxs-lookup"><span data-stu-id="abd9f-203">25</span></span>      | [<span data-ttu-id="abd9f-204">Décembre 2017</span><span class="sxs-lookup"><span data-stu-id="abd9f-204">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="abd9f-205">Fedora</span><span class="sxs-lookup"><span data-stu-id="abd9f-205">Fedora</span></span>   | <span data-ttu-id="abd9f-206">26</span><span class="sxs-lookup"><span data-stu-id="abd9f-206">26</span></span>      | [<span data-ttu-id="abd9f-207">Mai 2018</span><span class="sxs-lookup"><span data-stu-id="abd9f-207">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="abd9f-208">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="abd9f-208">openSUSE</span></span> | <span data-ttu-id="abd9f-209">42.1</span><span class="sxs-lookup"><span data-stu-id="abd9f-209">42.1</span></span>    | [<span data-ttu-id="abd9f-210">Mai 2017</span><span class="sxs-lookup"><span data-stu-id="abd9f-210">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="abd9f-211">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="abd9f-211">openSUSE</span></span> | <span data-ttu-id="abd9f-212">42.2</span><span class="sxs-lookup"><span data-stu-id="abd9f-212">42.2</span></span>    | [<span data-ttu-id="abd9f-213">Janvier 2018</span><span class="sxs-lookup"><span data-stu-id="abd9f-213">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="abd9f-214">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="abd9f-214">Ubuntu</span></span>   | <span data-ttu-id="abd9f-215">16.10</span><span class="sxs-lookup"><span data-stu-id="abd9f-215">16.10</span></span>   | [<span data-ttu-id="abd9f-216">Juillet 2017</span><span class="sxs-lookup"><span data-stu-id="abd9f-216">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="abd9f-217">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="abd9f-217">Ubuntu</span></span>   | <span data-ttu-id="abd9f-218">17.04</span><span class="sxs-lookup"><span data-stu-id="abd9f-218">17.04</span></span>   | [<span data-ttu-id="abd9f-219">Janvier 2018</span><span class="sxs-lookup"><span data-stu-id="abd9f-219">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="abd9f-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="abd9f-220">Ubuntu</span></span>   | <span data-ttu-id="abd9f-221">17.10</span><span class="sxs-lookup"><span data-stu-id="abd9f-221">17.10</span></span>   | [<span data-ttu-id="abd9f-222">Juillet 2018</span><span class="sxs-lookup"><span data-stu-id="abd9f-222">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="abd9f-223">Debian</span><span class="sxs-lookup"><span data-stu-id="abd9f-223">Debian</span></span>   | <span data-ttu-id="abd9f-224">8</span><span class="sxs-lookup"><span data-stu-id="abd9f-224">8</span></span>       | [<span data-ttu-id="abd9f-225">Juin 2018</span><span class="sxs-lookup"><span data-stu-id="abd9f-225">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="abd9f-226">Fedora</span><span class="sxs-lookup"><span data-stu-id="abd9f-226">Fedora</span></span>   | <span data-ttu-id="abd9f-227">27</span><span class="sxs-lookup"><span data-stu-id="abd9f-227">27</span></span>      | [<span data-ttu-id="abd9f-228">Novembre 2018</span><span class="sxs-lookup"><span data-stu-id="abd9f-228">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="abd9f-229">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="abd9f-229">Ubuntu</span></span>   | <span data-ttu-id="abd9f-230">14.04</span><span class="sxs-lookup"><span data-stu-id="abd9f-230">14.04</span></span>   | [<span data-ttu-id="abd9f-231">Avril 2019</span><span class="sxs-lookup"><span data-stu-id="abd9f-231">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="abd9f-232">Remarques sur les licences</span><span class="sxs-lookup"><span data-stu-id="abd9f-232">Notes on licensing</span></span>

<span data-ttu-id="abd9f-233">PowerShell Core est publié sous la [licence MIT][].</span><span class="sxs-lookup"><span data-stu-id="abd9f-233">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="abd9f-234">Sous cette licence et en l’absence d’un contrat de support payant, les utilisateurs sont limités au [support de la communauté][].</span><span class="sxs-lookup"><span data-stu-id="abd9f-234">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="abd9f-235">Dans le cadre du support de la communauté, Microsoft ne garantit pas la réactivité ni les correctifs.</span><span class="sxs-lookup"><span data-stu-id="abd9f-235">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="abd9f-236">Module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="abd9f-236">Windows PowerShell Module</span></span>

<span data-ttu-id="abd9f-237">Le support de PowerShell Core n’inclut pas de modules du produit, sauf si ces modules prennent explicitement en charge PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="abd9f-237">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="abd9f-238">Par exemple, l’utilisation du module `ActiveDirectory` qui est fourni dans le cadre de Windows Server est un scénario non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="abd9f-238">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="abd9f-239">Toutefois, les modules qui ne prennent pas explicitement en charge PowerShell Core peuvent être compatibles dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="abd9f-239">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="abd9f-240">En installant le module [`WindowsPSModulePath`][] vous pouvez ajouter Windows PowerShell `PSModulePath` à PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="abd9f-240">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="abd9f-241">Installez d’abord le module `WindowsPSModulePath` à partir de PowerShell Gallery :</span><span class="sxs-lookup"><span data-stu-id="abd9f-241">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="abd9f-242">Après avoir installé ce module, exécutez l’applet de commande `Add-WindowsPSModulePath` pour ajouter Windows PowerShell `PSModulePath` à PowerShell Core :</span><span class="sxs-lookup"><span data-stu-id="abd9f-242">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="abd9f-243">Fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="abd9f-243">Experimental features</span></span>

<span data-ttu-id="abd9f-244">Les [fonctionnalités expérimentales][] sont limitées au [support de la communauté](#community-support).</span><span class="sxs-lookup"><span data-stu-id="abd9f-244">[Experimental features][] are limited to [community support](#community-support).</span></span>

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
