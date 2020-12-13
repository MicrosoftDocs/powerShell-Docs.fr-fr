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
# <a name="formatting-displayed-data"></a><span data-ttu-id="71f8e-103">Mise en forme des données affichées</span><span class="sxs-lookup"><span data-stu-id="71f8e-103">Formatting Displayed Data</span></span>

<span data-ttu-id="71f8e-104">Vous pouvez spécifier le mode d’affichage des points de données individuels dans votre liste, votre table ou votre vue étendue.</span><span class="sxs-lookup"><span data-stu-id="71f8e-104">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="71f8e-105">Vous pouvez utiliser l' `FormatString` élément lors de la définition des éléments de votre affichage, ou vous pouvez utiliser l' `ScriptBlock` élément pour appeler la `FormatString` méthode sur les données.</span><span class="sxs-lookup"><span data-stu-id="71f8e-105">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="71f8e-106">Utilisation de l’élément FormatString</span><span class="sxs-lookup"><span data-stu-id="71f8e-106">Using the FormatString Element</span></span>

<span data-ttu-id="71f8e-107">Dans l’exemple suivant, la valeur de la `TotalProcessorTime` propriété de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) est mise en forme à l’aide de l’élément FormatString.</span><span class="sxs-lookup"><span data-stu-id="71f8e-107">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="71f8e-108">la `TotalProcessorTime` propriété</span><span class="sxs-lookup"><span data-stu-id="71f8e-108">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
