---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WindowsPackageCab
ms.openlocfilehash: ec465b2c3b1d180ba46ee24a61f2be1129148962
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954636"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="f7bcc-103">Ressource DSC WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="f7bcc-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="f7bcc-104">S’applique à : Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f7bcc-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="f7bcc-105">La ressource **WindowsPackageCab** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’installer ou de désinstaller des packages de cabinet Windows (.cab) sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="f7bcc-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="f7bcc-106">Le nœud cible doit disposer du module DISM PowerShell installé.</span><span class="sxs-lookup"><span data-stu-id="f7bcc-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="f7bcc-107">Pour plus d’informations, consultez [Utilisation de DISM Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="f7bcc-107">For information, see [Use DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>

## <a name="syntax"></a><span data-ttu-id="f7bcc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7bcc-108">Syntax</span></span>

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="f7bcc-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f7bcc-109">Properties</span></span>

|<span data-ttu-id="f7bcc-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="f7bcc-110">Property</span></span> |<span data-ttu-id="f7bcc-111">Description</span><span class="sxs-lookup"><span data-stu-id="f7bcc-111">Description</span></span> |
|---|---|
|<span data-ttu-id="f7bcc-112">Name</span><span class="sxs-lookup"><span data-stu-id="f7bcc-112">Name</span></span> |<span data-ttu-id="f7bcc-113">Indique le nom du package pour lequel vous souhaitez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="f7bcc-113">Indicates the name of the package for you want to ensure a specific state.</span></span> |
|<span data-ttu-id="f7bcc-114">SourcePath</span><span class="sxs-lookup"><span data-stu-id="f7bcc-114">SourcePath</span></span> |<span data-ttu-id="f7bcc-115">Indique le chemin où se trouve le package.</span><span class="sxs-lookup"><span data-stu-id="f7bcc-115">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="f7bcc-116">LogPath</span><span class="sxs-lookup"><span data-stu-id="f7bcc-116">LogPath</span></span> |<span data-ttu-id="f7bcc-117">Indique le chemin complet où vous souhaitez que le fournisseur enregistre un fichier journal pour installer ou désinstaller le package.</span><span class="sxs-lookup"><span data-stu-id="f7bcc-117">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="f7bcc-118">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="f7bcc-118">Common properties</span></span>

|<span data-ttu-id="f7bcc-119">Propriété</span><span class="sxs-lookup"><span data-stu-id="f7bcc-119">Property</span></span> |<span data-ttu-id="f7bcc-120">Description</span><span class="sxs-lookup"><span data-stu-id="f7bcc-120">Description</span></span> |
|---|---|
|<span data-ttu-id="f7bcc-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f7bcc-121">DependsOn</span></span> |<span data-ttu-id="f7bcc-122">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="f7bcc-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f7bcc-123">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f7bcc-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="f7bcc-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="f7bcc-124">Ensure</span></span> |<span data-ttu-id="f7bcc-125">Indique si le package est installé.</span><span class="sxs-lookup"><span data-stu-id="f7bcc-125">Indicates if the package is installed.</span></span> <span data-ttu-id="f7bcc-126">Définissez cette propriété sur **Absent** pour faire en sorte que le package ne soit pas installé (ou désinstallé, si le package est installé).</span><span class="sxs-lookup"><span data-stu-id="f7bcc-126">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="f7bcc-127">Définissez-la sur **Present** pour faire en sorte que le package soit installé.</span><span class="sxs-lookup"><span data-stu-id="f7bcc-127">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="f7bcc-128">**Ensure** est une propriété obligatoire pour la ressource **WindowsPackageCab**.</span><span class="sxs-lookup"><span data-stu-id="f7bcc-128">**Ensure** is a required property on the **WindowsPackageCab** resource.</span></span> |
|<span data-ttu-id="f7bcc-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f7bcc-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="f7bcc-130">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="f7bcc-130">Sets the credential for running the entire resource as.</span></span> |

## <a name="example"></a><span data-ttu-id="f7bcc-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="f7bcc-131">Example</span></span>

<span data-ttu-id="f7bcc-132">L’exemple de configuration suivant accepte des paramètres d’entrée et garantit que le fichier spécifié par le paramètre `$Name` est installé.</span><span class="sxs-lookup"><span data-stu-id="f7bcc-132">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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