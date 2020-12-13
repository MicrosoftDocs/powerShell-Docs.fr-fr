---
ms.date: 09/12/2016
ms.topic: reference
title: Mise en forme des données affichées
description: Mise en forme des données affichées
ms.openlocfilehash: 40f6b3b4fa36062ee0bad3f197ad159f571445c8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667859"
---
# <a name="formatting-displayed-data"></a>Mise en forme des données affichées

Vous pouvez spécifier le mode d’affichage des points de données individuels dans votre liste, votre table ou votre vue étendue. Vous pouvez utiliser l' `FormatString` élément lors de la définition des éléments de votre affichage, ou vous pouvez utiliser l' `ScriptBlock` élément pour appeler la `FormatString` méthode sur les données.

## <a name="using-the-formatstring-element"></a>Utilisation de l’élément FormatString

Dans l’exemple suivant, la valeur de la `TotalProcessorTime` propriété de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) est mise en forme à l’aide de l’élément FormatString. la `TotalProcessorTime` propriété

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
