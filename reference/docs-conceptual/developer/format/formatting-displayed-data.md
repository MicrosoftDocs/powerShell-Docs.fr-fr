---
title: Mise en forme des données affichées | Microsoft Docs
ms.date: 09/12/2016
ms.openlocfilehash: 97d23b3079b2779e518b6b6d2f2ac0c5e9d1f3a3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781509"
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
