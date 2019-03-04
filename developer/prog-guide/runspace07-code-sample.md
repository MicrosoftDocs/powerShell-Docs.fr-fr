---
title: Exemple de Code RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 3e016b0e98234797afc8f303a55919228eaf8829
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857925"
---
# <a name="runspace07-code-sample"></a>Exemple de code RunSpace07

Voici le code source pour l’exemple Runspace07 décrit dans [création d’une Application qu’ajoute des commandes de la Console à un Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e). Cet exemple d’application crée une instance d’exécution, crée un pipeline, ajoute les deux commandes au pipeline, puis exécute le pipeline. Les commandes ajoutées au pipeline sont le `Get-Process` et `Measure-Object` applets de commande.

> [!NOTE]
> Vous pouvez télécharger le C# le fichier source (runspace07.cs) en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants de Microsoft .NET Framework 3.0 Runtime. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
> Vous pouvez télécharger le C# le fichier source (runspace07.cs) en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants de Microsoft .NET Framework 3.0 Runtime. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.

## <a name="code-sample"></a>Exemple de code

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a>Voir aussi

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)