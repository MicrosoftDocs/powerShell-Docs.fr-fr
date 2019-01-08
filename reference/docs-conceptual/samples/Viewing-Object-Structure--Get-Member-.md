---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Affichage de structure d’objet Get Member
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401911"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="381f6-103">Affichage de structure d’objet (Get-Member)</span><span class="sxs-lookup"><span data-stu-id="381f6-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="381f6-104">Étant donné que les objets jouent un rôle central dans Windows PowerShell, il existe plusieurs commandes natives conçues pour fonctionner avec des types d’objets arbitraires.</span><span class="sxs-lookup"><span data-stu-id="381f6-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="381f6-105">La plus importante est l’applet de commande **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="381f6-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="381f6-106">La technique la plus simple pour analyser les objets qu’une commande retourne consiste à diriger sa sortie vers l’applet de commande **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="381f6-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="381f6-107">L’applet de commande **Get-Member** affiche le nom formel du type d’objet et la liste complète de ses membres.</span><span class="sxs-lookup"><span data-stu-id="381f6-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="381f6-108">Le nombre d’éléments retournés est parfois écrasant.</span><span class="sxs-lookup"><span data-stu-id="381f6-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="381f6-109">Par exemple, un objet de processus peut avoir plus de 100 membres.</span><span class="sxs-lookup"><span data-stu-id="381f6-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="381f6-110">Pour afficher tous les membres d’un objet de processus et paginer la sortie afin de pouvoir les afficher tous, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="381f6-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="381f6-111">La sortie de cette commande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="381f6-111">The output from this command will look something like this:</span></span>

```output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

<span data-ttu-id="381f6-112">Vous pouvez rendre cette longue liste d’informations plus utilisable en filtrant les éléments que vous souhaitez voir.</span><span class="sxs-lookup"><span data-stu-id="381f6-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="381f6-113">La commande **Get-Member** permet de répertorier uniquement les membres qui sont des propriétés.</span><span class="sxs-lookup"><span data-stu-id="381f6-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="381f6-114">Il existe plusieurs formes de propriétés.</span><span class="sxs-lookup"><span data-stu-id="381f6-114">There are several forms of properties.</span></span> <span data-ttu-id="381f6-115">Si vous définissez le paramètre **Get-MemberMemberType** sur la valeur **Properties**, l’applet de commande affiche tous les types de propriétés.</span><span class="sxs-lookup"><span data-stu-id="381f6-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="381f6-116">La liste obtenue reste très longue, mais est un peu plus gérable :</span><span class="sxs-lookup"><span data-stu-id="381f6-116">The resulting list is still very long, but a bit more manageable:</span></span>

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> <span data-ttu-id="381f6-117">Les valeurs de MemberType autorisées AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet et All.</span><span class="sxs-lookup"><span data-stu-id="381f6-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="381f6-118">Plus de 60 propriétés sont applicables à un processus.</span><span class="sxs-lookup"><span data-stu-id="381f6-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="381f6-119">La raison pour laquelle Windows PowerShell n’affiche souvent que quelques propriétés pour un objet bien connu est que les afficher toutes produirait une quantité ingérable d’informations.</span><span class="sxs-lookup"><span data-stu-id="381f6-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="381f6-120">Windows PowerShell détermine le mode d’affichage d’un type d’objet à l’aide des informations stockées dans des fichiers XML dont le nom se termine par .format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="381f6-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="381f6-121">La mise en forme des données pour des objets de processus, qui sont des objets .NET System.Diagnostics.Process, est stockée dans DotNetTypes.format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="381f6-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="381f6-122">Si vous avez besoin d’examiner les propriétés autres que celles que Windows PowerShell affiche par défaut, vous devez mettre en forme vous-même les données de sortie.</span><span class="sxs-lookup"><span data-stu-id="381f6-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="381f6-123">Cela est possible à l’aide des applets de commande Format.</span><span class="sxs-lookup"><span data-stu-id="381f6-123">This can be done by using the format cmdlets.</span></span>