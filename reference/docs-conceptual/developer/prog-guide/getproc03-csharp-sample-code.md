---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code GetProc03 (C#)
description: Exemple de code GetProc03 (C#)
ms.openlocfilehash: c81ba04b2b335f4ce992c6b3ed2f019cf6d7d20f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355576"
---
# <a name="getproc03-c-sample-code"></a>Exemple de code GetProc03 (C#)

Le code suivant illustre l’implémentation d’une `Get-Process` applet de commande qui peut accepter une entrée en pipeline. Cette implémentation définit un `Name` paramètre qui accepte l’entrée de pipeline, récupère des informations de processus à partir de l’ordinateur local en fonction des noms fournis, puis utilise la méthode [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) comme mécanisme de sortie pour envoyer des objets au pipeline.

> [!NOTE]
> Vous pouvez télécharger le fichier source C# (getprov03.cs) pour cette Get-Proc applet de commande à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour Windows Vista et .NET Framework les composants d’exécution 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.

## <a name="code-sample"></a>Exemple de code

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a>Voir aussi

[Guide de programmation pour Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
