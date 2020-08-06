---
title: Exemple de code GetProc02 (C#) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d9afa8fff23d99661987c067e8082a9294c12717
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787153"
---
# <a name="getproc02-c-sample-code"></a>Exemple de code GetProc02 (C#)

Le code suivant illustre l’implémentation d’une `Get-Process` applet de commande qui accepte l’entrée de ligne de commande. Notez que cette implémentation définit un `Name` paramètre pour autoriser l’entrée de ligne de commande et qu’elle utilise la méthode [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) comme mécanisme de sortie pour l’envoi d’objets de sortie au pipeline.

## <a name="code-sample"></a>Exemple de code

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)
