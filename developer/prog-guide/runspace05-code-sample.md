---
title: Exemple de Code RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: b16ee45383059c52ce3433699c6b8d2120992431
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429565"
---
# <a name="runspace05-code-sample"></a>Exemple de code RunSpace05

Voici le code source pour l’exemple Runspace05 qui est décrite dans [configuration un RunspaceConfiguration à l’aide d’instance d’exécution](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2). Cet exemple montre comment créer les informations de configuration d’instance d’exécution, créer une instance d’exécution, créer un pipeline avec une seule commande et puis exécuter le pipeline. La commande est exécutée est la `Get-Process` applet de commande.

> [!NOTE]
> Vous pouvez télécharger le C# le fichier source (runspace05.cs) en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.

## <a name="code-sample"></a>Exemple de code

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>Voir aussi

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)