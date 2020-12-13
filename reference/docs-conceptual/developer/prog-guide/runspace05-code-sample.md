---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code RunSpace05
description: Exemple de code RunSpace05
ms.openlocfilehash: f128e09522bdb05cba2c160bce4944c829a5c108
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654214"
---
# <a name="runspace05-code-sample"></a>Exemple de code RunSpace05

Voici le code source de l’exemple Runspace05 décrit dans [configuration d’une instance d’exécution à l’aide de RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).
Cet exemple montre comment créer les informations de configuration de l’instance d’exécution, créer une instance d’exécution, créer un pipeline avec une commande unique, puis exécuter le pipeline. La commande exécutée est l’applet de commande `Get-Process` .

> [!NOTE]
> Vous pouvez télécharger le fichier source C# (runspace05.cs) à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.

## <a name="code-sample"></a>Exemple de code

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a>Voir aussi

[Guide de programmation pour Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
