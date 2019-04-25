---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource nxFileLine dans DSC pour Linux
ms.openlocfilehash: 6a91db25638b09659adfabcec78f91bcb2e69dd9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077957"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="07f0c-103">Ressource nxFileLine dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="07f0c-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="07f0c-104">La ressource **nxFileLine** de DSC (Desired State Configuration) PowerShell offre un mécanisme permettant de gérer les lignes d’un fichier de configuration sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="07f0c-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="07f0c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07f0c-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="07f0c-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="07f0c-106">Properties</span></span>

|  <span data-ttu-id="07f0c-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="07f0c-107">Property</span></span> |  <span data-ttu-id="07f0c-108">Description</span><span class="sxs-lookup"><span data-stu-id="07f0c-108">Description</span></span> |
|---|---|
| <span data-ttu-id="07f0c-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="07f0c-109">FilePath</span></span>| <span data-ttu-id="07f0c-110">Le chemin complet du fichier dans lequel gérer les lignes se trouve sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="07f0c-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="07f0c-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="07f0c-111">ContainsLine</span></span>| <span data-ttu-id="07f0c-112">Une ligne à vérifier se trouve dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="07f0c-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="07f0c-113">Cette ligne est ajoutée au fichier si elle ne s’y trouve pas.</span><span class="sxs-lookup"><span data-stu-id="07f0c-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="07f0c-114">**ContainsLine** est obligatoire, mais peut être défini sur une chaîne vide (`ContainsLine = ""`) s’il n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="07f0c-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span>|
| <span data-ttu-id="07f0c-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="07f0c-115">DoesNotContainPattern</span></span>| <span data-ttu-id="07f0c-116">Modèle d’expression régulière pour les lignes qui ne doivent pas se trouver dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="07f0c-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="07f0c-117">Les lignes du fichier qui correspondent à cette expression régulière seront supprimées du fichier.</span><span class="sxs-lookup"><span data-stu-id="07f0c-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="07f0c-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="07f0c-118">DependsOn</span></span> | <span data-ttu-id="07f0c-119">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="07f0c-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="07f0c-120">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="07f0c-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="07f0c-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="07f0c-121">Example</span></span>

<span data-ttu-id="07f0c-122">Cet exemple montre comment utiliser la ressource **nxFileLine** pour configurer le fichier `/etc/sudoers`, en s’assurant que l’utilisateur :monuser est configuré sur DoNotRequireTTY.</span><span class="sxs-lookup"><span data-stu-id="07f0c-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```