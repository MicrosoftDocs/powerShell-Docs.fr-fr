---
title: Cycle de vie de support de PowerShell Core
description: Politiques régissant le support de PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 2e0ca1b9c133e6f316a40aff13365d0489059165
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402072"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="45efb-103">Cycle de vie de support de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="45efb-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="45efb-104">PowerShell Core est un ensemble d’outils et de composants distinct livré, installé et configuré séparément de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45efb-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="45efb-105">Par conséquent, PowerShell Core n’est pas inclus dans les contrats de licence Windows 7/8.1/10 ni Windows Server.</span><span class="sxs-lookup"><span data-stu-id="45efb-105">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="45efb-106">Toutefois, PowerShell Core est pris en charge dans des contrats de support Microsoft classiques, dont [Premier][], les [contrats Entreprise Microsoft ][enterprise-agreement] et [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="45efb-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="45efb-107">Vous pouvez également payer pour obtenir un [support assisté][] pour PowerShell Core en faisant une demande de support pour votre problème.</span><span class="sxs-lookup"><span data-stu-id="45efb-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="45efb-108">Nous proposons également un [support de la communauté][] sur GitHub, où vous pouvez signaler un problème, un bogue ou une demande de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="45efb-108">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="45efb-109">Vous pouvez également obtenir de l’aide auprès d’autres membres de la communauté sur la [Communauté Microsoft][] générale ou la [Communauté technique PowerShell][] Microsoft.</span><span class="sxs-lookup"><span data-stu-id="45efb-109">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="45efb-110">Nous n’offrons aucune garantie que votre problème y sera traité ou résolu en temps voulu.</span><span class="sxs-lookup"><span data-stu-id="45efb-110">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="45efb-111">Si vous avez un problème nécessitant une attention immédiate, vous devez utiliser les options de support payantes classiques.</span><span class="sxs-lookup"><span data-stu-id="45efb-111">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="45efb-112">Cycle de vie de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="45efb-112">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="45efb-113">PowerShell Core adopte la [politique de support moderne Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="45efb-113">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="45efb-114">Cette politique de support est destinée à maintenir les clients à jour avec les dernières versions.</span><span class="sxs-lookup"><span data-stu-id="45efb-114">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="45efb-115">La branche PowerShell Core version 6.x sera mise à jour environ une fois tous les six mois (par exemple, 6.0, 6.1, 6.2, etc.)</span><span class="sxs-lookup"><span data-stu-id="45efb-115">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45efb-116">Vous devez effectuer la mise à jour dans les six mois après la publication de chaque nouvelle version mineure pour continuer à recevoir un support.</span><span class="sxs-lookup"><span data-stu-id="45efb-116">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="45efb-117">Par exemple, si PowerShell Core 6.1 est publié le 1er juillet 2018, vous êtes supposé effectuer la mise à jour vers PowerShell Core 6.1 avant le 1er janvier 2019 pour continuer à bénéficier du support.</span><span class="sxs-lookup"><span data-stu-id="45efb-117">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![Cycle de vie de branche PowerShell Core][lifecycle-chart]

<span data-ttu-id="45efb-119">La politique de support moderne nécessite également que Microsoft prévienne les clients 12 mois avant de mettre fin au support d’un produit (par exemple, PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="45efb-119">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="45efb-120">Au final, PowerShell Core devrait suivre l’approche de « maintenance à long terme » où seules la maintenance et les mises à jour de sécurité resteront en support sur une branche/version spécifique de 6.x.</span><span class="sxs-lookup"><span data-stu-id="45efb-120">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="45efb-121">Plateformes prises en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-121">Supported platforms</span></span>

<span data-ttu-id="45efb-122">Consultez le tableau suivant pour voir quelle plateforme est officiellement prise en charge par la version de PowerShell Core que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="45efb-122">Please see the following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="45efb-123">Notre communauté a également proposé des packages pour certaines plateformes, mais ils ne sont pas officiellement pris en charge.</span><span class="sxs-lookup"><span data-stu-id="45efb-123">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="45efb-124">Ces packages sont marqués `Community` dans la table.</span><span class="sxs-lookup"><span data-stu-id="45efb-124">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="45efb-125">Les plateformes répertoriées en tant que `Experimental` ne sont pas officiellement prises en charge, mais sont disponibles pour l’expérimentation et les commentaires.</span><span class="sxs-lookup"><span data-stu-id="45efb-125">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="45efb-126">6.0</span><span class="sxs-lookup"><span data-stu-id="45efb-126">6.0</span></span>         | <span data-ttu-id="45efb-127">6.1</span><span class="sxs-lookup"><span data-stu-id="45efb-127">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="45efb-128">Windows 7, 8.1 et 10</span><span class="sxs-lookup"><span data-stu-id="45efb-128">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="45efb-129">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-129">Supported</span></span>   | <span data-ttu-id="45efb-130">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-130">Supported</span></span>   |
| <span data-ttu-id="45efb-131">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="45efb-131">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="45efb-132">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-132">Supported</span></span>   | <span data-ttu-id="45efb-133">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-133">Supported</span></span>   |
| <span data-ttu-id="45efb-134">[Canal semi-annuel Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="45efb-134">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="45efb-135">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-135">Supported</span></span>   | <span data-ttu-id="45efb-136">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-136">Supported</span></span>   |
| <span data-ttu-id="45efb-137">Ubuntu 14.04 et 16.04</span><span class="sxs-lookup"><span data-stu-id="45efb-137">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="45efb-138">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-138">Supported</span></span>   | <span data-ttu-id="45efb-139">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-139">Supported</span></span>   |
| <span data-ttu-id="45efb-140">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="45efb-140">Ubuntu 18.04</span></span>                                      |             | <span data-ttu-id="45efb-141">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-141">Supported</span></span>   |
| <span data-ttu-id="45efb-142">Ubuntu 18.10 (via Snap Package)</span><span class="sxs-lookup"><span data-stu-id="45efb-142">Ubuntu 18.10 (via Snap Package)</span></span>                   |             | <span data-ttu-id="45efb-143">Communauté</span><span class="sxs-lookup"><span data-stu-id="45efb-143">Community</span></span>   |
| <span data-ttu-id="45efb-144">Debian 8.7+ et 9</span><span class="sxs-lookup"><span data-stu-id="45efb-144">Debian 8.7+, and 9</span></span>                                | <span data-ttu-id="45efb-145">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-145">Supported</span></span>   | <span data-ttu-id="45efb-146">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-146">Supported</span></span>   |
| <span data-ttu-id="45efb-147">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="45efb-147">CentOS 7</span></span>                                          | <span data-ttu-id="45efb-148">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-148">Supported</span></span>   | <span data-ttu-id="45efb-149">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-149">Supported</span></span>   |
| <span data-ttu-id="45efb-150">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="45efb-150">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="45efb-151">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-151">Supported</span></span>   | <span data-ttu-id="45efb-152">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-152">Supported</span></span>   |
| <span data-ttu-id="45efb-153">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="45efb-153">OpenSUSE 42.3</span></span>                                     | <span data-ttu-id="45efb-154">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-154">Supported</span></span>   | <span data-ttu-id="45efb-155">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-155">Supported</span></span>   |
| <span data-ttu-id="45efb-156">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="45efb-156">Fedora 27</span></span>                                         | <span data-ttu-id="45efb-157">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-157">Supported</span></span>   | <span data-ttu-id="45efb-158">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-158">Supported</span></span>   |
| <span data-ttu-id="45efb-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="45efb-159">Fedora 28</span></span>                                         |             | <span data-ttu-id="45efb-160">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-160">Supported</span></span>   |
| <span data-ttu-id="45efb-161">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="45efb-161">macOS 10.12+</span></span>                                      | <span data-ttu-id="45efb-162">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-162">Supported</span></span>   | <span data-ttu-id="45efb-163">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-163">Supported</span></span>   |
| <span data-ttu-id="45efb-164">Arch</span><span class="sxs-lookup"><span data-stu-id="45efb-164">Arch</span></span>                                              | <span data-ttu-id="45efb-165">Communauté</span><span class="sxs-lookup"><span data-stu-id="45efb-165">Community</span></span>   | <span data-ttu-id="45efb-166">Communauté</span><span class="sxs-lookup"><span data-stu-id="45efb-166">Community</span></span>   |
| <span data-ttu-id="45efb-167">Raspbian</span><span class="sxs-lookup"><span data-stu-id="45efb-167">Raspbian</span></span>                                          | <span data-ttu-id="45efb-168">Expérimental</span><span class="sxs-lookup"><span data-stu-id="45efb-168">Experimental</span></span>| <span data-ttu-id="45efb-169">Communauté</span><span class="sxs-lookup"><span data-stu-id="45efb-169">Community</span></span>   |
| <span data-ttu-id="45efb-170">Kali</span><span class="sxs-lookup"><span data-stu-id="45efb-170">Kali</span></span>                                              | <span data-ttu-id="45efb-171">Communauté</span><span class="sxs-lookup"><span data-stu-id="45efb-171">Community</span></span>   | <span data-ttu-id="45efb-172">Communauté</span><span class="sxs-lookup"><span data-stu-id="45efb-172">Community</span></span>   |
| <span data-ttu-id="45efb-173">AppImage (fonctionne sur plusieurs plateformes Linux)</span><span class="sxs-lookup"><span data-stu-id="45efb-173">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="45efb-174">Communauté</span><span class="sxs-lookup"><span data-stu-id="45efb-174">Community</span></span>   | <span data-ttu-id="45efb-175">Communauté</span><span class="sxs-lookup"><span data-stu-id="45efb-175">Community</span></span>   |
| [<span data-ttu-id="45efb-176">Snap Package</span><span class="sxs-lookup"><span data-stu-id="45efb-176">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="45efb-177">Voir la remarque</span><span class="sxs-lookup"><span data-stu-id="45efb-177">See note</span></span>    | <span data-ttu-id="45efb-178">Voir la remarque</span><span class="sxs-lookup"><span data-stu-id="45efb-178">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="45efb-179">Snap Package va rester expérimental pendant un temps.</span><span class="sxs-lookup"><span data-stu-id="45efb-179">Snap packages will be experimental for a period.</span></span>  <span data-ttu-id="45efb-180">Après, nous sommes sûrs que Snap n’introduira pas de nouveaux problèmes de support. Le support suivra la distribution sur laquelle vous exécutez le package.</span><span class="sxs-lookup"><span data-stu-id="45efb-180">After, we are confident that Snap does not introduce new support issues, the support will follow the distribution you are running the package on.</span></span>

## <a name="platform-which-are-out-of-support"></a><span data-ttu-id="45efb-181">Plateformes qui ne sont plus prises en charge</span><span class="sxs-lookup"><span data-stu-id="45efb-181">Platform which are out of support</span></span>

<span data-ttu-id="45efb-182">Lorsqu’une version de plateforme atteint la fin de vie comme défini par le propriétaire de la plateforme, PowerShell Core cesse également de prendre en charge cette version de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="45efb-182">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to provide support for that platform version.</span></span> <span data-ttu-id="45efb-183">Les packages précédemment publiés resteront à la disposition des clients ayant besoin d’y accéder, mais il n’y aura plus ni prise en charge formelle ni mise à jour d’aucune sorte.</span><span class="sxs-lookup"><span data-stu-id="45efb-183">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="45efb-184">Par conséquent, la prise en charge des versions suivantes a été interrompue par les propriétaires de distribution et n’est plus assurée.</span><span class="sxs-lookup"><span data-stu-id="45efb-184">Therefore, support for the following versions was ended by the distribution owners and are not supported.</span></span>

| <span data-ttu-id="45efb-185">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="45efb-185">OS</span></span>       | <span data-ttu-id="45efb-186">Version</span><span class="sxs-lookup"><span data-stu-id="45efb-186">Version</span></span> | <span data-ttu-id="45efb-187">Fin de vie</span><span class="sxs-lookup"><span data-stu-id="45efb-187">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="45efb-188">Fedora</span><span class="sxs-lookup"><span data-stu-id="45efb-188">Fedora</span></span>   | <span data-ttu-id="45efb-189">24</span><span class="sxs-lookup"><span data-stu-id="45efb-189">24</span></span>      | [<span data-ttu-id="45efb-190">Août 2017</span><span class="sxs-lookup"><span data-stu-id="45efb-190">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="45efb-191">Fedora</span><span class="sxs-lookup"><span data-stu-id="45efb-191">Fedora</span></span>   | <span data-ttu-id="45efb-192">25</span><span class="sxs-lookup"><span data-stu-id="45efb-192">25</span></span>      | [<span data-ttu-id="45efb-193">Décembre 2017</span><span class="sxs-lookup"><span data-stu-id="45efb-193">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="45efb-194">Fedora</span><span class="sxs-lookup"><span data-stu-id="45efb-194">Fedora</span></span>   | <span data-ttu-id="45efb-195">26</span><span class="sxs-lookup"><span data-stu-id="45efb-195">26</span></span>      | [<span data-ttu-id="45efb-196">Mai 2018</span><span class="sxs-lookup"><span data-stu-id="45efb-196">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="45efb-197">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="45efb-197">openSUSE</span></span> | <span data-ttu-id="45efb-198">42.1</span><span class="sxs-lookup"><span data-stu-id="45efb-198">42.1</span></span>    | [<span data-ttu-id="45efb-199">Mai 2017</span><span class="sxs-lookup"><span data-stu-id="45efb-199">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="45efb-200">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="45efb-200">openSUSE</span></span> | <span data-ttu-id="45efb-201">42.2</span><span class="sxs-lookup"><span data-stu-id="45efb-201">42.2</span></span>    | [<span data-ttu-id="45efb-202">Janvier 2018</span><span class="sxs-lookup"><span data-stu-id="45efb-202">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="45efb-203">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="45efb-203">Ubuntu</span></span>   | <span data-ttu-id="45efb-204">16.10</span><span class="sxs-lookup"><span data-stu-id="45efb-204">16.10</span></span>   | [<span data-ttu-id="45efb-205">Juillet 2017</span><span class="sxs-lookup"><span data-stu-id="45efb-205">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="45efb-206">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="45efb-206">Ubuntu</span></span>   | <span data-ttu-id="45efb-207">17.04</span><span class="sxs-lookup"><span data-stu-id="45efb-207">17.04</span></span>   | [<span data-ttu-id="45efb-208">Janvier 2018</span><span class="sxs-lookup"><span data-stu-id="45efb-208">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="45efb-209">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="45efb-209">Ubuntu</span></span>   | <span data-ttu-id="45efb-210">17.10</span><span class="sxs-lookup"><span data-stu-id="45efb-210">17.10</span></span>   | [<span data-ttu-id="45efb-211">Juillet 2018</span><span class="sxs-lookup"><span data-stu-id="45efb-211">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |

## <a name="notes-on-licensing"></a><span data-ttu-id="45efb-212">Remarques sur les licences</span><span class="sxs-lookup"><span data-stu-id="45efb-212">Notes on licensing</span></span>

<span data-ttu-id="45efb-213">PowerShell Core est publié sous la [licence MIT][].</span><span class="sxs-lookup"><span data-stu-id="45efb-213">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="45efb-214">Sous cette licence et en l’absence d’un contrat de support payant, les utilisateurs sont limités au [support de la communauté][].</span><span class="sxs-lookup"><span data-stu-id="45efb-214">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="45efb-215">Dans le cadre du support de la communauté, Microsoft ne garantit pas la réactivité ni les correctifs.</span><span class="sxs-lookup"><span data-stu-id="45efb-215">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="45efb-216">Module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="45efb-216">Windows PowerShell Module</span></span>

<span data-ttu-id="45efb-217">Le support de PowerShell Core ne s’étend pas aux autres modules du produit, sauf si ces modules prennent explicitement en charge PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="45efb-217">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="45efb-218">Par exemple, l’utilisation du module `ActiveDirectory` qui est fourni dans le cadre de Windows Server est un scénario non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="45efb-218">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="45efb-219">Toutefois, les modules qui ne prennent pas explicitement en charge PowerShell Core peuvent être compatibles dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="45efb-219">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="45efb-220">En installant le module [`WindowsPSModulePath`][] vous pouvez ajouter Windows PowerShell `PSModulePath` à PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="45efb-220">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="45efb-221">Installez d’abord le module `WindowsPSModulePath` à partir de PowerShell Gallery :</span><span class="sxs-lookup"><span data-stu-id="45efb-221">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="45efb-222">Après avoir installé ce module, exécutez l’applet de commande `Add-WindowsPSModulePath` pour ajouter Windows PowerShell `PSModulePath` à PowerShell Core :</span><span class="sxs-lookup"><span data-stu-id="45efb-222">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

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
