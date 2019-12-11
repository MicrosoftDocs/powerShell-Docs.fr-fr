---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource nxFileLine dans DSC pour Linux
ms.openlocfilehash: 2e94bab318b5db65df88d268a88585079bab89bf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953216"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="9d318-103">Ressource nxFileLine dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="9d318-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="9d318-104">La ressource **nxFileLine** de DSC (Desired State Configuration) PowerShell offre un mécanisme permettant de gérer les lignes d’un fichier de configuration sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="9d318-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d318-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d318-105">Syntax</span></span>

```Syntax
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="9d318-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9d318-106">Properties</span></span>

|<span data-ttu-id="9d318-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="9d318-107">Property</span></span> |<span data-ttu-id="9d318-108">Description</span><span class="sxs-lookup"><span data-stu-id="9d318-108">Description</span></span> |
|---|---|
|<span data-ttu-id="9d318-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="9d318-109">FilePath</span></span> |<span data-ttu-id="9d318-110">Le chemin complet du fichier dans lequel gérer les lignes se trouve sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="9d318-110">The full path to the file to manage lines in on the target node.</span></span> |
|<span data-ttu-id="9d318-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="9d318-111">ContainsLine</span></span> |<span data-ttu-id="9d318-112">Une ligne à vérifier se trouve dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="9d318-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="9d318-113">Cette ligne est ajoutée au fichier si elle ne s’y trouve pas.</span><span class="sxs-lookup"><span data-stu-id="9d318-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="9d318-114">**ContainsLine** est obligatoire, mais peut être défini sur une chaîne vide (`ContainsLine = ""`) s’il n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9d318-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span> |
|<span data-ttu-id="9d318-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="9d318-115">DoesNotContainPattern</span></span> |<span data-ttu-id="9d318-116">Modèle d’expression régulière pour les lignes qui ne doivent pas se trouver dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="9d318-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="9d318-117">Les lignes du fichier qui correspondent à cette expression régulière seront supprimées du fichier.</span><span class="sxs-lookup"><span data-stu-id="9d318-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="9d318-118">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="9d318-118">Common properties</span></span>

|<span data-ttu-id="9d318-119">Propriété</span><span class="sxs-lookup"><span data-stu-id="9d318-119">Property</span></span> |<span data-ttu-id="9d318-120">Description</span><span class="sxs-lookup"><span data-stu-id="9d318-120">Description</span></span> |
|---|---|
|<span data-ttu-id="9d318-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9d318-121">DependsOn</span></span> |<span data-ttu-id="9d318-122">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="9d318-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9d318-123">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="9d318-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="9d318-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="9d318-124">Example</span></span>

<span data-ttu-id="9d318-125">Cet exemple montre comment utiliser la ressource **nxFileLine** pour configurer le fichier `/etc/sudoers`, en s’assurant que l’utilisateur :monuser est configuré sur DoNotRequireTTY.</span><span class="sxs-lookup"><span data-stu-id="9d318-125">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = "/etc/sudoers"
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```