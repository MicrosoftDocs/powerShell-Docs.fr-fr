---
ms.date: 08/27/2018
keywords: powershell,applet de commande
title: Scripts PowerShell
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "62058486"
---
# <a name="powershell"></a><span data-ttu-id="66718-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="66718-103">PowerShell</span></span>

<span data-ttu-id="66718-104">PowerShell est un interpréteur de ligne de commande et langage de script qui repose sur la technologie.NET.</span><span class="sxs-lookup"><span data-stu-id="66718-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="66718-105">PowerShell permet aux administrateurs système et aux utilisateurs avancés d’automatiser rapidement les tâches qui administrent les systèmes d’exploitation (Linux, macOS et Windows) et les processus.</span><span class="sxs-lookup"><span data-stu-id="66718-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="66718-106">Les commandes PowerShell vous permettent de gérer les ordinateurs à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="66718-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="66718-107">Les fournisseurs PowerShell vous permettent d’accéder à des magasins de données, par exemple le Registre et le magasin de certificats, aussi facilement que si vous accédiez au système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="66718-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="66718-108">PowerShell inclut un analyseur d’expression avancé et un langage de script entièrement développé.</span><span class="sxs-lookup"><span data-stu-id="66718-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="66718-109">PowerShell est open source</span><span class="sxs-lookup"><span data-stu-id="66718-109">PowerShell is open-source</span></span>

