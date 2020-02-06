---
title: Nouveautés de PowerShell Core 6.1
description: Nouvelles fonctionnalités et modifications de PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: 531259217f2b71213776e7d394616c7790e9aca9
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995518"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="a9e7b-103">Nouveautés de PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="a9e7b-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="a9e7b-104">Vous trouverez dans cet article certaines des plus importantes modifications et nouvelles fonctionnalités de PowerShell Core 6.1.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="a9e7b-105">Mais il y a aussi des **tonnes** d’autres « choses ennuyeuses » qui rendent PowerShell plus rapide et plus stable (ainsi que de nombreux correctifs de bogues) !</span><span class="sxs-lookup"><span data-stu-id="a9e7b-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span> <span data-ttu-id="a9e7b-106">Pour obtenir la liste complète des modifications, consultez le [journal des modifications sur GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="a9e7b-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="a9e7b-107">Nous profitons pour remercier [l’ensemble de la communauté des contributeurs](https://github.com/PowerShell/PowerShell/graphs/contributors) qui ont permis à cette version de voir le jour.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="a9e7b-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a9e7b-108">.NET Core 2.1</span></span>

<span data-ttu-id="a9e7b-109">PowerShell Core 6.1 est passé à .NET Core 2.1 après sa [publication en mai](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), ce qui a permis plusieurs améliorations, notamment :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="a9e7b-110">Améliorations des performances (voir [ci-dessous](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="a9e7b-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="a9e7b-111">Prise en charge de Linux Alpine (préversion)</span><span class="sxs-lookup"><span data-stu-id="a9e7b-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="a9e7b-112">[Prise en charge de l’outil global .NET](/dotnet/core/tools/global-tools) - bientôt disponible dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="a9e7b-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="a9e7b-113">Pack de compatibilité Windows pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="a9e7b-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="a9e7b-114">L’équipe .NET a publié le [Pack de compatibilité Windows pour .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), qui est un ensemble d’assemblys permettant de restaurer certaines API supprimées dans .NET Core sur Windows.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="a9e7b-115">Nous avons ajouté le Pack de compatibilité Windows à PowerShell Core 6.1 pour que tous les modules et scripts qui utilisent ces API puissent compter sur leur disponibilité.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="a9e7b-116">Le Pack de compatibilité Windows permet à PowerShell Core d’utiliser **plus de 1 900 applets de commande fournies avec la mise à jour d’octobre 2018 de Windows 10 et avec Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-whitelisting"></a><span data-ttu-id="a9e7b-117">Prise en charge de la mise en liste verte des applications</span><span class="sxs-lookup"><span data-stu-id="a9e7b-117">Support for Application Whitelisting</span></span>

<span data-ttu-id="a9e7b-118">Tout comme Windows PowerShell 5.1, PowerShell Core 6.1 prend en charge la mise en liste verte des applications pour [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) et [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control).</span><span class="sxs-lookup"><span data-stu-id="a9e7b-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application whitelisting.</span></span> <span data-ttu-id="a9e7b-119">La mise en liste verte des applications permet de contrôler précisément quels fichiers binaires peuvent être exécutés avec le [mode de langage limité](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-119">Application whitelisting allows granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="a9e7b-120">Optimisation des performances</span><span class="sxs-lookup"><span data-stu-id="a9e7b-120">Performance improvements</span></span>

<span data-ttu-id="a9e7b-121">D’importantes améliorations avaient été apportées à PowerShell Core 6.0 au niveau des performances.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-121">PowerShell Core 6.0 made some significant performance improvements.</span></span> <span data-ttu-id="a9e7b-122">PowerShell Core 6.1 améliore encore davantage la vitesse de certaines opérations.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="a9e7b-123">Par exemple, la vitesse d’exécution de `Group-Object` a augmenté de 66 % :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="a9e7b-124">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="a9e7b-124">Windows PowerShell 5.1</span></span> | <span data-ttu-id="a9e7b-125">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="a9e7b-125">PowerShell Core 6.0</span></span> | <span data-ttu-id="a9e7b-126">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="a9e7b-126">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="a9e7b-127">Durée (s)</span><span class="sxs-lookup"><span data-stu-id="a9e7b-127">Time (sec)</span></span>   | <span data-ttu-id="a9e7b-128">25,178</span><span class="sxs-lookup"><span data-stu-id="a9e7b-128">25.178</span></span>                 | <span data-ttu-id="a9e7b-129">19,653</span><span class="sxs-lookup"><span data-stu-id="a9e7b-129">19.653</span></span>              | <span data-ttu-id="a9e7b-130">6,641</span><span class="sxs-lookup"><span data-stu-id="a9e7b-130">6.641</span></span>               |
| <span data-ttu-id="a9e7b-131">Accélération (en %)</span><span class="sxs-lookup"><span data-stu-id="a9e7b-131">Speed-up (%)</span></span> | <span data-ttu-id="a9e7b-132">N/A</span><span class="sxs-lookup"><span data-stu-id="a9e7b-132">N/A</span></span>                    | <span data-ttu-id="a9e7b-133">21,9 %</span><span class="sxs-lookup"><span data-stu-id="a9e7b-133">21.9%</span></span>               | <span data-ttu-id="a9e7b-134">66,2 %</span><span class="sxs-lookup"><span data-stu-id="a9e7b-134">66.2%</span></span>               |

<span data-ttu-id="a9e7b-135">De même, les scénarios de tri similaires à celui-ci ont connu une amélioration de plus de 15 % :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-135">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="a9e7b-136">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="a9e7b-136">Windows PowerShell 5.1</span></span> | <span data-ttu-id="a9e7b-137">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="a9e7b-137">PowerShell Core 6.0</span></span> | <span data-ttu-id="a9e7b-138">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="a9e7b-138">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="a9e7b-139">Durée (s)</span><span class="sxs-lookup"><span data-stu-id="a9e7b-139">Time (sec)</span></span>   | <span data-ttu-id="a9e7b-140">12,170</span><span class="sxs-lookup"><span data-stu-id="a9e7b-140">12.170</span></span>                 | <span data-ttu-id="a9e7b-141">8,493</span><span class="sxs-lookup"><span data-stu-id="a9e7b-141">8.493</span></span>               | <span data-ttu-id="a9e7b-142">7,08</span><span class="sxs-lookup"><span data-stu-id="a9e7b-142">7.08</span></span>                |
| <span data-ttu-id="a9e7b-143">Accélération (en %)</span><span class="sxs-lookup"><span data-stu-id="a9e7b-143">Speed-up (%)</span></span> | <span data-ttu-id="a9e7b-144">N/A</span><span class="sxs-lookup"><span data-stu-id="a9e7b-144">N/A</span></span>                    | <span data-ttu-id="a9e7b-145">30,2 %</span><span class="sxs-lookup"><span data-stu-id="a9e7b-145">30.2%</span></span>               | <span data-ttu-id="a9e7b-146">16,6 %</span><span class="sxs-lookup"><span data-stu-id="a9e7b-146">16.6%</span></span>               |

<span data-ttu-id="a9e7b-147">L’exécution de l’opération `Import-Csv` a été considérablement accélérée après une régression de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-147">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="a9e7b-148">L’exemple suivant utilise un fichier CSV de test contenant 26 616 lignes et six colonnes :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-148">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="a9e7b-149">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="a9e7b-149">Windows PowerShell 5.1</span></span> | <span data-ttu-id="a9e7b-150">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="a9e7b-150">PowerShell Core 6.0</span></span> | <span data-ttu-id="a9e7b-151">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="a9e7b-151">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="a9e7b-152">Durée (s)</span><span class="sxs-lookup"><span data-stu-id="a9e7b-152">Time (sec)</span></span>   | <span data-ttu-id="a9e7b-153">0,441</span><span class="sxs-lookup"><span data-stu-id="a9e7b-153">0.441</span></span>                  | <span data-ttu-id="a9e7b-154">1,069</span><span class="sxs-lookup"><span data-stu-id="a9e7b-154">1.069</span></span>               | <span data-ttu-id="a9e7b-155">0,268</span><span class="sxs-lookup"><span data-stu-id="a9e7b-155">0.268</span></span>                  |
| <span data-ttu-id="a9e7b-156">Accélération (en %)</span><span class="sxs-lookup"><span data-stu-id="a9e7b-156">Speed-up (%)</span></span> | <span data-ttu-id="a9e7b-157">N/A</span><span class="sxs-lookup"><span data-stu-id="a9e7b-157">N/A</span></span>                    | <span data-ttu-id="a9e7b-158">-142,4 %</span><span class="sxs-lookup"><span data-stu-id="a9e7b-158">-142.4%</span></span>             | <span data-ttu-id="a9e7b-159">74,9 % (39,2 % sur WPS)</span><span class="sxs-lookup"><span data-stu-id="a9e7b-159">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="a9e7b-160">Enfin, la conversion de code JSON en `PSObject` a été accélérée de plus de 50 % par rapport à Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-160">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="a9e7b-161">L’exemple suivant utilise un fichier JSON de test d’environ 2 Mo :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-161">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="a9e7b-162">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="a9e7b-162">Windows PowerShell 5.1</span></span> | <span data-ttu-id="a9e7b-163">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="a9e7b-163">PowerShell Core 6.0</span></span> | <span data-ttu-id="a9e7b-164">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="a9e7b-164">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="a9e7b-165">Durée (s)</span><span class="sxs-lookup"><span data-stu-id="a9e7b-165">Time (sec)</span></span>   | <span data-ttu-id="a9e7b-166">0,259</span><span class="sxs-lookup"><span data-stu-id="a9e7b-166">0.259</span></span>                  | <span data-ttu-id="a9e7b-167">0,577</span><span class="sxs-lookup"><span data-stu-id="a9e7b-167">0.577</span></span>               | <span data-ttu-id="a9e7b-168">0,125</span><span class="sxs-lookup"><span data-stu-id="a9e7b-168">0.125</span></span>                  |
| <span data-ttu-id="a9e7b-169">Accélération (en %)</span><span class="sxs-lookup"><span data-stu-id="a9e7b-169">Speed-up (%)</span></span> | <span data-ttu-id="a9e7b-170">N/A</span><span class="sxs-lookup"><span data-stu-id="a9e7b-170">N/A</span></span>                    | <span data-ttu-id="a9e7b-171">-122,8 %</span><span class="sxs-lookup"><span data-stu-id="a9e7b-171">-122.8%</span></span>             | <span data-ttu-id="a9e7b-172">78,3 % (51,7 % sur WPS)</span><span class="sxs-lookup"><span data-stu-id="a9e7b-172">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a><span data-ttu-id="a9e7b-173">Consulter `system32` pour connaître les modules compatibles fournis avec Windows</span><span class="sxs-lookup"><span data-stu-id="a9e7b-173">Check `system32` for compatible in-box modules on Windows</span></span>

<span data-ttu-id="a9e7b-174">Dans la mise à jour 1809 de Windows 10 et dans Windows Server 2019, nous avons mis à jour plusieurs des modules PowerShell fournis avec Windows, afin de les marquer comme compatibles avec PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-174">In the Windows 10 1809 update and Windows Server 2019, we updated a number of in-box PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="a9e7b-175">Lorsque PowerShell Core 6.1 démarre, il inclut automatiquement `$windir\System32` dans la variable d’environnement `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-175">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span> <span data-ttu-id="a9e7b-176">Toutefois, il expose uniquement les modules à `Get-Module` et `Import-Module` si son `CompatiblePSEdition` est marqué comme étant compatible avec `Core`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-176">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="a9e7b-177">Les modules qui sont disponibles peuvent varier selon les rôles et les fonctionnalités installés.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-177">You may see different available modules depending on what roles and features are installed.</span></span>

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

<span data-ttu-id="a9e7b-178">Vous pouvez remplacer ce comportement pour afficher tous les modules à l’aide du paramètre de commutateur `-SkipEditionCheck`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-178">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="a9e7b-179">Nous avons également ajouté une propriété `PSEdition` à la sortie de la table.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-179">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="a9e7b-180">Pour plus d’informations sur ce comportement, consultez[PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="a9e7b-180">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="a9e7b-181">Applets de commande de Markdown et de rendu</span><span class="sxs-lookup"><span data-stu-id="a9e7b-181">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="a9e7b-182">Le standard Markdown permet de créer des documents en texte clair avec une mise en forme de base qui peuvent être affichés en HTML.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-182">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="a9e7b-183">Nous avons ajouté des applets de commande à la version 6.1 qui vous permettent de convertir et de restituer des documents Markdown dans la console, notamment :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-183">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="a9e7b-184">Par exemple, `Show-Markdown` restitue un fichier Markdown dans la console :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-184">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Exemple Show-Markdown](./images/markdown_example.png)

<span data-ttu-id="a9e7b-186">Pour plus d’informations sur le fonctionnement de ces applets de commande, consultez [ce document RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="a9e7b-186">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="a9e7b-187">Indicateurs de fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="a9e7b-187">Experimental feature flags</span></span>

<span data-ttu-id="a9e7b-188">Nous avons activé la prise en charge des [fonctionnalités expérimentales][].</span><span class="sxs-lookup"><span data-stu-id="a9e7b-188">We enabled support for [Experimental Features][].</span></span> <span data-ttu-id="a9e7b-189">Cela permet aux développeurs PowerShell de fournir de nouvelles fonctionnalités et d’obtenir des commentaires avant la fin de la conception.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-189">This allows PowerShell developers to deliver new features and get feedback before the design is complete.</span></span> <span data-ttu-id="a9e7b-190">Cela nous évite ainsi d’avoir à apporter d’importantes modifications à mesure que la conception évolue.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-190">This way we avoid making breaking changes as the design evolves.</span></span>

<span data-ttu-id="a9e7b-191">Utilisez `Get-ExperimentalFeature` pour obtenir la liste des fonctionnalités expérimentales disponibles.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-191">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="a9e7b-192">Vous pouvez activer ou désactiver ces fonctionnalités avec `Enable-ExperimentalFeature` et `Disable-ExperimentalFeature`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-192">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

<span data-ttu-id="a9e7b-193">Pour plus d’informations sur ces fonctionnalités, consultez [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="a9e7b-193">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="a9e7b-194">Améliorations apportées aux applets de commande web</span><span class="sxs-lookup"><span data-stu-id="a9e7b-194">Web cmdlet improvements</span></span>

<span data-ttu-id="a9e7b-195">Grâce à [@markekraus](https://github.com/markekraus), une myriade d’améliorations ont été apportées à nos applets de commande web [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="a9e7b-195">Thanks to [@markekraus](https://github.com/markekraus), a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="a9e7b-196">et [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span><span class="sxs-lookup"><span data-stu-id="a9e7b-196">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="a9e7b-197">[Demande de tirage #6109](https://github.com/PowerShell/PowerShell/pull/6109) - encodage par défaut défini sur UTF-8 pour les réponses `application-json`</span><span class="sxs-lookup"><span data-stu-id="a9e7b-197">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="a9e7b-198">[Demande de tirage #6018](https://github.com/PowerShell/PowerShell/pull/6018) - paramètre `-SkipHeaderValidation` pour autoriser les en-têtes `Content-Type` qui ne sont pas conformes aux normes</span><span class="sxs-lookup"><span data-stu-id="a9e7b-198">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="a9e7b-199">[Demande de tirage #5972](https://github.com/PowerShell/PowerShell/pull/5972) - paramètre `Form` permettant la prise en charge simplifiée de `multipart/form-data`</span><span class="sxs-lookup"><span data-stu-id="a9e7b-199">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="a9e7b-200">[Demande de tirage #6338](https://github.com/PowerShell/PowerShell/pull/6338) - gestion des clés de relation conforme et ne respectant pas la casse</span><span class="sxs-lookup"><span data-stu-id="a9e7b-200">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="a9e7b-201">[Demande de tirage #6447](https://github.com/PowerShell/PowerShell/pull/6447) - ajouter le paramètre `-Resume` pour les applets de commande web</span><span class="sxs-lookup"><span data-stu-id="a9e7b-201">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="a9e7b-202">Améliorations de la communication à distance</span><span class="sxs-lookup"><span data-stu-id="a9e7b-202">Remoting improvements</span></span>

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a><span data-ttu-id="a9e7b-203">PowerShell Direct pour les conteneurs tente d’abord d’utiliser PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="a9e7b-203">PowerShell Direct for Containers tries to use PowerShell Core first</span></span>

<span data-ttu-id="a9e7b-204">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) est une fonctionnalité PowerShell et Hyper-V, qui vous permet de vous connecter à une machine virtuelle Hyper-V ou à un conteneur sans connectivité réseau ni service de gestion à distance.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-204">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM or Container without network connectivity or other remote management services.</span></span>

<span data-ttu-id="a9e7b-205">Auparavant, PowerShell Direct se connectait à l’aide de l’instance Windows PowerShell fournie dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-205">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the Container.</span></span> <span data-ttu-id="a9e7b-206">À présent, PowerShell Direct tente d’abord de se connecter à l’aide de l’un des `pwsh.exe` disponibles dans la variable d’environnement `PATH`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-206">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span> <span data-ttu-id="a9e7b-207">Si aucun `pwsh.exe` n’est disponible, PowerShell Direct utilise à nouveau `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-207">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="a9e7b-208">À présent, `Enable-PSRemoting` crée des points de terminaison de communication à distance distincts pour chaque préversion</span><span class="sxs-lookup"><span data-stu-id="a9e7b-208">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="a9e7b-209">À présent, `Enable-PSRemoting` crée deux configurations de session de communication à distance :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-209">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="a9e7b-210">Une pour la version principale de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-210">One for the major version of PowerShell.</span></span> <span data-ttu-id="a9e7b-211">Par exemple : `PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-211">For example, `PowerShell.6`.</span></span> <span data-ttu-id="a9e7b-212">Pour les mises à jour de la version secondaire, ce point de terminaison peut correspondre à la configuration de session PowerShell 6 qui est appliquée à l’échelle du système</span><span class="sxs-lookup"><span data-stu-id="a9e7b-212">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="a9e7b-213">Une configuration de session spécifique à une version, par exemple : `PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="a9e7b-213">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="a9e7b-214">Ce comportement est utile si vous souhaitez que plusieurs versions de PowerShell 6 soient installées et accessibles sur un même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-214">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="a9e7b-215">En outre, les préversions de PowerShell peuvent désormais obtenir leurs propres configurations de session de communication à distance en exécutant l’applet de commande `Enable-PSRemoting` :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-215">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="a9e7b-216">Votre sortie peut être différente si vous n’avez pas configuré WinRM au préalable.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-216">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="a9e7b-217">Ensuite, vous pouvez voir les différentes configurations de session PowerShell pour la préversion et les builds stables de PowerShell 6, ainsi que pour chaque version.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-217">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="a9e7b-218">Syntaxe `user@host:port` prise en charge pour le protocole SSH</span><span class="sxs-lookup"><span data-stu-id="a9e7b-218">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="a9e7b-219">Les clients SSH prennent généralement en charge une chaîne de connexion au format `user@host:port`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-219">SSH clients typically support a connection string in the format `user@host:port`.</span></span> <span data-ttu-id="a9e7b-220">Avec l’ajout du protocole SSH pour la communication à distance PowerShell, nous permettons désormais la prise en charge de ce format de chaîne de connexion :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-220">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="a9e7b-221">Option MSI pour ajouter un menu contextuel de shell dans l’Explorateur Windows</span><span class="sxs-lookup"><span data-stu-id="a9e7b-221">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="a9e7b-222">Grâce à [@bergmeister](https://github.com/bergmeister), vous pouvez désormais activer un menu contextuel dans Windows.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-222">Thanks to [@bergmeister](https://github.com/bergmeister), now you can enable a context menu on Windows.</span></span> <span data-ttu-id="a9e7b-223">Vous pouvez ouvrir votre installation de PowerShell 6.1 à l’échelle du système à partir de n’importe quel dossier de l’Explorateur Windows :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-223">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![Menu contextuel de shell pour PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="a9e7b-225">Avantages</span><span class="sxs-lookup"><span data-stu-id="a9e7b-225">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="a9e7b-226">Option « Exécuter en tant qu’administrateur » dans la liste de raccourcis Windows</span><span class="sxs-lookup"><span data-stu-id="a9e7b-226">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="a9e7b-227">Grâce à [@bergmeister](https://github.com/bergmeister), la liste de raccourcis de PowerShell Core comprend désormais l’option « Exécuter en tant qu’administrateur » :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-227">Thanks to [@bergmeister](https://github.com/bergmeister), the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![Option Exécuter en tant qu’administrateur dans la liste de raccourcis PowerShell 6](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="a9e7b-229">`cd -` retourne au répertoire précédent</span><span class="sxs-lookup"><span data-stu-id="a9e7b-229">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="a9e7b-230">Sur Linux :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-230">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="a9e7b-231">En outre, `cd` et `cd --` sont remplacés par `$HOME`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-231">Also, `cd` and `cd --` change to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="a9e7b-232">Grâce à [@iSazonov](https://github.com/iSazonov), l’applet de commande [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) a été déplacée vers PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-232">Thanks to [@iSazonov](https://github.com/iSazonov), the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="a9e7b-233">`Update-Help` en tant que non administrateur</span><span class="sxs-lookup"><span data-stu-id="a9e7b-233">`Update-Help` as non-admin</span></span>

<span data-ttu-id="a9e7b-234">À la demande générale, il n’est plus obligatoire d’exécuter `Update-Help` en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-234">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span> <span data-ttu-id="a9e7b-235">Par défaut, `Update-Help` enregistre l’aide dans un dossier de portée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-235">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="a9e7b-236">Nouvelles méthodes et propriétés de `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="a9e7b-236">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="a9e7b-237">Grâce à [@iSazonov](https://github.com/iSazonov), nous avons ajouté de nouvelles méthodes et propriétés à `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-237">Thanks to [@iSazonov](https://github.com/iSazonov), we've added new methods and properties to `PSCustomObject`.</span></span> <span data-ttu-id="a9e7b-238">`PSCustomObject` inclut désormais une propriété `Count`/`Length`, comme les autres objets.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-238">`PSCustomObject` now includes a `Count`/`Length` property like other objects.</span></span>

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

<span data-ttu-id="a9e7b-239">Cela inclut également les méthodes `ForEach` et `Where` qui vous permettent d’utiliser et de filtrer les éléments `PSCustomObject` :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-239">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

<span data-ttu-id="a9e7b-240">Grâce à @SimonWahlin, nous avons ajouté le paramètre `-Not` à `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-240">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span> <span data-ttu-id="a9e7b-241">Vous pouvez désormais filtrer un objet au niveau du pipeline pour y voir l’absence d’une propriété, ou la présence d’une valeur de propriété Null ou vide.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-241">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="a9e7b-242">Par exemple, cette commande retourne tous les services dans lesquels aucun service dépendant n’est défini :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-242">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="a9e7b-243">`New-ModuleManifest` crée un document UTF-8 sans marque d’ordre d’octet</span><span class="sxs-lookup"><span data-stu-id="a9e7b-243">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="a9e7b-244">Compte tenu du passage au UTF-8 sans marque d’ordre d’octet dans PowerShell 6.0, nous avons mis à jour l’applet de commande `New-ModuleManifest` pour créer un document UTF-8 sans marque d’ordre d’octet, au lieu d’un document UTF-16.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-244">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="a9e7b-245">Conversions de PSMethod en Delegate</span><span class="sxs-lookup"><span data-stu-id="a9e7b-245">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="a9e7b-246">Grâce à [@powercode](https://github.com/powercode), nous prenons désormais en charge la conversion d’un `PSMethod` en un délégué.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-246">Thanks to [@powercode](https://github.com/powercode), we now support the conversion of a `PSMethod` into a delegate.</span></span> <span data-ttu-id="a9e7b-247">Vous pouvez ainsi effectuer des opérations comme passer `PSMethod` `[M]::DoubleStrLen` en tant que valeur de délégué dans `[M]::AggregateString` :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-247">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

<span data-ttu-id="a9e7b-248">Pour plus d’informations sur cette modification, consultez [Demande de tirage #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="a9e7b-248">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="a9e7b-249">Écart type dans `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="a9e7b-249">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="a9e7b-250">Grâce à [@CloudyDino](https://github.com/CloudyDino), nous avons ajouté une propriété `StandardDeviation` à `Measure-Object` :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-250">Thanks to [@CloudyDino](https://github.com/CloudyDino), we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

<span data-ttu-id="a9e7b-251">Grâce à [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` comprend désormais le paramètre `Password`, qui accepte un `SecureString`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-251">Thanks to [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="a9e7b-252">Cela vous permet de l’utiliser de manière non interactive :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-252">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="a9e7b-253">Suppression de la fonction `more`</span><span class="sxs-lookup"><span data-stu-id="a9e7b-253">Removal of the `more` function</span></span>

<span data-ttu-id="a9e7b-254">Auparavant, PowerShell fournissait une fonction appelée `more` dans Windows qui wrappait `more.com`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-254">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span> <span data-ttu-id="a9e7b-255">Cette fonction a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-255">That function has now been removed.</span></span>

<span data-ttu-id="a9e7b-256">En outre, la fonction `help` utilise désormais `more.com` dans Windows, ou un récepteur système par défaut spécifié par `$env:PAGER` sur les plateformes non Windows.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-256">Also, the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="a9e7b-257">`cd DriveName:` renvoie désormais les utilisateurs au répertoire de travail actuel du lecteur</span><span class="sxs-lookup"><span data-stu-id="a9e7b-257">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="a9e7b-258">Auparavant, l’utilisation de `Set-Location` ou de `cd` pour retourner à un PSDrive avait pour effet d’envoyer les utilisateurs à l’emplacement par défaut du lecteur.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-258">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="a9e7b-259">Grâce à [@mcbobke](https://github.com/mcbobke), les utilisateurs sont désormais envoyés vers le dernier répertoire de travail connu pour cette session.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-259">Thanks to [@mcbobke](https://github.com/mcbobke), users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="a9e7b-260">Accélérateurs de type Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a9e7b-260">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="a9e7b-261">Dans Windows PowerShell, nous avons inclus les accélérateurs de type suivants afin de faciliter l’utilisation des différents types :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-261">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="a9e7b-262">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="a9e7b-262">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="a9e7b-263">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="a9e7b-263">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="a9e7b-264">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="a9e7b-264">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="a9e7b-265">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="a9e7b-265">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="a9e7b-266">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="a9e7b-266">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="a9e7b-267">Ces accélérateurs de type n’étaient pas inclus dans PowerShell 6. Ils sont désormais disponibles dans PowerShell 6.1 pour Windows.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-267">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="a9e7b-268">Ces types facilitent la construction d’objets AD et WMI.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-268">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="a9e7b-269">Par exemple, vous pouvez exécuter des requêtes avec LDAP :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-269">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="a9e7b-270">L’exemple suivant crée un objet CIM Win32_OperatingSystem :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-270">Following example creates a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

<span data-ttu-id="a9e7b-271">Cet exemple retourne un objet ManagementClass pour la classe Win32_OperatingSystem.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-271">This example returns a ManagementClass object for Win32_OperatingSystem class.</span></span>

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="a9e7b-272">Alias `-lp` pour tous les paramètres `-LiteralPath`</span><span class="sxs-lookup"><span data-stu-id="a9e7b-272">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="a9e7b-273">Grâce à [@kvprasoon](https://github.com/kvprasoon), nous disposons désormais d’un alias de paramètre `-lp` pour toutes les applets de commande PowerShell intégrées qui ont un paramètre `-LiteralPath`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-273">Thanks to [@kvprasoon](https://github.com/kvprasoon), we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="a9e7b-274">Dernières modifications</span><span class="sxs-lookup"><span data-stu-id="a9e7b-274">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="a9e7b-275">Chemins d’installation MSI dans Windows</span><span class="sxs-lookup"><span data-stu-id="a9e7b-275">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="a9e7b-276">Dans Windows, le package MSI est désormais installé au chemin suivant :</span><span class="sxs-lookup"><span data-stu-id="a9e7b-276">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="a9e7b-277">`$env:ProgramFiles\PowerShell\6\` pour l’installation stable de 6.x</span><span class="sxs-lookup"><span data-stu-id="a9e7b-277">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="a9e7b-278">`$env:ProgramFiles\PowerShell\6-preview\` pour l’installation de la préversion de 6.x</span><span class="sxs-lookup"><span data-stu-id="a9e7b-278">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="a9e7b-279">Cette modification garantit que PowerShell Core pourra faire l’objet de mises à jour et de maintenances par Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-279">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="a9e7b-280">Pour plus d’informations, consultez [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="a9e7b-280">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="a9e7b-281">Les données de télémétrie peuvent uniquement être désactivées avec une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="a9e7b-281">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="a9e7b-282">PowerShell Core envoie des données de télémétrie de base à Microsoft au lancement de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-282">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="a9e7b-283">Les données incluent le nom du système d’exploitation, la version du système d’exploitation et la version de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-283">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="a9e7b-284">Ces données nous permettent de mieux comprendre les environnements dans lesquels PowerShell est utilisé, ainsi que de classer par ordre de priorité les correctifs et les nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-284">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="a9e7b-285">Pour refuser la collecte de ces données de télémétrie, définissez la variable d’environnement `POWERSHELL_TELEMETRY_OPTOUT` sur `true`, `yes` ou `1`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-285">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="a9e7b-286">Il n’est plus possible de supprimer le fichier `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` pour désactiver la télémétrie.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-286">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="a9e7b-287">Interdiction de l’authentification de base via HTTP pour la communication à distance PowerShell sur les plateformes Unix</span><span class="sxs-lookup"><span data-stu-id="a9e7b-287">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="a9e7b-288">Pour empêcher l’utilisation de trafic non chiffré, la communication à distance PowerShell sur les plateformes Unix exige désormais une authentification NTLM/Negotiate ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-288">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="a9e7b-289">Pour plus d’informations sur ces modifications, consultez [Problème #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span><span class="sxs-lookup"><span data-stu-id="a9e7b-289">For more information on these changes, check out [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="a9e7b-290">Suppression de `VisualBasic` comme langage pris en charge dans Add-Type</span><span class="sxs-lookup"><span data-stu-id="a9e7b-290">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="a9e7b-291">Auparavant, vous pouviez compiler du code Visual Basic à l’aide de l’applet de commande `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-291">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span> <span data-ttu-id="a9e7b-292">Visual Basic était rarement utilisé avec `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-292">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="a9e7b-293">Nous avons supprimé cette fonctionnalité afin de réduire la taille de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-293">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="a9e7b-294">Nettoyage des utilisations de `CommandTypes.Workflow` et `WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="a9e7b-294">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="a9e7b-295">Pour plus d’informations sur ces modifications, consultez [Demande de tirage #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="a9e7b-295">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>

### <a name="group-object-now-sorts-the-groups"></a><span data-ttu-id="a9e7b-296">Group-Object trie désormais les groupes</span><span class="sxs-lookup"><span data-stu-id="a9e7b-296">Group-Object now sorts the groups</span></span>

<span data-ttu-id="a9e7b-297">Dans le cadre de l’amélioration des performances, `Group-Object` renvoie désormais une liste triée des groupes.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-297">As part of the performance improvement, `Group-Object` now returns a sorted listing of the groups.</span></span>
<span data-ttu-id="a9e7b-298">Bien que vous ne deviez pas vous fier à l’ordre, vous pouvez être désactivé à cause de cette modification si vous souhaitiez le premier groupe.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-298">Although you should not rely on the order, you could be broken by this change if you wanted the first group.</span></span> <span data-ttu-id="a9e7b-299">Nous avons décidé que l’amélioration des performances valait cette modification dans la mesure où l’impact de la dépendance sur le comportement précédent est faible.</span><span class="sxs-lookup"><span data-stu-id="a9e7b-299">We decided that this performance improvement was worth the change since the impact of being dependent on previous behavior is low.</span></span>

<span data-ttu-id="a9e7b-300">Pour plus d’informations sur cette modification, consultez le [Problème #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span><span class="sxs-lookup"><span data-stu-id="a9e7b-300">For more information on this change, see [Issue #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span></span>

<!-- URL references -->
[Fonctionnalités expérimentales]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
