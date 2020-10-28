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
# <a name="viewing-object-structure-get-member"></a>Affichage de structure d’objet (Get-Member)

Étant donné que les objets jouent un rôle central dans Windows PowerShell, il existe plusieurs commandes natives conçues pour fonctionner avec des types d’objets arbitraires. La plus importante est l’applet de commande **Get-Member** .

La technique la plus simple pour analyser les objets qu’une commande retourne consiste à diriger sa sortie vers l’applet de commande **Get-Member** . L’applet de commande **Get-Member** affiche le nom formel du type d’objet et la liste complète de ses membres. Le nombre d’éléments retournés est parfois écrasant. Par exemple, un objet de processus peut avoir plus de 100 membres.

Pour afficher tous les membres d’un objet de processus et paginer la sortie afin de pouvoir les afficher tous, tapez ce qui suit :

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

La sortie de cette commande ressemble à ceci :

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

Vous pouvez rendre cette longue liste d’informations plus utilisable en filtrant les éléments que vous souhaitez voir. La commande **Get-Member** permet de répertorier uniquement les membres qui sont des propriétés. Il existe plusieurs formes de propriétés. Si vous définissez le paramètre **Get-MemberMemberType** sur la valeur **Properties** , l’applet de commande affiche tous les types de propriétés. La liste obtenue reste très longue, mais est un peu plus gérable :

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
> Les valeurs de MemberType autorisées AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet et All.

Plus de 60 propriétés sont applicables à un processus. La raison pour laquelle Windows PowerShell n’affiche souvent que quelques propriétés pour un objet bien connu est que les afficher toutes produirait une quantité ingérable d’informations.

> [!NOTE]
> Windows PowerShell détermine le mode d’affichage d’un type d’objet à l’aide des informations stockées dans des fichiers XML dont le nom se termine par .format.ps1xml. La mise en forme des données pour des objets de processus, qui sont des objets .NET System.Diagnostics.Process, est stockée dans DotNetTypes.format.ps1xml.

Si vous avez besoin d’examiner les propriétés autres que celles que Windows PowerShell affiche par défaut, vous devez mettre en forme vous-même les données de sortie. Cela est possible à l’aide des applets de commande Format.
