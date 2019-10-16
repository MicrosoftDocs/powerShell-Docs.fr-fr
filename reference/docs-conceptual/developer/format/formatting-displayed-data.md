---
title: Mise en forme des données affichées | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363698"
---
# <a name="formatting-displayed-data"></a>Mise en forme des données affichées

Vous pouvez spécifier le mode d’affichage des points de données individuels dans votre liste, votre table ou votre vue étendue. Vous pouvez utiliser l’élément `FormatString` lors de la définition des éléments de votre affichage, ou vous pouvez utiliser l’élément `ScriptBlock` pour appeler la méthode `FormatString` sur les données.

## <a name="using-the-formatstring-element"></a>Utilisation de l’élément FormatString

Dans l’exemple suivant, la valeur de la propriété `TotalProcessorTime` de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) est mise en forme à l’aide de l’élément FormatString. la propriété `TotalProcessorTime`

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



