---
description: Fournit des informations essentielles sur les objets dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_objects?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Objects
ms.openlocfilehash: b845dc8b55a19bb642c194398b0c9f5f13d24cb3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208118"
---
# <a name="about-objects"></a>À propos des objets

## <a name="short-description"></a>Description courte
Fournit des informations essentielles sur les objets dans PowerShell.

## <a name="long-description"></a>Description longue

Toutes les actions que vous effectuez dans PowerShell se produisent dans le contexte d’objets. À mesure que les données se déplacent d’une commande à l’autre, elles se déplacent sous la forme d’un ou plusieurs objets identifiables. Un objet est une collection de données qui représente un élément. Un objet est constitué de trois types de données : le type d’objets, ses méthodes et ses propriétés.

## <a name="types-methods-and-properties"></a>Types, méthodes et propriétés

Le type d’objet indique le type d’objet dont il s’agit. Par exemple, un objet qui représente un fichier est un objet FileInfo.

Les méthodes d’objet sont des actions que vous pouvez effectuer sur l’objet.
Par exemple, les objets FileInfo ont une méthode CopyTo que vous pouvez utiliser pour copier le fichier.

Les propriétés d’objet stockent des informations sur l’objet. Par exemple, les objets FileInfo ont une propriété LastWriteTime qui stocke la date et l’heure auxquelles le fichier a été accédé le plus récemment.

Lorsque vous travaillez avec des objets, vous pouvez utiliser leurs méthodes et propriétés dans les commandes pour effectuer une action et gérer des données.

## <a name="objects-in-pipelines"></a>Objets dans les pipelines

Lorsque les commandes sont combinées dans un pipeline, elles passent des informations les unes aux autres sous forme d’objets. Lorsque la première commande s’exécute, elle envoie un ou plusieurs objets dans le pipeline vers la deuxième commande. La deuxième commande reçoit les objets de la première commande, traite les objets, puis passe les objets nouveaux ou modifiés à la commande suivante dans le pipeline.
Cela se poursuit jusqu’à ce que toutes les commandes dans le pipeline s’exécutent.

L’exemple suivant montre comment les objets sont passés d’une commande à l’autre :

```powershell
Get-ChildItem C: | where { $_.PsIsContainer -eq $false } | Format-List
```

La première commande `Get-ChildItem C:` retourne un objet de fichier ou de répertoire pour chaque élément dans le répertoire racine du système de fichiers. Les objets de fichiers et de répertoires sont passés dans le pipeline à la deuxième commande.

La deuxième commande `where { $_.PsIsContainer -eq $false }` utilise la propriété PSIsContainer de tous les objets de système de fichiers pour sélectionner uniquement les fichiers qui ont la valeur false ( \$ false) dans leur propriété PSIsContainer. Les dossiers, qui sont des conteneurs et, par conséquent, ont la valeur true ( \$ vrai) dans leur propriété PSIsContainer, ils ne sont pas sélectionnés.

La deuxième commande transmet uniquement les objets de fichier à la troisième commande `Format-List` , qui affiche les objets de fichier dans une liste.

## <a name="see-also"></a>Voir aussi

[about_Methods](about_Methods.md)

[about_Object_Creation](about_Object_Creation.md)

[about_Properties](about_Properties.md)

[about_Pipelines](about_Pipelines.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)
