# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="67f63-101">Cycle de vie de support de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="67f63-101">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="67f63-102">PowerShell Core est un ensemble d’outils et de composants distinct livré, installé et configuré séparément de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67f63-102">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="67f63-103">Par conséquent, PowerShell Core n’est pas inclus dans les contrats de licence Windows 7/8.1/10 ni Windows Server.</span><span class="sxs-lookup"><span data-stu-id="67f63-103">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="67f63-104">Toutefois, PowerShell Core est pris en charge dans des contrats de support Microsoft classiques, dont [Premier][], les [contrats Entreprise Microsoft ][enterprise-agreement] et [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="67f63-104">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="67f63-105">Vous pouvez également payer pour obtenir un [support assisté][] pour PowerShell Core en faisant une demande de support pour votre problème.</span><span class="sxs-lookup"><span data-stu-id="67f63-105">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="67f63-106">Nous proposons également un [support de la communauté][] sur GitHub, où vous pouvez signaler un problème, un bogue ou une demande de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="67f63-106">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="67f63-107">Vous pouvez également obtenir de l’aide auprès d’autres membres de la communauté sur la [Communauté Microsoft][] générale ou la [Communauté technique PowerShell][] Microsoft.</span><span class="sxs-lookup"><span data-stu-id="67f63-107">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="67f63-108">Nous n’offrons aucune garantie que votre problème y sera traité ou résolu en temps voulu.</span><span class="sxs-lookup"><span data-stu-id="67f63-108">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="67f63-109">Si vous avez un problème nécessitant une attention immédiate, vous devez utiliser les options de support payantes classiques.</span><span class="sxs-lookup"><span data-stu-id="67f63-109">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="67f63-110">Cycle de vie de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="67f63-110">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="67f63-111">PowerShell Core adopte la [politique de support moderne Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="67f63-111">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="67f63-112">Cette politique de support est destinée à maintenir les clients à jour avec les dernières versions.</span><span class="sxs-lookup"><span data-stu-id="67f63-112">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="67f63-113">La branche PowerShell Core version 6.x sera mise à jour environ une fois tous les six mois (par exemple, 6.0, 6.1, 6.2, etc.)</span><span class="sxs-lookup"><span data-stu-id="67f63-113">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="67f63-114">Vous devez effectuer la mise à jour dans les six mois après la publication de chaque nouvelle version mineure pour continuer à recevoir un support.</span><span class="sxs-lookup"><span data-stu-id="67f63-114">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="67f63-115">Par exemple, si PowerShell Core 6.1 est publié le 1er juillet 2018, vous êtes supposé effectuer la mise à jour vers PowerShell Core 6.1 avant le 1er janvier 2019 pour continuer à bénéficier du support.</span><span class="sxs-lookup"><span data-stu-id="67f63-115">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![Cycle de vie de branche PowerShell Core][lifecycle-chart]

