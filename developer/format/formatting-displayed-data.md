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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854985"
---
# <a name="formatting-displayed-data"></a>Mise en forme des données affichées

Vous pouvez spécifier le mode d’affichage des points de données individuels dans votre liste, une Table ou un affichage plus large. Vous pouvez utiliser la `FormatString` élément lorsque vous définissez les éléments de votre vue, ou vous pouvez utiliser la `ScriptBlock` élément pour appeler le `FormatString` (méthode) sur les données.

## <a name="using-the-formatstring-element"></a>À l’aide de l’élément FormatString

Dans l’exemple suivant, la valeur de la `TotalProcessorTime` propriété de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet est mis en forme à l’aide de l’élément FormatString. Le `TotalProcessorTime` propriété

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



