---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code Runspace01 (C#)
description: Exemple de code Runspace01 (C#)
ms.openlocfilehash: e6121c144e1a4c1a1d9460d01119f44ee5835821
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657155"
---
# <a name="runspace01-c-code-sample"></a>Exemple de code Runspace01 (C#)

Voici les exemples de code pour l’instance d’exécution décrite dans [création d’une application console qui exécute une commande spécifiée](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).
Pour ce faire, l’application appelle une instance d’exécution, puis appelle une commande. (Notez que cette application ne spécifie pas d’informations de configuration d’instance d’exécution et ne crée pas de pipeline de manière explicite). La commande appelée est l’applet de commande `Get-Process` .

> [!NOTE]
> Vous pouvez télécharger le fichier source C# (runspace01.cs) pour cette instance d’exécution à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0.
> Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.

## <a name="code-sample"></a>Exemple de code

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a>Voir aussi

[Guide de programmation pour Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
