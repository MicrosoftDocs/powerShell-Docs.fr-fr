---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WindowsPackageCab
ms.openlocfilehash: 8c4de193c8ea787dd125436f86aa0b5eafdb1509
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="0d31d-103">Ressource DSC WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="0d31d-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="0d31d-104">S’applique à : Windows PowerShell 5.1 et ultérieur</span><span class="sxs-lookup"><span data-stu-id="0d31d-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="0d31d-105">La ressource **WindowsPackageCab** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’installer ou de désinstaller des packages de cabinet Windows (.cab) sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="0d31d-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="0d31d-106">Le nœud cible doit disposer du module DISM PowerShell installé.</span><span class="sxs-lookup"><span data-stu-id="0d31d-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="0d31d-107">Pour plus d’informations, consultez [Utilisation de DISM Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="0d31d-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="0d31d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d31d-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="0d31d-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0d31d-109">Properties</span></span>

|  <span data-ttu-id="0d31d-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="0d31d-110">Property</span></span>  |  <span data-ttu-id="0d31d-111">Description</span><span class="sxs-lookup"><span data-stu-id="0d31d-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="0d31d-112">Name</span><span class="sxs-lookup"><span data-stu-id="0d31d-112">Name</span></span>| <span data-ttu-id="0d31d-113">Indique le nom du package pour lequel vous souhaitez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="0d31d-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="0d31d-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="0d31d-114">Ensure</span></span>| <span data-ttu-id="0d31d-115">Indique si le package est installé.</span><span class="sxs-lookup"><span data-stu-id="0d31d-115">Indicates if the package is installed.</span></span> <span data-ttu-id="0d31d-116">Définissez cette propriété sur « Absent » pour vous assurer que le package n’est pas installé (ou désinstallé, si le package n’est pas installé).</span><span class="sxs-lookup"><span data-stu-id="0d31d-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="0d31d-117">Définissez cette propriété sur « Present » (valeur par défaut) pour vous assurer que le package est installé.</span><span class="sxs-lookup"><span data-stu-id="0d31d-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="0d31d-118">Path</span><span class="sxs-lookup"><span data-stu-id="0d31d-118">Path</span></span>| <span data-ttu-id="0d31d-119">Indique le chemin où se trouve le package.</span><span class="sxs-lookup"><span data-stu-id="0d31d-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="0d31d-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="0d31d-120">LogPath</span></span>| <span data-ttu-id="0d31d-121">Indique le chemin complet où vous souhaitez que le fournisseur enregistre un fichier journal pour installer ou désinstaller le package.</span><span class="sxs-lookup"><span data-stu-id="0d31d-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="0d31d-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0d31d-122">DependsOn</span></span> | <span data-ttu-id="0d31d-123">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="0d31d-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0d31d-124">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : DependsOn = "[ResourceType]ResourceName"</span><span class="sxs-lookup"><span data-stu-id="0d31d-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="0d31d-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="0d31d-125">Example</span></span>

<span data-ttu-id="0d31d-126">L’exemple de configuration suivant accepte des paramètres d’entrée et garantit que le fichier spécifié par le paramètre `$Name` est installé.</span><span class="sxs-lookup"><span data-stu-id="0d31d-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```