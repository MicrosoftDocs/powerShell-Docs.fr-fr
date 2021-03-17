---
description: Décrit comment accéder aux éléments à partir de l’emplacement de travail dans PowerShell.
Locale: en-US
ms.date: 03/15/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_locations?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Locations
ms.openlocfilehash: 312e5d8a80ade150cd9352908c0118174b519725
ms.sourcegitcommit: 15f759ca68d17acecab46b52250298d4f2037c4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103575557"
---
# <a name="about_locations"></a>about_Locations

## <a name="short-description"></a>Description courte
Décrit comment accéder aux éléments à partir de l’emplacement de travail dans PowerShell.

## <a name="long-description"></a>Description longue

L’emplacement de travail actuel est l’emplacement par défaut dans lequel les commandes pointent.
En d’autres termes, il s’agit de l’emplacement que PowerShell utilise si vous ne fournissez pas de chemin d’accès explicite à l’élément ou à l’emplacement affecté par la commande.

> [!NOTE]
> PowerShell prend en charge plusieurs instances d’exécution par processus. Chaque instance d’exécution a son propre _répertoire actif_. Ce n’est pas le même que le répertoire actif du processus : `[System.Environment]::CurrentDirectory` .

Dans la plupart des cas, l’emplacement de travail actuel est un lecteur accessible via le fournisseur FileSystem PowerShell et, dans certains cas, un répertoire sur ce lecteur.
Par exemple, vous pouvez définir l’emplacement de travail actuel à l’emplacement suivant :

```powershell
C:\Program Files\Windows PowerShell
```

Par conséquent, toutes les commandes sont traitées à partir de cet emplacement, sauf si un autre chemin d’accès est explicitement fourni.

PowerShell conserve l’emplacement de travail actuel de chaque lecteur, même si le lecteur n’est pas le lecteur actif. Cela vous permet d’accéder aux éléments à partir de l’emplacement de travail actuel en faisant référence uniquement au lecteur d’un autre emplacement.
Supposons, par exemple, que votre emplacement de travail actuel soit `C:\Windows` . Supposons à présent que vous utilisez la commande suivante pour modifier l’emplacement de travail actuel sur le lecteur HKLM :

```powershell
Set-Location HKLM:
```

Bien que votre emplacement actuel soit maintenant le lecteur de Registre, vous pouvez toujours accéder aux éléments de l' `C:\Windows` annuaire en utilisant simplement le lecteur C :, comme indiqué dans l’exemple suivant :

```powershell
Get-ChildItem C:
```

PowerShell se souvient que votre emplacement de travail actuel pour ce lecteur est le répertoire Windows. il récupère donc les éléments de ce répertoire. Les résultats seraient les mêmes si vous avez exécuté la commande suivante :

```powershell
Get-ChildItem C:\Windows
```

Dans PowerShell, vous pouvez utiliser la commande Get-Location pour déterminer l’emplacement de travail actuel, et vous pouvez utiliser la commande Set-Location pour définir l’emplacement de travail actuel. Par exemple, la commande suivante définit l’emplacement de travail actuel sur le répertoire Windows du lecteur C ::

```powershell
Set-Location c:\windows
```

Une fois que vous avez défini l’emplacement de travail actuel, vous pouvez toujours accéder aux éléments à partir d’autres lecteurs en incluant simplement le nom du lecteur (suivi d’un signe deux-points) dans la commande, comme illustré dans l’exemple suivant :

```powershell
Get-ChildItem HKLM:\software
```

L’exemple de commande récupère une liste d’éléments dans le conteneur logiciel de la ruche HKEY local machine dans le registre.

PowerShell vous permet également d’utiliser des caractères spéciaux pour représenter l’emplacement de travail actuel et son emplacement parent. Pour représenter l’emplacement de travail actuel, utilisez un seul point. Pour représenter le parent de l’emplacement de travail actuel, utilisez deux points. Par exemple, le code suivant spécifie le sous-répertoire système à l’emplacement de travail actuel :

```powershell
Get-ChildItem .\system
```

Si l’emplacement de travail actuel est `C:\Windows` , cette commande retourne une liste de tous les éléments dans `C:\Windows\System` . Toutefois, si vous utilisez deux périodes, le répertoire parent du répertoire de travail actuel est utilisé, comme illustré dans l’exemple suivant :

```powershell
Get-ChildItem ..\"program files"
```

Dans ce cas, PowerShell traite les deux points comme le lecteur C :, de sorte que la commande récupère tous les éléments de l' `C:\Program Files` Annuaire.

Un chemin d’accès commençant par une barre oblique identifie un chemin d’accès à la racine du lecteur actif. Par exemple, si votre emplacement de travail actuel est `C:\Program Files\PowerShell` , la racine de votre lecteur est C. Par conséquent, la commande suivante répertorie tous les éléments du `C:\Windows` répertoire :

```powershell
Get-ChildItem \windows
```

Si vous ne spécifiez pas de chemin d’accès commençant par un nom de lecteur, une barre oblique ou une période lorsque vous fournissez le nom d’un conteneur ou d’un élément, le conteneur ou l’élément est supposé être situé à l’emplacement de travail actuel. Par exemple, si votre emplacement de travail actuel est `C:\Windows` , la commande suivante renvoie tous les éléments du `C:\Windows\System` répertoire :

```powershell
Get-ChildItem system
```

Si vous spécifiez un nom de fichier plutôt qu’un nom de répertoire, PowerShell retourne des détails sur ce fichier (en supposant que ce fichier se trouve à l’emplacement de travail actuel).

## <a name="see-also"></a>Voir aussi

[Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)

[about_Providers](about_Providers.md)

[about_Path_Syntax](about_Path_Syntax.md)
