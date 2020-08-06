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
# <a name="formatting-displayed-data"></a><span data-ttu-id="d3434-102">Mise en forme des données affichées</span><span class="sxs-lookup"><span data-stu-id="d3434-102">Formatting Displayed Data</span></span>

<span data-ttu-id="d3434-103">Vous pouvez spécifier le mode d’affichage des points de données individuels dans votre liste, votre table ou votre vue étendue.</span><span class="sxs-lookup"><span data-stu-id="d3434-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="d3434-104">Vous pouvez utiliser l' `FormatString` élément lors de la définition des éléments de votre affichage, ou vous pouvez utiliser l' `ScriptBlock` élément pour appeler la `FormatString` méthode sur les données.</span><span class="sxs-lookup"><span data-stu-id="d3434-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="d3434-105">Utilisation de l’élément FormatString</span><span class="sxs-lookup"><span data-stu-id="d3434-105">Using the FormatString Element</span></span>

<span data-ttu-id="d3434-106">Dans l’exemple suivant, la valeur de la `TotalProcessorTime` propriété de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) est mise en forme à l’aide de l’élément FormatString.</span><span class="sxs-lookup"><span data-stu-id="d3434-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="d3434-107">la `TotalProcessorTime` propriété</span><span class="sxs-lookup"><span data-stu-id="d3434-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
