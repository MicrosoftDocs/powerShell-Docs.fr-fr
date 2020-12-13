---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code Runspace02 (C#)
description: Exemple de code Runspace02 (C#)
ms.openlocfilehash: 9e2c0cf37d1bf12a92f4fbf781928c0241202915
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647443"
---
# <a name="runspace02-c-code-sample"></a>Exemple de code Runspace02 (C#)

Voici le code source C# de l’exemple Runspace02. Cet exemple utilise la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) pour exécuter l’applet de commande de `Get-Process` façon synchrone. Les Windows Forms et la liaison de données sont ensuite utilisés pour afficher les résultats dans un contrôle DataGridView

## <a name="code-sample"></a>Exemple de code

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs" range="11-82":::

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)
