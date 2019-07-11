---
title: Runspace01 (C#) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: ab067485d70523a16493eb57170615ab300eaa98
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735059"
---
# <a name="runspace01-c-code-sample"></a>Exemple de code Runspace01 (C#)

Voici les exemples de code pour l’instance d’exécution décrit dans [création d’une Console Application qui s’exécute une commande spécifiée](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program). Pour ce faire, l’application appelle une instance d’exécution et appelle ensuite une commande. (Notez que cette application ne spécifie pas les informations de configuration d’instance d’exécution, ni il crée explicitement un pipeline). La commande est appelée est la `Get-Process` applet de commande.

> [!NOTE]
> Vous pouvez télécharger le C# le fichier source (runspace01.cs) pour cette instance d’exécution à l’aide du Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.

## <a name="code-sample"></a>Exemple de code

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a>Voir aussi

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)