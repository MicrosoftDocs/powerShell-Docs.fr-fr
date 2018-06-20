---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource nxFileLine dans DSC pour Linux
ms.openlocfilehash: 6b927839c23478aa9916a5d23836b31fccc58484
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219631"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="0008f-103">Ressource nxFileLine dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="0008f-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="0008f-104">La ressource **nxFileLine** dans DSC PowerShell fournit un mécanisme permettant de gérer des lignes au sein d’un fichier de configuration sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="0008f-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0008f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0008f-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="0008f-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0008f-106">Properties</span></span>

|  <span data-ttu-id="0008f-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="0008f-107">Property</span></span> |  <span data-ttu-id="0008f-108">Description</span><span class="sxs-lookup"><span data-stu-id="0008f-108">Description</span></span> |
|---|---|
| <span data-ttu-id="0008f-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="0008f-109">FilePath</span></span>| <span data-ttu-id="0008f-110">Le chemin complet du fichier dans lequel gérer les lignes se trouve sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="0008f-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="0008f-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="0008f-111">ContainsLine</span></span>| <span data-ttu-id="0008f-112">Une ligne à vérifier se trouve dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="0008f-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="0008f-113">Cette ligne est ajoutée au fichier si elle ne s’y trouve pas.</span><span class="sxs-lookup"><span data-stu-id="0008f-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="0008f-114">**ContainsLine** est obligatoire, mais peut être défini sur une chaîne vide (\`ContainsLine = ‘’\`\`) s’il n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0008f-114">**ContainsLine** is mandatory, but can be set to an empty string (\`ContainsLine = ‘’\`\`) if it is not needed.</span></span>|
| <span data-ttu-id="0008f-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="0008f-115">DoesNotContainPattern</span></span>| <span data-ttu-id="0008f-116">Modèle d’expression régulière pour les lignes qui ne doivent pas se trouver dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="0008f-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="0008f-117">Les lignes du fichier qui correspondent à cette expression régulière seront supprimées du fichier.</span><span class="sxs-lookup"><span data-stu-id="0008f-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="0008f-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0008f-118">DependsOn</span></span> | <span data-ttu-id="0008f-119">Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="0008f-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0008f-120">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0008f-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="0008f-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="0008f-121">Example</span></span>

<span data-ttu-id="0008f-122">Cet exemple montre comment utiliser la ressource **nxFileLine** pour configurer le fichier `/etc/sudoers`, en s’assurant que l’utilisateur :monuser est configuré sur DoNotRequireTTY.</span><span class="sxs-lookup"><span data-stu-id="0008f-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```
Import-DSCResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```