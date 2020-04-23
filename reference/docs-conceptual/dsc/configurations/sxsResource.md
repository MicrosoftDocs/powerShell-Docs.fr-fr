---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Importer une version spécifique d’une ressource installée
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953986"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="88b1a-103">Importer une version spécifique d’une ressource installée</span><span class="sxs-lookup"><span data-stu-id="88b1a-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="88b1a-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="88b1a-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="88b1a-105">Dans PowerShell 5.0, des versions distinctes des ressources DSC peuvent être installées sur un ordinateur côte à côte.</span><span class="sxs-lookup"><span data-stu-id="88b1a-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="88b1a-106">Un module de ressources peut stocker des versions distinctes d’une ressource dans des dossiers nommés selon la version.</span><span class="sxs-lookup"><span data-stu-id="88b1a-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="88b1a-107">Installation de versions de ressources distinctes côte à côte</span><span class="sxs-lookup"><span data-stu-id="88b1a-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="88b1a-108">Vous pouvez utiliser les paramètres **MinimumVersion**, **MaximumVersion** et **RequiredVersion** de l’applet de commande [Install-Module](/powershell/module/PowershellGet/Install-Module) pour indiquer la version d’un module à installer.</span><span class="sxs-lookup"><span data-stu-id="88b1a-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="88b1a-109">L’appel de l’applet de commande **Install-Module** sans spécifier de version installe la version la plus récente.</span><span class="sxs-lookup"><span data-stu-id="88b1a-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="88b1a-110">Par exemple, il existe plusieurs versions du module **xFailOverCluster**, chacun contenant une ressource **xCluster**.</span><span class="sxs-lookup"><span data-stu-id="88b1a-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="88b1a-111">L’appel de l’applet de commande **Install-Module** sans spécifier de numéro de version installe la version la plus récente du module.</span><span class="sxs-lookup"><span data-stu-id="88b1a-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="88b1a-112">Pour installer une version spécifique d’un module, vous devez spécifier une version 1.1.0.0 de **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="88b1a-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="88b1a-113">Cette opération installe la version spécifiée côte à côte avec la version installée.</span><span class="sxs-lookup"><span data-stu-id="88b1a-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="88b1a-114">Vous voyez à présent les deux versions du module lorsque vous utilisez `Get-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="88b1a-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="88b1a-115">Spécification d’une version de ressource dans une configuration</span><span class="sxs-lookup"><span data-stu-id="88b1a-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="88b1a-116">Si des versions de ressources distinctes sont installées sur un ordinateur, vous devez spécifier la version d’une ressource quand vous l’utilisez dans une configuration.</span><span class="sxs-lookup"><span data-stu-id="88b1a-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="88b1a-117">Pour cela, vous devez spécifier le paramètre **ModuleVersion** du mot-clé **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="88b1a-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="88b1a-118">Si vous ne parvenez pas à spécifier la version d’un module d’une ressource dont plusieurs versions sont installées, la configuration génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="88b1a-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="88b1a-119">La configuration suivante montre comment spécifier la version de la ressource à appeler :</span><span class="sxs-lookup"><span data-stu-id="88b1a-119">The following configuration shows how to specify the version of the resource to call:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

><span data-ttu-id="88b1a-120">Remarque : Le paramètre ModuleVersion d’Import-DscResource n’est pas disponible dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="88b1a-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="88b1a-121">Dans PowerShell 4.0, vous pouvez spécifier une version du module en passant un objet de spécification de module au paramètre ModuleName d’Import-DscResource.</span><span class="sxs-lookup"><span data-stu-id="88b1a-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="88b1a-122">Un objet de spécification de module est une table de hachage qui contient les clés ModuleName et RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="88b1a-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="88b1a-123">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="88b1a-123">For example:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

<span data-ttu-id="88b1a-124">Cela fonctionne également dans PowerShell 5.0, mais il est recommandé d’utiliser le paramètre **ModuleVersion**.</span><span class="sxs-lookup"><span data-stu-id="88b1a-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="88b1a-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88b1a-125">See also</span></span>

- [<span data-ttu-id="88b1a-126">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="88b1a-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="88b1a-127">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="88b1a-127">DSC Resources</span></span>](../resources/resources.md)
