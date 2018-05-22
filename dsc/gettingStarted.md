---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Prise en main de la configuration de l’état souhaité (DSC) Windows PowerShell
ms.openlocfilehash: a449382c979e680ea311c887c86cb675ba6162b7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a><span data-ttu-id="1c598-103">Prise en main de la configuration de l’état souhaité (DSC) Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c598-103">Getting Started with PowerShell Desired State Configuration</span></span> #

<span data-ttu-id="1c598-104">Ce guide explique comment créer des documents de configuration d’état souhaité PowerShell et comment les appliquer aux ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="1c598-104">This guide describes how to begin creating PowerShell Desired State Configuration documents and apply them to machines.</span></span> <span data-ttu-id="1c598-105">Il suppose une connaissance de base des applets de commande PowerShell, des modules et des fonctions.</span><span class="sxs-lookup"><span data-stu-id="1c598-105">It assumes basic familiarity with PowerShell cmdlets, modules, and functions.</span></span>


## <a name="create-a-configuration"></a><span data-ttu-id="1c598-106">Créer une configuration</span><span class="sxs-lookup"><span data-stu-id="1c598-106">Create a Configuration</span></span> ##

<span data-ttu-id="1c598-107">Les [**configurations**](https://msdn.microsoft.com/powershell/dsc/configurations) sont des documents qui décrivent un environnement.</span><span class="sxs-lookup"><span data-stu-id="1c598-107">[**Configurations**](https://msdn.microsoft.com/powershell/dsc/configurations) are documents that describe an environment.</span></span> <span data-ttu-id="1c598-108">Les environnements sont constitués de **nœuds** qui sont généralement des machines physiques ou virtuelles.</span><span class="sxs-lookup"><span data-stu-id="1c598-108">Environments consist of "**nodes**", which are commonly virtual or physical machines.</span></span>

<span data-ttu-id="1c598-109">Les configurations peuvent se présenter sous différentes formes.</span><span class="sxs-lookup"><span data-stu-id="1c598-109">Configurations can come in a variety of forms.</span></span> <span data-ttu-id="1c598-110">Le moyen le plus simple de créer une nouvelle configuration consiste à créer un fichier .ps1 (script PowerShell).</span><span class="sxs-lookup"><span data-stu-id="1c598-110">The easiest way to create a new configuration is to create a .ps1 (PowerShell script) file.</span></span> <span data-ttu-id="1c598-111">Pour ce faire, ouvrez l’éditeur de votre choix.</span><span class="sxs-lookup"><span data-stu-id="1c598-111">To do this, open your editor of choice.</span></span> <span data-ttu-id="1c598-112">PowerShell ISE constitue un bon choix, car il comprend DSC de manière native.</span><span class="sxs-lookup"><span data-stu-id="1c598-112">The PowerShell ISE is a good choice, since it understands DSC natively.</span></span> <span data-ttu-id="1c598-113">Enregistrez ce qui suit dans un fichier PS1 :</span><span class="sxs-lookup"><span data-stu-id="1c598-113">Save the following as a PS1:</span></span>

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }

    }

}
```
## <a name="parts-of-a-configuration"></a><span data-ttu-id="1c598-114">Composants d’une configuration</span><span class="sxs-lookup"><span data-stu-id="1c598-114">Parts of a Configuration</span></span> ##
<span data-ttu-id="1c598-115">**Configuration** est un mot clé qui date de PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="1c598-115">**Configuration** is a keyword that has been added to PowerShell 4.0.</span></span> <span data-ttu-id="1c598-116">Il désigne un type spécial de fonction PowerShell utilisée par DSC.</span><span class="sxs-lookup"><span data-stu-id="1c598-116">It signifies a special kind of PowerShell function used by Desired State Configuration.</span></span> <span data-ttu-id="1c598-117">Dans cet exemple, la fonction se nomme myFirstConfiguration.</span><span class="sxs-lookup"><span data-stu-id="1c598-117">In this example, the function is named myFirstConfiguration.</span></span>

<span data-ttu-id="1c598-118">La ligne suivante est une instruction d’importation, similaire à l’importation d’un module.</span><span class="sxs-lookup"><span data-stu-id="1c598-118">The next line is an import statement, similar to importing a module.</span></span> <span data-ttu-id="1c598-119">Nous l’aborderons plus tard.</span><span class="sxs-lookup"><span data-stu-id="1c598-119">It will be discussed later on.</span></span>

<span data-ttu-id="1c598-120">Node définit le nom de l’ordinateur auquel est appliquée la configuration.</span><span class="sxs-lookup"><span data-stu-id="1c598-120">"Node" defines the machine name this configuration will act on.</span></span> <span data-ttu-id="1c598-121">Même si elles sont modifiées localement, les configurations peuvent atteindre les nœuds distants et les configurer.</span><span class="sxs-lookup"><span data-stu-id="1c598-121">Although this configuration is edited locally, configurations can reach out to remote nodes and configure them.</span></span>

<span data-ttu-id="1c598-122">Les nœuds peuvent être des noms d’ordinateurs ou des adresses IP.</span><span class="sxs-lookup"><span data-stu-id="1c598-122">Nodes can be machine names or IP addresses.</span></span> <span data-ttu-id="1c598-123">Vous pouvez avoir plusieurs nœuds dans un même document de configuration.</span><span class="sxs-lookup"><span data-stu-id="1c598-123">You can have multiple nodes in a single configuration document.</span></span> <span data-ttu-id="1c598-124">À l’aide de [données de configuration](https://msdn.microsoft.com/powershell/dsc/configdata), vous pouvez également appliquer une même configuration à plusieurs nœuds.</span><span class="sxs-lookup"><span data-stu-id="1c598-124">Using [configuration data](https://msdn.microsoft.com/powershell/dsc/configdata), you can also have the same configuration apply to multiple nodes.</span></span> <span data-ttu-id="1c598-125">Ici, le nœud s’appelle « localhost », ce qui correspond à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1c598-125">In this case, the node is "localhost" - which means the local computer.</span></span>

<span data-ttu-id="1c598-126">L’élément suivant est une [**ressource**](https://msdn.microsoft.com/powershell/dsc/resources).</span><span class="sxs-lookup"><span data-stu-id="1c598-126">The next item is a [**resource**](https://msdn.microsoft.com/powershell/dsc/resources).</span></span> <span data-ttu-id="1c598-127">Les ressources sont les blocs de construction des configurations.</span><span class="sxs-lookup"><span data-stu-id="1c598-127">Resources are building blocks of configurations.</span></span> <span data-ttu-id="1c598-128">Chaque ressource est un module qui définit la logique d’implémentation d’un aspect d’un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1c598-128">Each resource is a module that defines the implementation logic of a single aspect of a machine.</span></span> <span data-ttu-id="1c598-129">Vous pouvez afficher toutes les ressources de votre ordinateur en exécutant **Get-DscResource** dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c598-129">You can view every resource on your machine by running **Get-DscResource** in PowerShell.</span></span> <span data-ttu-id="1c598-130">Les ressources doivent être présentes sur l’ordinateur local et importées avant de pouvoir être utilisées dans une configuration avec **Import-DscResource**, qui se trouve sur la deuxième ligne de cette configuration.</span><span class="sxs-lookup"><span data-stu-id="1c598-130">Resources must be present on the local machine and imported before they can be used in a configuration with **Import-DscResource** which is on the second line of this configuration.</span></span>

<span data-ttu-id="1c598-131">**Promulgation d’une configuration**</span><span class="sxs-lookup"><span data-stu-id="1c598-131">**Enacting a Configuration**</span></span>

<span data-ttu-id="1c598-132">Si le script ci-dessus est enregistré et exécuté, vous n’obtiendrez aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="1c598-132">If the script above is saved and run, no output will be produced.</span></span> <span data-ttu-id="1c598-133">En effet, une configuration est une fonction, et le script ci-dessus a défini la fonction, mais ne l’a pas encore exécutée.</span><span class="sxs-lookup"><span data-stu-id="1c598-133">This is because a configuration is just a function, and the script above has defined the function but not yet run it.</span></span> <span data-ttu-id="1c598-134">Une fois la fonction définie, elle doit être appelée :</span><span class="sxs-lookup"><span data-stu-id="1c598-134">After the function is defined, it must be invoked:</span></span>
```powershell
myFirstConfiguration
```

<span data-ttu-id="1c598-135">Quand elles sont exécutées, les fonctions de configuration confirment que la configuration est valide.</span><span class="sxs-lookup"><span data-stu-id="1c598-135">When executed, configuration functions validate the configuration is valid.</span></span> <span data-ttu-id="1c598-136">Elle ne doit comporter aucune erreur de syntaxe. Les paramètres obligatoires des ressources doivent être définis et toutes les ressources doivent être importées avant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="1c598-136">It should have no syntax errors, resources should have all mandatory parameters defined, and all resources should be imported before execution.</span></span>

<span data-ttu-id="1c598-137">Une fois la configuration exécutée, un dossier portant le nom de la configuration est créé. Il contient un **fichier .MOF** pour chaque nœud de la configuration.</span><span class="sxs-lookup"><span data-stu-id="1c598-137">Once the configuration is executed, it creates a folder with the name of the configuration containing a **.MOF file** for every node in the configuration.</span></span> <span data-ttu-id="1c598-138">Le format .MOF est un format de gestion basé sur des normes qui est utilisé par DSC PowerShell pour communiquer sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="1c598-138">The .MOF file is a standards-based management format which is used by PowerShell DSC to communicate over the network.</span></span>

<span data-ttu-id="1c598-139">Pour promulguer la configuration :</span><span class="sxs-lookup"><span data-stu-id="1c598-139">To enact the configuration:</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
<span data-ttu-id="1c598-140">Cela crée une tâche PowerShell qui contacte les nœuds de la configuration et les configure.</span><span class="sxs-lookup"><span data-stu-id="1c598-140">This creates a PowerShell job that reaches out to the nodes in the configuration and configures them.</span></span> <span data-ttu-id="1c598-141">Pour afficher la sortie de la tâche, utilisez -Wait.</span><span class="sxs-lookup"><span data-stu-id="1c598-141">To see the output of the job, use -Wait.</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```