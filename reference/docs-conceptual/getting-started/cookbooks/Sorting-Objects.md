---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Tri d’objets
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 272d550a67b206f9924ebe143eca2f5906c0a304
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30949976"
---
# <a name="sorting-objects"></a>Tri d’objets

Vous pouvez organiser des données affichées pour faciliter leur analyse en utilisant l’applet de commande **Sort-Object**. L’applet de commande **Sort-Object** prend le nom d’une ou plusieurs propriétés pour trier et retourner les données triées sur les valeurs de ces propriétés.

Prenez le problème de l’affichage de la liste d’instances Win32_SystemDriver. Si vous souhaitez trier sur l’état (**State**), puis sur le nom (**Name**), vous pouvez taper ce qui suit :

```powershell
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

Bien que l’affichage soit long, les éléments sont regroupés par état :

```output
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

Vous pouvez également trier les objets dans l’ordre inverse en spécifiant le paramètre **Descending**. Cela a pour effet d’inverser l’ordre de tri, de sorte que les noms sont triés dans l’ordre alphabétique inverse et les nombres dans l’ordre décroissant de leur valeur.

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```