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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363698"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="d4420-102">Mise en forme des données affichées</span><span class="sxs-lookup"><span data-stu-id="d4420-102">Formatting Displayed Data</span></span>

<span data-ttu-id="d4420-103">Vous pouvez spécifier le mode d’affichage des points de données individuels dans votre liste, votre table ou votre vue étendue.</span><span class="sxs-lookup"><span data-stu-id="d4420-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="d4420-104">Vous pouvez utiliser l’élément `FormatString` lors de la définition des éléments de votre affichage, ou vous pouvez utiliser l’élément `ScriptBlock` pour appeler la méthode `FormatString` sur les données.</span><span class="sxs-lookup"><span data-stu-id="d4420-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="d4420-105">Utilisation de l’élément FormatString</span><span class="sxs-lookup"><span data-stu-id="d4420-105">Using the FormatString Element</span></span>

<span data-ttu-id="d4420-106">Dans l’exemple suivant, la valeur de la propriété `TotalProcessorTime` de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) est mise en forme à l’aide de l’élément FormatString.</span><span class="sxs-lookup"><span data-stu-id="d4420-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="d4420-107">propriété `TotalProcessorTime`</span><span class="sxs-lookup"><span data-stu-id="d4420-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



