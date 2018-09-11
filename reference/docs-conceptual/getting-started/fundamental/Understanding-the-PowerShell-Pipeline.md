---
ms.date: 08/23/2018
keywords: powershell,applet de commande
title: Présentation des pipelines PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 3ee03f001668fb24ff9be1ea6ecb3817e319d0ee
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134158"
---
# <a name="understanding-pipelines"></a><span data-ttu-id="68bac-103">Présentation des pipelines</span><span class="sxs-lookup"><span data-stu-id="68bac-103">Understanding pipelines</span></span>

<span data-ttu-id="68bac-104">Les pipelines agissent comme une série de segments de canal connectés.</span><span class="sxs-lookup"><span data-stu-id="68bac-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="68bac-105">Les éléments se déplaçant dans pipeline passent par chaque segment.</span><span class="sxs-lookup"><span data-stu-id="68bac-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="68bac-106">Pour créer un pipeline dans PowerShell, vous interconnectez des commandes à l’aide de l’opérateur barre verticale « | » (pipe).</span><span class="sxs-lookup"><span data-stu-id="68bac-106">To create a pipeline in PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="68bac-107">La sortie de chaque commande est utilisée en tant qu’entrée pour la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="68bac-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="68bac-108">La notation utilisée pour les pipelines est similaire celle utilisée dans d’autres interpréteurs de commandes.</span><span class="sxs-lookup"><span data-stu-id="68bac-108">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="68bac-109">À première vue, les différences des pipelines dans PowerShell peuvent ne pas être évidentes.</span><span class="sxs-lookup"><span data-stu-id="68bac-109">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="68bac-110">Même si vous voyez du texte à l’écran, PowerShell canalise des objets, pas du texte, entre les commandes.</span><span class="sxs-lookup"><span data-stu-id="68bac-110">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

## <a name="the-powershell-pipeline"></a><span data-ttu-id="68bac-111">Le pipeline PowerShell</span><span class="sxs-lookup"><span data-stu-id="68bac-111">The PowerShell pipeline</span></span>

<span data-ttu-id="68bac-112">Les pipelines constituent indubitablement le concept plus important utilisé dans les interfaces de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="68bac-112">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="68bac-113">Lorsqu’ils sont utilisés correctement, les pipelines réduisent l’effort lié à l’utilisation de commandes complexes et facilitent la visualisation du flux de travail pour les commandes.</span><span class="sxs-lookup"><span data-stu-id="68bac-113">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work for the commands.</span></span> <span data-ttu-id="68bac-114">Chaque commande dans un pipeline (appelée élément de pipeline) transmet sa sortie à la commande suivante, élément par élément.</span><span class="sxs-lookup"><span data-stu-id="68bac-114">Each command in a pipeline (called a pipeline element) passes its output to the next command in the pipeline, item-by-item.</span></span> <span data-ttu-id="68bac-115">Les commandes n’ont pas à gérer plusieurs éléments à la fois.</span><span class="sxs-lookup"><span data-stu-id="68bac-115">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="68bac-116">Il en résulte une consommation réduite des ressources et la possibilité de commencer à recevoir la sortie immédiatement.</span><span class="sxs-lookup"><span data-stu-id="68bac-116">The result is reduced resource consumption and the ability to begin getting the output immediately.</span></span>

<span data-ttu-id="68bac-117">Par exemple, si vous utilisez la cmdlet `Out-Host` pour forcer un affichage page par page de la sortie d’une autre commande, la sortie ressemble exactement au texte normal affiché à l’écran, mais divisé en pages :</span><span class="sxs-lookup"><span data-stu-id="68bac-117">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="68bac-118">La pagination réduit également l’utilisation du processeur, car le traitement transfère à la cmdlet `Out-Host` lorsqu’il a une page complète prête à afficher.</span><span class="sxs-lookup"><span data-stu-id="68bac-118">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="68bac-119">L’exécution des cmdlets qui la précèdent dans le pipeline est interrompue jusqu’à ce que la page suivante de la sortie soit disponible.</span><span class="sxs-lookup"><span data-stu-id="68bac-119">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

<span data-ttu-id="68bac-120">Vous pouvez voir la différence dans le Gestionnaire des tâches de Windows pour surveiller l’utilisation du processeur et de la mémoire par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68bac-120">You can see the difference Windows Task Manager to monitor CPU and memory used by PowerShell.</span></span> <span data-ttu-id="68bac-121">Exécutez la commande suivante : `Get-ChildItem C:\\Windows -Recurse`.</span><span class="sxs-lookup"><span data-stu-id="68bac-121">Run the following command: `Get-ChildItem C:\\Windows -Recurse`.</span></span> <span data-ttu-id="68bac-122">Comparez l’utilisation du processeur et de la mémoire avec cette commande : `Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging`.</span><span class="sxs-lookup"><span data-stu-id="68bac-122">Compare the CPU and memory usage to this command: `Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging`.</span></span>

## <a name="objects-in-the-pipeline"></a><span data-ttu-id="68bac-123">Objets dans le pipeline</span><span class="sxs-lookup"><span data-stu-id="68bac-123">Objects in the pipeline</span></span>

<span data-ttu-id="68bac-124">Lorsque vous exécutez une cmdlet dans PowerShell, vous voyez une sortie texte, car il est de nécessaire de représenter les objets sous forme de texte dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="68bac-124">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="68bac-125">La sortie texte peut ne pas afficher toutes les propriétés de l’objet en cours de sortie.</span><span class="sxs-lookup"><span data-stu-id="68bac-125">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="68bac-126">Prenez, par exemple, la cmdlet `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="68bac-126">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="68bac-127">Si vous exécutez `Get-Location` alors que votre emplacement actuel est la racine du lecteur C, la sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="68bac-127">If you run `Get-Location` while your current location is the root of the C drive, you see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="68bac-128">La sortie texte est un résumé des informations, non une représentation complète de l’objet retourné par `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="68bac-128">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="68bac-129">Le titre dans la sortie est ajouté par le processus qui met en forme les données pour l’affichage à l’écran.</span><span class="sxs-lookup"><span data-stu-id="68bac-129">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

<span data-ttu-id="68bac-130">Lorsque vous dirigez la sortie vers la cmdlet `Get-Member`, vous obtenez des informations sur l’objet retourné par `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="68bac-130">When you pipe the output to the `Get-Member` cmdlet you get information about the object returned by `Get-Location`.</span></span>

```powershell
PS> Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="68bac-131">`Get-Location` retourne un objet **PathInfo** qui contient le chemin d’accès actuel et d’autres informations.</span><span class="sxs-lookup"><span data-stu-id="68bac-131">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>