<span data-ttu-id="66718-110">Le code source de base de PowerShell est maintenant disponible dans GitHub et ouvert aux contributions de la communauté.</span><span class="sxs-lookup"><span data-stu-id="66718-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="66718-111">Consultez [Source PowerShell sur GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="66718-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="66718-112">Vous pouvez commencer par les éléments nécessaires sur [Obtenir PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="66718-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="66718-113">Vous pouvez aussi peut-être parcourir rapidement [Prise en main](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span><span class="sxs-lookup"><span data-stu-id="66718-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="66718-114">Objectifs de conception de PowerShell</span><span class="sxs-lookup"><span data-stu-id="66718-114">PowerShell design goals</span></span>

<span data-ttu-id="66718-115">PowerShell est conçu pour améliorer l’environnement de script et de ligne de commande en éliminant des problèmes connus de longue date et en ajoutant de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="66718-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="66718-116">Détectabilité</span><span class="sxs-lookup"><span data-stu-id="66718-116">Discoverability</span></span>

<span data-ttu-id="66718-117">PowerShell facilite la découverte de ses fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="66718-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="66718-118">Par exemple, pour obtenir la liste des applets de commande qui permettent d’afficher et de modifier les services Windows, tapez :</span><span class="sxs-lookup"><span data-stu-id="66718-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="66718-119">Après avoir découvert l’applet de commande qui effectue une tâche, vous pouvez en apprendre davantage sur l’applet de commande à l’aide de l’applet de commande `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="66718-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="66718-120">Par exemple, pour afficher l’aide concernant l’applet de commande `Get-Service`, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="66718-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="66718-121">La plupart des cmdlets retournent des objets qui peuvent être manipulés puis rendus sous forme texte pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="66718-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="66718-122">Pour bien comprendre la sortie de cette cmdlet, canalisez la sortie vers la cmdlet `Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="66718-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="66718-123">Par exemple, la commande suivante affiche des informations sur les membres de l’objet retourné par l’applet de commande `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="66718-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="66718-124">Cohérence</span><span class="sxs-lookup"><span data-stu-id="66718-124">Consistency</span></span>

<span data-ttu-id="66718-125">L’administration de systèmes peut être une tâche complexe.</span><span class="sxs-lookup"><span data-stu-id="66718-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="66718-126">Les outils dont l’interface est cohérente facilitent le contrôle de la complexité intrinsèque.</span><span class="sxs-lookup"><span data-stu-id="66718-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="66718-127">Malheureusement, les outils en ligne de commande et les objets COM (Component Object Model) scriptables ne sont pas réputés pour leur cohérence.</span><span class="sxs-lookup"><span data-stu-id="66718-127">Unfortunately, command-line tools and scriptable Component Object Model (COM) objects aren't known for their consistency.</span></span>

<span data-ttu-id="66718-128">La cohérence de PowerShell est l’un de ses principaux atouts.</span><span class="sxs-lookup"><span data-stu-id="66718-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="66718-129">Par exemple, si vous apprenez à utiliser l’applet de commande `Sort-Object`, vous pouvez utiliser cette connaissance pour trier la sortie de toute applet de commande.</span><span class="sxs-lookup"><span data-stu-id="66718-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="66718-130">Vous n’avez pas à apprendre les différentes routines de tri de chaque cmdlet.</span><span class="sxs-lookup"><span data-stu-id="66718-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="66718-131">En outre, les développeurs de cmdlets n’ont pas à concevoir de fonctionnalités de tri pour leurs cmdlets.</span><span class="sxs-lookup"><span data-stu-id="66718-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="66718-132">PowerShell fournit une infrastructure avec les fonctionnalités de base qui forcent la cohérence.</span><span class="sxs-lookup"><span data-stu-id="66718-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="66718-133">L’infrastructure élimine certains choix qui sont laissés au développeur.</span><span class="sxs-lookup"><span data-stu-id="66718-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="66718-134">Toutefois, en retour, le développement des cmdlets est beaucoup plus simple.</span><span class="sxs-lookup"><span data-stu-id="66718-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="66718-135">Environnements interactifs et de scripts</span><span class="sxs-lookup"><span data-stu-id="66718-135">Interactive and scripting environments</span></span>

<span data-ttu-id="66718-136">L’invite de commandes Windows fournit un interpréteur de commandes interactif avec accès aux outils de ligne de commande et aux scripts de base.</span><span class="sxs-lookup"><span data-stu-id="66718-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="66718-137">Windows Script Host (WSH) inclut des outils de ligne de commande contenant des scripts et des objets d’automatisation COM, mais ne fournit pas d’interpréteur de commandes interactif.</span><span class="sxs-lookup"><span data-stu-id="66718-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="66718-138">PowerShell combine un interpréteur de commandes interactif et un environnement de script.</span><span class="sxs-lookup"><span data-stu-id="66718-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="66718-139">PowerShell peut accéder aux outils de ligne de commande, aux objets COM et aux bibliothèques de classes .NET.</span><span class="sxs-lookup"><span data-stu-id="66718-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="66718-140">Cette combinaison de fonctionnalités étend les capacités de l’utilisateur interactif, du writer de script et de l’administrateur système.</span><span class="sxs-lookup"><span data-stu-id="66718-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="66718-141">Orientation objet</span><span class="sxs-lookup"><span data-stu-id="66718-141">Object orientation</span></span>

<span data-ttu-id="66718-142">PowerShell est basé sur l’objet, pas le texte.</span><span class="sxs-lookup"><span data-stu-id="66718-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="66718-143">La sortie d’une commande est un objet.</span><span class="sxs-lookup"><span data-stu-id="66718-143">The output of a command is an object.</span></span> <span data-ttu-id="66718-144">Vous pouvez envoyer l’objet de sortie, via le pipeline, à une autre commande en tant qu’entrée.</span><span class="sxs-lookup"><span data-stu-id="66718-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="66718-145">Ce pipeline fournit une interface familière aux utilisateurs familiarisés avec d’autres interpréteurs de commandes.</span><span class="sxs-lookup"><span data-stu-id="66718-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="66718-146">PowerShell étend ce concept en envoyant des objets plutôt que du texte.</span><span class="sxs-lookup"><span data-stu-id="66718-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="66718-147">Transition aisée vers les scripts</span><span class="sxs-lookup"><span data-stu-id="66718-147">Easy transition to scripting</span></span>

<span data-ttu-id="66718-148">La détectabilité de commande de PowerShell facilite la transition de la saisie de commandes de façon interactive vers la création et l’exécution de scripts.</span><span class="sxs-lookup"><span data-stu-id="66718-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="66718-149">L’historique et les transcriptions de PowerShell facilitent la copie de commandes dans un fichier pour une utilisation en tant que script.</span><span class="sxs-lookup"><span data-stu-id="66718-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
