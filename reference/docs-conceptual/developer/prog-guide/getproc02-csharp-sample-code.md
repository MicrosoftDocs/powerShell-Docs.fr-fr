---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code GetProc02 (C#)
description: Exemple de code GetProc02 (C#)
ms.openlocfilehash: 17fd0d0c0829ed21ef955fd2e62e9ee089d62190
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355610"
---
# <a name="getproc02-c-sample-code"></a>Exemple de code GetProc02 (C#)

Le code suivant illustre l’implémentation d’une `Get-Process` applet de commande qui accepte l’entrée de ligne de commande. Notez que cette implémentation définit un `Name` paramètre pour autoriser l’entrée de ligne de commande et qu’elle utilise la méthode [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) comme mécanisme de sortie pour l’envoi d’objets de sortie au pipeline.

## <a name="code-sample"></a>Exemple de code

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)
