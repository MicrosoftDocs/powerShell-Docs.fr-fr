---
title: Exemple de code RunSpace06 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8767ac8dc3a3d9253c2a53a4754d9bd54304abb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784722"
---
# <a name="runspace06-code-sample"></a>Exemple de code RunSpace06

Voici le code source de l’exemple Runspace06 décrit dans [configuration d’une instance d’exécution à l’aide d’un composant logiciel enfichable Windows PowerShell](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).
Cet exemple d’application crée une instance d’exécution basée sur un composant logiciel enfichable Windows PowerShell, qui est ensuite utilisé pour exécuter un pipeline avec une seule commande. Pour ce faire, l’application crée les informations de configuration de l’instance d’exécution, crée une instance d’exécution, crée un pipeline avec une commande unique, puis exécute le pipeline.

> [!NOTE]
> Vous pouvez télécharger le fichier source C# (runspace06.cs) à l’aide du kit de développement logiciel (SDK) Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.

## <a name="code-sample"></a>Exemple de code

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs" range="11-85":::

## <a name="see-also"></a>Voir aussi

[Guide de programmation pour Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