<span data-ttu-id="67f63-117">La politique de support moderne nécessite également que Microsoft prévienne les clients 12 mois avant de mettre fin au support d’un produit (par exemple, PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="67f63-117">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="67f63-118">Au final, PowerShell Core devrait suivre l’approche de « maintenance à long terme » où seules la maintenance et les mises à jour de sécurité resteront en support sur une branche/version spécifique de 6.x.</span><span class="sxs-lookup"><span data-stu-id="67f63-118">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="67f63-119">Plateformes prises en charge</span><span class="sxs-lookup"><span data-stu-id="67f63-119">Supported platforms</span></span>

<span data-ttu-id="67f63-120">PowerShell Core est officiellement pris en charge sur les plateformes suivantes :</span><span class="sxs-lookup"><span data-stu-id="67f63-120">PowerShell Core is officially supported on the following platforms:</span></span>

* <span data-ttu-id="67f63-121">Windows 7, 8.1 et 10</span><span class="sxs-lookup"><span data-stu-id="67f63-121">Windows 7, 8.1, and 10</span></span>
* <span data-ttu-id="67f63-122">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="67f63-122">Windows Server 2008 R2, 2012 R2, 2016</span></span>
* <span data-ttu-id="67f63-123">[Canal semi-annuel Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="67f63-123">[Windows Server Semi-Annual Channel][semi-annual]</span></span>
* <span data-ttu-id="67f63-124">Ubuntu 14.04, 16.04 et 17.04</span><span class="sxs-lookup"><span data-stu-id="67f63-124">Ubuntu 14.04, 16.04, and 17.04</span></span>
* <span data-ttu-id="67f63-125">Debian 8.7+ et 9</span><span class="sxs-lookup"><span data-stu-id="67f63-125">Debian 8.7+, and 9</span></span>
* <span data-ttu-id="67f63-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="67f63-126">CentOS 7</span></span>
* <span data-ttu-id="67f63-127">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="67f63-127">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="67f63-128">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="67f63-128">OpenSUSE 42.2</span></span>
* <span data-ttu-id="67f63-129">Fedora 27, 28</span><span class="sxs-lookup"><span data-stu-id="67f63-129">Fedora 27, 28</span></span>
* <span data-ttu-id="67f63-130">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="67f63-130">macOS 10.12+</span></span>

<span data-ttu-id="67f63-131">Notre communauté a également proposé des packages pour les plateformes suivantes, mais ils ne sont pas officiellement pris en charge :</span><span class="sxs-lookup"><span data-stu-id="67f63-131">Our community has also contributed packages for the following platforms, but they are not officially suppported:</span></span>

* <span data-ttu-id="67f63-132">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="67f63-132">Arch Linux</span></span>
* <span data-ttu-id="67f63-133">Kali Linux</span><span class="sxs-lookup"><span data-stu-id="67f63-133">Kali Linux</span></span>
* <span data-ttu-id="67f63-134">AppImage (fonctionne sur plusieurs plateformes Linux)</span><span class="sxs-lookup"><span data-stu-id="67f63-134">AppImage (works on multiple Linux platforms)</span></span>

## <a name="notes-on-licensing"></a><span data-ttu-id="67f63-135">Remarques sur les licences</span><span class="sxs-lookup"><span data-stu-id="67f63-135">Notes on licensing</span></span>

<span data-ttu-id="67f63-136">PowerShell Core est publié sous la [licence MIT][].</span><span class="sxs-lookup"><span data-stu-id="67f63-136">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="67f63-137">Sous cette licence et en l’absence d’un contrat de support payant, les utilisateurs sont limités au [support de la communauté][].</span><span class="sxs-lookup"><span data-stu-id="67f63-137">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="67f63-138">Dans le cadre du support de la communauté, Microsoft ne garantit pas la réactivité ni les correctifs.</span><span class="sxs-lookup"><span data-stu-id="67f63-138">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="67f63-139">Module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="67f63-139">Windows PowerShell Module</span></span>

<span data-ttu-id="67f63-140">Le support de PowerShell Core ne s’étend pas aux autres modules du produit, sauf si ces modules prennent explicitement en charge PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="67f63-140">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="67f63-141">Par exemple, l’utilisation du module `ActiveDirectory` qui est fourni dans le cadre de Windows Server est un scénario non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="67f63-141">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="67f63-142">Toutefois, les modules qui ne prennent pas explicitement en charge PowerShell Core peuvent être compatibles dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="67f63-142">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="67f63-143">En installant le module [`WindowsPSModulePath`][] vous pouvez ajouter Windows PowerShell `PSModulePath` à PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="67f63-143">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="67f63-144">Installez d’abord le module `WindowsPSModulePath` à partir de PowerShell Gallery :</span><span class="sxs-lookup"><span data-stu-id="67f63-144">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="67f63-145">Après avoir installé ce module, exécutez l’applet de commande `Add-WindowsPSModulePath` pour ajouter Windows PowerShell `PSModulePath` à PowerShell Core :</span><span class="sxs-lookup"><span data-stu-id="67f63-145">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

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
