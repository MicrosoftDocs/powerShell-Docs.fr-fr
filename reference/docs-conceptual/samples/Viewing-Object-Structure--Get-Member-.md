---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Affichage de structure d’objet Get Member
description: Get-Member est un outil puissant qui permet de voir le type et la structure des objets dans PowerShell.
ms.openlocfilehash: 3c294fe47294e2cf8daf125aac55661dd38cf9bb
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501216"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="a2e44-104">Affichage de structure d’objet (Get-Member)</span><span class="sxs-lookup"><span data-stu-id="a2e44-104">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="a2e44-105">Étant donné que les objets jouent un rôle central dans Windows PowerShell, il existe plusieurs commandes natives conçues pour fonctionner avec des types d’objets arbitraires.</span><span class="sxs-lookup"><span data-stu-id="a2e44-105">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="a2e44-106">La plus importante est l’applet de commande **Get-Member** .</span><span class="sxs-lookup"><span data-stu-id="a2e44-106">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="a2e44-107">La technique la plus simple pour analyser les objets qu’une commande retourne consiste à diriger sa sortie vers l’applet de commande **Get-Member** .</span><span class="sxs-lookup"><span data-stu-id="a2e44-107">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="a2e44-108">L’applet de commande **Get-Member** affiche le nom formel du type d’objet et la liste complète de ses membres.</span><span class="sxs-lookup"><span data-stu-id="a2e44-108">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="a2e44-109">Le nombre d’éléments retournés est parfois écrasant.</span><span class="sxs-lookup"><span data-stu-id="a2e44-109">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="a2e44-110">Par exemple, un objet de processus peut avoir plus de 100 membres.</span><span class="sxs-lookup"><span data-stu-id="a2e44-110">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="a2e44-111">Pour afficher tous les membres d’un objet de processus et paginer la sortie afin de pouvoir les afficher tous, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="a2e44-111">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="a2e44-112">La sortie de cette commande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="a2e44-112">The output from this command will look something like this:</span></span>

```Output
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

<span data-ttu-id="a2e44-113">Vous pouvez rendre cette longue liste d’informations plus utilisable en filtrant les éléments que vous souhaitez voir.</span><span class="sxs-lookup"><span data-stu-id="a2e44-113">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="a2e44-114">La commande **Get-Member** permet de répertorier uniquement les membres qui sont des propriétés.</span><span class="sxs-lookup"><span data-stu-id="a2e44-114">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="a2e44-115">Il existe plusieurs formes de propriétés.</span><span class="sxs-lookup"><span data-stu-id="a2e44-115">There are several forms of properties.</span></span> <span data-ttu-id="a2e44-116">Si vous définissez le paramètre **Get-MemberMemberType** sur la valeur **Properties** , l’applet de commande affiche tous les types de propriétés.</span><span class="sxs-lookup"><span data-stu-id="a2e44-116">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties** .</span></span> <span data-ttu-id="a2e44-117">La liste obtenue reste très longue, mais est un peu plus gérable :</span><span class="sxs-lookup"><span data-stu-id="a2e44-117">The resulting list is still very long, but a bit more manageable:</span></span>

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
> <span data-ttu-id="a2e44-118">Les valeurs de MemberType autorisées AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet et All.</span><span class="sxs-lookup"><span data-stu-id="a2e44-118">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="a2e44-119">Plus de 60 propriétés sont applicables à un processus.</span><span class="sxs-lookup"><span data-stu-id="a2e44-119">There are over 60 properties for a process.</span></span> <span data-ttu-id="a2e44-120">La raison pour laquelle Windows PowerShell n’affiche souvent que quelques propriétés pour un objet bien connu est que les afficher toutes produirait une quantité ingérable d’informations.</span><span class="sxs-lookup"><span data-stu-id="a2e44-120">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="a2e44-121">Windows PowerShell détermine le mode d’affichage d’un type d’objet à l’aide des informations stockées dans des fichiers XML dont le nom se termine par .format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="a2e44-121">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="a2e44-122">La mise en forme des données pour des objets de processus, qui sont des objets .NET System.Diagnostics.Process, est stockée dans DotNetTypes.format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="a2e44-122">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="a2e44-123">Si vous avez besoin d’examiner les propriétés autres que celles que Windows PowerShell affiche par défaut, vous devez mettre en forme vous-même les données de sortie.</span><span class="sxs-lookup"><span data-stu-id="a2e44-123">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="a2e44-124">Cela est possible à l’aide des applets de commande Format.</span><span class="sxs-lookup"><span data-stu-id="a2e44-124">This can be done by using the format cmdlets.</span></span>
